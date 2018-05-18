---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Best practices voor pull-servers
ms.openlocfilehash: 1efc016df6882fa962f59dfd3e53eaa6d6b0c121
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="a7a26-103">Best practices voor pull-servers</span><span class="sxs-lookup"><span data-stu-id="a7a26-103">Pull server best practices</span></span>

><span data-ttu-id="a7a26-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a7a26-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7a26-105">De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="a7a26-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="a7a26-106">Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="a7a26-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="a7a26-107">Overzicht: Dit document is bedoeld om het proces en uitbreidingsmogelijkheden engineers die voor de oplossing voorbereiden zich helpen bevatten.</span><span class="sxs-lookup"><span data-stu-id="a7a26-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="a7a26-108">Gegevens moeten best practices te geven aangeduid met klanten en vervolgens worden gevalideerd door het productteam om ervoor te zorgen aanbevelingen toekomstige verbonden zijn en als stabiel beschouwd.</span><span class="sxs-lookup"><span data-stu-id="a7a26-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

| |<span data-ttu-id="a7a26-109">Informatie over dit document</span><span class="sxs-lookup"><span data-stu-id="a7a26-109">Doc Info</span></span>|
|:---|:---|
<span data-ttu-id="a7a26-110">auteur</span><span class="sxs-lookup"><span data-stu-id="a7a26-110">Author</span></span> | <span data-ttu-id="a7a26-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="a7a26-111">Michael Greene</span></span>
<span data-ttu-id="a7a26-112">Revisoren</span><span class="sxs-lookup"><span data-stu-id="a7a26-112">Reviewers</span></span> | <span data-ttu-id="a7a26-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="a7a26-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span>
<span data-ttu-id="a7a26-114">Gepubliceerd</span><span class="sxs-lookup"><span data-stu-id="a7a26-114">Published</span></span> | <span data-ttu-id="a7a26-115">April 2015</span><span class="sxs-lookup"><span data-stu-id="a7a26-115">April, 2015</span></span>

## <a name="abstract"></a><span data-ttu-id="a7a26-116">Abstracte</span><span class="sxs-lookup"><span data-stu-id="a7a26-116">Abstract</span></span>

<span data-ttu-id="a7a26-117">Dit document is ontworpen voor de officiële richtlijnen voor iedereen plannen voor een implementatie van Windows PowerShell Desired State Configuration pull-server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="a7a26-118">Een pull-server is een eenvoudige service die alleen minuten te implementeren.</span><span class="sxs-lookup"><span data-stu-id="a7a26-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="a7a26-119">Hoewel dit document technische procedures richtlijnen die kan worden gebruikt in een implementatie biedt, is de waarde van dit document als een verwijzing voor aanbevolen procedures en wat u moet denken voordat u implementeert.</span><span class="sxs-lookup"><span data-stu-id="a7a26-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span>
<span data-ttu-id="a7a26-120">Lezers enigszins bekend bent met DSC moeten hebben en de voorwaarden voor het beschrijven van de onderdelen die zijn opgenomen in een DSC-implementatie.</span><span class="sxs-lookup"><span data-stu-id="a7a26-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="a7a26-121">Zie voor meer informatie de [Windows PowerShell Desired Configuration overzicht](https://technet.microsoft.com/library/dn249912.aspx) onderwerp.</span><span class="sxs-lookup"><span data-stu-id="a7a26-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](https://technet.microsoft.com/library/dn249912.aspx)  topic.</span></span>
<span data-ttu-id="a7a26-122">Zoals DSC wordt verwacht op cloud uitgebracht ontwikkelen, worden de onderliggende technologie inclusief pull-server wordt ook verwacht ontwikkelen en nieuwe mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="a7a26-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="a7a26-123">Dit document bevat een versietabel in de bijlage die voorziet in verwijzingen naar de vorige releases en verwijzingen naar toekomstige Zoek oplossingen te moedigen toekomstgerichte ontwerpen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="a7a26-124">De twee hoofdonderdelen van dit document:</span><span class="sxs-lookup"><span data-stu-id="a7a26-124">The two major sections of this document:</span></span>

 - <span data-ttu-id="a7a26-125">Planning van de configuratie</span><span class="sxs-lookup"><span data-stu-id="a7a26-125">Configuration Planning</span></span>
 - <span data-ttu-id="a7a26-126">Installatiehandleiding</span><span class="sxs-lookup"><span data-stu-id="a7a26-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="a7a26-127">Versies van het Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="a7a26-127">Versions of the Windows Management Framework</span></span>
<span data-ttu-id="a7a26-128">De informatie in dit document is bedoeld om te passen op Windows Management Framework 5.0.</span><span class="sxs-lookup"><span data-stu-id="a7a26-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="a7a26-129">WMF 5.0 is niet vereist voor de implementatie en het gebruik van een pull-server, is versie 5.0 de focus van dit document.</span><span class="sxs-lookup"><span data-stu-id="a7a26-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="a7a26-130">Windows PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="a7a26-130">Windows PowerShell Desired State Configuration</span></span>
<span data-ttu-id="a7a26-131">Desired State Configuration (DSC) is een beheerplatform waarmee configuratiegegevens implementeren en beheren met behulp van een industrie-syntaxis Managed Object Format (MOF) met de naam voor het beschrijven van het Common Information Model (CIM).</span><span class="sxs-lookup"><span data-stu-id="a7a26-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="a7a26-132">Er bestaat een open source-project, Open Management Infrastructure (OMI), om verdere ontwikkeling van deze standaarden in verschillende platforms, waaronder Linux en -netwerkbesturingssystemen hardware.</span><span class="sxs-lookup"><span data-stu-id="a7a26-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="a7a26-133">Zie voor meer informatie de [DMTF pagina koppelen aan MOF specificaties](http://dmtf.org/standards/cim), en [OMI documenten en bron](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="a7a26-133">For more information, see the [DMTF page linking to MOF specifications](http://dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="a7a26-134">Windows PowerShell biedt een set met taaluitbreidingen voor Desired State Configuration waarmee u kunt maken en beheren van declaratieve configuraties.</span><span class="sxs-lookup"><span data-stu-id="a7a26-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="a7a26-135">Pull-serverfunctie</span><span class="sxs-lookup"><span data-stu-id="a7a26-135">Pull server role</span></span>
<span data-ttu-id="a7a26-136">Een pull-server biedt een gecentraliseerde service voor het opslaan van de configuraties die toegankelijk is voor de doelknooppunten.</span><span class="sxs-lookup"><span data-stu-id="a7a26-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="a7a26-137">De functie van de pull-server kan worden geïmplementeerd als een Web Server-exemplaar of een SMB-bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="a7a26-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="a7a26-138">De mogelijkheid van web server bevat een OData-interface en kunt u eventueel opnemen mogelijkheden voor de doelknooppunten om te rapporteren terug bevestiging van het slagen of mislukken als configuraties zijn toegepast.</span><span class="sxs-lookup"><span data-stu-id="a7a26-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="a7a26-139">Deze functionaliteit is handig in omgevingen wanneer er een groot aantal doelknooppunten.</span><span class="sxs-lookup"><span data-stu-id="a7a26-139">This functionality is useful in environments where there are a large number of target nodes.</span></span>
<span data-ttu-id="a7a26-140">Na het configureren van een doelknooppunt (ook wel een client genoemd) om te verwijzen naar de pull-server de configuratie van de meest recente zijn gegevens en alle vereiste scripts gedownload en toegepast.</span><span class="sxs-lookup"><span data-stu-id="a7a26-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="a7a26-141">Dit kan gebeuren als een eenmalige implementatie of als een taak voor opnieuw voorkomende waardoor dit ook de pull-server een belangrijk onderdeel voor het beheren van de wijziging op grote schaal.</span><span class="sxs-lookup"><span data-stu-id="a7a26-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="a7a26-142">Zie voor meer informatie [Windows PowerShell Desired status Pull-configuratieservers](https://technet.microsoft.com/library/dn249913.aspx) en [Push als Pull-Configuratiemodi](https://technet.microsoft.com/library/dn249913.aspx).</span><span class="sxs-lookup"><span data-stu-id="a7a26-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](https://technet.microsoft.com/library/dn249913.aspx) and [Push and Pull Configuration Modes](https://technet.microsoft.com/library/dn249913.aspx).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="a7a26-143">Planning van de configuratie</span><span class="sxs-lookup"><span data-stu-id="a7a26-143">Configuration planning</span></span>

<span data-ttu-id="a7a26-144">Er is voor de implementatie van enterprise software informatie die vooraf kan worden verzameld om u te helpen bij het plannen voor de juiste architectuur en om te worden voorbereid voor de stappen die nodig zijn om de implementatie te vervolledigen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="a7a26-145">De volgende secties bevatten informatie over het voorbereiden en de organisatie-verbindingen die waarschijnlijk moet van tevoren gebeuren.</span><span class="sxs-lookup"><span data-stu-id="a7a26-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="a7a26-146">Softwarevereisten</span><span class="sxs-lookup"><span data-stu-id="a7a26-146">Software requirements</span></span>

<span data-ttu-id="a7a26-147">Implementatie van een pull-server vereist de functie DSC-Service van Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="a7a26-148">Deze functie is geïntroduceerd in Windows Server 2012 en via lopende versies van Windows Management Framework (WMF) is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="a7a26-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="a7a26-149">Softwaredownloads</span><span class="sxs-lookup"><span data-stu-id="a7a26-149">Software downloads</span></span>

<span data-ttu-id="a7a26-150">Naast de meest recente inhoud vanaf Windows Update installeert, zijn er twee downloads beschouwd als aanbevolen procedure voor het implementeren van een DSC-pull-server: de meest recente versie van Windows Management Framework en een DSC-module voor het automatiseren van de inrichting van pull-server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="a7a26-151">WMF</span><span class="sxs-lookup"><span data-stu-id="a7a26-151">WMF</span></span>

<span data-ttu-id="a7a26-152">Windows Server 2012 R2 bevat een functie met de naam de DSC-Service.</span><span class="sxs-lookup"><span data-stu-id="a7a26-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="a7a26-153">De functie DSC-Service biedt de functionaliteit pull-server, met inbegrip van de binaire bestanden die ondersteuning bieden voor de OData-eindpunt.</span><span class="sxs-lookup"><span data-stu-id="a7a26-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span>
<span data-ttu-id="a7a26-154">WMF is opgenomen in Windows Server en een flexibele uitgebracht tussen versies van Windows Server wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="a7a26-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span> <span data-ttu-id="a7a26-155">[Nieuwe versies van WMF 5.0](http://aka.ms/wmf5latest) kunt bevatten updates voor de functie DSC-Service.</span><span class="sxs-lookup"><span data-stu-id="a7a26-155">[New versions of WMF 5.0](http://aka.ms/wmf5latest)  can include updates to the DSC Service feature.</span></span> <span data-ttu-id="a7a26-156">Daarom is een aanbevolen procedure voor het downloaden van de nieuwste versie van WMF en om te controleren van de release-opmerkingen om te bepalen of de versie een update op de functie voor DSC-service bevat.</span><span class="sxs-lookup"><span data-stu-id="a7a26-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="a7a26-157">U moet ook de sectie van de release-opmerkingen die aangeeft of de status van het ontwerp voor een update of scenario wordt vermeld als stabiel of experimentele bekijken.</span><span class="sxs-lookup"><span data-stu-id="a7a26-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span>
<span data-ttu-id="a7a26-158">Als u wilt toestaan voor een flexibele releasecyclus afzonderlijke functies worden gedeclareerd stabiele, is wat aangeeft dat de functie gereed om te worden gebruikt in een productieomgeving, zelfs terwijl WMF Preview-versie wordt uitgebracht.</span><span class="sxs-lookup"><span data-stu-id="a7a26-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span>
<span data-ttu-id="a7a26-159">Andere functies die in het verleden zijn bijgewerkt door WMF-versies (Zie de opmerkingen bij de Release van WMF voor verdere details):</span><span class="sxs-lookup"><span data-stu-id="a7a26-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

 - <span data-ttu-id="a7a26-160">Windows PowerShell, Windows PowerShell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="a7a26-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
 - <span data-ttu-id="a7a26-161">Environment (ISE) Windows PowerShell-webservices (Management OData</span><span class="sxs-lookup"><span data-stu-id="a7a26-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
 - <span data-ttu-id="a7a26-162">IIS-extensie) Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="a7a26-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
 - <span data-ttu-id="a7a26-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="a7a26-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="a7a26-164">DSC-resource</span><span class="sxs-lookup"><span data-stu-id="a7a26-164">DSC resource</span></span>

<span data-ttu-id="a7a26-165">De implementatie van een pull-server kan worden vereenvoudigd door de service met een DSC-configuratiescript inricht.</span><span class="sxs-lookup"><span data-stu-id="a7a26-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="a7a26-166">Dit document bevat configuratiescripts die kunnen worden gebruikt voor het implementeren van een knooppunt van de server gereed productie.</span><span class="sxs-lookup"><span data-stu-id="a7a26-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="a7a26-167">Voor het gebruik van de configuratiescripts een DSC-module is vereist dat niet is opgenomen in Windows Server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="a7a26-168">De vereiste modulenaam **xPSDesiredStateConfiguration**, waaronder de DSC-resource **xDscWebService**.</span><span class="sxs-lookup"><span data-stu-id="a7a26-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="a7a26-169">De module xPSDesiredStateConfiguration kan worden gedownload [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span><span class="sxs-lookup"><span data-stu-id="a7a26-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="a7a26-170">Gebruik de **Install-Module** cmdlet uit de **PowerShellGet** module.</span><span class="sxs-lookup"><span data-stu-id="a7a26-170">Use the **Install-Module** cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="a7a26-171">De **PowerShellGet** module zal de module die u wilt downloaden:</span><span class="sxs-lookup"><span data-stu-id="a7a26-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="a7a26-172">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="a7a26-172">Planning task</span></span>|
---|
<span data-ttu-id="a7a26-173">Hebt u toegang tot de installatiebestanden voor Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="a7a26-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>|
<span data-ttu-id="a7a26-174">De implementatieomgeving internettoegang hebben tot WMF en de module downloaden vanaf de on line galerie?</span><span class="sxs-lookup"><span data-stu-id="a7a26-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>|
<span data-ttu-id="a7a26-175">Hoe wordt u de meest recente beveiligingsupdates na de installatie van het besturingssysteem installeren?</span><span class="sxs-lookup"><span data-stu-id="a7a26-175">How will you install the latest security updates after installing the operating system?</span></span>|
<span data-ttu-id="a7a26-176">Wordt de omgeving hebben toegang tot het Internet om updates te downloaden of wordt er een lokale server met Windows Server Update Services (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="a7a26-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>|
<span data-ttu-id="a7a26-177">Hebt u toegang tot Windows Server-installatiebestanden die al updates via offline injectie zijn?</span><span class="sxs-lookup"><span data-stu-id="a7a26-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>|

### <a name="hardware-requirements"></a><span data-ttu-id="a7a26-178">Hardwarevereisten</span><span class="sxs-lookup"><span data-stu-id="a7a26-178">Hardware requirements</span></span>

<span data-ttu-id="a7a26-179">Implementaties van pull-server worden ondersteund op fysieke en virtuele servers.</span><span class="sxs-lookup"><span data-stu-id="a7a26-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="a7a26-180">De sizing vereisten voor pull-server worden uitgelijnd met de vereisten voor Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="a7a26-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

<span data-ttu-id="a7a26-181">Processor: 1,4 GHz, 64-bits processor geheugen: 512 MB aan schijfruimte: 32 GB netwerk: Gigabit Ethernet-Adapter</span><span class="sxs-lookup"><span data-stu-id="a7a26-181">CPU: 1.4 GHz 64-bit processor Memory: 512 MB Disk Space: 32 GB Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="a7a26-182">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="a7a26-182">Planning task</span></span>|
---|
<span data-ttu-id="a7a26-183">U implementeert op fysieke hardware of op een virtualisatieplatform?</span><span class="sxs-lookup"><span data-stu-id="a7a26-183">Will you deploy on physical hardware or on a virtualization platform?</span></span>|
<span data-ttu-id="a7a26-184">Wat is het proces voor het aanvragen van een nieuwe server voor de doelomgeving?</span><span class="sxs-lookup"><span data-stu-id="a7a26-184">What is the process to request a new server for your target environment?</span></span>|
<span data-ttu-id="a7a26-185">Wat is de gemiddelde verwerkingstijd voor een server beschikbaar?</span><span class="sxs-lookup"><span data-stu-id="a7a26-185">What is the average turnaround time for a server to become available?</span></span>|
<span data-ttu-id="a7a26-186">Welke server grootte vraagt u de?</span><span class="sxs-lookup"><span data-stu-id="a7a26-186">What size server will you request?</span></span>|

### <a name="accounts"></a><span data-ttu-id="a7a26-187">Accounts</span><span class="sxs-lookup"><span data-stu-id="a7a26-187">Accounts</span></span>

<span data-ttu-id="a7a26-188">Er zijn geen vereisten voor serviceaccount voor het implementeren van een pull-server-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="a7a26-188">There are no service account requirements to deploy a pull server instance.</span></span>
<span data-ttu-id="a7a26-189">Er zijn echter scenario's waarin de website kan worden uitgevoerd in de context van een lokale gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="a7a26-189">However, there are scenarios where the website could run in the context of a local user account.</span></span>
<span data-ttu-id="a7a26-190">Bijvoorbeeld, als er nodig is toegang tot een storage-share voor website-inhoud en de Windows-Server of het apparaat waarop de storage-share zijn niet verbonden met het domein.</span><span class="sxs-lookup"><span data-stu-id="a7a26-190">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="a7a26-191">DNS-records</span><span class="sxs-lookup"><span data-stu-id="a7a26-191">DNS records</span></span>

<span data-ttu-id="a7a26-192">U moet een servernaam moet worden gebruikt wanneer clients configureren voor gebruik met een pull-server-omgeving.</span><span class="sxs-lookup"><span data-stu-id="a7a26-192">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="a7a26-193">De hostnaam van de server wordt meestal gebruikt in een testomgeving, of het IP-adres voor de server kan worden gebruikt als DNS-naamomzetting niet beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="a7a26-193">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span>
<span data-ttu-id="a7a26-194">In productieomgevingen of in een testomgeving die is bedoeld voor een productie-implementatie, is de aanbevolen procedure om een DNS CNAME-record te maken.</span><span class="sxs-lookup"><span data-stu-id="a7a26-194">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="a7a26-195">Een DNS CNAME kunt u een alias om te verwijzen naar de host-A-record maken.</span><span class="sxs-lookup"><span data-stu-id="a7a26-195">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span>
<span data-ttu-id="a7a26-196">De bedoeling van de naamrecord van de aanvullende is om de flexibiliteit te vergroten, moet een wijziging zijn vereist in de toekomst.</span><span class="sxs-lookup"><span data-stu-id="a7a26-196">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span>
<span data-ttu-id="a7a26-197">Kunt u een CNAME isoleren van configuratie van de client, zodat de wijzigingen in de server-omgeving, zoals een pull-server vervangen of toevoegen van extra pull-servers, is een overeenkomstige wijziging in de configuratie van de client niet vereist.</span><span class="sxs-lookup"><span data-stu-id="a7a26-197">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="a7a26-198">Houd rekening met de oplossingsarchitectuur bij het kiezen van een naam voor de DNS-record.</span><span class="sxs-lookup"><span data-stu-id="a7a26-198">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="a7a26-199">Als met behulp van taakverdeling, wordt het certificaat dat wordt gebruikt om verkeer te beveiligen via HTTPS moet dezelfde naam als de DNS-record.</span><span class="sxs-lookup"><span data-stu-id="a7a26-199">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

<span data-ttu-id="a7a26-200">Scenario</span><span class="sxs-lookup"><span data-stu-id="a7a26-200">Scenario</span></span> |<span data-ttu-id="a7a26-201">Best practices</span><span class="sxs-lookup"><span data-stu-id="a7a26-201">Best Practice</span></span>
:---|:---
<span data-ttu-id="a7a26-202">Testomgeving</span><span class="sxs-lookup"><span data-stu-id="a7a26-202">Test Environment</span></span> |<span data-ttu-id="a7a26-203">De geplande productie-omgeving, indien mogelijk reproduceren.</span><span class="sxs-lookup"><span data-stu-id="a7a26-203">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="a7a26-204">Een hostnaam voor de server is geschikt voor eenvoudige configuraties.</span><span class="sxs-lookup"><span data-stu-id="a7a26-204">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="a7a26-205">Als DNS niet beschikbaar is, kan een IP-adres in plaats van een hostnaam worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a7a26-205">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>|
<span data-ttu-id="a7a26-206">Implementatie van één knooppunt</span><span class="sxs-lookup"><span data-stu-id="a7a26-206">Single Node Deployment</span></span> |<span data-ttu-id="a7a26-207">Maak een DNS CNAME-record die naar de hostnaam van de server verwijst.</span><span class="sxs-lookup"><span data-stu-id="a7a26-207">Create a DNS CNAME record that points to the server hostname.</span></span>|

<span data-ttu-id="a7a26-208">Zie voor meer informatie [DNS Round Robin configureren in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="a7a26-208">For more information, see [Configuring DNS Round Robin in Windows Server](https://technet.microsoft.com/en-us/library/cc787484(v=ws.10).aspx).</span></span>

<span data-ttu-id="a7a26-209">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="a7a26-209">Planning task</span></span>|
---|
<span data-ttu-id="a7a26-210">Weet u contactpersoon om DNS-records gemaakt en gewijzigd?</span><span class="sxs-lookup"><span data-stu-id="a7a26-210">Do you know who to contact to have DNS records created and changed?</span></span>|
<span data-ttu-id="a7a26-211">Wat is de gemiddelde reactietijd voor een aanvraag voor een DNS-record ook?</span><span class="sxs-lookup"><span data-stu-id="a7a26-211">What is the average turnaround for a request for a DNS record?</span></span>|
<span data-ttu-id="a7a26-212">Moet u de statische Hostname-A-records voor servers aanvragen?</span><span class="sxs-lookup"><span data-stu-id="a7a26-212">Do you need to request static Hostname (A) records for servers?</span></span>|
<span data-ttu-id="a7a26-213">Wat u vraagt de als een CNAME?</span><span class="sxs-lookup"><span data-stu-id="a7a26-213">What will you request as a CNAME?</span></span>|
<span data-ttu-id="a7a26-214">Indien nodig, wat voor soort Load Balancing-oplossing wordt u gebruiken?</span><span class="sxs-lookup"><span data-stu-id="a7a26-214">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="a7a26-215">(Zie de sectie taakverdeling voor meer informatie)</span><span class="sxs-lookup"><span data-stu-id="a7a26-215">(see section titled Load Balancing for details)</span></span>|

### <a name="public-key-infrastructure"></a><span data-ttu-id="a7a26-216">Openbare-sleutelinfrastructuur</span><span class="sxs-lookup"><span data-stu-id="a7a26-216">Public Key Infrastructure</span></span>

<span data-ttu-id="a7a26-217">De meeste organisaties vereisen vandaag dat netwerkverkeer, met name verkeer dat dergelijke gevoelige gegevens bevat, hoe servers zijn geconfigureerd, moet worden gevalideerd en/of tijdens de overdracht versleuteld.</span><span class="sxs-lookup"><span data-stu-id="a7a26-217">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="a7a26-218">Het is mogelijk voor het implementeren van een pull-server via HTTP wat vergemakkelijkt clientaanvragen in normale tekst, is het beste beveiligd verkeer via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a7a26-218">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="a7a26-219">De service kan worden geconfigureerd voor het gebruik van HTTPS met behulp van een set parameters in de DSC-resource **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="a7a26-219">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="a7a26-220">Certificaatvereisten voor het beveiligen van HTTPS-verkeer voor pull-server zijn niet anders dan een andere HTTPS-website te beveiligen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-220">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="a7a26-221">De **webserver** sjabloon in een Windows Server Certificate Services voldoet aan de vereiste mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="a7a26-221">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="a7a26-222">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="a7a26-222">Planning task</span></span>|
---|
<span data-ttu-id="a7a26-223">Als certificaataanvragen niet worden geautomatiseerd, die u moet contact op aanvragen van een certificaat?</span><span class="sxs-lookup"><span data-stu-id="a7a26-223">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>|
<span data-ttu-id="a7a26-224">Wat is de gemiddelde reactietijd ook voor de aanvraag?</span><span class="sxs-lookup"><span data-stu-id="a7a26-224">What is the average turnaround for the request?</span></span>|
<span data-ttu-id="a7a26-225">Hoe wordt het certificaatbestand overgedragen voor u?</span><span class="sxs-lookup"><span data-stu-id="a7a26-225">How will the certificate file be transferred to you?</span></span>|
<span data-ttu-id="a7a26-226">Hoe wordt de persoonlijke sleutel van het certificaat worden overgebracht naar u?</span><span class="sxs-lookup"><span data-stu-id="a7a26-226">How will the certificate private key be transferred to you?</span></span>|
<span data-ttu-id="a7a26-227">Hoe lang is de verlooptijd van de standaard?</span><span class="sxs-lookup"><span data-stu-id="a7a26-227">How long is the default expiration time?</span></span>|
<span data-ttu-id="a7a26-228">Hebt u verrekend op een DNS-naam voor de pull-server-omgeving, die u voor de certificaatnaam gebruiken kunt?</span><span class="sxs-lookup"><span data-stu-id="a7a26-228">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>|

### <a name="choosing-an-architecture"></a><span data-ttu-id="a7a26-229">Een architectuur kiezen</span><span class="sxs-lookup"><span data-stu-id="a7a26-229">Choosing an architecture</span></span>

<span data-ttu-id="a7a26-230">Een pull-server kan worden geïmplementeerd via een webservice die zijn gehost op IIS of een SMB-bestandsshare.</span><span class="sxs-lookup"><span data-stu-id="a7a26-230">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="a7a26-231">In de meeste gevallen wordt de optie web service bieden meer flexibiliteit.</span><span class="sxs-lookup"><span data-stu-id="a7a26-231">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="a7a26-232">Het is niet ongewoon is voor HTTPS-verkeer naar de grenzen van netwerken, passeren dat SMB-verkeer is vaak gefilterd of geblokkeerd tussen netwerken.</span><span class="sxs-lookup"><span data-stu-id="a7a26-232">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="a7a26-233">De web-service biedt ook de optie een overeenstemming Server of Web Reporting Manager (zowel onderwerpen worden opgelost in een toekomstige versie van dit document) die bieden een mechanisme voor clients voor statusrapportage terug naar een server voor gecentraliseerde zichtbaarheid op te nemen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-233">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span>
<span data-ttu-id="a7a26-234">SMB biedt een optie voor omgevingen waar beleid bepaalt dat een webserver niet worden gebruikt en voor andere omgevingsvereisten waaruit een Webserverrol ongewenste.</span><span class="sxs-lookup"><span data-stu-id="a7a26-234">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span>
<span data-ttu-id="a7a26-235">In beide gevallen moet u evalueren van de vereisten voor het ondertekenen en versleutelen van verkeer.</span><span class="sxs-lookup"><span data-stu-id="a7a26-235">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="a7a26-236">HTTPS, SMB-ondertekening en IPSEC-beleidsregels zijn alle opties waard.</span><span class="sxs-lookup"><span data-stu-id="a7a26-236">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="a7a26-237">Taakverdeling</span><span class="sxs-lookup"><span data-stu-id="a7a26-237">Load balancing</span></span>
<span data-ttu-id="a7a26-238">Clients communiceren met de webservice indienen voor informatie die in een enkel antwoord wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a7a26-238">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="a7a26-239">Er zijn geen opeenvolgende aanvragen zijn vereist, zodat het niet nodig zijn voor het platform om ervoor te zorgen sessies worden beheerd op één server op elk punt in tijd voor de taakverdeling.</span><span class="sxs-lookup"><span data-stu-id="a7a26-239">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="a7a26-240">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="a7a26-240">Planning task</span></span>|
---|
<span data-ttu-id="a7a26-241">Welke oplossing voor taakverdeling verkeer tussen servers worden gebruikt?</span><span class="sxs-lookup"><span data-stu-id="a7a26-241">What solution will be used for load balancing traffic across servers?</span></span>|
<span data-ttu-id="a7a26-242">Als een load balancer, die een aanvraag voor het toevoegen van een nieuwe configuratie op het apparaat te laten gebruiken?</span><span class="sxs-lookup"><span data-stu-id="a7a26-242">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>|
<span data-ttu-id="a7a26-243">Wat is de gemiddelde reactietijd ook voor een aanvraag voor het configureren van een nieuwe load balanced webservice?</span><span class="sxs-lookup"><span data-stu-id="a7a26-243">What is the average turnaround for a request to configure a new load balanced web service?</span></span>|
<span data-ttu-id="a7a26-244">Welke informatie is alleen vereist voor de aanvraag?</span><span class="sxs-lookup"><span data-stu-id="a7a26-244">What information will be required for the request?</span></span>|
<span data-ttu-id="a7a26-245">U moet aanvragen een extra IP-adres of het team dat verantwoordelijk is voor de taakverdeling wordt afgehandeld die?</span><span class="sxs-lookup"><span data-stu-id="a7a26-245">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>|
<span data-ttu-id="a7a26-246">Hebt u de DNS-records die nodig zijn en wordt dit door het team dat verantwoordelijk is voor het configureren van de oplossing voor taakverdeling worden vereist?</span><span class="sxs-lookup"><span data-stu-id="a7a26-246">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>|
<span data-ttu-id="a7a26-247">De load balancing oplossing vereist dat de PKI worden verwerkt door het apparaat of saldo HTTPS-verkeer, zolang er geen sessievereisten zijn laden?</span><span class="sxs-lookup"><span data-stu-id="a7a26-247">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>|

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="a7a26-248">Fasering configuraties en modules op de pull-server</span><span class="sxs-lookup"><span data-stu-id="a7a26-248">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="a7a26-249">Als onderdeel van de planning van de configuratie, moet u nadenken over welke DSC-modules en configuraties die wordt gehost door de pull-server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-249">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="a7a26-250">Omwille van de planning van de configuratie is het belangrijk dat u basiskennis van het voorbereiden en implementeren van inhoud naar een pull-server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-250">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="a7a26-251">In de toekomst wordt in deze sectie uitgebreid en opgenomen in de Operations Guide voor DSC-Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-251">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span>  <span data-ttu-id="a7a26-252">De handleiding wordt uitgelegd hoe het dagelijkse proces voor het beheren van modules en configuraties gedurende een periode met automation.</span><span class="sxs-lookup"><span data-stu-id="a7a26-252">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="a7a26-253">DSC-modules</span><span class="sxs-lookup"><span data-stu-id="a7a26-253">DSC modules</span></span>
<span data-ttu-id="a7a26-254">Clients die aanvragen van een configuratie moet de vereiste DSC-modules.</span><span class="sxs-lookup"><span data-stu-id="a7a26-254">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="a7a26-255">Een functionaliteit van de pull-server is voor het automatiseren van distributie op verzoek van DSC-modules voor clients.</span><span class="sxs-lookup"><span data-stu-id="a7a26-255">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="a7a26-256">Als u een pull-server mogelijk als een lab of het testen van het concept voor de eerste keer implementeert, gaat u waarschijnlijk afhangen van DSC-modules die beschikbaar via openbare opslagplaatsen zoals de galerie met PowerShell of de PowerShell.org GitHub-opslagplaatsen voor DSC-modules zijn .</span><span class="sxs-lookup"><span data-stu-id="a7a26-256">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="a7a26-257">Het is essentieel dat zelfs voor vertrouwde online-bronnen zoals de PowerShell-galerie, elke module die is gedownload van een openbare opslagplaats moet worden gecontroleerd door iemand met PowerShell-ervaring en kennis van de omgeving waar de modules worden onthouden gebruikt voordat het wordt gebruikt in productie.</span><span class="sxs-lookup"><span data-stu-id="a7a26-257">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="a7a26-258">Tijdens het uitvoeren van deze taak is het een goed moment om te controleren voor elke extra nettolading in de module die zoals documentatie en voorbeeld-scripts kan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="a7a26-258">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="a7a26-259">Zo beperkt u de netwerkbandbreedte per client in de eerste aanvraag wanneer modules worden gedownload via het netwerk van de server met de client.</span><span class="sxs-lookup"><span data-stu-id="a7a26-259">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="a7a26-260">Elke module moet worden verpakt in een specifieke indeling, een ZIP-bestand met de naam ModuleName_Version.zip waarin de nettolading van de module.</span><span class="sxs-lookup"><span data-stu-id="a7a26-260">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="a7a26-261">Nadat het bestand is gekopieerd naar de server die een controlesom-bestand moet worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a7a26-261">After the file is copied to the server a checksum file must be created.</span></span> <span data-ttu-id="a7a26-262">Wanneer clients verbinding met de server maken, wordt de controlesom gebruikt om te controleren of dat de inhoud van de DSC-module niet is gewijzigd sinds het is gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="a7a26-262">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscCheckSum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="a7a26-263">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="a7a26-263">Planning task</span></span>|
---|
<span data-ttu-id="a7a26-264">Als u van plan bent een test- of testomgeving omgeving weet welke scenario's sleutel om te valideren?</span><span class="sxs-lookup"><span data-stu-id="a7a26-264">If you are planning a test or lab environment which scenarios are key to validate?</span></span>|
<span data-ttu-id="a7a26-265">Zijn er openbaar beschikbare modules die bronnen ten aanzien van alles wat die u moet bevatten of u moet uw eigen resources ontwerpen?</span><span class="sxs-lookup"><span data-stu-id="a7a26-265">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>|
<span data-ttu-id="a7a26-266">Uw omgeving internettoegang hebben tot openbare modules ophalen?</span><span class="sxs-lookup"><span data-stu-id="a7a26-266">Will your environment have Internet access to retrieve public modules?</span></span>|
<span data-ttu-id="a7a26-267">Wie is verantwoordelijk voor het controleren van de DSC-modules?</span><span class="sxs-lookup"><span data-stu-id="a7a26-267">Who will be responsible for reviewing DSC modules?</span></span>|
<span data-ttu-id="a7a26-268">Als u van plan bent een productie-omgeving wat u gebruikt als een lokale opslagplaats voor het opslaan van DSC-modules?</span><span class="sxs-lookup"><span data-stu-id="a7a26-268">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>|
<span data-ttu-id="a7a26-269">Een centrale team DSC-modules van App-teams accepteert?</span><span class="sxs-lookup"><span data-stu-id="a7a26-269">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="a7a26-270">Wat is het proces</span><span class="sxs-lookup"><span data-stu-id="a7a26-270">What will the process be?</span></span>|
<span data-ttu-id="a7a26-271">Wordt u verpakking, kopiëren en een controlesom voor gereed is voor productie DSC modules maken met de server uit de opslagplaats van uw bron automatiseren?</span><span class="sxs-lookup"><span data-stu-id="a7a26-271">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>|
<span data-ttu-id="a7a26-272">Kan uw team zijn verantwoordelijk voor het beheren van het automatiseringsplatform?</span><span class="sxs-lookup"><span data-stu-id="a7a26-272">Will your team be responsible for managing the automation platform as well?</span></span>|

#### <a name="dsc-configurations"></a><span data-ttu-id="a7a26-273">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="a7a26-273">DSC configurations</span></span>

<span data-ttu-id="a7a26-274">Het doel van een pull-server is bieden een gecentraliseerde mechanisme voor het distribueren van DSC-configuraties voor client-knooppunten.</span><span class="sxs-lookup"><span data-stu-id="a7a26-274">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="a7a26-275">De configuraties worden opgeslagen op de server als MOF-documenten.</span><span class="sxs-lookup"><span data-stu-id="a7a26-275">The configurations are stored on the server as MOF documents.</span></span>
<span data-ttu-id="a7a26-276">Elk document worden benoemd met een unieke GUID.</span><span class="sxs-lookup"><span data-stu-id="a7a26-276">Each document will be named with a unique GUID.</span></span> <span data-ttu-id="a7a26-277">Wanneer clients verbinding maken met een pull-server worden geconfigureerd, krijgen ze ook de GUID voor de configuratie die moet aanvragen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-277">When clients are configured to connect with a pull server, they are also given the GUID for the configuration they should request.</span></span> <span data-ttu-id="a7a26-278">Dit systeem voor het verwijzen naar configuraties door GUID wordt gegarandeerd dat globale uniekheid en flexibele zodanig is dat een configuratie met een granulatie per knooppunt, of als een configuratie van de functie die veel servers met identieke configuraties omvat kan worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="a7a26-278">This system of referencing configurations by GUID guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="a7a26-279">GUID 's</span><span class="sxs-lookup"><span data-stu-id="a7a26-279">GUIDs</span></span>

<span data-ttu-id="a7a26-280">Planning voor de configuratie van GUID's is waard extra aandacht bij gegevensclassificatie via de implementatie van een pull-server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-280">Planning for configuration GUIDs is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="a7a26-281">Er is geen specifieke vereiste voor het verwerken van GUID's en het proces is waarschijnlijk uniek voor elke omgeving.</span><span class="sxs-lookup"><span data-stu-id="a7a26-281">There is no specific requirement for how to handle GUIDs and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="a7a26-282">Het proces kan variëren van eenvoudige tot complexe: een centraal opgeslagen CSV-bestand, een eenvoudige SQL-tabel, een CMDB of een complexe oplossing integratie met een andere oplossing voor hulpprogramma's of software vereisen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-282">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="a7a26-283">Er zijn twee algemene methoden:</span><span class="sxs-lookup"><span data-stu-id="a7a26-283">There are two general approaches:</span></span>

 - <span data-ttu-id="a7a26-284">**Toewijzen van GUID's per server** : biedt een zekere mate van zekerheid dat de configuratie van elke server afzonderlijk wordt beheerd.</span><span class="sxs-lookup"><span data-stu-id="a7a26-284">**Assigning GUIDs per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="a7a26-285">Dit biedt een niveau van precisie rond updates en kunt werken goed in omgevingen met enkele servers.</span><span class="sxs-lookup"><span data-stu-id="a7a26-285">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
 - <span data-ttu-id="a7a26-286">**Toewijzen van GUID's per serverfunctie** : alle servers die dezelfde functie, zoals webservers, uitvoeren met dezelfde GUID verwijzen naar de vereiste configuratiegegevens.</span><span class="sxs-lookup"><span data-stu-id="a7a26-286">**Assigning GUIDs per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span>  <span data-ttu-id="a7a26-287">Let wel dat als veel servers dezelfde GUID delen, deze zou worden bijgewerkt tegelijkertijd wanneer de configuratie wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="a7a26-287">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

<span data-ttu-id="a7a26-288">De GUID is iets die gevoelige gegevens moeten worden overwogen omdat deze kan worden gebruikt door iemand met kwade bedoelingen intelligence over hoe de servers zijn geïmplementeerd en geconfigureerd in uw omgeving te krijgen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-288">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="a7a26-289">Zie voor meer informatie [veilig toewijzen van GUID's in PowerShell Desired status Pull-configuratiemodus](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span><span class="sxs-lookup"><span data-stu-id="a7a26-289">For more information, see [Securely allocating GUIDs in PowerShell Desired State Configuration Pull Mode](http://blogs.msdn.com/b/powershell/archive/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode.aspx).</span></span>

<span data-ttu-id="a7a26-290">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="a7a26-290">Planning task</span></span>|
---|
<span data-ttu-id="a7a26-291">Wie is verantwoordelijk voor het kopiëren van configuraties in naar de map van de pull-server wanneer ze gereed zijn?</span><span class="sxs-lookup"><span data-stu-id="a7a26-291">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>|
<span data-ttu-id="a7a26-292">Als configuraties zijn gemaakt door een toepassingsteam van, wat het proces is op deze aanlevert?</span><span class="sxs-lookup"><span data-stu-id="a7a26-292">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>|
<span data-ttu-id="a7a26-293">Wordt u gebruikmaken van een opslagplaats voor het opslaan van configuraties als ze worden gemaakt, verschillende teams?</span><span class="sxs-lookup"><span data-stu-id="a7a26-293">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>|
<span data-ttu-id="a7a26-294">Automatiseert het proces van het kopiëren van configuraties naar de server en het maken van een controlesom wanneer ze gereed zijn?</span><span class="sxs-lookup"><span data-stu-id="a7a26-294">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>|
<span data-ttu-id="a7a26-295">Hoe wordt u GUID's toewijzen aan servers of -rollen en waar dit worden opgeslagen?</span><span class="sxs-lookup"><span data-stu-id="a7a26-295">How will you map GUIDs to servers or roles, and where will this be stored?</span></span>|
<span data-ttu-id="a7a26-296">Wat u gebruikt als een proces voor het configureren van clientcomputers en hoe wordt geïntegreerd met uw proces voor het maken en opslaan van de configuratie van GUID's?</span><span class="sxs-lookup"><span data-stu-id="a7a26-296">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration GUIDs?</span></span>|

## <a name="installation-guide"></a><span data-ttu-id="a7a26-297">Installatiehandleiding</span><span class="sxs-lookup"><span data-stu-id="a7a26-297">Installation Guide</span></span>

<span data-ttu-id="a7a26-298">*Scripts die zijn opgegeven in dit document zijn stabiele voorbeelden. Altijd zorgvuldig te controleren scripts voordat deze wordt uitgevoerd in een productieomgeving.*</span><span class="sxs-lookup"><span data-stu-id="a7a26-298">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a7a26-299">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a7a26-299">Prerequisites</span></span>

<span data-ttu-id="a7a26-300">De versie van PowerShell op uw server gebruik de volgende opdracht om te controleren.</span><span class="sxs-lookup"><span data-stu-id="a7a26-300">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="a7a26-301">Indien mogelijk een upgrade uitvoeren naar de nieuwste versie van Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="a7a26-301">If possible, upgrade to the latest version of Windows Management Framework.</span></span>
<span data-ttu-id="a7a26-302">Download vervolgens het `xPsDesiredStateConfiguration` module met behulp van de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="a7a26-302">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>


```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="a7a26-303">De opdracht vraagt naar uw goedkeuring wordt vereist voor het downloaden van de module.</span><span class="sxs-lookup"><span data-stu-id="a7a26-303">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="a7a26-304">Installatie en configuratie-scripts</span><span class="sxs-lookup"><span data-stu-id="a7a26-304">Installation and configuration scripts</span></span>
-

<span data-ttu-id="a7a26-305">De beste methode voor het implementeren van een DSC-pull-server is een DSC-configuratiescript gebruiken.</span><span class="sxs-lookup"><span data-stu-id="a7a26-305">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="a7a26-306">Dit document biedt zowel basisinstellingen die alleen de DSC-webservice configureren en geavanceerde instellingen dat er een Windows Server end-to-end inclusief DSC webservice configureren waaronder scripts.</span><span class="sxs-lookup"><span data-stu-id="a7a26-306">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="a7a26-307">Opmerking: Op dit moment de `xPSDesiredStateConfiguation` DSC-module vereist dat de server moet de landinstelling EN-US.</span><span class="sxs-lookup"><span data-stu-id="a7a26-307">Note:  Currently the `xPSDesiredStateConfiguation` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="a7a26-308">Basisconfiguratie voor Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="a7a26-308">Basic configuration for Windows Server 2012</span></span>
-------------------------------------------
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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="a7a26-309">Geavanceerde configuratie voor Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a7a26-309">Advanced configuration for Windows Server 2012 R2</span></span>

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


### <a name="verify-pull-server-functionality"></a><span data-ttu-id="a7a26-310">Controleer de functionaliteit van de pull-server</span><span class="sxs-lookup"><span data-stu-id="a7a26-310">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the default service URL, you will need to adjust accordingly.
function Verify-DSCPullServer ($fqdn) {
    ([xml](invoke-webrequest "https://$($fqdn):8080/psdscpullserver.svc" | % Content)).service.workspace.collection.href
}
Verify-DSCPullServer 'INSERT SERVER FQDN'

Expected Result:
Action
Module
StatusReport
Node
```

### <a name="configure-clients"></a><span data-ttu-id="a7a26-311">Clients configureren</span><span class="sxs-lookup"><span data-stu-id="a7a26-311">Configure clients</span></span>

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


## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="a7a26-312">Aanvullende verwijzingen, fragmenten en voorbeelden</span><span class="sxs-lookup"><span data-stu-id="a7a26-312">Additional references, snippets, and examples</span></span>

<span data-ttu-id="a7a26-313">Dit voorbeeld toont hoe u handmatig een clientverbinding tot stand (vereist WMF5) voor het testen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-313">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DSCConfiguration –Wait -Verbose
```

<span data-ttu-id="a7a26-314">De [toevoegen DnsServerResourceRecordName](http://bit.ly/1G1H31L) -cmdlet gebruikt voor een type CNAME-record toevoegen aan een DNS-zone.</span><span class="sxs-lookup"><span data-stu-id="a7a26-314">The [Add-DnsServerResourceRecordName](http://bit.ly/1G1H31L) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="a7a26-315">De functie PowerShell [een controlesom en DSC-MOF publiceren met SMB Pull-Server maken](http://bit.ly/1E46BhI) genereert automatisch de vereiste controlesom en kopieert u de configuratie van de MOF- en controlesom bestanden naar de SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="a7a26-315">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](http://bit.ly/1E46BhI) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="a7a26-316">Bijlage - Understanding ODATA-servicegegevens bestandstypen</span><span class="sxs-lookup"><span data-stu-id="a7a26-316">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="a7a26-317">Een bestand wordt opgeslagen als u wilt maken van gegevens tijdens de implementatie van een pull-server met de OData-webservice.</span><span class="sxs-lookup"><span data-stu-id="a7a26-317">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="a7a26-318">Het type bestand is afhankelijk van het besturingssysteem, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="a7a26-318">The type of file depends on the operating system, as described below.</span></span>

 - <span data-ttu-id="a7a26-319">**Windows Server 2012** het bestandstype worden altijd .mdb</span><span class="sxs-lookup"><span data-stu-id="a7a26-319">**Windows Server 2012** The file type will always be   .mdb</span></span>
 - <span data-ttu-id="a7a26-320">**Windows Server 2012 R2** het bestandstype wordt standaard edb tenzij een .mdb is opgegeven in de configuratie</span><span class="sxs-lookup"><span data-stu-id="a7a26-320">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="a7a26-321">In de [voorbeeldscript geavanceerde](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) voor het installeren van een Pull-Server, vindt u ook een voorbeeld van hoe u kunt de instellingen van het bestand web.config om te voorkomen dat een kans van de fout is veroorzaakt door het bestandstype automatisch te bepalen.</span><span class="sxs-lookup"><span data-stu-id="a7a26-321">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>