---
description: Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 6668e8a060c2468a4c7d98f52c7d493e1751970b
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/17/2020
ms.locfileid: "93253072"
---
# <a name="about-jobs"></a>Over taken

## <a name="short-description"></a>Korte beschrijving
Bevat informatie over de manier waarop Power shell-achtergrond taken een opdracht of expressie op de achtergrond uitvoeren zonder interactie met de huidige sessie.

## <a name="long-description"></a>Lange beschrijving

Met Power shell worden opdrachten en scripts gelijktijdig uitgevoerd via taken. Power shell biedt drie oplossingen op basis van taken voor ondersteuning van gelijktijdigheid.

|Taak            |Beschrijving                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |Opdracht en script worden uitgevoerd op een externe computer.                 |
|`BackgroundJob`|Opdracht en script worden uitgevoerd in een afzonderlijk proces op de lokale    |
|               |machine.                                                     |
|`ThreadJob`    |Opdracht en script worden uitgevoerd in een afzonderlijke thread binnen hetzelfde  |
|               |verwerken op de lokale computer.                                |

Elk type taak heeft voor delen en nadelen. Het uitvoeren van een script op afstand op een afzonderlijke machine of in een afzonderlijk proces heeft een goede isolatie. Fouten zijn niet van invloed op andere actieve taken of de client die de taak heeft gestart. Maar de externe laag voegt overhead toe, inclusief object serialisatie. Alle objecten die zijn door gegeven aan en van de externe sessie, moeten worden geserialiseerd en vervolgens worden gedeserialiseerd wanneer deze tussen de client en de doel sessie worden door gegeven. De serialisatie-bewerking kan veel reken-en geheugen bronnen gebruiken voor grote complexe gegevens objecten.

In dit onderwerp wordt uitgelegd hoe u achtergrond taken uitvoert in Power shell op een lokale computer. Zie [about_Remote_Jobs](about_Remote_Jobs.md)voor meer informatie over het uitvoeren van achtergrond taken op externe computers. Zie [about_Thread_Jobs](about_Thread_Jobs.md)voor meer informatie over thread taken.

Wanneer u een achtergrond taak start, wordt de opdracht prompt onmiddellijk geretourneerd, zelfs als de taak een lange tijd in beslag neemt. U kunt zonder onderbreking in de sessie blijven werken terwijl de taak wordt uitgevoerd.

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

`Start-Job`Met de opdracht wordt een object geretourneerd dat de taak vertegenwoordigt. Het taak object bevat nuttige informatie over de taak, maar bevat geen taak resultaten.

Sla het taak object op in een variabele en gebruik het vervolgens met de andere taak-cmdlets om de achtergrond taak te beheren. Met de volgende opdracht wordt een taak object gestart en wordt het resulterende taak object in de `$job` variabele opgeslagen.

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

Vanaf Power shell 6,0 kunt u een amersand ( `&` ) aan het einde van een pijp lijn gebruiken om een achtergrond taak te starten. De volgende opdracht is functioneel gelijk aan de bovenstaande opdracht.

```powershell
$job = Get-Process &
```

Het en-teken ( `&` ) wordt de operator achtergrond genoemd. Zie [achtergrond operator](about_Operators.md#background-operator-)voor meer informatie.

U kunt ook de- `Get-Job` cmdlet gebruiken om objecten op te halen die de taken vertegenwoordigen die in de huidige sessie zijn gestart. `Get-Job` retourneert hetzelfde taak object dat `Start-Job` retourneert.

## <a name="getting-job-objects"></a>Taak objecten ophalen

Als u object wilt ophalen dat de achtergrond taken vertegenwoordigt die in de huidige sessie zijn gestart, gebruikt u de `Get-Job` cmdlet. Zonder para meters `Get-Job` retourneert alle taken die in de huidige sessie zijn gestart.

Met de volgende opdracht worden bijvoorbeeld de taken in de huidige sessie opgehaald.

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

U kunt het taak object ook opslaan in een variabele en gebruiken om de taak te vertegenwoordigen in een latere opdracht. Met de volgende opdracht wordt de taak met ID 1 opgehaald en opgeslagen in de `$job` variabele.

```powershell
$job = Get-Job -Id 1
```

Het taak object bevat de status van de taak, die aangeeft of de taak is voltooid. Een voltooide taak heeft de status **voltooid** of **mislukt**. Een taak kan ook worden **geblokkeerd** of **uitgevoerd**.

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a>De resultaten van een taak ophalen

Wanneer u een achtergrond taak uitvoert, worden de resultaten niet onmiddellijk weer gegeven. In plaats daarvan `Start-Job` retourneert de cmdlet een taak object dat de taak vertegenwoordigt, maar bevat het geen resultaten. Als u de resultaten van een achtergrond taak wilt weer geven, gebruikt u de `Receive-Job` cmdlet.

De volgende opdracht gebruikt de `Receive-Job` cmdlet om de resultaten van de taak op te halen. Er wordt een taak object gebruikt dat in de variabele is opgeslagen `$job` om de taak te identificeren.

```powershell
Receive-Job -Job $job
```

`Receive-Job`Met de cmdlet worden de resultaten van de taak geretourneerd.

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

U kunt de resultaten van een taak ook opslaan in een variabele. Met de volgende opdracht worden de resultaten van de taak in de variabele opgeslagen in `$job` de `$results` variabele.

```powershell
$results = Receive-Job -Job $job
```

En u kunt de resultaten van de taak opslaan in een bestand met behulp van de omleidings operator ( `>` ) of de `Out-File` cmdlet. De volgende opdracht maakt gebruik van de omleidings operator om de resultaten van de taak in de `$job` variabele in het bestand op te slaan `Results.txt` .

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a>Gedeeltelijke taak resultaten ophalen en bewaren

De `Receive-Job` cmdlet haalt de resultaten van een achtergrond taak op. Als de taak is voltooid, worden `Receive-Job` alle taak resultaten opgehaald. Als de taak nog wordt uitgevoerd, worden `Receive-Job` de resultaten opgehaald die tot nu toe zijn gegenereerd. U kunt `Receive-Job` de opdrachten opnieuw uitvoeren om de resterende resultaten weer te geven.

Wanneer `Receive-Job` de resultaten worden geretourneerd, worden deze resultaten standaard verwijderd uit de cache waarin de taak resultaten worden opgeslagen. Als u een andere `Receive-Job` opdracht uitvoert, worden alleen de resultaten weer geven die nog niet zijn ontvangen.

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

Als u wilt voor komen `Receive-Job` dat de taak resultaten worden verwijderd die zijn geretourneerd, gebruikt u de para meter **Keep** . Als gevolg hiervan worden `Receive-Job` alle resultaten geretourneerd die tot dat moment zijn gegenereerd.

Met de volgende opdrachten wordt het effect van het gebruik van de para meter **Keep** voor een taak die nog niet is voltooid weer gegeven.

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

## <a name="waiting-for-the-results"></a>Wachten op de resultaten

Als u een opdracht uitvoert die veel tijd in beslag neemt, kunt u de eigenschappen van het taak object gebruiken om te bepalen wanneer de taak is voltooid. De volgende opdracht gebruikt het `Get-Job` object om alle achtergrond taken in de huidige sessie op te halen.

```powershell
Get-Job
```

De resultaten worden weer gegeven in een tabel. De status van de taak wordt weer gegeven in de kolom **status** .

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

In dit geval toont de status eigenschap dat taak 2 nog steeds wordt uitgevoerd. Als u de `Receive-Job` cmdlet nu wilt gebruiken om de resultaten van de taak te verkrijgen, zijn de resultaten niet volledig. U kunt de `Receive-Job` cmdlet herhaaldelijk gebruiken om alle resultaten op te halen. Elke keer dat u deze gebruikt, ontvangt u standaard alleen de resultaten die nog niet zijn ontvangen, maar u kunt de para meter **behouden** van de `Receive-Job` cmdlet gebruiken om de resultaten te bewaren, zelfs als deze al zijn ontvangen.

U kunt de gedeeltelijke resultaten naar een bestand schrijven en vervolgens nieuwere resultaten toevoegen wanneer ze binnenkomen of u kunt wachten en de status van de taak later controleren.

U kunt de **wait** -para meter van de `Receive-Job` cmdlet gebruiken. de opdracht prompt wordt niet geretourneerd totdat de taak is voltooid en alle resultaten beschikbaar zijn.

U kunt ook de `Wait-Job` cmdlet gebruiken om te wachten op de resultaten van de taak. `Wait-Job` Hiermee kunt u wachten op een bepaalde taak, voor alle taken of voor het volt ooien van de taken.

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

Als u wilt weten waarom een taak is mislukt, gebruikt u de eigenschap **reason** van het object taak.

Met de volgende opdracht wordt een taak gestart zonder de vereiste referenties. Het taak object wordt opgeslagen in de `$job` variabele.

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

De volgende opdracht gebruikt de eigenschap Reason om de fout te vinden waardoor de taak is mislukt.

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

In dit geval is de taak mislukt, omdat de externe computer expliciete referenties vereist om de opdracht uit te voeren. De waarde van de eigenschap **reason** is:

Verbinding maken met de externe server is mislukt met het volgende fout bericht: de toegang is geweigerd.

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
- [Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)
