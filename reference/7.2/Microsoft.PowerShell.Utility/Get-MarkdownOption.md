---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-MarkdownOption
ms.openlocfilehash: 0da0c869216fd2a044fe03faad25e3de6f3fb8fd
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195689"
---
# Get-MarkdownOption

## SAMENVATTING
Retourneert de huidige kleuren en stijlen die worden gebruikt voor het weer geven van de inhoud van de korting op de-console.

## SYNTAXIS

```
Get-MarkdownOption [<CommonParameters>]
```

## BESCHRIJVING

Retourneert de huidige kleuren en stijlen die worden gebruikt voor het weer geven van de inhoud van de korting op de-console. De teken reeksen die worden weer gegeven in de uitvoer van deze cmdlet, bevatten de ANSI-escape codes die worden gebruikt om de kleur en stijl van de gerenderde tekst van de prijs opgave te wijzigen.

Zie de [CommonMark](https://commonmark.org/) -website voor meer informatie over de prijs verlaging.

## VOORBEELDEN

### Voor beeld 1: de huidige kleuren en stijl ophalen

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> De teken reeks waarden die in de uitvoer worden weer gegeven, zijn de tekens die volgen op het **Escape** teken ( `[char]0x1B` ) voor de ANSI-escape reeks. Zie [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)voor meer informatie over ANSI escape-codes.

## PARAMETERS

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

## UITVOER

### Micro soft. Power shell. MarkdownRender. PSMarkdownOptionInfo

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Set-MarkdownOption](Set-MarkdownOption.md)

[ConvertFrom-prijs verlaging](ConvertFrom-Markdown.md)

[Weer geven-prijs verlaging](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)

