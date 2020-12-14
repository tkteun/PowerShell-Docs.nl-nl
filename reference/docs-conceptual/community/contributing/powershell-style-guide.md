---
title: Stijlgids voor PowerShell-documentatie
description: Dit artikel bevat de regels van de stijl voor het schrijven van Power shell-documentatie.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352675"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="f5eae-103">Stijlgids voor PowerShell-documentatie</span><span class="sxs-lookup"><span data-stu-id="f5eae-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="f5eae-104">Dit artikel bevat richt lijnen die specifiek zijn voor de PowerShell-Docs-inhoud.</span><span class="sxs-lookup"><span data-stu-id="f5eae-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="f5eae-105">Het is gebaseerd op de informatie die wordt beschreven in het [overzicht](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="f5eae-105">It builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="f5eae-106">Productterminologie</span><span class="sxs-lookup"><span data-stu-id="f5eae-106">Product Terminology</span></span>

<span data-ttu-id="f5eae-107">Er zijn verschillende varianten van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5eae-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="f5eae-108">**PowerShell**: Dit is de standaard.</span><span class="sxs-lookup"><span data-stu-id="f5eae-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="f5eae-109">We overwegen Power shell 7 te bekijken en de andere, waar Power shell.</span><span class="sxs-lookup"><span data-stu-id="f5eae-109">We consider PowerShell 7 and beyond to be the one, true PowerShell.</span></span>
- <span data-ttu-id="f5eae-110">**Power shell core** -Power shell gebouwd op .net core.</span><span class="sxs-lookup"><span data-stu-id="f5eae-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="f5eae-111">Het gebruik van de term **core** moet worden beperkt tot gevallen waarin het nodig is om het te onderscheiden van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="f5eae-111">Usage of the term **Core** should be limited to cases where it's necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="f5eae-112">**Windows Power shell** -Power shell is gebouwd op .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5eae-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="f5eae-113">Windows Power shell wordt alleen in Windows geleverd en vereist het volledige Framework.</span><span class="sxs-lookup"><span data-stu-id="f5eae-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="f5eae-114">In het algemeen kunnen verwijzingen naar ' Windows Power shell ' in de documentatie worden gewijzigd in _Power shell_.</span><span class="sxs-lookup"><span data-stu-id="f5eae-114">In general, references to "Windows PowerShell" in documentation can be changed to _PowerShell_.</span></span>
  <span data-ttu-id="f5eae-115">' Windows Power shell ' moet worden gebruikt als _Windows Power shell_-specifiek gedrag wordt besproken.</span><span class="sxs-lookup"><span data-stu-id="f5eae-115">"Windows PowerShell" should be used when _Windows PowerShell_-specific behavior is being discussed.</span></span>

<span data-ttu-id="f5eae-116">Gerelateerde producten</span><span class="sxs-lookup"><span data-stu-id="f5eae-116">Related products</span></span>

- <span data-ttu-id="f5eae-117">**Visual Studio code (VS code)** : dit is de gratis open source editor van micro soft.</span><span class="sxs-lookup"><span data-stu-id="f5eae-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open-source editor.</span></span> <span data-ttu-id="f5eae-118">Bij de eerste vermelding moet de volledige naam worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="f5eae-119">Daarna kunt u **VS code** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f5eae-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="f5eae-120">Gebruik niet ' VSCode '.</span><span class="sxs-lookup"><span data-stu-id="f5eae-120">Don't use "VSCode".</span></span>
- <span data-ttu-id="f5eae-121">**Power shell-extensie voor Visual Studio code** : de uitbrei ding schakelt versus code in voor de voor Keurs-IDE voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="f5eae-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="f5eae-122">Bij de eerste vermelding moet de volledige naam worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="f5eae-123">Daarna kunt u de **Power shell-extensie** gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f5eae-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="f5eae-124">**Azure PowerShell** : dit is de verzameling Power shell-modules die worden gebruikt voor het beheren van Azure-Services.</span><span class="sxs-lookup"><span data-stu-id="f5eae-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="f5eae-125">**Azure stack Power shell** : dit is de verzameling Power shell-modules die worden gebruikt voor het beheren van de hybride Cloud oplossing van micro soft.</span><span class="sxs-lookup"><span data-stu-id="f5eae-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="f5eae-126">Details van prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="f5eae-126">Markdown specifics</span></span>

<span data-ttu-id="f5eae-127">Het micro soft open publishing-systeem (OPS) dat onze documentatie bouwt, maakt gebruik van [markdig][] voor het verwerken van de verkortings documenten.</span><span class="sxs-lookup"><span data-stu-id="f5eae-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="f5eae-128">Markdig parseert de documenten op basis van de regels van de meest recente [CommonMark][] -specificatie.</span><span class="sxs-lookup"><span data-stu-id="f5eae-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="f5eae-129">De nieuwe CommonMark-specificatie is veel strikter dan de constructie van sommige prijs verlagings elementen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="f5eae-130">Let op de details die in dit document worden gegeven.</span><span class="sxs-lookup"><span data-stu-id="f5eae-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="f5eae-131">Witregels, spaties en tabs</span><span class="sxs-lookup"><span data-stu-id="f5eae-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="f5eae-132">Witregels geven ook het einde van een blok aan in Markdown.</span><span class="sxs-lookup"><span data-stu-id="f5eae-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="f5eae-133">Er moet één witregel tussen verschillende typen Markdown-blokken zijn (zoals tussen een alinea en een lijst of koptekst).</span><span class="sxs-lookup"><span data-stu-id="f5eae-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="f5eae-134">Meerdere opeenvolgende lege regels worden weer gegeven als één lege regel in HTML.</span><span class="sxs-lookup"><span data-stu-id="f5eae-134">Multiple consecutive blank lines render as a single blank line in HTML.</span></span> <span data-ttu-id="f5eae-135">Ze dienen geen doel te zijn.</span><span class="sxs-lookup"><span data-stu-id="f5eae-135">They serve no purpose.</span></span>
<span data-ttu-id="f5eae-136">Binnen een code blok verbreekt opeenvolgende lege regels het code blok.</span><span class="sxs-lookup"><span data-stu-id="f5eae-136">Within a code block, consecutive blank lines break the code block.</span></span>

<span data-ttu-id="f5eae-137">Verwijder extra spaties aan het einde van regels.</span><span class="sxs-lookup"><span data-stu-id="f5eae-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="f5eae-138">Spatiegebruik is erg belangrijk in Markdown.</span><span class="sxs-lookup"><span data-stu-id="f5eae-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="f5eae-139">Gebruik altijd spaties in plaats van harde tabs.</span><span class="sxs-lookup"><span data-stu-id="f5eae-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="f5eae-140">Volg spaties kunnen veranderen hoe de weer gave van de prijs wordt gerenderd.</span><span class="sxs-lookup"><span data-stu-id="f5eae-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="f5eae-141">Titels en koppen</span><span class="sxs-lookup"><span data-stu-id="f5eae-141">Titles and headings</span></span>

<span data-ttu-id="f5eae-142">Gebruik alleen [ATX-kopteksten][atx] (kopteksten in #-stijl in plaats van `=`- of `-`-stijl).</span><span class="sxs-lookup"><span data-stu-id="f5eae-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="f5eae-143">Gebruik alleen zinnen - alleen eigennamen en de eerste letter van een titel of koptekst moet een hoofdletter krijgen</span><span class="sxs-lookup"><span data-stu-id="f5eae-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="f5eae-144">Er moet één spatie zijn tussen de `#` en de eerste letter van de koptekst</span><span class="sxs-lookup"><span data-stu-id="f5eae-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="f5eae-145">Kopteksten moeten worden omgeven door één lege regel</span><span class="sxs-lookup"><span data-stu-id="f5eae-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="f5eae-146">Slechts één H1 per document</span><span class="sxs-lookup"><span data-stu-id="f5eae-146">Only one H1 per document</span></span>
- <span data-ttu-id="f5eae-147">Koptekst niveaus moeten met één worden verhoogd.</span><span class="sxs-lookup"><span data-stu-id="f5eae-147">Header levels should increment by one.</span></span> <span data-ttu-id="f5eae-148">Geen niveaus overs Laan</span><span class="sxs-lookup"><span data-stu-id="f5eae-148">Don't skip levels</span></span>
- <span data-ttu-id="f5eae-149">Geen vette of andere opmaak gebruiken in kopteksten</span><span class="sxs-lookup"><span data-stu-id="f5eae-149">Don't use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="f5eae-150">Beperk de lengte van regels tot 100 tekens</span><span class="sxs-lookup"><span data-stu-id="f5eae-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="f5eae-151">Dit geldt voor conceptuele artikelen en cmdlet-verwijzingen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="f5eae-152">Als u de lijn lengte beperkt, wordt de Lees baarheid van Git-verschillen en-geschiedenis verbeterd.</span><span class="sxs-lookup"><span data-stu-id="f5eae-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="f5eae-153">Het maakt het ook gemakkelijker voor andere schrijvers om bijdragen te maken.</span><span class="sxs-lookup"><span data-stu-id="f5eae-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="f5eae-154">Gebruik de [uitprijs][reflow] uitbreiding opnieuw plaatsen in Visual Studio code om alinea's eenvoudig opnieuw te plaatsen zodat deze overeenkomen met de voorgeschreven regel lengte.</span><span class="sxs-lookup"><span data-stu-id="f5eae-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="f5eae-155">About_topics is beperkt tot 80 tekens.</span><span class="sxs-lookup"><span data-stu-id="f5eae-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="f5eae-156">Zie [About_ bestanden Format teren](#formatting-about_-files)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f5eae-156">For more specific information, see [Formatting About_ files](#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="f5eae-157">Lijsten</span><span class="sxs-lookup"><span data-stu-id="f5eae-157">Lists</span></span>

<span data-ttu-id="f5eae-158">Als uw lijst meerdere zinnen of alinea's bevat, kunt u overwegen om een koptekst op subniveau te gebruiken in plaats van een lijst.</span><span class="sxs-lookup"><span data-stu-id="f5eae-158">If your list contains multiple sentences or paragraphs, consider using a sublevel header rather than a list.</span></span>

<span data-ttu-id="f5eae-159">Lijsten moeten worden omgeven door één lege regel.</span><span class="sxs-lookup"><span data-stu-id="f5eae-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="f5eae-160">Niet-geordende lijsten</span><span class="sxs-lookup"><span data-stu-id="f5eae-160">Unordered lists</span></span>

<span data-ttu-id="f5eae-161">Beëindig geen lijst items met een punt, tenzij deze meerdere zinnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="f5eae-161">Don't end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="f5eae-162">Gebruik het afbreekstreepje (`-`) als opsommingsteken voor een lijstitem.</span><span class="sxs-lookup"><span data-stu-id="f5eae-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="f5eae-163">Dit voorkomt verwarring met vette of cursieve markeringen, waarbij het sterretje [`*`] wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="f5eae-164">Voeg een regel toe en lijn de inspringing uit met het eerste teken achter het opsommingsteken om een alinea of andere elementen onder een opsomming op te nemen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="f5eae-165">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-165">For example:</span></span>

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="f5eae-166">Dit is een lijst met onderliggende elementen onder een item met opsommings tekens.</span><span class="sxs-lookup"><span data-stu-id="f5eae-166">This is a list that contains child elements under a bullet item.</span></span>

- <span data-ttu-id="f5eae-167">Item van eerste opsomming</span><span class="sxs-lookup"><span data-stu-id="f5eae-167">First bullet item</span></span>

  <span data-ttu-id="f5eae-168">Zin met uitleg voor de eerste opsomming.</span><span class="sxs-lookup"><span data-stu-id="f5eae-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="f5eae-169">Onderliggend item voor opsommings teken</span><span class="sxs-lookup"><span data-stu-id="f5eae-169">Child bullet item</span></span>

    <span data-ttu-id="f5eae-170">Zin waarin het onderliggende opsommings teken wordt uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="f5eae-170">Sentence explaining the child bullet.</span></span>

- <span data-ttu-id="f5eae-171">Item van tweede opsomming</span><span class="sxs-lookup"><span data-stu-id="f5eae-171">Second bullet item</span></span>
- <span data-ttu-id="f5eae-172">Item van derde opsomming</span><span class="sxs-lookup"><span data-stu-id="f5eae-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="f5eae-173">Geordende lijsten</span><span class="sxs-lookup"><span data-stu-id="f5eae-173">Ordered lists</span></span>

<span data-ttu-id="f5eae-174">Lijn de inspringing uit met het eerste teken achter het itemnummer om een alinea of andere elementen onder een genummerd item op te nemen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="f5eae-175">Alle items in een genummerde lijst moeten het nummer gebruiken in `1.` plaats van elk item te verhogen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="f5eae-176">Bij het weergeven van de Markdown wordt de waarde automatisch verhoogd.</span><span class="sxs-lookup"><span data-stu-id="f5eae-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="f5eae-177">Hierdoor kunnen items gemakkelijker in een andere volgorde worden geplaatst en wordt de inspringing van onderliggende inhoud gestandaardiseerd.</span><span class="sxs-lookup"><span data-stu-id="f5eae-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="f5eae-178">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-178">For example:</span></span>

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

<span data-ttu-id="f5eae-179">De resulterende prijs verlaging wordt als volgt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="f5eae-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="f5eae-180">Plaats bij het eerste element een spatie achter de 1.</span><span class="sxs-lookup"><span data-stu-id="f5eae-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="f5eae-181">Lange zinnen moeten passend worden gemaakt op de volgende regel en worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.</span><span class="sxs-lookup"><span data-stu-id="f5eae-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="f5eae-182">U kunt een tweede element (zoals dit) opnemen door een nieuwe regel na de eerste in te voegen en de inspringing uit te lijnen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="f5eae-183">De inspringing van het tweede element moet worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.</span><span class="sxs-lookup"><span data-stu-id="f5eae-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="f5eae-184">Voor items met één cijfer, zoals dit, springt u in naar kolom 4.</span><span class="sxs-lookup"><span data-stu-id="f5eae-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="f5eae-185">Voor items met dubbele cijfers, zoals nummer 10, springt u in naar kolom 5.</span><span class="sxs-lookup"><span data-stu-id="f5eae-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="f5eae-186">Het volgende genummerde item begint hier.</span><span class="sxs-lookup"><span data-stu-id="f5eae-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="f5eae-187">Installatiekopieën</span><span class="sxs-lookup"><span data-stu-id="f5eae-187">Images</span></span>

<span data-ttu-id="f5eae-188">De syntaxis voor het insluiten van een afbeelding is:</span><span class="sxs-lookup"><span data-stu-id="f5eae-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="f5eae-189">Hierbij is `alt text` een korte beschrijving van de afbeelding en `<folder path>` een relatief pad naar de afbeelding.</span><span class="sxs-lookup"><span data-stu-id="f5eae-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="f5eae-190">Voor schermlezers voor visueel gehandicapten is alternatieve tekst nodig.</span><span class="sxs-lookup"><span data-stu-id="f5eae-190">Alternate text is required for screen readers for the visually impaired.</span></span>

<span data-ttu-id="f5eae-191">Afbeeldingen moeten worden opgeslagen in een `media/<article-name>` map in de map waarin het artikel zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-191">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="f5eae-192">Deel geen afbeeldingen tussen artikelen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-192">Don't share images between articles.</span></span> <span data-ttu-id="f5eae-193">Maak onder de map `media` een map die overeenkomt met de bestandsnaam van uw artikel.</span><span class="sxs-lookup"><span data-stu-id="f5eae-193">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="f5eae-194">Kopieer de afbeeldingen voor dat artikel naar de nieuwe map.</span><span class="sxs-lookup"><span data-stu-id="f5eae-194">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="f5eae-195">Als een afbeelding door meerdere artikelen wordt gebruikt, moet elke afbeeldingsmap een kopie van het afbeeldingsbestand bevatten.</span><span class="sxs-lookup"><span data-stu-id="f5eae-195">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="f5eae-196">Dit voorkomt dat een wijziging voor een afbeelding in het ene artikel gevolgen heeft voor het andere artikelen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-196">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="f5eae-197">De volgende afbeeldings bestands typen worden ondersteund: `*.png` , `*.gif` , `*.jpeg` , `*.jpg` , `*.svg`</span><span class="sxs-lookup"><span data-stu-id="f5eae-197">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="f5eae-198">Markdown-extensies ondersteund door Open Publishing</span><span class="sxs-lookup"><span data-stu-id="f5eae-198">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="f5eae-199">Het [Microsoft docs authoring Pack](/contribute/how-to-write-docs-auth-pack) bevat hulpprogram ma's die ondersteuning bieden voor functies die uniek zijn voor het publicatie systeem.</span><span class="sxs-lookup"><span data-stu-id="f5eae-199">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="f5eae-200">Waarschuwingen zijn een uitkortings extensie voor het maken van Block quotes die op docs.microsoft.com worden weer gegeven met kleuren en pictogrammen die de betekenis van de inhoud markeren.</span><span class="sxs-lookup"><span data-stu-id="f5eae-200">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="f5eae-201">De volgende typen waarschuwingen worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="f5eae-201">The following alert types are supported:</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="f5eae-202">Deze waarschuwingen zien er op docs.microsoft.com als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="f5eae-202">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="f5eae-203">Notitie blok</span><span class="sxs-lookup"><span data-stu-id="f5eae-203">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="f5eae-204">Information the user should notice even if skimming.</span><span class="sxs-lookup"><span data-stu-id="f5eae-204">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="f5eae-205">Info blok</span><span class="sxs-lookup"><span data-stu-id="f5eae-205">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="f5eae-206">Optional information to help a user be more successful.</span><span class="sxs-lookup"><span data-stu-id="f5eae-206">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="f5eae-207">Belang rijk blok</span><span class="sxs-lookup"><span data-stu-id="f5eae-207">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5eae-208">Essential information required for user success.</span><span class="sxs-lookup"><span data-stu-id="f5eae-208">Essential information required for user success.</span></span>

<span data-ttu-id="f5eae-209">Waarschuwings blok</span><span class="sxs-lookup"><span data-stu-id="f5eae-209">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="f5eae-210">Negative potential consequences of an action.</span><span class="sxs-lookup"><span data-stu-id="f5eae-210">Negative potential consequences of an action.</span></span>

<span data-ttu-id="f5eae-211">Waarschuwings blok</span><span class="sxs-lookup"><span data-stu-id="f5eae-211">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="f5eae-212">Bepaalde gevaarlijke gevolgen van een actie.</span><span class="sxs-lookup"><span data-stu-id="f5eae-212">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="f5eae-213">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="f5eae-213">Hyperlinks</span></span>

- <span data-ttu-id="f5eae-214">Hyper links moeten gebruikmaken van de syntaxis voor afkortingen `[friendlyname](url-or-path)` .</span><span class="sxs-lookup"><span data-stu-id="f5eae-214">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`.</span></span> <span data-ttu-id="f5eae-215">[Koppelings verwijzingen][linkref] worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f5eae-215">[Link references][linkref] are supported.</span></span>
- <span data-ttu-id="f5eae-216">Het publicatie systeem ondersteunt drie typen koppelingen:</span><span class="sxs-lookup"><span data-stu-id="f5eae-216">The publishing system supports three types of links:</span></span>
  - <span data-ttu-id="f5eae-217">URL-koppelingen</span><span class="sxs-lookup"><span data-stu-id="f5eae-217">URL links</span></span>
  - <span data-ttu-id="f5eae-218">Bestands koppelingen</span><span class="sxs-lookup"><span data-stu-id="f5eae-218">File links</span></span>
  - <span data-ttu-id="f5eae-219">Kruis verwijzings koppelingen</span><span class="sxs-lookup"><span data-stu-id="f5eae-219">Cross-reference links</span></span>
- <span data-ttu-id="f5eae-220">Koppelingen naar andere artikelen op docs.microsoft.com moeten site-relatieve paden zijn</span><span class="sxs-lookup"><span data-stu-id="f5eae-220">Links to other articles on docs.microsoft.com must be site-relative paths</span></span>
- <span data-ttu-id="f5eae-221">Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site.</span><span class="sxs-lookup"><span data-stu-id="f5eae-221">All URLs to external websites should use HTTPS unless that isn't valid for the target site.</span></span>
- <span data-ttu-id="f5eae-222">Koppelingen moeten een beschrijvende naam hebben, meestal de titel van het gekoppelde artikel</span><span class="sxs-lookup"><span data-stu-id="f5eae-222">Links must have a friendly name, usually the title of the linked article</span></span>
- <span data-ttu-id="f5eae-223">Voor alle items in de sectie _Verwante koppelingen_ onderaan moet een Hyper link worden</span><span class="sxs-lookup"><span data-stu-id="f5eae-223">All items in the _Related links_ section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="f5eae-224">Gebruik geen accents graves, vet of andere opmaak binnen de haakjes van een Hyper link.</span><span class="sxs-lookup"><span data-stu-id="f5eae-224">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="f5eae-225">Bare Url's kunnen worden gebruikt wanneer u een specifieke URI documenteert.</span><span class="sxs-lookup"><span data-stu-id="f5eae-225">Bare URLs may be used when you're documenting a specific URI.</span></span> <span data-ttu-id="f5eae-226">De URI moet worden inge sloten in accents graves.</span><span class="sxs-lookup"><span data-stu-id="f5eae-226">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="f5eae-227">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-227">For example:</span></span>

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a><span data-ttu-id="f5eae-228">Koppeling naar andere inhoud op docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="f5eae-228">Linking to other content on docs.microsoft.com</span></span>

- <span data-ttu-id="f5eae-229">**URL-koppelingen** naar andere artikelen op docs.Microsoft.com moeten site-relatieve paden zijn.</span><span class="sxs-lookup"><span data-stu-id="f5eae-229">**URL links** to other articles on docs.microsoft.com must be site-relative paths.</span></span> <span data-ttu-id="f5eae-230">De eenvoudigste manier om een relatieve koppeling te maken, is door de URL te kopiëren uit uw browser en vervolgens te verwijderen `https://docs.microsoft.com/en-us` van de waarde die u in de prijs opsplitsen hebt geplakt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-230">The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span> <span data-ttu-id="f5eae-231">Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (verwijderen `/en-us` van URL).</span><span class="sxs-lookup"><span data-stu-id="f5eae-231">Don't include locales in URLs on Microsoft properties (remove `/en-us` from URL).</span></span> <span data-ttu-id="f5eae-232">Verwijder overbodige query parameters uit de URL.</span><span class="sxs-lookup"><span data-stu-id="f5eae-232">Remove any unnecessary query parameters from the URL.</span></span> <span data-ttu-id="f5eae-233">Voor beelden die moeten worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="f5eae-233">Examples that should be removed:</span></span>

  - <span data-ttu-id="f5eae-234">`?view=powershell-5.1` -wordt gebruikt om een koppeling te maken naar een specifieke versie van Power shell</span><span class="sxs-lookup"><span data-stu-id="f5eae-234">`?view=powershell-5.1` - used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="f5eae-235">`?redirectedfrom=MSDN` -wordt toegevoegd aan de URL wanneer u wordt omgeleid van een oud artikel naar de nieuwe locatie</span><span class="sxs-lookup"><span data-stu-id="f5eae-235">`?redirectedfrom=MSDN` - added to the URL when you get redirected from an old article to its new location</span></span>

  <span data-ttu-id="f5eae-236">Als u een koppeling naar een specifieke versie van een document wilt maken, moet u de `&preserve_view=true` para meter toevoegen aan de query reeks.</span><span class="sxs-lookup"><span data-stu-id="f5eae-236">If you need to link to a specific version of a document, then you need to add the `&preserve_view=true` parameter to the query string.</span></span> <span data-ttu-id="f5eae-237">Bijvoorbeeld: `?view=powershell-5.1&preserve_view=true`</span><span class="sxs-lookup"><span data-stu-id="f5eae-237">For example: `?view=powershell-5.1&preserve_view=true`</span></span>

- <span data-ttu-id="f5eae-238">Een **koppeling** naar een bestand wordt gebruikt om te koppelen van het ene referentie artikel naar het andere of van het ene conceptuele artikel naar het andere.</span><span class="sxs-lookup"><span data-stu-id="f5eae-238">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="f5eae-239">Als u een verwijzing naar een referentie artikel moet koppelen voor een specifieke versie van Power shell, moet u een URL-koppeling gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f5eae-239">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

  - <span data-ttu-id="f5eae-240">Bestands koppelingen bevatten een relatief bestandspad (bijvoorbeeld: `../folder/file.md` )</span><span class="sxs-lookup"><span data-stu-id="f5eae-240">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
  - <span data-ttu-id="f5eae-241">Alle bestands paden gebruiken tekens voor voorwaartse slash ( `/` )</span><span class="sxs-lookup"><span data-stu-id="f5eae-241">All file paths use forward-slash (`/`) characters</span></span>

- <span data-ttu-id="f5eae-242">**Kruis verwijzings koppelingen** zijn een speciale functie die door het publicatie systeem wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f5eae-242">**Cross-reference links** are a special feature supported by the publishing system.</span></span> <span data-ttu-id="f5eae-243">U kunt Kruis verwijzings koppelingen in conceptuele artikelen gebruiken om een koppeling te maken naar .NET API of cmdlet Reference.</span><span class="sxs-lookup"><span data-stu-id="f5eae-243">You can use cross-reference links in conceptual articles to link to .NET API or cmdlet reference.</span></span>

  <span data-ttu-id="f5eae-244">Zie [koppelingen gebruiken in documentatie](/contribute/how-to-write-links#xref-cross-reference-links) in de hand leiding voor centraal-inzenders voor koppelingen naar .net API-verwijzingen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-244">For links to .NET API reference, see [Use links in documentation](/contribute/how-to-write-links#xref-cross-reference-links) in the central Contributor Guide.</span></span>

  <span data-ttu-id="f5eae-245">Koppelingen naar cmdlet-verwijzingen hebben de volgende indeling: `xref:<module-name>.<cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="f5eae-245">Links to cmdlet reference have the following format: `xref:<module-name>.<cmdlet-name>`.</span></span> <span data-ttu-id="f5eae-246">Als u bijvoorbeeld een koppeling wilt maken naar de `Get-Content` cmdlet in de module **micro soft. Power shell. Management** .</span><span class="sxs-lookup"><span data-stu-id="f5eae-246">For example, to link to the `Get-Content` cmdlet in the **Microsoft.PowerShell.Management** module.</span></span>

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

<span data-ttu-id="f5eae-247">Uitgebreide koppeling is toegestaan voor URL-en bestands koppelingen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-247">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="f5eae-248">Voeg het anker toe aan het einde van het doelpad.</span><span class="sxs-lookup"><span data-stu-id="f5eae-248">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="f5eae-249">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-249">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="f5eae-250">Zie [koppelingen in documentatie gebruiken](/contribute/how-to-write-links)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f5eae-250">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="f5eae-251">Syntaxiselementen van opdrachten opmaken</span><span class="sxs-lookup"><span data-stu-id="f5eae-251">Formatting command syntax elements</span></span>

- <span data-ttu-id="f5eae-252">Gebruik altijd de volledige naam voor cmdlets en para meters.</span><span class="sxs-lookup"><span data-stu-id="f5eae-252">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="f5eae-253">Vermijd het gebruik van aliassen tenzij u zeker weet dat de alias.</span><span class="sxs-lookup"><span data-stu-id="f5eae-253">Avoid using aliases unless you're specifically demonstrating the alias.</span></span>

- <span data-ttu-id="f5eae-254">Eigenschap, para meter, object, type namen, klassen namen en klassen methoden moeten **vet** zijn.</span><span class="sxs-lookup"><span data-stu-id="f5eae-254">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="f5eae-255">Eigenschaps-en parameter waarden moeten worden verpakt in accents graves ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="f5eae-255">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="f5eae-256">Wanneer u verwijst naar typen met behulp van de stijl met tussen haakjes, gebruikt u accents graves.</span><span class="sxs-lookup"><span data-stu-id="f5eae-256">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="f5eae-257">Bijvoorbeeld: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="f5eae-257">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="f5eae-258">Taal trefwoorden, namen van cmdlets, functies, variabelen, systeem eigen exe, bestands paden en in-line syntaxis voorbeelden moeten worden verpakt in apostroffen- `` ` `` tekens ().</span><span class="sxs-lookup"><span data-stu-id="f5eae-258">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="f5eae-259">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-259">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="f5eae-260">Wanneer naar een parameter wordt verwezen aan de hand van de naam, moet de naam **vet** zijn.</span><span class="sxs-lookup"><span data-stu-id="f5eae-260">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="f5eae-261">Wanneer het gebruik van een parameter met een afbreekstreepje als voorvoegsel wordt gedemonstreerd, moet de parameter tussen accents graves worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="f5eae-261">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="f5eae-262">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-262">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="f5eae-263">Wanneer een voorbeeld van het gebruik van een externe opdracht wordt gebruikt, moet het voorbeeld tussen accents graves zijn geplaatst.</span><span class="sxs-lookup"><span data-stu-id="f5eae-263">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="f5eae-264">Neem altijd de bestands extensie op in de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="f5eae-264">Always include the file extension in the native command.</span></span> <span data-ttu-id="f5eae-265">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-265">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="f5eae-266">Met inbegrip van de bestands extensie zorgt ervoor dat de juiste opdracht wordt uitgevoerd volgens de opdracht prioriteit van Power shell.</span><span class="sxs-lookup"><span data-stu-id="f5eae-266">Including the file extension ensures that the correct command is executed according to PowerShell's command precedence.</span></span>

- <span data-ttu-id="f5eae-267">Als u een conceptueel artikel (in tegenstelling tot referentie-inhoud) schrijft, moet de eerste instantie van een cmdlet-naam een hyperlink naar de cmdlet-documentatie bevatten.</span><span class="sxs-lookup"><span data-stu-id="f5eae-267">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="f5eae-268">Gebruik geen accents graves, vet of andere opmaak binnen de haakjes van een Hyper link.</span><span class="sxs-lookup"><span data-stu-id="f5eae-268">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="f5eae-269">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-269">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="f5eae-270">Zie de sectie [hyper links](#hyperlinks) in dit artikel voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f5eae-270">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="f5eae-271">Prijs verlaging voor code voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-271">Markdown for code samples</span></span>

<span data-ttu-id="f5eae-272">Markdown ondersteunt twee verschillende codestijlen:</span><span class="sxs-lookup"><span data-stu-id="f5eae-272">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="f5eae-273">**Code reeksen (inline)** : gemarkeerd met één apostroffen ( `` ` `` )-teken.</span><span class="sxs-lookup"><span data-stu-id="f5eae-273">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="f5eae-274">Wordt gebruikt in een alinea in plaats van als een zelfstandig blok.</span><span class="sxs-lookup"><span data-stu-id="f5eae-274">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="f5eae-275">**Code blokken** : een blok met meerdere regels dat is omgeven door Triple-apostroffen ( `` ``` `` ) teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-275">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="f5eae-276">Code blokken kunnen ook een taal label volgen volgens het accents graves.</span><span class="sxs-lookup"><span data-stu-id="f5eae-276">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="f5eae-277">Het taal label schakelt syntaxis markering in voor de inhoud van het code blok.</span><span class="sxs-lookup"><span data-stu-id="f5eae-277">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="f5eae-278">Alle codeblokken moeten zich binnen een afscheiding bevinden.</span><span class="sxs-lookup"><span data-stu-id="f5eae-278">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="f5eae-279">Gebruik nooit inspringing voor code blokken.</span><span class="sxs-lookup"><span data-stu-id="f5eae-279">Never use indentation for code blocks.</span></span> <span data-ttu-id="f5eae-280">Met prijs verlaging wordt dit patroon toegestaan, maar dit kan een probleem zijn en moet worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="f5eae-280">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="f5eae-281">Een code blok bestaat uit een of meer regels code omgeven door een code Fence van Triple-apostroffen ( `` ``` `` ).</span><span class="sxs-lookup"><span data-stu-id="f5eae-281">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="f5eae-282">De markeringen voor de codeafscheiding moeten zich op een eigen regel voor en na het codevoorbeeld bevinden.</span><span class="sxs-lookup"><span data-stu-id="f5eae-282">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="f5eae-283">De markering na het begin van het codeblok heeft mogelijk een optioneel taallabel.</span><span class="sxs-lookup"><span data-stu-id="f5eae-283">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="f5eae-284">In het Open Publishing System (OPS) van Microsoft wordt het taallabel gebruikt om de functie voor markering van de syntaxis te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-284">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="f5eae-285">Zie [Geomheiningde code blokken](/contribute/code-in-docs#fenced-code-blocks) in de hand leiding gecentraliseerde Inzender voor een volledige lijst met ondersteunde taal codes.</span><span class="sxs-lookup"><span data-stu-id="f5eae-285">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="f5eae-286">OPS voegt tevens een knop **Kopiëren** toe waarmee u de inhoud van het codeblok naar het klembord kopieert.</span><span class="sxs-lookup"><span data-stu-id="f5eae-286">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="f5eae-287">Zo kunt u de code snel in een script plakken om het code voorbeeld te testen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-287">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="f5eae-288">Niet alle voor beelden in onze documentatie zijn echter bedoeld om te worden uitgevoerd als.</span><span class="sxs-lookup"><span data-stu-id="f5eae-288">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="f5eae-289">Sommige code blokken zijn eenvoudige illustraties van een Power shell-concept.</span><span class="sxs-lookup"><span data-stu-id="f5eae-289">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="f5eae-290">Er zijn drie typen code blokken die in onze documentatie worden gebruikt:</span><span class="sxs-lookup"><span data-stu-id="f5eae-290">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="f5eae-291">Syntaxis blokken</span><span class="sxs-lookup"><span data-stu-id="f5eae-291">Syntax blocks</span></span>
1. <span data-ttu-id="f5eae-292">Illustratieve voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-292">Illustrative examples</span></span>
1. <span data-ttu-id="f5eae-293">Uitvoerbare voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-293">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="f5eae-294">Syntaxis code blokken</span><span class="sxs-lookup"><span data-stu-id="f5eae-294">Syntax code blocks</span></span>

<span data-ttu-id="f5eae-295">Syntaxis code blokken worden gebruikt voor het beschrijven van de syntaxis structuur van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="f5eae-295">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="f5eae-296">Gebruik geen taal code op de code Fence.</span><span class="sxs-lookup"><span data-stu-id="f5eae-296">Don't use a language tag on the code fence.</span></span> <span data-ttu-id="f5eae-297">Dit voorbeeld toont alle mogelijke parameters van de `Get-Command`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f5eae-297">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="f5eae-298">Dit voorbeeld bevat een beschrijving van de `for`-instructie in algemene termen:</span><span class="sxs-lookup"><span data-stu-id="f5eae-298">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="f5eae-299">Illustratieve voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-299">Illustrative examples</span></span>

<span data-ttu-id="f5eae-300">Illustratieve voorbeelden worden gebruikt om een PowerShell-concept uit te leggen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-300">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="f5eae-301">Ze zijn niet bedoeld om te worden gekopieerd naar het klem bord voor uitvoering.</span><span class="sxs-lookup"><span data-stu-id="f5eae-301">They aren't meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="f5eae-302">Deze worden meestal gebruikt voor eenvoudige voor beelden die eenvoudig te typen zijn en eenvoudig te begrijpen zijn.</span><span class="sxs-lookup"><span data-stu-id="f5eae-302">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="f5eae-303">Het code blok kan de Power shell-prompt en voorbeeld uitvoer bevatten.</span><span class="sxs-lookup"><span data-stu-id="f5eae-303">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="f5eae-304">Hier volgt een eenvoudig voor beeld van de Power shell-vergelijkings operatoren.</span><span class="sxs-lookup"><span data-stu-id="f5eae-304">Here's a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="f5eae-305">In dit geval is het niet de bedoeling dat de lezer dit voorbeeld kopieert en uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f5eae-305">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="f5eae-306">Uitvoerbare voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-306">Executable examples</span></span>

<span data-ttu-id="f5eae-307">Complexe voor beelden of voor beelden die bedoeld zijn om te worden gekopieerd en uitgevoerd, moeten de volgende opmaak voor blok stijl gebruiken:</span><span class="sxs-lookup"><span data-stu-id="f5eae-307">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="f5eae-308">De uitvoer die door PowerShell-opdrachten wordt weergegeven, moet zich in een **Uitvoer**-codeblok bevinden om markering van de syntaxis te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-308">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="f5eae-309">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-309">For example:</span></span>

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

<span data-ttu-id="f5eae-310">Het code label van de **uitvoer** is geen officiële taal die wordt ondersteund door het markerings systeem van de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="f5eae-310">The **Output** code label isn't an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="f5eae-311">Dit label is echter nuttig omdat OPS het label "uitvoer" toevoegt aan het frame van de code op de webpagina.</span><span class="sxs-lookup"><span data-stu-id="f5eae-311">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="f5eae-312">Het vak uitvoer code heeft geen syntaxis markering.</span><span class="sxs-lookup"><span data-stu-id="f5eae-312">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="f5eae-313">Stijlregels voor code</span><span class="sxs-lookup"><span data-stu-id="f5eae-313">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="f5eae-314">Voortzetting van regels in codevoorbeelden vermijden</span><span class="sxs-lookup"><span data-stu-id="f5eae-314">Avoid line continuation in code samples</span></span>

<span data-ttu-id="f5eae-315">Vermijd tekens voor voortzetting van de regel (`` ` ``) in PowerShell-codevoorbeelden.</span><span class="sxs-lookup"><span data-stu-id="f5eae-315">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="f5eae-316">Deze zijn moeilijk te zien en kunnen problemen veroorzaken als er extra spaties aan het einde van de regel staan.</span><span class="sxs-lookup"><span data-stu-id="f5eae-316">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="f5eae-317">Gebruik Power shell splatting om de regel lengte voor cmdlets met verschillende para meters te reduceren.</span><span class="sxs-lookup"><span data-stu-id="f5eae-317">Use PowerShell splatting to reduce line length for cmdlets that have several parameters.</span></span>
- <span data-ttu-id="f5eae-318">Profiteer van de natuurlijke lijn grens mogelijkheden van Power shell, zoals na sluis `|` tekens (), accolades openen ( `{` ), haakjes ( `(` ) en haakjes ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="f5eae-318">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces (`{`), parentheses (`(`), and brackets (`[`).</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="f5eae-319">PowerShell-prompts vermijden in voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-319">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="f5eae-320">Het gebruik van de prompt teken reeks wordt afgeraden en moet worden beperkt tot scenario's die bedoeld zijn voor het illustreren van het gebruik van de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="f5eae-320">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command-line usage.</span></span> <span data-ttu-id="f5eae-321">Voor de meeste van deze voor beelden moet de prompt teken reeks zijn `PS>` .</span><span class="sxs-lookup"><span data-stu-id="f5eae-321">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="f5eae-322">Deze prompt is onafhankelijk van indicatoren voor specifieke besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-322">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="f5eae-323">Prompts zijn in voor beelden vereist voor het illustreren van opdrachten die de prompt wijzigen of wanneer het weer gegeven pad belang rijk is voor het scenario.</span><span class="sxs-lookup"><span data-stu-id="f5eae-323">Prompts are required in examples to illustrate commands that alter the prompt or when the path displayed is significant to the scenario.</span></span> <span data-ttu-id="f5eae-324">In het volgende voorbeeld wordt getoond hoe de prompt verandert als de registerprovider wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-324">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="dont-use-aliases-in-examples"></a><span data-ttu-id="f5eae-325">Geen aliassen gebruiken in voor beelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-325">Don't use aliases in examples</span></span>

<span data-ttu-id="f5eae-326">Gebruik de volledige naam van alle-cmdlets en-para meters, tenzij u de alias expliciet wilt documenteren.</span><span class="sxs-lookup"><span data-stu-id="f5eae-326">Use the full name of all cmdlets and parameters unless you're specifically documenting the alias.</span></span>
<span data-ttu-id="f5eae-327">De namen van cmdlets en para meters moeten gebruikmaken van de juiste namen van [Pascal-cases][] .</span><span class="sxs-lookup"><span data-stu-id="f5eae-327">Cmdlet and parameter names must use the proper [Pascal-cased][] names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="f5eae-328">Parameters gebruiken in voorbeelden</span><span class="sxs-lookup"><span data-stu-id="f5eae-328">Using parameters in examples</span></span>

<span data-ttu-id="f5eae-329">Vermijd het gebruik van positionele parameters.</span><span class="sxs-lookup"><span data-stu-id="f5eae-329">Avoid using positional parameters.</span></span> <span data-ttu-id="f5eae-330">Over het algemeen moet u altijd de parameter naam in een voor beeld meenemen, zelfs als de para meter positioneel is.</span><span class="sxs-lookup"><span data-stu-id="f5eae-330">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="f5eae-331">Dit verkleint de kans op verwarring in uw voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="f5eae-331">This reduces the chance of confusion in your examples.</span></span>

## <a name="formatting-cmdlet-reference-articles"></a><span data-ttu-id="f5eae-332">Naslag informatie over het format teren van cmdlets</span><span class="sxs-lookup"><span data-stu-id="f5eae-332">Formatting cmdlet reference articles</span></span>

<span data-ttu-id="f5eae-333">Artikelen met naslaginformatie voor cmdlets hebben een specifieke structuur.</span><span class="sxs-lookup"><span data-stu-id="f5eae-333">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="f5eae-334">Deze structuur wordt gedefinieerd door [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="f5eae-334">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="f5eae-335">PlatyPS genereert de cmdlet-Help voor Power shell-modules in korting.</span><span class="sxs-lookup"><span data-stu-id="f5eae-335">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="f5eae-336">Nadat de Markdown-bestanden zijn bewerkt, wordt PlatyPS gebruikt om de MAML-helpbestanden te maken die door de `Get-Help`-cmdlet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-336">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="f5eae-337">In PlatyPS is een in code vastgelegd schema voor cmdlet-naslaginformatie. Dit schema is in de code geschreven.</span><span class="sxs-lookup"><span data-stu-id="f5eae-337">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="f5eae-338">In het document [platyPS. schema.md][] is deze structuur beschreven.</span><span class="sxs-lookup"><span data-stu-id="f5eae-338">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="f5eae-339">Schendingen van het schema veroorzaken compilatiefouten die moeten worden opgelost voordat we uw bijdrage kunnen accepteren.</span><span class="sxs-lookup"><span data-stu-id="f5eae-339">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

- <span data-ttu-id="f5eae-340">Verwijder geen van de ATX-header structuren.</span><span class="sxs-lookup"><span data-stu-id="f5eae-340">Don't remove any of the ATX header structures.</span></span> <span data-ttu-id="f5eae-341">PlatyPS verwacht een specifieke reeks kopteksten.</span><span class="sxs-lookup"><span data-stu-id="f5eae-341">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="f5eae-342">De kopteksten **Inputtype** en **Outputtype** moeten een type hebben.</span><span class="sxs-lookup"><span data-stu-id="f5eae-342">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="f5eae-343">Als de cmdlet geen invoer heeft of een waarde retourneert, gebruikt u de waarde `None` .</span><span class="sxs-lookup"><span data-stu-id="f5eae-343">If the cmdlet doesn't take input or return a value, then use the value `None`.</span></span>
- <span data-ttu-id="f5eae-344">In elke alinea kunnen inline codereeksen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-344">Inline code spans can be used in any paragraph.</span></span>
- <span data-ttu-id="f5eae-345">Geomheiningde code blokken zijn alleen toegestaan in de sectie **voor beelden** .</span><span class="sxs-lookup"><span data-stu-id="f5eae-345">Fenced code blocks are only allowed in the **EXAMPLES** section.</span></span>

<span data-ttu-id="f5eae-346">In het PlatyPS-schema is **voor beelden** een kop van H2.</span><span class="sxs-lookup"><span data-stu-id="f5eae-346">In the PlatyPS schema, **EXAMPLES** is an H2 header.</span></span> <span data-ttu-id="f5eae-347">Elk voor beeld is een H3-header.</span><span class="sxs-lookup"><span data-stu-id="f5eae-347">Each example is an H3 header.</span></span> <span data-ttu-id="f5eae-348">Binnen een voor beeld staat het schema niet toe dat code blokken worden gescheiden door alinea's.</span><span class="sxs-lookup"><span data-stu-id="f5eae-348">Within an example, the schema doesn't allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="f5eae-349">In het schema is de volgende structuur toegestaan:</span><span class="sxs-lookup"><span data-stu-id="f5eae-349">The schema allows the following structure:</span></span>

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="f5eae-350">Geef elk voorbeeld een nummer en voeg een korte titel toe.</span><span class="sxs-lookup"><span data-stu-id="f5eae-350">Number each example and add a brief title.</span></span>

<span data-ttu-id="f5eae-351">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-351">For example:</span></span>

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a><span data-ttu-id="f5eae-352">About_-bestanden opmaken</span><span class="sxs-lookup"><span data-stu-id="f5eae-352">Formatting About_ files</span></span>

<span data-ttu-id="f5eae-353">`About_*` bestanden worden in korting geschreven, maar worden als tekst bestanden verzonden.</span><span class="sxs-lookup"><span data-stu-id="f5eae-353">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="f5eae-354">We gebruiken [pandoc][] om de prijs verlaging te converteren naar platte tekst.</span><span class="sxs-lookup"><span data-stu-id="f5eae-354">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="f5eae-355">`About_*` bestanden zijn ingedeeld voor de beste compatibiliteit tussen alle versies van Power shell en met de hulpprogram ma's voor publiceren.</span><span class="sxs-lookup"><span data-stu-id="f5eae-355">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="f5eae-356">Algemene richtlijnen voor het opmaken:</span><span class="sxs-lookup"><span data-stu-id="f5eae-356">Basic formatting guidelines:</span></span>

- <span data-ttu-id="f5eae-357">Normale regels beperken tot 80 tekens</span><span class="sxs-lookup"><span data-stu-id="f5eae-357">Limit normal lines to 80 characters</span></span>
- <span data-ttu-id="f5eae-358">Code blokken zijn beperkt tot 76 tekens</span><span class="sxs-lookup"><span data-stu-id="f5eae-358">Code blocks are limited to 76 characters</span></span>
- <span data-ttu-id="f5eae-359">Block Quotes (en waarschuwingen) zijn beperkt tot 78 tekens</span><span class="sxs-lookup"><span data-stu-id="f5eae-359">Blockquotes (and Alerts) are limited 78 characters</span></span>
- <span data-ttu-id="f5eae-360">Wanneer u deze speciale meta tekens gebruikt `\` , `$` en `<` :</span><span class="sxs-lookup"><span data-stu-id="f5eae-360">When using these special meta-characters `\`,`$`, and `<`:</span></span>
  - <span data-ttu-id="f5eae-361">Binnen een kop moeten deze tekens worden voorafgegaan door een voorloop `\` teken of worden inge sloten in code reeksen met behulp van accents graves ( `` ` `` )</span><span class="sxs-lookup"><span data-stu-id="f5eae-361">Within a header, these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="f5eae-362">In een alinea moeten deze tekens in code reeksen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="f5eae-362">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="f5eae-363">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f5eae-363">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="f5eae-364">Tabellen moeten binnen 76 tekens passen</span><span class="sxs-lookup"><span data-stu-id="f5eae-364">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="f5eae-365">Laat inhoud van cellen die over meerdere regels valt handmatig teruglopen</span><span class="sxs-lookup"><span data-stu-id="f5eae-365">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="f5eae-366">Gebruik op elke regel `|`-tekens voor openen en sluiten</span><span class="sxs-lookup"><span data-stu-id="f5eae-366">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="f5eae-367">In het volgende voor beeld ziet u hoe u een tabel op een juiste manier kunt samen stellen die informatie bevat die op meerdere regels in een cel inloopt.</span><span class="sxs-lookup"><span data-stu-id="f5eae-367">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="f5eae-368">De limiet van 76 kolommen geldt alleen voor `About_*` onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-368">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="f5eae-369">U kunt brede kolommen gebruiken in conceptuele of cmdlet-referentie artikelen.</span><span class="sxs-lookup"><span data-stu-id="f5eae-369">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f5eae-370">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="f5eae-370">Next steps</span></span>

[<span data-ttu-id="f5eae-371">Redactionele controlelijst</span><span class="sxs-lookup"><span data-stu-id="f5eae-371">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[Pascal-cases]: https://en.wikipedia.org/wiki/PascalCase
[Pascal-cased]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
