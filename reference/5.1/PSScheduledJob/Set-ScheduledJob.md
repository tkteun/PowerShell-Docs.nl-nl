---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJob
ms.openlocfilehash: 6144d9f19b86727bc09d07e94f4bcf158e3b7071
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387903"
---
# Set-ScheduledJob

## SAMENVATTING
Geplande taken worden gewijzigd.

## SYNTAXIS

### Script Block (standaard)

```
Set-ScheduledJob [-Name <String>] [-ScriptBlock <ScriptBlock>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### Bestandspad

```
Set-ScheduledJob [-Name <String>] [-FilePath <String>] [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-InputObject] <ScheduledJobDefinition> [-MaxResultCount <Int32>] [-PassThru] [-ArgumentList <Object[]>]
 [-RunNow] [-RunEvery <TimeSpan>] [<CommonParameters>]
```

### Uitvoering

```
Set-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-ClearExecutionHistory] [-PassThru]
 [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **set-ScheduledJob** worden de eigenschappen van geplande taken gewijzigd, zoals de opdrachten die de taken uitvoeren of de referenties die nodig zijn om de taak uit te voeren.
U kunt dit ook gebruiken om de uitvoerings geschiedenis van de geplande taak te wissen.

Als u deze cmdlet wilt gebruiken, moet u beginnen met de cmdlet Get-ScheduledJob om de geplande taak op te halen.
Pipet vervolgens de geplande taak om **ScheduledJob** in te stellen of de taak op te slaan in een variabele en de para meter *input object* te gebruiken om de taak te identificeren.
Gebruik de resterende para meters van **set-ScheduledJob** om de taak eigenschappen te wijzigen of de uitvoerings geschiedenis te wissen.

Hoewel u **set-ScheduledJob** kunt gebruiken om de triggers en opties van een geplande taak te wijzigen, bieden de cmdlets Add-JobTrigger, set-JobTrigger en Set-ScheduledJobOption veel eenvoudiger manieren om deze taken uit te voeren.
Als u een nieuwe geplande taak wilt maken, gebruikt u de cmdlet Register-ScheduledJob.

De *trigger* parameter van **set-ScheduledJob** voegt een of meer taak triggers toe waarmee de taak wordt gestart.
De *trigger* parameter is optioneel. u kunt triggers toevoegen wanneer u de geplande taak maakt, taak triggers later toevoegen, de para meter *RunNow* toevoegen om de taak onmiddellijk te starten. Gebruik de cmdlet Start-Job om de taak onmiddellijk te starten of sla de niet-geactiveerde geplande taak op als een sjabloon voor andere taken.

**Set-ScheduledJob** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: het script wijzigen dat door een taak wordt uitgevoerd

```
PS C:\> Get-ScheduledJob -Name "Inventory"
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-Inventory.ps1             True

The second command uses the Get-ScheduledJob cmdlet to get the Inventory scheduled job. A pipeline operator (|) sends the scheduled job to the **Set-ScheduledJob** cmdlet. The **Set-ScheduledJob** cmdlet uses the *Script* parameter to specify a new script, Get-FullInventory.ps1. The command uses the *Passthru* parameter to return the scheduled job after the change.
PS C:\> Get-ScheduledJob -Name "Inventory" | Set-ScheduledJob -FilePath "C:\Scripts\Get-FullInventory.ps1" -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          Inventory       {1}             C:\Scripts\Get-FullInventory.ps1         True
```

In dit voor beeld ziet u hoe u het script wijzigt dat in een geplande taak wordt uitgevoerd.

De eerste opdracht maakt gebruik van de cmdlet Get-ScheduledJob om de geplande voorraad taak te verkrijgen.
In de uitvoer ziet u dat de taak het Get-Inventory.ps1 script uitvoert.

Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de script wijziging weer te geven.

### Voor beeld 2: de uitvoerings geschiedenis van een geplande taak verwijderen

```
PS C:\> Get-ScheduledJob BackupArchive | Set-ScheduledJob -ClearExecutionHistory
```

Met deze opdracht worden de huidige uitvoerings geschiedenis en opgeslagen taak resultaten verwijderd voor de geplande taak BackupArchive.

De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taak BackupArchive te verkrijgen.
Een pijplijn operator (|) verzendt de taak naar de cmdlet **set-ScheduledJob** om deze te wijzigen.
De cmdlet **set-ScheduledJob** gebruikt de para meter *ClearExecutionHistory* om de uitvoerings geschiedenis te verwijderen en de resultaten op te slaan.

Zie about_Scheduled_Jobs voor meer informatie over de uitvoerings geschiedenis en de opgeslagen taak resultaten van geplande taken.

### Voor beeld 3: geplande taken wijzigen op een externe computer

```
PS C:\> Invoke-Command -Computer "Server01, Server02" -ScriptBlock {Get-ScheduledJob | Set-ScheduledJob -InitializationScript \\SrvA\Scripts\SetForRun.ps1}
```

Met deze opdracht wordt het initialisatie script gewijzigd in alle geplande taken op de Server01-en Server02-computers.

De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de Server01-en Server02-computers.

De externe opdracht begint met een Get-ScheduledJob opdracht waarmee alle geplande taken op de computer worden opgehaald.
De geplande taken worden gepiped naar de cmdlet **set-ScheduledJob** , waarmee het initialisatie script wordt gewijzigd in SetForRun.ps1.

## PARAMETERS

### -Argument List
Hiermee geeft u waarden op voor de para meters van het script dat is opgegeven met de para meter *filepath* of voor de opdracht die is opgegeven door de para meter *script Block* .

```yaml
Type: System.Object[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verificatie
Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren.
De aanvaardbare waarden voor deze parameter zijn:

- Standaard
- Basic
- CredSSP
- Samenvatting
- Kerberos
- Negotiate
- NegotiateWithImplicitCredential

De standaard waarde is standaard. Zie [AuthenticationMechanism-inventarisatie](/dotnet/api/system.management.automation.runspaces.authenticationmechanism) in de Power shell SDK voor meer informatie over de waarden van deze para meter.

Let op: de verificatie van de referentie provider (CredSSP), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten die verificatie vereisen voor meer dan één bron, zoals het openen van een externe netwerk share.
Dit mechanisme verhoogt het beveiligings risico van de externe bewerking.
Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ScriptBlock, FilePath
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ClearExecutionHistory
Hiermee worden de huidige uitvoerings geschiedenis en de opgeslagen resultaten van de geplande taak verwijderd.

De geschiedenis van de taak uitvoering en taak resultaten worden opgeslagen met de geplande taak in de map $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs op de computer waarop de taak is gemaakt.
Als u de uitvoerings geschiedenis wilt zien, gebruikt u de cmdlet Get-Job.
Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.

Deze para meter heeft geen invloed op de gebeurtenissen die door Task Scheduler naar de gebeurtenis logboeken van Windows worden geschreven. de taak resultaten worden niet gestopt door Windows Power shell.
Als u het aantal taak resultaten wilt beheren dat is opgeslagen, gebruikt u de para meter *MaxResultCount* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Execution
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Hiermee geeft u een gebruikers account op dat gemachtigd is om de geplande taak uit te voeren.
Standaard is dit de huidige gebruiker.

Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals een van de Get-Credential-cmdlet.
Als u alleen een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath
Hiermee geeft u een script op dat door de geplande taak wordt uitgevoerd.
Geef het pad op naar een. ps1-bestand op de lokale computer.
Als u standaard waarden voor de script parameters wilt opgeven, gebruikt u de para meter *argument List* .
Elke geplande taak moet een waarde van *script Block* of *filepath* hebben.

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InitializationScript
Hiermee geeft u het volledig gekwalificeerde pad naar een Windows Power shell-script (. ps1) op.
Het initialisatie script wordt uitgevoerd in de sessie die is gemaakt voor de achtergrond taak vóór de opdrachten die zijn opgegeven door de para meter *script Block* of het script dat is opgegeven door de para meter *filepath* .
U kunt het initialisatie script gebruiken om de sessie te configureren, zoals het toevoegen van bestanden, functies of aliassen, het maken van mappen of het controleren op vereisten.

Als u een script wilt opgeven dat de opdrachten van de primaire opdracht uitvoert, gebruikt u de *filepath* -para meter.

Als het initialisatie script een fout genereert, inclusief een niet-afsluit fout, wordt het huidige exemplaar van de geplande taak niet uitgevoerd en is de status mislukt.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u de geplande taak moet worden gewijzigd.
Voer een variabele in die **ScheduledJobDefinition** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobDefinition** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook een **ScheduledJobDefinition** -object pipeen naar **set-ScheduledJob**.

Als u meerdere geplande taken opgeeft, worden met **set-ScheduledJob** dezelfde wijzigingen aangebracht aan alle taken.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MaxResultCount
Hiermee geeft u op hoeveel items van de taak resultaat voor de geplande taak worden bewaard.
De standaard waarde is 32.

Windows Power shell slaat de uitvoerings geschiedenis en resultaten van elk geactiveerd exemplaar van de geplande taak op schijf op.
De waarde van deze para meter bepaalt het aantal taak exemplaar resultaten dat voor deze geplande taak wordt opgeslagen.
Wanneer het aantal taak exemplaren deze waarde overschrijdt, worden de resultaten van het oudste taak exemplaar door Windows Power shell verwijderd om ruimte te maken voor de resultaten van het nieuwste taak exemplaar.

De geschiedenis van de taak uitvoering en taak resultaten worden opgeslagen in de \Output-directory's van $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs \\ \<JobName\> \\ \<Timestamp\> op de computer waarop de taak is gemaakt.
Als u de uitvoerings geschiedenis wilt zien, gebruikt u de cmdlet Get-Job.
Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.

Met de para meter *MaxResultCount* wordt de waarde van de eigenschap ExecutionHistoryLength van de geplande taak ingesteld.

Als u de huidige uitvoerings geschiedenis en taak resultaten wilt verwijderen, gebruikt u de para meter *ClearExecutionHistory* .

```yaml
Type: System.Int32
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Hiermee geeft u een nieuwe naam op voor de geplande taak en exemplaren van de geplande taak.
De naam moet uniek zijn op de lokale computer.

Als u wilt weten welke geplande taak moet worden gewijzigd, gebruikt u de para meter *input object* of pipet u een geplande taak van Get-ScheduledJob naar **set-ScheduledJob**.

Met deze para meter worden de namen van taak exemplaren op de schijf niet gewijzigd.
Dit is alleen van invloed op taak exemplaren die worden gestart nadat deze opdracht is voltooid.

```yaml
Type: System.String
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru
Retourneert een object dat het item vertegenwoordigt waarmee u werkt.
Deze cmdlet genereert standaard geen uitvoer.

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

### -RunAs32
De geplande taak wordt uitgevoerd in een 32-bits proces.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunEvery

Wordt gebruikt om op te geven hoe vaak de taak moet worden uitgevoerd. Gebruik deze optie bijvoorbeeld om elke 15 minuten een taak uit te voeren.

```yaml
Type: System.TimeSpan
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RunNow
Start een taak onmiddellijk zodra de cmdlet **set-ScheduledJob** wordt uitgevoerd.
Met deze para meter is het niet nodig om taak planner te activeren om een Windows Power shell-script uit te voeren direct na de registratie, en hoeven gebruikers geen trigger te maken die een begin datum en-tijd opgeeft.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ScheduledJobOption
Opties instellen voor de geplande taak.
Voer een **ScheduledJobOptions** -object in, zoals een, dat u maakt met behulp van de cmdlet New-ScheduledJobOption, of een hash-tabel waarde.

U kunt opties voor een geplande taak instellen wanneer u de geplande taak registreert of de Set-ScheduledJobOption-of **set-ScheduledJob-** cmdlets gebruikt om opties in te stellen of te wijzigen.

Veel van de opties en hun standaard waarden bepalen of en wanneer een geplande taak wordt uitgevoerd.
Controleer deze opties voordat u een taak plant.
Zie New-ScheduledJobOption voor een beschrijving van de opties voor geplande taken, met inbegrip van de standaard waarden.

Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels.
In de volgende hash-tabel worden de sleutels weer gegeven met de standaard waarden.

`@{# Power SettingsStartIfOnBattery=$False;StopIfGoingOnBattery=$True; WakeToRun=$False; # Idle SettingsStartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False;# Security settingsShowInTaskScheduler=$TrueRunElevated=$False;# MiscRunWithoutNetwork=$False;DoNotAllowDemandStart=$False;MultipleInstancePolicy=IgnoreNew# Can be IgnoreNew, Parallel, Queue, StopExisting}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Script Block
Hiermee geeft u de opdrachten op die door de geplande taak worden uitgevoerd.
Plaats de opdrachten tussen accolades ({}) om een script blok te maken.
Als u standaard waarden voor opdracht parameters wilt opgeven, gebruikt u de para meter *argument List* .

Elke Register-ScheduledJob-opdracht moet de para meters *script Block* of *filepath* gebruiken.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Trigger
Hiermee geeft u de triggers voor de geplande taak op.
Voer een of meer **ScheduledJobTrigger** -objecten in, zoals de objecten die de New-JobTrigger cmdlet retourneert of een hash-tabel met sleutels en waarden van de taak trigger.

Met een taak trigger wordt automatisch een geplande taak gestart op een eenmalige of terugkerende geplande of wanneer er een gebeurtenis optreedt.

Taak triggers zijn optioneel.
U kunt een trigger toevoegen tijdens het maken van de geplande taak. Gebruik de cmdlets Add-JobTrigger of **set-ScheduledJob** om later triggers toe te voegen of gebruik de Start-Job cmdlet om de geplande taak onmiddellijk te starten.
U kunt ook een geplande taak maken en onderhouden die geen taak triggers heeft.

Als u een hash-tabel wilt verzenden, gebruikt u de volgende sleutels.

`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (of een wille keurige geldige tijd reeks); `DaysOfWeek="Monday", "Wednesday"` (of een combi natie van namen van dagen); `Interval=2` (of een geldig frequentie-interval); `RandomDelay="30minutes"` (of een wille keurige geldige time span-teken reeks); `User="Domain1\User01"` (of een geldige gebruiker; wordt alleen gebruikt met de frequentie waarde AtLogon)

}

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: ScriptBlock, FilePath
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition
U kunt geplande taken door sluizen naar **set-ScheduledJob**.

## UITVOER

### Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobDefinition
Als u de para meter *PassThru* gebruikt, wordt door **set-ScheduledJob** de geplande taak geretourneerd die is gewijzigd.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Enable-JobTrigger](Enable-JobTrigger.md)

[Enable-ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[REGI ster-ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Registratie ongedaan maken-ScheduledJob](Unregister-ScheduledJob.md)
