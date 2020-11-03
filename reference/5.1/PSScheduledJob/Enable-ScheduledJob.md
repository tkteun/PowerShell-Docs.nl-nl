---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250309"
---
# Enable-ScheduledJob

## SAMENVATTING
Hiermee wordt een geplande taak ingeschakeld.

## SYNTAXIS

### Definitie (standaard)

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Definitie

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Enable-ScheduledJob** worden geplande taken die zijn uitgeschakeld, ingeschakeld, zoals die zijn uitgeschakeld met behulp van de cmdlet Disable-ScheduledJob.
Ingeschakelde taken worden automatisch uitgevoerd wanneer deze wordt geactiveerd.

Als u een geplande taak wilt inschakelen, stelt de cmdlet **Enable-ScheduledJob** de eigenschap Enabled van de geplande taak in op $True.

**Ingeschakeld: ScheduledJob** is een van een verzameling cmdlets voor taak planning in de **PSScheduledJob** -module die is opgenomen in Windows Power shell.

Zie de onderwerpen in de PSScheduledJob-module voor meer informatie over geplande taken.
Importeer de PSScheduledJob-module en typ vervolgens: `Get-Help about_Scheduled*` of zie about_Scheduled_Jobs.

Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.

## VOORBEELDEN

### Voor beeld 1: een geplande taak inschakelen

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

Met deze opdracht wordt de geplande taak met ID 2 ingeschakeld op de lokale computer.
In de uitvoer ziet u het effect van de opdracht.

### Voor beeld 2: alle geplande taken inschakelen

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

Met deze opdracht worden alle geplande taken op de lokale computer ingeschakeld.
De cmdlet Get-ScheduledJob wordt gebruikt voor het ophalen van alle geplande taken en de cmdlet **Enable-ScheduledJob** om deze in te scha kelen.

**Enable-ScheduledJob** genereert geen waarschuwingen of fouten als u een geplande taak inschakelt die al is ingeschakeld, zodat u alle geplande taken zonder voor waarden kunt inschakelen.

### Voor beeld 3: geselecteerde geplande taken inschakelen

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

Met deze opdracht worden geplande taken ingeschakeld waarvoor geen netwerk verbinding nodig is.

De opdracht gebruikt de cmdlet Get-ScheduledJob om alle geplande taken op de computer op te halen.
Een pijplijn operator verzendt de geplande taken naar de cmdlet Get-ScheduledJobOption, waarmee de taak opties van elke geplande taak worden opgehaald.
Elk taak opties object heeft een eigenschap taak definitie die de bijbehorende geplande taak bevat.
De eigenschap taak definitie wordt gebruikt om de opdracht te volt ooien.

De opdracht maakt gebruik van een pijplijn operator (|) voor het verzenden van de taak opties naar de cmdlet Where-Object, waarmee optie objecten van geplande taken worden geselecteerd waarin de eigenschap **RunWithoutNetwork** de waarde True ($true) heeft.
Een andere pijplijn operator verzendt de geselecteerde geplande opdracht Opties objecten naar de ForEach-Object-cmdlet waarmee de opdracht **Enable-ScheduledJob** wordt uitgevoerd voor de geplande taak in de waarde van de eigenschap taak definitie van elk object voor taak opties.

### Voor beeld 4: geplande taken inschakelen op een externe computer

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

Met deze opdracht kunt u geplande taken met ' test ' in hun namen op twee externe computers, Srv01 en Srv10.

De opdracht gebruikt de cmdlet Invoke-Command om een opdracht **Enable-ScheduledJob** uit te voeren op de computers Srv01 en Srv10.
De opdracht maakt gebruik van de para meter *name* van **Enable-ScheduledJob** om de geplande inventaris op elke computer in te scha kelen.

## PARAMETERS

### -Id
Hiermee wordt de geplande taak met het opgegeven id-nummer (ID) ingeschakeld.
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
Hiermee geeft u de geplande taak moet worden ingeschakeld.
Voer een variabele in die **ScheduledJobDefinition** -objecten bevat of typ een opdracht of expressie waarmee **ScheduledJobDefinition** -objecten worden opgehaald, zoals een Get-ScheduledJob opdracht.
U kunt ook een **ScheduledJobDefinition** -object pipeen om **-ScheduledJob in te scha kelen**.

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
Hiermee worden de geplande taken met de opgegeven namen ingeschakeld.
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
U kunt een geplande taak pipeen om **-ScheduledJob in te scha kelen**.

## UITVOER

### Geen of Microsoft. Power shell. ScheduledJob. ScheduledJobDefinition
Als u de para meter **PassThru** gebruikt, wordt de geplande taak die is ingeschakeld, door **Enable-ScheduledJob** geretourneerd.
Anders wordt met deze cmdlet geen uitvoer gegenereerd.

## OPMERKINGEN

* **Enable-ScheduledJob** genereert geen waarschuwingen of fouten als u deze gebruikt om een geplande taak in te scha kelen die al is ingeschakeld.

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
