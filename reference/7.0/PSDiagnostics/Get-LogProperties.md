---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
Locale: en-US
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 08638749b7a5bb57bee804fccf9de17f50fd6736
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249635"
---
# Get-LogProperties

## SAMENVATTING
Hiermee worden de eigenschappen van een Windows-gebeurtenis logboek opgehaald.

## SYNTAXIS

```
Get-LogProperties [-Name] <Object> [<CommonParameters>]
```

## BESCHRIJVING

Met deze cmdlet worden de configuratie-instellingen van een Windows-gebeurtenis logboek opgehaald. Deze cmdlet wordt gebruikt door de- `Enable-PSTrace` en- `Disable-PSTrace` cmdlets.

## VOORBEELDEN

### Voor beeld 1: de configuratie-instellingen van het Windows Power shell-gebeurtenis logboek ophalen

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## PARAMETERS

### -Name

De naam van de provider van de gebeurtenis.

```yaml
Type: System.Object
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

### System. String

## UITVOER

### Micro soft. Power shell. Diagnostics. LogDetails

De **PSDiagnostics** -module voegt de klasse **LogDetails** toe aan de `Microsoft.PowerShell.Diagnostics` naam ruimte.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Set-LogProperties](Set-LogProperties.md)

[Enable-PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
