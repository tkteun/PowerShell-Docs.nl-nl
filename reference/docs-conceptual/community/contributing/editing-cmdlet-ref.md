---
title: Verwijzings artikelen bewerken
description: In dit artikel worden de specifieke vereisten beschreven voor het bewerken van cmdlet-verwijzingen en over onderwerpen in de Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624768"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="1e870-103">Verwijzings artikelen bewerken</span><span class="sxs-lookup"><span data-stu-id="1e870-103">Editing reference articles</span></span>

<span data-ttu-id="1e870-104">Artikelen met naslaginformatie voor cmdlets hebben een specifieke structuur.</span><span class="sxs-lookup"><span data-stu-id="1e870-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="1e870-105">Deze structuur wordt gedefinieerd door [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="1e870-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="1e870-106">PlatyPS genereert de cmdlet-Help voor Power shell-modules in korting.</span><span class="sxs-lookup"><span data-stu-id="1e870-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="1e870-107">Nadat de Markdown-bestanden zijn bewerkt, wordt PlatyPS gebruikt om de MAML-helpbestanden te maken die door de `Get-Help`-cmdlet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e870-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="1e870-108">In PlatyPS is een in code vastgelegd schema voor cmdlet-naslaginformatie. Dit schema is in de code geschreven.</span><span class="sxs-lookup"><span data-stu-id="1e870-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="1e870-109">In het document [platyPS. schema.md][] is deze structuur beschreven.</span><span class="sxs-lookup"><span data-stu-id="1e870-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="1e870-110">Schendingen van het schema veroorzaken compilatiefouten die moeten worden opgelost voordat we uw bijdrage kunnen accepteren.</span><span class="sxs-lookup"><span data-stu-id="1e870-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="1e870-111">Algemene richtlijnen</span><span class="sxs-lookup"><span data-stu-id="1e870-111">General guidelines</span></span>

- <span data-ttu-id="1e870-112">Verwijder geen koptekststructuren.</span><span class="sxs-lookup"><span data-stu-id="1e870-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="1e870-113">PlatyPS verwacht een specifieke reeks kopteksten.</span><span class="sxs-lookup"><span data-stu-id="1e870-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="1e870-114">De kopteksten \*\*Inputtype \*\* en \*\*Outputtype \*\* moeten een type hebben.</span><span class="sxs-lookup"><span data-stu-id="1e870-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="1e870-115">Als de cmdlet geen invoer heeft of een waarde retourneert, gebruikt u de waarde `None`.</span><span class="sxs-lookup"><span data-stu-id="1e870-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="1e870-116">Afgebakende codeblokken zijn alleen toegestaan in de sectie [Voorbeelden](#structuring-examples).</span><span class="sxs-lookup"><span data-stu-id="1e870-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="1e870-117">In elke alinea kunnen inline codereeksen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1e870-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="1e870-118">About_-bestanden opmaken</span><span class="sxs-lookup"><span data-stu-id="1e870-118">Formatting About_ files</span></span>

<span data-ttu-id="1e870-119">`About_*`bestanden worden in korting geschreven, maar worden als tekst bestanden verzonden.</span><span class="sxs-lookup"><span data-stu-id="1e870-119">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="1e870-120">We gebruiken [pandoc][] om de prijs verlaging te converteren naar platte tekst.</span><span class="sxs-lookup"><span data-stu-id="1e870-120">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="1e870-121">`About_*`bestanden zijn ingedeeld voor de beste compatibiliteit tussen alle versies van Power shell en met de hulpprogram ma's voor publiceren.</span><span class="sxs-lookup"><span data-stu-id="1e870-121">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="1e870-122">Algemene richtlijnen voor het opmaken:</span><span class="sxs-lookup"><span data-stu-id="1e870-122">Basic formatting guidelines:</span></span>

- <span data-ttu-id="1e870-123">Regels beperken tot 80 tekens.</span><span class="sxs-lookup"><span data-stu-id="1e870-123">Limit lines to 80 characters.</span></span> <span data-ttu-id="1e870-124">Met pandoc worden enkele prijsverlagings blokken Inge sprongen zodat dit blok moet worden aangepast.</span><span class="sxs-lookup"><span data-stu-id="1e870-124">Pandoc indents some Markdown blocks so those block must be adjusted.</span></span>
  - <span data-ttu-id="1e870-125">Code blokken zijn beperkt tot 76 tekens</span><span class="sxs-lookup"><span data-stu-id="1e870-125">Code blocks are limited to 76 characters</span></span>
  - <span data-ttu-id="1e870-126">Tabellen zijn beperkt tot 76 tekens</span><span class="sxs-lookup"><span data-stu-id="1e870-126">Tables are limited 76 characters</span></span>
  - <span data-ttu-id="1e870-127">Block Quotes (en waarschuwingen) zijn beperkt tot 78 tekens</span><span class="sxs-lookup"><span data-stu-id="1e870-127">Blockquotes (and Alerts) are limited 78 characters</span></span>

- <span data-ttu-id="1e870-128">De speciale meta tekens `\`van pandoc gebruiken,`$`en`<`</span><span class="sxs-lookup"><span data-stu-id="1e870-128">Using Pandoc's special meta-characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="1e870-129">In een koptekst-deze tekens moeten worden voorafgegaan door een voorloop `\` teken of worden inge sloten in code reeksen met behulp`` ` ``van accents graves ()</span><span class="sxs-lookup"><span data-stu-id="1e870-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="1e870-130">In een alinea moeten deze tekens in code reeksen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="1e870-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="1e870-131">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e870-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="1e870-132">Tabellen moeten binnen 76 tekens passen</span><span class="sxs-lookup"><span data-stu-id="1e870-132">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="1e870-133">Laat inhoud van cellen die over meerdere regels valt handmatig teruglopen</span><span class="sxs-lookup"><span data-stu-id="1e870-133">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="1e870-134">Gebruik op elke regel `|`-tekens voor openen en sluiten</span><span class="sxs-lookup"><span data-stu-id="1e870-134">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="1e870-135">In het volgende voor beeld ziet u hoe u een tabel op een juiste manier kunt samen stellen die informatie bevat die op meerdere regels in een cel inloopt.</span><span class="sxs-lookup"><span data-stu-id="1e870-135">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

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
    > <span data-ttu-id="1e870-136">De limiet van 76 kolommen geldt alleen voor `About_*` onderwerpen.</span><span class="sxs-lookup"><span data-stu-id="1e870-136">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="1e870-137">U kunt brede kolommen gebruiken in conceptuele of cmdlet-referentie artikelen.</span><span class="sxs-lookup"><span data-stu-id="1e870-137">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="structuring-examples"></a><span data-ttu-id="1e870-138">Voor beelden van structureren</span><span class="sxs-lookup"><span data-stu-id="1e870-138">Structuring examples</span></span>

<span data-ttu-id="1e870-139">In het PlatyPS-schema is de koptekst **VOORBEELDEN** een H2-kop en elk voorbeeld een H3-koptekst.</span><span class="sxs-lookup"><span data-stu-id="1e870-139">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="1e870-140">Het schema staat binnen een voorbeeld niet toe dat codeblokken worden gescheiden door alinea’s.</span><span class="sxs-lookup"><span data-stu-id="1e870-140">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="1e870-141">Het ondersteunde schema is:</span><span class="sxs-lookup"><span data-stu-id="1e870-141">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="1e870-142">Geef elk voorbeeld een nummer en voeg een korte titel toe.</span><span class="sxs-lookup"><span data-stu-id="1e870-142">Number each example and add a brief title.</span></span>

<span data-ttu-id="1e870-143">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e870-143">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="1e870-144">Voor beeld 1: cmdlets, functies en aliassen ophalen</span><span class="sxs-lookup"><span data-stu-id="1e870-144">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="1e870-145">Met deze opdracht worden de Power shell-cmdlets, functies en aliassen opgehaald die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1e870-145">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="1e870-146">Voor beeld 2: opdrachten in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="1e870-146">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="1e870-147">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="1e870-147">Next steps</span></span>

[<span data-ttu-id="1e870-148">Redactionele controlelijst</span><span class="sxs-lookup"><span data-stu-id="1e870-148">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
