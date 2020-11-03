---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 993cc47f9c95fc39d717bb3b76b3de01f16ad47e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251243"
---
# Get-ExperimentalFeature

## SAMENVATTING
Hiermee worden experimentele functies opgehaald.

## SYNTAXIS

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-ExperimentalFeature` cmdlet retourneert alle experimentele functies die zijn gedetecteerd door Power shell.
Experimentele functies kunnen afkomstig zijn uit modules of de Power shell-engine. Met experimentele functies kunnen gebruikers veilig nieuwe functies testen en feedback geven (meestal via GitHub) voordat het ontwerp als voltooid wordt beschouwd en alle wijzigingen kunnen worden gewijzigd.

## VOORBEELDEN

### Voorbeeld 1

Hiermee wordt de lijst met momenteel geregistreerde experimentele functies en de huidige status opgehaald.

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## PARAMETERS

### -Name

Naam of namen van specifieke experimentele functies die moeten worden geretourneerd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System.String[]

Naam of namen van experimentele functies die moeten worden geretourneerd.

## UITVOER

### ExperimentalFeature

Retourneert instanties die overeenkomen met de aangevraagde namen of alle experimentele functies als er geen naam is opgegeven.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Enable-ExperimentalFeature.md)
