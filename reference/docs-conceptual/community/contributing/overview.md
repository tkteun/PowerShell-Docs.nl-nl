---
title: Bijdragen aan Power shell-documentatie
description: In dit artikel vindt u een overzicht van de stappen die nodig zijn om aan de Power shell-documentatie te bijdragen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 255b74a75b8412ed509f6da930eb722d54233711
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354399"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="c8e7a-103">Bijdragen aan Power shell-documentatie</span><span class="sxs-lookup"><span data-stu-id="c8e7a-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="c8e7a-104">Hartelijk dank voor uw ondersteuning van Power shell.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="c8e7a-105">De gids voor inzenders is een verzameling artikelen waarin de hulpprogramma's en processen worden uitgelegd die we gebruiken om documentatie bij Microsoft te maken.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-105">The Contributor's Guide is a collection of articles that explain the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="c8e7a-106">Sommige van deze hand leidingen beslaan informatie die gemeen schappelijk is voor elke documentatieset die wordt gepubliceerd op [docs.Microsoft.com][docs].</span><span class="sxs-lookup"><span data-stu-id="c8e7a-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="c8e7a-107">Sommige gidsen zijn specifiek voor het schrijven van documentatie voor PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="c8e7a-108">De gemeen schappelijke artikelen zijn beschikbaar in onze gecentraliseerde [hand leiding voor mede][contribute]werkers.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="c8e7a-109">De Power shell-specifieke hand leidingen zijn hier beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="c8e7a-110">Manieren om bij te dragen</span><span class="sxs-lookup"><span data-stu-id="c8e7a-110">Ways to contribute</span></span>

<span data-ttu-id="c8e7a-111">Er zijn twee manieren om bij te dragen.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-111">There are two ways to contribute.</span></span> <span data-ttu-id="c8e7a-112">Beide bijdragen zijn waardevol voor ons.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="c8e7a-113">Bij het [archiveren van problemen][file-an-issue] kunnen we problemen en hiaten in onze documentatie identificeren.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="c8e7a-114">Soms zijn problemen moeilijk op te lossen, waardoor meer onderzoek en onderzoek is vereist.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="c8e7a-115">Met het probleem proces kan ons een gesprek over het probleem hebben en een bevredigende oplossing ontwikkelen.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="c8e7a-116">Het verzenden van nieuwe inhoud of wijzigingen in bestaande artikelen is een meer betrokken proces.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-116">Submitting new content or changes to existing articles is a more involved process.</span></span> <span data-ttu-id="c8e7a-117">De volgende informatie bevat een overzicht van de hulpprogram ma's, processen en standaarden voor het verzenden van inhoud aan de documentatie.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="c8e7a-118">Voor bereidingen treffen om een bijdrage te leveren</span><span class="sxs-lookup"><span data-stu-id="c8e7a-118">Prepare to make a contribution</span></span>

<span data-ttu-id="c8e7a-119">U hebt allereerst een GitHub-account nodig om bij te dragen aan de documentatie.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="c8e7a-120">Gebruik de volgende controle lijst om de hulpprogram ma's op te halen en inzicht te krijgen in de processen die we gebruiken om bijdragen te leveren.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-120">Use the following checklist to get the tools and understand the processes we use for making contributions.</span></span>

1. [<span data-ttu-id="c8e7a-121">Registreren voor GitHub</span><span class="sxs-lookup"><span data-stu-id="c8e7a-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="c8e7a-122">Hulpprogramma's voor Git/Markdown installeren</span><span class="sxs-lookup"><span data-stu-id="c8e7a-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="c8e7a-123">Het docs-ontwerp pakket installeren</span><span class="sxs-lookup"><span data-stu-id="c8e7a-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="c8e7a-124">[Installeer posh-Git][posh-git] -niet vereist maar wordt aanbevolen</span><span class="sxs-lookup"><span data-stu-id="c8e7a-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="c8e7a-125">Een lokale Git-opslagplaats instellen</span><span class="sxs-lookup"><span data-stu-id="c8e7a-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="c8e7a-126">De basis principes van Git en GitHub controleren</span><span class="sxs-lookup"><span data-stu-id="c8e7a-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="c8e7a-127">Aan de slag met het schrijven van documentatie</span><span class="sxs-lookup"><span data-stu-id="c8e7a-127">Get started writing docs</span></span>

<span data-ttu-id="c8e7a-128">Er zijn twee manieren om wijzigingen in de documentatie bij te dragen:</span><span class="sxs-lookup"><span data-stu-id="c8e7a-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="c8e7a-129">Snelle bewerkingen in bestaande documenten</span><span class="sxs-lookup"><span data-stu-id="c8e7a-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="c8e7a-130">Kleine correcties, type fouten corrigeren of kleine toevoegingen</span><span class="sxs-lookup"><span data-stu-id="c8e7a-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="c8e7a-131">Volledige GitHub-werk stroom voor docs</span><span class="sxs-lookup"><span data-stu-id="c8e7a-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="c8e7a-132">grote wijzigingen, meerdere versies, toevoegen of wijzigen van installatie kopieën, of bijdragen aan nieuwe artikelen</span><span class="sxs-lookup"><span data-stu-id="c8e7a-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="c8e7a-133">Lees ook de sectie over het [schrijven van essentiële](/contribute/style-quick-start) elementen van de gecentraliseerde hand leiding voor mede werkers.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="c8e7a-134">Een andere uitstekende resource is de [micro soft-stijl gids voor schrijven][style-guide].</span><span class="sxs-lookup"><span data-stu-id="c8e7a-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="c8e7a-135">Het doel van de micro soft-stijl gids voor schrijven is om editors, technische schrijvers, ontwikkel aars, markt verwerkers en anderen te helpen betere inhoud te schrijven.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="c8e7a-136">Kleine correcties of verduidelijkingen van documentatie en code voorbeelden in open bare opslag plaatsen vallen onder de [gebruiks voorwaarden van][terms-of-use]docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="c8e7a-137">Gebruik de volledige GitHub-werk stroom wanneer u belang rijke wijzigingen aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="c8e7a-138">Als u geen werk nemer van micro soft bent, wordt in belang rijke wijzigingen een opmerking in de pull-aanvraag gegenereerd waarin u wordt gevraagd om een online [contribution License Agreement (CLA)][cla]in te dienen.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="c8e7a-139">U moet het onlineformulier invullen voordat we uw pull-aanvraag kunnen beoordelen of accepteren.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="c8e7a-140">Gedragscode</span><span class="sxs-lookup"><span data-stu-id="c8e7a-140">Code of conduct</span></span>

<span data-ttu-id="c8e7a-141">Op alle opslagplaatsen die naar docs.microsoft.com publiceren, is de [Microsoft Open Source-gedragscode](https://opensource.microsoft.com/codeofconduct/) of de [.NET Foundation-gedragscode](https://dotnetfoundation.org/code-of-conduct) van toepassing.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="c8e7a-142">Zie [Veelgestelde vragen over de gedragscode](https://opensource.microsoft.com/codeofconduct/faq/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8e7a-143">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="c8e7a-143">Next steps</span></span>

<span data-ttu-id="c8e7a-144">De volgende artikelen behandelen informatie die specifiek is afgestemd op Power shell-documentatie.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="c8e7a-145">Als er een overlap is met de instructies in de hand leiding voor gecentraliseerde Inzender, roepen we uit hoe deze regels verschillen voor de Power shell-inhoud.</span><span class="sxs-lookup"><span data-stu-id="c8e7a-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="c8e7a-146">Bekijk de volgende documenten:</span><span class="sxs-lookup"><span data-stu-id="c8e7a-146">Review the following documents:</span></span>

- [<span data-ttu-id="c8e7a-147">Een probleem in een bestand opslaan</span><span class="sxs-lookup"><span data-stu-id="c8e7a-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="c8e7a-148">Aan de slag met het schrijven van documentatie</span><span class="sxs-lookup"><span data-stu-id="c8e7a-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="c8e7a-149">Een pull-aanvraag verzenden</span><span class="sxs-lookup"><span data-stu-id="c8e7a-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="c8e7a-150">Stijlgids voor PowerShell-documentatie</span><span class="sxs-lookup"><span data-stu-id="c8e7a-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)
- [<span data-ttu-id="c8e7a-151">Naslaginformatie voor cmdlets bewerken</span><span class="sxs-lookup"><span data-stu-id="c8e7a-151">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<span data-ttu-id="c8e7a-152">Aanvullende resources</span><span class="sxs-lookup"><span data-stu-id="c8e7a-152">Additional resources</span></span>

- [<span data-ttu-id="c8e7a-153">Redactionele controlelijst</span><span class="sxs-lookup"><span data-stu-id="c8e7a-153">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="c8e7a-154">De manier waarop we problemen beheren</span><span class="sxs-lookup"><span data-stu-id="c8e7a-154">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="c8e7a-155">De manier waarop we pull-aanvragen beheren</span><span class="sxs-lookup"><span data-stu-id="c8e7a-155">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
