---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250302"
---
# New-ScheduledJobOption

## SAMENVATTING
Hiermee maakt u een object dat geavanceerde opties bevat voor een geplande taak.

## SYNTAXIS

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **New-ScheduledJobOption** maakt u een object dat geavanceerde opties bevat voor een geplande taak.

U kunt het **ScheduledJobOptions** -object gebruiken dat door **New-ScheduledJobOption** wordt geretourneerd om de taak opties voor een nieuwe of bestaande geplande taak in te stellen.
U kunt ook taak opties instellen met behulp van de cmdlet Get-ScheduledJobOption om de taak opties van een bestaande geplande taak te verkrijgen of door een waarde van een hash-tabel te gebruiken om de taak opties weer te geven.

Zonder para meters, **New-ScheduledJobOption** genereert een object dat de standaard waarden voor alle opties bevat.
Omdat alle eigenschappen, met uitzonde ring van de eigenschap taak definitie, kunnen worden bewerkt, kunt u het resulterende object als sjabloon gebruiken en standaard optie objecten maken voor uw onderneming.

Controleer de standaard waarden van alle geplande taak opties bij het maken van geplande taken en het instellen van geplande taak opties.
Geplande taken worden alleen uitgevoerd als aan alle voor waarden is voldaan die voor de uitvoering ervan zijn ingesteld.

**New-ScheduledJobOption** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een optie object voor een geplande taak maken met standaard waarden

```
PS C:\> New-ScheduledJobOption
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

Met deze opdracht maakt u een optie object voor een geplande taak dat alle standaard waarden bevat.

### Voor beeld 2: een optie object voor een geplande taak maken met aangepaste waarden

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

Met de volgende opdracht maakt u een gepland taak object waarvoor het netwerk is vereist en waarop de geplande taak wordt uitgevoerd, zelfs als de computer niet is verbonden met de netspanning.

In de uitvoer ziet u *dat de waarde* van de eigenschap RunWithoutNetwork in $False is gewijzigd en dat de para meter *StartIfOnBattery* de waarde van de eigenschap StartIfOnBatteries heeft gewijzigd in $True.

### Voor beeld 3: opties instellen voor een nieuwe geplande taak

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : True
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

In dit voor beeld ziet u hoe u het **ScheduledJobOptions** -object gebruikt dat door **New-ScheduledJobOption** wordt geretourneerd om de opties voor een nieuwe geplande taak in te stellen.

### Voor beeld 4: de eigenschappen van een geplande taak selecteren optie object

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

In dit voor beeld ziet u hoe u de eigenschappen van een **ScheduledJobOptions** -object in alfabetische volg orde sorteert voor eenvoudig lezen.

De eerste opdracht maakt gebruik van de cmdlet **New-ScheduledJobOption** om een **ScheduledJobOptions** -object te maken.
De opdracht maakt gebruik van de para meter *WakeToRun* en slaat het resulterende object op in de variabele $Options.

De tweede opdracht gebruikt de eigenschap **PSObject** van alle Windows Power shell-objecten en de eigenschap eigenschappen om de eigenschappen van $Options als objecten op te halen.
De opdracht bewaart de eigenschappen objecten vervolgens naar de cmdlet Sort-Object, waarmee de eigenschappen in alfabetische volg orde op naam worden gesorteerd en vervolgens naar de Format-Table-cmdlet, waarin de namen en waarden van de eigenschappen in een tabel worden weer gegeven.

Met deze indeling is het veel eenvoudiger om de eigenschap WakeToRun van het object **ScheduledJobOptions** in $Options te vinden en te controleren of de waarde van $false is gewijzigd in $True.

## PARAMETERS

### -ContinueIfGoingOnBattery
Stop de geplande taak niet als de computer overschakelt naar de accu stroom (de verbinding met netstroom verbreekt) terwijl de taak wordt uitgevoerd.
Geplande taken worden standaard gestopt wanneer de computer de verbinding met netstroom verbreekt.

Met de para meter *ContinueIfGoingOnBattery* wordt de waarde van de eigenschap StopIfGoingOnBatteries van geplande taken ingesteld op $True.

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

### -DoNotAllowDemandStart
Start de taak alleen wanneer deze wordt geactiveerd.
Gebruikers kunnen de taak niet hand matig starten, bijvoorbeeld met behulp van de functie uitvoeren in taak planner.

Deze para meter is alleen van invloed op de taak planner.
Hiermee wordt niet voor komen dat gebruikers de cmdlet Start-Job gebruiken om de taak te starten.

Met de para meter *DoNotAllowDemandStart* wordt de waarde van de eigenschap DoNotAllowDemandStart van geplande taken ingesteld op $True.

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

### -HideInTaskScheduler
De taak niet weer geven in taak planner.
Deze waarde is alleen van invloed op de computer waarop de taak wordt uitgevoerd.
Geplande taken worden standaard weer gegeven in taak planner.

Zelfs als een taak verborgen is, kunnen gebruikers de taak weer geven door de optie verborgen taken weer geven in taak planner te selecteren.

Met de para meter *HideInTaskScheduler* wordt de waarde van de eigenschap ShowInTaskScheduler van geplande taken ingesteld op $false.

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

### -IdleDuration
Hiermee geeft u op hoe lang de computer inactief moet zijn voordat de taak wordt gestart.
De standaardwaarde is 10 minuten.
Als de computer niet inactief is voor de opgegeven duur voordat de waarde van *IdleTimeout* verloopt, wordt de geplande taak niet uitgevoerd tot de volgende geplande tijd, indien van toepassing.

Voer een **time span** -object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.

Als u deze waarde wilt inschakelen, gebruikt u de para meter *StartIfIdle* .
De eigenschap StartIfNotIdle van geplande taken is standaard ingesteld op $True en Windows Power shell negeert de waarden voor *IdleDuration* en *IdleTimeout* .

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout
Hiermee geeft u op hoe lang de geplande taak wacht om de computer inactief te maken.
Als deze time-out verloopt voordat de computer inactief blijft gedurende de periode die is opgegeven door de para meter *IdleDuration* , wordt de taak niet uitgevoerd tot de volgende geplande tijd, indien van toepassing.
De standaard waarde is een uur.

Voer een **time span** -object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.

Als u deze waarde wilt inschakelen, gebruikt u de para meter *StartIfIdle* .
De eigenschap StartIfNotIdle van geplande taken is standaard ingesteld op $True en Windows Power shell negeert de waarden voor *IdleDuration* en *IdleTimeout* .

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MultipleInstancePolicy
Hiermee wordt bepaald hoe het systeem reageert op een aanvraag om een exemplaar van een geplande taak te starten terwijl een ander exemplaar van de taak wordt uitgevoerd.
De standaard waarde is IgnoreNew.
De aanvaardbare waarden voor deze parameter zijn:

- IgnoreNew.
Het nieuwe taak exemplaar wordt genegeerd.
- Daarmee.
Het nieuwe taak exemplaar wordt onmiddellijk gestart.
- Wachtrij.
Het nieuwe taak exemplaar wordt gestart zodra het huidige exemplaar is voltooid.
- StopExisting.
Het huidige exemplaar van de taak wordt gestopt en het nieuwe exemplaar wordt gestart.

Als u de taak wilt uitvoeren, moeten aan alle voor waarden voor de taak planning worden voldaan.
Als de voor waarden die zijn ingesteld door de para meters *RequireNetwork* , *IdleDuration* en *IdleTimeout* niet worden vervuld, wordt het taak exemplaar niet gestart, ongeacht de waarde van deze para meter.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireNetwork
De geplande taak wordt alleen uitgevoerd als er netwerk verbindingen beschikbaar zijn.

Als u deze para meter opgeeft en het netwerk is niet beschikbaar op de geplande begin tijd, wordt de taak niet uitgevoerd tot de volgende geplande begin tijd, indien van toepassing.

Met de para meter *RequireNetwork* wordt de waarde van de eigenschap RunWithoutNetwork van geplande taken ingesteld op $false.

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

### -RestartOnIdleResume
Hiermee wordt een geplande taak opnieuw gestart wanneer de computer inactief wordt.
Deze para meter werkt met de para meter *StopIfGoingOffIdle* , die een actieve geplande taak onderbreekt als de computer actief wordt (de niet-actieve status blijft).

Met de para meter *RestartOnIdleResume* wordt de waarde van de eigenschap RestartOnIdleResume van geplande taken ingesteld op $True.

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

### -RunElevated
De geplande taak wordt uitgevoerd met de machtigingen van een lid van de groep Administrators op de computer waarop de taak wordt uitgevoerd.

Als u wilt dat een geplande taak wordt uitgevoerd met beheerders machtigingen, gebruikt u de para meter *Credential* van Register-ScheduledJob om expliciete referenties voor de taak op te geven.

Met de para meter *RunElevated* wordt de waarde van de eigenschap RunElevated van geplande taken ingesteld op $True.

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

### -StartIfIdle
Start de geplande taak als de computer niet actief is geweest gedurende de tijd die is opgegeven door de para meter *IdleDuration* voordat de tijd die is opgegeven door de para meter *IdleTimeout* is verlopen.

Standaard worden de para meters *IdleDuration* en *IdleTimeout* genegeerd en wordt de taak gestart op de geplande begin tijd, zelfs als de computer bezet is.

Als u deze para meter opgeeft en de computer bezet is (niet inactief) op de geplande begin tijd, wordt de taak niet uitgevoerd tot de volgende geplande begin tijd, indien van toepassing.

Met de para meter *StartIfIdle* wordt de waarde van de eigenschap StartIfNotIdle van geplande taken ingesteld op $false.

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

### -StartIfOnBattery
Hiermee wordt de geplande taak gestart, zelfs als de computer op de geplande begin tijd op de accu werkt.
De standaard waarde is $False.

Met de para meter *StartIfOnBattery* wordt de waarde van de eigenschap StartIfOnBatteries van geplande taken ingesteld op $True.

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

### -StopIfGoingOffIdle
Hiermee wordt een actieve geplande taak onderbroken als de computer actief wordt (niet-inactief) terwijl de taak wordt uitgevoerd.

Standaard wordt een geplande taak die wordt onderbroken wanneer de computer actief wordt hervat wanneer de computer weer actief wordt.
Als u dit standaard gedrag wilt wijzigen, gebruikt u de para meter *RestartOnIdleResume* .

Met de para meter *StopIfGoingOffIdle* wordt de waarde van de eigenschap StopIfGoingOffIdle van geplande taken ingesteld op $True.

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

### -WakeToRun
De computer uit de slaap stand of sluimer stand halen op de geplande begin tijd zodat de taak kan worden uitgevoerd.
Als de computer zich standaard in de sluimer stand of slaap stand bevindt op de geplande begin tijd, wordt de taak niet uitgevoerd.

Met de para meter *WakeToRun* wordt de waarde van de eigenschap WakeToRun van geplande taken ingesteld op $True.

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

### CommonParameters
Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen
U kunt geen invoer van een pipe naar deze cmdlet.

## UITVOER

### Micro soft. Power shell. ScheduledJob. ScheduledJobOptions

## OPMERKINGEN

* U kunt het **ScheduledJobOptions** -object gebruiken dat **New-ScheduledJobOption** maakt als de waarde van de para meter *ScheduledJobOption* van de cmdlet Register-ScheduledJob. De para meter *ScheduledJobOption* kan echter ook een hash-tabel waarde maken die de eigenschappen van het **ScheduledJobOptions** -object en hun waarden opgeeft, zoals:

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

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
