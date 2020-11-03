---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250515"
---
# Get-OperationValidation

## SAMENVATTING
Hiermee worden tests voor het validatie raamwerk voor bewerkingen opgehaald.

## SYNTAXIS

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## BESCHRIJVING
Met de cmdlet **Get-OperationValidation** worden bewerkings validatie raamwerk tests voor geïnstalleerde modules opgehaald.

Modules die een map met diagnostische gegevens bevatten, worden gecontroleerd op Ziekteloze tests in de submap Simple of complete, of beide.

## VOORBEELDEN

### Voor beeld 1: validatie tests voor bewerkingen ophalen

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

Met deze opdracht worden validatie tests uitgevoerd vanuit de module met de naam AddNumbers in de map C:\temp\modules.

## PARAMETERS

### -Module naam
Hiermee geeft u een matrix met namen van modules op.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TestType
Hiermee geeft u een matrix met test typen op.
Geldige waarden zijn eenvoudig, uitgebreid of beide.
De standaard instelling is eenvoudig, uitgebreid.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

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
U kunt geen invoer naar deze cmdlet pipeen.

## UITVOER

### PSCustomObject
De **PSCustomObject** beschrijft de validatie.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Invoke-OperationValidation](Invoke-OperationValidation.md)
