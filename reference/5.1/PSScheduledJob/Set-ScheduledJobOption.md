---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250291"
---
# Set-ScheduledJobOption

## SAMENVATTING
Hiermee wijzigt u de taak opties van een geplande taak.

## SYNTAXIS

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **set-ScheduledJobOptions** wijzigt de taak opties van geplande taken.

Als u de opties van een geplande taak wilt wijzigen, begint u met de cmdlet Get-ScheduledJobOption om de taak opties van een geplande taak op te halen.
Vervolgens kunt u de opties voor de **ScheduledJobOption instellen** of de opties in een variabele opslaan en de para meter *input object* van de cmdlet **set-ScheduledJobOption** gebruiken om de opties te identificeren.
Gebruik de resterende para meters van **set-ScheduledJobOption** om de taak opties te wijzigen.

Als u een taak optie wilt inschakelen, gebruikt u de para meter waarmee die optie wordt ingesteld.
Als u een optie wilt uitschakelen, typt u de parameter naam, een dubbele punt (:) en $False.
Als u bijvoorbeeld de optie *RunElevated* wilt uitschakelen, typt u `-RunElevated:$False` .

Elk object taak opties bevat een taak definitie-eigenschap die de geplande taak bevat, waardoor de koppeling met de geplande taak behouden blijft wanneer de taak opties worden gewijzigd.

De geplande taak opties bepalen hoe de taak wordt uitgevoerd wanneer deze wordt gestart door de taak planner.
Deze opties worden niet toegepast wanneer u de cmdlet Start-Job gebruikt om een geplande taak te starten.

**Set-ScheduledJobOption** is een van een verzameling taak planning-cmdlets in de PSScheduledJob-module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: taak opties wijzigen

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
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
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

In dit voor beeld ziet u hoe u de opties van een geplande taak op de lokale computer wijzigt.

De eerste opdracht gebruikt de cmdlet Get-ScheduledJobOption om de taak opties van de geplande DeployPackage-taak op te halen.
In de uitvoer ziet u dat de eigenschappen WakeToRun en RunElevated zijn ingesteld op $False.

Deze opdracht is niet vereist. het is alleen opgenomen om het effect van de optie wijziging weer te geven.

### Voor beeld 2: een optie wijzigen voor alle externe geplande taken

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

Met deze opdracht wordt de waarde van de *IdleTimeout* van één uur (de standaard waarde) gewijzigd in twee uur op alle geplande taken op de Server01-computer.

De opdracht gebruikt de cmdlet Invoke-Command om een opdracht uit te voeren op de computer Server01.

De externe opdracht begint met een Get-ScheduledJob opdracht waarmee alle geplande taken op de computer worden opgehaald.
De geplande taken worden door gegeven aan de cmdlet Get-ScheduledJobOption, waarmee de taak opties van de geplande taken worden opgehaald.
Elk-taak opties object bevat een taak definitie-eigenschap die de geplande taak bevat, zodat het opties-object is gekoppeld aan de geplande taak, zelfs wanneer dit wordt gewijzigd.

De taak triggers worden gepiped naar de cmdlet **set-ScheduledJobOption** , waarmee de waarde van de optie *IdleTimeout* wordt gewijzigd in twee uur (2:00:00).

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

Zelfs als een taak verborgen is, kunnen gebruikers de taak weer geven door de optie **verborgen taken** weer geven in taak planner te selecteren.

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

Voer een time span-object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.

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
Hiermee geeft u op hoe lang de computer inactief moet zijn voordat de taak wordt gestart.
De standaardwaarde is 10 minuten.
Als de computer niet inactief is voor de opgegeven duur voordat de waarde van **IdleTimeout** verloopt, wordt de geplande taak niet uitgevoerd tot de volgende geplande tijd, indien van toepassing.

Voer een time span-object in, zoals het nummer dat is gegenereerd door de New-TimeSpan cmdlet of voer een waarde in \<hours\> : \<minutes\> : \<seconds\> Format die automatisch wordt geconverteerd naar een **time span** -object.

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

### -Input object
Hiermee geeft u de taak opties.
Voer een variabele in die **ScheduledJobOptions** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobOptions** -objecten worden opgehaald, zoals een Get-ScheduledJobOption opdracht.
U kunt ook een **ScheduledJobOptions** -object pipeen naar **set-ScheduledJobOption**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MultipleInstancePolicy
Hiermee wordt bepaald hoe het systeem reageert op een aanvraag om een exemplaar van een geplande taak te starten terwijl een ander exemplaar van de taak wordt uitgevoerd.
De aanvaardbare waarden voor deze parameter zijn:

- IgnoreNew.
Het nieuwe taak exemplaar wordt genegeerd.
Dit is de standaardwaarde.
- Daarmee.
Het nieuwe taak exemplaar wordt onmiddellijk gestart.
- Wachtrij.
Het nieuwe taak exemplaar wordt gestart zodra het huidige exemplaar is voltooid.
- StopExisting.
Het huidige exemplaar van de taak stop en het nieuwe exemplaar wordt gestart.

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

Met de para meter **RunElevated** wordt de waarde van de eigenschap **RunElevated** van geplande taken ingesteld op True.

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
Start de geplande taak als de computer niet actief is geweest gedurende de tijd die is opgegeven door de para meter **IdleDuration** voordat de tijd die is opgegeven door de para meter *IdleTimeout* is verlopen.

Standaard worden de para meters *IdleDuration* en *IdleTimeout* genegeerd en wordt de taak gestart op de geplande begin tijd, zelfs als de computer bezet is.

Als u deze para meter opgeeft en de computer bezet is (niet inactief) op de geplande begin tijd, wordt de taak niet uitgevoerd tot de volgende geplande begin tijd, indien van toepassing.

De para meter *StartIfIdle* stelt de waarde van de eigenschap **StartIfNotIdle** van geplande taken in op false.

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
De standaard waarde is False.

Met de para meter *StartIfOnBattery* wordt de waarde van de eigenschap **StartIfOnBatteries** van geplande taken ingesteld op $True.

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

### Micro soft. Power shell. ScheduledJob. ScheduledJobOptions
U kunt een geplande taak opties-object door geven aan **set-ScheduledJobOption**.

## UITVOER

### Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobOptions
Wanneer u de para meter *PassThru* gebruikt, retourneert **set-ScheduledJobOption** de taak opties die zijn gewijzigd.
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
