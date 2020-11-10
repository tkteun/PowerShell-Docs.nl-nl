---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 77982029240727ff5c7c90866d1a67cf7cae794d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391303"
---
# Stop-Job

## SAMENVATTING
Hiermee stopt u een Power shell-achtergrond taak.

## SYNTAXIS

### SessionIdParameterSet (standaard)

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Stop-Job` cmdlet stopt Power shell-achtergrond taken die worden uitgevoerd. U kunt deze cmdlet gebruiken om alle taken te stoppen of de geselecteerde taken te stoppen op basis van hun naam, ID, exemplaar-ID of status, of door een taak object door te geven aan `Stop-Job` .

U kunt gebruiken `Stop-Job` om achtergrond taken te stoppen, zoals die zijn gestart met behulp `Start-Job` van de cmdlet of de **AsJob** -para meter van een cmdlet. Wanneer u een achtergrond taak stopt, worden alle taken die in de taak wachtrij in behandeling zijn, door Power Shell voltooid en wordt de taak vervolgens beëindigd. Er worden geen nieuwe taken aan de wachtrij toegevoegd nadat deze opdracht is verzonden.

Met deze cmdlet worden geen achtergrond taken verwijderd. Als u een taak wilt verwijderen, gebruikt u de `Remove-Job` cmdlet.

Met ingang van Windows Power Shell 3,0 worden `Stop-Job` ook aangepaste taak typen gestopt, zoals werk stroom taken en exemplaren van geplande taken. Als u `Stop-Job` wilt inschakelen om een taak met een aangepast taak type te stoppen, importeert u de module die het aangepaste taak type ondersteunt in de sessie voordat u een `Stop-Job` opdracht uitvoert, met behulp van de `Import-Module` cmdlet of door een cmdlet in de module te gebruiken of op te halen. Zie de documentatie van de functie aangepast taak type voor meer informatie over een bepaald aangepast taak type.

## VOORBEELDEN

### Voor beeld 1: een taak stoppen op een externe computer met behulp van Invoke-Command

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

In dit voor beeld ziet u hoe u de cmdlet kunt gebruiken `Stop-Job` om een taak te stoppen die wordt uitgevoerd op een externe computer.

Omdat de taak is gestart met behulp van de `Invoke-Command` cmdlet om een opdracht op afstand uit te voeren `Start-Job` , wordt het taak object opgeslagen op de externe computer. U moet een andere `Invoke-Command` opdracht gebruiken om een `Stop-Job` opdracht op afstand uit te voeren. Zie about_Remote_Jobs voor meer informatie over externe achtergrond taken.

Met de eerste opdracht maakt u een Power shell-sessie ( **PSSession** ) op de Server01-computer. vervolgens slaat u het sessie object op in de `$s` variabele. De opdracht gebruikt de referenties van een domein beheerder.

Met de tweede opdracht wordt de `Invoke-Command` cmdlet gebruikt om een `Start-Job` opdracht uit te voeren in de sessie. Met de opdracht in de taak worden alle gebeurtenissen in het systeem gebeurtenis logboek opgehaald. Het resulterende taak object wordt opgeslagen in de `$j` variabele.

Met de derde opdracht wordt de taak gestopt. De cmdlet wordt gebruikt `Invoke-Command` om een opdracht uit te voeren `Stop-Job` in de **PSSession** op Server01. Omdat de taak objecten worden opgeslagen in `$j` , een variabele op de lokale computer, gebruikt de opdracht de aanpassings functie voor het gebruik van scope om te identificeren `$j` als een lokale variabele.
Zie [about_Remote_Variables](about/about_Remote_Variables.md)voor meer informatie over de aanpassing van het bereik.

Wanneer de opdracht is voltooid, wordt de taak gestopt en is de **PSSession** in `$s` beschikbaar voor gebruik.

### Voor beeld 2: een achtergrond taak stoppen

```powershell
Stop-Job -Name "Job1"
```

Met deze opdracht wordt de Taak1-achtergrond taak gestopt.

### Voor beeld 3: meerdere achtergrond taken stoppen

```powershell
Stop-Job -Id 1, 3, 4
```

Met deze opdracht worden drie taken gestopt.
Ze worden geïdentificeerd aan de hand van hun Id's.

### Voor beeld 4: alle achtergrond taken stoppen

```powershell
Get-Job | Stop-Job
```

Met deze opdracht worden alle achtergrond taken in de huidige sessie gestopt.

### Voor beeld 5: alle geblokkeerde achtergrond taken stoppen

```powershell
Stop-Job -State Blocked
```

Met deze opdracht worden alle geblokkeerde taken gestopt.

### Voor beeld 6: een taak stoppen met een exemplaar-ID

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

Deze opdrachten laten zien hoe u een taak kunt stoppen op basis van de exemplaar-ID.

Met de eerste opdracht wordt de `Get-Job` cmdlet gebruikt om de taken in de huidige sessie op te halen. De opdracht maakt gebruik van een pijplijn operator ( `|` ) om de taken naar een `Format-Table` opdracht te verzenden, waarin een tabel van de opgegeven eigenschappen van elke taak wordt weer gegeven. De tabel bevat de exemplaar-ID van elke taak. Er wordt een berekende eigenschap gebruikt om de taak status weer te geven.

De tweede opdracht maakt gebruik van een `Stop-Job` opdracht met de para meter **InstanceId** om een geselecteerde taak te stoppen.

### Voor beeld 7: een taak stoppen op een externe computer

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

In dit voor beeld ziet u hoe u de cmdlet kunt gebruiken `Stop-Job` om een taak te stoppen die wordt uitgevoerd op een externe computer.

Omdat de taak is gestart met behulp van de para meter **AsJob** van de cmdlet, bevindt `Invoke-Command` het taak object zich op de lokale computer, zelfs als de taak wordt uitgevoerd op de externe computer. Daarom kunt u een lokale opdracht gebruiken `Stop-Job` om de taak te stoppen.

De eerste opdracht gebruikt de `Invoke-Command` cmdlet om een achtergrond taak op de Server01-computer te starten. De opdracht gebruikt de para meter **AsJob** om de externe opdracht als achtergrond taak uit te voeren.

Met deze opdracht wordt een taak object geretourneerd. Dit is hetzelfde taak object dat door de `Start-Job` cmdlet wordt geretourneerd.
De opdracht slaat het taak object op in de `$j` variabele.

De tweede opdracht maakt gebruik van een pijplijn operator om de taak in de `$j` variabele naar te verzenden `Stop-Job` . De opdracht gebruikt de para meter **PassThru** om direct `Stop-Job` een taak object te retour neren. In de weer gave taak object wordt bevestigd dat de status van de taak is gestopt.

Zie about_Remote_Jobs voor meer informatie over externe achtergrond taken.

## PARAMETERS

### -Filter

Hiermee geeft u een hash-tabel met voor waarden op. Met deze cmdlet worden taken gestopt die voldoen aan alle voor waarden.
Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.

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

### -Id

Hiermee geeft u de Id's op van taken die met deze cmdlet worden gestopt. De standaard instelling is alle taken in de huidige sessie.

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie. Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie. U kunt een of meer Id's typen, gescheiden door komma's. Als u de ID van een taak wilt zoeken, typt u `Get-Job` .

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Hiermee geeft u de exemplaar-Id's op van taken die met deze cmdlet worden gestopt. De standaard waarde is alle taken.

Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert. Gebruik om de exemplaar-ID van een taak te vinden `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Taak

Hiermee geeft u de taken op die met deze cmdlet worden gestopt. Voer een variabele in die de taken bevat of een opdracht waarmee de taken worden opgehaald. U kunt ook een pijplijn operator gebruiken om taken naar de cmdlet te verzenden `Stop-Job` . Standaard `Stop-Job` verwijdert alle taken die in de huidige sessie zijn gestart.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u beschrijvende namen op van taken die met deze cmdlet worden gestopt. Voer de namen van de taken in een lijst met door komma's gescheiden waarden in of gebruik joker tekens (*) om een taak naam patroon in te voeren. Standaard `Stop-Job` stopt alle taken die in de huidige sessie zijn gemaakt.

Omdat de beschrijvende naam niet gegarandeerd uniek is, gebruikt u de para meters **WhatIf** en **confirm** bij het stoppen van taken op naam.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PassThru

Retourneert een object dat het item vertegenwoordigt waarmee u werkt. Deze cmdlet genereert standaard geen uitvoer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Status

Hiermee geeft u een taak status op. Met deze cmdlet worden alleen taken in de opgegeven status gestopt. De aanvaardbare waarden voor deze parameter zijn:

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
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Management. Automation. RemotingJob

U kunt een taak object door sluizen naar deze cmdlet.

## UITVOER

### Geen, System. Management. Automation. PSRemotingJob

Met deze cmdlet wordt een taak object geretourneerd als u de para meter **PassThru** opgeeft. Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Invoke-opdracht](Invoke-Command.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Begin taak](Start-Job.md)

[Wait-Job](Wait-Job.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Remote_Variables](About/about_Remote_Variables.md)

[about_Jobs](About/about_Jobs.md)

[about_Scopes](About/about_scopes.md)
