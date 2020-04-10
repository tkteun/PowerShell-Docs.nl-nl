---
title: Stijlgids voor PowerShell-documentatie
description: Dit artikel bevat de regels van de stijl voor het schrijven van Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b4bc547c3560538ba246a6ed582fd4f9ce796dd2
ms.sourcegitcommit: bda70d2163eef5a158441cb1c38ac422d704535d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/10/2020
ms.locfileid: "81005581"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="2a231-103">Stijlgids voor PowerShell-documentatie</span><span class="sxs-lookup"><span data-stu-id="2a231-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="2a231-104">Dit artikel bevat richt lijnen die specifiek zijn voor de Power shell-docs-inhoud.</span><span class="sxs-lookup"><span data-stu-id="2a231-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="2a231-105">Dit is gebaseerd op de informatie die wordt beschreven in het [overzicht](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="2a231-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="2a231-106">Product terminologie</span><span class="sxs-lookup"><span data-stu-id="2a231-106">Product Terminology</span></span>

<span data-ttu-id="2a231-107">Er zijn verschillende varianten van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2a231-107">There are several variants of PowerShell.</span></span>
<span data-ttu-id="2a231-108">In deze tabel worden enkele van de verschillende termen gedefinieerd die worden gebruikt voor het bespreken van Power shell.</span><span class="sxs-lookup"><span data-stu-id="2a231-108">This table defines some of the different terms used to discuss PowerShell.</span></span>

- <span data-ttu-id="2a231-109">**Power shell** : dit is de standaard instelling.</span><span class="sxs-lookup"><span data-stu-id="2a231-109">**PowerShell** - This is the default.</span></span> <span data-ttu-id="2a231-110">We overwegen Power shell 7 en nog eens te zijn. de echte Power shell gaat verder.</span><span class="sxs-lookup"><span data-stu-id="2a231-110">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>

- <span data-ttu-id="2a231-111">**Power shell core** -Power shell gebouwd op .net core.</span><span class="sxs-lookup"><span data-stu-id="2a231-111">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="2a231-112">Het gebruik van de term **core** moet worden beperkt tot gevallen waarin het nodig is om het te onderscheiden van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="2a231-112">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>

- <span data-ttu-id="2a231-113">**Windows Power shell** -Power shell is gebouwd op .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2a231-113">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="2a231-114">Windows Power shell wordt alleen in Windows geleverd en vereist het volledige Framework.</span><span class="sxs-lookup"><span data-stu-id="2a231-114">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

<span data-ttu-id="2a231-115">In het algemeen kunnen verwijzingen naar ' Windows Power shell ' in de documentatie worden gewijzigd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2a231-115">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
<span data-ttu-id="2a231-116">' Windows Power shell ' mag **niet** worden gewijzigd wanneer de Windows-specifieke technologie wordt besproken.</span><span class="sxs-lookup"><span data-stu-id="2a231-116">"Windows PowerShell" should **not** be changed when Windows-specific technology is being discussed.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="2a231-117">Details van prijs verlaging</span><span class="sxs-lookup"><span data-stu-id="2a231-117">Markdown specifics</span></span>

<span data-ttu-id="2a231-118">Het micro soft open publishing-systeem (OPS) dat onze documentatie bouwt, maakt gebruik van [markdig][] voor het verwerken van de verkortings documenten.</span><span class="sxs-lookup"><span data-stu-id="2a231-118">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="2a231-119">Markdig parseert de documenten op basis van de regels van de meest recente [CommonMark][] -specificatie.</span><span class="sxs-lookup"><span data-stu-id="2a231-119">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="2a231-120">De nieuwe CommonMark-specificatie is veel strikter dan de constructie van sommige prijs verlagings elementen.</span><span class="sxs-lookup"><span data-stu-id="2a231-120">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="2a231-121">Let op de details die in dit document worden gegeven.</span><span class="sxs-lookup"><span data-stu-id="2a231-121">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="2a231-122">Lege regels, spaties en tabbladen</span><span class="sxs-lookup"><span data-stu-id="2a231-122">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="2a231-123">Verwijder dubbele lege regels.</span><span class="sxs-lookup"><span data-stu-id="2a231-123">Remove duplicate blank lines.</span></span> <span data-ttu-id="2a231-124">Meerdere lege regels worden weer gegeven als één lege regel in HTML, zodat er geen meerdere lege regels zijn.</span><span class="sxs-lookup"><span data-stu-id="2a231-124">Multiple blank lines render as a single blank line in HTML so there is not purpose for multiple blank lines.</span></span>

<span data-ttu-id="2a231-125">Lege regels geven ook aan dat het einde van een blok in de prijs opgave wordt gesignaleerd.</span><span class="sxs-lookup"><span data-stu-id="2a231-125">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="2a231-126">Er mag slechts één lege waarde zijn tussen blokken van verschillende typen (bijvoorbeeld tussen een alinea en een lijst of koptekst).</span><span class="sxs-lookup"><span data-stu-id="2a231-126">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

> [!NOTE]
> <span data-ttu-id="2a231-127">De afstand is significant in de prijs verlaging.</span><span class="sxs-lookup"><span data-stu-id="2a231-127">Spacing is significant in Markdown.</span></span> <span data-ttu-id="2a231-128">Maakt altijd gebruik van spaties in plaats van harde tabbladen.</span><span class="sxs-lookup"><span data-stu-id="2a231-128">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="2a231-129">Verwijder extra spaties aan het einde van regels.</span><span class="sxs-lookup"><span data-stu-id="2a231-129">Remove extra spaces at the end of lines.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="2a231-130">Titels en koppen</span><span class="sxs-lookup"><span data-stu-id="2a231-130">Titles and headings</span></span>

<span data-ttu-id="2a231-131">Gebruik alleen [ATX-koppen][atx] (# Style, in plaats van `=`-of `-` stijl headers).</span><span class="sxs-lookup"><span data-stu-id="2a231-131">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="2a231-132">Gebruik alleen zinnen: alleen de juiste naam woorden en de eerste letter van een titel of koptekst moeten worden gekapitaliseerd</span><span class="sxs-lookup"><span data-stu-id="2a231-132">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="2a231-133">Er mag slechts één spatie tussen de `#` en de eerste letter van de kop staan</span><span class="sxs-lookup"><span data-stu-id="2a231-133">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="2a231-134">Koppen moeten worden omgeven door één lege regel</span><span class="sxs-lookup"><span data-stu-id="2a231-134">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="2a231-135">Slechts één H1 per document</span><span class="sxs-lookup"><span data-stu-id="2a231-135">Only one H1 per document</span></span>
- <span data-ttu-id="2a231-136">Koptekst niveaus moeten met één worden verhoogd.</span><span class="sxs-lookup"><span data-stu-id="2a231-136">Header levels should increment by one.</span></span> <span data-ttu-id="2a231-137">Geen niveaus overs Laan</span><span class="sxs-lookup"><span data-stu-id="2a231-137">Do not skip levels</span></span>
- <span data-ttu-id="2a231-138">Geen vette of andere opmaak gebruiken in kopteksten</span><span class="sxs-lookup"><span data-stu-id="2a231-138">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="2a231-139">Regel lengte beperken tot 100 tekens</span><span class="sxs-lookup"><span data-stu-id="2a231-139">Limit line length to 100 characters</span></span>

<span data-ttu-id="2a231-140">Dit geldt voor conceptuele artikelen en cmdlet-verwijzingen.</span><span class="sxs-lookup"><span data-stu-id="2a231-140">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="2a231-141">About_topics is beperkt tot 80 tekens.</span><span class="sxs-lookup"><span data-stu-id="2a231-141">About_topics are limited to 80 characters.</span></span>
<span data-ttu-id="2a231-142">Als u de lijn lengte beperkt, wordt de Lees baarheid van Git-verschillen en-geschiedenis verbeterd.</span><span class="sxs-lookup"><span data-stu-id="2a231-142">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="2a231-143">Het maakt het ook gemakkelijker voor andere schrijvers om bijdragen te maken.</span><span class="sxs-lookup"><span data-stu-id="2a231-143">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="2a231-144">Gebruik de [uitprijs][reflow] uitbreiding opnieuw plaatsen in Visual Studio code om alinea's eenvoudig opnieuw te plaatsen zodat deze overeenkomen met de voorgeschreven regel lengte.</span><span class="sxs-lookup"><span data-stu-id="2a231-144">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

### <a name="lists"></a><span data-ttu-id="2a231-145">Lijsten</span><span class="sxs-lookup"><span data-stu-id="2a231-145">Lists</span></span>

<span data-ttu-id="2a231-146">Als uw lijst meerdere zinnen of alinea's bevat, kunt u overwegen om een koptekst op subniveau te gebruiken in plaats van een lijst.</span><span class="sxs-lookup"><span data-stu-id="2a231-146">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="2a231-147">De lijst moet tussen één lege regel worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="2a231-147">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="2a231-148">Niet-geordende lijsten</span><span class="sxs-lookup"><span data-stu-id="2a231-148">Unordered lists</span></span>

<span data-ttu-id="2a231-149">Beëindig geen lijst items met een punt, tenzij deze meerdere zinnen bevatten.</span><span class="sxs-lookup"><span data-stu-id="2a231-149">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="2a231-150">Gebruik het afbreek streepje (`-`) voor opsommings tekens in lijst items.</span><span class="sxs-lookup"><span data-stu-id="2a231-150">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="2a231-151">Dit voor komt Verwar ring met vette of cursieve markeringen die gebruikmaken van het sterretje [`*`].</span><span class="sxs-lookup"><span data-stu-id="2a231-151">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="2a231-152">Als u een alinea of andere elementen onder een item met opsommings tekens wilt opnemen, voegt u een regel-en inspringing in met het eerste teken achter het bullet.</span><span class="sxs-lookup"><span data-stu-id="2a231-152">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="2a231-153">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-153">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="2a231-154">Dit is een lijst met subelementen onder een item met opsommings tekens.</span><span class="sxs-lookup"><span data-stu-id="2a231-154">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="2a231-155">Eerste item in opsommings teken</span><span class="sxs-lookup"><span data-stu-id="2a231-155">First bullet item</span></span>

  <span data-ttu-id="2a231-156">Zin waarin het eerste opsommings teken wordt uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="2a231-156">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="2a231-157">Item in subopsommingsteken</span><span class="sxs-lookup"><span data-stu-id="2a231-157">Sub-bullet item</span></span>

    <span data-ttu-id="2a231-158">Zin waarin het subopsommingsteken wordt uitgelegd.</span><span class="sxs-lookup"><span data-stu-id="2a231-158">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="2a231-159">Tweede item voor opsommings teken</span><span class="sxs-lookup"><span data-stu-id="2a231-159">Second bullet item</span></span>
- <span data-ttu-id="2a231-160">Derde item voor opsommings teken</span><span class="sxs-lookup"><span data-stu-id="2a231-160">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="2a231-161">Geordende lijsten</span><span class="sxs-lookup"><span data-stu-id="2a231-161">Ordered lists</span></span>

<span data-ttu-id="2a231-162">Als u een alinea of andere elementen onder een genummerd item wilt toevoegen, moet u de inspringing uitlijnen met het eerste teken na het item nummer.</span><span class="sxs-lookup"><span data-stu-id="2a231-162">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="2a231-163">Alle items in een genummerde lijst moeten het getal `1.` gebruiken in plaats van elk item te verhogen.</span><span class="sxs-lookup"><span data-stu-id="2a231-163">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="2a231-164">Bij het weer geven van de prijs verlaging wordt de waarde automatisch verhoogd.</span><span class="sxs-lookup"><span data-stu-id="2a231-164">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="2a231-165">Dit maakt het gemakkelijker om items opnieuw in te delen en de inspringing van onderliggende inhoud te standaardiseren.</span><span class="sxs-lookup"><span data-stu-id="2a231-165">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="2a231-166">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-166">For example:</span></span>

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

<span data-ttu-id="2a231-167">De resulterende prijs verlaging wordt als volgt weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="2a231-167">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="2a231-168">Voeg voor het eerste element één spatie toe na de 1.</span><span class="sxs-lookup"><span data-stu-id="2a231-168">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="2a231-169">Lange zinnen moeten worden verpakt naar de volgende regel en moeten worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.</span><span class="sxs-lookup"><span data-stu-id="2a231-169">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="2a231-170">Als u een tweede element (zoals deze) wilt opnemen, voegt u een regel afbreek na de eerste en inspringing in.</span><span class="sxs-lookup"><span data-stu-id="2a231-170">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="2a231-171">De inspringing van het tweede element moet worden uitgelijnd met het eerste teken na de markering van de genummerde lijst.</span><span class="sxs-lookup"><span data-stu-id="2a231-171">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="2a231-172">Voor items met één cijfer, zoals deze, inspringen naar kolom 4.</span><span class="sxs-lookup"><span data-stu-id="2a231-172">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="2a231-173">Voor items met dubbele cijfers, bijvoorbeeld item nummer 10, inspringen naar kolom 5.</span><span class="sxs-lookup"><span data-stu-id="2a231-173">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="2a231-174">Het volgende genummerde item wordt hier gestart.</span><span class="sxs-lookup"><span data-stu-id="2a231-174">The next numbered item starts here.</span></span>

### <a name="formatting-command-syntax-elements"></a><span data-ttu-id="2a231-175">Opmaak van opdracht syntaxis elementen</span><span class="sxs-lookup"><span data-stu-id="2a231-175">Formatting command syntax elements</span></span>

- <span data-ttu-id="2a231-176">Gebruik altijd de volledige naam voor cmdlets en para meters.</span><span class="sxs-lookup"><span data-stu-id="2a231-176">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="2a231-177">Vermijd het gebruik van aliassen tenzij u de alias expliciet demonstreert.</span><span class="sxs-lookup"><span data-stu-id="2a231-177">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="2a231-178">In een alinea moeten tref woorden, namen van cmdlets, variabelen en bestands paden worden verpakt in apostroffen-tekens (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="2a231-178">Within a paragraph, language keywords, cmdlet names, variables, and file paths should be wrapped in backtick (`` ` ``) characters.</span></span> <span data-ttu-id="2a231-179">Eigenschaps-, para meter-en klassen namen moeten **vet**zijn.</span><span class="sxs-lookup"><span data-stu-id="2a231-179">Property, parameter, and class names should be **bold**.</span></span>

  <span data-ttu-id="2a231-180">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-180">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- <span data-ttu-id="2a231-181">Wanneer u verwijst naar een para meter op naam, moet de naam **vet**zijn.</span><span class="sxs-lookup"><span data-stu-id="2a231-181">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="2a231-182">Bij het illustreren van het gebruik van een para meter met het voor voegsel hyphen moet de para meter worden ingepakt in accents graves.</span><span class="sxs-lookup"><span data-stu-id="2a231-182">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="2a231-183">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-183">For example:</span></span>

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- <span data-ttu-id="2a231-184">Bij het verwijzen naar externe opdrachten (exe, scripts, enzovoort) moet de naam van de opdracht vet, alle kleine letters (of een hoofd letter als aan het begin van een zin) worden weer gegeven en de juiste bestands extensie bevatten.</span><span class="sxs-lookup"><span data-stu-id="2a231-184">When referring to external commands (EXEs, scripts, etc.), the command name should be bold, all lowercase (or capitalized if at the beginning of a sentence), and include the appropriate file extension.</span></span> <span data-ttu-id="2a231-185">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-185">For example:</span></span>

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- <span data-ttu-id="2a231-186">Wanneer het voor beeld-gebruik van een externe opdracht wordt weer gegeven, moet het voor beeld worden verpakt in accents graves.</span><span class="sxs-lookup"><span data-stu-id="2a231-186">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
  <span data-ttu-id="2a231-187">Wanneer er een naam conflict is met een alias, moet u de bestands extensie in het opdracht voorbeeld toevoegen.</span><span class="sxs-lookup"><span data-stu-id="2a231-187">When there is a name collisions with an alias you must include the file extension in the command example.</span></span> <span data-ttu-id="2a231-188">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-188">For example:</span></span>

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- <span data-ttu-id="2a231-189">Bij het schrijven van een conceptueel artikel (in plaats van referentie-inhoud) moet het eerste exemplaar van een naam van een cmdlet worden gelinkt naar de cmdlet-documentatie.</span><span class="sxs-lookup"><span data-stu-id="2a231-189">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="2a231-190">Gebruik geen accents graves, vet of andere opmaak binnen de haakjes van een Hyper link.</span><span class="sxs-lookup"><span data-stu-id="2a231-190">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="2a231-191">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-191">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="2a231-192">Zie de sectie [hyper links](#hyperlinks) in dit artikel voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2a231-192">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

### <a name="images"></a><span data-ttu-id="2a231-193">Installatiekopieën</span><span class="sxs-lookup"><span data-stu-id="2a231-193">Images</span></span>

<span data-ttu-id="2a231-194">De syntaxis voor het insluiten van een afbeelding is:</span><span class="sxs-lookup"><span data-stu-id="2a231-194">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="2a231-195">Waarbij `alt text` een korte beschrijving van de installatie kopie is en `<folder path>` een relatief pad naar de afbeelding is.</span><span class="sxs-lookup"><span data-stu-id="2a231-195">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="2a231-196">Alternatieve tekst is vereist voor scherm lezers voor visueel gehandicapten.</span><span class="sxs-lookup"><span data-stu-id="2a231-196">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="2a231-197">Het is ook handig als er een site fout is waar de installatie kopie niet kan worden gerenderd.</span><span class="sxs-lookup"><span data-stu-id="2a231-197">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="2a231-198">Afbeeldingen moeten worden opgeslagen in een `media/<article-name>` map in de map waarin het artikel zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="2a231-198">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="2a231-199">Afbeeldingen mogen niet tussen artikelen worden gedeeld.</span><span class="sxs-lookup"><span data-stu-id="2a231-199">Images should not be shared between articles.</span></span> <span data-ttu-id="2a231-200">Maak een map die overeenkomt met de bestands naam van uw artikel in de map `media`.</span><span class="sxs-lookup"><span data-stu-id="2a231-200">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="2a231-201">Kopieer de installatie kopieën voor dat artikel naar de nieuwe map.</span><span class="sxs-lookup"><span data-stu-id="2a231-201">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="2a231-202">Als een installatie kopie wordt gebruikt door meerdere artikelen, moet elke map met de installatie kopie een kopie van het afbeeldings bestand bevatten.</span><span class="sxs-lookup"><span data-stu-id="2a231-202">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="2a231-203">In deze praktijk wordt voor komen dat een afbeelding wordt gewijzigd in een ander artikel.</span><span class="sxs-lookup"><span data-stu-id="2a231-203">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="2a231-204">De volgende afbeeldings bestands typen worden ondersteund: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span><span class="sxs-lookup"><span data-stu-id="2a231-204">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="2a231-205">Uitprijs uitbreidingen ondersteund door open Publishing</span><span class="sxs-lookup"><span data-stu-id="2a231-205">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="2a231-206">Het [Microsoft docs authoring Pack](/contribute/how-to-write-docs-auth-pack) bevat hulpprogram ma's die ondersteuning bieden voor functies die uniek zijn voor het publicatie systeem.</span><span class="sxs-lookup"><span data-stu-id="2a231-206">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="2a231-207">Waarschuwingen zijn een uitstel extensie voor het maken van blok citaten die op docs.microsoft.com worden weer gegeven met kleuren en pictogrammen die de betekenis van de inhoud aangeven.</span><span class="sxs-lookup"><span data-stu-id="2a231-207">Alerts are a Markdown extension to create block quotes that render on docs.microsoft.com with colors and icons that indicate the significance of the content.</span></span> <span data-ttu-id="2a231-208">De volgende waarschuwings typen worden ondersteund:</span><span class="sxs-lookup"><span data-stu-id="2a231-208">The following alert types are supported:</span></span>

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

<span data-ttu-id="2a231-209">Deze waarschuwingen zien er als volgt uit op docs.microsoft.com:</span><span class="sxs-lookup"><span data-stu-id="2a231-209">These alerts look like this on docs.microsoft.com:</span></span>

> [!NOTE]
> <span data-ttu-id="2a231-210">De informatie die de gebruiker moet opmerken, zelfs bij het onderhouden.</span><span class="sxs-lookup"><span data-stu-id="2a231-210">Information the user should notice even if skimming.</span></span>

> [!TIP]
> <span data-ttu-id="2a231-211">Optionele informatie voor een succes volle gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2a231-211">Optional information to help a user be more successful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a231-212">Essentiële informatie die nodig is voor het slagen van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="2a231-212">Essential information required for user success.</span></span>

> [!CAUTION]
> <span data-ttu-id="2a231-213">Negatieve mogelijke gevolgen van een actie.</span><span class="sxs-lookup"><span data-stu-id="2a231-213">Negative potential consequences of an action.</span></span>

> [!WARNING]
> <span data-ttu-id="2a231-214">Gevaarlijke bepaalde gevolgen van een actie.</span><span class="sxs-lookup"><span data-stu-id="2a231-214">Dangerous certain consequences of an action.</span></span>

## <a name="hyperlinks"></a><span data-ttu-id="2a231-215">Link</span><span class="sxs-lookup"><span data-stu-id="2a231-215">Hyperlinks</span></span>

- <span data-ttu-id="2a231-216">Vermijd het gebruik van bare Url's.</span><span class="sxs-lookup"><span data-stu-id="2a231-216">Avoid using bare URLs.</span></span> <span data-ttu-id="2a231-217">Links moeten de syntaxis van de prijs verlaging gebruiken `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="2a231-217">Links should use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="2a231-218">Bare Url's kunnen worden gebruikt wanneer dit nodig is, maar moeten worden inge sloten in accents graves.</span><span class="sxs-lookup"><span data-stu-id="2a231-218">Bare URLs may be used when necessary, but should be enclosed in backticks.</span></span> <span data-ttu-id="2a231-219">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-219">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- <span data-ttu-id="2a231-220">URL-koppelingen moeten indien mogelijk HTTPS zijn.</span><span class="sxs-lookup"><span data-stu-id="2a231-220">URL links should be HTTPS when possible.</span></span>
- <span data-ttu-id="2a231-221">Koppelingen moeten een beschrijvende naam hebben, meestal de titel van het gekoppelde onderwerp</span><span class="sxs-lookup"><span data-stu-id="2a231-221">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="2a231-222">Voor alle items in de sectie ' Verwante koppelingen ' aan de onderkant moet een Hyper link worden weer.</span><span class="sxs-lookup"><span data-stu-id="2a231-222">All items in the "related links" section at the bottom should be hyperlinked.</span></span>
- <span data-ttu-id="2a231-223">Gebruik geen accents graves, vet of andere opmaak binnen de haakjes van een Hyper link.</span><span class="sxs-lookup"><span data-stu-id="2a231-223">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

### <a name="linking-to-other-content"></a><span data-ttu-id="2a231-224">Koppeling naar andere inhoud</span><span class="sxs-lookup"><span data-stu-id="2a231-224">Linking to other content</span></span>

<span data-ttu-id="2a231-225">Er zijn twee typen hyper links die worden ondersteund door het publicatie systeem: Url's en bestands koppelingen.</span><span class="sxs-lookup"><span data-stu-id="2a231-225">There are two types of hyperlinks supported by the publishing system: URLs and file links.</span></span>

<span data-ttu-id="2a231-226">Een URL-koppeling kan een URL-pad zijn dat relatief is ten opzichte van de hoofdmap van docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="2a231-226">A URL link can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="2a231-227">Of een absolute URL die de syntaxis van de volledige URL bevat.</span><span class="sxs-lookup"><span data-stu-id="2a231-227">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="2a231-228">(Bijvoorbeeld: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span><span class="sxs-lookup"><span data-stu-id="2a231-228">(For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span></span>

- <span data-ttu-id="2a231-229">Gebruik URL-koppelingen wanneer u een koppeling maakt naar inhoud buiten Power shell-docs of tussen Naslag informatie over de cmdlet en conceptuele artikelen in Power shell-docs.</span><span class="sxs-lookup"><span data-stu-id="2a231-229">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs.</span></span>
- <span data-ttu-id="2a231-230">De eenvoudigste manier om een relatieve koppeling te maken, is door de URL te kopiëren uit uw browser en vervolgens `https://docs.microsoft.com/en-us` te verwijderen van de waarde die u in de prijs van de geplakte hebt geplakt.</span><span class="sxs-lookup"><span data-stu-id="2a231-230">The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
   - <span data-ttu-id="2a231-231">Land instellingen niet opnemen in Url's op Eigenschappen van micro soft (bijv.</span><span class="sxs-lookup"><span data-stu-id="2a231-231">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="2a231-232">/en-US verwijderen uit de URL).</span><span class="sxs-lookup"><span data-stu-id="2a231-232">remove "/en-us" from URL).</span></span>
- <span data-ttu-id="2a231-233">Alle Url's naar externe websites moeten HTTPS gebruiken, tenzij dat niet geldig is voor de doel site.</span><span class="sxs-lookup"><span data-stu-id="2a231-233">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="2a231-234">Een koppeling naar een bestand wordt gebruikt om te koppelen van het ene referentie artikel naar het andere of van het ene conceptuele artikel naar het andere.</span><span class="sxs-lookup"><span data-stu-id="2a231-234">A file link is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="2a231-235">Als u een koppeling moet maken naar een referentie artikel voor een specifieke versie van Power shell, moet u een URL-koppeling gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2a231-235">If you need to link to a reference article for a specific version of PowerShell, then you need to use a URL link.</span></span>

- <span data-ttu-id="2a231-236">Bestands koppelingen bevatten een relatief bestandspad (bijvoorbeeld: `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="2a231-236">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="2a231-237">Alle bestands paden gebruiken tekens voor voorwaartse slash (`/`)</span><span class="sxs-lookup"><span data-stu-id="2a231-237">All file paths use forward-slash (`/`) characters</span></span>

## <a name="formatting-code-samples"></a><span data-ttu-id="2a231-238">Code voorbeelden opmaken</span><span class="sxs-lookup"><span data-stu-id="2a231-238">Formatting code samples</span></span>

<span data-ttu-id="2a231-239">Prijs verlaging ondersteunt twee verschillende code stijlen:</span><span class="sxs-lookup"><span data-stu-id="2a231-239">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="2a231-240">Code reeksen (inline): gemarkeerd met een enkel apostroffen-teken (`` ` ``).</span><span class="sxs-lookup"><span data-stu-id="2a231-240">Code spans (inline) - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="2a231-241">Wordt gebruikt in een alinea in plaats van als een zelfstandig blok.</span><span class="sxs-lookup"><span data-stu-id="2a231-241">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="2a231-242">Code blokken: een blok met meerdere regels dat is omgeven door Triple-apostroffen (`` ``` ``) teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="2a231-242">Code blocks - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="2a231-243">Code blokken kunnen ook een taal label volgen volgens het accents graves.</span><span class="sxs-lookup"><span data-stu-id="2a231-243">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="2a231-244">Het taal label schakelt syntaxis markering in voor de inhoud van het code blok.</span><span class="sxs-lookup"><span data-stu-id="2a231-244">The language label enables syntax highlighting for the contents of the code block.</span></span>

### <a name="using-code-blocks"></a><span data-ttu-id="2a231-245">Code blokken gebruiken</span><span class="sxs-lookup"><span data-stu-id="2a231-245">Using code blocks</span></span>

<span data-ttu-id="2a231-246">Met prijs verlaging kunt u inspringen om een code blok aan te duiden, maar dit patroon kan problematisch zijn en moet worden vermeden.</span><span class="sxs-lookup"><span data-stu-id="2a231-246">Markdown allows for indentation to signify a code block, but this pattern can be problematic and should be avoided.</span></span> <span data-ttu-id="2a231-247">Alle code blokken moeten zich in een code Fence bevinden.</span><span class="sxs-lookup"><span data-stu-id="2a231-247">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="2a231-248">Een code Fence is een code blok dat is omgeven door Triple-apostroffen (`` ``` ``) teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="2a231-248">A code fence is a block of code surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="2a231-249">De markeringen voor de code omheining moeten zich op hun eigen regel vóór en na het code voorbeeld bevindt.</span><span class="sxs-lookup"><span data-stu-id="2a231-249">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="2a231-250">De markering aan het begin van het code blok heeft mogelijk een optioneel taal label.</span><span class="sxs-lookup"><span data-stu-id="2a231-250">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="2a231-251">Het open Publishing System (OPS) van micro soft gebruikt het taal label voor de ondersteuning van de functie voor het markeren van syntaxis.</span><span class="sxs-lookup"><span data-stu-id="2a231-251">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="2a231-252">Met OPS wordt ook een **Kopieer** knop toegevoegd waarmee de inhoud van het code blok naar het klem bord wordt gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="2a231-252">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="2a231-253">Zo kunt u de code snel in een script plakken om het code voorbeeld te testen.</span><span class="sxs-lookup"><span data-stu-id="2a231-253">This allows you to quickly paste the code into a script for testing the code example.</span></span> <span data-ttu-id="2a231-254">Niet alle voor beelden in onze documentatie zijn echter bedoeld om te worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2a231-254">However, not all examples in our documentation are intended to be run.</span></span> <span data-ttu-id="2a231-255">Sommige code blokken zijn eenvoudige illustraties van een Power shell-concept.</span><span class="sxs-lookup"><span data-stu-id="2a231-255">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="2a231-256">Er zijn twee typen code blokken die in onze documentatie worden gebruikt:</span><span class="sxs-lookup"><span data-stu-id="2a231-256">There are two types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="2a231-257">Voor beelden van illustreren</span><span class="sxs-lookup"><span data-stu-id="2a231-257">Illustrative examples</span></span>
2. <span data-ttu-id="2a231-258">Uitvoer bare voor beelden</span><span class="sxs-lookup"><span data-stu-id="2a231-258">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="2a231-259">Syntaxis code blokken</span><span class="sxs-lookup"><span data-stu-id="2a231-259">Syntax code blocks</span></span>

<span data-ttu-id="2a231-260">In dit voor beeld ziet u alle mogelijke para meters van de cmdlet `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="2a231-260">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="2a231-261">In dit voor beeld wordt de `for` instructie in algemene termen beschreven:</span><span class="sxs-lookup"><span data-stu-id="2a231-261">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="2a231-262">Voor beelden van illustreren</span><span class="sxs-lookup"><span data-stu-id="2a231-262">Illustrative examples</span></span>

<span data-ttu-id="2a231-263">Voor beelden van illustreren een Power shell-concept.</span><span class="sxs-lookup"><span data-stu-id="2a231-263">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="2a231-264">Ze zijn niet bedoeld om te worden gekopieerd naar het klem bord voor uitvoering.</span><span class="sxs-lookup"><span data-stu-id="2a231-264">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="2a231-265">Deze worden meestal gebruikt voor eenvoudige voor beelden die eenvoudig kunnen worden getypt.</span><span class="sxs-lookup"><span data-stu-id="2a231-265">These are most commonly used for simple examples that are easy to type.</span></span>
<span data-ttu-id="2a231-266">Ze worden ook gebruikt voor syntaxis voorbeelden waarbij u de syntaxis van een opdracht illustreert.</span><span class="sxs-lookup"><span data-stu-id="2a231-266">They are also used for syntax examples where you are illustrating the syntax of a command.</span></span> <span data-ttu-id="2a231-267">Het code blok bevat mogelijk voorbeeld uitvoer van de opdracht die wordt geïllustreerd.</span><span class="sxs-lookup"><span data-stu-id="2a231-267">The code block may contain example output from the command being illustrated.</span></span>

<span data-ttu-id="2a231-268">Hier volgt een eenvoudig voor beeld van het illustreren van een Power shell-vergelijkings operator:</span><span class="sxs-lookup"><span data-stu-id="2a231-268">Here is a simple example illustrating a PowerShell comparison operators:</span></span>

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

<span data-ttu-id="2a231-269">Houd er rekening mee dat in dit voor beeld de vereenvoudigde Power shell-prompt wordt weer gegeven en de resulterende uitvoer.</span><span class="sxs-lookup"><span data-stu-id="2a231-269">Note that this example has the simplified PowerShell prompt and shows the resulting output.</span></span> <span data-ttu-id="2a231-270">In dit geval is de lezer niet van plan om dit voor beeld te kopiëren en uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="2a231-270">In this case, we don't intend the reader to copy and run this example.</span></span>

### <a name="executable-examples"></a><span data-ttu-id="2a231-271">Uitvoer bare voor beelden</span><span class="sxs-lookup"><span data-stu-id="2a231-271">Executable examples</span></span>

<span data-ttu-id="2a231-272">Complexere voor beelden of voor beelden die bedoeld zijn om te kopiëren en uit te voeren, moeten de volgende opmaak voor blok stijl gebruiken:</span><span class="sxs-lookup"><span data-stu-id="2a231-272">More complex examples or examples that are intended to be useful to copy and execute should use the following block-style markup:</span></span>

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

<span data-ttu-id="2a231-273">De uitvoer die door Power shell-opdrachten wordt weer gegeven, moet worden inge sloten in een **uitvoer** code blok om te voor komen dat de syntaxis wordt gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="2a231-273">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="2a231-274">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2a231-274">For example:</span></span>

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

<span data-ttu-id="2a231-275">Het code label van de **uitvoer** is geen officiële taal die wordt ondersteund door het markerings systeem van de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="2a231-275">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="2a231-276">Dit label is echter nuttig omdat OPS het label "uitvoer" toevoegt aan het frame van de code op de webpagina.</span><span class="sxs-lookup"><span data-stu-id="2a231-276">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="2a231-277">Het vak uitvoer code heeft geen syntaxis markering.</span><span class="sxs-lookup"><span data-stu-id="2a231-277">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="2a231-278">Coderings stijl regels</span><span class="sxs-lookup"><span data-stu-id="2a231-278">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="2a231-279">Regel voortzetting in code voorbeelden voor komen</span><span class="sxs-lookup"><span data-stu-id="2a231-279">Avoid line continuation in code samples</span></span>

<span data-ttu-id="2a231-280">Vermijd het gebruik van regel voortzettings tekens (`` ` ``) in voor beelden van Power shell-code.</span><span class="sxs-lookup"><span data-stu-id="2a231-280">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="2a231-281">Deze zijn moeilijk te zien en kunnen problemen veroorzaken als er extra spaties aan het einde van de regel staan.</span><span class="sxs-lookup"><span data-stu-id="2a231-281">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="2a231-282">Gebruik Power shell splatting om de regel lengte te verminderen voor cmdlets die veel para meters hebben.</span><span class="sxs-lookup"><span data-stu-id="2a231-282">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="2a231-283">Profiteer van de natuurlijke lijn grens mogelijkheden van Power shell, zoals na het sluis teken (`|`), accolades, haakjes en haakjes.</span><span class="sxs-lookup"><span data-stu-id="2a231-283">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="2a231-284">Vermijd het gebruik van Power shell-prompts in voor beelden</span><span class="sxs-lookup"><span data-stu-id="2a231-284">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="2a231-285">Het gebruik van de prompt teken reeks wordt afgeraden en moet worden beperkt tot scenario's die bedoeld zijn om het gebruik van de opdracht regel te illustreren.</span><span class="sxs-lookup"><span data-stu-id="2a231-285">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="2a231-286">Voor de meeste van deze voor beelden moet de prompt teken reeks `PS>`zijn.</span><span class="sxs-lookup"><span data-stu-id="2a231-286">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="2a231-287">Deze vraag is onafhankelijk van specifieke indica toren voor het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="2a231-287">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="2a231-288">Prompts zijn vereist voor voor beelden van opdrachten voor het wijzigen van de prompt of wanneer het weer gegeven pad belang rijk is voor het scenario dat wordt geïllustreerd.</span><span class="sxs-lookup"><span data-stu-id="2a231-288">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="2a231-289">In het volgende voor beeld ziet u hoe de prompt verandert wanneer u de register provider gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2a231-289">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="2a231-290">Gebruik geen aliassen in voor beelden</span><span class="sxs-lookup"><span data-stu-id="2a231-290">Do not use aliases in examples</span></span>

<span data-ttu-id="2a231-291">U moet altijd de volledige naam van alle cmdlets en para meters gebruiken, tenzij u specifiek op de alias spreekt.</span><span class="sxs-lookup"><span data-stu-id="2a231-291">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="2a231-292">De namen van cmdlets en para meters moeten de juiste spelling gebruiken die in de code is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2a231-292">Cmdlet and parameter names must use the proper spelling defined in the code.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="2a231-293">Para meters in voor beelden gebruiken</span><span class="sxs-lookup"><span data-stu-id="2a231-293">Using parameters in examples</span></span>

<span data-ttu-id="2a231-294">Vermijd het gebruik van positionele para meters.</span><span class="sxs-lookup"><span data-stu-id="2a231-294">Avoid using positional parameters.</span></span> <span data-ttu-id="2a231-295">Over het algemeen moet u altijd de parameter naam in een voor beeld meenemen, zelfs als de para meter positioneel is.</span><span class="sxs-lookup"><span data-stu-id="2a231-295">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="2a231-296">Dit verkleint de kans op Verwar ring in uw voor beelden.</span><span class="sxs-lookup"><span data-stu-id="2a231-296">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2a231-297">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="2a231-297">Next steps</span></span>

[<span data-ttu-id="2a231-298">Naslag informatie voor het bewerken van cmdlets</span><span class="sxs-lookup"><span data-stu-id="2a231-298">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
