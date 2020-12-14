---
title: De manier waarop we problemen beheren
description: In dit artikel wordt uitgelegd hoe het PowerShell-Docs-team problemen beheert.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352706"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="823d0-103">De manier waarop we problemen beheren</span><span class="sxs-lookup"><span data-stu-id="823d0-103">How we manage issues</span></span>

<span data-ttu-id="823d0-104">In dit artikel wordt beschreven hoe we problemen beheren in de PowerShell-Docs opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="823d0-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="823d0-105">Dit artikel is bedoeld als taak hulp voor leden van het PowerShell-Docs team.</span><span class="sxs-lookup"><span data-stu-id="823d0-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="823d0-106">Het wordt hier gepubliceerd om proces transparantie te bieden voor de open bare mede werkers.</span><span class="sxs-lookup"><span data-stu-id="823d0-106">It's published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="823d0-107">Bronnen van problemen</span><span class="sxs-lookup"><span data-stu-id="823d0-107">Sources of issues</span></span>

- <span data-ttu-id="823d0-108">Community-inzenders</span><span class="sxs-lookup"><span data-stu-id="823d0-108">Community contributors</span></span>
- <span data-ttu-id="823d0-109">Interne inzenders</span><span class="sxs-lookup"><span data-stu-id="823d0-109">Internal contributors</span></span>
- <span data-ttu-id="823d0-110">Transcripties van opmerkingen van sociale-media kanalen</span><span class="sxs-lookup"><span data-stu-id="823d0-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="823d0-111">Feedback via het formulier docs feedback</span><span class="sxs-lookup"><span data-stu-id="823d0-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="823d0-112">Doelen voor reactie tijd</span><span class="sxs-lookup"><span data-stu-id="823d0-112">Response time targets</span></span>

<span data-ttu-id="823d0-113">80% van de nieuwe problemen zijn binnen drie werk dagen gesloten.</span><span class="sxs-lookup"><span data-stu-id="823d0-113">80% of new issues are closed within 3 business days.</span></span>

- <span data-ttu-id="823d0-114">Ingedeeld-1 werk dagen</span><span class="sxs-lookup"><span data-stu-id="823d0-114">Triaged - 1 business days</span></span>
- <span data-ttu-id="823d0-115">Herstellen of wijzigen-10 werk dagen</span><span class="sxs-lookup"><span data-stu-id="823d0-115">Fix or change - 10 business days</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="823d0-116">Labels & mijl palen</span><span class="sxs-lookup"><span data-stu-id="823d0-116">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="823d0-117">Label typen</span><span class="sxs-lookup"><span data-stu-id="823d0-117">Label Types</span></span>

|   <span data-ttu-id="823d0-118">Type</span><span class="sxs-lookup"><span data-stu-id="823d0-118">Type</span></span>   | <span data-ttu-id="823d0-119">Description</span><span class="sxs-lookup"><span data-stu-id="823d0-119">Description</span></span>                                                         |
| -------- | ------------------------------------------------------------------- |
| <span data-ttu-id="823d0-120">Gebied</span><span class="sxs-lookup"><span data-stu-id="823d0-120">Area</span></span>     | <span data-ttu-id="823d0-121">Wordt gebruikt om aan te geven welk gedeelte van Power shell of welke docs het probleem ondervindt.</span><span class="sxs-lookup"><span data-stu-id="823d0-121">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="823d0-122">Deze optie is handig voor eigen aars om problemen voor hun functie te vinden.</span><span class="sxs-lookup"><span data-stu-id="823d0-122">Useful for feature owners to find issues for their feature.</span></span> |
| <span data-ttu-id="823d0-123">Probleem</span><span class="sxs-lookup"><span data-stu-id="823d0-123">Issue</span></span>    | <span data-ttu-id="823d0-124">Hiermee wordt het type probleem aangegeven</span><span class="sxs-lookup"><span data-stu-id="823d0-124">Indicates the type of issue</span></span>                                         |
| <span data-ttu-id="823d0-125">Prioriteit</span><span class="sxs-lookup"><span data-stu-id="823d0-125">Priority</span></span> | <span data-ttu-id="823d0-126">Hiermee wordt de prioriteit van het probleem aangegeven.</span><span class="sxs-lookup"><span data-stu-id="823d0-126">Indicates the priority of the issue.</span></span> <span data-ttu-id="823d0-127">Waardebereik 0 (hoog)-4 (laag)</span><span class="sxs-lookup"><span data-stu-id="823d0-127">Value range 0 (high) -4 (low)</span></span>  |
| <span data-ttu-id="823d0-128">Status</span><span class="sxs-lookup"><span data-stu-id="823d0-128">Status</span></span>   | <span data-ttu-id="823d0-129">Hiermee wordt de status van het werk item aangegeven of de reden waarom deze is gesloten</span><span class="sxs-lookup"><span data-stu-id="823d0-129">Indicates the status of the work item or why it was closed</span></span>          |
| <span data-ttu-id="823d0-130">Label</span><span class="sxs-lookup"><span data-stu-id="823d0-130">Tag</span></span>      | <span data-ttu-id="823d0-131">Labels die worden gebruikt voor extra classificatie</span><span class="sxs-lookup"><span data-stu-id="823d0-131">Labels used to for additional classification</span></span>                        |
| <span data-ttu-id="823d0-132">Wachten</span><span class="sxs-lookup"><span data-stu-id="823d0-132">Waiting</span></span>  | <span data-ttu-id="823d0-133">Hiermee wordt aangegeven dat er wordt gewacht op iemand of een andere gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="823d0-133">Indicates that we're waiting on someone or some other event</span></span>         |

#### <a name="milestones"></a><span data-ttu-id="823d0-134">Mijlpalen</span><span class="sxs-lookup"><span data-stu-id="823d0-134">Milestones</span></span>

<span data-ttu-id="823d0-135">Problemen en pull moeten worden gelabeld met de juiste mijl paal.</span><span class="sxs-lookup"><span data-stu-id="823d0-135">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="823d0-136">Als het probleem niet van toepassing is op een specifieke versie, wordt er geen mijl paal gebruikt.</span><span class="sxs-lookup"><span data-stu-id="823d0-136">If the issue doesn't apply to a specific version, then no milestone is used.</span></span> <span data-ttu-id="823d0-137">Pull en gerelateerde problemen voor wijzigingen die nog moeten worden samengevoegd met de Power shell-code basis, moeten worden toegewezen aan de **toekomstige** mijl paal.</span><span class="sxs-lookup"><span data-stu-id="823d0-137">PRs and related issues for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="823d0-138">Nadat de code wijziging is samengevoegd, wijzigt u de mijl paal naar de juiste versie.</span><span class="sxs-lookup"><span data-stu-id="823d0-138">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="823d0-139">Mijlpalen</span><span class="sxs-lookup"><span data-stu-id="823d0-139">Milestone</span></span>     |                    <span data-ttu-id="823d0-140">Description</span><span class="sxs-lookup"><span data-stu-id="823d0-140">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="823d0-141">7.0.0</span><span class="sxs-lookup"><span data-stu-id="823d0-141">7.0.0</span></span>            | <span data-ttu-id="823d0-142">Werk items met betrekking tot Power shell 7,0</span><span class="sxs-lookup"><span data-stu-id="823d0-142">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="823d0-143">7.1.0</span><span class="sxs-lookup"><span data-stu-id="823d0-143">7.1.0</span></span>            | <span data-ttu-id="823d0-144">Werk items met betrekking tot Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="823d0-144">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="823d0-145">7.2.0</span><span class="sxs-lookup"><span data-stu-id="823d0-145">7.2.0</span></span>            | <span data-ttu-id="823d0-146">Werk items met betrekking tot Power shell 7,2</span><span class="sxs-lookup"><span data-stu-id="823d0-146">Work items related to PowerShell 7.2</span></span>               |
| <span data-ttu-id="823d0-147">Toekomstig</span><span class="sxs-lookup"><span data-stu-id="823d0-147">Future</span></span>           | <span data-ttu-id="823d0-148">Werk items een toekomstige versie van Power shell</span><span class="sxs-lookup"><span data-stu-id="823d0-148">Work items a future version of PowerShell</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="823d0-149">Sorteren-proces</span><span class="sxs-lookup"><span data-stu-id="823d0-149">Triage process</span></span>

<span data-ttu-id="823d0-150">Team leden van Power shell-docs bekijken de problemen dagelijks en sorteren nieuwe problemen wanneer ze binnenkomen.</span><span class="sxs-lookup"><span data-stu-id="823d0-150">PowerShell docs team members review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="823d0-151">Het team voldoet aan de wekelijkse voor het bespreken van problemen die sorteren of onopgelost moeten blijven.</span><span class="sxs-lookup"><span data-stu-id="823d0-151">The team meets weekly to discuss issues that need triage or remain unresolved.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="823d0-152">Verkeerd geplaatste product feedback</span><span class="sxs-lookup"><span data-stu-id="823d0-152">Misplaced product feedback</span></span>

- <span data-ttu-id="823d0-153">Voer een opmerking in die de klant omleidt naar het juiste feedback kanaal.</span><span class="sxs-lookup"><span data-stu-id="823d0-153">Enter a comment redirecting the customer to the correct feedback channel.</span></span>
- <span data-ttu-id="823d0-154">Optioneel: Kopieer het probleem naar de juiste locatie van de product feedback, voeg een koppeling naar het gekopieerde item toe en sluit het probleem.</span><span class="sxs-lookup"><span data-stu-id="823d0-154">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="823d0-155">GEEN problemen naar UserVoice kopiëren.</span><span class="sxs-lookup"><span data-stu-id="823d0-155">DO NOT copy issues to UserVoice.</span></span>

  <span data-ttu-id="823d0-156">De standaard locatie voor Power Shell-problemen is [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) .</span><span class="sxs-lookup"><span data-stu-id="823d0-156">The default location for PowerShell issues is [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

  <span data-ttu-id="823d0-157">De volgende onderwerpgebieden hebben verschillende locaties voor problemen:</span><span class="sxs-lookup"><span data-stu-id="823d0-157">The following subject areas have different locations for issues:</span></span>

  | <span data-ttu-id="823d0-158">Onderwerpen</span><span class="sxs-lookup"><span data-stu-id="823d0-158">Subjects</span></span> |                                                     <span data-ttu-id="823d0-159">URL van product feedback</span><span class="sxs-lookup"><span data-stu-id="823d0-159">Product Feedback URL</span></span>                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | <span data-ttu-id="823d0-160">dsc</span><span class="sxs-lookup"><span data-stu-id="823d0-160">dsc</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | <span data-ttu-id="823d0-161">galerie</span><span class="sxs-lookup"><span data-stu-id="823d0-161">gallery</span></span>  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | <span data-ttu-id="823d0-162">JEA</span><span class="sxs-lookup"><span data-stu-id="823d0-162">jea</span></span>      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | <span data-ttu-id="823d0-163">WMF</span><span class="sxs-lookup"><span data-stu-id="823d0-163">wmf</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a><span data-ttu-id="823d0-164">Ondersteuningsaanvragen</span><span class="sxs-lookup"><span data-stu-id="823d0-164">Support requests</span></span>

- <span data-ttu-id="823d0-165">Als de vraag van de ondersteuning eenvoudig is, beantwoordt u deze en sluit u het probleem.</span><span class="sxs-lookup"><span data-stu-id="823d0-165">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="823d0-166">Als de vraag gecompliceerder is, of als de indiener antwoordt met meer vragen, stuurt u deze om naar forums en ondersteunings kanalen.</span><span class="sxs-lookup"><span data-stu-id="823d0-166">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="823d0-167">Voorgestelde tekst voor omleiding naar forums:</span><span class="sxs-lookup"><span data-stu-id="823d0-167">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="823d0-168">Gedrags code schendingen</span><span class="sxs-lookup"><span data-stu-id="823d0-168">Code of conduct violations</span></span>

- <span data-ttu-id="823d0-169">Bewerk het probleem zo nodig om eventuele aanstootgevende inhoud te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="823d0-169">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="823d0-170">Voer een opmerking in om aan te geven dat het probleem spam is, sluit het probleem en vergrendel het vervolgens om verdere opmerkingen te voor komen.</span><span class="sxs-lookup"><span data-stu-id="823d0-170">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="823d0-171">Elke schending moet worden besproken in de wekelijkse sorteren om te bepalen of verdere actie moet worden ondernomen (rapporteren aan GitHub of micro soft juridisch).</span><span class="sxs-lookup"><span data-stu-id="823d0-171">Each violation should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
