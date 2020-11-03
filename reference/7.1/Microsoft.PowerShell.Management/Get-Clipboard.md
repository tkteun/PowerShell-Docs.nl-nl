---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: da1df360d7c471d925bd2f57f5258ecb2d60e631
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/03/2020
ms.locfileid: "93253297"
---
# Get-Clipboard

## SAMENVATTING
Hiermee haalt u de inhoud van het klem bord.

## SYNTAXIS

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## BESCHRIJVING

`Get-Clipboard`Met de cmdlet wordt de inhoud van het klem bord opgehaald als tekst. Meerdere tekst regels worden geretourneerd als een matrix met teken reeksen die vergelijkbaar zijn met `Get-Content` .

> [!NOTE]
> Op Linux moet voor deze cmdlet het `xclip` hulp programma zich in het pad bevinden.

## VOORBEELDEN

### Voor beeld 1: de inhoud van het klem bord ophalen en weer geven op de opdracht regel

In dit voor beeld is de tekst ' Hello ' naar het klem bord gekopieerd.

```powershell
Get-Clipboard
```

```Output
hello
```

## PARAMETERS

### -RAW

Hiermee haalt u de volledige inhoud van het klem bord. Tekst met meerdere regels wordt geretourneerd als één teken reeks in plaats van een matrix met teken reeksen.

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

## UITVOER

### System. String

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Set-klem bord](Set-Clipboard.md)

