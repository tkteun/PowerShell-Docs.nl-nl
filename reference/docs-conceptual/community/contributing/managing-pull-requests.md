---
title: De manier waarop we pull-aanvragen beheren
description: In dit artikel wordt uitgelegd hoe het PowerShell-Docs-team pull-aanvragen beheert.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 7050db6ad30963d0a75b2a083daace494d703027
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090529"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="59532-103">Pull-aanvragen beheren</span><span class="sxs-lookup"><span data-stu-id="59532-103">Managing pull requests</span></span>

<span data-ttu-id="59532-104">In dit artikel wordt beschreven hoe u pull-aanvragen beheert in de PowerShell-Docs opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="59532-104">This article documents how we manage pull requests in the PowerShell-Docs repository.</span></span> <span data-ttu-id="59532-105">Dit artikel is bedoeld als taak hulp voor leden van het PowerShell-Docs team.</span><span class="sxs-lookup"><span data-stu-id="59532-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="59532-106">Het wordt hier gepubliceerd om proces transparantie te bieden voor de open bare mede werkers.</span><span class="sxs-lookup"><span data-stu-id="59532-106">It's published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="59532-107">Aanbevolen procedures</span><span class="sxs-lookup"><span data-stu-id="59532-107">Best practices</span></span>

- <span data-ttu-id="59532-108">De persoon die de PR verzendt, mag de PR niet zonder een beoordeling van een peer samen voegen.</span><span class="sxs-lookup"><span data-stu-id="59532-108">The person submitting the PR shouldn't merge the PR without a peer review.</span></span>
- <span data-ttu-id="59532-109">Wijs de persoons revisor toe wanneer de PR wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="59532-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="59532-110">Met een vroege toewijzing kan de revisor snel met redactionele opmerkingen reageren.</span><span class="sxs-lookup"><span data-stu-id="59532-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="59532-111">Gebruik opmerkingen om de aard van de wijziging of het type revisie dat wordt aangevraagd te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="59532-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="59532-112">Zorg ervoor dat u @mention de revisor bekijkt.</span><span class="sxs-lookup"><span data-stu-id="59532-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="59532-113">Als de wijziging bijvoorbeeld klein is en u geen volledige technische controle nodig hebt, wordt dit in een opmerking beschreven.</span><span class="sxs-lookup"><span data-stu-id="59532-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="59532-114">PR proces stappen</span><span class="sxs-lookup"><span data-stu-id="59532-114">PR Process steps</span></span>

1. <span data-ttu-id="59532-115">Writer: PR maken</span><span class="sxs-lookup"><span data-stu-id="59532-115">Writer: Create PR</span></span>
   - <span data-ttu-id="59532-116">Koppelingen oplossen die zijn opgelost door de PR</span><span class="sxs-lookup"><span data-stu-id="59532-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="59532-117">De functie [AutoClose](https://help.github.com/en/articles/closing-issues-using-keywords) van github gebruiken om het probleem te sluiten</span><span class="sxs-lookup"><span data-stu-id="59532-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="59532-118">Writer: de revisor van een peer toewijzen</span><span class="sxs-lookup"><span data-stu-id="59532-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="59532-119">Revisor: reviews en opmerkingen (indien nodig)</span><span class="sxs-lookup"><span data-stu-id="59532-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="59532-120">Writer: beoordelings feedback opnemen</span><span class="sxs-lookup"><span data-stu-id="59532-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="59532-121">Beide: Preview-rendering bekijken</span><span class="sxs-lookup"><span data-stu-id="59532-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="59532-122">Beide: validatie rapport controleren-waarschuwingen en fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="59532-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="59532-123">Writer: afmelding toevoegen (Acrolinx-informatie vermelden)</span><span class="sxs-lookup"><span data-stu-id="59532-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="59532-124">Revisor: Markeer beoordeling "goedgekeurd"</span><span class="sxs-lookup"><span data-stu-id="59532-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="59532-125">Opslag plaats beheerder: PR samen voegen (zie hieronder voor de criteria)</span><span class="sxs-lookup"><span data-stu-id="59532-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="59532-126">Controle lijst voor inhouds revisor</span><span class="sxs-lookup"><span data-stu-id="59532-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="59532-127">Raadpleeg de [controle lijst voor redactionele](editorial-checklist.md) voor een uitgebreidere lijst.</span><span class="sxs-lookup"><span data-stu-id="59532-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="59532-128">Review voor grammatica, stijl, Concision, technische nauw keurigheid</span><span class="sxs-lookup"><span data-stu-id="59532-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="59532-129">Zorg ervoor dat er nog steeds voor beelden gelden voor de doel versie</span><span class="sxs-lookup"><span data-stu-id="59532-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="59532-130">Preview-rendering controleren</span><span class="sxs-lookup"><span data-stu-id="59532-130">Check Preview rendering</span></span>
- <span data-ttu-id="59532-131">Meta gegevens controleren-MS. date, MS. AssetID verwijderen, verplichte velden controleren</span><span class="sxs-lookup"><span data-stu-id="59532-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="59532-132">De juistheid van de prijs verlaging valideren</span><span class="sxs-lookup"><span data-stu-id="59532-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="59532-133">Zie stijl gids voor taalspecifieke opmaak regels</span><span class="sxs-lookup"><span data-stu-id="59532-133">See style guide for content-specific formatting rules</span></span>
- <span data-ttu-id="59532-134">Voor beelden opnieuw ordenen:</span><span class="sxs-lookup"><span data-stu-id="59532-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="59532-135">Inleiding zin (s)</span><span class="sxs-lookup"><span data-stu-id="59532-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="59532-136">Code en uitvoer</span><span class="sxs-lookup"><span data-stu-id="59532-136">Code and output</span></span>
  - <span data-ttu-id="59532-137">Gedetailleerde uitleg van code (indien nodig)</span><span class="sxs-lookup"><span data-stu-id="59532-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="59532-138">Hyper links controleren op nauw keurigheid</span><span class="sxs-lookup"><span data-stu-id="59532-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="59532-139">TechNet/MSDN-koppelingen vervangen of verwijderen</span><span class="sxs-lookup"><span data-stu-id="59532-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="59532-140">Het minimum aantal omleidingen voor de doel groep controleren</span><span class="sxs-lookup"><span data-stu-id="59532-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="59532-141">HTTPS controleren</span><span class="sxs-lookup"><span data-stu-id="59532-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="59532-142">Juiste koppelings type</span><span class="sxs-lookup"><span data-stu-id="59532-142">Correct link type</span></span>
    - <span data-ttu-id="59532-143">Bestands koppelingen voor lokale bestanden</span><span class="sxs-lookup"><span data-stu-id="59532-143">File links for local files</span></span>
    - <span data-ttu-id="59532-144">URL-koppelingen voor bestanden buiten de docset</span><span class="sxs-lookup"><span data-stu-id="59532-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="59532-145">Land instellingen uit Url's verwijderen</span><span class="sxs-lookup"><span data-stu-id="59532-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="59532-146">Vereenvoudig Url's waarnaar wordt verwezen `docs.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="59532-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="59532-147">Vertakkings samenvoegings proces</span><span class="sxs-lookup"><span data-stu-id="59532-147">Branch Merge Process</span></span>

<span data-ttu-id="59532-148">De `staging` vertakking is de enige vertakking die wordt samengevoegd in `live` .</span><span class="sxs-lookup"><span data-stu-id="59532-148">The `staging` branch is the only branch that is merged into `live`.</span></span> <span data-ttu-id="59532-149">Het samen voegen van branches met een korte levens duur (werk) moet squashed zijn.</span><span class="sxs-lookup"><span data-stu-id="59532-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="59532-150">*Samen voegen van/naar*</span><span class="sxs-lookup"><span data-stu-id="59532-150">*Merge from/to*</span></span>  | <span data-ttu-id="59532-151">*release-vertakking*</span><span class="sxs-lookup"><span data-stu-id="59532-151">*release-branch*</span></span> | <span data-ttu-id="59532-152">*Stell*</span><span class="sxs-lookup"><span data-stu-id="59532-152">*staging*</span></span>        | <span data-ttu-id="59532-153">*Galerie*</span><span class="sxs-lookup"><span data-stu-id="59532-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="59532-154">*werk vertakking*</span><span class="sxs-lookup"><span data-stu-id="59532-154">*working-branch*</span></span> | <span data-ttu-id="59532-155">Squash en samen voegen</span><span class="sxs-lookup"><span data-stu-id="59532-155">squash and merge</span></span> | <span data-ttu-id="59532-156">Squash en samen voegen</span><span class="sxs-lookup"><span data-stu-id="59532-156">squash and merge</span></span> | <span data-ttu-id="59532-157">Niet toegestaan</span><span class="sxs-lookup"><span data-stu-id="59532-157">Not allowed</span></span> |
| <span data-ttu-id="59532-158">*release-vertakking*</span><span class="sxs-lookup"><span data-stu-id="59532-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="59532-159">samenvoegen</span><span class="sxs-lookup"><span data-stu-id="59532-159">merge</span></span>            | <span data-ttu-id="59532-160">Niet toegestaan</span><span class="sxs-lookup"><span data-stu-id="59532-160">Not allowed</span></span> |
| <span data-ttu-id="59532-161">*Stell*</span><span class="sxs-lookup"><span data-stu-id="59532-161">*staging*</span></span>        | <span data-ttu-id="59532-162">opnieuw baseren</span><span class="sxs-lookup"><span data-stu-id="59532-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="59532-163">samenvoegen</span><span class="sxs-lookup"><span data-stu-id="59532-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="59532-164">Controle lijst PR fusie</span><span class="sxs-lookup"><span data-stu-id="59532-164">PR Merger checklist</span></span>

- <span data-ttu-id="59532-165">Beoordeling van inhoud is voltooid</span><span class="sxs-lookup"><span data-stu-id="59532-165">Content review complete</span></span>
- <span data-ttu-id="59532-166">Juiste doel vertakking voor de wijziging</span><span class="sxs-lookup"><span data-stu-id="59532-166">Correct target branch for the change</span></span>
- <span data-ttu-id="59532-167">Geen samenvoeg conflicten</span><span class="sxs-lookup"><span data-stu-id="59532-167">No merge conflicts</span></span>
- <span data-ttu-id="59532-168">Alle validatie-en build-stap fase</span><span class="sxs-lookup"><span data-stu-id="59532-168">All validation and build step pass</span></span>
  - <span data-ttu-id="59532-169">Waarschuwingen en suggesties moeten worden opgelost (Zie [opmerkingen](#notes) voor uitzonde ringen)</span><span class="sxs-lookup"><span data-stu-id="59532-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="59532-170">Geen verbroken koppelingen</span><span class="sxs-lookup"><span data-stu-id="59532-170">No broken links</span></span>
- <span data-ttu-id="59532-171">Samen voegen volgens tabel</span><span class="sxs-lookup"><span data-stu-id="59532-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="59532-172">Notities</span><span class="sxs-lookup"><span data-stu-id="59532-172">Notes</span></span>

<span data-ttu-id="59532-173">De volgende waarschuwingen kunnen niet worden genegeerd:</span><span class="sxs-lookup"><span data-stu-id="59532-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="59532-174">Wanneer een PR wordt samengevoegd, wordt de kop van de doel vertakking gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="59532-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="59532-175">Alle open pull die waren gebaseerd op de vorige kop zijn nu verouderd.</span><span class="sxs-lookup"><span data-stu-id="59532-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="59532-176">De verouderde PR kan worden samengevoegd met beheerders rechten om de samenvoeg waarschuwingen in GitHub te negeren.</span><span class="sxs-lookup"><span data-stu-id="59532-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="59532-177">Dit is veilig om te doen als de eerder samengevoegde PR (s) niet dezelfde bestanden hebben geraken.</span><span class="sxs-lookup"><span data-stu-id="59532-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="59532-178">Als u echter op de knop **vertakking bijwerken** klikt, is de veiligste optie.</span><span class="sxs-lookup"><span data-stu-id="59532-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="59532-179">Mogelijk zijn er conflicten opgelost die moeten worden opgelost.</span><span class="sxs-lookup"><span data-stu-id="59532-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="59532-180">Publiceren naar Live</span><span class="sxs-lookup"><span data-stu-id="59532-180">Publishing to Live</span></span>

<span data-ttu-id="59532-181">De wijzigingen die in de vertakking zijn verzameld, moeten regel matig `staging` worden gepubliceerd op de Live-website.</span><span class="sxs-lookup"><span data-stu-id="59532-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span>

- <span data-ttu-id="59532-182">De `staging` vertakking wordt samengevoegd met `live` elke weekdag op 3pm PST.</span><span class="sxs-lookup"><span data-stu-id="59532-182">The `staging` branch is merged to `live` each weekday at 3pm PST.</span></span>
- <span data-ttu-id="59532-183">De `staging` vertakking moet worden samengevoegd tot `live` na een belang rijke wijziging.</span><span class="sxs-lookup"><span data-stu-id="59532-183">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="59532-184">Wijzigingen in 50 of meer bestanden</span><span class="sxs-lookup"><span data-stu-id="59532-184">Changes to 50 or more files</span></span>
  - <span data-ttu-id="59532-185">Na het samen voegen van een release vertakking</span><span class="sxs-lookup"><span data-stu-id="59532-185">After merging a release branch</span></span>
  - <span data-ttu-id="59532-186">Wijzigingen in opslag plaats-of docset-configuraties (docfx.jsin, OPS-configuratie, build-scripts enzovoort)</span><span class="sxs-lookup"><span data-stu-id="59532-186">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="59532-187">Wijzigingen in het omleidings bestand</span><span class="sxs-lookup"><span data-stu-id="59532-187">Changes to the redirection file</span></span>
  - <span data-ttu-id="59532-188">Wijzigingen in de inhouds opgave</span><span class="sxs-lookup"><span data-stu-id="59532-188">Changes to the TOC</span></span>
  - <span data-ttu-id="59532-189">Na het samen voegen van een ' project-' vertakking (content Reorg, bulksgewijze update, enzovoort)</span><span class="sxs-lookup"><span data-stu-id="59532-189">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>
