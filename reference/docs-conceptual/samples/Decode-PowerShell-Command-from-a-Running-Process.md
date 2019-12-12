---
ms.date: 11/13/2018
keywords: Power shell, cmdlet
title: Een PowerShell-opdracht decoderen vanuit een actief proces
author: randomnote1
ms.openlocfilehash: a6c01d8edf67aba6c47350a97cc0ceec4801ad29
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "66470960"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Een PowerShell-opdracht decoderen vanuit een actief proces

Op het moment dat er een Power Shell-proces wordt uitgevoerd dat een grote hoeveelheid resources in beslag neemt.
Dit proces kan worden uitgevoerd in de context van een [taak planner][] of een [SQL Server Agent][] taak. Als er meerdere Power shell-processen worden uitgevoerd, kan het lastig zijn om te weten welk proces het probleem vertegenwoordigt. In dit artikel wordt beschreven hoe u een script blok decodeert dat op dit moment wordt uitgevoerd voor een Power Shell-proces.

## <a name="create-a-long-running-process"></a>Een langlopend proces maken

Open een nieuw Power shell-venster en voer de volgende code uit om dit scenario te demonstreren. Er wordt een Power shell-opdracht uitgevoerd die elke minuut gedurende tien minuten een getal uitvoert.

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

## <a name="view-the-process"></a>Het proces weer geven

De hoofd tekst van de opdracht die Power shell uitvoert, wordt opgeslagen in de eigenschap **commandline** van de klasse [Win32_Process][] . Als de opdracht een gecodeerde opdracht is, bevat de eigenschap **commandline** de teken reeks "EncodedCommand". Met deze informatie kunt u de gecodeerde opdracht decoderen via het volgende proces.

Start Power shell als Administrator. Het is essentieel dat Power shell wordt uitgevoerd als Administrator, anders worden er geen resultaten geretourneerd tijdens het uitvoeren van query's op de actieve processen.

Voer de volgende opdracht uit om alle Power shell-processen met een gecodeerde opdracht op te halen:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

Met de volgende opdracht maakt u een aangepast Power shell-object dat de proces-ID en de versleutelde opdracht bevat.

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

De gecodeerde opdracht kan nu worden gedecodeerd. Het volgende code fragment loopt over het object opdracht Details, decodeert de gecodeerde opdracht en voegt de gedecodeerde opdracht weer toe aan het object voor verdere onderzoek.

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

De gedecodeerde opdracht kan nu worden gecontroleerd door de gedecodeerde opdracht eigenschap te selecteren.

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

[Taak planner]: /windows/desktop/TaskSchd/task-scheduler-start-page
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
