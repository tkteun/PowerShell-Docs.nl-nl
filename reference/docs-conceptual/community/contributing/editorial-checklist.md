---
title: Redactionele controlelijst
description: Dit is een overzicht van de regels voor het bewerken van Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b5baf7366239084779d34e23f218e5e6222ed1a3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "81624734"
---
# <a name="editors-checklist"></a><span data-ttu-id="476d0-103">Controle lijst van de editor</span><span class="sxs-lookup"><span data-stu-id="476d0-103">Editor's checklist</span></span>

<span data-ttu-id="476d0-104">Dit is een samen vatting van regels die moeten worden toegepast bij het schrijven van nieuwe of het bijwerken van bestaande artikelen.</span><span class="sxs-lookup"><span data-stu-id="476d0-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="476d0-105">Zie andere artikelen in de hand leiding van de mede werker voor gedetailleerde uitleg en voor beelden van deze regels.</span><span class="sxs-lookup"><span data-stu-id="476d0-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="476d0-106">Metagegevens</span><span class="sxs-lookup"><span data-stu-id="476d0-106">Metadata</span></span>

- <span data-ttu-id="476d0-107">`ms.date`: moet de notatie **mm/dd/jjjj** hebben</span><span class="sxs-lookup"><span data-stu-id="476d0-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="476d0-108">De datum wijzigen wanneer er een belang rijke of feitelijke update is</span><span class="sxs-lookup"><span data-stu-id="476d0-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="476d0-109">Het artikel opnieuw ordenen</span><span class="sxs-lookup"><span data-stu-id="476d0-109">Reorganizing the article</span></span>
    - <span data-ttu-id="476d0-110">Feitelijke fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="476d0-110">Fixing factual errors</span></span>
    - <span data-ttu-id="476d0-111">Nieuwe informatie toevoegen</span><span class="sxs-lookup"><span data-stu-id="476d0-111">Adding new information</span></span>
  - <span data-ttu-id="476d0-112">Wijzig de datum niet als de update niet significant is</span><span class="sxs-lookup"><span data-stu-id="476d0-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="476d0-113">Typfouten en opmaak corrigeren</span><span class="sxs-lookup"><span data-stu-id="476d0-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="476d0-114">`title`: unieke teken reeks van 43-59 tekens inclusief spaties</span><span class="sxs-lookup"><span data-stu-id="476d0-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="476d0-115">Site-id niet toevoegen (deze wordt automatisch gegenereerd)</span><span class="sxs-lookup"><span data-stu-id="476d0-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="476d0-116">Gebruik een hoofd letter: alleen het eerste woord en eventuele eigen naam woorden</span><span class="sxs-lookup"><span data-stu-id="476d0-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="476d0-117">`description`: 115-145 tekens inclusief spaties: deze abstract wordt weer gegeven in het Zoek resultaat</span><span class="sxs-lookup"><span data-stu-id="476d0-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="476d0-118">Opmaak</span><span class="sxs-lookup"><span data-stu-id="476d0-118">Formatting</span></span>

- <span data-ttu-id="476d0-119">Apostroffen-syntaxis elementen die worden weer gegeven, inline in een alinea</span><span class="sxs-lookup"><span data-stu-id="476d0-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="476d0-120">Namen van cmdlets `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="476d0-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="476d0-121">Variabeletype `$counter`</span><span class="sxs-lookup"><span data-stu-id="476d0-121">Variable `$counter`</span></span>
  - <span data-ttu-id="476d0-122">Syntaxis voorbeelden `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="476d0-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="476d0-123">Bestands paden `C:\Program Files\PowerShell` , `/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="476d0-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="476d0-124">Url's die niet in het document kunnen worden geklikt</span><span class="sxs-lookup"><span data-stu-id="476d0-124">URLs that are not meant to be clickable in the document</span></span>
  - <span data-ttu-id="476d0-125">Eigenschaps-of parameter waarden</span><span class="sxs-lookup"><span data-stu-id="476d0-125">Property or parameter values</span></span>
- <span data-ttu-id="476d0-126">Vetgedrukt gebruiken voor eigenschapnamen van eigenschappen, parameter namen, klassenamen, module namen, entiteits namen, object-of type namen</span><span class="sxs-lookup"><span data-stu-id="476d0-126">Use bold for property names, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="476d0-127">Vet wordt gebruikt voor semantische opmaak, niet nadruk</span><span class="sxs-lookup"><span data-stu-id="476d0-127">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="476d0-128">Vet: sterretjes gebruiken `**`</span><span class="sxs-lookup"><span data-stu-id="476d0-128">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="476d0-129">Cursief: onderstrepings tekens gebruiken `_`</span><span class="sxs-lookup"><span data-stu-id="476d0-129">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="476d0-130">Alleen gebruikt voor nadruk, niet voor semantische opmaak</span><span class="sxs-lookup"><span data-stu-id="476d0-130">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="476d0-131">Regel einden in 100 kolommen (of op 80 voor **about_Topics**)</span><span class="sxs-lookup"><span data-stu-id="476d0-131">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="476d0-132">Geen harde tabbladen: alleen spaties gebruiken</span><span class="sxs-lookup"><span data-stu-id="476d0-132">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="476d0-133">Geen Volg spaties op regels</span><span class="sxs-lookup"><span data-stu-id="476d0-133">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="476d0-134">Kopteksten</span><span class="sxs-lookup"><span data-stu-id="476d0-134">Headers</span></span>

- <span data-ttu-id="476d0-135">H1 is in eerste instantie slechts één H1 per artikel</span><span class="sxs-lookup"><span data-stu-id="476d0-135">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="476d0-136">Alleen [ATX-kopteksten](https://github.github.com/gfm/#atx-headings) gebruiken</span><span class="sxs-lookup"><span data-stu-id="476d0-136">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="476d0-137">Gebruik een zin voor alle kopteksten</span><span class="sxs-lookup"><span data-stu-id="476d0-137">Use sentence case for all headers</span></span>
- <span data-ttu-id="476d0-138">Geen niveaus overs Laan: geen H3 zonder een H2</span><span class="sxs-lookup"><span data-stu-id="476d0-138">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="476d0-139">Maximale diepte van H3 of H4</span><span class="sxs-lookup"><span data-stu-id="476d0-139">Max depth of H3 or H4</span></span>
- <span data-ttu-id="476d0-140">Lege regel voor en na</span><span class="sxs-lookup"><span data-stu-id="476d0-140">Blank line before and after</span></span>
- <span data-ttu-id="476d0-141">PlatyPS dwingt specifieke headers in het schema af-Voeg geen headers toe of verwijder deze</span><span class="sxs-lookup"><span data-stu-id="476d0-141">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="476d0-142">Codeblokken</span><span class="sxs-lookup"><span data-stu-id="476d0-142">Code blocks</span></span>

- <span data-ttu-id="476d0-143">Lege regel voor en na</span><span class="sxs-lookup"><span data-stu-id="476d0-143">Blank line before and after</span></span>
- <span data-ttu-id="476d0-144">Gelabelde code Fences gebruiken- **Power shell**, **output** of een andere geschikte taal-id</span><span class="sxs-lookup"><span data-stu-id="476d0-144">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="476d0-145">Niet-gecodeerde blokken met omheinings syntaxis of andere shells</span><span class="sxs-lookup"><span data-stu-id="476d0-145">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="476d0-146">Plaats de uitvoer in een afzonderlijk code blok, met uitzonde ring van eenvoudige voor beelden waarin u niet van plan bent om de knop **kopiëren** te gebruiken voor de lezer</span><span class="sxs-lookup"><span data-stu-id="476d0-146">Put output in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="476d0-147">Lijst met [ondersteunde talen](/contribute/code-in-docs#supported-languages) weer geven</span><span class="sxs-lookup"><span data-stu-id="476d0-147">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="476d0-148">Lijsten</span><span class="sxs-lookup"><span data-stu-id="476d0-148">Lists</span></span>

- <span data-ttu-id="476d0-149">Correct Inge sprongen</span><span class="sxs-lookup"><span data-stu-id="476d0-149">Indented properly</span></span>
- <span data-ttu-id="476d0-150">Lege regel voor het eerste item en na het laatste item</span><span class="sxs-lookup"><span data-stu-id="476d0-150">Blank line before first item and after last item</span></span>
- <span data-ttu-id="476d0-151">Bullet: use afbreek streepje ( `-` ) geen asterisk ( `*` )-te eenvoudig te verwarren met nadruk</span><span class="sxs-lookup"><span data-stu-id="476d0-151">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="476d0-152">Voor genummerde lijsten zijn alle cijfers ' 1 '.</span><span class="sxs-lookup"><span data-stu-id="476d0-152">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="476d0-153">Terminologie</span><span class="sxs-lookup"><span data-stu-id="476d0-153">Terminology</span></span>

- <span data-ttu-id="476d0-154">Power shell versus Windows Power shell versus Power shell core</span><span class="sxs-lookup"><span data-stu-id="476d0-154">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="476d0-155">Zie [product terminologie](powershell-style-guide.md#product-terminology)</span><span class="sxs-lookup"><span data-stu-id="476d0-155">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="476d0-156">Naslag informatie voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="476d0-156">Cmdlet reference examples</span></span>

- <span data-ttu-id="476d0-157">Er moet ten minste één voor beeld in de cmdlet-verwijzing zijn</span><span class="sxs-lookup"><span data-stu-id="476d0-157">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="476d0-158">Voor beelden moeten net genoeg code zijn om het gebruik te demonstreren</span><span class="sxs-lookup"><span data-stu-id="476d0-158">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="476d0-159">PowerShell-syntaxis</span><span class="sxs-lookup"><span data-stu-id="476d0-159">PowerShell syntax</span></span>
  - <span data-ttu-id="476d0-160">Volledige namen van cmdlets en para meters gebruiken-geen aliassen</span><span class="sxs-lookup"><span data-stu-id="476d0-160">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="476d0-161">Splatting gebruiken voor para meters wanneer de opdracht regel te lang wordt</span><span class="sxs-lookup"><span data-stu-id="476d0-161">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="476d0-162">Vermijd het gebruik van regel voortzettings accents graves indien nodig</span><span class="sxs-lookup"><span data-stu-id="476d0-162">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="476d0-163">Verwijder of Vereenvoudig de Power shell-prompt ( `PS>` ), met uitzonde ring van waar nodig voor het voor beeld</span><span class="sxs-lookup"><span data-stu-id="476d0-163">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="476d0-164">Voor de cmdlet-referentie moet het volgende PlatyPS-schema worden gevolgd</span><span class="sxs-lookup"><span data-stu-id="476d0-164">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="476d0-165">Plaats geen alinea's tussen de code blokken.</span><span class="sxs-lookup"><span data-stu-id="476d0-165">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="476d0-166">Alle beschrijvende inhoud moet vóór of na de code blokken komen.</span><span class="sxs-lookup"><span data-stu-id="476d0-166">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="476d0-167">Koppelen aan andere documenten</span><span class="sxs-lookup"><span data-stu-id="476d0-167">Linking to other documents</span></span>

- <span data-ttu-id="476d0-168">Koppelen buiten de docset of tussen de cmdlet-verwijzing en de conceptuele</span><span class="sxs-lookup"><span data-stu-id="476d0-168">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="476d0-169">Relatieve Url's gebruiken wanneer u een koppeling maakt naar docs.microsoft.com (verwijderen `https://docs.microsoft.com/en-us` )</span><span class="sxs-lookup"><span data-stu-id="476d0-169">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="476d0-170">Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (bijv.</span><span class="sxs-lookup"><span data-stu-id="476d0-170">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="476d0-171">verwijderen `/en-us` uit URL)</span><span class="sxs-lookup"><span data-stu-id="476d0-171">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="476d0-172">Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site</span><span class="sxs-lookup"><span data-stu-id="476d0-172">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="476d0-173">Binnen docset</span><span class="sxs-lookup"><span data-stu-id="476d0-173">Within docset</span></span>
  - <span data-ttu-id="476d0-174">Koppeling naar bestandspad (bijvoorbeeld `../folder/file.md` )</span><span class="sxs-lookup"><span data-stu-id="476d0-174">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="476d0-175">Alle bestands paden gebruiken tekens voor voorwaartse slash ( `/` )</span><span class="sxs-lookup"><span data-stu-id="476d0-175">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="476d0-176">Afbeeldings koppelingen moeten unieke alternatieve tekst bevatten</span><span class="sxs-lookup"><span data-stu-id="476d0-176">Image links should have unique alt text</span></span>
