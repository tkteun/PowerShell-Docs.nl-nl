---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: c694e73e69c1e51ecf88f445684923ef5f19113f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705848"
---
# <span data-ttu-id="8b9a0-102">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="8b9a0-102">ConvertFrom-Markdown</span></span>

## <span data-ttu-id="8b9a0-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="8b9a0-103">SYNOPSIS</span></span>
<span data-ttu-id="8b9a0-104">De inhoud van een teken reeks of een bestand converteren naar een **MarkdownInfo** -object.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-104">Convert the contents of a string or a file to a **MarkdownInfo** object.</span></span>

## <span data-ttu-id="8b9a0-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="8b9a0-105">SYNTAX</span></span>

### <span data-ttu-id="8b9a0-106">PathParamSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="8b9a0-106">PathParamSet (Default)</span></span>

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="8b9a0-107">LiteralParamSet</span><span class="sxs-lookup"><span data-stu-id="8b9a0-107">LiteralParamSet</span></span>

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="8b9a0-108">InputObjParamSet</span><span class="sxs-lookup"><span data-stu-id="8b9a0-108">InputObjParamSet</span></span>

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## <span data-ttu-id="8b9a0-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="8b9a0-109">DESCRIPTION</span></span>

<span data-ttu-id="8b9a0-110">Met deze cmdlet wordt de opgegeven inhoud geconverteerd naar een **MarkdownInfo**.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-110">This cmdlet converts the specified content into a **MarkdownInfo**.</span></span> <span data-ttu-id="8b9a0-111">Wanneer een bestandspad is opgegeven voor de para meter **Path** , wordt de inhoud van het bestand geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-111">When a file path is specified for the **Path** parameter, the contents on the file are converted.</span></span> <span data-ttu-id="8b9a0-112">Het uitvoer object heeft drie eigenschappen:</span><span class="sxs-lookup"><span data-stu-id="8b9a0-112">The output object has three properties:</span></span>

- <span data-ttu-id="8b9a0-113">De eigenschap **token** heeft de abstracte syntaxis structuur (AST) van het geconverteerde object</span><span class="sxs-lookup"><span data-stu-id="8b9a0-113">The **Token** property has the abstract syntax tree (AST) of the the converted object</span></span>
- <span data-ttu-id="8b9a0-114">De eigenschap **HTML** heeft de HTML-conversie van de opgegeven invoer</span><span class="sxs-lookup"><span data-stu-id="8b9a0-114">The **Html** property has the HTML conversion of the specified input</span></span>
- <span data-ttu-id="8b9a0-115">De eigenschap **VT100EncodedString** heeft de geconverteerde teken reeks met ANSI (VT100) escape-reeksen als de para meter **AsVT100EncodedString** is opgegeven</span><span class="sxs-lookup"><span data-stu-id="8b9a0-115">The **VT100EncodedString** property has the converted string with ANSI (VT100) escape sequences if the **AsVT100EncodedString** parameter was specified</span></span>

<span data-ttu-id="8b9a0-116">Deze cmdlet is geïntroduceerd in Power shell 6,1.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-116">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="8b9a0-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="8b9a0-117">EXAMPLES</span></span>

### <span data-ttu-id="8b9a0-118">Voor beeld 1: een bestand met de inhoud van de prijs verlaging converteren naar HTML</span><span class="sxs-lookup"><span data-stu-id="8b9a0-118">Example 1: Convert a file containing Markdown content to HTML</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md
```

<span data-ttu-id="8b9a0-119">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-119">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="8b9a0-120">De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-120">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="8b9a0-121">De **HTML-** eigenschap bevat de HTML-inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-121">The **Html** property has the HTML converted content of the `README.md` file.</span></span>

### <span data-ttu-id="8b9a0-122">Voor beeld 2: een bestand met de inhoud van de prijs opwaarde converteren naar een VT100-gecodeerde teken reeks</span><span class="sxs-lookup"><span data-stu-id="8b9a0-122">Example 2: Convert a file containing Markdown content to a VT100-encoded string</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

<span data-ttu-id="8b9a0-123">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-123">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="8b9a0-124">De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-124">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="8b9a0-125">De eigenschap **VT100EncodedString** heeft de door VT100 versleutelde teken reeks die inhoud van het bestand heeft geconverteerd `README.md` .</span><span class="sxs-lookup"><span data-stu-id="8b9a0-125">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="8b9a0-126">Voor beeld 3: een invoer object met de inhoud van de prijs opwaarde converteren naar een VT100-gecodeerde teken reeks</span><span class="sxs-lookup"><span data-stu-id="8b9a0-126">Example 3: Convert input object containing Markdown content to a VT100-encoded string</span></span>

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="8b9a0-127">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-127">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="8b9a0-128">Het **file info** -object van `Get-Item` wordt geconverteerd naar een met VT100 versleutelde teken reeks.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-128">The **FileInfo** object from `Get-Item` is converted to a VT100-encoded string.</span></span> <span data-ttu-id="8b9a0-129">De eigenschap **tokens** heeft de AST van de geconverteerde inhoud van het `README.md` bestand.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-129">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="8b9a0-130">De eigenschap **VT100EncodedString** heeft de door VT100 versleutelde teken reeks die inhoud van het bestand heeft geconverteerd `README.md` .</span><span class="sxs-lookup"><span data-stu-id="8b9a0-130">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="8b9a0-131">Voor beeld 4: een teken reeks met de inhoud van de prijs opwaarderen naar een VT100-gecodeerde teken reeks</span><span class="sxs-lookup"><span data-stu-id="8b9a0-131">Example 4: Convert a string containing Markdown content to a VT100-encoded string</span></span>

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="8b9a0-132">Het **MarkdownInfo** -object wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-132">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="8b9a0-133">De opgegeven teken reeks `**Bold text**` wordt geconverteerd naar een in VT100 versleutelde teken reeks en is beschikbaar in de eigenschap **VT100EncodedString** .</span><span class="sxs-lookup"><span data-stu-id="8b9a0-133">The specified string `**Bold text**` is converted to a VT100-encoded string and available in **VT100EncodedString** property.</span></span>

## <span data-ttu-id="8b9a0-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b9a0-134">PARAMETERS</span></span>

### <span data-ttu-id="8b9a0-135">-AsVT100EncodedString</span><span class="sxs-lookup"><span data-stu-id="8b9a0-135">-AsVT100EncodedString</span></span>

<span data-ttu-id="8b9a0-136">Geeft aan of de uitvoer moet worden gecodeerd als een teken reeks met VT100-escape codes.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-136">Specifies if the output should be encoded as a string with VT100 escape codes.</span></span>

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

### <span data-ttu-id="8b9a0-137">-Input object</span><span class="sxs-lookup"><span data-stu-id="8b9a0-137">-InputObject</span></span>

<span data-ttu-id="8b9a0-138">Geeft het object aan dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-138">Specifies the object to be converted.</span></span> <span data-ttu-id="8b9a0-139">Wanneer een object van het type **System. String** wordt opgegeven, wordt de teken reeks geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-139">When an object of type **System.String** is specified, the string is converted.</span></span> <span data-ttu-id="8b9a0-140">Wanneer een object van het type **System. io. file info** is opgegeven, wordt de inhoud van het bestand dat is opgegeven door het object geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-140">When an object of type **System.IO.FileInfo** is specified, the contents of the file specified by the object are converted.</span></span> <span data-ttu-id="8b9a0-141">Objecten van elk ander type resulteren in een fout.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-141">Objects of any other type result in an error.</span></span>

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

### <span data-ttu-id="8b9a0-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8b9a0-142">-LiteralPath</span></span>

<span data-ttu-id="8b9a0-143">Hiermee geeft u een pad op naar het bestand dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-143">Specifies a path to the file to be converted.</span></span>

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

### <span data-ttu-id="8b9a0-144">-Path</span><span class="sxs-lookup"><span data-stu-id="8b9a0-144">-Path</span></span>

<span data-ttu-id="8b9a0-145">Hiermee geeft u een pad op naar het bestand dat moet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-145">Specifies a path to the file to be converted.</span></span>

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

### <span data-ttu-id="8b9a0-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b9a0-146">CommonParameters</span></span>

<span data-ttu-id="8b9a0-147">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b9a0-148">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8b9a0-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b9a0-149">INVOER</span><span class="sxs-lookup"><span data-stu-id="8b9a0-149">INPUTS</span></span>

### <span data-ttu-id="8b9a0-150">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8b9a0-150">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="8b9a0-151">UITVOER</span><span class="sxs-lookup"><span data-stu-id="8b9a0-151">OUTPUTS</span></span>

### <span data-ttu-id="8b9a0-152">Micro soft. Power shell. MarkdownRender. MarkdownInfo</span><span class="sxs-lookup"><span data-stu-id="8b9a0-152">Microsoft.PowerShell.MarkdownRender.MarkdownInfo</span></span>

## <span data-ttu-id="8b9a0-153">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="8b9a0-153">NOTES</span></span>

## <span data-ttu-id="8b9a0-154">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="8b9a0-154">RELATED LINKS</span></span>

[<span data-ttu-id="8b9a0-155">Parser prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="8b9a0-155">Markdown Parser</span></span>](https://github.com/lunet-io/markdig)

[<span data-ttu-id="8b9a0-156">ANSI escape-code</span><span class="sxs-lookup"><span data-stu-id="8b9a0-156">ANSI escape code</span></span>](https://wikipedia.org/wiki/ANSI_escape_code)

