---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250308"
---
# Enable-JobTrigger

## SAMENVATTING
Hiermee schakelt u de taak triggers van geplande taken in.

## SYNTAXIS

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Enable-JobTrigger** worden taak triggers van geplande taken opnieuw ingeschakeld, zoals die zijn uitgeschakeld met behulp van de cmdlet Disable-JobTrigger.
Met ingeschakelde en opnieuw ingeschakelde taak triggers kunnen geplande taken onmiddellijk starten. u hoeft Windows of Windows Power shell niet opnieuw op te starten.

Als u deze cmdlet wilt gebruiken, gebruikt u de cmdlet Get-JobTrigger om de taak triggers te verkrijgen.
Pipet vervolgens de taak triggers in om **-JobTrigger in te scha kelen** of de *input object* -para meter te gebruiken.

Als u een taak trigger wilt inschakelen, stelt de cmdlet **Enable-JobTrigger** de eigenschap Enabled van de taak trigger in op $True.

**Enable-ScheduledJob** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een taak trigger inschakelen

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

Met deze opdracht wordt de eerste trigger (ID = 1) van de Backup-Archives geplande taak op de lokale computer ingeschakeld.

De opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger op te halen.
Een pijplijn operator verzendt de taak trigger naar de cmdlet **Enable-JobTrigger** , waarmee deze wordt ingeschakeld.

### Voor beeld 2: alle taak triggers inschakelen

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taken op de lokale computer op te halen.
Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet Get-JobTrigger, waarmee alle taak triggers van de geplande taken worden opgehaald.
Een andere pijplijn operator verzendt de taak triggers naar de cmdlet **Enable-JobTrigger** , waarmee ze worden ingeschakeld.

### Voor beeld 3: de taak trigger van een geplande taak op een externe computer inschakelen

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

Met deze opdracht wordt de AtLogon-taak triggers ingeschakeld op de geplande DeployPackage-taak op de externe computer Server01.

De opdracht gebruikt de cmdlet Invoke-Command om de opdrachten uit te voeren op de computer Server01.
De opdracht extern maakt gebruik van de cmdlet Get-JobTrigger om de taak triggers van de geplande DeployPackage-taak te verkrijgen.
Een pijplijn operator verzendt de taak triggers naar de Where-Object cmdlet waarmee alleen AtLogon-taak triggers worden geretourneerd.
Een pijplijn operator verzendt de AtLogon-taak triggers naar de cmdlet **Enable-JobTrigger** , waarmee ze worden ingeschakeld.

### Voor beeld 4: Uitgeschakelde taak triggers weer geven

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

Met deze opdracht worden alle uitgeschakelde taak triggers van alle geplande taken in een tabel weer gegeven.
U kunt een opdracht als deze gebruiken om taak triggers te detecteren die mogelijk moeten worden ingeschakeld.

De opdracht gebruikt de cmdlet Get-ScheduledJob om de geplande taken op de lokale computer op te halen.
Een pijplijn operator (|) verzendt de geplande taken naar de cmdlet Get-JobTrigger, waarmee alle taak triggers van de geplande taken worden opgehaald.
Een andere pijplijn operator verzendt de taak triggers naar de cmdlet Where-Object, waarmee alleen taak triggers worden geretourneerd die zijn uitgeschakeld, dat wil zeggen, waarbij de waarde van de eigenschap Enabled van de taak trigger niet (!) True is.

Een andere pijplijn operator verzendt de uitgeschakelde taak triggers naar de cmdlet Format-Table, waarin de geselecteerde eigenschappen van de taak triggers in een tabel worden weer gegeven.
De eigenschappen bevatten een nieuwe JobName-eigenschap waarmee de naam van de geplande taak wordt weer gegeven in de eigenschap taak definitie van de taak trigger.

## PARAMETERS

### -Input object
Hiermee geeft u de taak trigger op die moet worden ingeschakeld.
Voer een variabele in die **ScheduledJobTrigger** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.
U kunt ook een **ScheduledJobTrigger** -object pipeen om **-JobTrigger in te scha kelen**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
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

### Micro soft. Power shell. ScheduledJob. ScheduledJobTrigger
U kunt taak triggers pipet om **-JobTrigger in te scha kelen**.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* **Enable-JobTrigger** genereert geen fouten of waarschuwingen als u een taak trigger inschakelt die al is ingeschakeld.

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
