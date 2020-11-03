---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7.x.0&WT.mc_id=ps-gethelp
ms.date: 01/30/2020
schema: 2.0.0
ms.openlocfilehash: e7e70637afcf53f84c719b489575f5267f9048b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249907"
---
# <span data-ttu-id="48e2d-101">Set-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="48e2d-101">Set-MarkdownOption</span></span>

## <span data-ttu-id="48e2d-102">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="48e2d-102">SYNOPSIS</span></span>
<span data-ttu-id="48e2d-103">Hiermee stelt u de kleuren en stijlen in die worden gebruikt voor het weer geven van de inhoud van de korting</span><span class="sxs-lookup"><span data-stu-id="48e2d-103">Sets the colors and styles used for rendering Markdown content in the console.</span></span>

## <span data-ttu-id="48e2d-104">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="48e2d-104">SYNTAX</span></span>

### <span data-ttu-id="48e2d-105">IndividualSetting (standaard)</span><span class="sxs-lookup"><span data-stu-id="48e2d-105">IndividualSetting (Default)</span></span>

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### <span data-ttu-id="48e2d-106">Thema</span><span class="sxs-lookup"><span data-stu-id="48e2d-106">Theme</span></span>

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### <span data-ttu-id="48e2d-107">Input object</span><span class="sxs-lookup"><span data-stu-id="48e2d-107">InputObject</span></span>

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## <span data-ttu-id="48e2d-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="48e2d-108">DESCRIPTION</span></span>

<span data-ttu-id="48e2d-109">Hiermee stelt u de kleuren en stijlen in die worden gebruikt voor het weer geven van de inhoud van de korting</span><span class="sxs-lookup"><span data-stu-id="48e2d-109">Sets the colors and styles used for rendering Markdown content in the console.</span></span> <span data-ttu-id="48e2d-110">Deze stijlen worden gedefinieerd met behulp van ANSI-escape codes die de kleur en stijl van de gerenderde tekst van de prijs opgave wijzigen.</span><span class="sxs-lookup"><span data-stu-id="48e2d-110">These styles are defined using ANSI escape codes that change the color and style of the Markdown text being rendered.</span></span>

<span data-ttu-id="48e2d-111">Zie de [CommonMark](https://commonmark.org/) -website voor meer informatie over de prijs verlaging.</span><span class="sxs-lookup"><span data-stu-id="48e2d-111">For more information about Markdown, see the [CommonMark](https://commonmark.org/) website.</span></span>

> [!NOTE]
> <span data-ttu-id="48e2d-112">De teken reeks waarden die in de instellingen worden gebruikt, zijn de tekens die volgen op het **Escape** teken ( `[char]0x1B` ) voor de ANSI-escape reeks.</span><span class="sxs-lookup"><span data-stu-id="48e2d-112">The string values used in the settings are the characters that follow the **Escape** character (`[char]0x1B`) for the ANSI escape sequence.</span></span> <span data-ttu-id="48e2d-113">Neem het **Escape** -teken niet op in de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="48e2d-113">Do not include the **Escape** character in the string.</span></span> <span data-ttu-id="48e2d-114">Zie [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)voor meer informatie over ANSI escape-codes.</span><span class="sxs-lookup"><span data-stu-id="48e2d-114">For more information about ANSI escape codes work, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

## <span data-ttu-id="48e2d-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="48e2d-115">EXAMPLES</span></span>

### <span data-ttu-id="48e2d-116">Voor beeld 1: overschakelen naar het licht thema</span><span class="sxs-lookup"><span data-stu-id="48e2d-116">Example 1 - Switch to the Light Theme</span></span>

<span data-ttu-id="48e2d-117">In dit voor beeld wordt het **licht** thema geselecteerd en wordt de nieuwe configuratie weer gegeven met behulp van de para meter **PassThru** .</span><span class="sxs-lookup"><span data-stu-id="48e2d-117">This example selects the **Light** theme and displays the new configuration using the **PassThru** parameter.</span></span>

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### <span data-ttu-id="48e2d-118">Voor beeld 2: de kleur-en stijl instellingen aanpassen</span><span class="sxs-lookup"><span data-stu-id="48e2d-118">Example 2 - Customize the color and style settings</span></span>

<span data-ttu-id="48e2d-119">In dit voor beeld wordt de escape-code voor de kopteksten van de korting gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="48e2d-119">This example changes the escape code for the Markdown headers.</span></span> <span data-ttu-id="48e2d-120">De standaard configuratie voor kopteksten wordt weer gegeven als onderstreepte tekst van verschillende kleuren.</span><span class="sxs-lookup"><span data-stu-id="48e2d-120">The default configuration for headers renders them as underlined text of various colors.</span></span> <span data-ttu-id="48e2d-121">Met deze wijziging wordt de onderstrepings stijl verwijderd.</span><span class="sxs-lookup"><span data-stu-id="48e2d-121">This change removes the underline style.</span></span>

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## <span data-ttu-id="48e2d-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="48e2d-122">PARAMETERS</span></span>

### <span data-ttu-id="48e2d-123">-BoldForegroundColor</span><span class="sxs-lookup"><span data-stu-id="48e2d-123">-BoldForegroundColor</span></span>

<span data-ttu-id="48e2d-124">Hiermee stelt u de voorgrond kleur voor het weer geven van tekst met een zwarte prijs verlaging.</span><span class="sxs-lookup"><span data-stu-id="48e2d-124">Sets the foreground color for rendering bold Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-125">-Code</span><span class="sxs-lookup"><span data-stu-id="48e2d-125">-Code</span></span>

<span data-ttu-id="48e2d-126">Hiermee stelt u de kleur in voor het renderen van code blokken en-reeksen in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-126">Sets the color for rendering code blocks and spans in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-127">-Header1Color</span><span class="sxs-lookup"><span data-stu-id="48e2d-127">-Header1Color</span></span>

<span data-ttu-id="48e2d-128">Hiermee stelt u de kleur voor het renderen van Header1-blokken in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-128">Sets the color for rendering Header1 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-129">-Header2Color</span><span class="sxs-lookup"><span data-stu-id="48e2d-129">-Header2Color</span></span>

<span data-ttu-id="48e2d-130">Hiermee stelt u de kleur voor het renderen van Header2-blokken in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-130">Sets the color for rendering Header2 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-131">-Header3Color</span><span class="sxs-lookup"><span data-stu-id="48e2d-131">-Header3Color</span></span>

<span data-ttu-id="48e2d-132">Hiermee stelt u de kleur voor het renderen van Header3-blokken in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-132">Sets the color for rendering Header3 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-133">-Header4Color</span><span class="sxs-lookup"><span data-stu-id="48e2d-133">-Header4Color</span></span>

<span data-ttu-id="48e2d-134">Hiermee stelt u de kleur voor het renderen van Header4-blokken in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-134">Sets the color for rendering Header4 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-135">-Header5Color</span><span class="sxs-lookup"><span data-stu-id="48e2d-135">-Header5Color</span></span>

<span data-ttu-id="48e2d-136">Hiermee stelt u de kleur voor het renderen van Header5-blokken in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-136">Sets the color for rendering Header5 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-137">-Header6Color</span><span class="sxs-lookup"><span data-stu-id="48e2d-137">-Header6Color</span></span>

<span data-ttu-id="48e2d-138">Hiermee stelt u de kleur voor het renderen van Header6-blokken in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-138">Sets the color for rendering Header6 blocks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-139">-ImageAltTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="48e2d-139">-ImageAltTextForegroundColor</span></span>

<span data-ttu-id="48e2d-140">Hiermee stelt u de voorgrond kleur voor het renderen van de alternatieve tekst van een afbeeldings element in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-140">Sets the foreground color for rendering the alternate text of an image element in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-141">-Input object</span><span class="sxs-lookup"><span data-stu-id="48e2d-141">-InputObject</span></span>

<span data-ttu-id="48e2d-142">Een **PSMarkdownOptionInfo** -object met de configuratie die moet worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="48e2d-142">A **PSMarkdownOptionInfo** object containing the configuration to be set.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-143">-ItalicsForegroundColor</span><span class="sxs-lookup"><span data-stu-id="48e2d-143">-ItalicsForegroundColor</span></span>

<span data-ttu-id="48e2d-144">Hiermee stelt u de voorgrond kleur voor het renderen van de cursief in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-144">Sets the foreground color for rendering the italics in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-145">-LinkForegroundColor</span><span class="sxs-lookup"><span data-stu-id="48e2d-145">-LinkForegroundColor</span></span>

<span data-ttu-id="48e2d-146">Hiermee stelt u de voorgrond kleur voor het weer geven van Hyper links in de tekst voor de korting.</span><span class="sxs-lookup"><span data-stu-id="48e2d-146">Sets the foreground color for rendering hyperlinks in Markdown text.</span></span>

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-147">-PassThru</span><span class="sxs-lookup"><span data-stu-id="48e2d-147">-PassThru</span></span>

<span data-ttu-id="48e2d-148">Zorgt ervoor dat de cmdlet een **PSMarkdownOptionInfo** -object met de nieuwe configuratie uitvoer.</span><span class="sxs-lookup"><span data-stu-id="48e2d-148">Causes the cmdlet to output a **PSMarkdownOptionInfo** object containing the new configuration.</span></span>

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

### <span data-ttu-id="48e2d-149">-Thema</span><span class="sxs-lookup"><span data-stu-id="48e2d-149">-Theme</span></span>

<span data-ttu-id="48e2d-150">Hiermee selecteert u een thema met vooraf gedefinieerde kleur instellingen.</span><span class="sxs-lookup"><span data-stu-id="48e2d-150">Selects a theme containing predefined color settings.</span></span> <span data-ttu-id="48e2d-151">De mogelijke waarden zijn **donker** en **licht**.</span><span class="sxs-lookup"><span data-stu-id="48e2d-151">The possible values are **Dark** and **Light**.</span></span>

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48e2d-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="48e2d-152">CommonParameters</span></span>

<span data-ttu-id="48e2d-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="48e2d-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="48e2d-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="48e2d-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48e2d-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="48e2d-155">INPUTS</span></span>

### <span data-ttu-id="48e2d-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="48e2d-156">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="48e2d-157">UITVOER</span><span class="sxs-lookup"><span data-stu-id="48e2d-157">OUTPUTS</span></span>

### <span data-ttu-id="48e2d-158">Micro soft. Power shell. MarkdownRender. PSMarkdownOptionInfo</span><span class="sxs-lookup"><span data-stu-id="48e2d-158">Microsoft.PowerShell.MarkdownRender.PSMarkdownOptionInfo</span></span>

## <span data-ttu-id="48e2d-159">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="48e2d-159">NOTES</span></span>

<span data-ttu-id="48e2d-160">De teken reeks waarden die worden gebruikt voor het definiëren van de kleur en stijl moeten overeenkomen met de reguliere expressie `^\[*[0-9;]*?m{1}` .</span><span class="sxs-lookup"><span data-stu-id="48e2d-160">The string values used to define the color and style must match the regular expression `^\[*[0-9;]*?m{1}`.</span></span>

## <span data-ttu-id="48e2d-161">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="48e2d-161">RELATED LINKS</span></span>

[<span data-ttu-id="48e2d-162">Get-MarkdownOption</span><span class="sxs-lookup"><span data-stu-id="48e2d-162">Get-MarkdownOption</span></span>](Get-MarkdownOption.md)

[<span data-ttu-id="48e2d-163">ConvertFrom-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="48e2d-163">ConvertFrom-Markdown</span></span>](ConvertFrom-Markdown.md)

[<span data-ttu-id="48e2d-164">Weer geven-prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="48e2d-164">Show-Markdown</span></span>](Show-Markdown.md)

[<span data-ttu-id="48e2d-165">ANSI_escape_code</span><span class="sxs-lookup"><span data-stu-id="48e2d-165">ANSI_escape_code</span></span>](https://en.wikipedia.org/wiki/ANSI_escape_code)

[<span data-ttu-id="48e2d-166">CommonMark</span><span class="sxs-lookup"><span data-stu-id="48e2d-166">CommonMark</span></span>](https://commonmark.org/)

