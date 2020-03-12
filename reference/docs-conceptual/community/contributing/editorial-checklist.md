---
title: Controle lijst voor redactionele
description: Dit is een overzicht van de regels voor het bewerken van Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078575"
---
# <a name="editors-checklist"></a><span data-ttu-id="125cb-103">Controle lijst van de editor</span><span class="sxs-lookup"><span data-stu-id="125cb-103">Editor's checklist</span></span>

<span data-ttu-id="125cb-104">Dit is een samen vatting van regels die moeten worden toegepast bij het schrijven van nieuwe of het bijwerken van bestaande artikelen.</span><span class="sxs-lookup"><span data-stu-id="125cb-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="125cb-105">Zie andere artikelen in de hand leiding van de mede werker voor gedetailleerde uitleg en voor beelden van deze regels.</span><span class="sxs-lookup"><span data-stu-id="125cb-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="125cb-106">Metagegevens</span><span class="sxs-lookup"><span data-stu-id="125cb-106">Metadata</span></span>

- <span data-ttu-id="125cb-107">`ms.date`: moet de notatie **mm/dd/jjjj** hebben</span><span class="sxs-lookup"><span data-stu-id="125cb-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="125cb-108">De datum wijzigen wanneer er een belang rijke of feitelijke update is</span><span class="sxs-lookup"><span data-stu-id="125cb-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="125cb-109">Het artikel opnieuw ordenen</span><span class="sxs-lookup"><span data-stu-id="125cb-109">Reorganizing the article</span></span>
    - <span data-ttu-id="125cb-110">Feitelijke fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="125cb-110">Fixing factual errors</span></span>
    - <span data-ttu-id="125cb-111">Nieuwe informatie toevoegen</span><span class="sxs-lookup"><span data-stu-id="125cb-111">Adding new information</span></span>
  - <span data-ttu-id="125cb-112">Wijzig de datum niet als de update niet significant is</span><span class="sxs-lookup"><span data-stu-id="125cb-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="125cb-113">Typfouten en opmaak corrigeren</span><span class="sxs-lookup"><span data-stu-id="125cb-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="125cb-114">`title`: een unieke teken reeks van 43-59 tekens inclusief spaties</span><span class="sxs-lookup"><span data-stu-id="125cb-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="125cb-115">Site-id niet toevoegen (deze wordt automatisch gegenereerd)</span><span class="sxs-lookup"><span data-stu-id="125cb-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="125cb-116">Gebruik een hoofd letter: alleen het eerste woord en eventuele eigen naam woorden</span><span class="sxs-lookup"><span data-stu-id="125cb-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="125cb-117">`description`: 115-145 tekens inclusief spaties: deze abstract wordt weer gegeven in het Zoek resultaat</span><span class="sxs-lookup"><span data-stu-id="125cb-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="125cb-118">Opmaak</span><span class="sxs-lookup"><span data-stu-id="125cb-118">Formatting</span></span>

- <span data-ttu-id="125cb-119">Apostroffen-syntaxis elementen die worden weer gegeven, inline in een alinea</span><span class="sxs-lookup"><span data-stu-id="125cb-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="125cb-120">Cmdlet-namen `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="125cb-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="125cb-121">Variabele `$counter`</span><span class="sxs-lookup"><span data-stu-id="125cb-121">Variable `$counter`</span></span>
  - <span data-ttu-id="125cb-122">Voor beelden van syntaxis `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="125cb-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="125cb-123">Bestands paden `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="125cb-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="125cb-124">Url's die niet in het document kunnen worden geklikt</span><span class="sxs-lookup"><span data-stu-id="125cb-124">URLs that are not meant to be clickable in the document</span></span>
- <span data-ttu-id="125cb-125">Vet gebruiken voor eigenschapnamen, parameter waarden, parameter namen, klassen namen, module namen, namen van entiteiten, object-of type namen</span><span class="sxs-lookup"><span data-stu-id="125cb-125">Use bold for property names, parameter values, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="125cb-126">Vet wordt gebruikt voor semantische opmaak, niet nadruk</span><span class="sxs-lookup"><span data-stu-id="125cb-126">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="125cb-127">Vet: sterretjes `**` gebruiken</span><span class="sxs-lookup"><span data-stu-id="125cb-127">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="125cb-128">Cursief: onderstrepings `_` gebruiken</span><span class="sxs-lookup"><span data-stu-id="125cb-128">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="125cb-129">Alleen gebruikt voor nadruk, niet voor semantische opmaak</span><span class="sxs-lookup"><span data-stu-id="125cb-129">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="125cb-130">Regel einden in 100 kolommen (of op 80 voor **about_Topics**)</span><span class="sxs-lookup"><span data-stu-id="125cb-130">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="125cb-131">Geen harde tabbladen: alleen spaties gebruiken</span><span class="sxs-lookup"><span data-stu-id="125cb-131">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="125cb-132">Geen Volg spaties op regels</span><span class="sxs-lookup"><span data-stu-id="125cb-132">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="125cb-133">Headers</span><span class="sxs-lookup"><span data-stu-id="125cb-133">Headers</span></span>

- <span data-ttu-id="125cb-134">H1 is in eerste instantie slechts één H1 per artikel</span><span class="sxs-lookup"><span data-stu-id="125cb-134">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="125cb-135">Alleen [ATX-kopteksten](https://github.github.com/gfm/#atx-headings) gebruiken</span><span class="sxs-lookup"><span data-stu-id="125cb-135">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="125cb-136">Gebruik een zin voor alle kopteksten</span><span class="sxs-lookup"><span data-stu-id="125cb-136">Use sentence case for all headers</span></span>
- <span data-ttu-id="125cb-137">Geen niveaus overs Laan: geen H3 zonder een H2</span><span class="sxs-lookup"><span data-stu-id="125cb-137">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="125cb-138">Maximale diepte van H3 of H4</span><span class="sxs-lookup"><span data-stu-id="125cb-138">Max depth of H3 or H4</span></span>
- <span data-ttu-id="125cb-139">Lege regel voor en na</span><span class="sxs-lookup"><span data-stu-id="125cb-139">Blank line before and after</span></span>
- <span data-ttu-id="125cb-140">PlatyPS dwingt specifieke headers in het schema af-Voeg geen headers toe of verwijder deze</span><span class="sxs-lookup"><span data-stu-id="125cb-140">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="125cb-141">Code blokken</span><span class="sxs-lookup"><span data-stu-id="125cb-141">Code blocks</span></span>

- <span data-ttu-id="125cb-142">Lege regel voor en na</span><span class="sxs-lookup"><span data-stu-id="125cb-142">Blank line before and after</span></span>
- <span data-ttu-id="125cb-143">Gelabelde code Fences gebruiken- **Power shell**, **output**of een andere geschikte taal-id</span><span class="sxs-lookup"><span data-stu-id="125cb-143">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="125cb-144">Niet-gecodeerde blokken met omheinings syntaxis of andere shells</span><span class="sxs-lookup"><span data-stu-id="125cb-144">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="125cb-145">Plaats de **uitvoer** in een afzonderlijk code blok, met uitzonde ring van eenvoudige voor beelden waarin u niet van plan bent om de knop **kopiëren** te gebruiken voor de lezer</span><span class="sxs-lookup"><span data-stu-id="125cb-145">Put **Output** in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="125cb-146">Lijst met [ondersteunde talen](/contribute/code-in-docs#supported-languages) weer geven</span><span class="sxs-lookup"><span data-stu-id="125cb-146">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="125cb-147">Lijsten</span><span class="sxs-lookup"><span data-stu-id="125cb-147">Lists</span></span>

- <span data-ttu-id="125cb-148">Correct Inge sprongen</span><span class="sxs-lookup"><span data-stu-id="125cb-148">Indented properly</span></span>
- <span data-ttu-id="125cb-149">Lege regel voor het eerste item en na het laatste item</span><span class="sxs-lookup"><span data-stu-id="125cb-149">Blank line before first item and after last item</span></span>
- <span data-ttu-id="125cb-150">Bullet: use afbreek streepje (`-`) geen asterisk (`*`)-te eenvoudig te verwarren met nadruk</span><span class="sxs-lookup"><span data-stu-id="125cb-150">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="125cb-151">Voor genummerde lijsten zijn alle cijfers ' 1 '.</span><span class="sxs-lookup"><span data-stu-id="125cb-151">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="125cb-152">Terminologie</span><span class="sxs-lookup"><span data-stu-id="125cb-152">Terminology</span></span>

- <span data-ttu-id="125cb-153">Power shell versus Windows Power shell versus Power shell core</span><span class="sxs-lookup"><span data-stu-id="125cb-153">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="125cb-154">Zie [product terminologie](powershell-style-guide.md#product-terminology)</span><span class="sxs-lookup"><span data-stu-id="125cb-154">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="125cb-155">Naslag informatie voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="125cb-155">Cmdlet reference examples</span></span>

- <span data-ttu-id="125cb-156">Er moet ten minste één voor beeld in de cmdlet-verwijzing zijn</span><span class="sxs-lookup"><span data-stu-id="125cb-156">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="125cb-157">Voor beelden moeten net genoeg code zijn om het gebruik te demonstreren</span><span class="sxs-lookup"><span data-stu-id="125cb-157">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="125cb-158">Power shell-syntaxis</span><span class="sxs-lookup"><span data-stu-id="125cb-158">PowerShell syntax</span></span>
  - <span data-ttu-id="125cb-159">Volledige namen van cmdlets en para meters gebruiken-geen aliassen</span><span class="sxs-lookup"><span data-stu-id="125cb-159">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="125cb-160">Splatting gebruiken voor para meters wanneer de opdracht regel te lang wordt</span><span class="sxs-lookup"><span data-stu-id="125cb-160">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="125cb-161">Vermijd het gebruik van regel voortzettings accents graves indien nodig</span><span class="sxs-lookup"><span data-stu-id="125cb-161">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="125cb-162">De Power shell-prompt (`PS>`) verwijderen of vereenvoudigen, behalve wanneer dit nodig is voor het voor beeld</span><span class="sxs-lookup"><span data-stu-id="125cb-162">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="125cb-163">Voor de cmdlet-referentie moet het volgende PlatyPS-schema worden gevolgd</span><span class="sxs-lookup"><span data-stu-id="125cb-163">Cmdlet reference example must follow the following PlatyPS schema</span></span>

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

- <span data-ttu-id="125cb-164">Plaats geen alinea's tussen de code blokken.</span><span class="sxs-lookup"><span data-stu-id="125cb-164">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="125cb-165">Alle beschrijvende inhoud moet vóór of na de code blokken komen.</span><span class="sxs-lookup"><span data-stu-id="125cb-165">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="125cb-166">Koppelen aan andere documenten</span><span class="sxs-lookup"><span data-stu-id="125cb-166">Linking to other documents</span></span>

- <span data-ttu-id="125cb-167">Koppelen buiten de docset of tussen de cmdlet-verwijzing en de conceptuele</span><span class="sxs-lookup"><span data-stu-id="125cb-167">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="125cb-168">Relatieve Url's gebruiken bij het koppelen aan docs.microsoft.com (`https://docs.microsoft.com/en-us`verwijderen)</span><span class="sxs-lookup"><span data-stu-id="125cb-168">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="125cb-169">Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (bijv.</span><span class="sxs-lookup"><span data-stu-id="125cb-169">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="125cb-170">`/en-us` verwijderen uit URL)</span><span class="sxs-lookup"><span data-stu-id="125cb-170">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="125cb-171">Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site</span><span class="sxs-lookup"><span data-stu-id="125cb-171">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="125cb-172">Binnen docset</span><span class="sxs-lookup"><span data-stu-id="125cb-172">Within docset</span></span>
  - <span data-ttu-id="125cb-173">Koppeling naar bestandspad (bijvoorbeeld `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="125cb-173">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="125cb-174">Alle bestands paden gebruiken tekens voor voorwaartse slash (`/`)</span><span class="sxs-lookup"><span data-stu-id="125cb-174">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="125cb-175">Afbeeldings koppelingen moeten unieke alternatieve tekst bevatten</span><span class="sxs-lookup"><span data-stu-id="125cb-175">Image links should have unique alt text</span></span>
