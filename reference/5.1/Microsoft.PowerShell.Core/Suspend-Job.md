---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388462"
---
# Suspend-Job

## SAMENVATTING
Stopt werk stroom taken tijdelijk.

## SYNTAXIS

### SessionIdParameterSet (standaard)

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Suspend-Job` cmdlet suspendeert werk stroom taken. Suspend betekent dat een werk stroom taak tijdelijk moet worden onderbroken of onderbroken. Met deze cmdlet kunnen gebruikers die werk stromen uitvoeren, de werk stroom onderbreken. Dit is een aanvulling op de activiteit Suspend-workflow https://go.microsoft.com/fwlink/?LinkId=267141 , een opdracht in de werk stroom waarmee de werk stroom wordt onderbroken.

De `Suspend-Job` cmdlet werkt alleen op werk stroom taken. Deze functie werkt niet op standaard achtergrond taken, zoals die worden gestart met behulp van de `Start-Job` cmdlet.

Zoek naar een waarde van PSWorkflowJob in de eigenschap **PSJobTypeName** van de taak om een werk stroom taak te identificeren. `Suspend-Job`Zie de Help-onderwerpen voor het aangepaste taak type om te bepalen of een bepaald aangepast taak type de cmdlet ondersteunt.

Wanneer u een werk stroom taak uitbreekt, wordt de werk stroom taak uitgevoerd op het volgende controle punt, wordt deze onderbroken en wordt er onmiddellijk een werk stroom taak object geretourneerd. Als u wilt wachten tot de onderbreking is voltooid, gebruikt u de para meter **wait** van `Suspend-Job` of de `Wait-Job` cmdlet. Wanneer de werk stroom taak is onderbroken, wordt de waarde van de eigenschap **State** van de taak onderbroken.

Het onderbreken van de wacht stand is afhankelijk van controle punten. De huidige taak status, meta gegevens en uitvoer worden opgeslagen in het controle punt zodat de werk stroom taak kan worden hervat zonder dat de status of gegevens verloren gaan. Als de werk stroom taak geen controle punten heeft, kan deze niet goed worden onderbroken. Als u controle punten wilt toevoegen aan een werk stroom die u uitvoert, gebruikt u de algemene para meter **PSPersist** workflow. U kunt de para meter **Force** gebruiken om een werk stroom taak onmiddellijk te onderbreken en een werk stroom taak te onderbreken die geen controle punten heeft, maar de actie kan leiden tot verlies van status en gegevens.

Voordat u een taak-cmdlet voor een aangepast taak type gebruikt, zoals een werk stroom taak ( **PSWorkflowJob** ), moet u de module importeren die het aangepaste taak type ondersteunt, hetzij met behulp van de cmdlet, hetzij met behulp van `Import-Module` een cmdlet in de module.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een werk stroom taak op naam onderbreken

In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt.

Met de eerste opdracht wordt de `Get-SystemLog` werk stroom gemaakt. De werk stroom gebruikt de `CheckPoint-Workflow` activiteit om een controle punt in de werk stroom te definiëren.

De tweede opdracht maakt gebruik van de para meter **AsJob** die gemeen schappelijk is voor alle werk stromen om de `Get-SystemLog` werk stroom als achtergrond taak uit te voeren. De opdracht gebruikt de algemene para meter **JobName** workflow om een beschrijvende naam voor de werk stroom taak op te geven.

De derde opdracht gebruikt de `Get-Job` cmdlet om de `Get-SystemLogJob` werk stroom taak op te halen. In de uitvoer ziet u dat de waarde van de eigenschap **PSJobTypeName** PSWorkflowJob is.

De vierde opdracht gebruikt de `Suspend-Job` cmdlet om de taak te onderbreken `Get-SystemLogJob` . De taak wordt uitgevoerd op het controle punt en wordt vervolgens onderbroken.

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### Voor beeld 2: een werk stroom taak opschorten en hervatten

In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt en hervat.

Met de eerste opdracht wordt de LogWorkflowJob-taak onderbroken. De opdracht wordt direct geretourneerd. In de uitvoer ziet u dat de werk stroom taak nog actief is, ook al wordt deze onderbroken.

De tweede opdracht gebruikt de `Get-Job` cmdlet om de LogWorkflowJob-taak op te halen. In de uitvoer ziet u dat de werk stroom taak is onderbroken.

De derde opdracht gebruikt de `Get-Job` cmdlet om de LogWorkflowJob-taak en de `Resume-Job` cmdlet te krijgen om deze te hervatten. In de uitvoer ziet u dat de werk stroom taak is hervat en nu wordt uitgevoerd.

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### Voor beeld 3: een werk stroom taak op een externe computer onderbreken

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

Met deze opdracht wordt de `Invoke-Command` cmdlet gebruikt om een werk stroom taak op de externe computer Srv01 te onderbreken. De waarde van de **filter** parameter is een hash-tabel waarin een CustomID-waarde wordt opgegeven.
Dit **CustomID** is taak-meta gegevens ( **PSPrivateMetadata** ).

### Voor beeld 4: wachten tot de werk stroom taak is onderbroken

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

Met deze opdracht wordt de werk stroom taak VersionCheck onderbroken. De opdracht gebruikt de **wait** -para meter om te wachten tot de werk stroom taak is onderbroken. Wanneer de werk stroom taak wordt uitgevoerd op het volgende controle punt en is onderbroken, wordt de opdracht beëindigd en wordt het taak object geretourneerd.

### Voor beeld 5: een werk stroom taak geforceerd onderbreken

```
PS C:\> Suspend-Job Maintenance -Force
```

Met deze opdracht wordt de werk stroom taak geforceerd onderbroken. De onderhouds taak heeft geen controle punten. Het kan niet juist worden onderbroken en wordt mogelijk niet goed hervat.

## PARAMETERS

### -Filter

Hiermee geeft u een hash-tabel met voor waarden op. Met deze cmdlet worden taken opgeschort die voldoen aan alle voor waarden.
Voer een hash-tabel in waarbij de sleutels taak eigenschappen zijn en de waarden van de taak eigenschaps waarden.

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

Hiermee wordt de werk stroom taak onmiddellijk onderbroken. Deze actie kan leiden tot verlies van status en gegevens.

Standaard kan `Suspend-Job` de werk stroom taak worden uitgevoerd tot het volgende controle punt en wordt deze vervolgens onderbroken.
U kunt deze para meter ook gebruiken om werk stroom taken te onderbreken die geen controle punten hebben.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

Hiermee geeft u de Id's op van taken die met deze cmdlet worden onderbroken.

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie. Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie. U kunt een of meer Id's typen, gescheiden door komma's. Gebruik de cmdlet om de ID van een taak te vinden `Get-Job` .

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

Hiermee geeft u de exemplaar-Id's op van de taken die met deze cmdlet worden onderbroken. De standaard waarde is alle taken.

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

Hiermee geeft u de werk stroom taken op die met deze cmdlet worden gestopt. Voer een variabele in die de werk stroom taken bevat of een opdracht waarmee de werk stroom taken worden opgehaald. U kunt werk stroom taken ook door sluizen naar de `Suspend-Job` cmdlet.

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

Hiermee geeft u beschrijvende namen op van taken die met deze cmdlet worden onderbroken. Voer een of meer werk stroom taak namen in.
Joker tekens worden ondersteund.

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

`Suspend-Job` Hiermee worden alleen werk stroom taken met de status **actief** onderbroken.

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

### -Wachten

Geeft aan dat deze cmdlet de opdracht prompt onderdrukt totdat de werk stroom taak de status onderbroken heeft. Standaard wordt `Suspend-Job` direct geretourneerd, zelfs als de werk stroom taak nog niet de status onderbroken heeft.

De **wait** -para meter is gelijk aan het sluizen van een `Suspend-Job` opdracht aan de `Wait-Job` cmdlet.

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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

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

### System. Management. Automation. job

U kunt alle typen taken naar deze cmdlet pipeen. Als er echter `Suspend-Job` een taak van een niet-ondersteund type wordt opgehaald, wordt een afsluit fout geretourneerd.

## UITVOER

### System. Management. Automation. job
Met deze cmdlet worden de taken geretourneerd die zijn onderbroken.

## OPMERKINGEN

- Het mechanisme en de locatie voor het opslaan van een onderbroken taak kunnen variëren afhankelijk van het taak type. Onderbroken werk stroom taken worden bijvoorbeeld standaard opgeslagen in een plat bestands archief, maar kunnen ook worden opgeslagen in een Data Base.
- Als u een werk stroom taak indient die niet wordt uitgevoerd, `Suspend-Job` wordt een waarschuwings bericht weer gegeven. Als u de waarschuwing wilt onderdrukken, gebruikt u de gemeen schappelijke **WarningAction** para meter met de waarde SilentlyContinue.

  Als een taak niet van een type is dat opschorting ondersteunt, `Suspend-Job` wordt een afsluit fout geretourneerd.

- Gebruik de para meter **State** van de cmdlet om werk stroom taken met de status onderbroken te krijgen om de werk stroom taken te vinden die zijn onderbroken `Get-Job` .
- Sommige taak typen hebben opties of eigenschappen die verhinderen dat Windows Power shell de taak onderbreekt.
  Als er wordt geprobeerd de taak te onderbreken, controleert u of de taak opties en eigenschappen het blok keren toestaan.

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Resume-job](Resume-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Onderbreken-taak](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
