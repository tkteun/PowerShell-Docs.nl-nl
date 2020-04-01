---
title: Verwijzings artikelen bewerken
description: In dit artikel worden de specifieke vereisten beschreven voor het bewerken van cmdlet-verwijzingen en over onderwerpen in de Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3aed1c14429310c57681397d4877a3a6f48400fd
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500982"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="a1c77-103">Verwijzings artikelen bewerken</span><span class="sxs-lookup"><span data-stu-id="a1c77-103">Editing reference articles</span></span>

<span data-ttu-id="a1c77-104">De cmdlet-referentie artikelen hebben een specifieke structuur.</span><span class="sxs-lookup"><span data-stu-id="a1c77-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="a1c77-105">Deze structuur wordt gedefinieerd door [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="a1c77-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="a1c77-106">PlatyPS genereert de cmdlet-Help voor Power shell-modules in korting.</span><span class="sxs-lookup"><span data-stu-id="a1c77-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="a1c77-107">Nadat de bestanden voor de verlaging zijn bewerkt, wordt PlatyPS gebruikt om de MAML-Help bestanden te maken die worden gebruikt door de `Get-Help`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1c77-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="a1c77-108">PlatyPS heeft een in code vastgelegd schema voor cmdlet-verwijzingen die in de code zijn geschreven.</span><span class="sxs-lookup"><span data-stu-id="a1c77-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="a1c77-109">Het [platyPS.schema.MD][] -document probeert deze structuur te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="a1c77-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="a1c77-110">Schema schendingen veroorzaken compilatie fouten die moeten worden opgelost voordat we uw bijdrage kunnen accepteren.</span><span class="sxs-lookup"><span data-stu-id="a1c77-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="a1c77-111">Algemene richtlijnen</span><span class="sxs-lookup"><span data-stu-id="a1c77-111">General guidelines</span></span>

- <span data-ttu-id="a1c77-112">Verwijder geen koptekst structuren.</span><span class="sxs-lookup"><span data-stu-id="a1c77-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="a1c77-113">PlatyPS verwacht een specifieke set kopteksten.</span><span class="sxs-lookup"><span data-stu-id="a1c77-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="a1c77-114">Het **invoer type** en de headers van het **uitvoer type** moeten een type hebben.</span><span class="sxs-lookup"><span data-stu-id="a1c77-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="a1c77-115">Als de cmdlet geen invoer heeft of een waarde retourneert, gebruikt u de waarde `None`.</span><span class="sxs-lookup"><span data-stu-id="a1c77-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="a1c77-116">Geomheiningde code blokken zijn alleen toegestaan in de sectie [voor beelden](#structuring-examples) .</span><span class="sxs-lookup"><span data-stu-id="a1c77-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="a1c77-117">Inline code reeksen kunnen worden gebruikt in een wille keurige alinea.</span><span class="sxs-lookup"><span data-stu-id="a1c77-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="a1c77-118">About_ bestanden Format teren</span><span class="sxs-lookup"><span data-stu-id="a1c77-118">Formatting About_ files</span></span>

<span data-ttu-id="a1c77-119">`About_*`-bestanden worden nu verwerkt door [pandoc][]in plaats van PlatyPS.</span><span class="sxs-lookup"><span data-stu-id="a1c77-119">`About_*` files are now processed by [Pandoc][], instead of PlatyPS.</span></span> <span data-ttu-id="a1c77-120">`About_*` bestanden zijn ingedeeld voor de beste compatibiliteit tussen alle versies van Power shell en met de hulpprogram ma's voor publiceren.</span><span class="sxs-lookup"><span data-stu-id="a1c77-120">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="a1c77-121">Richt lijnen voor basis opmaak:</span><span class="sxs-lookup"><span data-stu-id="a1c77-121">Basic formatting guidelines:</span></span>

- <span data-ttu-id="a1c77-122">Regels beperken tot 80 tekens</span><span class="sxs-lookup"><span data-stu-id="a1c77-122">Limit lines to 80 characters</span></span>
- <span data-ttu-id="a1c77-123">Code blokken en tabellen zijn beperkt tot 76 tekens omdat pandoc deze met vier spaties inspringt tijdens de conversie naar tekst zonder opmaak</span><span class="sxs-lookup"><span data-stu-id="a1c77-123">Code blocks and tables are limited to 76 characters because Pandoc indents these by four spaces during conversion to plain text</span></span>
- <span data-ttu-id="a1c77-124">Tabellen moeten binnen 76 tekens passen</span><span class="sxs-lookup"><span data-stu-id="a1c77-124">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="a1c77-125">Hand matig inhoud van cellen op meerdere regels laten teruglopen</span><span class="sxs-lookup"><span data-stu-id="a1c77-125">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="a1c77-126">`|` tekens openen en sluiten op elke regel gebruiken</span><span class="sxs-lookup"><span data-stu-id="a1c77-126">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="a1c77-127">Een werk voorbeeld in [about_Comparison_Operators][about-example] weer geven</span><span class="sxs-lookup"><span data-stu-id="a1c77-127">See a working example in [about_Comparison_Operators][about-example]</span></span>
- <span data-ttu-id="a1c77-128">Pandoc speciale tekens gebruiken `\`,`$`en `<`</span><span class="sxs-lookup"><span data-stu-id="a1c77-128">Using Pandoc special characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="a1c77-129">In een koptekst-deze tekens moeten worden voorafgegaan door een voorloop `\` teken of worden inge sloten in accents graves (`` ` ``)</span><span class="sxs-lookup"><span data-stu-id="a1c77-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in backticks (`` ` ``)</span></span>
  - <span data-ttu-id="a1c77-130">In een alinea moeten deze tekens in code reeksen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="a1c77-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="a1c77-131">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a1c77-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a><span data-ttu-id="a1c77-132">Voor beelden van structureren</span><span class="sxs-lookup"><span data-stu-id="a1c77-132">Structuring examples</span></span>

<span data-ttu-id="a1c77-133">In het PlatyPS-schema is de **voor** beeld-header een H2-kop en elk voor beeld is een H3-header.</span><span class="sxs-lookup"><span data-stu-id="a1c77-133">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="a1c77-134">Binnen een voor beeld staat het schema niet toe dat code blokken worden gescheiden door alinea's.</span><span class="sxs-lookup"><span data-stu-id="a1c77-134">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="a1c77-135">Het ondersteunde schema is:</span><span class="sxs-lookup"><span data-stu-id="a1c77-135">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="a1c77-136">Nummer elk voor beeld en voeg een korte titel toe.</span><span class="sxs-lookup"><span data-stu-id="a1c77-136">Number each example and add a brief title.</span></span>

<span data-ttu-id="a1c77-137">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a1c77-137">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="a1c77-138">Voor beeld 1: cmdlets, functies en aliassen ophalen</span><span class="sxs-lookup"><span data-stu-id="a1c77-138">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="a1c77-139">Met deze opdracht worden de Power shell-cmdlets, functies en aliassen opgehaald die op de computer zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a1c77-139">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="a1c77-140">Voor beeld 2: opdrachten in de huidige sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="a1c77-140">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="a1c77-141">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="a1c77-141">Next steps</span></span>

[<span data-ttu-id="a1c77-142">Controle lijst voor redactionele</span><span class="sxs-lookup"><span data-stu-id="a1c77-142">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
