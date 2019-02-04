---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Best practices voor pull-servers
ms.openlocfilehash: da67f8fd793878b097ffb260afad0fcf5c69bb04
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686675"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="dfd1c-103">Best practices voor pull-servers</span><span class="sxs-lookup"><span data-stu-id="dfd1c-103">Pull server best practices</span></span>

<span data-ttu-id="dfd1c-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="dfd1c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dfd1c-105">De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="dfd1c-106">Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="dfd1c-107">Samenvatting: Dit document is bedoeld om op te nemen proces en uitbreidbaarheid voor de ondersteuning van technici die zijn voorbereid voor de oplossing.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="dfd1c-108">Details dient aanbevolen procedures aangeduid met de klanten en vervolgens worden gevalideerd door het productteam om te controleren of aanbevelingen toekomstige gericht zijn en als stabiel beschouwd.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="dfd1c-109">Informatie over dit document</span><span class="sxs-lookup"><span data-stu-id="dfd1c-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="dfd1c-110">De auteur</span><span class="sxs-lookup"><span data-stu-id="dfd1c-110">Author</span></span> | <span data-ttu-id="dfd1c-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="dfd1c-111">Michael Greene</span></span>
<span data-ttu-id="dfd1c-112">Revisoren</span><span class="sxs-lookup"><span data-stu-id="dfd1c-112">Reviewers</span></span> | <span data-ttu-id="dfd1c-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="dfd1c-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="dfd1c-114">Gepubliceerd</span><span class="sxs-lookup"><span data-stu-id="dfd1c-114">Published</span></span> | <span data-ttu-id="dfd1c-115">April 2015</span><span class="sxs-lookup"><span data-stu-id="dfd1c-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="dfd1c-116">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="dfd1c-116">Abstract</span></span>

<span data-ttu-id="dfd1c-117">Dit document is ontworpen als officiële richtlijn voor iedereen plannen voor een implementatie van Windows PowerShell Desired State Configuration pull-server.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="dfd1c-118">Een pull-server is een eenvoudige service die duurt slechts enkele minuten om te implementeren.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="dfd1c-119">Hoewel dit document technische uitleg die kan worden gebruikt in een implementatie biedt, wordt de waarde van dit document is als referentie voor aanbevolen procedures en wat te denken voordat u implementeert.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="dfd1c-120">Lezers mooi met DSC moeten zijn en de voorwaarden die worden gebruikt om te beschrijven van de onderdelen die zijn opgenomen in een DSC-implementatie.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="dfd1c-121">Zie voor meer informatie de [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview) onderwerp.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/dsc/overview)  topic.</span></span>
<span data-ttu-id="dfd1c-122">Zoals DSC wordt verwacht op cloudcadans ontwikkelen, wordt de onderliggende technologie, met inbegrip van pull-server ook verwacht ontwikkelen en nieuwe mogelijkheden geïntroduceerd.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="dfd1c-123">Dit document bevat een versietabel met in de bijlage die verwijzingen naar de vorige releases en verwijzingen naar toekomstige uitziende oplossingen om aan te moedigen toekomstgerichte ontwerpen biedt.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="dfd1c-124">De twee belangrijkste secties van dit document:</span><span class="sxs-lookup"><span data-stu-id="dfd1c-124">The two major sections of this document:</span></span>

- <span data-ttu-id="dfd1c-125">Planning van de configuratie</span><span class="sxs-lookup"><span data-stu-id="dfd1c-125">Configuration Planning</span></span>
- <span data-ttu-id="dfd1c-126">Installatiehandleiding</span><span class="sxs-lookup"><span data-stu-id="dfd1c-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="dfd1c-127">Versies van Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="dfd1c-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="dfd1c-128">De informatie in dit document is bedoeld om te passen op Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="dfd1c-129">WMF 5.0 is niet vereist voor de implementatie en het gebruik van een pull-server, is versie 5.0 de focus van dit document.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="dfd1c-130">Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="dfd1c-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="dfd1c-131">Desired State Configuration (DSC) is een beheerplatform waarmee configuratiegegevens implementeren en beheren met behulp van een industrie-syntaxis met de naam van het Managed Object Format (MOF) om te beschrijven van het Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="dfd1c-132">Er bestaat een open source-project, Open Management Infrastructure (OMI), om verdere ontwikkeling van deze standaarden voor platformen, waaronder Linux en de hardware, besturingssystemen.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="dfd1c-133">Zie voor meer informatie de [DMTF-pagina koppelen volgens de specificaties van MOF](https://www.dmtf.org/standards/cim), en [OMI documenten en bron](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="dfd1c-134">Windows PowerShell biedt een set met taaluitbreidingen voor Desired State Configuration die u gebruiken kunt voor het maken en beheren van declaratieve configuraties.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="dfd1c-135">Pull-server-rol</span><span class="sxs-lookup"><span data-stu-id="dfd1c-135">Pull server role</span></span>

<span data-ttu-id="dfd1c-136">Een pull-server voorziet in een gecentraliseerde service voor het opslaan van configuraties die is toegankelijk voor de doelknooppunten.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="dfd1c-137">De functie voor pull-server kan worden geïmplementeerd als een Web Server-exemplaar of een SMB-bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="dfd1c-138">De web server-functie bevat een OData-interface en kan de mogelijkheden voor doelknooppunten om te rapporteren terug bevestiging van het slagen of mislukken als configuraties zijn toegepast (optioneel) bevatten.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="dfd1c-139">Deze functionaliteit is nuttig in omgevingen waarin er een groot aantal doelknooppunten.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="dfd1c-140">Na het configureren van een doelknooppunt (ook wel een client genoemd) om te verwijzen naar de pull-server de configuratie van de meest recente gegevens en alle vereiste scripts gedownload en toegepast.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="dfd1c-141">Dit kan gebeuren als een eenmalige installatie of als een opnieuw voorkomende taak waardoor ook de pull-server een belangrijk onderdeel voor het beheren van de wijziging op schaal.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="dfd1c-142">Zie voor meer informatie, [Windows PowerShell Desired State Configuration Pull-Servers](/powershell/dsc/pullServer) en</span><span class="sxs-lookup"><span data-stu-id="dfd1c-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](/powershell/dsc/pullServer) and</span></span>

<span data-ttu-id="dfd1c-143">[Pushen en ophalen van configuratie-modi](/powershell/dsc/pullServer).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-143">[Push and Pull Configuration Modes](/powershell/dsc/pullServer).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="dfd1c-144">Planning van de configuratie</span><span class="sxs-lookup"><span data-stu-id="dfd1c-144">Configuration planning</span></span>

<span data-ttu-id="dfd1c-145">Er is informatie die vooraf kan worden verzameld om u te helpen bij het plannen voor de juiste architectuur en om te worden voorbereid voor de stappen die nodig zijn om uit te voeren van de implementatie voor alle enterprise software-implementatie.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-145">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="dfd1c-146">De volgende secties bevatten informatie over het voorbereiden en de organisatie-verbindingen die waarschijnlijk moet gebeuren vooraf.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-146">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="dfd1c-147">Softwarevereisten</span><span class="sxs-lookup"><span data-stu-id="dfd1c-147">Software requirements</span></span>

<span data-ttu-id="dfd1c-148">Implementatie van een pull-server vereist de functie van de DSC-Service van Windows Server.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-148">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="dfd1c-149">Deze functie is geïntroduceerd in Windows Server 2012 en is bijgewerkt via voortdurende versies van Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-149">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="dfd1c-150">Software downloaden</span><span class="sxs-lookup"><span data-stu-id="dfd1c-150">Software downloads</span></span>

<span data-ttu-id="dfd1c-151">Naast het installeren van de meest recente inhoud van Windows Update, er zijn twee downloads beschouwd als aanbevolen procedure voor het implementeren van een DSC-pull-server: De meest recente versie van Windows Management Framework en een DSC-module voor het automatiseren van pull-server inrichten.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-151">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="dfd1c-152">WMF</span><span class="sxs-lookup"><span data-stu-id="dfd1c-152">WMF</span></span>

<span data-ttu-id="dfd1c-153">Windows Server 2012 R2 bevat een functie met de naam van de DSC-Service.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-153">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="dfd1c-154">De functie DSC-Service biedt de functionaliteit pull-server, met inbegrip van de binaire bestanden die ondersteuning bieden voor het OData-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-154">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="dfd1c-155">WMF is opgenomen in Windows Server en een flexibele uitgebracht tussen Windows Server-versies is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-155">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="dfd1c-156">[Nieuwe versies van WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) kunnen updates op de functie voor DSC-Service zijn.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-156">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="dfd1c-157">Daarom is het een aanbevolen procedure voor het downloaden van de nieuwste versie van WMF en om te controleren om na te gaan als u de release van een update voor de functie voor DSC-service bevat de opmerkingen bij de release.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-157">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="dfd1c-158">Ook moet u de sectie van de opmerkingen bij de release die aangeeft of de status van het ontwerp voor een update of scenario wordt vermeld als stabiel of experimentele controleren.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-158">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="dfd1c-159">Als u wilt toestaan voor een flexibele releasecyclus afzonderlijke functies worden gedeclareerd stabiel, is wat aangeeft dat de functie gereed om te worden gebruikt in een productie-omgeving, terwijl de WMF in Preview-versie is uitgebracht.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-159">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="dfd1c-160">Andere functies die in het verleden zijn bijgewerkt door versies van WMF (Zie de opmerkingen bij de Release van WMF voor verdere details):</span><span class="sxs-lookup"><span data-stu-id="dfd1c-160">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="dfd1c-161">Windows PowerShell Windows PowerShell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="dfd1c-161">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="dfd1c-162">Environment (ISE) Windows PowerShell-webservices (Management OData</span><span class="sxs-lookup"><span data-stu-id="dfd1c-162">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="dfd1c-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="dfd1c-163">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="dfd1c-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="dfd1c-164">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="dfd1c-165">DSC-resource</span><span class="sxs-lookup"><span data-stu-id="dfd1c-165">DSC resource</span></span>

<span data-ttu-id="dfd1c-166">De implementatie van een pull-server kan worden vereenvoudigd door de service met behulp van een DSC-configuratiescript inricht.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-166">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="dfd1c-167">Dit document bevat configuratiescripts die kunnen worden gebruikt voor het implementeren van een productie gereed server-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-167">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="dfd1c-168">Voor het gebruik van de van configuratiescripts, een DSC-module is vereist dat niet is opgenomen in Windows Server.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-168">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="dfd1c-169">De modulenaam van de vereiste is **xPSDesiredStateConfiguration**, waaronder de DSC-resource **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-169">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="dfd1c-170">De module xPSDesiredStateConfiguration kan worden gedownload [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-170">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="dfd1c-171">Gebruik de `Install-Module` cmdlet uit de **PowerShellGet** module.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-171">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="dfd1c-172">De **PowerShellGet** module wordt de module te downloaden:</span><span class="sxs-lookup"><span data-stu-id="dfd1c-172">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="dfd1c-173">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-173">Planning task</span></span>|
---|
<span data-ttu-id="dfd1c-174">U hebt toegang tot de installatiebestanden voor Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-174">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="dfd1c-175">De implementatieomgeving van een internettoegang hebben tot de module en WMF downloaden uit de galerie met online?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-175">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="dfd1c-176">Hoe installeert u de meest recente beveiligingsupdates na de installatie van het besturingssysteem?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-176">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="dfd1c-177">Wordt de omgeving hebt u toegang tot Internet om updates te downloaden of heeft deze een lokale Windows Server Update Services (WSUS)-server?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-177">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="dfd1c-178">Hebt u toegang tot bestanden die al updates via offline injectie zijn voor installatie van Windows Server?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-178">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="dfd1c-179">Hardwarevereisten</span><span class="sxs-lookup"><span data-stu-id="dfd1c-179">Hardware requirements</span></span>

<span data-ttu-id="dfd1c-180">Pull-server-implementaties worden ondersteund op fysieke en virtuele servers.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-180">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="dfd1c-181">Vereisten voor pull-server de grootte uitgelijnd met de vereisten voor Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-181">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="dfd1c-182">CPU: 1,4 GHz, 64-bits processor, geheugen: 512 MB schijfruimte: Netwerk van 32 GB: Gigabit Ethernet-Adapter</span><span class="sxs-lookup"><span data-stu-id="dfd1c-182">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="dfd1c-183">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-183">Planning task</span></span>|
---|
<span data-ttu-id="dfd1c-184">Wilt u implementeren op fysieke hardware of op een virtualisatieplatform?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-184">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="dfd1c-185">Wat is het proces voor het aanvragen van een nieuwe server voor uw doelomgeving?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-185">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="dfd1c-186">Wat is de gemiddelde verwerkingstijd voor een server beschikbaar?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-186">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="dfd1c-187">Welke grootte-server zal u vragen?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-187">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="dfd1c-188">Accounts</span><span class="sxs-lookup"><span data-stu-id="dfd1c-188">Accounts</span></span>

<span data-ttu-id="dfd1c-189">Er zijn geen vereisten voor serviceaccount om een pull-server-exemplaar te implementeren.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-189">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="dfd1c-190">Er zijn echter scenario's waarin de website in de context van een lokale gebruikersaccount toegekend uitvoeren kan.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-190">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="dfd1c-191">Bijvoorbeeld, als er behoefte aan toegang tot een storage-share voor website-inhoud en de Windows-Server of het apparaat die als host fungeert voor de storage-share zijn niet toegevoegd aan een domein.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-191">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="dfd1c-192">DNS-records</span><span class="sxs-lookup"><span data-stu-id="dfd1c-192">DNS records</span></span>

<span data-ttu-id="dfd1c-193">U moet een servernaam bij het configureren van clients gebruiken om te werken met een pull-server-omgeving.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-193">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="dfd1c-194">Hostnaam van de server wordt meestal gebruikt in een testomgeving, of het IP-adres voor de server kan worden gebruikt als DNS-naamomzetting niet beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-194">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="dfd1c-195">In een productieomgeving of in een testomgeving die is bedoeld om weer te geven van een productie-implementatie, wordt de aanbevolen procedure is het maken van een DNS CNAME-record.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-195">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="dfd1c-196">Een DNS CNAME kunt u een alias om te verwijzen naar de host-A-record maken.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-196">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="dfd1c-197">Het doel van de extra UPN-record is de flexibiliteit te vergroten moet een wijziging vereist in de toekomst zijn.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-197">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="dfd1c-198">Een CNAME te isoleren van configuratie van de client zodat wijzigingen in de server-omgeving, zoals het vervangen van een pull-server of het toevoegen van extra pull-servers, wordt een bijbehorende wijziging in de configuratie van de client vereist.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-198">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="dfd1c-199">Bij het kiezen van een naam op voor de DNS-record, houd rekening met de oplossingsarchitectuur.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-199">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="dfd1c-200">Als met behulp van de taakverdeling, moet het certificaat dat wordt gebruikt om verkeer te beveiligen via HTTPS voor het delen van dezelfde naam als de DNS-record.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-200">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="dfd1c-201">Scenario</span><span class="sxs-lookup"><span data-stu-id="dfd1c-201">Scenario</span></span> |<span data-ttu-id="dfd1c-202">Best practices</span><span class="sxs-lookup"><span data-stu-id="dfd1c-202">Best Practice</span></span>
:---|:---
<span data-ttu-id="dfd1c-203">Testomgeving</span><span class="sxs-lookup"><span data-stu-id="dfd1c-203">Test Environment</span></span> |<span data-ttu-id="dfd1c-204">De geplande productie-omgeving, indien mogelijk reproduceren.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-204">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="dfd1c-205">De hostnaam van een server is geschikt voor eenvoudige configuraties.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-205">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="dfd1c-206">Als DNS niet beschikbaar is, kan een IP-adres kan worden gebruikt in plaats van een hostnaam.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-206">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="dfd1c-207">Implementatie met één knooppunt</span><span class="sxs-lookup"><span data-stu-id="dfd1c-207">Single Node Deployment</span></span> |<span data-ttu-id="dfd1c-208">Maak een DNS CNAME-record die naar de hostnaam van de server verwijst.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-208">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="dfd1c-209">Zie voor meer informatie, [DNS Round Robin configureren in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-209">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="dfd1c-210">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-210">Planning task</span></span>|
---|
<span data-ttu-id="dfd1c-211">Wist u dat met wie neem contact op met om DNS-records gemaakt en gewijzigd?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-211">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="dfd1c-212">Wat is de gemiddelde doorlooptijd voor een aanvraag voor een DNS-record?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-212">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="dfd1c-213">Moet u om aan te vragen van statische hostnaam-A-records voor servers?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-213">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="dfd1c-214">Welke vragen u als een CNAME?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-214">What will you request as a CNAME?</span></span>|
<span data-ttu-id="dfd1c-215">Indien nodig, welk type Load Balancing-oplossing wordt u gebruiken?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-215">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="dfd1c-216">(Zie sectie Load Balancing voor meer informatie)</span><span class="sxs-lookup"><span data-stu-id="dfd1c-216">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="dfd1c-217">Openbare-sleutelinfrastructuur</span><span class="sxs-lookup"><span data-stu-id="dfd1c-217">Public Key Infrastructure</span></span>

<span data-ttu-id="dfd1c-218">De meeste organisaties vereisen dat het netwerkverkeer, met name verkeer dat dergelijke gevoelige gegevens bevat, hoe servers zijn geconfigureerd, moet worden gevalideerd en/of tijdens de overdracht versleuteld.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-218">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="dfd1c-219">Het is mogelijk om te implementeren met behulp van HTTP, vereenvoudigt het uitvoeren van een pull-server aanvragen van clients in normale tekst, het is een best practice voor beveiligde via HTTPS-verkeer.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-219">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="dfd1c-220">De service kan worden geconfigureerd voor het gebruik van HTTPS met behulp van een set parameters in de DSC-resource **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-220">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="dfd1c-221">De vereisten voor certificaten voor het beveiligen van HTTPS-verkeer voor pull-server zijn niet anders dan het beveiligen van een andere HTTPS-website.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-221">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="dfd1c-222">De **webserver** sjabloon in een Windows Server Certificate Services voldoet aan de vereiste mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-222">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="dfd1c-223">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-223">Planning task</span></span>|
---|
<span data-ttu-id="dfd1c-224">Als certificaataanvragen niet zijn geautomatiseerd, die u moet contact opnemen met op aanvragen van een certificaat?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-224">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="dfd1c-225">Wat is de gemiddelde doorlooptijd voor de aanvraag?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-225">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="dfd1c-226">Hoe wordt het certificaatbestand worden overgebracht naar u?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-226">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="dfd1c-227">Hoe wordt de persoonlijke sleutel van het certificaat aan u worden overgedragen?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-227">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="dfd1c-228">Hoe lang is de verlooptijd van de standaard?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-228">How long is the default expiration time?</span></span>|
<span data-ttu-id="dfd1c-229">Hebt u verrekend op een DNS-naam voor de pull-server-omgeving, die u voor de naam van het certificaat gebruiken kunt?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-229">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="dfd1c-230">Een architectuur kiezen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-230">Choosing an architecture</span></span>

<span data-ttu-id="dfd1c-231">Een pull-server kan worden geïmplementeerd met behulp van een webservice die zijn gehost op IIS of een SMB-bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-231">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="dfd1c-232">In de meeste gevallen wordt de web service-optie bieden meer flexibiliteit.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-232">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="dfd1c-233">Het is niet ongebruikelijk dat HTTPS-verkeer naar de grenzen van het netwerk, door te gaan dat SMB-verkeer is vaak gefilterd of geblokkeerd tussen netwerken.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-233">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="dfd1c-234">De webservice biedt ook de mogelijkheid om op te nemen van een conformiteit van Server of Web Reporting Manager (beide onderwerpen in een toekomstige versie van dit document worden verholpen) die bieden een mechanisme voor clients voor statusrapportage terug naar een server voor gecentraliseerde zichtbaarheid.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-234">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="dfd1c-235">SMB biedt een optie voor omgevingen waar beleid bepaalt dat een webserver niet moet worden gebruikt, en voor andere omgevingsvereisten die een web server-rol ongewenste maken.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-235">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="dfd1c-236">Vergeet niet om te evalueren van de vereisten voor het ondertekenen en versleutelen van verkeer in beide gevallen.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-236">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="dfd1c-237">HTTPS en SMB-ondertekening IPSEC-beleid zijn alle opties waard.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-237">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="dfd1c-238">Taakverdeling</span><span class="sxs-lookup"><span data-stu-id="dfd1c-238">Load balancing</span></span>

<span data-ttu-id="dfd1c-239">Clients communiceren met de webservice te vragen voor informatie die in een enkel antwoord wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-239">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="dfd1c-240">Er zijn geen opeenvolgende aanvragen zijn vereist, dus het is niet nodig zijn voor de load balancer-platform, zodat er sessies op één server op elk gewenst moment worden bijgehouden in de tijd.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-240">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="dfd1c-241">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-241">Planning task</span></span>|
---|
<span data-ttu-id="dfd1c-242">Welke oplossing wordt gebruikt voor verkeer te verdelen over meerdere servers?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-242">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="dfd1c-243">Als u een load balancer, die een aanvraag voor het toevoegen van een nieuwe configuratie op het apparaat?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-243">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="dfd1c-244">Wat is de gemiddelde doorlooptijd voor een aanvraag voor het configureren van een nieuwe load balanced webservice?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-244">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="dfd1c-245">Welke gegevens zijn vereist voor de aanvraag?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-245">What information will be required for the request?</span></span>|
<span data-ttu-id="dfd1c-246">Hebt u nodig om aan te vragen van een extra IP-adres of het team dat verantwoordelijk is voor de taakverdeling wordt afgehandeld dat?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-246">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="dfd1c-247">Hebt u de DNS-records die nodig zijn, en deze zijn vereist om het team dat verantwoordelijk is voor het configureren van de load balancer-oplossing?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-247">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="dfd1c-248">De oplossing voor taakverdeling vereist dat de PKI worden verwerkt door het apparaat of saldo HTTPS-verkeer, zolang er geen sessievereisten zijn laden?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-248">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="dfd1c-249">Staging-configuraties en -modules op de pull-server</span><span class="sxs-lookup"><span data-stu-id="dfd1c-249">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="dfd1c-250">Als onderdeel van de planning van de configuratie, moet u nadenken over welke DSC-modules en configuraties worden gehost door de pull-server.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-250">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="dfd1c-251">Voor de planning van de configuratie is het belangrijk dat u hebt een basiskennis hebt van het voorbereiden en implementeren van inhoud naar een pull-server.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-251">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="dfd1c-252">Deze sectie wordt in de toekomst worden uitgebreid en opgenomen in de Operations Guide voor DSC-Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-252">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="dfd1c-253">De handleiding wordt uitgelegd hoe het dagelijkse proces voor het beheren van modules en configuraties na verloop van tijd met automation.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-253">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="dfd1c-254">DSC-modules</span><span class="sxs-lookup"><span data-stu-id="dfd1c-254">DSC modules</span></span>

<span data-ttu-id="dfd1c-255">Clients die aanvragen van een configuratie moet de vereiste DSC-modules.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-255">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="dfd1c-256">Een functionaliteit van de pull-server is voor het automatiseren van distributie op aanvraag van DSC-modules voor clients.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-256">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="dfd1c-257">Als u een pull-server mogelijk als een testomgeving of testen van concept voor het eerst implementeert, gaat u waarschijnlijk afhangen van DSC-modules die beschikbaar via openbare opslagplaatsen, zoals de PowerShell Gallery of de PowerShell.org GitHub-opslagplaatsen voor DSC-modules zijn .</span><span class="sxs-lookup"><span data-stu-id="dfd1c-257">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="dfd1c-258">Het is essentieel om te onthouden dat zelfs voor betrouwbare online-bronnen, zoals de PowerShell Gallery, een module die is gedownload vanuit een openbare opslagplaats, moet worden gecontroleerd door iemand met PowerShell-ervaring en kennis van de omgeving waar de modules worden gebruikt voordat het wordt gebruikt in de productieomgeving.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-258">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="dfd1c-259">Tijdens het uitvoeren van deze taak is het een goed moment om te controleren voor elke extra nettolading in de module die kan worden verwijderd, zoals documentatie en scripts.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-259">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="dfd1c-260">Zo beperkt u de netwerkbandbreedte per client in de eerste aanvraag wanneer modules worden gedownload via het netwerk van server naar de client.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-260">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="dfd1c-261">Elke module moet zijn ingepakt in een specifieke indeling, een ZIP-bestand met de naam ModuleName_Version.zip met de nettolading van de module.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-261">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="dfd1c-262">Nadat het bestand wordt gekopieerd naar de server die een controlesom-bestand moet worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-262">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="dfd1c-263">Wanneer clients verbinding met de server maken, wordt de controlesom gebruikt om te controleren of dat de inhoud van de DSC-module is niet gewijzigd sinds het is gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-263">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="dfd1c-264">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-264">Planning task</span></span>|
---|
<span data-ttu-id="dfd1c-265">Als u van plan bent een omgeving met test- of testomgeving weet welke scenario's sleutel valideren?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-265">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="dfd1c-266">Zijn er openbaar beschikbare modules met resources voor alles wat die u nodig hebt of moet u uw eigen resources maken?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-266">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="dfd1c-267">Wordt uw omgeving hebt u toegang tot Internet om op te halen van openbare modules?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-267">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="dfd1c-268">Wie zijn verantwoordelijk voor het controleren van DSC-modules?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-268">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="dfd1c-269">Als u van plan bent een productie-omgeving wat u gebruikt als een lokale opslagplaats voor het opslaan van DSC-modules?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-269">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="dfd1c-270">Accepteert een centraal team DSC-modules van App-teams?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-270">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="dfd1c-271">Wat is het proces?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-271">What will the process be?</span></span>|
<span data-ttu-id="dfd1c-272">Wordt u verpakking, kopiëren en het maken van een controlesom voor gereed is voor productie DSC modules met de server uit de opslagplaats van het automatiseren?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-272">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="dfd1c-273">Uw team zijn verantwoordelijk voor het beheren van het automatiseringsplatform?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-273">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="dfd1c-274">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="dfd1c-274">DSC configurations</span></span>

<span data-ttu-id="dfd1c-275">Het doel van een pull-server is een gecentraliseerde mechanisme voor het distribueren van DSC-configuraties voor de client-knooppunten bieden.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-275">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="dfd1c-276">De configuraties worden opgeslagen op de server als MOF-documenten.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-276">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="dfd1c-277">Elk document worden benoemd met een unieke **Guid**.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-277">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="dfd1c-278">Wanneer clients verbinding maken met een pull-server worden geconfigureerd, krijgen ze ook de **Guid** voor de configuratie van deze moeten aanvragen.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-278">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="dfd1c-279">Dit systeem van configuraties door te verwijzen naar **Guid** gegarandeerd uniek globale en flexibele heeft dat kan een configuratie met granulatie per knooppunt, of als een configuratie van de functie die omvat veel servers zijn die moeten worden toegepast configuraties van identieke.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-279">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="dfd1c-280">GUID 's</span><span class="sxs-lookup"><span data-stu-id="dfd1c-280">Guids</span></span>

<span data-ttu-id="dfd1c-281">Planning voor de configuratie van **GUID's** de moeite waard is extra aandacht bij via een pull-server-implementatie.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-281">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="dfd1c-282">Er is geen specifieke vereiste voor het afhandelen van **GUID's** en het proces is waarschijnlijk moet uniek zijn voor elke omgeving.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-282">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="dfd1c-283">Het proces kan variëren van eenvoudige tot complexe: een centraal opgeslagen CSV-bestand, een eenvoudige SQL-tabel, een CMDB of een complexe oplossingen maken waarvoor integratie met een ander hulpprogramma of software-oplossing nodig.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-283">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="dfd1c-284">Er zijn twee algemene methoden:</span><span class="sxs-lookup"><span data-stu-id="dfd1c-284">There are two general approaches:</span></span>

- <span data-ttu-id="dfd1c-285">**Toewijzen van GUID's per server** : biedt een zekere mate van zekerheid dat de configuratie van elke server afzonderlijk wordt beheerd.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-285">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="dfd1c-286">Dit biedt een precisieniveau om updates en kan ze goed werken in omgevingen met een klein aantal servers.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-286">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="dfd1c-287">**Toewijzen van GUID's per serverfunctie** : alle servers die dezelfde functie, zoals webservers vervullen, gebruikt u dezelfde GUID om te verwijzen naar de vereiste configuratiegegevens.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-287">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="dfd1c-288">Er rekening mee dat als veel servers dezelfde GUID delen, al deze zou worden bijgewerkt tegelijkertijd wanneer de configuratie wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-288">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="dfd1c-289">De GUID is iets dat gevoelige gegevens moet worden overwogen omdat deze kan worden gebruikt door iemand met kwade bedoelingen te krijgen van inzicht in hoe servers zijn geïmplementeerd en geconfigureerd in uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-289">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="dfd1c-290">Zie voor meer informatie, [veilig bij het toewijzen van GUID's in PowerShell Desired State Configuration Pull-modus](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span><span class="sxs-lookup"><span data-stu-id="dfd1c-290">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="dfd1c-291">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-291">Planning task</span></span>|
---|
<span data-ttu-id="dfd1c-292">Wie zijn verantwoordelijk voor het kopiëren van configuraties in naar de map van de pull-server wanneer ze klaar zijn?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-292">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="dfd1c-293">Als configuraties zijn gemaakt door een team van toepassing, wat het proces is om ze uit?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-293">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="dfd1c-294">Gebruik u van een opslagplaats voor het opslaan van configuraties als ze worden gemaakt, tussen teams?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-294">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="dfd1c-295">Automatiseert u het proces van configuraties kopiëren naar de server en het maken van een controlesom wanneer ze klaar zijn?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-295">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="dfd1c-296">Hoe wordt u GUID's toewijzen aan servers of rollen en waar deze worden opgeslagen?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-296">How will you map Guids to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="dfd1c-297">Wat u gebruikt als een proces voor het configureren van clientcomputers, en hoe wordt deze dan geïntegreerd met het proces voor het maken en opslaan van configuratie-GUID's?</span><span class="sxs-lookup"><span data-stu-id="dfd1c-297">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="dfd1c-298">Installatiehandleiding</span><span class="sxs-lookup"><span data-stu-id="dfd1c-298">Installation Guide</span></span>

<span data-ttu-id="dfd1c-299">*Scripts die worden vermeld in dit document zijn stabiel voorbeelden. Altijd zorgvuldig te controleren scripts voordat deze wordt uitgevoerd in een productie-omgeving.*</span><span class="sxs-lookup"><span data-stu-id="dfd1c-299">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="dfd1c-300">Vereisten</span><span class="sxs-lookup"><span data-stu-id="dfd1c-300">Prerequisites</span></span>

<span data-ttu-id="dfd1c-301">De versie van PowerShell op uw server gebruik de volgende opdracht uit om te controleren.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-301">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="dfd1c-302">Indien mogelijk een upgrade uitvoeren naar de nieuwste versie van Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-302">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="dfd1c-303">Download vervolgens het `xPsDesiredStateConfiguration` module met behulp van de volgende opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-303">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="dfd1c-304">De opdracht vraagt om uw goedkeuring wordt vereist voor het downloaden van de module.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-304">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="dfd1c-305">Installatie en configuratie-scripts</span><span class="sxs-lookup"><span data-stu-id="dfd1c-305">Installation and configuration scripts</span></span>

<span data-ttu-id="dfd1c-306">De beste methode voor het implementeren van een DSC-pull-server is het gebruik van een script voor DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-306">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="dfd1c-307">Dit document worden gepresenteerd scripts, met inbegrip van beide basisinstellingen die alleen de DSC-webservice configureren en geavanceerde instellingen van een Windows Server-end-to-end met DSC webservice configureren.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-307">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="dfd1c-308">Opmerking:  Op dit moment de `xPSDesiredStateConfiguation` DSC-module vereist dat de server om te worden van de landinstelling EN-US.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-308">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="dfd1c-309">Basisinformatie over de configuratie voor Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="dfd1c-309">Basic configuration for Windows Server 2012</span></span>

```powershell
# This is a very basic Configuration to deploy a pull server instance in a lab environment on Windows Server 2012.

Configuration PullServer {
Import-DscResource -ModuleName xPSDesiredStateConfiguration

        # Load the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
          Ensure = 'Present'
          Name = 'DSC-Service'
        }

        # Use the DSC Resource to simplify deployment of the web service
        xDSCWebService PSDSCPullServer
        {
          Ensure = 'Present'
          EndpointName = 'PSDSCPullServer'
          Port = 8080
          PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
          CertificateThumbPrint = 'AllowUnencryptedTraffic'
          ModulePath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
          ConfigurationPath = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
          State = 'Started'
          DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
}
PullServer -OutputPath 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'
```

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="dfd1c-310">Geavanceerde configuratie voor Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="dfd1c-310">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments on Windows Server 2012 R2.
# Many of the features demonstrated are optional and provided to demonstrate how to adapt the Configuration for multiple scenarios
# Select the needed resources based on the requirements for each environment.
# Optional scenarios include:
#      * Reduce footprint to Server Core
#      * Rename server and join domain
#      * Switch from SSL to TLS for HTTPS
#      * Automatically load certificate from Certificate Authority
#      * Locate Modules and Configuration data on remote SMB share
#      * Manage state of default websites in IIS

param (
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [System.String] $ServerName,
        [System.String] $DomainName,
        [System.String] $CARootName,
        [System.String] $CAServerFQDN,
        [System.String] $CertSubject,
        [System.String] $SMBShare,
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $Credential
    )

Configuration PullServer {
    Import-DscResource -ModuleName xPSDesiredStateConfiguration, xWebAdministration, xCertificate, xComputerManagement
    Node localhost
    {

        # Configure the server to automatically corret configuration drift including reboots if needed.
        LocalConfigurationManager
        {
            ConfigurationMode = 'ApplyAndAutoCorrect'
            RebootNodeifNeeded = $node.RebootNodeifNeeded
            CertificateId = $node.Thumbprint
        }

        # Remove all GUI interfaces so the server has minimum running footprint.
        WindowsFeature ServerCore
        {
            Ensure = 'Absent'
            Name = 'User-Interfaces-Infra'
        }

        # Set the server name and if needed, join a domain. If not joining a domain, remove the DomainName parameter.
        xComputer DomainJoin
        {
            Name = $Node.ServerName
            DomainName = $Node.DomainName
            Credential = $Node.Credential
        }

        # The next series of settings disable SSL and enable TLS, for environments where that is required by policy.
        Registry TLS1_2ServerEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ServerDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Server'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientEnabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'Enabled'
            ValueData = 1
            ValueType = 'Dword'
        }

        Registry TLS1_2ClientDisabledByDefault
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.2\Client'
            ValueName = 'DisabledByDefault'
            ValueData = 0
            ValueType = 'Dword'
        }

        Registry SSL2ServerDisabled
        {
            Ensure = 'Present'
            Key = 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\SSL 2.0\Server'
            ValueName = 'Enabled'
            ValueData = 0
            ValueType = 'Dword'
        }

        # Install the Windows Server DSC Service feature
        WindowsFeature DSCServiceFeature
        {
            Ensure = 'Present'
            Name = 'DSC-Service'
        }

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority, complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider modifying the default port, possibly leveraging port 443 in environments where that is enforced as a standard.
        xDSCWebService PSDSCPullServer
        {
            Ensure = 'Present'
            EndpointName = 'PSDSCPullServer'
            Port = 8080
            PhysicalPath = "$env:SYSTEMDRIVE\inetpub\wwwroot\PSDSCPullServer"
            CertificateThumbPrint = 'CertificateSubject'
            CertificateSubject = $Node.CertSubject
            ModulePath = "$($Node.SMBShare)\DscService\Modules"
            ConfigurationPath = "$($Node.SMBShare)\DscService\Configuration"
            State = 'Started'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }

        # Validate web config file contains current DB settings
        xWebConfigKeyValue CorrectDBProvider
        {
            ConfigSection = 'AppSettings'
            Key = 'dbprovider'
            Value = 'System.Data.OleDb'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }
        xWebConfigKeyValue CorrectDBConnectionStr
        {
            ConfigSection = 'AppSettings'
            Key = 'dbconnectionstr'
            Value = 'Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Program Files\WindowsPowerShell\DscService\Devices.mdb;'
            WebsitePath = 'IIS:\sites\PSDSCPullServer'
            DependsOn = '[xDSCWebService]PSDSCPullServer'
        }

        # Stop the default website
        xWebsite StopDefaultSite
        {
            Ensure = 'Present'
            Name = 'Default Web Site'
            State = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn = '[WindowsFeature]DSCServiceFeature'
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            ServerName = $ServerName
            DomainName = $DomainName
            CARootName = $CARootName
            CAServerFQDN = $CAServerFQDN
            CertSubject = $CertSubject
            AutoRenew = $true
            SMBShare = $SMBShare
            Credential = $Credential
            RebootNodeifNeeded = $true
            CertificateFile = 'c:\PullServerConfig\Cert.cer'
            Thumbprint = 'B9A39921918B466EB1ADF2509E00F5DECB2EFDA9'
            }
        )
    }

PullServer -ConfigurationData $configData -OutputPath 'C:\PullServerConfig\'
Set-DscLocalConfigurationManager -ComputerName localhost -Path 'C:\PullServerConfig\'
Start-DscConfiguration -Wait -Force -Verbose -Path 'C:\PullServerConfig\'

# .\Script.ps1 -ServerName web1 -domainname 'test.pha' -carootname 'test-dc01-ca' -caserverfqdn 'dc01.test.pha' -certsubject 'CN=service.test.pha' -smbshare '\\sofs1.test.pha\share'
```

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="dfd1c-311">Controleer de functionaliteit van de pull-server</span><span class="sxs-lookup"><span data-stu-id="dfd1c-311">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](Invoke-WebRequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}

Verify-DSCPullServer 'INSERT SERVER FQDN'
```

```output
Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="dfd1c-312">Clients configureren</span><span class="sxs-lookup"><span data-stu-id="dfd1c-312">Configure clients</span></span>

```powershell
Configuration PullClient {
    param(
    $ID,
    $Server
    )
        LocalConfigurationManager
                {
                    ConfigurationID = $ID;
                    RefreshMode = 'PULL';
                    DownloadManagerName = 'WebDownloadManager';
                    RebootNodeIfNeeded = $true;
                    RefreshFrequencyMins = 30;
                    ConfigurationModeFrequencyMins = 15;
                    ConfigurationMode = 'ApplyAndAutoCorrect';
                    DownloadManagerCustomData = @{ServerUrl = "http://"+$Server+":8080/PSDSCPullServer.svc"; AllowUnsecureConnection = $true}
                }
}

PullClient -ID 'INSERTGUID' -Server 'INSERTSERVER' -Output 'C:\DSCConfig\'
Set-DscLocalConfigurationManager -ComputerName 'Localhost' -Path 'C:\DSCConfig\' -Verbose
```

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="dfd1c-313">Aanvullende verwijzingen, codefragmenten en voorbeelden</span><span class="sxs-lookup"><span data-stu-id="dfd1c-313">Additional references, snippets, and examples</span></span>

<span data-ttu-id="dfd1c-314">Dit voorbeeld laat zien hoe u handmatig een clientverbinding tot stand (vereist WMF5) voor het testen.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-314">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="dfd1c-315">De [toevoegen DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet een type CNAME-record toevoegen aan een DNS-zone wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-315">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="dfd1c-316">De PowerShell-functie aan [een controlesom en DSC MOF publiceren met SMB-Pull-Server maken](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genereert automatisch de vereiste controlesom en vervolgens de configuratie van de MOF- en controlesom bestanden worden gekopieerd naar de SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-316">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="dfd1c-317">Bijlage - Understanding ODATA-servicegegevens bestandstypen</span><span class="sxs-lookup"><span data-stu-id="dfd1c-317">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="dfd1c-318">Een bestand wordt opgeslagen voor het maken van informatie tijdens de implementatie van een pull-server met de OData-webservice.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-318">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="dfd1c-319">Het type bestand is afhankelijk van het besturingssysteem, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-319">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="dfd1c-320">**Windows Server 2012** het bestandstype is altijd .mdb</span><span class="sxs-lookup"><span data-stu-id="dfd1c-320">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="dfd1c-321">**Windows Server 2012 R2** het bestandstype wordt standaard edb, tenzij een .mdb is opgegeven in de configuratie</span><span class="sxs-lookup"><span data-stu-id="dfd1c-321">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="dfd1c-322">In de [voorbeeldscript geavanceerde](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) voor het installeren van een Pull-Server, vindt u ook een voorbeeld van hoe u kunt de instellingen van het bestand web.config om te voorkomen dat elke kans van de fout wordt veroorzaakt door het bestandstype automatisch te bepalen.</span><span class="sxs-lookup"><span data-stu-id="dfd1c-322">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
