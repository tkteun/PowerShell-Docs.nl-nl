---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250316"
---
# Disable-ScheduledJob

## SAMENVATTING
Hiermee wordt een geplande taak uitgeschakeld.

## SYNTAXIS

### Definitie (standaard)

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Definitie

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Disable-ScheduledJob** worden geplande taken tijdelijk uitgeschakeld.
Als u uitschakelen kiest, worden alle taak eigenschappen behouden en worden de taak triggers niet uitgeschakeld, maar wordt voor komen dat de geplande taken automatisch worden gestart wanneer deze worden geactiveerd.
U kunt een uitgeschakelde geplande taak starten met behulp van de cmdlet Start-Job of een uitgeschakelde geplande taak als sjabloon gebruiken.

Als u een geplande taak wilt uitschakelen, stelt de cmdlet **Disable-ScheduledJob** de eigenschap **enabled** van de geplande taak in op False ($false).
Gebruik de cmdlet Enable-ScheduledJob om de geplande taak opnieuw in te scha kelen.

**Disable-ScheduledJob** is een van een verzameling taak planning-cmdlets in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een geplande taak uitschakelen

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

Met deze opdracht wordt de geplande taak met ID 2 op de lokale computer uitgeschakeld.
In de uitvoer ziet u het effect van de opdracht.

### Voor beeld 2: alle geplande taken uitschakelen

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

Met deze opdracht worden alle geplande taken op de lokale computer uitgeschakeld.
De cmdlet Get-ScheduledJob wordt gebruikt om alle geplande taken en de cmdlet **Disable-ScheduledJob** uit te scha kelen.

U kunt de geplande taak opnieuw inschakelen met behulp van de cmdlet Enable-ScheduledJob en een uitgeschakelde geplande taak uitvoeren met behulp van de Start-Job-cmdlet.

**Met Disable-ScheduledJob** worden geen waarschuwingen of fouten gegenereerd als u een geplande taak uitschakelt die al is uitgeschakeld, zodat u alle geplande taken zonder voor waarden kunt uitschakelen.

### Voor beeld 3: geselecteerde geplande taken uitschakelen

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

Met deze opdracht wordt de geplande taak uitgeschakeld, wordt er geen referentie opgenomen.
Taken zonder referenties worden uitgevoerd met de machtiging van de gebruiker die ze heeft gemaakt.

De opdracht gebruikt de cmdlet Get-ScheduledJob om alle geplande taken op de computer op te halen.
Een pijplijn operator verzendt de geplande taken naar de cmdlet Where-Object, waarmee geplande taken worden geselecteerd die geen referenties hebben.
De opdracht maakt gebruik van de operator Not (!) en verwijst naar de eigenschap Credential van de geplande taak.
Een andere pijplijn operator verzendt de geselecteerde geplande taken naar de cmdlet **Disable-ScheduledJob** , waarmee deze worden uitgeschakeld.

### Voor beeld 4: geplande taken uitschakelen op een externe computer

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

Met deze opdracht wordt de geplande taak TestJob op twee externe computers, Srv01 en Srv10, uitgeschakeld.

De opdracht gebruikt de cmdlet Invoke-Command om een opdracht **Disable-ScheduledJob** uit te voeren op de computers Srv01 en Srv10.
De opdracht gebruikt de para meter *name* van **Disable-ScheduledJob** om de geplande TestJob-taak op elke computer te selecteren.

### Voor beeld 5: een geplande taak uitschakelen op basis van de algemene ID

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

In deze voor beelden ziet u hoe u een geplande taak kunt uitschakelen met behulp van de algemene id.
De waarde van de eigenschap GlobalID van een geplande taak is een unieke id (GUID).
Gebruik de GlobalID-waarde wanneer Precision vereist is, bijvoorbeeld wanneer u geplande taken op meerdere computers uitschakelt.

## PARAMETERS

### -Id
Hiermee wordt de geplande taak met het opgegeven id-nummer (ID) uitgeschakeld.
Voer de ID van een geplande taak in.

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Input object
Hiermee geeft u de geplande taak moet worden uitgeschakeld.
Voer een variabele in die  **ScheduledJobDefinition** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobDefinition** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook een **ScheduledJobDefinition** -object pipeen om **-ScheduledJob uit te scha kelen**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Hiermee worden de geplande taken met de opgegeven namen uitgeschakeld.
Voer de naam van een geplande taak in.
Joker tekens worden ondersteund.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
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

### Micro soft. Power shell. ScheduledJob. ScheduledJobDefinition
U kunt een geplande taak door sluizen naar **Disable-ScheduledJob**.

## UITVOER

### Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobDefinition
Als u de para meter **PassThru** gebruikt, wordt de geplande taak die is uitgeschakeld, door **Disable-ScheduledJob** geretourneerd.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* Als u **Disable-ScheduledJob** gebruikt, worden er geen waarschuwingen of fouten gegenereerd als u hiermee een geplande taak die al is uitgeschakeld, uitschakelt.

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
