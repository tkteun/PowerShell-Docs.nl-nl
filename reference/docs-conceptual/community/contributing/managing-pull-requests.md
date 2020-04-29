---
title: De manier waarop we pull-aanvragen beheren
description: In dit artikel wordt uitgelegd hoe het Power shell-docs-team pull-aanvragen beheert.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b9b37816dfdf38e4d8b7c2d66799164d0e97d257
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "79078610"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="cbeb2-103">Pull-aanvragen beheren</span><span class="sxs-lookup"><span data-stu-id="cbeb2-103">Managing pull requests</span></span>

<span data-ttu-id="cbeb2-104">In dit artikel wordt beschreven hoe u pull-aanvragen beheert in het Power shell-docs opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-104">This article documents how we manage pull requests in the PowerShell-Docs repo.</span></span> <span data-ttu-id="cbeb2-105">Dit artikel is bedoeld als taak hulp voor leden van het Power shell-docs-team.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="cbeb2-106">Dit wordt hier gepubliceerd om proces transparantie te bieden voor de open bare mede werkers.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="cbeb2-107">Aanbevolen procedures</span><span class="sxs-lookup"><span data-stu-id="cbeb2-107">Best practices</span></span>

- <span data-ttu-id="cbeb2-108">De persoon die de PR verzendt, mag de PR niet samen voegen zonder een peer beoordeling.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-108">The person submitting the PR should not merge the PR without a peer review.</span></span>
- <span data-ttu-id="cbeb2-109">Wijs de persoons revisor toe wanneer de PR wordt verzonden.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="cbeb2-110">Met een vroege toewijzing kan de revisor snel met redactionele opmerkingen reageren.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="cbeb2-111">Gebruik opmerkingen om de aard van de wijziging of het type revisie dat wordt aangevraagd te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="cbeb2-112">Zorg ervoor dat @mention u de revisor bekijkt.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="cbeb2-113">Als de wijziging bijvoorbeeld klein is en u geen volledige technische controle nodig hebt, wordt dit in een opmerking beschreven.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="cbeb2-114">PR proces stappen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-114">PR Process steps</span></span>

1. <span data-ttu-id="cbeb2-115">Writer: PR maken</span><span class="sxs-lookup"><span data-stu-id="cbeb2-115">Writer: Create PR</span></span>
   - <span data-ttu-id="cbeb2-116">Koppelingen oplossen die zijn opgelost door de PR</span><span class="sxs-lookup"><span data-stu-id="cbeb2-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="cbeb2-117">De functie [AutoClose](https://help.github.com/en/articles/closing-issues-using-keywords) van github gebruiken om het probleem te sluiten</span><span class="sxs-lookup"><span data-stu-id="cbeb2-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="cbeb2-118">Writer: de revisor van een peer toewijzen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="cbeb2-119">Revisor: reviews en opmerkingen (indien nodig)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="cbeb2-120">Writer: beoordelings feedback opnemen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="cbeb2-121">Beide: Preview-rendering bekijken</span><span class="sxs-lookup"><span data-stu-id="cbeb2-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="cbeb2-122">Beide: validatie rapport controleren-waarschuwingen en fouten oplossen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="cbeb2-123">Writer: afmelding toevoegen (Acrolinx-informatie vermelden)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="cbeb2-124">Revisor: Markeer beoordeling "goedgekeurd"</span><span class="sxs-lookup"><span data-stu-id="cbeb2-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="cbeb2-125">Opslag plaats beheerder: PR samen voegen (zie hieronder voor de criteria)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="cbeb2-126">Controle lijst voor inhouds revisor</span><span class="sxs-lookup"><span data-stu-id="cbeb2-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="cbeb2-127">Raadpleeg de [controle lijst voor redactionele](editorial-checklist.md) voor een uitgebreidere lijst.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="cbeb2-128">Review voor grammatica, stijl, Concision, technische nauw keurigheid</span><span class="sxs-lookup"><span data-stu-id="cbeb2-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="cbeb2-129">Zorg ervoor dat er nog steeds voor beelden gelden voor de doel versie</span><span class="sxs-lookup"><span data-stu-id="cbeb2-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="cbeb2-130">Preview-rendering controleren</span><span class="sxs-lookup"><span data-stu-id="cbeb2-130">Check Preview rendering</span></span>
- <span data-ttu-id="cbeb2-131">Meta gegevens controleren-MS. date, MS. AssetID verwijderen, verplichte velden controleren</span><span class="sxs-lookup"><span data-stu-id="cbeb2-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="cbeb2-132">De juistheid van de prijs verlaging valideren</span><span class="sxs-lookup"><span data-stu-id="cbeb2-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="cbeb2-133">Zie stijl gids voor het opmaken van specifieke inhoud</span><span class="sxs-lookup"><span data-stu-id="cbeb2-133">See style guide for formatting specific content</span></span>
- <span data-ttu-id="cbeb2-134">Voor beelden opnieuw ordenen:</span><span class="sxs-lookup"><span data-stu-id="cbeb2-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="cbeb2-135">Inleiding zin (s)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="cbeb2-136">Code en uitvoer</span><span class="sxs-lookup"><span data-stu-id="cbeb2-136">Code and output</span></span>
  - <span data-ttu-id="cbeb2-137">Gedetailleerde uitleg van code (indien nodig)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="cbeb2-138">Hyper links controleren op nauw keurigheid</span><span class="sxs-lookup"><span data-stu-id="cbeb2-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="cbeb2-139">TechNet/MSDN-koppelingen vervangen of verwijderen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="cbeb2-140">Het minimum aantal omleidingen voor de doel groep controleren</span><span class="sxs-lookup"><span data-stu-id="cbeb2-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="cbeb2-141">HTTPS controleren</span><span class="sxs-lookup"><span data-stu-id="cbeb2-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="cbeb2-142">Juiste koppelings type</span><span class="sxs-lookup"><span data-stu-id="cbeb2-142">Correct link type</span></span>
    - <span data-ttu-id="cbeb2-143">Bestands koppelingen voor lokale bestanden</span><span class="sxs-lookup"><span data-stu-id="cbeb2-143">File links for local files</span></span>
    - <span data-ttu-id="cbeb2-144">URL-koppelingen voor bestanden buiten de docset</span><span class="sxs-lookup"><span data-stu-id="cbeb2-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="cbeb2-145">Land instellingen uit Url's verwijderen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="cbeb2-146">Vereenvoudig Url's waarnaar wordt verwezen`docs.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="cbeb2-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="cbeb2-147">Vertakkings samenvoegings proces</span><span class="sxs-lookup"><span data-stu-id="cbeb2-147">Branch Merge Process</span></span>

<span data-ttu-id="cbeb2-148">De staging-vertakking is de enige vertakking die ooit in Live moet worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-148">The staging branch is the only branch that should ever be merged into live.</span></span> <span data-ttu-id="cbeb2-149">Het samen voegen van branches met een korte levens duur (werk) moet squashed zijn.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="cbeb2-150">*Samen voegen van/naar*</span><span class="sxs-lookup"><span data-stu-id="cbeb2-150">*Merge from/to*</span></span>  | <span data-ttu-id="cbeb2-151">*release-vertakking*</span><span class="sxs-lookup"><span data-stu-id="cbeb2-151">*release-branch*</span></span> | <span data-ttu-id="cbeb2-152">*Stell*</span><span class="sxs-lookup"><span data-stu-id="cbeb2-152">*staging*</span></span>        | <span data-ttu-id="cbeb2-153">*Galerie*</span><span class="sxs-lookup"><span data-stu-id="cbeb2-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="cbeb2-154">*werk vertakking*</span><span class="sxs-lookup"><span data-stu-id="cbeb2-154">*working-branch*</span></span> | <span data-ttu-id="cbeb2-155">Squash en samen voegen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-155">squash and merge</span></span> | <span data-ttu-id="cbeb2-156">Squash en samen voegen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-156">squash and merge</span></span> | <span data-ttu-id="cbeb2-157">Niet toegestaan</span><span class="sxs-lookup"><span data-stu-id="cbeb2-157">Not allowed</span></span> |
| <span data-ttu-id="cbeb2-158">*release-vertakking*</span><span class="sxs-lookup"><span data-stu-id="cbeb2-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="cbeb2-159">samenvoegen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-159">merge</span></span>            | <span data-ttu-id="cbeb2-160">Niet toegestaan</span><span class="sxs-lookup"><span data-stu-id="cbeb2-160">Not allowed</span></span> |
| <span data-ttu-id="cbeb2-161">*Stell*</span><span class="sxs-lookup"><span data-stu-id="cbeb2-161">*staging*</span></span>        | <span data-ttu-id="cbeb2-162">opnieuw baseren</span><span class="sxs-lookup"><span data-stu-id="cbeb2-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="cbeb2-163">samenvoegen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="cbeb2-164">Controle lijst PR fusie</span><span class="sxs-lookup"><span data-stu-id="cbeb2-164">PR Merger checklist</span></span>

- <span data-ttu-id="cbeb2-165">Beoordeling van inhoud is voltooid</span><span class="sxs-lookup"><span data-stu-id="cbeb2-165">Content review complete</span></span>
- <span data-ttu-id="cbeb2-166">Juiste doel vertakking voor de wijziging</span><span class="sxs-lookup"><span data-stu-id="cbeb2-166">Correct target branch for the change</span></span>
- <span data-ttu-id="cbeb2-167">Geen samenvoeg conflicten</span><span class="sxs-lookup"><span data-stu-id="cbeb2-167">No merge conflicts</span></span>
- <span data-ttu-id="cbeb2-168">Alle validatie-en build-stap fase</span><span class="sxs-lookup"><span data-stu-id="cbeb2-168">All validation and build step pass</span></span>
  - <span data-ttu-id="cbeb2-169">Waarschuwingen en suggesties moeten worden opgelost (Zie [opmerkingen](#notes) voor uitzonde ringen)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="cbeb2-170">Geen verbroken koppelingen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-170">No broken links</span></span>
- <span data-ttu-id="cbeb2-171">Samen voegen volgens tabel</span><span class="sxs-lookup"><span data-stu-id="cbeb2-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="cbeb2-172">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cbeb2-172">Notes</span></span>

<span data-ttu-id="cbeb2-173">De volgende waarschuwingen kunnen niet worden genegeerd:</span><span class="sxs-lookup"><span data-stu-id="cbeb2-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="cbeb2-174">Wanneer een PR wordt samengevoegd, wordt de kop van de doel vertakking gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="cbeb2-175">Alle open pull die waren gebaseerd op de vorige kop zijn nu verouderd.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="cbeb2-176">De verouderde PR kan worden samengevoegd met beheerders rechten om de samenvoeg waarschuwingen in GitHub te negeren.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="cbeb2-177">Dit is veilig om te doen als de eerder samengevoegde PR (s) niet dezelfde bestanden hebben geraken.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="cbeb2-178">Als u echter op de knop **vertakking bijwerken** klikt, is de veiligste optie.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="cbeb2-179">Mogelijk zijn er conflicten opgelost die moeten worden opgelost.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="cbeb2-180">Publiceren naar Live</span><span class="sxs-lookup"><span data-stu-id="cbeb2-180">Publishing to Live</span></span>

<span data-ttu-id="cbeb2-181">De wijzigingen die in de `staging` vertakking zijn verzameld, moeten regel matig worden gepubliceerd op de Live-website.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span> <span data-ttu-id="cbeb2-182">Hiervoor moet de `staging` vertakking in de `live` vertakking worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-182">This require merging the `staging` branch into the `live` branch.</span></span>

- <span data-ttu-id="cbeb2-183">De `staging` vertakking moet `live` ten minste eenmaal per week worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-183">The `staging` branch should be merged to `live` at least once per week.</span></span>
- <span data-ttu-id="cbeb2-184">De `staging` vertakking moet worden samengevoegd tot `live` na een belang rijke wijziging.</span><span class="sxs-lookup"><span data-stu-id="cbeb2-184">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="cbeb2-185">Wijzigingen in 50 of meer bestanden</span><span class="sxs-lookup"><span data-stu-id="cbeb2-185">Changes to 50 or more files</span></span>
  - <span data-ttu-id="cbeb2-186">Na het samen voegen van een release vertakking</span><span class="sxs-lookup"><span data-stu-id="cbeb2-186">After merging a release branch</span></span>
  - <span data-ttu-id="cbeb2-187">Wijzigingen in opslag plaats-of docset-configuraties (docfx. json, OPS-configuratie, build-scripts enzovoort)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-187">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="cbeb2-188">Wijzigingen in het omleidings bestand</span><span class="sxs-lookup"><span data-stu-id="cbeb2-188">Changes to the redirection file</span></span>
  - <span data-ttu-id="cbeb2-189">Wijzigingen in de inhouds opgave</span><span class="sxs-lookup"><span data-stu-id="cbeb2-189">Changes to the TOC</span></span>
  - <span data-ttu-id="cbeb2-190">Na het samen voegen van een ' project-' vertakking (content Reorg, bulksgewijze update, enzovoort)</span><span class="sxs-lookup"><span data-stu-id="cbeb2-190">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>
