---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: e9170a8023977f485a99e5e7fc59fb2280a8081e
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347581"
---
# Get-ComputerInfo

## SAMENVATTING
Hiermee haalt u een geconsolideerd object op met de eigenschappen van het systeem en het besturings systeem.

## SYNTAXIS

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-ComputerInfo` cmdlet haalt een geconsolideerd object op van de eigenschappen van het systeem en het besturings systeem.
Deze cmdlet is geïntroduceerd in Windows Power shell 5,1.

## VOORBEELDEN

### Voor beeld 1: alle computer Eigenschappen ophalen

```powershell
Get-ComputerInfo
```

Met deze opdracht worden alle eigenschappen van het systeem en het besturings systeem van de computer opgehaald.

### Voor beeld 2: alle eigenschappen van het besturings systeem van de computer ophalen

```powershell
Get-ComputerInfo -Property "os*"
```

Met deze opdracht worden alle eigenschappen van het besturings systeem van de computer opgehaald.

## PARAMETERS

### -Eigenschap

Hiermee geeft u als een teken reeks matrix de computer eigenschappen op waarin deze cmdlet wordt weer gegeven.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.

## INVOER

### System.String[]

## UITVOER

### Micro soft. Power shell. Management. ComputerInfo

## OPMERKINGEN

Deze cmdlet is alleen beschikbaar op Windows-platforms.

## GERELATEERDE KOPPELINGEN
