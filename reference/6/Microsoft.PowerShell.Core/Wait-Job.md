---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 35a70c24b3bc93a64daa0d20df7fa5b6ff9e53d6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251217"
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

De **wacht opdracht-** cmdlet wacht totdat de Power shell-achtergrond taken zijn voltooid, voordat de-prompt wordt weer gegeven.
U kunt wachten tot een wille keurige achtergrond taak is voltooid of totdat alle achtergrond taken zijn voltooid en u een maximale wacht tijd voor de taak kunt instellen.

Wanneer de opdrachten in de taak zijn voltooid, wordt de opdracht prompt weer gegeven **en wordt een** taak object geretourneerd, zodat u het kunt door sluizen naar een andere opdracht.

U kunt de cmdlet **wacht opdracht** gebruiken om te wachten op achtergrond taken, zoals die zijn gestart met behulp van de cmdlet Start-Job of de para meter *AsJob* van de cmdlet Invoke-Command.
Zie about_Jobs voor meer informatie over Power shell-achtergrond taken.

Vanaf Windows Power Shell 3,0 wacht de cmdlet **wait-job** ook op aangepaste taak typen, zoals werk stroom taken en exemplaren van geplande taken.
Als u **wacht** op taken van een bepaald type wilt wachten, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u de cmdlet Get-Job uitvoert, met behulp van de Import-Module cmdlet of door een cmdlet in de module te gebruiken of op te halen.
Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.

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

In dit voor beeld ziet u hoe u de cmdlet **wait-job** gebruikt met taken die zijn gestart op externe computers met behulp van de cmdlet **Start-job** .
De opdrachten **Start-job** en **wait-job** worden verzonden naar de externe computer met behulp van de cmdlet **invoke-opdracht** .

In dit voor beeld wordt **wacht taak** gebruikt om te bepalen of een Get-Date-opdracht die als achtergrond taak wordt uitgevoerd op drie verschillende computers is voltooid.

Met de eerste opdracht maakt u een Power shell-sessie ( **PSSession** ) op elk van de drie externe computers en slaat u deze op in de variabele $s.

Met de tweede opdracht wordt **invoke-opdracht** gebruikt voor het uitvoeren van **Start-taak** in elk van de drie sessies in $s.
Alle taken hebben de naam Datum1.

De derde opdracht maakt gebruik van de **opdracht invoke** om een **wachtende taak** uit te voeren.
Met deze opdracht wordt gewacht op de Datum1-taken op elke computer om te volt ooien.
De resulterende verzameling (matrix) van taak objecten wordt opgeslagen in de variabele $done.

De vierde opdracht gebruikt de eigenschap **Count** van de matrix met taak objecten in de variabele $Done om te bepalen hoeveel taken zijn voltooid.

### Voor beeld 3: bepalen wanneer de eerste achtergrond taak is voltooid

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

In dit voor beeld wordt de para meter van *een* **wachtende taak** gebruikt om te bepalen wanneer de eerste van de vele achtergrond taken die in de huidige sessie worden uitgevoerd, zijn voltooid.
U ziet ook hoe u de cmdlet **wait-job** gebruikt om te wachten tot externe taken zijn voltooid.

Met de eerste opdracht maakt u een **PSSession** op elke computer die wordt vermeld in het Machines.txt-bestand en worden de **PSSession** -objecten opgeslagen in de variabele $s.
De opdracht gebruikt de cmdlet Get-Content om de inhoud van het bestand op te halen.
De opdracht **Get-content** bevindt zich tussen haakjes om ervoor te zorgen dat deze wordt uitgevoerd vóór de opdracht New-PSSession.

Met de tweede opdracht wordt een teken reeks voor de opdracht **get-eventlog** opgeslagen, tussen aanhalings tekens in de variabele $c.

De derde opdracht maakt gebruik van Invoke-Command cmdlet om **Start-taak** uit te voeren in elk van de sessies in $s.
Met de opdracht **Start-job** wordt een achtergrond taak gestart waarmee de opdracht **get-eventlog** wordt uitgevoerd in de variabele $c.

De opdracht gebruikt de aanpassings functie voor het **gebruik** van het bereik om aan te geven dat de variabele $c op de lokale computer is gedefinieerd.
De aanpassings functie voor het **gebruik** van scopes is geïntroduceerd in Windows power Shell 3,0.
Zie [about_Remote_Variables](about/about_Remote_Variables.md)voor meer informatie **over de aanpassing van het** bereik.

De vierde opdracht gebruikt **invoke-opdracht** om een **wacht** opdracht uit te voeren in de sessies.
De *para meter* wordt gebruikt om te wachten tot de eerste taak op de externe computers is voltooid.

### Voor beeld 4: een wacht tijd instellen voor taken op externe computers

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

In dit voor beeld ziet u hoe u de para meter *time-out* van **wacht taak** gebruikt om een maximale wacht tijd in te stellen voor de taken die worden uitgevoerd op externe computers.

Met de eerste opdracht maakt u een **PSSession** op elk van de drie externe computers (Server01, Server02 en Server03), waarna de **PSSession** -objecten worden opgeslagen in de variabele $s.

De tweede opdracht maakt gebruik van **invoke-opdracht** voor het uitvoeren van **Start-taak** in elk van de **PSSession** -objecten in $s.
De resulterende taak objecten worden opgeslagen in de variabele $jobs.

De derde opdracht gebruikt **invoke-opdracht** voor het uitvoeren van een **wachtende taak** in elk van de sessies in $s.
De opdracht **wachten** bepaalt of alle opdrachten binnen 30 seconden zijn voltooid.
Hierbij wordt de para meter *time-out* met de waarde 30 gebruikt voor het instellen van de maximale wacht tijd en worden de resultaten van de opdracht opgeslagen in de variabele $done.

In dit geval, na 30 seconden, is alleen de opdracht op de Server02 computer voltooid.
**Wacht taak** eindigt de wacht tijd, geeft de opdracht prompt en retourneert het object dat de voltooide taak vertegenwoordigt.

De variabele $done bevat een taak object dat de taak vertegenwoordigt die is uitgevoerd op Server02.

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

Met deze opdracht wordt 120 seconden (twee minuten) gewacht totdat de DailyLog-taak is voltooid.
Als de taak niet in de volgende twee minuten wordt voltooid, wordt de opdracht prompt toch geretourneerd en wordt de taak op de achtergrond uitgevoerd.

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

In dit voor beeld ziet u hoe u de cmdlet **wait-job** gebruikt met taken die zijn gestart op de lokale computer met behulp van **Start-job**.

Met deze opdrachten wordt een taak gestart waarmee de Power shell-script bestanden worden opgehaald die in de afgelopen week zijn toegevoegd of bijgewerkt.

De eerste opdracht maakt gebruik van **Start-taak** om een achtergrond taak op de lokale computer te starten.
De taak voert een Get-ChildItem-opdracht uit waarmee alle bestanden met de bestandsnaam extensie. ps1 die in de afgelopen week zijn toegevoegd of bijgewerkt, worden opgehaald.

De derde opdracht gebruikt **wacht tijden** om te wachten tot de taak is voltooid.
Wanneer de taak is voltooid, wordt met de opdracht het taak object weer gegeven, dat informatie over de taak bevat.

### Voor beeld 9: wachten op taken die zijn gestart op externe computers met behulp van Invoke-Command

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

In dit voor beeld ziet u hoe u **wacht** opdrachten gebruikt met taken die zijn gestart op externe computers met behulp van de para meter *AsJob* van **invoke-Command**.
Wanneer u *AsJob* gebruikt, wordt de taak op de lokale computer gemaakt en worden de resultaten automatisch naar de lokale computer geretourneerd, zelfs als de taak wordt uitgevoerd op de externe computers.

In dit voor beeld wordt **wacht taak** gebruikt om te bepalen of een **Get-process-** opdracht die wordt uitgevoerd in de sessies op drie externe computers, is voltooid.

Met de eerste opdracht worden **PSSession** -objecten op drie computers gemaakt en opgeslagen in de variabele $s.

De tweede opdracht gebruikt u **invoke-opdracht** voor het uitvoeren van **Get-process** in elk van de drie sessies in $s.
De opdracht gebruikt de para meter *AsJob* om de opdracht asynchroon uit te voeren als een achtergrond taak.
De opdracht retourneert een taak object, net zoals de taken die zijn gestart met behulp van **Start taak** en het taak object wordt opgeslagen in de variabele $j.

De derde opdracht maakt gebruik van een pijplijn operator (|) om het taak object in $j te verzenden naar de cmdlet **wait-job** .
Een opdracht **invoke-opdracht** is in dit geval niet vereist omdat de taak zich op de lokale computer bevindt.

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

Geeft aan dat met deze cmdlet de opdracht prompt wordt weer gegeven en het taak object als resultaat wordt gegeven wanneer een taak is voltooid.
**Wacht** totdat alle opgegeven taken zijn voltooid, wordt standaard gewacht voordat de prompt wordt weer gegeven.

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

Hiermee geeft u een hash-tabel met voor waarden op.
Met deze cmdlet wordt gewacht op taken die voldoen aan alle voor waarden in de hash-tabel.
Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.

Deze para meter werkt alleen voor aangepaste taak typen, zoals werk stroom taken en geplande taken.
Deze functie werkt niet op standaard achtergrond taken, zoals die zijn gemaakt met behulp van de cmdlet **Start-job** .
Zie het Help-onderwerp voor het taak type voor meer informatie over de ondersteuning voor deze para meter.

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

Hiermee wordt aangegeven dat deze cmdlet blijft wachten op taken met de status onderbroken of niet verbonden.
Standaard retourneert een **wacht opdracht** of de wacht tijd wanneer taken een van de volgende statussen hebben:

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

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.
Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.
U kunt een of meer Id's typen, gescheiden door komma's.
Als u de ID van een taak wilt zoeken, typt u `Get-Job` .

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

Hiermee geeft u een matrix met exemplaar-Id's op van taken waarvoor deze cmdlet wacht.
De standaard waarde is alle taken.

Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.
Gebruik **Get-job** om de exemplaar-id van een taak te vinden.

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

Hiermee geeft u de taken op waarvoor deze cmdlet wacht.
Voer een variabele in die de taak objecten bevat of een opdracht waarmee de taak objecten worden opgehaald.
U kunt ook een pijplijn operator gebruiken om taak objecten te verzenden naar de cmdlet **wait-job** .
Standaard **wacht een wachten op** alle taken die in de huidige sessie zijn gemaakt.

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

Hiermee geeft u een taak status op.
Met deze cmdlet wordt alleen gewacht op taken in de opgegeven status.
De aanvaardbare waarden voor deze parameter zijn:

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

Zie [JobState Enumeration (Engelstalig)](https://msdn.microsoft.com/library/system.management.automation.jobstate) in de MSDN-bibliotheek voor meer informatie over de status van de taak.

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

Hiermee geeft u de maximale wacht tijd op voor elke achtergrond taak, in seconden.
De standaard waarde-1 geeft aan dat de cmdlet wacht totdat de taak is voltooid.
De tijds duur begint wanneer u de opdracht **wacht** op te sturen, niet de opdracht **Start-job** .

Als deze tijd wordt overschreden, worden de wacht tijden beëindigd en wordt de opdracht prompt weer gegeven, zelfs als de taak nog steeds wordt uitgevoerd.
Met de opdracht wordt geen fout bericht weer gegeven.

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

Met deze cmdlet worden taak objecten geretourneerd die de voltooide taken vertegenwoordigen.
Als de wacht tijd eindigt omdat de waarde van de para meter *time-out* is overschreden, worden er geen objecten geretourneerd met een **wacht opdracht** .

## OPMERKINGEN

* Standaard retourneert een **wacht opdracht** of de wacht tijd wanneer taken een van de volgende statussen hebben:

- Voltooid
- Mislukt
- Gestopt
- Onderbroken
- De verbinding met de directe **wacht taak** is verbroken. Als u wilt blijven wachten op onderbroken en verbroken taken, gebruikt u de para meter *Force* .

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Invoke-opdracht](Invoke-Command.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)
