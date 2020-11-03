---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 85cbfad2a4866bf18e69fb99afb8698e233c4c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250145"
---
# Resume-Job

## SAMENVATTING
Hiermee wordt een onderbroken taak opnieuw gestart.

## SYNTAXIS

### SessionIdParameterSet (standaard)

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Resume-job** wordt een werk stroom taak hervat die is onderbroken, bijvoorbeeld door gebruik te maken van de Suspend-Job cmdlet of de activiteit About_Suspend werk stroom.
Wanneer een werk stroom taak wordt hervat, bouwt de taak engine de status, meta gegevens en uitvoer op uit opgeslagen resources, zoals controle punten.
De taak wordt opnieuw gestart zonder dat de status of gegevens verloren zijn gegaan.
De taak status is gewijzigd van **opgeschort** in **actief**.

Gebruik de para meters van **Resume-job** om taken op naam, id, exemplaar-id of pipe een taak object te selecteren, zoals één geretourneerd door de Get-Job-cmdlet, om de **taak te hervatten**.
U kunt ook een eigenschappen filter gebruiken om een taak te selecteren die u wilt hervatten.

**Resume-job** retourneert standaard onmiddellijk, zelfs als alle taken nog niet zijn hervat.
Gebruik de *wait* -para meter om de opdracht prompt te onderdrukken totdat alle opgegeven taken zijn hervat.

De cmdlet **Resume-job** werkt alleen voor aangepaste taak typen, zoals werk stroom taken.
Deze functie werkt niet op standaard achtergrond taken, zoals die worden gestart met behulp van de cmdlet Start-Job.
Als u een taak voor een niet-ondersteund type verzendt, wordt met **hervatten taak** een afsluit fout gegenereerd en stopt de uitvoering.

Zoek naar een waarde van **PSWorkflowJob** in de eigenschap **PSJobTypeName** van de taak om een werk stroom taak te identificeren.
Zie de Help-onderwerpen voor het aangepaste taak type om te bepalen of een bepaald aangepast taak type de cmdlet **Resume-job** ondersteunt.

Voordat u een taak-cmdlet voor een aangepast taak type gebruikt, importeert u de module die het aangepaste taak type ondersteunt, hetzij met behulp van de cmdlet Import-Module, hetzij door een cmdlet in de module op te halen of te gebruiken.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een taak hervatten op ID

```
The first command uses the **Get-Job** cmdlet to get the job. The output shows that the job is a suspended workflow job.
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

The second command uses the *Id* parameter of the **Resume-Job** cmdlet to resume the job with an *Id* value of 4.
PS C:\> Resume-Job -Id 4
```

Met de opdrachten in dit voor beeld wordt gecontroleerd of de taak een onderbroken werk stroom taak is en vervolgens de taak hervatten.

### Voor beeld 2: een taak hervatten op naam

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

Met deze opdracht wordt de para meter *name* gebruikt voor het hervatten van verschillende werk stroom taken op de lokale computer.

### Voor beeld 3: aangepaste eigenschaps waarden gebruiken

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

Met deze opdracht wordt de waarde van een aangepaste eigenschap gebruikt om de werk stroom taak te identificeren die u wilt hervatten.
De *filter* parameter wordt gebruikt om de werk stroom taak te identificeren met behulp van de eigenschap **CustomID** .
Er wordt ook gebruikgemaakt van de para meter *State* om te controleren of de werk stroom taak is onderbroken voordat deze probeert om deze te hervatten.

### Voor beeld 4: alle uitgestelde taken op een externe computer hervatten

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

Met deze opdracht worden alle onderbroken taken hervat op de externe computer Srv01.

De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Srv01.
De opdracht extern maakt gebruik van de para meter *State* van de cmdlet **Get-job** om alle uitgestelde taken op de computer op te halen.
Met een pijplijn operator (|) worden de uitgestelde taken verzonden naar de cmdlet **Resume-job** , waarmee ze worden hervat.

### Voor beeld 5: wachten tot taken worden hervat

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

Met deze opdracht wordt de *wait* -para meter voor het direct hervatten van de **taak** gebruikt om alleen te retour neren nadat alle opgegeven taken zijn hervat.
De *wait* -para meter is vooral nuttig in scripts die ervan uitgaan dat taken worden hervat voordat het script doorgaat.

### Voor beeld 6: een werk stroom die zichzelf onderbreekt hervatten

```
This code sample shows the **Suspend-Workflow** activity in a workflow.
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

The following command runs the Test-Suspend workflow on the Server01 computer.When you run the workflow, the workflow runs the Get-Date activity and stores the result in the $a variable. Then it runs the Suspend-Workflow activity. In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.  Suspend-Workflow returns a workflow job object even if the workflow is not explicitly run as a job.
PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

The following command resumes the Test-Suspend workflow in Job8. It uses the *Wait* parameter to hold the command prompt until the job is resumed.
PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command

--     ----            -------------   -----         -----------     --------             -------

8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

This command uses the **Receive-Job** cmdlet to get the results of the Test-Suspend workflow. The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the $a variable before the workflow was suspended.
PS C:\> Receive-Job -Name Job8
        Days              : 0
        Hours             : 0
        Minutes           : 0
        Seconds           : 19
        Milliseconds      : 823
        Ticks             : 198230041
        TotalDays         : 0.000229432917824074
        TotalHours        : 0.00550639002777778
        TotalMinutes      : 0.330383401666667
        TotalSeconds      : 19.8230041
        TotalMilliseconds : 19823.0041
        PSComputerName    : Server01
```

Met de cmdlet **Resume-job** kunt u een werk stroom taak hervatten die is onderbroken met behulp van de **suspend-werk stroom** activiteit.
Met deze activiteit wordt een werk stroom in een werk stroom onderbroken.
Het is alleen geldig in werk stromen.

Zie about_Suspend-werk stroom voor meer informatie over de Suspend-werk stroom.

## PARAMETERS

### -Filter
Hiermee geeft u een hash-tabel met voor waarden op.
Met deze cmdlet worden taken hervat die voldoen aan alle voor waarden in de hash-tabel.
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

### -Id
Hiermee wordt een matrix met Id's opgegeven voor taken die met deze cmdlet worden hervat.

De ID is een geheel getal dat de taak op unieke wijze identificeert in de huidige sessie.
Het is gemakkelijker te onthouden en te typen dan de exemplaar-ID, maar is alleen uniek in de huidige sessie.
U kunt een of meer Id's typen, gescheiden door komma's.
Voer **Get-job** uit om de id van een taak te vinden.

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
Hiermee geeft u een matrix met exemplaar-Id's van taken op die met deze cmdlet worden hervat.
De standaard waarde is alle taken.

Een exemplaar-ID is een GUID die de taak op de computer uniek identificeert.
Voer **Get-job** uit om de exemplaar-id van een taak te vinden.

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
Hiermee geeft u de taken op die moeten worden hervat.
Voer een variabele in die de taken bevat of een opdracht waarmee de taken worden opgehaald.
U kunt ook taken door sluizen naar de cmdlet **Resume-job** .

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
Hiermee geeft u een matrix met beschrijvende namen op van taken die met deze cmdlet worden hervat.
Voer een of meer taak namen in.
Joker tekens zijn toegestaan.

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
Hiermee wordt de status van taken opgegeven die moeten worden hervat.
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

Met deze cmdlet worden alleen taken hervat die de status **onderbroken** hebben.

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
Geeft aan dat deze cmdlet de opdracht prompt onderdrukt voordat alle taak resultaten opnieuw worden gestart.
Standaard retourneert deze cmdlet onmiddellijk de beschik bare resultaten.

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
Als **Resume-job** een taak van een niet-ondersteund type ontvangt, wordt een afsluit fout geretourneerd.

## UITVOER

### Geen, System. Management. Automation. job
Met deze cmdlet worden de taken geretourneerd die worden hervat als u de para meter *PassThru* gebruikt.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* **Resume-job** kan alleen taken hervatten die zijn onderbroken. Als u een taak in een andere status verzendt, wordt de **bewerking hervatten voor de taak uitgevoerd.** er wordt een waarschuwing gegenereerd om u te melden dat de taak niet kan worden hervat. Als u de waarschuwing wilt onderdrukken, gebruikt u de gemeen schappelijke *WarningAction* para meter met de waarde SilentlyContinue.
* Als een taak niet van een type is dat hervatten ondersteunt, zoals een werk stroom taak ( **PSWorkflowJob** ), retourneert **hervatten taak** een afsluit fout.
* Het mechanisme en de locatie voor het opslaan van een onderbroken taak kunnen variëren afhankelijk van het taak type. Onderbroken werk stroom taken worden bijvoorbeeld standaard opgeslagen in een plat bestands archief, maar kunnen ook worden opgeslagen in een SQL database.
* Wanneer u een taak hervat, wordt de status van de taak gewijzigd van **opgeschort** in **actief**. Als u de taken wilt vinden die worden uitgevoerd, met inbegrip van die die zijn hervat door deze cmdlet, gebruikt u de para meter *State* van de cmdlet **Get-job** om taken in de **actieve** status op te halen.
* Sommige taak typen hebben opties of eigenschappen die verhinderen dat Windows Power shell de taak onderbreekt. Als er wordt geprobeerd de taak te onderbreken, controleert u of de taak opties en eigenschappen het blok keren toestaan.

## GERELATEERDE KOPPELINGEN

[Get-job](Get-Job.md)

[Receive-job](Receive-Job.md)

[Verwijderen-taak](Remove-Job.md)

[Begin taak](Start-Job.md)

[Stoppen-taak](Stop-Job.md)

[Onderbreken-taak](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
