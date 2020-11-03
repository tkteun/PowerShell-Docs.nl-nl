---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: 52c0a94304156a7c1cf89bbc5ae98a0668789bd2
ms.sourcegitcommit: 23ea4a36ee85f923684657de5313a5adf0b6b094
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/21/2020
ms.locfileid: "93247161"
---
# <span data-ttu-id="84de2-101">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="84de2-101">Get-MarkdownOption</span></span>

## <span data-ttu-id="84de2-102">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="84de2-102">SYNOPSIS</span></span>
<span data-ttu-id="84de2-103">Retourneert de huidige kleuren en stijlen die worden gebruikt voor het weer geven van de inhoud van de korting op de-console.</span><span class="sxs-lookup"><span data-stu-id="84de2-103">Returns the current colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="84de2-104">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="84de2-104">SYNTAX</span></span>

```
Get-MarkdownOption [<CommonParameters>]
```

## <span data-ttu-id="84de2-105">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="84de2-105">DESCRIPTION</span></span>

<span data-ttu-id="84de2-106">Retourneert de huidige kleuren en stijlen die worden gebruikt voor het weer geven van de inhoud van de korting op de-console.</span><span class="sxs-lookup"><span data-stu-id="84de2-106">Returns the current colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="84de2-107">De teken reeksen die worden weer gegeven in de uitvoer van deze cmdlet, bevatten de ANSI-escape codes die worden gebruikt om de kleur en stijl van de gerenderde tekst van de prijs opgave te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="84de2-107">The strings displayed in the output of this cmdlet contain the ANSI escape codes used to change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="84de2-108">Zie de [CommonMark](https://commonmark.org/) -website voor meer informatie over de prijs verlaging.</span><span class="sxs-lookup"><span data-stu-id="84de2-108">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

## <span data-ttu-id="84de2-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="84de2-109">EXAMPLES</span></span>

### <span data-ttu-id="84de2-110">Voor beeld 1: de huidige kleuren en stijl ophalen</span><span class="sxs-lookup"><span data-stu-id="84de2-110">Example 1 - Get the current colors and style</span></span>

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
> <span data-ttu-id="84de2-111">De teken reeks waarden die in de uitvoer worden weer gegeven, zijn de tekens die volgen op het **Escape** teken ( `[char]0x1B` ) voor de ANSI-escape reeks.</span><span class="sxs-lookup"><span data-stu-id="84de2-111">The string values shown in the output are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="84de2-112">Zie [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)voor meer informatie over ANSI escape-codes.</span><span class="sxs-lookup"><span data-stu-id="84de2-112">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="84de2-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="84de2-113">PARAMETERS</span></span>

### <span data-ttu-id="84de2-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="84de2-114">CommonParameters</span></span>

<span data-ttu-id="84de2-115">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="84de2-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="84de2-116">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="84de2-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="84de2-117">INVOER</span><span class="sxs-lookup"><span data-stu-id="84de2-117">INPUTS</span></span>

### <span data-ttu-id="84de2-118">Geen</span><span class="sxs-lookup"><span data-stu-id="84de2-118">None</span></span>

## <span data-ttu-id="84de2-119">UITVOER</span><span class="sxs-lookup"><span data-stu-id="84de2-119">OUTPUTS</span></span>

### <span data-ttu-id="84de2-120">Micro soft. Power shell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="84de2-120">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="84de2-121">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="84de2-121">NOTES</span></span>

## <span data-ttu-id="84de2-122">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="84de2-122">RELATED LINKS</span></span>

[<span data-ttu-id="84de2-123">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="84de2-123">Set-MarkdownOption</span></span>](Set-MarkdownOption.md)

[<span data-ttu-id="84de2-124">ConvertFrom-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="84de2-124">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="84de2-125">Weer geven-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="84de2-125">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="84de2-126">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="84de2-126">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="84de2-127">CommonMark</span><span class="sxs-lookup"><span data-stu-id="84de2-127">CommonMark</span></span>](https://commonmark.org/)

