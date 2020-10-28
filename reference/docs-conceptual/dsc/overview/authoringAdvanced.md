---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Informatie over de rol van DSC in een CI/CD-pijp lijn
description: In dit artikel worden de soorten benaderingen beschreven die beschikbaar zijn voor het combi neren van configuraties en resources in een CI/CD-pijp lijn.
ms.openlocfilehash: 8d06b86724eb25e657687e6518c01bb29d984264
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647029"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="b8165-104">Informatie over de rol van DSC in een CI/CD-pijp lijn</span><span class="sxs-lookup"><span data-stu-id="b8165-104">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="b8165-105">In dit artikel worden de soorten benaderingen beschreven die beschikbaar zijn voor het combi neren van configuraties en resources.</span><span class="sxs-lookup"><span data-stu-id="b8165-105">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="b8165-106">Het doel van elk scenario is hetzelfde, om de complexiteit te reduceren wanneer meerdere configuraties de voor keur hebben om de eind status van de server implementatie te bereiken.</span><span class="sxs-lookup"><span data-stu-id="b8165-106">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span> <span data-ttu-id="b8165-107">Een voor beeld hiervan is dat meerdere teams bijdragen aan het resultaat van een server implementatie, zoals een toepassings eigenaar die de toepassings status bijhoudt en een centraal team wijzigingen in de beveiligings basislijnen aanbrengt.</span><span class="sxs-lookup"><span data-stu-id="b8165-107">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span> <span data-ttu-id="b8165-108">De nuances van elke benadering, met inbegrip van de voor delen en risico's, worden hier beschreven.</span><span class="sxs-lookup"><span data-stu-id="b8165-108">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Proces stroom van een CI/CD-pijp lijn](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="b8165-110">Typen technieken voor gezamenlijk ontwerpen</span><span class="sxs-lookup"><span data-stu-id="b8165-110">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="b8165-111">Er zijn twee oplossingen ingebouwd in lokale Configuration Manager om dit concept in te scha kelen:</span><span class="sxs-lookup"><span data-stu-id="b8165-111">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

|        <span data-ttu-id="b8165-112">Concept</span><span class="sxs-lookup"><span data-stu-id="b8165-112">Concept</span></span>         |                    <span data-ttu-id="b8165-113">Gedetailleerde informatie</span><span class="sxs-lookup"><span data-stu-id="b8165-113">Detailed Information</span></span>                     |
| ---------------------- | ----------------------------------------------------------- |
| <span data-ttu-id="b8165-114">Gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="b8165-114">Partial Configurations</span></span> | [<span data-ttu-id="b8165-115">Documentatie</span><span class="sxs-lookup"><span data-stu-id="b8165-115">Documentation</span></span>](../pull-server/partialConfigs.md)           |
| <span data-ttu-id="b8165-116">Samengestelde resources</span><span class="sxs-lookup"><span data-stu-id="b8165-116">Composite Resources</span></span>    | [<span data-ttu-id="b8165-117">Documentatie</span><span class="sxs-lookup"><span data-stu-id="b8165-117">Documentation</span></span>](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="b8165-118">Het effect van elke benadering</span><span class="sxs-lookup"><span data-stu-id="b8165-118">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="b8165-119">Een van deze oplossingen kan worden gebruikt om het resultaat van een server implementatie te beheren.</span><span class="sxs-lookup"><span data-stu-id="b8165-119">Either of these solutions can be used to manage the outcome of a server deployment.</span></span> <span data-ttu-id="b8165-120">Er is echter een aanzienlijk verschil in de impact van het gebruik van elke benadering.</span><span class="sxs-lookup"><span data-stu-id="b8165-120">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="b8165-121">Gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="b8165-121">Partial Configurations</span></span>

<span data-ttu-id="b8165-122">Bij het gebruik van gedeeltelijke configuraties is lokale Configuration Manager geconfigureerd om meerdere configuraties onafhankelijk te beheren.</span><span class="sxs-lookup"><span data-stu-id="b8165-122">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span> <span data-ttu-id="b8165-123">Configuraties worden onafhankelijk gecompileerd en vervolgens toegewezen aan het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="b8165-123">Configurations are compiled independently and then assigned to the node.</span></span> <span data-ttu-id="b8165-124">Hiervoor moet LCM vooraf worden geconfigureerd met de naam van elke configuratie.</span><span class="sxs-lookup"><span data-stu-id="b8165-124">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![Diagram van gedeeltelijke configuraties](media/authoringAdvanced/PartialConfiguration.jpg)

<span data-ttu-id="b8165-126">Gedeeltelijke configuraties bieden twee of meer teams die de configuratie van een server volledig kunnen beheren, vaak zonder het voor deel van communicatie of samen werking.</span><span class="sxs-lookup"><span data-stu-id="b8165-126">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="b8165-127">Klanten hebben feedback gegeven die dit kan leiden tot bron conflicten, onbedoelde onderdrukkingen en uiteindelijk verlies van echte configuratie beheer van de Asset.</span><span class="sxs-lookup"><span data-stu-id="b8165-127">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="b8165-128">Daarnaast hebben klanten feedback gegeven die bij het gebruik van dit model de configuratie wijzigingen van teams beheert waarschijnlijk niet volledig worden getest via een release pijplijn, waardoor onverwachte resultaten ontstaan bij de productie.</span><span class="sxs-lookup"><span data-stu-id="b8165-128">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="b8165-129">**Het is essentieel dat één pijp lijn wordt gebruikt voor het evalueren van alle wijzigingen die zijn uitgebracht op servers.**</span><span class="sxs-lookup"><span data-stu-id="b8165-129">**It is critical that a single pipeline be used to evaluate all changes released to servers.**</span></span>

<span data-ttu-id="b8165-130">In de onderstaande afbeelding heeft Team B hun gedeeltelijke configuratie vrijgegeven aan team A. team A voert vervolgens hun tests uit op een server waarop beide configuraties zijn toegepast.</span><span class="sxs-lookup"><span data-stu-id="b8165-130">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span> <span data-ttu-id="b8165-131">In dit model is slechts één instantie gemachtigd om wijzigingen aan te brengen in de productie.</span><span class="sxs-lookup"><span data-stu-id="b8165-131">In this model, only one authority has permission to make changes in production.</span></span>

![Diagram van een gedeeltelijke enkele pijp lijn](media/authoringAdvanced/PartialSinglePipeline.jpg)

<span data-ttu-id="b8165-133">Als er wijzigingen zijn vereist van Team B, moeten ze een pull-aanvraag indienen bij de bron beheer omgeving van team A.</span><span class="sxs-lookup"><span data-stu-id="b8165-133">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span> <span data-ttu-id="b8165-134">Team A bekijkt vervolgens de wijzigingen met behulp van test automatisering en release to Production wanneer er betrouw baarheid is dat de wijzigingen geen fouten veroorzaken in de toepassingen of services die door de server worden gehost.</span><span class="sxs-lookup"><span data-stu-id="b8165-134">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="b8165-135">Samengestelde resources</span><span class="sxs-lookup"><span data-stu-id="b8165-135">Composite Resources</span></span>

<span data-ttu-id="b8165-136">Een samengestelde resource is een DSC-configuratie die is verpakt als een resource.</span><span class="sxs-lookup"><span data-stu-id="b8165-136">A composite resource is simply a DSC Configuration packaged as a resource.</span></span> <span data-ttu-id="b8165-137">Er zijn geen speciale vereisten voor het configureren van LCM om samengestelde resources te accepteren.</span><span class="sxs-lookup"><span data-stu-id="b8165-137">There are no special requirements for configuring LCM to accept composite resources.</span></span> <span data-ttu-id="b8165-138">De resources worden gebruikt binnen een nieuwe configuratie en een enkele compilatie resulteert in één MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="b8165-138">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![Diagram van een samengestelde resource](media/authoringAdvanced/CompositeResource.jpg)

<span data-ttu-id="b8165-140">Er zijn twee veelvoorkomende scenario's voor samengestelde resources.</span><span class="sxs-lookup"><span data-stu-id="b8165-140">There are two common scenarios for composite resources.</span></span> <span data-ttu-id="b8165-141">De eerste is om complexiteit en abstracte unieke concepten te reduceren.</span><span class="sxs-lookup"><span data-stu-id="b8165-141">The first is to reduce complexity and abstract unique concepts.</span></span> <span data-ttu-id="b8165-142">De tweede is om toe te staan dat basis lijnen worden verpakt zodat een toepassings team veilig kan worden geïmplementeerd via hun release pijplijn tot productie nadat alle tests zijn geslaagd.</span><span class="sxs-lookup"><span data-stu-id="b8165-142">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

<span data-ttu-id="b8165-143">Samengestelde resources bevorderen zowel samen stelling als samen werking met behulp van een pijp lijn tijdens het bouwen van een operationele loop tijd.</span><span class="sxs-lookup"><span data-stu-id="b8165-143">Composite resources promote both composition and collaboration using a pipeline while building operational maturity.</span></span>

<span data-ttu-id="b8165-144">Mogelijk maakt u al gebruik van samengestelde resources zonder deze te realiseren.</span><span class="sxs-lookup"><span data-stu-id="b8165-144">You might be already using composite resources without realizing it.</span></span> <span data-ttu-id="b8165-145">Een voor beeld is **serviceset** .</span><span class="sxs-lookup"><span data-stu-id="b8165-145">An example is **ServiceSet** .</span></span>
<span data-ttu-id="b8165-146">Deze resource beheert de status van meerdere Windows-Services zonder deze afzonderlijk te hoeven aanbieden.</span><span class="sxs-lookup"><span data-stu-id="b8165-146">This resource manages the state of multiple Windows Services without listing them individually.</span></span> <span data-ttu-id="b8165-147">De eigenschap name accepteert een matrix met teken reeksen om de naam van elke service op te geven.</span><span class="sxs-lookup"><span data-stu-id="b8165-147">The Name property accepts an array of strings to provide the name of each service.</span></span> <span data-ttu-id="b8165-148">Wanneer de configuratie is gecompileerd, bevat de MOF een unieke service sectie voor elk van de namen die worden door gegeven aan serviceset.</span><span class="sxs-lookup"><span data-stu-id="b8165-148">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="b8165-149">Organisaties kunnen "agents" of "middleware" hebben die op elke server moeten worden geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b8165-149">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span> <span data-ttu-id="b8165-150">Een samengestelde resource is het beste antwoord op het beheren van de afhankelijkheden, het instellen en configureren van dergelijke hulpprogram ma's en hulpprogram ma's.</span><span class="sxs-lookup"><span data-stu-id="b8165-150">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="b8165-151">De persoon of het team dat verantwoordelijk is voor oplossingen die meerdere servers beslaan, is een configuratie met hun vereisten.</span><span class="sxs-lookup"><span data-stu-id="b8165-151">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span> <span data-ttu-id="b8165-152">Vervolgens wordt de configuratie gebundeld als een samengestelde resource met behulp van de instructies in de documentatie voor de samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="b8165-152">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span> <span data-ttu-id="b8165-153">Ten slotte moet de nieuwe samengestelde resource worden gepubliceerd op een locatie zoals een bestands share of NuGet feed waar toepassings teams deze kunnen gebruiken in hun configuraties.</span><span class="sxs-lookup"><span data-stu-id="b8165-153">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="b8165-154">Telkens wanneer het team een nieuwe versie loslaat, wordt het versie nummer in het module manifest voor de samengestelde resource verhoogd.</span><span class="sxs-lookup"><span data-stu-id="b8165-154">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span> <span data-ttu-id="b8165-155">De toepassings teams bevatten de samengestelde resource in de configuratie die ze ontwerpen voor het beheren van toepassings afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="b8165-155">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span> <span data-ttu-id="b8165-156">Wanneer de operations/Security-teams een nieuwe versie van hun resource vrijgeven, melden ze de toepassings teams van een nieuwe wijziging.</span><span class="sxs-lookup"><span data-stu-id="b8165-156">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="b8165-157">De toepassings teams kunnen een vrijgave voor productie activeren waarbij alleen de basis lijnen worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b8165-157">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="b8165-158">Dit biedt echter een kans om de impact op toepassingen te evalueren voordat het risico op een service storing optreedt.</span><span class="sxs-lookup"><span data-stu-id="b8165-158">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

> [!NOTE]
> <span data-ttu-id="b8165-159">Feedback over het gebruik van samengestelde resources bevat criticism die wijzigingen aanbrengen vereist het compileren en uitgeven van een nieuwe MOF.</span><span class="sxs-lookup"><span data-stu-id="b8165-159">Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span> <span data-ttu-id="b8165-160">Dit is standaard.</span><span class="sxs-lookup"><span data-stu-id="b8165-160">This is by design.</span></span> <span data-ttu-id="b8165-161">Elke nieuwe configuratie release moet een statische verwijzing naar een specifieke versie van elke resource bevatten en moet worden gevalideerd door tests voordat productie server knooppunten worden bereikt.</span><span class="sxs-lookup"><span data-stu-id="b8165-161">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span> <span data-ttu-id="b8165-162">Het proces van het testen en vrijgeven van wijzigingen van broncode beheer maakt een veilige omgeving voor het vrijgeven van wijzigingen in kleine, maar veelvuldige batches.</span><span class="sxs-lookup"><span data-stu-id="b8165-162">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="b8165-163">Meer informatie over het gebruik van release pijplijnen voor het beheren van de basis infrastructuur vindt u in het Witboek: [het pipeline-model voor de release](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="b8165-163">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
