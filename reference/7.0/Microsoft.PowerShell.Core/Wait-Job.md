---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 2eeacf8703dbe0f662d0b26d405c605d21c2b84e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390351"
---
# Wait-Job

## SAMENVATTING
Onderdrukt de opdracht prompt totdat een of alle Power shell-achtergrond taken die in de sessie worden uitgevoerd, zijn voltooid.

## SYNTAXIS

### SessionIdParameterSet (standaard)

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### JobParameterSet

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### NameParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### InstanceIdParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### StateParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### FilterParameterSet

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## BESCHRIJVING

De `Wait-Job` cmdlet wacht tot de Power shell-achtergrond taken zijn voltooid voordat de opdracht prompt wordt weer gegeven. U kunt wachten tot een wille keurige achtergrond taak is voltooid of totdat alle achtergrond taken zijn voltooid en u een maximale wacht tijd voor de taak kunt instellen.

Wanneer de opdrachten in de taak zijn voltooid, `Wait-Job` wordt de opdracht prompt weer gegeven en wordt een taak object geretourneerd, zodat u het kunt door sluizen naar een andere opdracht.

U kunt `Wait-Job` de cmdlet gebruiken om te wachten op achtergrond taken, zoals die zijn gestart met behulp `Start-Job` van de cmdlet of de para meter **AsJob** van de `Invoke-Command` cmdlet. Zie [about_Jobs](./about/about_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.

Vanaf Windows Power Shell 3,0 wacht de `Wait-Job` cmdlet ook op aangepaste taak typen, zoals werk stroom taken en exemplaren van geplande taken. Als u `Wait-Job` wilt wachten op taken van een bepaald type, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u de `Get-Job` cmdlet uitvoert, hetzij met behulp van de `Import-Module` cmdlet of door een cmdlet in de module te gebruiken of op te halen. Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.

## VOORBEELDEN

### Voor beeld 1: wachten op alle taken

```powershell
Get-Job | Wait-Job
```

Met deze opdracht wordt gewacht tot alle achtergrond taken die in de sessie worden uitgevoerd, worden voltooid.

### Voor beeld 2: wachten op taken die zijn gestart op externe computers met behulp van Start-Job

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

In dit voor beeld ziet u hoe u de `Wait-Job` cmdlet gebruikt met taken die zijn gestart op externe computers met behulp van de- `Start-Job` cmdlet. Zowel `Start-Job` als- `Wait-Job` opdrachten worden naar de externe computer verzonden met behulp van de- `Invoke-Command` cmdlet.

In dit voor beeld wordt gebruikt `Wait-Job` om te bepalen of een `Get-Date` opdracht die wordt uitgevoerd als achtergrond taak op drie verschillende computers is voltooid.

Met de eerste opdracht maakt u een Windows Power shell-sessie ( **PSSession** ) op elk van de drie externe computers en slaat u deze op in de `$s` variabele.

De tweede opdracht wordt gebruikt `Invoke-Command` om `Start-Job` in elk van de drie sessies in te worden uitgevoerd `$s` .
Alle taken hebben de naam Datum1.

De derde opdracht wordt gebruikt `Invoke-Command` om uit te voeren `Wait-Job` . Met deze opdracht wordt gewacht op de Datum1-taken op elke computer om te volt ooien. De resulterende verzameling (matrix) van taak objecten wordt opgeslagen in de `$done` variabele.

De vierde opdracht gebruikt de eigenschap **Count** van de matrix met taak objecten in de `$done` variabele om te bepalen hoeveel taken zijn voltooid.

### Voor beeld 3: bepalen wanneer de eerste achtergrond taak is voltooid

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

In dit voor beeld wordt **de para meter** van gebruikt `Wait-Job` om te bepalen wanneer de eerste van de vele achtergrond taken die in de huidige sessie worden uitgevoerd, zijn voltooid. U ziet ook hoe u de cmdlet kunt gebruiken `Wait-Job` om te wachten tot externe taken zijn voltooid.

Met de eerste opdracht maakt u een **PSSession** op elke computer die wordt vermeld in het Machines.txt-bestand en worden de **PSSession** -objecten opgeslagen in de `$s` variabele. De opdracht gebruikt de `Get-Content` cmdlet om de inhoud van het bestand op te halen. De `Get-Content` opdracht bevindt zich tussen haakjes om er zeker van te zijn dat deze vóór de opdracht wordt uitgevoerd `New-PSSession` .

Met de tweede opdracht `Get-EventLog` wordt een opdracht reeks opgeslagen tussen aanhalings tekens in de `$c` variabele.

De derde opdracht gebruikt `Invoke-Command` cmdlet om uit te voeren `Start-Job` in elk van de sessies in `$s` .
`Start-Job`Met de opdracht wordt een achtergrond taak gestart waarmee de opdracht wordt uitgevoerd `Get-EventLog` in de `$c` variabele.

De opdracht gebruikt de aanpassings functie voor het **gebruik** van het bereik om aan te geven dat de `$c` variabele op de lokale computer is gedefinieerd. De aanpassings functie voor het **gebruik** van scopes is geïntroduceerd in Windows power Shell 3,0. Zie [about_Remote_Variables](./about/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.

De vierde opdracht wordt gebruikt `Invoke-Command` om een opdracht uit te voeren `Wait-Job` in de sessies. De **para meter** wordt gebruikt om te wachten tot de eerste taak op de externe computers is voltooid.

### Voor beeld 4: een wacht tijd instellen voor taken op externe computers

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

In dit voor beeld ziet u hoe u de para meter **time-out** van gebruikt `Wait-Job` om een maximale wacht tijd in te stellen voor de taken die worden uitgevoerd op externe computers.

Met de eerste opdracht maakt u een **PSSession** op elk van de drie externe computers (Server01, Server02 en Server03), waarna de **PSSession** -objecten worden opgeslagen in de `$s` variabele.

De tweede opdracht wordt gebruikt `Invoke-Command` om `Start-Job` in elk van de **PSSession** -objecten in te worden uitgevoerd `$s` . De resulterende taak objecten worden opgeslagen in de `$jobs` variabele.

De derde opdracht wordt gebruikt `Invoke-Command` om `Wait-Job` in elk van de sessies in te worden uitgevoerd `$s` . De `Wait-Job` opdracht bepaalt of alle opdrachten binnen 30 seconden zijn voltooid. De para meter **time-out** met de waarde 30 wordt gebruikt om de maximale wacht tijd te bepalen en vervolgens de resultaten van de opdracht in de variabele op te slaan `$done` .

In dit geval, na 30 seconden, is alleen de opdracht op de Server02 computer voltooid. `Wait-Job` de wacht tijd wordt beëindigd, de opdracht prompt wordt weer gegeven en het object wordt geretourneerd dat de voltooide taak vertegenwoordigt.

De `$done` variabele bevat een taak object dat de taak vertegenwoordigt die is uitgevoerd op Server02.

### Voor beeld 5: wachten tot een van de taken is voltooid

```powershell
Wait-Job -id 1,2,5 -Any
```

Met deze opdracht worden drie taken geïdentificeerd op basis van hun Id's en wordt gewacht totdat een van deze opdrachten is voltooid.
De opdracht prompt wordt weer gegeven wanneer de eerste taak is voltooid.

### Voor beeld 6: wachten op een periode, waarna de taak op de achtergrond kan worden voortgezet

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

Met deze opdracht wordt 120 seconden (twee minuten) gewacht totdat de DailyLog-taak is voltooid. Als de taak niet in de volgende twee minuten wordt voltooid, wordt de opdracht prompt toch geretourneerd en wordt de taak op de achtergrond uitgevoerd.

### Voor beeld 7: wachten op een taak op naam

```powershell
Wait-Job -Name "Job3"
```

Met deze opdracht wordt de taak naam gebruikt om de taak te identificeren waarvoor moet worden gewacht.

### Voor beeld 8: wachten op taken op de lokale computer die is gestart met Start-Job

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

In dit voor beeld ziet u hoe u de `Wait-Job` cmdlet gebruikt met taken die zijn gestart op de lokale computer met behulp van `Start-Job` .

Met deze opdrachten wordt een taak gestart waarmee de Windows Power shell-script bestanden worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.

De eerste opdracht wordt gebruikt `Start-Job` om een achtergrond taak op de lokale computer te starten. Met de taak wordt een `Get-ChildItem` opdracht uitgevoerd waarmee alle bestanden met de bestandsnaam extensie. ps1 worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.

De derde opdracht wordt gebruikt `Wait-Job` om te wachten tot de taak is voltooid. Wanneer de taak is voltooid, wordt met de opdracht het taak object weer gegeven, dat informatie over de taak bevat.

### Voor beeld 9: wachten op taken die zijn gestart op externe computers met behulp van Invoke-Command

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

In dit voor beeld ziet u hoe u kunt gebruiken `Wait-Job` met taken die zijn gestart op externe computers met behulp van de para meter **AsJob** van `Invoke-Command` . Wanneer u **AsJob** gebruikt, wordt de taak op de lokale computer gemaakt en worden de resultaten automatisch naar de lokale computer geretourneerd, zelfs als de taak wordt uitgevoerd op de externe computers.

In dit voor beeld wordt gebruikt `Wait-Job` om te bepalen of een `Get-Process` opdracht die wordt uitgevoerd in de sessies op drie externe computers, is voltooid.

Met de eerste opdracht worden **PSSession** -objecten op drie computers gemaakt en opgeslagen in de `$s` variabele.

De tweede opdracht wordt gebruikt `Invoke-Command` om `Get-Process` in elk van de drie sessies in te worden uitgevoerd `$s` .
De opdracht gebruikt de para meter **AsJob** om de opdracht asynchroon uit te voeren als een achtergrond taak. De opdracht retourneert een taak object, net zoals de taken die met `Start-Job` worden gestart, en het taak object wordt opgeslagen in de `$j` variabele.

De derde opdracht maakt gebruik van een pijplijn operator ( `|` ) voor het verzenden van het taak object in `$j` naar de `Wait-Job` cmdlet. `Invoke-Command`In dit geval is een opdracht niet vereist, omdat de taak zich op de lokale computer bevindt.

### Voor beeld 10: wachten op een taak met een ID

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

Met deze opdracht wordt gewacht op de taak met de ID-waarde 1.

## PARAMETERS

### -Alle

Geeft aan dat met deze cmdlet de opdracht prompt wordt weer gegeven en het taak object als resultaat wordt gegeven wanneer een taak is voltooid. Standaard wordt `Wait-Job` gewacht totdat alle opgegeven taken zijn voltooid voordat de prompt wordt weer gegeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Hiermee geeft u een hash-tabel met voor waarden op. Met deze cmdlet wordt gewacht op taken die voldoen aan alle voor waarden in de hash-tabel. Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken. Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de `Start-Job` cmdlet. Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Hiermee wordt aangegeven dat deze cmdlet blijft wachten op taken met de status onderbroken of niet verbonden. `Wait-Job`Retourneert standaard of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:

- Voltooid
- Mislukt
- Gestopt
- Onderbroken
- Ontkoppeld

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u een matrix met Id's van taken op waarvoor deze cmdlet wacht.

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie. Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie. U kunt een of meer Id's typen, gescheiden door komma's. Als u de ID van een taak wilt zoeken, typt u `Get-Job` .

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u een matrix met exemplaar-Id's op van taken waarvoor deze cmdlet wacht. De standaard waarde is alle taken.

Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert. Gebruik om de exemplaar-ID van een taak te vinden `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Taak

Hiermee geeft u de taken op waarvoor deze cmdlet wacht. Voer een variabele in die de taak objecten bevat of een opdracht waarmee de taak objecten worden opgehaald. U kunt ook een pijplijn operator gebruiken om taak objecten te verzenden naar de `Wait-Job` cmdlet. Standaard wordt `Wait-Job` gewacht op alle taken die in de huidige sessie zijn gemaakt.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u beschrijvende namen van taken op waarvoor deze cmdlet wacht.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Status

Hiermee geeft u een taak status op. Met deze cmdlet wordt alleen gewacht op taken in de opgegeven status. De aanvaardbare waarden voor deze parameter zijn:

- NotStarted
- Wordt uitgevoerd
- Voltooid
- Mislukt
- Gestopt
- Geblokkeerd
- Onderbroken
- Ontkoppeld
- Onderbreken
- Stoppen

Zie [JobState Enumeration](/dotnet/api/system.management.automation.jobstate)(Engelstalig) voor meer informatie over de status van een taak.

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Time-out

Hiermee geeft u de maximale wacht tijd op voor elke achtergrond taak, in seconden. De standaard waarde-1 geeft aan dat de cmdlet wacht totdat de taak is voltooid. De tijds duur begint wanneer u de `Wait-Job` opdracht verzendt, niet de `Start-Job` opdracht.

Als deze tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de opdracht prompt weer gegeven, zelfs als de taak nog steeds wordt uitgevoerd. Met de opdracht wordt geen fout bericht weer gegeven.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. RemotingJob

U kunt een taak object door sluizen naar deze cmdlet.

## UITVOER

### System. Management. Automation. PSRemotingJob

Met deze cmdlet worden taak objecten geretourneerd die de voltooide taken vertegenwoordigen. Als de wacht tijd eindigt omdat de waarde van de para meter **time-out** is overschreden, `Wait-Job` worden er geen objecten geretourneerd.

## OPMERKINGEN

`Wait-Job`Retourneert standaard of beëindigt de wacht tijd wanneer taken een van de volgende statussen hebben:

- Voltooid
- Mislukt
- Gestopt
- Onderbroken
- De verbinding is verbroken zodat u `Wait-Job` verder kunt wachten op onderbroken en verbroken taken, gebruikt u de para meter **Force** .

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Invoke-opdracht](Invoke-Command.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)
