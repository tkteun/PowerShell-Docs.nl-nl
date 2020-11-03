---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: Power shell, cmdlet, prijs verlaging
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: 9f070819491b87b02868dffdfbe25bf5d72ecab8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251174"
---
# <span data-ttu-id="c4694-103">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="c4694-103">ConvertFrom-Markdown</span></span>

## <span data-ttu-id="c4694-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="c4694-104">SYNOPSIS</span></span>
<span data-ttu-id="c4694-105">De inhoud van een teken reeks of een bestand converteren naar een **MarkdownInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="c4694-105">Convert the contents of a string or a file to a **MarkdownInfo** object.</span></span>

## <span data-ttu-id="c4694-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c4694-106">SYNTAX</span></span>

### <span data-ttu-id="c4694-107">PathParamSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="c4694-107">PathParamSet (Default)</span></span>

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="c4694-108">LiteralParamSet</span><span class="sxs-lookup"><span data-stu-id="c4694-108">LiteralParamSet</span></span>

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="c4694-109">InputObjParamSet</span><span class="sxs-lookup"><span data-stu-id="c4694-109">InputObjParamSet</span></span>

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## <span data-ttu-id="c4694-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c4694-110">DESCRIPTION</span></span>

<span data-ttu-id="c4694-111">Met deze cmdlet wordt de opgegeven inhoud geconverteerd naar een **MarkdownInfo**.</span><span class="sxs-lookup"><span data-stu-id="c4694-111">This cmdlet converts the specified content into a **MarkdownInfo**.</span></span> <span data-ttu-id="c4694-112">Wanneer een bestandspad is opgegeven voor de para meter **Path** , wordt de inhoud van het bestand geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-112">When a file path is specified for the **Path** parameter, the contents on the file are converted.</span></span> <span data-ttu-id="c4694-113">Het uitvoer object heeft drie eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="c4694-113">The output object has three properties:</span></span>

- <span data-ttu-id="c4694-114">De eigenschap **token** heeft de abstracte syntaxis structuur (AST) van het geconverteerde object</span><span class="sxs-lookup"><span data-stu-id="c4694-114">The **Token** property has the abstract syntax tree (AST) of the the converted object</span></span>
- <span data-ttu-id="c4694-115">De eigenschap **HTML** heeft de HTML-conversie van de opgegeven invoer</span><span class="sxs-lookup"><span data-stu-id="c4694-115">The **Html** property has the HTML conversion of the specified input</span></span>
- <span data-ttu-id="c4694-116">De eigenschap **VT100EncodedString** heeft de geconverteerde teken reeks met ANSI (VT100) escape-reeksen als de para meter **AsVT100EncodedString** is opgegeven</span><span class="sxs-lookup"><span data-stu-id="c4694-116">The **VT100EncodedString** property has the converted string with ANSI (VT100) escape sequences if the **AsVT100EncodedString** parameter was specified</span></span>

<span data-ttu-id="c4694-117">Deze cmdlet is geïntroduceerd in Power shell 6,1.</span><span class="sxs-lookup"><span data-stu-id="c4694-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="c4694-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c4694-118">EXAMPLES</span></span>

### <span data-ttu-id="c4694-119">Voor beeld 1: een bestand met de inhoud van de prijs verlaging converteren naar HTML</span><span class="sxs-lookup"><span data-stu-id="c4694-119">Example 1: Convert a file containing Markdown content to HTML</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md
```

<span data-ttu-id="c4694-120">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-120">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="c4694-121">De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="c4694-121">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="c4694-122">De **HTML-** eigenschap bevat de HTML-inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="c4694-122">The **Html** property has the HTML converted content of the `README.md` file.</span></span>

### <span data-ttu-id="c4694-123">Voor beeld 2: een bestand met de inhoud van de prijs opwaarde converteren naar een VT100-gecodeerde teken reeks</span><span class="sxs-lookup"><span data-stu-id="c4694-123">Example 2: Convert a file containing Markdown content to a VT100-encoded string</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

<span data-ttu-id="c4694-124">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-124">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="c4694-125">De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="c4694-125">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="c4694-126">De eigenschap **VT100EncodedString** heeft de door VT100 versleutelde teken reeks die inhoud van het bestand heeft geconverteerd `README.md` .</span><span class="sxs-lookup"><span data-stu-id="c4694-126">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="c4694-127">Voor beeld 3: een invoer object met de inhoud van de prijs opwaarde converteren naar een VT100-gecodeerde teken reeks</span><span class="sxs-lookup"><span data-stu-id="c4694-127">Example 3: Convert input object containing Markdown content to a VT100-encoded string</span></span>

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="c4694-128">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-128">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="c4694-129">Het **file info** -object van `Get-Item` wordt geconverteerd naar een met VT100 versleutelde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c4694-129">The **FileInfo** object from `Get-Item` is converted to a VT100-encoded string.</span></span> <span data-ttu-id="c4694-130">De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="c4694-130">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="c4694-131">De eigenschap **VT100EncodedString** heeft de door VT100 versleutelde teken reeks die inhoud van het bestand heeft geconverteerd `README.md` .</span><span class="sxs-lookup"><span data-stu-id="c4694-131">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="c4694-132">Voor beeld 4: een teken reeks met de inhoud van de prijs opwaarderen naar een VT100-gecodeerde teken reeks</span><span class="sxs-lookup"><span data-stu-id="c4694-132">Example 4: Convert a string containing Markdown content to a VT100-encoded string</span></span>

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="c4694-133">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-133">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="c4694-134">De opgegeven teken reeks `**Bold text**` wordt geconverteerd naar een in VT100 versleutelde teken reeks en is beschikbaar in de eigenschap **VT100EncodedString** .</span><span class="sxs-lookup"><span data-stu-id="c4694-134">The specified string `**Bold text**` is converted to a VT100-encoded string and available in **VT100EncodedString** property.</span></span>

## <span data-ttu-id="c4694-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c4694-135">PARAMETERS</span></span>

### <span data-ttu-id="c4694-136">-AsVT100EncodedString</span><span class="sxs-lookup"><span data-stu-id="c4694-136">-AsVT100EncodedString</span></span>

<span data-ttu-id="c4694-137">Geeft aan of de uitvoer moet worden gecodeerd als een teken reeks met VT100-escape codes.</span><span class="sxs-lookup"><span data-stu-id="c4694-137">Specifies if the output should be encoded as a string with VT100 escape codes.</span></span>

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

### <span data-ttu-id="c4694-138">-Input object</span><span class="sxs-lookup"><span data-stu-id="c4694-138">-InputObject</span></span>

<span data-ttu-id="c4694-139">Geeft het object aan dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-139">Specifies the object to be converted.</span></span> <span data-ttu-id="c4694-140">Wanneer een object van het type **System. String** wordt opgegeven, wordt de teken reeks geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-140">When an object of type **System.String** is specified, the string is converted.</span></span> <span data-ttu-id="c4694-141">Wanneer een object van het type **System. io. file info** is opgegeven, wordt de inhoud van het bestand dat is opgegeven door het object geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-141">When an object of type **System.IO.FileInfo** is specified, the contents of the file specified by the object are converted.</span></span> <span data-ttu-id="c4694-142">Objecten van elk ander type resulteren in een fout.</span><span class="sxs-lookup"><span data-stu-id="c4694-142">Objects of any other type result in an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c4694-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c4694-143">-LiteralPath</span></span>

<span data-ttu-id="c4694-144">Hiermee geeft u een pad op naar het bestand dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-144">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c4694-145">-Path</span><span class="sxs-lookup"><span data-stu-id="c4694-145">-Path</span></span>

<span data-ttu-id="c4694-146">Hiermee geeft u een pad op naar het bestand dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="c4694-146">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="c4694-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4694-147">CommonParameters</span></span>

<span data-ttu-id="c4694-148">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4694-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4694-149">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c4694-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4694-150">INVOER</span><span class="sxs-lookup"><span data-stu-id="c4694-150">INPUTS</span></span>

### <span data-ttu-id="c4694-151">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="c4694-151">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="c4694-152">UITVOER</span><span class="sxs-lookup"><span data-stu-id="c4694-152">OUTPUTS</span></span>

### <span data-ttu-id="c4694-153">Micro soft. Power shell. MarkdownRender. MarkdownInfo</span><span class="sxs-lookup"><span data-stu-id="c4694-153">Microsoft.PowerShell.MarkdownRender.MarkdownInfo</span></span>

## <span data-ttu-id="c4694-154">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="c4694-154">NOTES</span></span>

## <span data-ttu-id="c4694-155">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="c4694-155">RELATED LINKS</span></span>

[<span data-ttu-id="c4694-156">Parser prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="c4694-156">Markdown Parser</span></span>](https://github.com/lunet-io/markdig)

[<span data-ttu-id="c4694-157">ANSI escape-code</span><span class="sxs-lookup"><span data-stu-id="c4694-157">ANSI escape code</span></span>](https://wikipedia.org/wiki/ANSI_escape_code)

