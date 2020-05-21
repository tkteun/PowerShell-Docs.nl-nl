---
title: Bijdragen aan Power shell-documentatie
description: Dit artikel bevat een overzicht van hoe u aan de slag kunt gaan als bijdrager aan de Power shell-documentatie.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 5f9efbff500b1fd0c11e9b43ca0a7feb77684c6a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560658"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="f3651-103">Bijdragen aan Power shell-documentatie</span><span class="sxs-lookup"><span data-stu-id="f3651-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="f3651-104">Hartelijk dank voor uw ondersteuning van Power shell.</span><span class="sxs-lookup"><span data-stu-id="f3651-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="f3651-105">De hand leiding voor inzenders is een verzameling artikelen waarin de hulpprogram ma's en processen worden uitgelegd die we gebruiken om documentatie bij micro soft te maken.</span><span class="sxs-lookup"><span data-stu-id="f3651-105">The Contributor's Guide is a collection of articles that explain the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="f3651-106">Sommige van deze hand leidingen beslaan informatie die gemeen schappelijk is voor elke documentatieset die wordt gepubliceerd op [docs.Microsoft.com][docs].</span><span class="sxs-lookup"><span data-stu-id="f3651-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="f3651-107">Sommige hand leidingen zijn specifiek voor het schrijven van documentatie voor Power shell.</span><span class="sxs-lookup"><span data-stu-id="f3651-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="f3651-108">De gemeen schappelijke artikelen zijn beschikbaar in onze gecentraliseerde [hand leiding voor mede][contribute]werkers.</span><span class="sxs-lookup"><span data-stu-id="f3651-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="f3651-109">De Power shell-specifieke hand leidingen zijn hier beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="f3651-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="f3651-110">Manieren om bij te dragen</span><span class="sxs-lookup"><span data-stu-id="f3651-110">Ways to contribute</span></span>

<span data-ttu-id="f3651-111">Er zijn twee manieren om bij te dragen.</span><span class="sxs-lookup"><span data-stu-id="f3651-111">There are two ways to contribute.</span></span> <span data-ttu-id="f3651-112">Beide bijdragen zijn waardevol voor ons.</span><span class="sxs-lookup"><span data-stu-id="f3651-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="f3651-113">Bij het [archiveren van problemen][file-an-issue] kunnen we problemen en hiaten in onze documentatie identificeren.</span><span class="sxs-lookup"><span data-stu-id="f3651-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="f3651-114">Soms zijn problemen moeilijk op te lossen, waardoor meer onderzoek en onderzoek is vereist.</span><span class="sxs-lookup"><span data-stu-id="f3651-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="f3651-115">Met het probleem proces kan ons een gesprek over het probleem hebben en een bevredigende oplossing ontwikkelen.</span><span class="sxs-lookup"><span data-stu-id="f3651-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="f3651-116">Het verzenden van nieuwe inhoud of wijzigingen in bestaande artikelen is een meer betrokken proces.</span><span class="sxs-lookup"><span data-stu-id="f3651-116">Submitting new content or changes to existing articles is a more involved process.</span></span> <span data-ttu-id="f3651-117">De volgende informatie bevat een overzicht van de hulpprogram ma's, processen en standaarden voor het verzenden van inhoud aan de documentatie.</span><span class="sxs-lookup"><span data-stu-id="f3651-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="f3651-118">Voor bereidingen treffen om een bijdrage te leveren</span><span class="sxs-lookup"><span data-stu-id="f3651-118">Prepare to make a contribution</span></span>

<span data-ttu-id="f3651-119">U hebt allereerst een GitHub-account nodig om bij te dragen aan de documentatie.</span><span class="sxs-lookup"><span data-stu-id="f3651-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="f3651-120">Gebruik de volgende controle lijst om de hulpprogram ma's op te halen en inzicht te krijgen in de processen die we gebruiken om bijdragen te leveren.</span><span class="sxs-lookup"><span data-stu-id="f3651-120">Use the following checklist to get the tools and understand the processes we use for making contributions.</span></span>

1. [<span data-ttu-id="f3651-121">Aanmelden voor GitHub</span><span class="sxs-lookup"><span data-stu-id="f3651-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="f3651-122">Hulpprogramma's voor Git/Markdown installeren</span><span class="sxs-lookup"><span data-stu-id="f3651-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="f3651-123">Het docs-ontwerp pakket installeren</span><span class="sxs-lookup"><span data-stu-id="f3651-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="f3651-124">[Installeer posh-Git][posh-git] -niet vereist maar wordt aanbevolen</span><span class="sxs-lookup"><span data-stu-id="f3651-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="f3651-125">Een lokale Git-opslagplaats instellen</span><span class="sxs-lookup"><span data-stu-id="f3651-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="f3651-126">De basis principes van Git en GitHub controleren</span><span class="sxs-lookup"><span data-stu-id="f3651-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="f3651-127">Aan de slag met het schrijven van documentatie</span><span class="sxs-lookup"><span data-stu-id="f3651-127">Get started writing docs</span></span>

<span data-ttu-id="f3651-128">Er zijn twee manieren om wijzigingen in de documentatie bij te dragen:</span><span class="sxs-lookup"><span data-stu-id="f3651-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="f3651-129">Snelle bewerkingen in bestaande documenten</span><span class="sxs-lookup"><span data-stu-id="f3651-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="f3651-130">Kleine correcties, type fouten corrigeren of kleine toevoegingen</span><span class="sxs-lookup"><span data-stu-id="f3651-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="f3651-131">Volledige GitHub-werk stroom voor docs</span><span class="sxs-lookup"><span data-stu-id="f3651-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="f3651-132">grote wijzigingen, meerdere versies, toevoegen of wijzigen van installatie kopieën, of bijdragen aan nieuwe artikelen</span><span class="sxs-lookup"><span data-stu-id="f3651-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="f3651-133">Lees ook de sectie over het [schrijven van essentiële](/contribute/style-quick-start) elementen van de gecentraliseerde hand leiding voor mede werkers.</span><span class="sxs-lookup"><span data-stu-id="f3651-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="f3651-134">Een andere uitstekende resource is de [micro soft-stijl gids voor schrijven][style-guide].</span><span class="sxs-lookup"><span data-stu-id="f3651-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="f3651-135">Het doel van de micro soft-stijl gids voor schrijven is om editors, technische schrijvers, ontwikkel aars, markt verwerkers en anderen te helpen betere inhoud te schrijven.</span><span class="sxs-lookup"><span data-stu-id="f3651-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="f3651-136">Kleine correcties of verduidelijkingen van documentatie en code voorbeelden in open bare opslag plaatsen vallen onder de [gebruiks voorwaarden van][terms-of-use]docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="f3651-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="f3651-137">Gebruik de volledige GitHub-werk stroom wanneer u belang rijke wijzigingen aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="f3651-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="f3651-138">Als u geen werk nemer van micro soft bent, wordt in belang rijke wijzigingen een opmerking in de pull-aanvraag gegenereerd waarin u wordt gevraagd om een online [contribution License Agreement (CLA)][cla]in te dienen.</span><span class="sxs-lookup"><span data-stu-id="f3651-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="f3651-139">U moet het onlineformulier invullen voordat we uw pull-aanvraag kunnen beoordelen of accepteren.</span><span class="sxs-lookup"><span data-stu-id="f3651-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="f3651-140">Gedragscode</span><span class="sxs-lookup"><span data-stu-id="f3651-140">Code of conduct</span></span>

<span data-ttu-id="f3651-141">Op alle opslagplaatsen die naar docs.microsoft.com publiceren, is de [Microsoft Open Source-gedragscode](https://opensource.microsoft.com/codeofconduct/) of de [.NET Foundation-gedragscode](https://dotnetfoundation.org/code-of-conduct) van toepassing.</span><span class="sxs-lookup"><span data-stu-id="f3651-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="f3651-142">Zie [Veelgestelde vragen over de gedragscode](https://opensource.microsoft.com/codeofconduct/faq/) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f3651-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f3651-143">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="f3651-143">Next steps</span></span>

<span data-ttu-id="f3651-144">De volgende artikelen behandelen informatie die specifiek is afgestemd op Power shell-documentatie.</span><span class="sxs-lookup"><span data-stu-id="f3651-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="f3651-145">Als er een overlap is met de instructies in de hand leiding voor gecentraliseerde Inzender, roepen we uit hoe deze regels verschillen voor de Power shell-inhoud.</span><span class="sxs-lookup"><span data-stu-id="f3651-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="f3651-146">Bekijk de volgende documenten:</span><span class="sxs-lookup"><span data-stu-id="f3651-146">Review the following documents:</span></span>

- [<span data-ttu-id="f3651-147">Een probleem in een bestand opslaan</span><span class="sxs-lookup"><span data-stu-id="f3651-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="f3651-148">Aan de slag met het schrijven van documentatie</span><span class="sxs-lookup"><span data-stu-id="f3651-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="f3651-149">Een pull-aanvraag verzenden</span><span class="sxs-lookup"><span data-stu-id="f3651-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="f3651-150">Stijlgids voor PowerShell-documentatie</span><span class="sxs-lookup"><span data-stu-id="f3651-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)
- [<span data-ttu-id="f3651-151">Naslaginformatie voor cmdlets bewerken</span><span class="sxs-lookup"><span data-stu-id="f3651-151">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<span data-ttu-id="f3651-152">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="f3651-152">Additional resources</span></span>

- [<span data-ttu-id="f3651-153">Redactionele controlelijst</span><span class="sxs-lookup"><span data-stu-id="f3651-153">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="f3651-154">De manier waarop we problemen beheren</span><span class="sxs-lookup"><span data-stu-id="f3651-154">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="f3651-155">De manier waarop we pull-aanvragen beheren</span><span class="sxs-lookup"><span data-stu-id="f3651-155">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: https://docs.microsoft.com/powershell
[style-guide]: https://docs.microsoft.com/style-guide/welcome/
[terms-of-use]: https://docs.microsoft.com/legal/termsofuse
