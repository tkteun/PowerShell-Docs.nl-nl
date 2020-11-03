---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250132"
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
Met de cmdlet **suspend-job** worden werk stroom taken onderbroken.
Suspend betekent dat een werk stroom taak tijdelijk moet worden onderbroken of onderbroken.
Met deze cmdlet kunnen gebruikers die werk stromen uitvoeren, de werk stroom onderbreken.
Dit is een aanvulling op de activiteit Suspend-workflow https://go.microsoft.com/fwlink/?LinkId=267141 , een opdracht in de werk stroom waarmee de werk stroom wordt onderbroken.

De cmdlet **suspend-job** werkt alleen op werk stroom taken.
Deze functie werkt niet op standaard achtergrond taken, zoals die worden gestart met behulp van de cmdlet Start-Job.

Zoek naar een waarde van PSWorkflowJob in de eigenschap **PSJobTypeName** van de taak om een werk stroom taak te identificeren.
Zie de Help-onderwerpen voor het aangepaste taak type om te bepalen of een bepaald aangepast taak type de cmdlet **pause-job** ondersteunt.

Wanneer u een werk stroom taak uitbreekt, wordt de werk stroom taak uitgevoerd op het volgende controle punt, wordt deze onderbroken en wordt er onmiddellijk een werk stroom taak object geretourneerd.
Als u wilt wachten tot de onderbreking is voltooid voordat u de taak kunt ophalen, gebruikt u de para meter *wait* of **pause-job** of de cmdlet Wait-Job.
Wanneer de werk stroom taak is onderbroken, wordt de waarde van de eigenschap **State** van de taak onderbroken.

Het onderbreken van de wacht stand is afhankelijk van controle punten.
De huidige taak status, meta gegevens en uitvoer worden opgeslagen in het controle punt zodat de werk stroom taak kan worden hervat zonder dat de status of gegevens verloren gaan.
Als de werk stroom taak geen controle punten heeft, kan deze niet goed worden onderbroken.
Als u controle punten wilt toevoegen aan een werk stroom die u uitvoert, gebruikt u de algemene para meter *PSPersist* workflow.
U kunt de para meter *Force* gebruiken om een werk stroom taak onmiddellijk te onderbreken en een werk stroom taak te onderbreken die geen controle punten heeft, maar de actie kan leiden tot verlies van status en gegevens.

Voordat u een taak-cmdlet voor een aangepast taak type gebruikt, zoals een werk stroom taak ( **PSWorkflowJob** ), moet u de module importeren die het aangepaste taak type ondersteunt, hetzij met behulp van de cmdlet Import-Module, hetzij met behulp van een cmdlet in de module.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een werk stroom taak op naam onderbreken

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt.

### Voor beeld 2: een werk stroom taak opschorten en hervatten

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

In dit voor beeld ziet u hoe u een werk stroom taak uitbreekt en hervat.

### Voor beeld 3: een werk stroom taak op een externe computer onderbreken

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

Met deze opdracht wordt de cmdlet Invoke-Command gebruikt om een werk stroom taak op de externe computer Srv01 te onderbreken.
De waarde van de *filter* parameter is een hash-tabel waarin een CustomID-waarde wordt opgegeven.
Dit **CustomID** is taak-meta gegevens ( **PSPrivateMetadata** ).

### Voor beeld 4: wachten tot de werk stroom taak is onderbroken

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

Met deze opdracht wordt de werk stroom taak VersionCheck onderbroken.
De opdracht gebruikt de *wait* -para meter om te wachten tot de werk stroom taak is onderbroken.
Wanneer de werk stroom taak wordt uitgevoerd op het volgende controle punt en is onderbroken, wordt de opdracht beëindigd en wordt het taak object geretourneerd.

### Voor beeld 5: een werk stroom taak geforceerd onderbreken

```
PS C:\> Suspend-Job Maintenance -Force
```

Met deze opdracht wordt de werk stroom taak geforceerd onderbroken.
De onderhouds taak heeft geen controle punten.
Het kan niet juist worden onderbroken en wordt mogelijk niet goed hervat.

## PARAMETERS

### -Filter
Hiermee geeft u een hash-tabel met voor waarden op.
Met deze cmdlet worden taken opgeschort die voldoen aan alle voor waarden.
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
Hiermee wordt de werk stroom taak onmiddellijk onderbroken.
Deze actie kan leiden tot verlies van status en gegevens.

Standaard kan de werk stroom **taak worden uitgevoerd** tot het volgende controle punt. vervolgens wordt de taak onderbroken.
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

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.
Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.
U kunt een of meer Id's typen, gescheiden door komma's.
Gebruik de cmdlet Get-Job om de ID van een taak te vinden.

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
Hiermee geeft u de exemplaar-Id's op van de taken die met deze cmdlet worden onderbroken.
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
Hiermee geeft u de werk stroom taken op die met deze cmdlet worden gestopt.
Voer een variabele in die de werk stroom taken bevat of een opdracht waarmee de werk stroom taken worden opgehaald.
U kunt werk stroom taken ook pipet naar de cmdlet **pause-job** .

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
Hiermee geeft u beschrijvende namen op van taken die met deze cmdlet worden onderbroken.
Voer een of meer werk stroom taak namen in.
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
Hiermee geeft u een taak status op.
Met deze cmdlet worden alleen taken in de opgegeven status gestopt.
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

**Suspend: taak** suspendeert alleen werk stroom taken met de status **actief** .

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

### -Wachten
Geeft aan dat deze cmdlet de opdracht prompt onderdrukt totdat de werk stroom taak de status onderbroken heeft.
Standaard wordt de **suspend-taak** onmiddellijk geretourneerd, zelfs als de werk stroom taak nog niet de status onderbroken heeft.

De *wait* -para meter is gelijk aan het sluizen van een **suspend-job-** opdracht naar de cmdlet **wait-job** .

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

### System. Management. Automation. job
U kunt alle typen taken naar deze cmdlet pipeen.
Als **opschorting-taak** echter een taak van een niet-ondersteund type krijgt, wordt een afsluit fout geretourneerd.

## UITVOER

### System. Management. Automation. job
Met deze cmdlet worden de taken geretourneerd die zijn onderbroken.

## OPMERKINGEN

* Het mechanisme en de locatie voor het opslaan van een onderbroken taak kunnen variëren afhankelijk van het taak type. Onderbroken werk stroom taken worden bijvoorbeeld standaard opgeslagen in een plat bestands archief, maar kunnen ook worden opgeslagen in een Data Base.
* Als u een werk stroom taak indient die niet wordt uitgevoerd, wordt er een waarschuwings bericht weer gegeven in de **suspend-taak** . Als u de waarschuwing wilt onderdrukken, gebruikt u de gemeen schappelijke *WarningAction* para meter met de waarde SilentlyContinue.

  Als een taak niet van een type is dat opschorting ondersteunt, retourneert **suspend-taak** een afsluit fout.

* Gebruik de para meter *State* van de cmdlet **Get-job** om werk stroom taken met de status onderbroken te krijgen om de werk stroom taken te vinden die zijn onderbroken.
* Sommige taak typen hebben opties of eigenschappen die verhinderen dat Windows Power shell de taak onderbreekt. Als er wordt geprobeerd de taak te onderbreken, controleert u of de taak opties en eigenschappen het blok keren toestaan.

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Resume-job](Resume-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Onderbreken-taak](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
