---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-MarkdownOption
ms.openlocfilehash: b4dec8766b283dd16ccee0e73dd893582ed5fc8e
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194482"
---
# <span data-ttu-id="14926-102">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="14926-102">Get-MarkdownOption</span></span>

## <span data-ttu-id="14926-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="14926-103">SYNOPSIS</span></span>
<span data-ttu-id="14926-104">Retourneert de huidige kleuren en stijlen die worden gebruikt voor het weer geven van de inhoud van de korting op de-console.</span><span class="sxs-lookup"><span data-stu-id="14926-104">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="14926-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="14926-105">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="14926-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="14926-106">DESCRIPTION</span></span>

<span data-ttu-id="14926-107">Retourneert de huidige kleuren en stijlen die worden gebruikt voor het weer geven van de inhoud van de korting op de-console.</span><span class="sxs-lookup"><span data-stu-id="14926-107">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="14926-108">De teken reeksen die worden weer gegeven in de uitvoer van deze cmdlet, bevatten de ANSI-escape codes die worden gebruikt om de kleur en stijl van de gerenderde tekst van de prijs opgave te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="14926-108">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="14926-109">Zie de [CommonMark](https://commonmark.org/) -website voor meer informatie over de prijs verlaging.</span><span class="sxs-lookup"><span data-stu-id="14926-109">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="14926-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="14926-110">EXAMPLES</span></span>

### <span data-ttu-id="14926-111">Voor beeld 1: de huidige kleuren en stijl ophalen</span><span class="sxs-lookup"><span data-stu-id="14926-111">Example 1 - Get the current colors and style</span></span>

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
> <span data-ttu-id="14926-112">De teken reeks waarden die in de uitvoer worden weer gegeven, zijn de tekens die volgen op het **Escape** teken ( `[char]0x1B` ) voor de ANSI-escape reeks.</span><span class="sxs-lookup"><span data-stu-id="14926-112">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="14926-113">Zie [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)voor meer informatie over ANSI escape-codes.</span><span class="sxs-lookup"><span data-stu-id="14926-113">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="14926-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="14926-114">PARAMETERS</span></span>

### <span data-ttu-id="14926-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14926-115">CommonParameters</span></span>

<span data-ttu-id="14926-116">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14926-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14926-117">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="14926-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14926-118">INVOER</span><span class="sxs-lookup"><span data-stu-id="14926-118">INPUTS</span></span>

### <span data-ttu-id="14926-119">Geen</span><span class="sxs-lookup"><span data-stu-id="14926-119">None</span></span>

## <span data-ttu-id="14926-120">UITVOER</span><span class="sxs-lookup"><span data-stu-id="14926-120">OUTPUTS</span></span>

### <span data-ttu-id="14926-121">Micro soft. Power shell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="14926-121">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="14926-122">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="14926-122">NOTES</span></span>

## <span data-ttu-id="14926-123">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="14926-123">RELATED LINKS</span></span>

[<span data-ttu-id="14926-124">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="14926-124">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="14926-125">ConvertFrom-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="14926-125">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="14926-126">Weer geven-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="14926-126">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="14926-127">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="14926-127">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="14926-128">CommonMark</span><span class="sxs-lookup"><span data-stu-id="14926-128">CommonMark</span></span>](https://commonmark.org/)
