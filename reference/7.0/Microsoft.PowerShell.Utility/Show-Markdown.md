---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: bb73853c8432bcd4fcc900ee1d6fc620ed883ebb
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249501"
---
# <span data-ttu-id="7a9de-103">Show-Markdown</span><span class="sxs-lookup"><span data-stu-id="7a9de-103">Show-Markdown</span></span>

## <span data-ttu-id="7a9de-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="7a9de-104">SYNOPSIS</span></span>
<span data-ttu-id="7a9de-105">Toont een bestand of teken reeks in de-console op een beschrijvende manier met VT100-escape reeksen of in een browser met behulp van HTML.</span><span class="sxs-lookup"><span data-stu-id="7a9de-105">Shows a Markdown file or string in the console in a friendly way using VT100 escape sequences or in a browser using HTML.</span></span>

## <span data-ttu-id="7a9de-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="7a9de-106">SYNTAX</span></span>

### <span data-ttu-id="7a9de-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="7a9de-107">Path (Default)</span></span>

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="7a9de-108">Input object</span><span class="sxs-lookup"><span data-stu-id="7a9de-108">InputObject</span></span>

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### <span data-ttu-id="7a9de-109">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a9de-109">LiteralPath</span></span>

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## <span data-ttu-id="7a9de-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="7a9de-110">DESCRIPTION</span></span>

<span data-ttu-id="7a9de-111">De `Show-Markdown` cmdlet wordt gebruikt om de prijs verlaging te genereren in een lees bare vorm in een Terminal of in een browser.</span><span class="sxs-lookup"><span data-stu-id="7a9de-111">The `Show-Markdown` cmdlet is used to render Markdown in a human readable format either in a terminal or in a browser.</span></span>

<span data-ttu-id="7a9de-112">`Show-Markdown` kan een teken reeks retour neren die de VT100-escape reeksen bevat die door de terminal worden weer gegeven (als deze ondersteuning biedt voor VT100-escape reeksen).</span><span class="sxs-lookup"><span data-stu-id="7a9de-112">`Show-Markdown` can return a string that includes the VT100 escape sequences which the terminal renders (if it supports VT100 escape sequences).</span></span> <span data-ttu-id="7a9de-113">Dit wordt voornamelijk gebruikt voor het weer geven van de kortings bestanden in een Terminal.</span><span class="sxs-lookup"><span data-stu-id="7a9de-113">This is primarily used for viewing Markdown files in a terminal.</span></span> <span data-ttu-id="7a9de-114">U kunt deze teken reeks ook ophalen via de `ConvertFrom-Markdown` door de para meter **AsVT100EncodedString** op te geven.</span><span class="sxs-lookup"><span data-stu-id="7a9de-114">You can also get this string via the `ConvertFrom-Markdown` by specifying the **AsVT100EncodedString** parameter.</span></span>

<span data-ttu-id="7a9de-115">`Show-Markdown` biedt ook de mogelijkheid om een browser te openen en een gerenderde versie van de prijs opgave weer te geven.</span><span class="sxs-lookup"><span data-stu-id="7a9de-115">`Show-Markdown` also has the ability to open a browser and show you a rendered version of the Markdown.</span></span> <span data-ttu-id="7a9de-116">De korting wordt weer gegeven door deze in HTML in te scha kelen en het HTML-bestand te openen in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="7a9de-116">It renders the Markdown by turning it into HTML and opening the HTML file in your default browser.</span></span>

<span data-ttu-id="7a9de-117">U kunt wijzigen hoe `Show-Markdown` de prestaties van een terminal worden geprijsd met behulp van `Set-MarkdownOption` .</span><span class="sxs-lookup"><span data-stu-id="7a9de-117">You can change how `Show-Markdown` renders Markdown in a terminal by using `Set-MarkdownOption`.</span></span>

<span data-ttu-id="7a9de-118">Deze cmdlet is geïntroduceerd in Power shell 6,1.</span><span class="sxs-lookup"><span data-stu-id="7a9de-118">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="7a9de-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="7a9de-119">EXAMPLES</span></span>

### <span data-ttu-id="7a9de-120">Voor beeld 1: eenvoudig voor beeld van een pad opgeven</span><span class="sxs-lookup"><span data-stu-id="7a9de-120">Example 1: Simple example specifying a path</span></span>

```powershell
Show-Markdown -Path ./README.md
```

### <span data-ttu-id="7a9de-121">Voor beeld 2: een eenvoudig voor beeld van een teken reeks opgeven</span><span class="sxs-lookup"><span data-stu-id="7a9de-121">Example 2: Simple example specifying a string</span></span>

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### <span data-ttu-id="7a9de-122">Voor beeld 2: de prijs verlaging wordt geopend in een browser</span><span class="sxs-lookup"><span data-stu-id="7a9de-122">Example 2: Opening Markdown in a browser</span></span>

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## <span data-ttu-id="7a9de-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7a9de-123">PARAMETERS</span></span>

### <span data-ttu-id="7a9de-124">-Input object</span><span class="sxs-lookup"><span data-stu-id="7a9de-124">-InputObject</span></span>

<span data-ttu-id="7a9de-125">Een kortings teken reeks die wordt weer gegeven in de Terminal.</span><span class="sxs-lookup"><span data-stu-id="7a9de-125">A Markdown string that will be shown in the terminal.</span></span> <span data-ttu-id="7a9de-126">Als u geen ondersteunde indeling doorgeeft, `Show-Markdown` wordt een fout bericht weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="7a9de-126">If you do not pass in a supported format, `Show-Markdown` will emit an error.</span></span>

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

### <span data-ttu-id="7a9de-127">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7a9de-127">-LiteralPath</span></span>

<span data-ttu-id="7a9de-128">Hiermee geeft u het pad op naar het bestand voor een afkorting.</span><span class="sxs-lookup"><span data-stu-id="7a9de-128">Specifies the path to a Markdown file.</span></span> <span data-ttu-id="7a9de-129">In tegens telling tot de para meter path wordt de waarde van LiteralPath precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="7a9de-129">Unlike the Path parameter, the value of LiteralPath is used exactly as it is typed.</span></span> <span data-ttu-id="7a9de-130">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="7a9de-130">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7a9de-131">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="7a9de-131">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7a9de-132">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="7a9de-132">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="7a9de-133">-Path</span><span class="sxs-lookup"><span data-stu-id="7a9de-133">-Path</span></span>

<span data-ttu-id="7a9de-134">Hiermee geeft u het pad op naar het bestand voor afkorting dat moet worden gerenderd.</span><span class="sxs-lookup"><span data-stu-id="7a9de-134">Specifies the path to a Markdown file to be rendered.</span></span>

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

### <span data-ttu-id="7a9de-135">-UseBrowser</span><span class="sxs-lookup"><span data-stu-id="7a9de-135">-UseBrowser</span></span>

<span data-ttu-id="7a9de-136">Compileert de invoer voor de prijs verlaging als HTML en opent deze in de standaard browser.</span><span class="sxs-lookup"><span data-stu-id="7a9de-136">Compiles the Markdown input as HTML and opens it in your default browser.</span></span>

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

### <span data-ttu-id="7a9de-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a9de-137">CommonParameters</span></span>

<span data-ttu-id="7a9de-138">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a9de-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a9de-139">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7a9de-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a9de-140">INVOER</span><span class="sxs-lookup"><span data-stu-id="7a9de-140">INPUTS</span></span>

### <span data-ttu-id="7a9de-141">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7a9de-141">System.Management.Automation.PSObject</span></span>

### <span data-ttu-id="7a9de-142">System.String[]</span><span class="sxs-lookup"><span data-stu-id="7a9de-142">System.String[]</span></span>

## <span data-ttu-id="7a9de-143">UITVOER</span><span class="sxs-lookup"><span data-stu-id="7a9de-143">OUTPUTS</span></span>

### <span data-ttu-id="7a9de-144">System. String</span><span class="sxs-lookup"><span data-stu-id="7a9de-144">System.String</span></span>

## <span data-ttu-id="7a9de-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="7a9de-145">NOTES</span></span>

## <span data-ttu-id="7a9de-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="7a9de-146">RELATED LINKS</span></span>

[<span data-ttu-id="7a9de-147">ConvertFrom-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="7a9de-147">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)
