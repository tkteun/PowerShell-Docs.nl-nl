---
description: Bevat informatie over Power shell-thread taken. Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 4951ac2c14c0685fbf2ead16bc52c64096231260
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2020
ms.locfileid: "93253078"
---
# <a name="about-thread-jobs"></a>Over thread-taken

## <a name="short-description"></a>Korte beschrijving

Bevat informatie over Power shell-thread taken. Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.

## <a name="long-description"></a>Lange beschrijving

In dit artikel wordt uitgelegd hoe u thread taken uitvoert in Power shell op een lokale computer.
Zie [about_Jobs](about_Jobs.md)voor meer informatie over het uitvoeren van achtergrond taken op een lokale computer.

Start een thread-taak met behulp van de- `Start-ThreadJob` cmdlet. Deze cmdlet is beschikbaar in de **ThreadJob** -module die wordt geleverd met Power shell.
`Start-ThreadJob` retourneert een enkel taak object waarmee de uitgevoerde opdracht of het script wordt ingekapseld en kan worden gebruikt met alle Power shell-taken voor het bewerken van cmdlets.

## <a name="the-job-cmdlets"></a>De taak-cmdlets

|Cmdlet           |Beschrijving                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|Hiermee wordt een thread taak op een lokale computer gestart.               |
|`Get-Job`        |Hiermee worden de taken opgehaald die in de huidige sessie zijn gestart.|
|`Receive-Job`    |Hiermee worden de resultaten van taken opgehaald.                              |
|`Stop-Job`       |Hiermee stopt u een actieve taak.                                   |
|`Wait-Job`       |Onderdrukt de opdracht prompt totdat een of alle taken zijn|
|                 |aangevuld.                                              |
|`Remove-Job`     |Hiermee verwijdert u een taak.                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a>Een thread-taak op de lokale computer starten

Als u een thread-taak op de lokale computer wilt starten, gebruikt u de `Start-ThreadJob` cmdlet.

Als u een `Start-ThreadJob` opdracht wilt schrijven, plaatst u de opdracht of het script waarmee de taak wordt uitgevoerd in accolades ( `{ }` ).

Met de volgende opdracht wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` op de lokale computer.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

`Start-ThreadJob`Met de opdracht wordt een `ThreadJob` object geretourneerd dat de actieve taak vertegenwoordigt. Het taak object bevat nuttige informatie over de taak, inclusief de huidige uitvoerings status. De resultaten van de taak worden verzameld wanneer de resultaten worden gegenereerd.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>Wachten tot een taak is voltooid en taak resultaten ophalen

U kunt Power shell-taak-cmdlets gebruiken, zoals `Wait-Job` en `Receive-Job` wachten tot een taak is voltooid en vervolgens alle resultaten retour neren die zijn gegenereerd door de taak.

Met de volgende opdracht wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` , wordt gewacht tot de opdracht is voltooid en worden alle gegevens resultaten weer gegeven die zijn gegenereerd door de opdracht.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

## <a name="powershell-concurrency-and-jobs"></a>Gelijktijdigheid en taken voor Power shell

Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken. Power shell biedt drie oplossingen op basis van taken voor ondersteuning van gelijktijdigheid.

|Taak            |Beschrijving                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |Opdracht en script worden uitgevoerd op een externe computer.                 |
|`BackgroundJob`|Opdracht en script worden uitgevoerd in een afzonderlijk proces op de lokale    |
|               |machine.                                                     |
|`ThreadJob`    |Opdracht en script worden uitgevoerd in een afzonderlijke thread binnen hetzelfde  |
|               |verwerken op de lokale computer.                                |

Elk type taak heeft voor delen en nadelen. Het uitvoeren van een script op afstand op een afzonderlijke machine of in een afzonderlijk proces heeft een goede isolatie. Fouten zijn niet van invloed op andere actieve taken of de client die de taak heeft gestart. Maar de externe laag voegt overhead toe, inclusief object serialisatie. Alle objecten die zijn door gegeven aan en van de externe sessie, moeten worden geserialiseerd en vervolgens worden gedeserialiseerd wanneer deze tussen de client en de doel sessie worden door gegeven. De serialisatie-bewerking kan veel reken-en geheugen bronnen gebruiken voor grote complexe gegevens objecten.

## <a name="powershell-thread-based-jobs"></a>Taken op basis van Power shell-thread

Thread-gebaseerde taken zijn niet zo krachtig als externe en achtergrond taken, omdat ze in hetzelfde proces worden uitgevoerd op verschillende threads. Als één taak een kritieke fout heeft waardoor het proces wordt afgebroken, mislukken alle andere taken in het proces ook.

Thread-gebaseerde taken hebben echter veel minder overhead. Ze hoeven geen externe laag of serialisatie te gebruiken. Het resultaat is dat thread-gebaseerde taken veel sneller worden uitgevoerd en veel minder resources gebruiken dan de andere taak typen.

## <a name="thread-job-performance"></a>Thread-taak prestaties

Thread taken zijn sneller en lichter gewicht dan andere typen taken. Maar ze hebben nog steeds overhead die erg groot kan zijn in vergelijking met werk dat door de taak wordt uitgevoerd.

Power Shell voert opdrachten en scripts uit in een sessie. Er kan slechts één opdracht of script tegelijk in een sessie worden uitgevoerd. Bij het uitvoeren van meerdere taken wordt elke taak in een afzonderlijke sessie uitgevoerd. Elke sessie draagt bij aan de overhead.

Thread taken bieden de beste prestaties wanneer het werk dat ze uitvoeren, groter is dan de overhead van de sessie die wordt gebruikt om de taak uit te voeren. Er zijn twee gevallen voor die voldoen aan deze criteria.

- Werk is het berekenen van intensieve uitvoering van een script op meerdere thread taken kan profiteren van meerdere processor kernen en sneller worden uitgevoerd.

- Het werk bestaat uit een belang rijke wacht tijd: een script dat wacht op een time-out voor I/O-of externe aanroep resultaten. Parallelle uitvoeringen worden gewoonlijk sneller uitgevoerd dan bij een opeenvolgende uitvoering.

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

In het eerste voor beeld ziet u een foreach-lus waarmee 1000-thread taken worden gemaakt voor het schrijven van eenvoudige teken reeksen. Als gevolg van de taak overhead duurt het meer dan 33 seconden om te volt ooien.

In het tweede voor beeld wordt de `ForEach` cmdlet uitgevoerd om dezelfde 1000 bewerkingen uit te voeren en elke teken reeks schrijven wordt sequentieel uitgevoerd zonder taak overhead. Deze is in een paar 25 milliseconden voltooid.

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

In het bovenstaande voor beeld worden Maxi maal 5000 vermeldingen verzameld voor 10 afzonderlijke systeem Logboeken. Omdat het script een aantal logboeken moet lezen, is het zinvol om de bewerkingen parallel uit te voeren. En de taak wordt twee keer zo snel voltooid als wanneer het script op de juiste wijze wordt uitgevoerd.

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>Thread-taken en-variabelen

Variabelen worden op verschillende manieren door gegeven aan thread taken.

`Start-ThreadJob` kan variabelen accepteren die worden verzonden naar de cmdlet, door gegeven aan het script blok via het `$using` sleutel woord of door gegeven via de para meter **argument List** .

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

Omdat thread-taken in hetzelfde proces worden uitgevoerd, moet elk referentie type dat naar de taak wordt door gegeven, zorgvuldig worden behandeld. Als het geen thread-safe object is, mag het nooit worden toegewezen aan en moet de methode en eigenschappen nooit worden aangeroepen.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

In het bovenstaande voor beeld wordt een thread safe dotNet-object door gegeven `ConcurrentDictionary` aan alle onderliggende taken om proces objecten met unieke namen te verzamelen. Omdat het een thread-safe object is, kan het veilig worden gebruikt terwijl de taken gelijktijdig in het proces worden uitgevoerd.

## <a name="see-also"></a>Zie ook

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Begin taak](xref:Microsoft.PowerShell.Core.Start-Job)
- [Get-job](xref:Microsoft.PowerShell.Core.Get-Job)
- [Receive-job](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stoppen-taak](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Verwijderen-taak](xref:Microsoft.PowerShell.Core.Remove-Job)
