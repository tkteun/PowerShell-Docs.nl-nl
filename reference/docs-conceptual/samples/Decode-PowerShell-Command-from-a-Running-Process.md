---
ms.date: 11/13/2018
keywords: PowerShell-cmdlet
title: Een PowerShell-opdracht decoderen vanuit een actief proces
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403914"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a><span data-ttu-id="05f9f-103">Een PowerShell-opdracht decoderen vanuit een actief proces</span><span class="sxs-lookup"><span data-stu-id="05f9f-103">Decode a PowerShell command from a running process</span></span>

<span data-ttu-id="05f9f-104">Mogelijk hebt u soms een proces dat wordt uitgevoerd in een grote hoeveelheid is beslag PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05f9f-104">At times, you may have a PowerShell process running that is taking up a large amount of resources.</span></span>
<span data-ttu-id="05f9f-105">Dit proces kan worden uitgevoerd in de context van een [Task Scheduler][] taak of een [SQL ServerAgent][] taak.</span><span class="sxs-lookup"><span data-stu-id="05f9f-105">This process could be running in the context of a [Task Scheduler][] job or a [SQL Server Agent][] job.</span></span> <span data-ttu-id="05f9f-106">Wanneer er meerdere PowerShell processen die worden uitgevoerd, kan het lastig zijn om te weten welk proces Hiermee geeft u het probleem.</span><span class="sxs-lookup"><span data-stu-id="05f9f-106">Where there are multiple PowerShell processes running, it can be difficult to know which process represents the problem.</span></span> <span data-ttu-id="05f9f-107">In dit artikel laat zien hoe moet worden gedecodeerd een scriptblok een PowerShell-proces momenteel wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="05f9f-107">This article shows how to decode a script block that a PowerShell process is currently running.</span></span>

## <a name="create-a-long-running-process"></a><span data-ttu-id="05f9f-108">Een langlopende proces maken</span><span class="sxs-lookup"><span data-stu-id="05f9f-108">Create a long running process</span></span>

<span data-ttu-id="05f9f-109">Om te demonstreren in dit scenario, opent u een nieuwe PowerShell-venster en voer de volgende code uit.</span><span class="sxs-lookup"><span data-stu-id="05f9f-109">To demonstrate this scenario, open a new PowerShell window and run the following code.</span></span> <span data-ttu-id="05f9f-110">Het uitvoeren van een PowerShell-opdracht die een getal elke minuut gedurende tien minuten uitvoert.</span><span class="sxs-lookup"><span data-stu-id="05f9f-110">It executes a PowerShell command that outputs a number every minute for 10 minutes.</span></span>

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

## <a name="view-the-process"></a><span data-ttu-id="05f9f-111">Het proces weergeven</span><span class="sxs-lookup"><span data-stu-id="05f9f-111">View the process</span></span>

<span data-ttu-id="05f9f-112">De hoofdtekst van de opdracht waarmee het uitvoeren van PowerShell wordt opgeslagen in de **CommandLine** eigenschap van de [Win32_Process][] klasse.</span><span class="sxs-lookup"><span data-stu-id="05f9f-112">The body of the command which PowerShell is executing is stored in the **CommandLine** property of the [Win32_Process][] class.</span></span> <span data-ttu-id="05f9f-113">Als de opdracht is een [opdracht gecodeerd][], wordt de **CommandLine** eigenschap bevat de tekenreeks 'EncodedCommand'.</span><span class="sxs-lookup"><span data-stu-id="05f9f-113">If the command is an [encoded command][], the **CommandLine** property contains the string "EncodedCommand".</span></span> <span data-ttu-id="05f9f-114">Met deze informatie, zijn de gecodeerde opdracht ongedaan maken via het volgende proces verborgen.</span><span class="sxs-lookup"><span data-stu-id="05f9f-114">Using this information, the encoded command can be de-obfuscated via the following process.</span></span>

<span data-ttu-id="05f9f-115">Start PowerShell als beheerder.</span><span class="sxs-lookup"><span data-stu-id="05f9f-115">Start PowerShell as Administrator.</span></span> <span data-ttu-id="05f9f-116">Het is essentieel dat PowerShell als beheerder wordt uitgevoerd, anders geen resultaten worden geretourneerd bij het opvragen van de actieve processen.</span><span class="sxs-lookup"><span data-stu-id="05f9f-116">It is vital that PowerShell is running as administrator, otherwise no results are returned when querying the running processes.</span></span>

<span data-ttu-id="05f9f-117">Voer de volgende opdracht uit om de PowerShell-processen met een gecodeerde-opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="05f9f-117">Execute the following command to get all of the PowerShell processes that have an encoded command:</span></span>

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

<span data-ttu-id="05f9f-118">De volgende opdracht maakt u een aangepaste PowerShell-object dat de proces-ID en de gecodeerde opdracht bevat.</span><span class="sxs-lookup"><span data-stu-id="05f9f-118">The following command creates a custom PowerShell object that contains the process ID and the encoded command.</span></span>

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

<span data-ttu-id="05f9f-119">Nu kan de gecodeerde opdracht worden gedecodeerd.</span><span class="sxs-lookup"><span data-stu-id="05f9f-119">Now the encoded command can be decoded.</span></span> <span data-ttu-id="05f9f-120">Het volgende codefragment doorloopt over het object command details, de gecodeerde opdracht decodeert en voegt de gedecodeerde opdracht terug naar het object voor verder onderzoek.</span><span class="sxs-lookup"><span data-stu-id="05f9f-120">The following snippet iterates over the command details object, decodes the encoded command, and adds the decoded command back to the object for further investigation.</span></span>

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

<span data-ttu-id="05f9f-121">De gedecodeerde opdracht kan nu worden gecontroleerd door het selecteren van de eigenschap gedecodeerde command.</span><span class="sxs-lookup"><span data-stu-id="05f9f-121">The decoded command can now be reviewed by selecting the decoded command property.</span></span>

```output
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

[Task Scheduler]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL ServerAgent]: /sql/ssms/agent/sql-server-agent
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[opdracht gecodeerd]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
[encoded command]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
