---
ms.date: 11/13/2018
keywords: powershell,cmdlet
title: Een PowerShell-opdracht decoderen vanuit een actief proces
author: randomnote1
description: In dit artikel wordt beschreven hoe u een script blok decodeert dat op dit moment wordt uitgevoerd voor een Power Shell-proces.
ms.openlocfilehash: 95b4b806665bf8137712ebb183329039bc1e1deb
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500484"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="11ad4-104">Een PowerShell-opdracht decoderen vanuit een actief proces</span><span class="sxs-lookup"><span data-stu-id="11ad4-104">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="11ad4-105">Op het moment dat er een Power Shell-proces wordt uitgevoerd dat een grote hoeveelheid resources in beslag neemt.</span><span class="sxs-lookup"><span data-stu-id="11ad4-105">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="11ad4-106">Dit proces kan worden uitgevoerd in de context van een [taak planner][] of een [SQL Server Agent][] taak.</span><span class="sxs-lookup"><span data-stu-id="11ad4-106">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="11ad4-107">Als er meerdere Power shell-processen worden uitgevoerd, kan het lastig zijn om te weten welk proces het probleem vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="11ad4-107">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="11ad4-108">In dit artikel wordt beschreven hoe u een script blok decodeert dat op dit moment wordt uitgevoerd voor een Power Shell-proces.</span><span class="sxs-lookup"><span data-stu-id="11ad4-108">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="11ad4-109">Een langlopend proces maken</span><span class="sxs-lookup"><span data-stu-id="11ad4-109">Create a long running process</span></span>

<span data-ttu-id="11ad4-110">Open een nieuw Power shell-venster en voer de volgende code uit om dit scenario te demonstreren.</span><span class="sxs-lookup"><span data-stu-id="11ad4-110">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="11ad4-111">Er wordt een Power shell-opdracht uitgevoerd die elke minuut gedurende tien minuten een getal uitvoert.</span><span class="sxs-lookup"><span data-stu-id="11ad4-111">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

```powershell
powershell.exe -Command {
    $i = 1
    while ( $i -le 10 )
    {
        Write-Output -InputObject $i
        Start-Sleep -Seconds 60
        $i++
    }
}
```

## <a name="view-the-process"></a><span data-ttu-id="11ad4-112">Het proces weer geven</span><span class="sxs-lookup"><span data-stu-id="11ad4-112">View the process</span></span>

<span data-ttu-id="11ad4-113">De hoofd tekst van de opdracht die Power shell uitvoert, wordt opgeslagen in de eigenschap **commandline** van de klasse [Win32_Process][] .</span><span class="sxs-lookup"><span data-stu-id="11ad4-113">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="11ad4-114">Als de opdracht een gecodeerde opdracht is, bevat de eigenschap **commandline** de teken reeks "EncodedCommand".</span><span class="sxs-lookup"><span data-stu-id="11ad4-114">If the command is an encoded command, the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="11ad4-115">Met deze informatie kunt u de gecodeerde opdracht decoderen via het volgende proces.</span><span class="sxs-lookup"><span data-stu-id="11ad4-115">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="11ad4-116">Start Power shell als Administrator.</span><span class="sxs-lookup"><span data-stu-id="11ad4-116">Start PowerShell as Administrator.</span></span> <span data-ttu-id="11ad4-117">Het is essentieel dat Power shell wordt uitgevoerd als Administrator, anders worden er geen resultaten geretourneerd tijdens het uitvoeren van query's op de actieve processen.</span><span class="sxs-lookup"><span data-stu-id="11ad4-117">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="11ad4-118">Voer de volgende opdracht uit om alle Power shell-processen met een gecodeerde opdracht op te halen:</span><span class="sxs-lookup"><span data-stu-id="11ad4-118">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="11ad4-119">Met de volgende opdracht maakt u een aangepast Power shell-object dat de proces-ID en de versleutelde opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="11ad4-119">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

```powershell
$commandDetails = $powerShellProcesses | Select-Object -Property ProcessId,
@{
    name       = 'EncodedCommand'
    expression = {
        if ( $_.CommandLine -match 'encodedCommand (.*) -inputFormat' )
        {
            return $matches[1]
        }
    }
}
```

<span data-ttu-id="11ad4-120">De gecodeerde opdracht kan nu worden gedecodeerd.</span><span class="sxs-lookup"><span data-stu-id="11ad4-120">Now the encoded command can be decoded.</span></span> <span data-ttu-id="11ad4-121">Het volgende code fragment loopt over het object opdracht Details, decodeert de gecodeerde opdracht en voegt de gedecodeerde opdracht weer toe aan het object voor verdere onderzoek.</span><span class="sxs-lookup"><span data-stu-id="11ad4-121">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

```powershell
$commandDetails | ForEach-Object -Process {
    # Get the current process
    $currentProcess = $_

    # Convert the Base 64 string to a Byte Array
    $commandBytes = [System.Convert]::FromBase64String($currentProcess.EncodedCommand)

    # Convert the Byte Array to a string
    $decodedCommand = [System.Text.Encoding]::Unicode.GetString($commandBytes)

    # Add the decoded command back to the object
    $commandDetails |
        Where-Object -FilterScript { $_.ProcessId -eq $_.ProcessId } |
        Add-Member -MemberType NoteProperty -Name DecodedCommand -Value $decodedCommand
}
$commandDetails[0]
```

<span data-ttu-id="11ad4-122">De gedecodeerde opdracht kan nu worden gecontroleerd door de gedecodeerde opdracht eigenschap te selecteren.</span><span class="sxs-lookup"><span data-stu-id="11ad4-122">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```Output
ProcessId      : 8752
EncodedCommand : IAAKAAoACgAgAAoAIAAgACAAIAAkAGkAIAA9ACAAMQAgAAoACgAKACAACgAgACAAIAAgAHcAaABpAGwAZQAgACgAIAAkAGkAIAAtAG
                 wAZQAgADEAMAAgACkAIAAKAAoACgAgAAoAIAAgACAAIAB7ACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABXAHIAaQB0AGUALQBP
                 AHUAdABwAHUAdAAgAC0ASQBuAHAAdQB0AE8AYgBqAGUAYwB0ACAAJABpACAACgAKAAoAIAAKACAAIAAgACAAIAAgACAAIABTAHQAYQ
                 ByAHQALQBTAGwAZQBlAHAAIAAtAFMAZQBjAG8AbgBkAHMAIAA2ADAAIAAKAAoACgAgAAoAIAAgACAAIAAgACAAIAAgACQAaQArACsA
                 IAAKAAoACgAgAAoAIAAgACAAIAB9ACAACgAKAAoAIAAKAA==
DecodedCommand :
                     $i = 1

                     while ( $i -le 10 )

                     {

                         Write-Output -InputObject $i

                         Start-Sleep -Seconds 60

                         $i++

                     }
```

[Taak planner]: /windows/desktop/TaskSchd/task-scheduler-start-page
[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
