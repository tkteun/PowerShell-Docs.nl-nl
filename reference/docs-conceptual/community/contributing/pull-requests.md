---
title: Pull-aanvragen verzenden
description: In dit artikel wordt uitgelegd hoe u pull-aanvragen verzendt naar de Power shell-docs-opslag plaats.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 2600049b06da5ad4869b6ff335f00bc40c2d1c22
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "79078505"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="e7364-103">Pull-aanvragen verzenden</span><span class="sxs-lookup"><span data-stu-id="e7364-103">How to submit pull requests</span></span>

<span data-ttu-id="e7364-104">Als u inhoud wilt wijzigen, moet u een pull-aanvraag (PR) bij uw Fork indienen.</span><span class="sxs-lookup"><span data-stu-id="e7364-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="e7364-105">Een pull-aanvraag moet worden gecontroleerd voordat deze kan worden samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="e7364-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="e7364-106">Voor de beste resultaten raadpleegt u de [controle lijst voor redactionele](editorial-checklist.md) voordat u uw pull-aanvraag indient.</span><span class="sxs-lookup"><span data-stu-id="e7364-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="e7364-107">De juiste vertakking kiezen</span><span class="sxs-lookup"><span data-stu-id="e7364-107">Target the correct branch</span></span>

<span data-ttu-id="e7364-108">Alle pull-aanvragen moeten gericht `staging` zijn op de vertakking.</span><span class="sxs-lookup"><span data-stu-id="e7364-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="e7364-109">Wijzigingen mogen nooit naar de `live` vertakking worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="e7364-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="e7364-110">Wijzigingen die in de `staging` vertakking zijn aangebracht, `live`worden samengevoegd in, waarbij wijzigingen in `live`worden overschreven.</span><span class="sxs-lookup"><span data-stu-id="e7364-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="e7364-111">Als u een wijziging indient die alleen van toepassing is op een niet-uitgebrachte versie van Power shell, controleert u op een release vertakking voor die versie.</span><span class="sxs-lookup"><span data-stu-id="e7364-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="e7364-112">Uw PR moet zijn gericht op de release vertakking.</span><span class="sxs-lookup"><span data-stu-id="e7364-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="e7364-113">Releasevertakkingen hebben het volgende naamgevingspatroon: `release-<version>`.</span><span class="sxs-lookup"><span data-stu-id="e7364-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="e7364-114">Het proces voor pull-aanvragen voor iedereen beter laten werken</span><span class="sxs-lookup"><span data-stu-id="e7364-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="e7364-115">Het eenvoudiger en gerichter u kunt uw PR maken, des te sneller kan deze worden gecontroleerd en samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="e7364-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="e7364-116">Vermijd vertakkingen die een groot aantal bestanden bijwerken of niet-gerelateerde wijzigingen bevatten</span><span class="sxs-lookup"><span data-stu-id="e7364-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="e7364-117">Vermijd het maken van pull die niet-gerelateerde wijzigingen bevatten.</span><span class="sxs-lookup"><span data-stu-id="e7364-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="e7364-118">Scheid kleine updates aan bestaande artikelen van nieuwe artikelen of artikelen die grotendeels zijn herschreven.</span><span class="sxs-lookup"><span data-stu-id="e7364-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="e7364-119">Behandel deze wijzigingen in aparte werkstromen.</span><span class="sxs-lookup"><span data-stu-id="e7364-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="e7364-120">Bulk wijzigingen maken pull met een groot aantal gewijzigde bestanden.</span><span class="sxs-lookup"><span data-stu-id="e7364-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="e7364-121">Beperk uw pull-aanvragen tot maximaal 50 gewijzigde bestanden.</span><span class="sxs-lookup"><span data-stu-id="e7364-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="e7364-122">Grote pull-aanvragen zijn moeilijk te controleren en gevoeliger voor fouten.</span><span class="sxs-lookup"><span data-stu-id="e7364-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="e7364-123">Bestanden een andere naam geven of verwijderen</span><span class="sxs-lookup"><span data-stu-id="e7364-123">Renaming or deleting files</span></span>

<span data-ttu-id="e7364-124">Als u een nieuwe naam wilt geven of bestanden wilt verwijderen, moet er een probleem zijn dat is gekoppeld aan de PR.</span><span class="sxs-lookup"><span data-stu-id="e7364-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="e7364-125">Dit probleem moet betrekking hebben op de nood zaak om de bestanden een andere naam te geven of te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e7364-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="e7364-126">Vermijd het combi neren van inhouds toevoegingen of wijziging van het wijzigen van de naam en het verwijderen van bestanden.</span><span class="sxs-lookup"><span data-stu-id="e7364-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="e7364-127">Elk bestand waarvan de naam wordt gewijzigd of verwijderd, moet worden toegevoegd aan het Master-omleidings bestand.</span><span class="sxs-lookup"><span data-stu-id="e7364-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="e7364-128">Indien mogelijk moet u ook alle bestanden bijwerken die zijn gekoppeld aan de hernoemde of verwijderde inhoud.</span><span class="sxs-lookup"><span data-stu-id="e7364-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="e7364-129">Dit omvat ook alle inhoudsopgavebestanden.</span><span class="sxs-lookup"><span data-stu-id="e7364-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="e7364-130">Docs PR-validatieservice</span><span class="sxs-lookup"><span data-stu-id="e7364-130">Docs PR validation service</span></span>

<span data-ttu-id="e7364-131">De Docs PR-validatieservice is een GitHub-app die validatieregels uitvoert op de bestanden in een PR.</span><span class="sxs-lookup"><span data-stu-id="e7364-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="e7364-132">U moet eventuele fouten of waarschuwingen oplossen (Zie uitzonde ringen) die door de validatie service zijn gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="e7364-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="e7364-133">De volgende waarschuwingen kunnen niet worden genegeerd:</span><span class="sxs-lookup"><span data-stu-id="e7364-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="e7364-134">U ziet het volgende gedrag:</span><span class="sxs-lookup"><span data-stu-id="e7364-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="e7364-135">U dient een PR in.</span><span class="sxs-lookup"><span data-stu-id="e7364-135">You submit a PR.</span></span>
1. <span data-ttu-id="e7364-136">In de GitHub-opmerking die de status van uw PR aangeeft, ziet u de status van controles die zijn ingeschakeld voor de opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="e7364-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repo.</span></span> <span data-ttu-id="e7364-137">In dit voorbeeld zijn er twee controles ingeschakeld, namelijk "Commit Validation" en "OpenPublishing.Build":</span><span class="sxs-lookup"><span data-stu-id="e7364-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![sommige controles zijn mislukt](media/pull-requests/validation-failed.png)

   <span data-ttu-id="e7364-139">De build kan worden door gegeven, zelfs als de commit-validatie is mislukt.</span><span class="sxs-lookup"><span data-stu-id="e7364-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="e7364-140">Klik op **Details** voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e7364-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="e7364-141">Op de pagina Details ziet u alle validatiecontroles die zijn mislukt, met informatie over wat u moet doen om de problemen op te lossen.</span><span class="sxs-lookup"><span data-stu-id="e7364-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="e7364-142">Als de validatie slaagt, wordt de volgende opmerking toegevoegd aan de pull-aanvraag:</span><span class="sxs-lookup"><span data-stu-id="e7364-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![build-validatie](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="e7364-144">Als u een externe mede werker (niet een micro soft-mede werker) bent, hebt u geen toegang tot de gedetailleerde rapporten van de build of de preview-koppelingen.</span><span class="sxs-lookup"><span data-stu-id="e7364-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="e7364-145">Wanneer de PR wordt gecontroleerd door een lid van het Power shell-docs-team, wordt u mogelijk gevraagd om wijzigingen aan te brengen of problemen op te lossen die door het validatie rapport zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="e7364-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="e7364-146">Het Power shell-docs-team kan u helpen inzicht te krijgen in het oplossen en voor komen van deze problemen voor toekomstige inzendingen.</span><span class="sxs-lookup"><span data-stu-id="e7364-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e7364-147">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="e7364-147">Next steps</span></span>

[<span data-ttu-id="e7364-148">Stijlgids voor PowerShell-documentatie</span><span class="sxs-lookup"><span data-stu-id="e7364-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="e7364-149">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="e7364-149">Additional resources</span></span>

[<span data-ttu-id="e7364-150">De manier waarop we pull-aanvragen beheren</span><span class="sxs-lookup"><span data-stu-id="e7364-150">How we manage pull requests</span></span>](managing-pull-requests.md)
