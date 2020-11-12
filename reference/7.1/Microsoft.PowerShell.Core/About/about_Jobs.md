---
description: Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: d4d4f4b8a2f57edcfa72247d9f9bc224b848789a
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524770"
---
# <a name="about-jobs"></a>Over taken

## <a name="short-description"></a>Korte beschrijving
Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.

## <a name="long-description"></a>Lange beschrijving

Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken. Er zijn drie typen taken die door Power shell worden geboden ter ondersteuning van gelijktijdigheid.

- `RemoteJob` -Opdrachten en scripts worden uitgevoerd op een externe sessie. Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.
- `BackgroundJob` -Opdrachten en scripts worden in een afzonderlijk proces op de lokale computer uitgevoerd.
- `PSTaskJob` of `ThreadJob` -opdrachten en scripts worden uitgevoerd in een afzonderlijke thread binnen hetzelfde proces op de lokale computer. Zie [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs)voor meer informatie.

Het uitvoeren van scripts op afstand, op een afzonderlijke machine of in een afzonderlijk proces, biedt een uitstekende isolatie. Fouten die optreden in de externe taak hebben geen invloed op andere actieve taken of de bovenliggende sessie die de taak heeft gestart. De externe laag voegt echter overhead toe, inclusief object serialisatie. Alle objecten worden geserialiseerd en gedeserialiseerd wanneer ze worden door gegeven tussen de bovenliggende sessie en de externe (taak) sessie. Serialisatie van grote complexe gegevens objecten kan grote hoeveel heden reken-en geheugen bronnen verbruiken en grote hoeveel heden gegevens via het netwerk overzetten.

Thread-gebaseerde taken zijn niet zo krachtig als externe en achtergrond taken, omdat ze in hetzelfde proces op verschillende threads worden uitgevoerd. Als één taak een kritieke fout heeft die het proces vastloopt, worden alle andere taken in het proces beëindigd.

Thread-gebaseerde taken vereisen echter minder overhead. Ze gebruiken geen externe laag of serialisatie. De resultaat objecten worden geretourneerd als verwijzingen naar live-objecten in de huidige sessie. Zonder deze overhead worden thread-gebaseerde taken sneller uitgevoerd en worden minder resources gebruikt dan de andere taak typen.

> [!IMPORTANT]
> Met de bovenliggende sessie die de taak heeft gemaakt, wordt ook de taak status bewaakt en worden de pijplijn gegevens verzameld. Het onderliggende proces van de taak wordt beëindigd door de bovenliggende bewerking zodra de taak de status voltooid heeft bereikt. Als de bovenliggende sessie wordt beëindigd, worden alle actieve onderliggende taken beëindigd samen met de onderliggende processen.

Er zijn twee manieren om deze situatie te omzeilen:

1. Gebruiken `Invoke-Command` om taken te maken die worden uitgevoerd in sessies zonder verbinding. Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie.
1. Gebruiken `Start-Process` om een nieuw proces te maken in plaats van een taak. Zie [start-process](xref:Microsoft.PowerShell.Management.Start-Process)(Engelstalig) voor meer informatie.

## <a name="the-job-cmdlets"></a>De taak-cmdlets

|Cmdlet          |Beschrijving                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |Hiermee wordt een achtergrond taak op een lokale computer gestart.           |
|`Get-Job`       |Hiermee worden de achtergrond taken opgehaald die zijn gestart in de      |
|                |huidige sessie.                                       |
|`Receive-Job`   |Hiermee worden de resultaten van achtergrond taken opgehaald.                   |
|`Stop-Job`      |Hiermee stopt u een achtergrond taak.                                |
|`Wait-Job`      |Onderdrukt de opdracht prompt totdat een of alle taken zijn|
|                |aangevuld.                                              |
|`Remove-Job`    |Hiermee verwijdert u een achtergrond taak.                              |
|`Invoke-Command`|Met de para meter **AsJob** maakt u een achtergrond taak op een  |
|                |externe computer. U kunt gebruiken `Invoke-Command` om uit te voeren   |
|                |elke taak opdracht op afstand, inclusief `Start-Job` .       |

## <a name="how-to-start-a-job-on-the-local-computer"></a>Een taak op de lokale computer starten

Als u een achtergrond taak op de lokale computer wilt starten, gebruikt u de `Start-Job` cmdlet.

Als u een `Start-Job` opdracht wilt schrijven, moet u de opdracht sluiten die de taak in accolades () wordt uitgevoerd `{}` . Gebruik de para meter **script Block** om de opdracht op te geven.

Met de volgende opdracht wordt een achtergrond taak gestart waarmee een opdracht wordt uitgevoerd `Get-Process` op de lokale computer.

```powershell
Start-Job -ScriptBlock {Get-Process}
```

Wanneer u een achtergrond taak start, wordt de opdracht prompt onmiddellijk geretourneerd, zelfs als de taak een lange tijd in beslag neemt. U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.

`Start-Job`Met de opdracht wordt een object geretourneerd dat de taak vertegenwoordigt. Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.

U kunt het taak object opslaan in een variabele en dit vervolgens gebruiken met de andere **taak** -cmdlets om de achtergrond taak te beheren. Met de volgende opdracht wordt een taak object gestart en wordt het resulterende taak object in de `$job` variabele opgeslagen.

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

Vanaf Power shell 6,0 kunt u de operator background ( `&` ) aan het einde van een pijp lijn gebruiken om een achtergrond taak te starten. Zie [achtergrond operator](about_Operators.md#background-operator-)voor meer informatie.

Het gebruik van de operator background is functioneel equivalent aan het gebruik `Start-Job` van de cmdlet in het vorige voor beeld.

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a>Taak objecten ophalen

De `Get-Job` cmdlet retourneert objecten die de achtergrond taken vertegenwoordigen die in de huidige sessie zijn gestart. Zonder para meters `Get-Job` retourneert alle taken die in de huidige sessie zijn gestart.

```powershell
Get-Job
```

Het taak object bevat de status van de taak, die aangeeft of de taak is voltooid. Een voltooide taak heeft de status **voltooid** of **mislukt**. Een taak kan ook worden **geblokkeerd** of **uitgevoerd**.

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

U kunt het taak object opslaan in een variabele en gebruiken om de taak te vertegenwoordigen in een latere opdracht. Met de volgende opdracht wordt de taak met ID 1 opgehaald en opgeslagen in de `$job` variabele.

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a>De resultaten van een taak ophalen

Wanneer u een achtergrond taak uitvoert, worden de resultaten niet onmiddellijk weer gegeven. Als u de resultaten van een achtergrond taak wilt weer geven, gebruikt u de `Receive-Job` cmdlet.

In het volgende voor beeld worden de `Receive-Job` resultaten van de taak met behulp van het taak object in de variabele opgehaald met de cmdlet `$job` .

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

U kunt de resultaten van een taak opslaan in een variabele. Met de volgende opdracht worden de resultaten van de taak in de variabele opgeslagen in `$job` de `$results` variabele.

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a>Gedeeltelijke taak resultaten ophalen en bewaren

De `Receive-Job` cmdlet haalt de resultaten van een achtergrond taak op. Als de taak is voltooid, worden `Receive-Job` alle taak resultaten opgehaald. Als de taak nog wordt uitgevoerd, worden `Receive-Job` de resultaten opgehaald die tot nu toe zijn gegenereerd. U kunt `Receive-Job` de opdrachten opnieuw uitvoeren om de resterende resultaten weer te geven.

`Receive-Job`De resultaten worden standaard verwijderd uit de cache waarin de taak resultaten worden opgeslagen. Wanneer u het `Receive-Job` opnieuw uitvoert, krijgt u alleen de nieuwe resultaten die na de eerste uitvoering zijn aangekomen.

Met de volgende opdrachten worden de resultaten weer gegeven van `Receive-Job` opdrachten die worden uitgevoerd voordat de taak is voltooid.

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

Gebruik de para meter **Keep** om te voor komen dat `Receive-Job` de geretourneerde taak resultaten worden verwijderd. Met de volgende opdrachten wordt het effect van het gebruik van de para meter **Keep** voor een taak die nog niet is voltooid weer gegeven.

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a>Wachten op de resultaten

Als u een opdracht uitvoert die veel tijd in beslag neemt, kunt u de eigenschappen van het taak object gebruiken om te bepalen wanneer de taak is voltooid. De volgende opdracht gebruikt het `Get-Job` object om alle achtergrond taken in de huidige sessie op te halen.

```powershell
Get-Job
```

De resultaten worden weer gegeven in een tabel. De status van de taak wordt weer gegeven in de kolom **status** .

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

In dit geval toont de **status** eigenschap dat taak 2 nog steeds wordt uitgevoerd. Als u de `Receive-Job` cmdlet nu wilt gebruiken om de resultaten van de taak te verkrijgen, zijn de resultaten niet volledig. U kunt de `Receive-Job` cmdlet herhaaldelijk gebruiken om alle resultaten op te halen. Gebruik de eigenschap **State** om te bepalen wanneer de taak is voltooid.

U kunt ook de **wait** -para meter van de `Receive-Job` cmdlet gebruiken. Wanneer u deze para meter gebruiken, wordt de opdracht prompt niet door de cmdlet geretourneerd totdat de taak is voltooid en alle resultaten beschikbaar zijn.

U kunt ook de `Wait-Job` cmdlet gebruiken om te wachten op de resultaten van de taak. `Wait-Job` Hiermee kunt u wachten op een of meer specifieke taak of voor alle taken.
De volgende opdracht gebruikt de `Wait-Job` cmdlet om te wachten op een taak met **id**
10.

```powershell
Wait-Job -ID 10
```

Als gevolg hiervan wordt de Power shell-prompt onderdrukt totdat de taak is voltooid.

U kunt ook wachten op een vooraf bepaalde periode. Met deze opdracht wordt de para meter **time-out** gebruikt om de wacht tijd van 120 seconden te beperken. Wanneer de tijd is verlopen, wordt de opdracht prompt weer gegeven, maar wordt de taak nog steeds op de achtergrond uitgevoerd.

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a>Een taak stoppen

Als u een achtergrond taak wilt stoppen, gebruikt u de `Stop-Job` cmdlet. Met de volgende opdracht wordt een taak gestart om elk item in het logboek voor systeem gebeurtenissen op te halen. Het taak object wordt opgeslagen in de `$job` variabele.

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

Met de volgende opdracht wordt de taak gestopt. Er wordt een pijplijn operator ( `|` ) gebruikt om de taak in de `$job` variabele naar te verzenden `Stop-Job` .

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a>Een taak verwijderen

Als u een achtergrond taak wilt verwijderen, gebruikt u de `Remove-Job` cmdlet. Met de volgende opdracht wordt de taak verwijderd uit de `$job` variabele.

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a>Een mislukte taak onderzoeken

Taken kunnen om verschillende redenen mislukken. het taak object bevat een eigenschap **reason** die informatie bevat over de oorzaak van de fout.

In het volgende voor beeld wordt een taak gestart zonder de vereiste referenties.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

Controleer de eigenschap **reason** om de fout te vinden waardoor de taak is mislukt.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

In dit geval is de taak mislukt, omdat de externe computer expliciete referenties vereist om de opdracht uit te voeren. De eigenschap **reason** bevat het volgende bericht:

> Verbinding maken met de externe server is mislukt met het volgende fout bericht: de toegang is geweigerd.

## <a name="see-also"></a>Zie tevens

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
- [Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)
