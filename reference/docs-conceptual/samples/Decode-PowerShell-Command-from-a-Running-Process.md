---
ms.date: 11/13/2018
keywords: PowerShell-cmdlet
title: Een PowerShell-opdracht decoderen vanuit een actief proces
author: randomnote1
ms.openlocfilehash: a0602070a8c5b60ce0bb09e227690f48d970a868
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086235"
---
# <a name="decode-a-powershell-command-from-a-running-process"></a>Een PowerShell-opdracht decoderen vanuit een actief proces

Mogelijk hebt u soms een proces dat wordt uitgevoerd in een grote hoeveelheid is beslag PowerShell.
Dit proces kan worden uitgevoerd in de context van een [Task Scheduler][] taak of een [SQL Server Agent][] taak. Wanneer er meerdere PowerShell processen die worden uitgevoerd, kan het lastig zijn om te weten welk proces Hiermee geeft u het probleem. In dit artikel laat zien hoe moet worden gedecodeerd een scriptblok een PowerShell-proces momenteel wordt uitgevoerd.

## <a name="create-a-long-running-process"></a>Een langlopende proces maken

Om te demonstreren in dit scenario, opent u een nieuwe PowerShell-venster en voer de volgende code uit. Het uitvoeren van een PowerShell-opdracht die een getal elke minuut gedurende tien minuten uitvoert.

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

## <a name="view-the-process"></a>Het proces weergeven

De hoofdtekst van de opdracht waarmee het uitvoeren van PowerShell wordt opgeslagen in de **CommandLine** eigenschap van de [Win32_Process][] klasse. Als de opdracht is een [opdracht gecodeerd][], wordt de **CommandLine** eigenschap bevat de tekenreeks 'EncodedCommand'. Met deze informatie, zijn de gecodeerde opdracht ongedaan maken via het volgende proces verborgen.

Start PowerShell als beheerder. Het is essentieel dat PowerShell als beheerder wordt uitgevoerd, anders geen resultaten worden geretourneerd bij het opvragen van de actieve processen.

Voer de volgende opdracht uit om de PowerShell-processen met een gecodeerde-opdracht uit:

```powershell
$powerShellProcesses = Get-CimInstance -ClassName Win32_Process -Filter 'CommandLine LIKE "%EncodedCommand%"'
```

De volgende opdracht maakt u een aangepaste PowerShell-object dat de proces-ID en de gecodeerde opdracht bevat.

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

Nu kan de gecodeerde opdracht worden gedecodeerd. Het volgende codefragment doorloopt over het object command details, de gecodeerde opdracht decodeert en voegt de gedecodeerde opdracht terug naar het object voor verder onderzoek.

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

De gedecodeerde opdracht kan nu worden gecontroleerd door het selecteren van de eigenschap gedecodeerde command.

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
[SQL Server Agent]: /sql/ssms/agent/sql-server-agent
[Win32_Process]: /windows/desktop/CIMWin32Prov/win32-process
[opdracht gecodeerd]: /powershell/scripting/core-powershell/console/powershell.exe-command-line-help#-encodedcommand-
