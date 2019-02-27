---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Informatie over de DSC-rol in een CI/CD-pijplijn
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803375"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a><span data-ttu-id="26e19-103">Informatie over de DSC-rol in een CI/CD-pijplijn</span><span class="sxs-lookup"><span data-stu-id="26e19-103">Understanding DSC's role in a CI/CD pipeline</span></span>

<span data-ttu-id="26e19-104">Dit artikel beschrijft de soorten methoden voor het combineren van configuraties en resources.</span><span class="sxs-lookup"><span data-stu-id="26e19-104">This article describes the types of approaches available for combining configurations and resources.</span></span>
<span data-ttu-id="26e19-105">Het doel voor elk scenario is hetzelfde, te verminderen van complexiteit wanneer meerdere configuraties voorkeur een server end Implementatiestatus bereiken.</span><span class="sxs-lookup"><span data-stu-id="26e19-105">The goal for each scenario is the same, to reduce complexity when multiple configurations are preferred to reach a server deployment end state.</span></span>
<span data-ttu-id="26e19-106">Een voorbeeld hiervan is meerdere teams die bijdragen aan het resultaat van een server-implementatie, zoals de eigenaar van een toepassing status van de toepassing en een centraal team brengt wijzigingen aan basisbeveiliging gehandhaafd blijft.</span><span class="sxs-lookup"><span data-stu-id="26e19-106">An example of this would be multiple teams contributing to the outcome of a server deployment, such as an application owner maintaining the application state and a central team releasing changes to security baselines.</span></span>
<span data-ttu-id="26e19-107">De aspecten van elke methode met inbegrip van de voordelen en risico's, worden hier beschreven.</span><span class="sxs-lookup"><span data-stu-id="26e19-107">The nuances of each approach including the benefits and risks are detailed here.</span></span>

![Pijplijn](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a><span data-ttu-id="26e19-109">Typen gezamenlijke Authoring technieken</span><span class="sxs-lookup"><span data-stu-id="26e19-109">Types of Collaborative Authoring Techniques</span></span>

<span data-ttu-id="26e19-110">Er zijn twee oplossingen die zijn ingebouwd in Local Configuration Manager zodat dit concept:</span><span class="sxs-lookup"><span data-stu-id="26e19-110">There are two solutions built in to Local Configuration Manager to enable this concept:</span></span>

| <span data-ttu-id="26e19-111">Concept</span><span class="sxs-lookup"><span data-stu-id="26e19-111">Concept</span></span> | <span data-ttu-id="26e19-112">Gedetailleerde informatie</span><span class="sxs-lookup"><span data-stu-id="26e19-112">Detailed Information</span></span>
|-|-
| <span data-ttu-id="26e19-113">Gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="26e19-113">Partial Configurations</span></span> | [<span data-ttu-id="26e19-114">Documentatie</span><span class="sxs-lookup"><span data-stu-id="26e19-114">Documentation</span></span>](../pull-server/partialConfigs.md)
| <span data-ttu-id="26e19-115">Samengestelde Resources</span><span class="sxs-lookup"><span data-stu-id="26e19-115">Composite Resources</span></span> | [<span data-ttu-id="26e19-116">Documentatie</span><span class="sxs-lookup"><span data-stu-id="26e19-116">Documentation</span></span>](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a><span data-ttu-id="26e19-117">De invloed van elke methode</span><span class="sxs-lookup"><span data-stu-id="26e19-117">Understanding The Impact of Each Approach</span></span>

<span data-ttu-id="26e19-118">Een van deze oplossingen kan worden gebruikt voor het beheren van de uitkomst van een server-implementatie.</span><span class="sxs-lookup"><span data-stu-id="26e19-118">Either of these solutions can be used to manage the outcome of a server deployment.</span></span>
<span data-ttu-id="26e19-119">Er is echter aanzienlijk verschil zijn in de gevolgen van het gebruik van elke methode.</span><span class="sxs-lookup"><span data-stu-id="26e19-119">However, there is significant difference in the impact of using each approach.</span></span>

## <a name="partial-configurations"></a><span data-ttu-id="26e19-120">Gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="26e19-120">Partial Configurations</span></span>

<span data-ttu-id="26e19-121">Bij het gebruik van gedeeltelijke configuraties worden Local Configuration Manager is geconfigureerd voor het beheren van configuraties met meerdere onafhankelijk van elkaar.</span><span class="sxs-lookup"><span data-stu-id="26e19-121">When using Partial Configurations, Local Configuration Manager is configured to manage multiple configurations independently.</span></span>
<span data-ttu-id="26e19-122">Configuraties worden gecompileerd onafhankelijk en vervolgens toegewezen aan het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="26e19-122">Configurations are compiled independently and then assigned to the node.</span></span>
<span data-ttu-id="26e19-123">Dit vereist LCM vooraf worden geconfigureerd met de naam van elke configuratie.</span><span class="sxs-lookup"><span data-stu-id="26e19-123">This requires LCM to be configured in advance with the name of each configuration.</span></span>

![PartialConfiguration](../images/PartialConfiguration.jpg)

<span data-ttu-id="26e19-125">Gedeeltelijke configuraties bieden twee of meer teams volledige controle over configuratie van een server, vaak zonder het voordeel van de communicatieservices of samenwerkingsservices.</span><span class="sxs-lookup"><span data-stu-id="26e19-125">Partial Configurations provide two, or more, teams complete control over configuration of a server, often without the benefit of communication or collaboration.</span></span>

<span data-ttu-id="26e19-126">Feedback die dit tot bronconflicten, onbedoelde onderdrukkingen en uiteindelijk verlies van true Configuratiebeheer van de activa leiden kan van klanten hebt gegeven.</span><span class="sxs-lookup"><span data-stu-id="26e19-126">Customers have provided feedback that this can lead to resource conflicts, unintentional overrides, and ultimately loss of true configuration control of the asset.</span></span>

<span data-ttu-id="26e19-127">Bovendien hebben klanten feedback dat wanneer u dit model, elke beheren teams configuratiewijzigingen waarschijnlijk niet volledig worden getest via een release-pijplijn, die leiden tot onverwachte resultaten in de productieomgeving.</span><span class="sxs-lookup"><span data-stu-id="26e19-127">Additionally, customers have provided feedback that when using this model, each controlling teams configuration changes are unlikely to be fully tested through a release pipeline, leading to unexpected results in production.</span></span>

<span data-ttu-id="26e19-128">**Het is essentieel dat één pijplijn worden gebruikt voor het evalueren van alle wijzigingen release op servers.**</span><span class="sxs-lookup"><span data-stu-id="26e19-128">**It is critical that a single pipeline be used to evaluate all changes release to servers.**</span></span>

<span data-ttu-id="26e19-129">In de onderstaande afbeelding Team B hun Team A. Team een gedeeltelijke configuratie worden vrijgegeven en vervolgens wordt de tests uitgevoerd op een server met beide configuraties toegepast.</span><span class="sxs-lookup"><span data-stu-id="26e19-129">In the illustration below, Team B releases their partial configuration to Team A. Team A then runs their tests against a server with both configurations applied.</span></span>
<span data-ttu-id="26e19-130">In dit model is slechts één instantie gemachtigd wijzigingen aanbrengen in de productieomgeving.</span><span class="sxs-lookup"><span data-stu-id="26e19-130">In this model, only one authority has permission to make changes in production.</span></span>

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

<span data-ttu-id="26e19-132">Wanneer er wijzigingen nodig uit de B-Team zijn, dienen ze een Pull-aanvragen op basis van Team van een besturingselement bronomgeving.</span><span class="sxs-lookup"><span data-stu-id="26e19-132">When changes are required from Team B, they should submit a Pull Request against Team A's source control environment.</span></span>
<span data-ttu-id="26e19-133">Team een zou vervolgens Bekijk de wijzigingen met behulp van test automation en vrijgeven naar productie wanneer er vertrouwen te geven dat de wijzigingen niet leiden fouten in de toepassingen of services die worden gehost door de server tot.</span><span class="sxs-lookup"><span data-stu-id="26e19-133">Team A would then review the changes using test automation and release to production when there is confidence that the changes will not cause errors in the applications or services hosted by the server.</span></span>

## <a name="composite-resources"></a><span data-ttu-id="26e19-134">Samengestelde Resources</span><span class="sxs-lookup"><span data-stu-id="26e19-134">Composite Resources</span></span>

<span data-ttu-id="26e19-135">Een samengestelde resource is gewoon een DSC-configuratie die zijn verpakt als een resource.</span><span class="sxs-lookup"><span data-stu-id="26e19-135">A composite resource is simply a DSC Configuration packaged as a resource.</span></span>
<span data-ttu-id="26e19-136">Er zijn geen speciale vereisten voor het configureren van LCM samengestelde resources accepteren.</span><span class="sxs-lookup"><span data-stu-id="26e19-136">There are no special requirements for configuring LCM to accept composite resources.</span></span>
<span data-ttu-id="26e19-137">De resources worden gebruikt in een nieuwe configuratie en een enkele compilatie resulteert in een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="26e19-137">The resources are used within a new configuration and a single compilation results in one MOF file.</span></span>

![CompositeResource](../images/CompositeResource.jpg)

<span data-ttu-id="26e19-139">Er zijn twee algemene scenario's voor samengestelde resources.</span><span class="sxs-lookup"><span data-stu-id="26e19-139">There are two common scenarios for composite resources.</span></span>
<span data-ttu-id="26e19-140">De eerste is complex en abstracte unieke concepten te verminderen.</span><span class="sxs-lookup"><span data-stu-id="26e19-140">The first is to reduce complexity and abstract unique concepts.</span></span>
<span data-ttu-id="26e19-141">De tweede is om toe te staan basislijnen om te worden verpakt voor een team van toepassing voor het veilig implementeren via hun release-pijplijn naar productie nadat alle tests zijn geslaagd.</span><span class="sxs-lookup"><span data-stu-id="26e19-141">The second is to allow baselines to be packaged for an application team to safely deploy through their release pipeline to production after all tests have passed.</span></span>

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

<span data-ttu-id="26e19-142">Samengestelde resources bevordering van zowel de samenstelling en de samenwerking met behulp van een pijplijn tijdens het maken van operationele vervaldatum</span><span class="sxs-lookup"><span data-stu-id="26e19-142">Composite resources promote both composition and collaboration using a pipeline while building operational maturity</span></span>

<span data-ttu-id="26e19-143">U mogelijk al gebruikt samengestelde resources gerust.</span><span class="sxs-lookup"><span data-stu-id="26e19-143">You might be already using composite resources without realizing it.</span></span>
<span data-ttu-id="26e19-144">Een voorbeeld is **ServiceSet**.</span><span class="sxs-lookup"><span data-stu-id="26e19-144">An example is **ServiceSet**.</span></span>
<span data-ttu-id="26e19-145">Deze resource beheert de status van meerdere Windows-Services zonder dat ze afzonderlijk.</span><span class="sxs-lookup"><span data-stu-id="26e19-145">This resource manages the state of multiple Windows Services without listing them individually.</span></span>
<span data-ttu-id="26e19-146">De eigenschap Name accepteert een matrix met tekenreeksen met de naam van elke service op te geven.</span><span class="sxs-lookup"><span data-stu-id="26e19-146">The Name property accepts an array of strings to provide the name of each service.</span></span>
<span data-ttu-id="26e19-147">Wanneer de configuratie wordt gecompileerd, bevat het MOF voor elk van de namen die is doorgegeven aan ServiceSet een unieke Service-sectie.</span><span class="sxs-lookup"><span data-stu-id="26e19-147">When the configuration is compiled, the MOF will contain a unique Service section for each of the Names passed to ServiceSet.</span></span>

<span data-ttu-id="26e19-148">Organisaties mogelijk 'agents' of 'middleware' die moet worden geïnstalleerd op elke server.</span><span class="sxs-lookup"><span data-stu-id="26e19-148">Organizations might have "agents" or "middleware" that should be installed on every server.</span></span>
<span data-ttu-id="26e19-149">Een samengestelde resource is het beste antwoord voor het beheren van de afhankelijkheden, instellingen en configuratie van deze hulpprogramma's en hulpprogramma's.</span><span class="sxs-lookup"><span data-stu-id="26e19-149">A composite resource is the best answer to managing the dependencies, setup, and configuration of any such tools and utilities.</span></span>

<span data-ttu-id="26e19-150">De persoon die of het team dat verantwoordelijk is voor oplossingen waarbij meerdere servers omvatten ontwikkelt een configuratie met de vereisten.</span><span class="sxs-lookup"><span data-stu-id="26e19-150">The person or team responsible for solutions that span multiple servers authors a configuration containing their requirements.</span></span>
<span data-ttu-id="26e19-151">Vervolgens zou de configuratie worden geleverd als een samengestelde resource met behulp van instructies hiervoor vindt u in de documentatie van samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="26e19-151">Next, the configuration would be packaged as a composite resource using instructions provided in the composite resource documentation.</span></span>
<span data-ttu-id="26e19-152">Ten slotte de nieuwe samengestelde resource moet worden gepubliceerd naar een locatie zoals een bestandsshare of NuGet feed toepassingsteams waar deze kan gebruiken in hun configuraties.</span><span class="sxs-lookup"><span data-stu-id="26e19-152">Finally, the new composite resource should be published to a location such as a file share or NuGet feed where application teams can consume it in their configurations.</span></span>

<span data-ttu-id="26e19-153">Telkens wanneer die het team een nieuwe versie geeft, zouden ze Verhoog het versienummer in de module-manifest voor de samengestelde resource.</span><span class="sxs-lookup"><span data-stu-id="26e19-153">Each time the team releases a new version, they would increment the version number in the module manifest for their composite resource.</span></span>
<span data-ttu-id="26e19-154">De App-teams omvatten de samengestelde resource in de configuratie die ze zelf voor het beheren van afhankelijkheden voor toepassingen.</span><span class="sxs-lookup"><span data-stu-id="26e19-154">The application teams include the composite resource in the configuration they author for managing application dependencies.</span></span>
<span data-ttu-id="26e19-155">Wanneer de Operations-/ beveiligingsteams een nieuwe versie van de resource kennis ze de App-teams van een nieuwe wijziging.</span><span class="sxs-lookup"><span data-stu-id="26e19-155">When the Operations/Security teams release a new version of their resource, they notify the application teams of a new change.</span></span>

<span data-ttu-id="26e19-156">De App-teams mogelijk een release naar productie waarop de enige wijziging basislijnen wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="26e19-156">The application teams might trigger a release to production where the only change is to baselines.</span></span>
<span data-ttu-id="26e19-157">Dit biedt echter een kans om te evalueren van invloed op toepassingen voordat het risico van een serviceonderbreking.</span><span class="sxs-lookup"><span data-stu-id="26e19-157">However, this provides an opportunity to evaluate impact to applications before risk of a service outage.</span></span>

<span data-ttu-id="26e19-158">Houd er rekening mee - Feedback over het gebruik van samengestelde resources is kritiek dat u wijzigingen vereist compileren en het vrijgeven van een nieuwe MOF opgenomen.</span><span class="sxs-lookup"><span data-stu-id="26e19-158">Note - Feedback regarding the use of composite resources has included criticism that making changes requires compiling and releasing a new MOF.</span></span>
<span data-ttu-id="26e19-159">Dit vindt standaard plaats.</span><span class="sxs-lookup"><span data-stu-id="26e19-159">This is by design.</span></span>
<span data-ttu-id="26e19-160">Elke nieuwe versie van de configuratie van een statische verwijzing naar een specifieke versie van elke resource moet bevatten en moet worden gevalideerd door testen alvorens productie serverknooppunten.</span><span class="sxs-lookup"><span data-stu-id="26e19-160">Each new configuration release should include a static reference to a specific version of each resource, and should be validated by tests before reaching production server nodes.</span></span>
<span data-ttu-id="26e19-161">Het proces van het testen en brengt wijzigingen vanuit broncodebeheer Hiermee maakt u een veilige omgeving voor het vrijgeven van de wijziging in kleine, maar vaak batches.</span><span class="sxs-lookup"><span data-stu-id="26e19-161">The process of testing and releasing changes from source control creates a safe environment for releasing change in small but frequent batches.</span></span>

<span data-ttu-id="26e19-162">Zie het technische document voor meer informatie over het gebruik van de release-pijplijnen voor het beheren van infrastructuur: [Het Model van de pijplijn Release](../further-reading/whitepapers.md).</span><span class="sxs-lookup"><span data-stu-id="26e19-162">For more information about using release pipelines to manage core infrastructure, see the whitepaper: [The Release Pipeline Model](../further-reading/whitepapers.md).</span></span>
