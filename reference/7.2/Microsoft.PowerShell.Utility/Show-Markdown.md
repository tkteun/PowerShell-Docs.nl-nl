---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: d14e6332a2da5c86c4f8ada0d110c64e080437e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705812"
---
# <span data-ttu-id="6ef89-102">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="6ef89-102">Show-Markdown</span></span>

## <span data-ttu-id="6ef89-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="6ef89-103">SYNOPSIS</span></span>
<span data-ttu-id="6ef89-104">Toont een bestand of teken reeks in de-console op een beschrijvende manier met VT100-escape reeksen of in een browser met behulp van HTML.</span><span class="sxs-lookup"><span data-stu-id="6ef89-104">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="6ef89-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6ef89-105">SYNTAX</span></span>

### <span data-ttu-id="6ef89-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="6ef89-106">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="6ef89-107">Input object</span><span class="sxs-lookup"><span data-stu-id="6ef89-107">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="6ef89-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6ef89-108">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="6ef89-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6ef89-109">DESCRIPTION</span></span>

<span data-ttu-id="6ef89-110">De `Show-Markdown` cmdlet wordt gebruikt om de prijs verlaging te genereren in een lees bare vorm in een Terminal of in een browser.</span><span class="sxs-lookup"><span data-stu-id="6ef89-110">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="6ef89-111">`Show-Markdown` kan een teken reeks retour neren die de VT100-escape reeksen bevat die door de terminal worden weer gegeven (als deze ondersteuning biedt voor VT100-escape reeksen).</span><span class="sxs-lookup"><span data-stu-id="6ef89-111">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="6ef89-112">Dit wordt voornamelijk gebruikt voor het weer geven van de kortings bestanden in een Terminal.</span><span class="sxs-lookup"><span data-stu-id="6ef89-112">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="6ef89-113">U kunt deze teken reeks ook ophalen via de `ConvertFrom-Markdown` door de para meter **AsVT100EncodedString** op te geven.</span><span class="sxs-lookup"><span data-stu-id="6ef89-113">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="6ef89-114">`Show-Markdown` biedt ook de mogelijkheid om een browser te openen en een gerenderde versie van de prijs opgave weer te geven.</span><span class="sxs-lookup"><span data-stu-id="6ef89-114">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="6ef89-115">De korting wordt weer gegeven door deze in HTML in te scha kelen en het HTML-bestand te openen in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="6ef89-115">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="6ef89-116">U kunt wijzigen hoe `Show-Markdown` de prestaties van een terminal worden geprijsd met behulp van `Set-MarkdownOption` .</span><span class="sxs-lookup"><span data-stu-id="6ef89-116">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="6ef89-117">Deze cmdlet is geïntroduceerd in Power shell 6,1.</span><span class="sxs-lookup"><span data-stu-id="6ef89-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="6ef89-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6ef89-118">EXAMPLES</span></span>

### <span data-ttu-id="6ef89-119">Voor beeld 1: eenvoudig voor beeld van een pad opgeven</span><span class="sxs-lookup"><span data-stu-id="6ef89-119">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="6ef89-120">Voor beeld 2: een eenvoudig voor beeld van een teken reeks opgeven</span><span class="sxs-lookup"><span data-stu-id="6ef89-120">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="6ef89-121">Voor beeld 2: de prijs verlaging wordt geopend in een browser</span><span class="sxs-lookup"><span data-stu-id="6ef89-121">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="6ef89-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6ef89-122">PARAMETERS</span></span>

### <span data-ttu-id="6ef89-123">-Input object</span><span class="sxs-lookup"><span data-stu-id="6ef89-123">-InputObject</span></span>

<span data-ttu-id="6ef89-124">Een kortings teken reeks die wordt weer gegeven in de Terminal.</span><span class="sxs-lookup"><span data-stu-id="6ef89-124">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="6ef89-125">Als u geen ondersteunde indeling doorgeeft, `Show-Markdown` wordt een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="6ef89-125">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6ef89-126">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="6ef89-126">-LiteralPath</span></span>

<span data-ttu-id="6ef89-127">Hiermee geeft u het pad op naar het bestand voor een afkorting.</span><span class="sxs-lookup"><span data-stu-id="6ef89-127">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="6ef89-128">In tegens telling tot de para meter path wordt de waarde van LiteralPath precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="6ef89-128">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="6ef89-129">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="6ef89-129">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="6ef89-130">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="6ef89-130">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="6ef89-131">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="6ef89-131">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ef89-132">-Path</span><span class="sxs-lookup"><span data-stu-id="6ef89-132">-Path</span></span>

<span data-ttu-id="6ef89-133">Hiermee geeft u het pad op naar het bestand voor afkorting dat moet worden gerenderd.</span><span class="sxs-lookup"><span data-stu-id="6ef89-133">Specifies the path to a Markdown file to be rendered.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6ef89-134">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="6ef89-134">-UseBrowser</span></span>

<span data-ttu-id="6ef89-135">Compileert de invoer voor de prijs verlaging als HTML en opent deze in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="6ef89-135">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ef89-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ef89-136">CommonParameters</span></span>

<span data-ttu-id="6ef89-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6ef89-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ef89-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6ef89-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ef89-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="6ef89-139">INPUTS</span></span>

### <span data-ttu-id="6ef89-140">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="6ef89-140">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="6ef89-141">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6ef89-141">System.String[]</span></span>

## <span data-ttu-id="6ef89-142">UITVOER</span><span class="sxs-lookup"><span data-stu-id="6ef89-142">OUTPUTS</span></span>

### <span data-ttu-id="6ef89-143">System. String</span><span class="sxs-lookup"><span data-stu-id="6ef89-143">System.String</span></span>

## <span data-ttu-id="6ef89-144">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="6ef89-144">NOTES</span></span>

## <span data-ttu-id="6ef89-145">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="6ef89-145">RELATED LINKS</span></span>

[<span data-ttu-id="6ef89-146">ConvertFrom-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="6ef89-146">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

