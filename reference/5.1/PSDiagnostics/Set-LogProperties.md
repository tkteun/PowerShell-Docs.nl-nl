---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/set-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LogProperties
ms.openlocfilehash: ff51e4c30c2554ba58aa28862c44bb5fdbfd78d1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250327"
---
# Set-LogProperties

## SAMENVATTING
Hiermee wijzigt u de eigenschappen van een Windows-gebeurtenis logboek.

## SYNTAXIS

```
Set-LogProperties [-LogDetails] <LogDetails> [-Force] [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet worden de configuratie-instellingen van een Windows-gebeurtenis logboek gewijzigd. Deze cmdlet wordt gebruikt door de- `Enable-PSTrace` en- `Disable-PSTrace` cmdlets.

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## VOORBEELDEN

### Voor beeld 1: de Bewaar instelling van het Windows Power shell-gebeurtenis logboek wijzigen

```powershell
$logDetails = Get-LogProperties 'Windows PowerShell'
$logDetails.Retention = $True
Set-LogProperties -LogDetails $logDetails
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : True
AutoBackup : False
MaxLogSize : 15728640
```

## PARAMETERS

### -Force

Wordt gebruikt om de wijziging te forceren zonder te vragen.

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

### -LogDetails

De bijgewerkte configuratie-instellingen die moeten worden toegewezen aan het gebeurtenis logboek.

```yaml
Type: Microsoft.PowerShell.Diagnostics.LogDetails
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Micro soft. Power shell. Diagnostics. LogDetails

U moet een volledig geconfigureerd **LogDetails** -object door geven aan de `Set-LogProperties` cmdlet.
Als u één instelling wilt wijzigen, moet u daarom gebruiken `Get-LogProperties` om de huidige configuratie op te halen.

## UITVOER

### System. object

## OPMERKINGEN

U moet deze cmdlet uitvoeren vanuit een Power shell-sessie met verhoogde bevoegdheden.

## GERELATEERDE KOPPELINGEN

[Get-LogProperties](Get-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
