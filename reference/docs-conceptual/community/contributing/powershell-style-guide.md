---
title: Stijlgids voor PowerShell-documentatie
description: Dit artikel bevat de regels van de stijl voor het schrijven van Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 32df641f7cafa2a5bfcf1bcbf94be594aa77c7d0
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837440"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="85740-103">Stijlgids voor PowerShell-documentatie</span><span class="sxs-lookup"><span data-stu-id="85740-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="85740-104">Dit artikel bevat richt lijnen die specifiek zijn voor de Power shell-docs-inhoud.</span><span class="sxs-lookup"><span data-stu-id="85740-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="85740-105">Dit is gebaseerd op de informatie die wordt beschreven in het [overzicht](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="85740-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="85740-106">Productterminologie</span><span class="sxs-lookup"><span data-stu-id="85740-106">Product Terminology</span></span>

<span data-ttu-id="85740-107">Er zijn verschillende varianten van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85740-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="85740-108">**PowerShell**: Dit is de standaard.</span><span class="sxs-lookup"><span data-stu-id="85740-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="85740-109">We overwegen Power shell 7 en nog eens te zijn. de echte Power shell gaat verder.</span><span class="sxs-lookup"><span data-stu-id="85740-109">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>
- <span data-ttu-id="85740-110">**Power shell core** -Power shell gebouwd op .net core.</span><span class="sxs-lookup"><span data-stu-id="85740-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="85740-111">Het gebruik van de term **core** moet worden beperkt tot gevallen waarin het nodig is om het te onderscheiden van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="85740-111">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="85740-112">**Windows Power shell** -Power shell is gebouwd op .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85740-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="85740-113">Windows Power shell wordt alleen in Windows geleverd en vereist het volledige Framework.</span><span class="sxs-lookup"><span data-stu-id="85740-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="85740-114">Over het algemeen kunnen verwijzingen naar ‘Windows PowerShell’ in documentatie worden vervangen door ‘PowerShell’.</span><span class="sxs-lookup"><span data-stu-id="85740-114">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
  <span data-ttu-id="85740-115">' Windows Power shell ' moet worden gebruikt wanneer ' Windows Power Shell-specifiek gedrag wordt besproken.</span><span class="sxs-lookup"><span data-stu-id="85740-115">"Windows PowerShell" should be used when "Windows PowerShell"-specific behavior is being discussed.</span></span>

<span data-ttu-id="85740-116">Gerelateerde producten</span><span class="sxs-lookup"><span data-stu-id="85740-116">Related products</span></span>

- <span data-ttu-id="85740-117">**Visual Studio code (VS code)** : dit is de gratis open source editor van micro soft.</span><span class="sxs-lookup"><span data-stu-id="85740-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open source editor.</span></span> <span data-ttu-id="85740-118">Bij de eerste vermelding moet de volledige naam worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="85740-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="85740-119">Daarna kunt u **VS code**gebruiken.</span><span class="sxs-lookup"><span data-stu-id="85740-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="85740-120">Gebruik niet ' VSCode '.</span><span class="sxs-lookup"><span data-stu-id="85740-120">Do not use "VSCode".</span></span>
- <span data-ttu-id="85740-121">**Power shell-extensie voor Visual Studio code** : de uitbrei ding schakelt versus code in voor de voor Keurs-IDE voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="85740-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="85740-122">Bij de eerste vermelding moet de volledige naam worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="85740-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="85740-123">Daarna kunt u de **Power shell-extensie**gebruiken.</span><span class="sxs-lookup"><span data-stu-id="85740-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="85740-124">**Azure PowerShell** : dit is de verzameling Power shell-modules die worden gebruikt voor het beheren van Azure-Services.</span><span class="sxs-lookup"><span data-stu-id="85740-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="85740-125">**Azure stack Power shell** : dit is de verzameling Power shell-modules die worden gebruikt voor het beheren van de hybride Cloud oplossing van micro soft.</span><span class="sxs-lookup"><span data-stu-id="85740-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="85740-126">Details van prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="85740-126">Markdown specifics</span></span>

<span data-ttu-id="85740-127">Het micro soft open publishing-systeem (OPS) dat onze documentatie bouwt, maakt gebruik van [markdig][] voor het verwerken van de verkortings documenten.</span><span class="sxs-lookup"><span data-stu-id="85740-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="85740-128">Markdig parseert de documenten op basis van de regels van de meest recente [CommonMark][] -specificatie.</span><span class="sxs-lookup"><span data-stu-id="85740-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="85740-129">De nieuwe CommonMark-specificatie is veel strikter dan de constructie van sommige prijs verlagings elementen.</span><span class="sxs-lookup"><span data-stu-id="85740-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="85740-130">Let op de details die in dit document worden gegeven.</span><span class="sxs-lookup"><span data-stu-id="85740-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="85740-131">Witregels, spaties en tabs</span><span class="sxs-lookup"><span data-stu-id="85740-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="85740-132">Witregels geven ook het einde van een blok aan in Markdown.</span><span class="sxs-lookup"><span data-stu-id="85740-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="85740-133">Er moet één witregel tussen verschillende typen Markdown-blokken zijn (zoals tussen een alinea en een lijst of koptekst).</span><span class="sxs-lookup"><span data-stu-id="85740-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="85740-134">Verwijder dubbele witregels.</span><span class="sxs-lookup"><span data-stu-id="85740-134">Remove duplicate blank lines.</span></span> <span data-ttu-id="85740-135">Meerdere lege regels worden weer gegeven als één lege regel in HTML, zodat er geen doel is voor meerdere lege regels.</span><span class="sxs-lookup"><span data-stu-id="85740-135">Multiple blank lines render as a single blank line in HTML so there is no purpose for multiple blank lines.</span></span> <span data-ttu-id="85740-136">Er zijn meerdere lege regels in een code blok die het code blok opsplitsen.</span><span class="sxs-lookup"><span data-stu-id="85740-136">Multiple blank lines within a code block break the code block.</span></span>

<span data-ttu-id="85740-137">Verwijder extra spaties aan het einde van regels.</span><span class="sxs-lookup"><span data-stu-id="85740-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="85740-138">Spatiegebruik is erg belangrijk in Markdown.</span><span class="sxs-lookup"><span data-stu-id="85740-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="85740-139">Gebruik altijd spaties in plaats van harde tabs.</span><span class="sxs-lookup"><span data-stu-id="85740-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="85740-140">Volg spaties kunnen veranderen hoe de weer gave van de prijs wordt gerenderd.</span><span class="sxs-lookup"><span data-stu-id="85740-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="85740-141">Titels en koppen</span><span class="sxs-lookup"><span data-stu-id="85740-141">Titles and headings</span></span>

<span data-ttu-id="85740-142">Gebruik alleen [ATX-kopteksten][atx] (kopteksten in #-stijl in plaats van `=`- of `-`-stijl).</span><span class="sxs-lookup"><span data-stu-id="85740-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="85740-143">Gebruik alleen zinnen - alleen eigennamen en de eerste letter van een titel of koptekst moet een hoofdletter krijgen</span><span class="sxs-lookup"><span data-stu-id="85740-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="85740-144">Er moet één spatie zijn tussen de `#` en de eerste letter van de koptekst</span><span class="sxs-lookup"><span data-stu-id="85740-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="85740-145">Kopteksten moeten worden omgeven door één lege regel</span><span class="sxs-lookup"><span data-stu-id="85740-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="85740-146">Slechts één H1 per document</span><span class="sxs-lookup"><span data-stu-id="85740-146">Only one H1 per document</span></span>
- <span data-ttu-id="85740-147">Koptekst niveaus moeten met één worden verhoogd.</span><span class="sxs-lookup"><span data-stu-id="85740-147">Header levels should increment by one.</span></span> <span data-ttu-id="85740-148">Geen niveaus overs Laan</span><span class="sxs-lookup"><span data-stu-id="85740-148">Do not skip levels</span></span>
- <span data-ttu-id="85740-149">Geen vette of andere opmaak gebruiken in kopteksten</span><span class="sxs-lookup"><span data-stu-id="85740-149">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="85740-150">Beperk de lengte van regels tot 100 tekens</span><span class="sxs-lookup"><span data-stu-id="85740-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="85740-151">Dit geldt voor conceptuele artikelen en cmdlet-verwijzingen.</span><span class="sxs-lookup"><span data-stu-id="85740-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="85740-152">Als u de lijn lengte beperkt, wordt de Lees baarheid van Git-verschillen en-geschiedenis verbeterd.</span><span class="sxs-lookup"><span data-stu-id="85740-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="85740-153">Het maakt het ook gemakkelijker voor andere schrijvers om bijdragen te maken.</span><span class="sxs-lookup"><span data-stu-id="85740-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="85740-154">Gebruik de [uitprijs][reflow] uitbreiding opnieuw plaatsen in Visual Studio code om alinea's eenvoudig opnieuw te plaatsen zodat deze overeenkomen met de voorgeschreven regel lengte.</span><span class="sxs-lookup"><span data-stu-id="85740-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="85740-155">About_topics is beperkt tot 80 tekens.</span><span class="sxs-lookup"><span data-stu-id="85740-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="85740-156">Zie [verwijzings artikelen bewerken](./editing-cmdlet-ref.md#formatting-about_-files)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85740-156">For more specific information, see [Editing reference articles](./editing-cmdlet-ref.md#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="85740-157">Lijsten</span><span class="sxs-lookup"><span data-stu-id="85740-157">Lists</span></span>

<span data-ttu-id="85740-158">Als uw lijst meerdere zinnen of alinea’s bevat, kunt u overwegen een koptekst op subniveau te gebruiken in plaats van een lijst.</span><span class="sxs-lookup"><span data-stu-id="85740-158">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="85740-159">Lijsten moeten worden omgeven door één lege regel.</span><span class="sxs-lookup"><span data-stu-id="85740-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="85740-160">Niet-geordende lijsten</span><span class="sxs-lookup"><span data-stu-id="85740-160">Unordered lists</span></span>

<span data-ttu-id="85740-161">Beëindig lijstitems niet met een punt, tenzij ze meerdere zinnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="85740-161">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="85740-162">Gebruik het afbreekstreepje (`-`) als opsommingsteken voor een lijstitem.</span><span class="sxs-lookup"><span data-stu-id="85740-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="85740-163">Dit voorkomt verwarring met vette of cursieve markeringen, waarbij het sterretje [`*`] wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="85740-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="85740-164">Voeg een regel toe en lijn de inspringing uit met het eerste teken achter het opsommingsteken om een alinea of andere elementen onder een opsomming op te nemen.</span><span class="sxs-lookup"><span data-stu-id="85740-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="85740-165">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-165">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="85740-166">Dit is een lijst met subelementen onder een opsommingsteken.</span><span class="sxs-lookup"><span data-stu-id="85740-166">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="85740-167">Item van eerste opsomming</span><span class="sxs-lookup"><span data-stu-id="85740-167">First bullet item</span></span>

  <span data-ttu-id="85740-168">Zin met uitleg voor de eerste opsomming.</span><span class="sxs-lookup"><span data-stu-id="85740-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="85740-169">Item van subopsommingsteken</span><span class="sxs-lookup"><span data-stu-id="85740-169">Sub-bullet item</span></span>

    <span data-ttu-id="85740-170">Zin met uitleg voor de subopsomming.</span><span class="sxs-lookup"><span data-stu-id="85740-170">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="85740-171">Item van tweede opsomming</span><span class="sxs-lookup"><span data-stu-id="85740-171">Second bullet item</span></span>
- <span data-ttu-id="85740-172">Item van derde opsomming</span><span class="sxs-lookup"><span data-stu-id="85740-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="85740-173">Geordende lijsten</span><span class="sxs-lookup"><span data-stu-id="85740-173">Ordered lists</span></span>

<span data-ttu-id="85740-174">Lijn de inspringing uit met het eerste teken achter het itemnummer om een alinea of andere elementen onder een genummerd item op te nemen.</span><span class="sxs-lookup"><span data-stu-id="85740-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="85740-175">Alle items in een genummerde lijst moeten het nummer gebruiken in `1.` plaats van elk item te verhogen.</span><span class="sxs-lookup"><span data-stu-id="85740-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="85740-176">Bij het weergeven van de Markdown wordt de waarde automatisch verhoogd.</span><span class="sxs-lookup"><span data-stu-id="85740-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="85740-177">Hierdoor kunnen items gemakkelijker in een andere volgorde worden geplaatst en wordt de inspringing van onderliggende inhoud gestandaardiseerd.</span><span class="sxs-lookup"><span data-stu-id="85740-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="85740-178">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-178">For example:</span></span>

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

<span data-ttu-id="85740-179">De resulterende prijs verlaging wordt als volgt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="85740-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="85740-180">Plaats bij het eerste element een spatie achter de 1.</span><span class="sxs-lookup"><span data-stu-id="85740-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="85740-181">Lange zinnen moeten passend worden gemaakt op de volgende regel en worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.</span><span class="sxs-lookup"><span data-stu-id="85740-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="85740-182">U kunt een tweede element (zoals dit) opnemen door een nieuwe regel na de eerste in te voegen en de inspringing uit te lijnen.</span><span class="sxs-lookup"><span data-stu-id="85740-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="85740-183">De inspringing van het tweede element moet worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.</span><span class="sxs-lookup"><span data-stu-id="85740-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="85740-184">Voor items met één cijfer, zoals dit, springt u in naar kolom 4.</span><span class="sxs-lookup"><span data-stu-id="85740-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="85740-185">Voor items met dubbele cijfers, zoals nummer 10, springt u in naar kolom 5.</span><span class="sxs-lookup"><span data-stu-id="85740-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="85740-186">Het volgende genummerde item begint hier.</span><span class="sxs-lookup"><span data-stu-id="85740-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="85740-187">Installatiekopieën</span><span class="sxs-lookup"><span data-stu-id="85740-187">Images</span></span>

<span data-ttu-id="85740-188">De syntaxis voor het insluiten van een afbeelding is:</span><span class="sxs-lookup"><span data-stu-id="85740-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="85740-189">Hierbij is `alt text` een korte beschrijving van de afbeelding en `<folder path>` een relatief pad naar de afbeelding.</span><span class="sxs-lookup"><span data-stu-id="85740-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="85740-190">Voor schermlezers voor visueel gehandicapten is alternatieve tekst nodig.</span><span class="sxs-lookup"><span data-stu-id="85740-190">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="85740-191">Dit is ook handig wanneer de afbeelding niet kan worden weergegeven door een sitebug.</span><span class="sxs-lookup"><span data-stu-id="85740-191">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="85740-192">Afbeeldingen moeten worden opgeslagen in een `media/<article-name>` map in de map waarin het artikel zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="85740-192">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="85740-193">Afbeeldingen moeten niet worden gedeeld tussen artikelen.</span><span class="sxs-lookup"><span data-stu-id="85740-193">Images should not be shared between articles.</span></span> <span data-ttu-id="85740-194">Maak onder de map `media` een map die overeenkomt met de bestandsnaam van uw artikel.</span><span class="sxs-lookup"><span data-stu-id="85740-194">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="85740-195">Kopieer de afbeeldingen voor dat artikel naar de nieuwe map.</span><span class="sxs-lookup"><span data-stu-id="85740-195">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="85740-196">Als een afbeelding door meerdere artikelen wordt gebruikt, moet elke afbeeldingsmap een kopie van het afbeeldingsbestand bevatten.</span><span class="sxs-lookup"><span data-stu-id="85740-196">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="85740-197">Dit voorkomt dat een wijziging voor een afbeelding in het ene artikel gevolgen heeft voor het andere artikelen.</span><span class="sxs-lookup"><span data-stu-id="85740-197">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="85740-198">De volgende afbeeldings bestands typen worden ondersteund: `*.png` , `*.gif` , `*.jpeg` , `*.jpg` , `*.svg`</span><span class="sxs-lookup"><span data-stu-id="85740-198">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="85740-199">Markdown-extensies ondersteund door Open Publishing</span><span class="sxs-lookup"><span data-stu-id="85740-199">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="85740-200">Het [Microsoft docs authoring Pack](/contribute/how-to-write-docs-auth-pack) bevat hulpprogram ma's die ondersteuning bieden voor functies die uniek zijn voor het publicatie systeem.</span><span class="sxs-lookup"><span data-stu-id="85740-200">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="85740-201">Waarschuwingen zijn een uitkortings extensie voor het maken van Block quotes die op docs.microsoft.com worden weer gegeven met kleuren en pictogrammen die de betekenis van de inhoud markeren.</span><span class="sxs-lookup"><span data-stu-id="85740-201">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="85740-202">De volgende typen waarschuwingen worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="85740-202">The following alert types are supported:</span></span>

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

<span data-ttu-id="85740-203">Deze waarschuwingen zien er op docs.microsoft.com als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="85740-203">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="85740-204">Notitie blok</span><span class="sxs-lookup"><span data-stu-id="85740-204">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="85740-205">Information the user should notice even if skimming.</span><span class="sxs-lookup"><span data-stu-id="85740-205">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="85740-206">Info blok</span><span class="sxs-lookup"><span data-stu-id="85740-206">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="85740-207">Optional information to help a user be more successful.</span><span class="sxs-lookup"><span data-stu-id="85740-207">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="85740-208">Belang rijk blok</span><span class="sxs-lookup"><span data-stu-id="85740-208">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85740-209">Essential information required for user success.</span><span class="sxs-lookup"><span data-stu-id="85740-209">Essential information required for user success.</span></span>

<span data-ttu-id="85740-210">Waarschuwings blok</span><span class="sxs-lookup"><span data-stu-id="85740-210">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="85740-211">Negative potential consequences of an action.</span><span class="sxs-lookup"><span data-stu-id="85740-211">Negative potential consequences of an action.</span></span>

<span data-ttu-id="85740-212">Waarschuwings blok</span><span class="sxs-lookup"><span data-stu-id="85740-212">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="85740-213">Bepaalde gevaarlijke gevolgen van een actie.</span><span class="sxs-lookup"><span data-stu-id="85740-213">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="85740-214">Hyperlinks</span><span class="sxs-lookup"><span data-stu-id="85740-214">Hyperlinks</span></span>

- <span data-ttu-id="85740-215">Hyper links moeten de syntaxis van de korting gebruiken `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="85740-215">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="85740-216">Koppelingen moeten indien mogelijk HTTPS zijn.</span><span class="sxs-lookup"><span data-stu-id="85740-216">Links should be HTTPS when possible.</span></span>
- <span data-ttu-id="85740-217">Koppelingen moeten een beschrijvende naam hebben, meestal de titel van het onderwerp waarnaar wordt verwezen</span><span class="sxs-lookup"><span data-stu-id="85740-217">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="85740-218">Met alle items in de sectie ' Verwante koppelingen ' aan de onderkant moet een Hyper link worden</span><span class="sxs-lookup"><span data-stu-id="85740-218">All items in the "related links" section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="85740-219">Gebruik geen accents graves, vetgedrukte tekst of andere opmaak binnen de haakjes van een hyperlink.</span><span class="sxs-lookup"><span data-stu-id="85740-219">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="85740-220">Bare Url's kunnen worden gebruikt wanneer u aan het praten bent over een specifieke URI.</span><span class="sxs-lookup"><span data-stu-id="85740-220">Bare URLs may be used when you are talking about a specific URI.</span></span> <span data-ttu-id="85740-221">De URI moet worden inge sloten in accents graves.</span><span class="sxs-lookup"><span data-stu-id="85740-221">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="85740-222">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-222">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a><span data-ttu-id="85740-223">Koppeling naar andere inhoud</span><span class="sxs-lookup"><span data-stu-id="85740-223">Linking to other content</span></span>

<span data-ttu-id="85740-224">Er zijn twee typen hyper links die worden ondersteund door het publicatie systeem:</span><span class="sxs-lookup"><span data-stu-id="85740-224">There are two types of hyperlinks supported by the publishing system:</span></span>

<span data-ttu-id="85740-225">Een **URL-koppeling** kan een URL-pad zijn dat relatief is ten opzichte van de hoofdmap van docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="85740-225">A **URL link** can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="85740-226">Of een absolute URL die de syntaxis van de volledige URL bevat.</span><span class="sxs-lookup"><span data-stu-id="85740-226">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="85740-227">Bijvoorbeeld: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span><span class="sxs-lookup"><span data-stu-id="85740-227">For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span></span>

- <span data-ttu-id="85740-228">Gebruik URL-koppelingen wanneer u een koppeling maakt naar inhoud buiten Power shell-docs of tussen Naslag informatie over de cmdlet en conceptuele artikelen in Power shell-docs. De eenvoudigste manier om een relatieve koppeling te maken, is door de URL te kopiëren uit uw browser en vervolgens te verwijderen `https://docs.microsoft.com/en-us` van de waarde die u in de prijs opsplitsen hebt geplakt.</span><span class="sxs-lookup"><span data-stu-id="85740-228">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs. The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
- <span data-ttu-id="85740-229">Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (bijv.</span><span class="sxs-lookup"><span data-stu-id="85740-229">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="85740-230">verwijderen `/en-us` van URL).</span><span class="sxs-lookup"><span data-stu-id="85740-230">remove `/en-us` from URL).</span></span>
- <span data-ttu-id="85740-231">Verwijder overbodige query parameters uit de URL, tenzij u een koppeling moet maken naar een specifieke versie van een artikel.</span><span class="sxs-lookup"><span data-stu-id="85740-231">Remove any unnecessary query parameters from the URL unless you need to link to a specific version of an article.</span></span> <span data-ttu-id="85740-232">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="85740-232">Examples:</span></span>
  - <span data-ttu-id="85740-233">`?view=powershell-5.1` : dit wordt gebruikt om een koppeling te maken naar een specifieke versie van Power shell</span><span class="sxs-lookup"><span data-stu-id="85740-233">`?view=powershell-5.1` - this is used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="85740-234">`?redirectedfrom=MSDN` : deze wordt toegevoegd aan de URL wanneer u wordt omgeleid van een oud artikel naar de nieuwe locatie</span><span class="sxs-lookup"><span data-stu-id="85740-234">`?redirectedfrom=MSDN` - this is added to the URL when you get redirected from an old article to its new location</span></span>
- <span data-ttu-id="85740-235">Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site.</span><span class="sxs-lookup"><span data-stu-id="85740-235">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="85740-236">Een **koppeling** naar een bestand wordt gebruikt om te koppelen van het ene referentie artikel naar het andere of van het ene conceptuele artikel naar het andere.</span><span class="sxs-lookup"><span data-stu-id="85740-236">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="85740-237">Als u een verwijzing naar een referentie artikel moet koppelen voor een specifieke versie van Power shell, moet u een URL-koppeling gebruiken.</span><span class="sxs-lookup"><span data-stu-id="85740-237">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

- <span data-ttu-id="85740-238">Bestands koppelingen bevatten een relatief bestandspad (bijvoorbeeld: `../folder/file.md` )</span><span class="sxs-lookup"><span data-stu-id="85740-238">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="85740-239">Alle bestands paden gebruiken tekens voor voorwaartse slash ( `/` )</span><span class="sxs-lookup"><span data-stu-id="85740-239">All file paths use forward-slash (`/`) characters</span></span>

<span data-ttu-id="85740-240">Uitgebreide koppeling is toegestaan voor URL-en bestands koppelingen.</span><span class="sxs-lookup"><span data-stu-id="85740-240">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="85740-241">Voeg het anker toe aan het einde van het doelpad.</span><span class="sxs-lookup"><span data-stu-id="85740-241">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="85740-242">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-242">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="85740-243">Zie [koppelingen in documentatie gebruiken](/contribute/how-to-write-links)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85740-243">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="85740-244">Syntaxiselementen van opdrachten opmaken</span><span class="sxs-lookup"><span data-stu-id="85740-244">Formatting command syntax elements</span></span>

- <span data-ttu-id="85740-245">Gebruik altijd de volledige naam voor cmdlets en para meters.</span><span class="sxs-lookup"><span data-stu-id="85740-245">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="85740-246">Vermijd het gebruik van aliassen tenzij u de alias expliciet demonstreert.</span><span class="sxs-lookup"><span data-stu-id="85740-246">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="85740-247">Eigenschap, para meter, object, type namen, klassen namen en klassen methoden moeten **vet**zijn.</span><span class="sxs-lookup"><span data-stu-id="85740-247">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="85740-248">Eigenschaps-en parameter waarden moeten worden verpakt in accents graves ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="85740-248">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="85740-249">Wanneer u verwijst naar typen met behulp van de stijl met tussen haakjes, gebruikt u accents graves.</span><span class="sxs-lookup"><span data-stu-id="85740-249">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="85740-250">Bijvoorbeeld: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="85740-250">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="85740-251">Taal trefwoorden, namen van cmdlets, functies, variabelen, systeem eigen exe, bestands paden en in-line syntaxis voorbeelden moeten worden verpakt in apostroffen- `` ` `` tekens ().</span><span class="sxs-lookup"><span data-stu-id="85740-251">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="85740-252">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-252">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="85740-253">Wanneer naar een parameter wordt verwezen aan de hand van de naam, moet de naam **vet** zijn.</span><span class="sxs-lookup"><span data-stu-id="85740-253">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="85740-254">Wanneer het gebruik van een parameter met een afbreekstreepje als voorvoegsel wordt gedemonstreerd, moet de parameter tussen accents graves worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="85740-254">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="85740-255">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-255">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="85740-256">Wanneer een voorbeeld van het gebruik van een externe opdracht wordt gebruikt, moet het voorbeeld tussen accents graves zijn geplaatst.</span><span class="sxs-lookup"><span data-stu-id="85740-256">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="85740-257">Neem altijd de bestands extensie op in de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="85740-257">Always include the file extension in the native command.</span></span> <span data-ttu-id="85740-258">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-258">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="85740-259">Met inbegrip van de bestands extensie zorgt ervoor dat de juiste opdracht wordt uitgevoerd volgens de opdracht prioriteit van Power shell.</span><span class="sxs-lookup"><span data-stu-id="85740-259">Including the file extension ensures that the correct command is executed according PowerShell's command precedence.</span></span>

- <span data-ttu-id="85740-260">Als u een conceptueel artikel (in tegenstelling tot referentie-inhoud) schrijft, moet de eerste instantie van een cmdlet-naam een hyperlink naar de cmdlet-documentatie bevatten.</span><span class="sxs-lookup"><span data-stu-id="85740-260">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="85740-261">Gebruik geen accents graves, vetgedrukte tekst of andere opmaak binnen de haakjes van een hyperlink.</span><span class="sxs-lookup"><span data-stu-id="85740-261">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="85740-262">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-262">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="85740-263">Zie de sectie [hyper links](#hyperlinks) in dit artikel voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="85740-263">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="85740-264">Prijs verlaging voor code voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-264">Markdown for code samples</span></span>

<span data-ttu-id="85740-265">Markdown ondersteunt twee verschillende codestijlen:</span><span class="sxs-lookup"><span data-stu-id="85740-265">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="85740-266">**Code reeksen (inline)** : gemarkeerd met één apostroffen ( `` ` `` )-teken.</span><span class="sxs-lookup"><span data-stu-id="85740-266">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="85740-267">Wordt gebruikt in een alinea in plaats van als een zelfstandig blok.</span><span class="sxs-lookup"><span data-stu-id="85740-267">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="85740-268">**Code blokken** : een blok met meerdere regels dat is omgeven door Triple-apostroffen ( `` ``` `` ) teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="85740-268">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="85740-269">Code blokken kunnen ook een taal label volgen volgens het accents graves.</span><span class="sxs-lookup"><span data-stu-id="85740-269">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="85740-270">Het taal label schakelt syntaxis markering in voor de inhoud van het code blok.</span><span class="sxs-lookup"><span data-stu-id="85740-270">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="85740-271">Alle codeblokken moeten zich binnen een afscheiding bevinden.</span><span class="sxs-lookup"><span data-stu-id="85740-271">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="85740-272">Gebruik nooit inspringing voor code blokken.</span><span class="sxs-lookup"><span data-stu-id="85740-272">Never use indentation for code blocks.</span></span> <span data-ttu-id="85740-273">Met prijs verlaging wordt dit patroon toegestaan, maar dit kan een probleem zijn en moet worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="85740-273">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="85740-274">Een code blok bestaat uit een of meer regels code omgeven door een code Fence van Triple-apostroffen ( `` ``` `` ).</span><span class="sxs-lookup"><span data-stu-id="85740-274">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="85740-275">De markeringen voor de codeafscheiding moeten zich op een eigen regel voor en na het codevoorbeeld bevinden.</span><span class="sxs-lookup"><span data-stu-id="85740-275">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="85740-276">De markering na het begin van het codeblok heeft mogelijk een optioneel taallabel.</span><span class="sxs-lookup"><span data-stu-id="85740-276">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="85740-277">In het Open Publishing System (OPS) van Microsoft wordt het taallabel gebruikt om de functie voor markering van de syntaxis te ondersteunen.</span><span class="sxs-lookup"><span data-stu-id="85740-277">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="85740-278">Zie [Geomheiningde code blokken](/contribute/code-in-docs#fenced-code-blocks) in de hand leiding gecentraliseerde Inzender voor een volledige lijst met ondersteunde taal codes.</span><span class="sxs-lookup"><span data-stu-id="85740-278">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="85740-279">OPS voegt tevens een knop **Kopiëren** toe waarmee u de inhoud van het codeblok naar het klembord kopieert.</span><span class="sxs-lookup"><span data-stu-id="85740-279">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="85740-280">Zo kunt u de code snel in een script plakken om het code voorbeeld te testen.</span><span class="sxs-lookup"><span data-stu-id="85740-280">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="85740-281">Niet alle voor beelden in onze documentatie zijn echter bedoeld om te worden uitgevoerd als.</span><span class="sxs-lookup"><span data-stu-id="85740-281">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="85740-282">Sommige code blokken zijn eenvoudige illustraties van een Power shell-concept.</span><span class="sxs-lookup"><span data-stu-id="85740-282">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="85740-283">Er zijn drie typen code blokken die in onze documentatie worden gebruikt:</span><span class="sxs-lookup"><span data-stu-id="85740-283">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="85740-284">Syntaxis blokken</span><span class="sxs-lookup"><span data-stu-id="85740-284">Syntax blocks</span></span>
1. <span data-ttu-id="85740-285">Illustratieve voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-285">Illustrative examples</span></span>
1. <span data-ttu-id="85740-286">Uitvoerbare voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-286">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="85740-287">Syntaxis code blokken</span><span class="sxs-lookup"><span data-stu-id="85740-287">Syntax code blocks</span></span>

<span data-ttu-id="85740-288">Syntaxis code blokken worden gebruikt voor het beschrijven van de syntaxis structuur van een opdracht.</span><span class="sxs-lookup"><span data-stu-id="85740-288">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="85740-289">Gebruik geen taal code op de code Fence.</span><span class="sxs-lookup"><span data-stu-id="85740-289">Do not use a language tag on the code fence.</span></span> <span data-ttu-id="85740-290">Dit voorbeeld toont alle mogelijke parameters van de `Get-Command`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="85740-290">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="85740-291">Dit voorbeeld bevat een beschrijving van de `for`-instructie in algemene termen:</span><span class="sxs-lookup"><span data-stu-id="85740-291">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="85740-292">Illustratieve voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-292">Illustrative examples</span></span>

<span data-ttu-id="85740-293">Illustratieve voorbeelden worden gebruikt om een PowerShell-concept uit te leggen.</span><span class="sxs-lookup"><span data-stu-id="85740-293">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="85740-294">Ze zijn niet bedoeld om naar het klembord te worden gekopieerd en te worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="85740-294">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="85740-295">Deze worden meestal gebruikt voor eenvoudige voor beelden die eenvoudig te typen zijn en eenvoudig te begrijpen zijn.</span><span class="sxs-lookup"><span data-stu-id="85740-295">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="85740-296">Het code blok kan de Power shell-prompt en voorbeeld uitvoer bevatten.</span><span class="sxs-lookup"><span data-stu-id="85740-296">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="85740-297">Hier volgt een eenvoudig voor beeld van de Power shell-vergelijkings operatoren.</span><span class="sxs-lookup"><span data-stu-id="85740-297">Here is a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="85740-298">In dit geval is het niet de bedoeling dat de lezer dit voorbeeld kopieert en uitvoert.</span><span class="sxs-lookup"><span data-stu-id="85740-298">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="85740-299">Uitvoerbare voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-299">Executable examples</span></span>

<span data-ttu-id="85740-300">Complexe voor beelden of voor beelden die bedoeld zijn om te worden gekopieerd en uitgevoerd, moeten de volgende opmaak voor blok stijl gebruiken:</span><span class="sxs-lookup"><span data-stu-id="85740-300">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="85740-301">De uitvoer die door PowerShell-opdrachten wordt weergegeven, moet zich in een **Uitvoer**-codeblok bevinden om markering van de syntaxis te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="85740-301">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="85740-302">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="85740-302">For example:</span></span>

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

<span data-ttu-id="85740-303">Het codelabel **Uitvoer** is geen officiële ‘taal’ die door het systeem voor het markeren van syntaxis wordt ondersteund.</span><span class="sxs-lookup"><span data-stu-id="85740-303">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="85740-304">Dit label is echter nuttig omdat OPS het label "uitvoer" toevoegt aan het frame van de code op de webpagina.</span><span class="sxs-lookup"><span data-stu-id="85740-304">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="85740-305">Het vak uitvoer code heeft geen syntaxis markering.</span><span class="sxs-lookup"><span data-stu-id="85740-305">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="85740-306">Stijlregels voor code</span><span class="sxs-lookup"><span data-stu-id="85740-306">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="85740-307">Voortzetting van regels in codevoorbeelden vermijden</span><span class="sxs-lookup"><span data-stu-id="85740-307">Avoid line continuation in code samples</span></span>

<span data-ttu-id="85740-308">Vermijd tekens voor voortzetting van de regel (`` ` ``) in PowerShell-codevoorbeelden.</span><span class="sxs-lookup"><span data-stu-id="85740-308">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="85740-309">Deze zijn moeilijk te zien en kunnen problemen veroorzaken als er extra spaties aan het einde van de regel staan.</span><span class="sxs-lookup"><span data-stu-id="85740-309">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="85740-310">Gebruik PowerShell-splatting om de regellengte in te korten voor cmdlets die veel parameters bevatten.</span><span class="sxs-lookup"><span data-stu-id="85740-310">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="85740-311">Profiteer van de mogelijkheden voor natuurlijke regeleinden in PowerShell, zoals na het pijpteken (`|`), accolades en haakjes.</span><span class="sxs-lookup"><span data-stu-id="85740-311">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="85740-312">PowerShell-prompts vermijden in voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-312">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="85740-313">Het gebruik van de prompt-tekenreeks wordt afgeraden en moet worden beperkt tot scenario’s die zijn bedoeld om het gebruik van de opdrachtregel te illustreren.</span><span class="sxs-lookup"><span data-stu-id="85740-313">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="85740-314">Voor de meeste van deze voor beelden moet de prompt teken reeks zijn `PS>` .</span><span class="sxs-lookup"><span data-stu-id="85740-314">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="85740-315">Deze prompt is onafhankelijk van indicatoren voor specifieke besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="85740-315">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="85740-316">Prompts zijn vereist voor voorbeelden waarin opdrachten worden weergegeven waarmee de prompt wordt aangepast of als het getoonde pad van belang is voor het scenario dat wordt geïllustreerd.</span><span class="sxs-lookup"><span data-stu-id="85740-316">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="85740-317">In het volgende voorbeeld wordt getoond hoe de prompt verandert als de registerprovider wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="85740-317">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="85740-318">Geen aliassen gebruiken in voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-318">Do not use aliases in examples</span></span>

<span data-ttu-id="85740-319">Gebruik altijd de volledige naam van cmdlets en parameters, tenzij u het specifiek over de alias hebt.</span><span class="sxs-lookup"><span data-stu-id="85740-319">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="85740-320">De namen van cmdlets en para meters moeten gebruikmaken van de juiste namen van Pascal-cases.</span><span class="sxs-lookup"><span data-stu-id="85740-320">Cmdlet and parameter names must use the proper Pascal-cased names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="85740-321">Parameters gebruiken in voorbeelden</span><span class="sxs-lookup"><span data-stu-id="85740-321">Using parameters in examples</span></span>

<span data-ttu-id="85740-322">Vermijd het gebruik van positionele parameters.</span><span class="sxs-lookup"><span data-stu-id="85740-322">Avoid using positional parameters.</span></span> <span data-ttu-id="85740-323">Over het algemeen moet u altijd de parameter naam in een voor beeld meenemen, zelfs als de para meter positioneel is.</span><span class="sxs-lookup"><span data-stu-id="85740-323">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="85740-324">Dit verkleint de kans op verwarring in uw voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="85740-324">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="85740-325">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="85740-325">Next steps</span></span>

[<span data-ttu-id="85740-326">Naslaginformatie voor cmdlets bewerken</span><span class="sxs-lookup"><span data-stu-id="85740-326">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
