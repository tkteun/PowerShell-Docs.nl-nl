---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250320"
---
# Disable-JobTrigger

## SAMENVATTING
Hiermee schakelt u de taak triggers van geplande taken uit.

## SYNTAXIS

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
De cmdlet **Disable-JobTrigger** schakelt tijdelijk de taak triggers van geplande taken uit.
Als u deze optie uitschakelt, worden alle taak trigger eigenschappen behouden, maar wordt voor komen dat de taak trigger de geplande taak start.

Als u deze cmdlet wilt gebruiken, gebruikt u de cmdlet Get-JobTrigger om de taak triggers te verkrijgen.
Pipet vervolgens de taak triggers om **JobTrigger uit te scha kelen** of de para meter *input object* te gebruiken.

Als u een taak trigger wilt uitschakelen, stelt de cmdlet **Disable-JobTrigger** de eigenschap Enabled van de taak trigger in op $false.
Als u de taak trigger opnieuw wilt inschakelen, gebruikt u de cmdlet Enable-JobTrigger, waarmee de eigenschap **enabled** van de taak trigger wordt ingesteld op $True.
Als u een taak trigger uitschakelt, wordt de geplande taak niet uitgeschakeld, bijvoorbeeld door de cmdlet Disable-ScheduledJob, maar als u alle taak triggers uitschakelt, is het effect hetzelfde als het uitschakelen van de geplande taak.

Als u een geplande taak uitschakelt of alle taak triggers van een geplande taak uitschakelt, kunt u de taak nog steeds starten met behulp van de cmdlet Start-Job of de uitgeschakelde geplande taak als sjabloon gebruiken.

**Disable-ScheduledJob** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een taak trigger uitschakelen

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

Met deze opdracht wordt de eerste trigger (ID = 1) van de Backup-Archives geplande taak op de lokale computer uitgeschakeld.

De opdracht gebruikt de cmdlet Get-JobTrigger om de taak trigger op te halen.
Een pijplijn operator verzendt de taak trigger naar de cmdlet **Disable-JobTrigger** , waardoor deze wordt uitgeschakeld.

### Voor beeld 2: alle taak triggers uitschakelen

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

Met deze opdrachten worden alle taak triggers op twee geplande taken uitgeschakeld en worden de resultaten weer gegeven.

### Voor beeld 3: taak trigger van een geplande taak op een externe computer uitschakelen

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

Met deze opdracht worden de dagelijkse taak triggers uitgeschakeld op de geplande DeployPackage-taak op de externe computer met Server01.

De opdracht gebruikt de cmdlet Invoke-Command om de opdrachten uit te voeren op de computer Server01.
De opdracht extern maakt gebruik van de cmdlet Get-JobTrigger om de taak triggers van de geplande DeployPackage-taak te verkrijgen.
Een pijplijn operator verzendt de taak triggers naar de cmdlet Where-Object, waarmee alleen dagelijkse taak triggers worden geretourneerd.
Een pijplijn operator verzendt de dagelijkse taak triggers naar de cmdlet **Disable-JobTrigger** , waarmee deze worden uitgeschakeld.

## PARAMETERS

### -Input object
Hiermee geeft u de taak trigger op die moet worden uitgeschakeld.
Voer een variabele in die  **ScheduledJobTrigger** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobTrigger** -objecten worden opgehaald, zoals een Get-JobTrigger opdracht.
U kunt ook een **ScheduledJobTrigger** -object pipeen om **-JobTrigger uit te scha kelen**.

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
U kunt taak triggers pipet om **-JobTrigger uit te scha kelen**.

## UITVOER

### Geen
Met deze cmdlet wordt geen uitvoer gegenereerd.

## OPMERKINGEN

* **Disable-JobTrigger** genereert geen fouten of waarschuwingen als u een taak trigger uitschakelt die al is uitgeschakeld.

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
