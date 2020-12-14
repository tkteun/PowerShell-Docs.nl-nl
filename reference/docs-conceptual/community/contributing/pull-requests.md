---
title: Pull-aanvragen verzenden
description: In dit artikel wordt uitgelegd hoe u pull-aanvragen verzendt naar de PowerShell-Docs opslag plaats.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090213"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="12425-103">Pull-aanvragen verzenden</span><span class="sxs-lookup"><span data-stu-id="12425-103">How to submit pull requests</span></span>

<span data-ttu-id="12425-104">Als u inhoud wilt wijzigen, moet u een pull-aanvraag (PR) bij uw Fork indienen.</span><span class="sxs-lookup"><span data-stu-id="12425-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="12425-105">Een pull-aanvraag moet worden gecontroleerd voordat deze kan worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="12425-105">A pull request must be reviewed before it can be merged.</span></span> <span data-ttu-id="12425-106">Voor de beste resultaten raadpleegt u de [controle lijst voor redactionele](editorial-checklist.md) voordat u uw pull-aanvraag indient.</span><span class="sxs-lookup"><span data-stu-id="12425-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="using-git-branches"></a><span data-ttu-id="12425-107">Git-vertakkingen gebruiken</span><span class="sxs-lookup"><span data-stu-id="12425-107">Using git branches</span></span>

<span data-ttu-id="12425-108">De standaard vertakking voor PowerShell-Docs is de `staging` vertakking.</span><span class="sxs-lookup"><span data-stu-id="12425-108">The default branch for PowerShell-Docs is the `staging` branch.</span></span> <span data-ttu-id="12425-109">Wijzigingen die zijn aangebracht in werk vertakkingen worden samengevoegd in de `staging` vertakking voordat ze worden gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="12425-109">Changes made in working branches are merged into the `staging` branch before then being published.</span></span> <span data-ttu-id="12425-110">De `staging` vertakking wordt `live` elke weekdag in de vertakking samengevoegd om 3:00 uur (Pacific Time).</span><span class="sxs-lookup"><span data-stu-id="12425-110">The `staging` branch is merged into the `live` branch every weekday at 3:00 PM (Pacific Time).</span></span> <span data-ttu-id="12425-111">De `live` vertakking bevat de inhoud die wordt gepubliceerd op docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="12425-111">The `live` branch contains the content that is published to docs.microsoft.com.</span></span>

<span data-ttu-id="12425-112">Voordat u wijzigingen start, maakt u een werk vertakking in uw lokale kopie van de PowerShell-Docs-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="12425-112">Before starting any changes, create a working branch in your local copy of the PowerShell-Docs repository.</span></span> <span data-ttu-id="12425-113">Als u lokaal werkt, moet u uw lokale opslag plaats synchroniseren voordat u uw werk vertakking maakt.</span><span class="sxs-lookup"><span data-stu-id="12425-113">When working locally, be sure to synchronize your local repository before creating your working branch.</span></span> <span data-ttu-id="12425-114">De werk vertakking moet worden gemaakt op basis van een update-to-date kopie van de `staging` vertakking.</span><span class="sxs-lookup"><span data-stu-id="12425-114">The working branch should be created from an update-to-date copy of the `staging` branch.</span></span>

<span data-ttu-id="12425-115">Alle pull-aanvragen moeten gericht zijn op de `staging` vertakking.</span><span class="sxs-lookup"><span data-stu-id="12425-115">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="12425-116">Verzend de wijziging niet naar de `live` vertakking.</span><span class="sxs-lookup"><span data-stu-id="12425-116">Don't submit change to the `live` branch.</span></span>
<span data-ttu-id="12425-117">Wijzigingen die in de `staging` vertakking zijn aangebracht, worden samengevoegd in `live` , waarbij wijzigingen in worden overschreven `live` .</span><span class="sxs-lookup"><span data-stu-id="12425-117">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="12425-118">Het proces voor pull-aanvragen voor iedereen beter laten werken</span><span class="sxs-lookup"><span data-stu-id="12425-118">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="12425-119">Het eenvoudiger en gerichter u kunt uw PR maken, des te sneller kan deze worden gecontroleerd en samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="12425-119">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="12425-120">Pull-aanvragen voor komen die een groot aantal bestanden bijwerken of niet-gerelateerde wijzigingen bevatten</span><span class="sxs-lookup"><span data-stu-id="12425-120">Avoid pull requests that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="12425-121">Vermijd het maken van pull die niet-gerelateerde wijzigingen bevatten.</span><span class="sxs-lookup"><span data-stu-id="12425-121">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="12425-122">Scheid kleine updates aan bestaande artikelen van nieuwe artikelen of artikelen die grotendeels zijn herschreven.</span><span class="sxs-lookup"><span data-stu-id="12425-122">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="12425-123">Behandel deze wijzigingen in aparte werkstromen.</span><span class="sxs-lookup"><span data-stu-id="12425-123">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="12425-124">Bulk wijzigingen maken pull met een groot aantal gewijzigde bestanden.</span><span class="sxs-lookup"><span data-stu-id="12425-124">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="12425-125">Beperk uw pull-aanvragen tot maximaal 50 gewijzigde bestanden.</span><span class="sxs-lookup"><span data-stu-id="12425-125">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="12425-126">Grote pull-aanvragen zijn moeilijk te controleren en gevoeliger voor fouten.</span><span class="sxs-lookup"><span data-stu-id="12425-126">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="12425-127">Bestanden een andere naam geven of verwijderen</span><span class="sxs-lookup"><span data-stu-id="12425-127">Renaming or deleting files</span></span>

<span data-ttu-id="12425-128">Bij het wijzigen van de naam of het verwijderen van bestanden moet er een probleem zijn dat is gekoppeld aan de PR.</span><span class="sxs-lookup"><span data-stu-id="12425-128">When renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="12425-129">Dit probleem moet betrekking hebben op de nood zaak om de bestanden een andere naam te geven of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="12425-129">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="12425-130">Vermijd het combi neren van inhouds toevoegingen of wijziging van het wijzigen van de naam en het verwijderen van bestanden.</span><span class="sxs-lookup"><span data-stu-id="12425-130">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="12425-131">Elk bestand waarvan de naam wordt gewijzigd of verwijderd, moet worden toegevoegd aan het globale omleidings bestand.</span><span class="sxs-lookup"><span data-stu-id="12425-131">Any file that is renamed or deleted must be added to the global redirection file.</span></span> <span data-ttu-id="12425-132">Als dat mogelijk is, werkt u de bestanden bij die zijn gekoppeld aan de hernoemde of verwijderde inhoud, inclusief eventuele inhoudsopgave bestanden.</span><span class="sxs-lookup"><span data-stu-id="12425-132">When possible, update any files that link to the renamed or deleted content, including any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="12425-133">Docs PR-validatieservice</span><span class="sxs-lookup"><span data-stu-id="12425-133">Docs PR validation service</span></span>

<span data-ttu-id="12425-134">De docs PR-validatie service is een GitHub-app waarmee validatie regels worden uitgevoerd op uw wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="12425-134">The Docs PR validation service is a GitHub app that runs validation rules on your changes.</span></span> <span data-ttu-id="12425-135">U moet eventuele fouten of waarschuwingen die zijn gerapporteerd door de validatie service corrigeren.</span><span class="sxs-lookup"><span data-stu-id="12425-135">You must fix any errors or warnings reported by the validation service.</span></span>

<span data-ttu-id="12425-136">U ziet het volgende gedrag:</span><span class="sxs-lookup"><span data-stu-id="12425-136">You'll see the following behavior:</span></span>

1. <span data-ttu-id="12425-137">U dient een PR in.</span><span class="sxs-lookup"><span data-stu-id="12425-137">You submit a PR.</span></span>
1. <span data-ttu-id="12425-138">In de GitHub-opmerking die de status van uw PR aangeeft, ziet u de status ' controles ' die zijn ingeschakeld voor de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="12425-138">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="12425-139">In dit voor beeld zijn er twee controles ingeschakeld, ' commit-validatie ' en ' openpublishing. build ':</span><span class="sxs-lookup"><span data-stu-id="12425-139">In this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![validatie status-sommige controles zijn mislukt](media/pull-requests/validation-failed.png)

   <span data-ttu-id="12425-141">De build kan worden door gegeven, zelfs als de commit-validatie is mislukt.</span><span class="sxs-lookup"><span data-stu-id="12425-141">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="12425-142">Klik op **Details** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12425-142">Click **Details** for more information.</span></span>
1. <span data-ttu-id="12425-143">Op de pagina Details ziet u alle validatiecontroles die zijn mislukt, met informatie over wat u moet doen om de problemen op te lossen.</span><span class="sxs-lookup"><span data-stu-id="12425-143">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="12425-144">Als de validatie slaagt, wordt de volgende opmerking toegevoegd aan de pull-aanvraag:</span><span class="sxs-lookup"><span data-stu-id="12425-144">When validation succeeds, the following comment is added to the PR:</span></span>

   ![Validatie status: geslaagd](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="12425-146">Als u een externe mede werker (niet een micro soft-mede werker) bent, hebt u geen toegang tot de gedetailleerde rapporten van de build of de preview-koppelingen.</span><span class="sxs-lookup"><span data-stu-id="12425-146">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="12425-147">Wanneer de PR wordt gecontroleerd, wordt u mogelijk gevraagd om wijzigingen aan te brengen of validatie waarschuwings berichten op te lossen.</span><span class="sxs-lookup"><span data-stu-id="12425-147">When the PR is reviewed, you may be asked to make changes or fix validation warning messages.</span></span> <span data-ttu-id="12425-148">Het PowerShell-Docs-team kan u helpen bij het begrijpen van validatie fouten en redactionele vereisten.</span><span class="sxs-lookup"><span data-stu-id="12425-148">The PowerShell-Docs team can help you understand validation errors and editorial requirements.</span></span>

## <a name="next-steps"></a><span data-ttu-id="12425-149">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="12425-149">Next steps</span></span>

[<span data-ttu-id="12425-150">Stijlgids voor PowerShell-documentatie</span><span class="sxs-lookup"><span data-stu-id="12425-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="12425-151">Aanvullende resources</span><span class="sxs-lookup"><span data-stu-id="12425-151">Additional resources</span></span>

[<span data-ttu-id="12425-152">De manier waarop we pull-aanvragen beheren</span><span class="sxs-lookup"><span data-stu-id="12425-152">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
