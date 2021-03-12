---
description: Bevat informatie over Power shell-thread taken. Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.
Locale: en-US
ms.date: 11/11/2020
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 67f3fc585a8c2d1c3ca98c7336a7e367ed6c66c7
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194250"
---
# <a name="about-thread-jobs"></a>Over thread-taken

## <a name="short-description"></a>Korte beschrijving

Bevat informatie over Power shell-thread taken. Een thread-taak is een type achtergrond taak waarmee een opdracht of expressie wordt uitgevoerd in een afzonderlijke thread binnen het huidige sessie proces.

## <a name="long-description"></a>Lange beschrijving

Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken. Er zijn drie typen taken die door Power shell worden geboden ter ondersteuning van gelijktijdigheid.

- `RemoteJob` -Opdrachten en scripts worden uitgevoerd in een externe sessie. Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.
- `BackgroundJob` -Opdrachten en scripts worden in een afzonderlijk proces op de lokale computer uitgevoerd. Zie [About Jobs](about_Jobs.md) (Taken) voor meer informatie.
- `PSTaskJob` of `ThreadJob` -opdrachten en scripts worden uitgevoerd in een afzonderlijke thread binnen hetzelfde proces op de lokale computer.

Thread-gebaseerde taken zijn niet zo krachtig als externe en achtergrond taken, omdat ze in hetzelfde proces op verschillende threads worden uitgevoerd. Als één taak een kritieke fout heeft die het proces vastloopt, worden alle andere taken in het proces beëindigd.

Thread-gebaseerde taken vereisen echter minder overhead. Ze gebruiken geen externe laag of serialisatie. De resultaat objecten worden geretourneerd als verwijzingen naar live-objecten in de huidige sessie. Zonder deze overhead worden thread-gebaseerde taken sneller uitgevoerd en worden minder resources gebruikt dan de andere taak typen.

> [!IMPORTANT]
> Met de bovenliggende sessie die de taak heeft gemaakt, wordt ook de taak status bewaakt en worden de pijplijn gegevens verzameld. Het onderliggende proces van de taak wordt beëindigd door de bovenliggende bewerking zodra de taak de status voltooid heeft bereikt. Als de bovenliggende sessie wordt beëindigd, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen.

Er zijn twee manieren om deze situatie te omzeilen:

1. Gebruiken `Invoke-Command` om taken te maken die worden uitgevoerd in sessies zonder verbinding. Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.
1. Gebruiken `Start-Process` om een nieuw proces te maken in plaats van een taak. Zie [start-process](xref:Microsoft.PowerShell.Management.Start-Process)(Engelstalig) voor meer informatie.

## <a name="how-to-start-and-manage-thread-based-jobs"></a>Thread-gebaseerde taken starten en beheren

Er zijn twee manieren om thread-gebaseerde taken te starten:

- `Start-ThreadJob` -uit de **ThreadJob** -module
- `ForEach-Object -Parallel -AsJob` -de parallelle functie is toegevoegd in Power shell 7,0

Gebruik dezelfde **taak** -cmdlets die worden beschreven in [about_Jobs](about_Jobs.md) om thread-gebaseerde taken te beheren.

### <a name="using-start-threadjob"></a>`Start-ThreadJob` gebruiken

De **ThreadJob** -module wordt eerst geleverd met Power shell 6. Het kan ook worden geïnstalleerd via de PowerShell Gallery voor Windows Power shell 5,1.

Als u een thread-taak op de lokale computer wilt starten, gebruikt u de `Start-ThreadJob` cmdlet met een opdracht of een script dat is inge sloten in accolades ( `{ }` ).

In het volgende voor beeld wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` op de lokale computer.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

`Start-ThreadJob`Met de opdracht wordt een `ThreadJob` object geretourneerd dat de actieve taak vertegenwoordigt. Het taak object bevat nuttige informatie over de taak, inclusief de huidige uitvoerings status. De resultaten van de taak worden verzameld wanneer de resultaten worden gegenereerd.

### <a name="using-foreach-object--parallel--asjob"></a>`ForEach-Object -Parallel -AsJob` gebruiken

Power shell 7,0 een nieuwe para meter is toegevoegd aan de `ForEach-Object` cmdlet. Met de nieuwe para meters kunt u script blokken uitvoeren in parallelle threads als Power shell-taken.

U kunt gegevens door sluizen naar `ForEach-Object -Parallel` . De gegevens worden door gegeven aan het script blok dat parallel wordt uitgevoerd. De `-AsJob` para meter maakt taken objecten voor elk van de parallelle threads.

Met de volgende opdracht wordt een taak gestart die onderliggende taken bevat voor elke invoer waarde die is opgenomen in de opdracht. Elke onderliggende taak voert de `Write-Output` opdracht uit met een gesluisde invoer waarde als het argument.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

`ForEach-Object -Parallel`Met de opdracht wordt een `PSTaskJob` object geretourneerd dat onderliggende taken bevat voor elke invoer waarde van de pijp lijn. Het taak object bevat nuttige informatie over de uitvoerings status van de onderliggende taken. De resultaten van de onderliggende taken worden verzameld wanneer de resultaten worden gegenereerd.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>Wachten tot een taak is voltooid en taak resultaten ophalen

U kunt Power shell-taak-cmdlets gebruiken, zoals `Wait-Job` en `Receive-Job` wachten tot een taak is voltooid en vervolgens alle resultaten retour neren die zijn gegenereerd door de taak.

Met de volgende opdracht wordt een thread taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` , wordt gewacht tot de opdracht is voltooid en worden alle gegevens resultaten weer gegeven die zijn gegenereerd door de opdracht.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

Met de volgende opdracht wordt een taak gestart die een `Write-Output` opdracht uitvoert voor elke gepipede invoer, wordt gewacht tot alle onderliggende taken zijn voltooid en worden alle gegevens resultaten geretourneerd die zijn gegenereerd door de onderliggende taken.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

`Receive-Job`Met de cmdlet worden de resultaten van de onderliggende taken geretourneerd.

```powershell
1
3
2
4
5
```

Omdat elke onderliggende taak parallel wordt uitgevoerd, wordt de volg orde van de gegenereerde resultaten niet gegarandeerd.

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
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

In het eerste voor beeld ziet u een foreach-lus waarmee 1000-thread taken worden gemaakt voor het schrijven van eenvoudige teken reeksen. Als gevolg van de taak overhead duurt het meer dan 36 seconden om te volt ooien.

In het tweede voor beeld wordt de `ForEach` cmdlet uitgevoerd om dezelfde 1000 bewerkingen uit te voeren.
Deze tijd `ForEach-Object` wordt opeenvolgend uitgevoerd op één thread, zonder dat er taak overhead nodig is. Deze is in een paar 7 milliseconden voltooid.

In het volgende voor beeld worden Maxi maal 5000 vermeldingen verzameld voor 10 afzonderlijke systeem Logboeken. Omdat het script een aantal logboeken moet lezen, is het zinvol om de bewerkingen parallel uit te voeren.

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

Het script wordt voltooid in de helft van het tijdstip waarop de taken parallel worden uitgevoerd.

```powershell
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

## <a name="thread-jobs-and-variables"></a>Thread-taken en-variabelen

Er zijn meerdere manieren om waarden door te geven aan de thread-gebaseerde taken.

`Start-ThreadJob` kan variabelen accepteren die worden verzonden naar de cmdlet, door gegeven aan het script blok via het `$using` sleutel woord of door gegeven via de para meter **argument List** .

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

`ForEach-Object -Parallel` accepteert pipes in variabelen en variabelen die rechtstreeks aan het script blok worden door gegeven via het `$using` sleutel woord.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

Omdat thread-taken in hetzelfde proces worden uitgevoerd, moet elk referentie type dat naar de taak wordt door gegeven, zorgvuldig worden behandeld. Als het geen thread-safe object is, mag het nooit worden toegewezen aan en moet de methode en eigenschappen nooit worden aangeroepen.

In het volgende voor beeld wordt een thread-safe .NET-object door gegeven `ConcurrentDictionary` aan alle onderliggende taken om unieke benoemde proces objecten te verzamelen. Omdat het een thread-safe object is, kan het veilig worden gebruikt terwijl de taken gelijktijdig in het proces worden uitgevoerd.

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
