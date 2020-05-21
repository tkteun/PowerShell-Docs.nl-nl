---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Best practices voor pull-servers
ms.openlocfilehash: 2d707dc64c327cf30d09104aee140e5b78ee7c29
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692249"
---
# <a name="pull-server-best-practices"></a><span data-ttu-id="afda7-103">Best practices voor pull-servers</span><span class="sxs-lookup"><span data-stu-id="afda7-103">Pull server best practices</span></span>

<span data-ttu-id="afda7-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="afda7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="afda7-105">De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="afda7-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="afda7-106">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="afda7-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="afda7-107">Samen vatting: dit document is bedoeld om proces en uitbreid baarheid te omvatten om de technici te helpen bij het voorbereiden van de oplossing.</span><span class="sxs-lookup"><span data-stu-id="afda7-107">Summary: This document is intended to include process and extensibility to assist engineers who are preparing for the solution.</span></span> <span data-ttu-id="afda7-108">Details moeten aanbevolen procedures bieden die door klanten worden geïdentificeerd en vervolgens door het product team worden gevalideerd om ervoor te zorgen dat aanbevelingen op de toekomst worden gericht en stabiel worden beschouwd.</span><span class="sxs-lookup"><span data-stu-id="afda7-108">Details should provide best practices as identified by customers and then validated by the product team to ensure recommendations are future facing and considered stable.</span></span>

|           |                      <span data-ttu-id="afda7-109">Doc-info</span><span class="sxs-lookup"><span data-stu-id="afda7-109">Doc Info</span></span>                      |
| :-------- | :------------------------------------------------- |
| <span data-ttu-id="afda7-110">Auteur</span><span class="sxs-lookup"><span data-stu-id="afda7-110">Author</span></span>    | <span data-ttu-id="afda7-111">Michael Greene</span><span class="sxs-lookup"><span data-stu-id="afda7-111">Michael Greene</span></span>                                     |
| <span data-ttu-id="afda7-112">Revisoren</span><span class="sxs-lookup"><span data-stu-id="afda7-112">Reviewers</span></span> | <span data-ttu-id="afda7-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span><span class="sxs-lookup"><span data-stu-id="afda7-113">Ben Gelens, Ravikanth Chaganti, Aleksandar Nikolic</span></span> |
| <span data-ttu-id="afda7-114">Gepubliceerd</span><span class="sxs-lookup"><span data-stu-id="afda7-114">Published</span></span> | <span data-ttu-id="afda7-115">April, 2015</span><span class="sxs-lookup"><span data-stu-id="afda7-115">April, 2015</span></span>                                        |

## <a name="abstract"></a><span data-ttu-id="afda7-116">Abstract</span><span class="sxs-lookup"><span data-stu-id="afda7-116">Abstract</span></span>

<span data-ttu-id="afda7-117">Dit document is ontworpen om officiële richt lijnen te bieden voor iedereen die een Windows Power shell desired state Configuration pull-Server implementatie moet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="afda7-117">This document is designed to provide official guidance for anyone planning for a Windows PowerShell Desired State Configuration pull server implementation.</span></span> <span data-ttu-id="afda7-118">Een pull-server is een eenvoudige service die slechts enkele minuten mag duren om te implementeren.</span><span class="sxs-lookup"><span data-stu-id="afda7-118">A pull server is a simple service that should take only minutes to deploy.</span></span> <span data-ttu-id="afda7-119">Hoewel dit document technische instructies biedt die kunnen worden gebruikt in een implementatie, is de waarde van dit document als referentie voor de aanbevolen procedures en wat u moet nadenken voordat u implementeert.</span><span class="sxs-lookup"><span data-stu-id="afda7-119">Although this document will offer technical how-to guidance that can be used in a deployment, the value of this document is as a reference for best practices and what to think about before deploying.</span></span> <span data-ttu-id="afda7-120">Lezers moeten basis kennis hebben van DSC en de voor waarden die worden gebruikt voor het beschrijven van de onderdelen die zijn opgenomen in een DSC-implementatie.</span><span class="sxs-lookup"><span data-stu-id="afda7-120">Readers should have basic familiarity with DSC, and the terms used to describe the components that are included in a DSC deployment.</span></span> <span data-ttu-id="afda7-121">Zie het onderwerp [Windows Power shell desired state Configuration (overzicht](/powershell/scripting/dsc/overview/overview) ) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="afda7-121">For more information, see the [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/overview) topic.</span></span> <span data-ttu-id="afda7-122">Aangezien DSC wordt verwacht te ontwikkelen in de Cloud uitgebracht, wordt de onderliggende technologie, inclusief Pull-server, ook verwacht om nieuwe mogelijkheden te ontwikkelen en te introduceren.</span><span class="sxs-lookup"><span data-stu-id="afda7-122">As DSC is expected to evolve at cloud cadence, the underlying technology including pull server is also expected to evolve and to introduce new capabilities.</span></span> <span data-ttu-id="afda7-123">Dit document bevat een versie tabel in de bijlage die verwijzingen bevat naar eerdere releases en verwijzingen naar toekomstige oplossingen om voorwaartse ontwerpen te stimuleren.</span><span class="sxs-lookup"><span data-stu-id="afda7-123">This document includes a version table in the appendix that provides references to previous releases and references to future looking solutions to encourage forward-looking designs.</span></span>

<span data-ttu-id="afda7-124">De twee belangrijkste secties van dit document:</span><span class="sxs-lookup"><span data-stu-id="afda7-124">The two major sections of this document:</span></span>

- <span data-ttu-id="afda7-125">Configuratie planning</span><span class="sxs-lookup"><span data-stu-id="afda7-125">Configuration Planning</span></span>
- <span data-ttu-id="afda7-126">Installatiehandleiding</span><span class="sxs-lookup"><span data-stu-id="afda7-126">Installation Guide</span></span>

### <a name="versions-of-the-windows-management-framework"></a><span data-ttu-id="afda7-127">Versies van het Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="afda7-127">Versions of the Windows Management Framework</span></span>

<span data-ttu-id="afda7-128">De informatie in dit document is bedoeld voor toepassing op Windows Management Framework 5,0.</span><span class="sxs-lookup"><span data-stu-id="afda7-128">The information in this document is intended to apply to Windows Management Framework 5.0.</span></span> <span data-ttu-id="afda7-129">Hoewel WMF 5,0 niet is vereist voor het implementeren en gebruiken van een pull-server, is versie 5,0 de focus van dit document.</span><span class="sxs-lookup"><span data-stu-id="afda7-129">While WMF 5.0 is not required for deploying and operating a pull server, version 5.0 is the focus of this document.</span></span>

### <a name="windows-powershell-desired-state-configuration"></a><span data-ttu-id="afda7-130">Windows Power shell desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="afda7-130">Windows PowerShell Desired State Configuration</span></span>

<span data-ttu-id="afda7-131">Desired state Configuration (DSC) is een beheer platform waarmee configuratie gegevens kunnen worden geïmplementeerd en beheerd met behulp van een industrie syntaxis met de naam de Managed Object Format (MOF) om de Common Information Model (CIM) te beschrijven.</span><span class="sxs-lookup"><span data-stu-id="afda7-131">Desired State Configuration (DSC) is a management platform that enables deploying and managing configuration data by using an industry syntax named the Managed Object Format (MOF) to describe the Common Information Model (CIM).</span></span> <span data-ttu-id="afda7-132">Een open-source project, open Management Infrastructure (OMI), bestaat uit het verder ontwikkelen van deze standaarden op verschillende platforms, waaronder Linux en netwerkhardware.</span><span class="sxs-lookup"><span data-stu-id="afda7-132">An open source project, Open Management Infrastructure (OMI), exists to further development of these standards across platforms including Linux and network hardware operating systems.</span></span> <span data-ttu-id="afda7-133">Zie voor meer informatie de [DMTF-pagina koppelen aan MOF-specificaties](https://www.dmtf.org/standards/cim)en [Omi-documenten en-bron](https://collaboration.opengroup.org/omi/documents.php).</span><span class="sxs-lookup"><span data-stu-id="afda7-133">For more information, see the [DMTF page linking to MOF specifications](https://www.dmtf.org/standards/cim), and [OMI Documents and Source](https://collaboration.opengroup.org/omi/documents.php).</span></span>

<span data-ttu-id="afda7-134">Windows Power shell biedt een set taal extensies voor desired state Configuration, die u kunt gebruiken om declaratieve configuraties te maken en te beheren.</span><span class="sxs-lookup"><span data-stu-id="afda7-134">Windows PowerShell provides a set of language extensions for Desired State Configuration that you can use to create and manage declarative configurations.</span></span>

### <a name="pull-server-role"></a><span data-ttu-id="afda7-135">Server functie pull</span><span class="sxs-lookup"><span data-stu-id="afda7-135">Pull server role</span></span>

<span data-ttu-id="afda7-136">Een pull-server biedt een gecentraliseerde service voor het opslaan van configuraties die toegankelijk zijn voor doel knooppunten.</span><span class="sxs-lookup"><span data-stu-id="afda7-136">A pull server provides a centralized service to store configurations that will be accessible to target nodes.</span></span>

<span data-ttu-id="afda7-137">De rol van de pull-server kan worden geïmplementeerd als een webserver instantie of een SMB-bestands share.</span><span class="sxs-lookup"><span data-stu-id="afda7-137">The pull server role can be deployed as either a Web Server instance or an SMB file share.</span></span> <span data-ttu-id="afda7-138">De webserver-functionaliteit bevat een OData-interface en kan eventueel mogelijkheden voor doel knooppunten bevatten om de bevestiging van het slagen of mislukken van de toepassing te rapporteren.</span><span class="sxs-lookup"><span data-stu-id="afda7-138">The web server capability includes an OData interface and can optionally include capabilities for target nodes to report back confirmation of success or failure as configurations are applied.</span></span> <span data-ttu-id="afda7-139">Deze functionaliteit is handig in omgevingen waar zich een groot aantal doel knooppunten bevindt.</span><span class="sxs-lookup"><span data-stu-id="afda7-139">This functionality is useful in environments where there are a large number of target nodes.</span></span> <span data-ttu-id="afda7-140">Na het configureren van een doel knooppunt (ook wel een client genoemd) om naar de pull-server te verwijzen, worden de nieuwste configuratie gegevens en eventuele vereiste scripts gedownload en toegepast.</span><span class="sxs-lookup"><span data-stu-id="afda7-140">After configuring a target node (also referred to as a client) to point to the pull server the latest configuration data and any required scripts are downloaded and applied.</span></span> <span data-ttu-id="afda7-141">Dit kan gebeuren als een eenmalige implementatie of als een nieuwe taak, waardoor de pull-server ook een belang rijk activum vormt voor het beheer van wijzigingen op schaal.</span><span class="sxs-lookup"><span data-stu-id="afda7-141">This can happen as a one-time deployment or as a re-occurring job which also makes the pull server an important asset for managing change at scale.</span></span> <span data-ttu-id="afda7-142">Zie voor meer informatie [Windows Power shell desired state Configuration pull servers](pullserver.md) en [push and pull Configuration mode](pullserver.md)(Engelstalig).</span><span class="sxs-lookup"><span data-stu-id="afda7-142">For more information, see [Windows PowerShell Desired State Configuration Pull Servers](pullserver.md) and [Push and Pull Configuration Modes](pullserver.md).</span></span>

## <a name="configuration-planning"></a><span data-ttu-id="afda7-143">Configuratie planning</span><span class="sxs-lookup"><span data-stu-id="afda7-143">Configuration planning</span></span>

<span data-ttu-id="afda7-144">Voor elke implementatie van een bedrijfs software is er informatie die van tevoren kan worden verzameld om te helpen bij het plannen van de juiste architectuur en om voor te bereiden op de stappen die nodig zijn om de implementatie te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="afda7-144">For any enterprise software deployment there is information that can be collected in advance to help plan for the correct architecture and to be prepared for the steps required to complete the deployment.</span></span> <span data-ttu-id="afda7-145">De volgende secties bevatten informatie over de voor bereiding en de organisatie verbindingen die waarschijnlijk van tevoren moeten plaatsvinden.</span><span class="sxs-lookup"><span data-stu-id="afda7-145">The following sections provide information regarding how to prepare and the organizational connections that will likely need to happen in advance.</span></span>

### <a name="software-requirements"></a><span data-ttu-id="afda7-146">Softwarevereisten</span><span class="sxs-lookup"><span data-stu-id="afda7-146">Software requirements</span></span>

<span data-ttu-id="afda7-147">De implementatie van een pull-server vereist de DSC-service functie van Windows Server.</span><span class="sxs-lookup"><span data-stu-id="afda7-147">Deployment of a pull server requires the DSC Service feature of Windows Server.</span></span> <span data-ttu-id="afda7-148">Deze functie is geïntroduceerd in Windows Server 2012 en is bijgewerkt via de doorlopende versies van Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="afda7-148">This feature was introduced in Windows Server 2012, and has been updated through ongoing releases of Windows Management Framework (WMF).</span></span>

### <a name="software-downloads"></a><span data-ttu-id="afda7-149">Software downloads</span><span class="sxs-lookup"><span data-stu-id="afda7-149">Software downloads</span></span>

<span data-ttu-id="afda7-150">Naast het installeren van de meest recente inhoud van Windows Update, worden er twee down loads beschouwd als best practice voor het implementeren van een DSC-pull-server: de nieuwste versie van Windows Management Framework en een DSC-module voor het automatiseren van het inrichten van pull-servers.</span><span class="sxs-lookup"><span data-stu-id="afda7-150">In addition to installing the latest content from Windows Update, there are two downloads considered best practice to deploy a DSC pull server: The latest version of Windows Management Framework, and a DSC module to automate pull server provisioning.</span></span>

### <a name="wmf"></a><span data-ttu-id="afda7-151">WMF</span><span class="sxs-lookup"><span data-stu-id="afda7-151">WMF</span></span>

<span data-ttu-id="afda7-152">Windows Server 2012 R2 bevat een functie met de naam DSC-service.</span><span class="sxs-lookup"><span data-stu-id="afda7-152">Windows Server 2012 R2 includes a feature named the DSC Service.</span></span> <span data-ttu-id="afda7-153">De functie DSC-service biedt de functionaliteit van de pull-server, met inbegrip van de binaire bestanden die ondersteuning bieden voor het OData-eind punt.</span><span class="sxs-lookup"><span data-stu-id="afda7-153">The DSC Service feature provides the pull server functionality, including the binaries that support the OData endpoint.</span></span> <span data-ttu-id="afda7-154">WMF is opgenomen in Windows Server en wordt bijgewerkt op een flexibele uitgebracht tussen Windows Server-releases.</span><span class="sxs-lookup"><span data-stu-id="afda7-154">WMF is included in Windows Server and is updated on an agile cadence between Windows Server releases.</span></span>
<span data-ttu-id="afda7-155">[Nieuwe versies van WMF 5,0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) kunnen updates bevatten voor de functie DSC-service.</span><span class="sxs-lookup"><span data-stu-id="afda7-155">[New versions of WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=54616) can include updates to the DSC Service feature.</span></span> <span data-ttu-id="afda7-156">Daarom is het een best practice om de meest recente versie van WMF te downloaden en de release opmerkingen te bekijken om te bepalen of de release een update voor de DSC-service functie bevat.</span><span class="sxs-lookup"><span data-stu-id="afda7-156">For this reason, it is a best practice to download the latest release of WMF and to review the release notes to determine if the release includes an update to the DSC service feature.</span></span> <span data-ttu-id="afda7-157">U moet ook de sectie van de release-opmerkingen door nemen die aangeven of de ontwerp status voor een update of scenario wordt weer gegeven als stabiel of experimenteel.</span><span class="sxs-lookup"><span data-stu-id="afda7-157">You should also review the section of the release notes that indicates whether the design status for an update or scenario is listed as stable or experimental.</span></span> <span data-ttu-id="afda7-158">Om een flexibele release cyclus mogelijk te maken, kunnen afzonderlijke functies worden gedeclareerd als stabiel, wat aangeeft dat de functie gereed is om te worden gebruikt in een productie omgeving, zelfs wanneer WMF in Preview wordt uitgebracht.</span><span class="sxs-lookup"><span data-stu-id="afda7-158">To allow for an agile release cycle, individual features can be declared stable, which indicates the feature is ready to be used in a production environment even while WMF is released in preview.</span></span> <span data-ttu-id="afda7-159">Andere functies die historisch zijn bijgewerkt door WMF-releases (zie opmerkingen bij de WMF-release voor meer informatie):</span><span class="sxs-lookup"><span data-stu-id="afda7-159">Other features that have historically been updated by WMF releases (see the WMF Release Notes for further detail):</span></span>

- <span data-ttu-id="afda7-160">Windows Power shell Windows Power shell Integrated Scripting</span><span class="sxs-lookup"><span data-stu-id="afda7-160">Windows PowerShell Windows PowerShell Integrated Scripting</span></span>
- <span data-ttu-id="afda7-161">Environment (ISE) Windows Power shell-webservices (Management OData</span><span class="sxs-lookup"><span data-stu-id="afda7-161">Environment (ISE) Windows PowerShell Web Services (Management OData</span></span>
- <span data-ttu-id="afda7-162">IIS-uitbrei ding) Windows Power shell desired state Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="afda7-162">IIS Extension)  Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="afda7-163">Windows Management Instrumentation van Windows Remote Management (WinRM) (WMI)</span><span class="sxs-lookup"><span data-stu-id="afda7-163">Windows Remote Management (WinRM) Windows Management Instrumentation (WMI)</span></span>

### <a name="dsc-resource"></a><span data-ttu-id="afda7-164">DSC-resource</span><span class="sxs-lookup"><span data-stu-id="afda7-164">DSC resource</span></span>

<span data-ttu-id="afda7-165">Een pull-Server implementatie kan worden vereenvoudigd door de service in te richten met behulp van een DSC-configuratie script.</span><span class="sxs-lookup"><span data-stu-id="afda7-165">A pull server deployment can be simplified by provisioning the service using a DSC configuration script.</span></span> <span data-ttu-id="afda7-166">Dit document bevat configuratie scripts die kunnen worden gebruikt voor het implementeren van een server knooppunt dat gereed is voor productie.</span><span class="sxs-lookup"><span data-stu-id="afda7-166">This document includes configuration scripts that can be used to deploy a production ready server node.</span></span> <span data-ttu-id="afda7-167">Als u de configuratie scripts wilt gebruiken, is een DSC-module vereist die niet is opgenomen in Windows Server.</span><span class="sxs-lookup"><span data-stu-id="afda7-167">To use the configuration scripts, a DSC module is required that is not included in Windows Server.</span></span> <span data-ttu-id="afda7-168">De vereiste module naam is **xPSDesiredStateConfiguration**, die de DSC-resource **xDscWebService**bevat.</span><span class="sxs-lookup"><span data-stu-id="afda7-168">The required module name is **xPSDesiredStateConfiguration**, which includes the DSC resource **xDscWebService**.</span></span> <span data-ttu-id="afda7-169">De xPSDesiredStateConfiguration-module kan [hier](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d)worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="afda7-169">The xPSDesiredStateConfiguration module can be downloaded [here](https://gallery.technet.microsoft.com/xPSDesiredStateConfiguratio-417dc71d).</span></span>

<span data-ttu-id="afda7-170">Gebruik de `Install-Module` cmdlet uit de **PowerShellGet** -module.</span><span class="sxs-lookup"><span data-stu-id="afda7-170">Use the `Install-Module` cmdlet from the **PowerShellGet** module.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="afda7-171">De module **PowerShellGet** wordt door de module gedownload naar:</span><span class="sxs-lookup"><span data-stu-id="afda7-171">The **PowerShellGet** module will download the module to:</span></span>

`C:\Program Files\Windows PowerShell\Modules`

<span data-ttu-id="afda7-172">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="afda7-172">Planning task</span></span>

- <span data-ttu-id="afda7-173">Hebt u toegang tot de installatie bestanden voor Windows Server 2012 R2?</span><span class="sxs-lookup"><span data-stu-id="afda7-173">Do you have access to the installation files for Windows Server 2012 R2?</span></span>
- <span data-ttu-id="afda7-174">Heeft de implementatie omgeving via internet toegang tot het downloaden van WMF en de module vanuit de online galerie?</span><span class="sxs-lookup"><span data-stu-id="afda7-174">Will the deployment environment have Internet access to download WMF and the module from the online gallery?</span></span>
- <span data-ttu-id="afda7-175">Hoe installeert u de nieuwste beveiligings updates na de installatie van het besturings systeem?</span><span class="sxs-lookup"><span data-stu-id="afda7-175">How will you install the latest security updates after installing the operating system?</span></span>
- <span data-ttu-id="afda7-176">Heeft de omgeving Internet toegang om updates te verkrijgen of heeft deze een lokale Windows Server Update Services server (WSUS)?</span><span class="sxs-lookup"><span data-stu-id="afda7-176">Will the environment have Internet access to obtain updates, or will it have a local Windows Server Update Services (WSUS) server?</span></span>
- <span data-ttu-id="afda7-177">Hebt u toegang tot installatie bestanden van Windows Server die al updates bevatten via offline injectie?</span><span class="sxs-lookup"><span data-stu-id="afda7-177">Do you have access to Windows Server installation files that already include updates through offline injection?</span></span>

### <a name="hardware-requirements"></a><span data-ttu-id="afda7-178">Hardwarevereisten</span><span class="sxs-lookup"><span data-stu-id="afda7-178">Hardware requirements</span></span>

<span data-ttu-id="afda7-179">Pull-server implementaties worden ondersteund op zowel fysieke als virtuele servers.</span><span class="sxs-lookup"><span data-stu-id="afda7-179">Pull server deployments are supported on both physical and virtual servers.</span></span> <span data-ttu-id="afda7-180">De grootte vereisten voor pull-server worden uitgelijnd met de vereisten voor Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="afda7-180">The sizing requirements for pull server align with the requirements for Windows Server 2012 R2.</span></span>

- <span data-ttu-id="afda7-181">CPU: 1,4 GHz 64-bits processor</span><span class="sxs-lookup"><span data-stu-id="afda7-181">CPU: 1.4 GHz 64-bit processor</span></span>
- <span data-ttu-id="afda7-182">Geheugen: 512 MB</span><span class="sxs-lookup"><span data-stu-id="afda7-182">Memory: 512 MB</span></span>
- <span data-ttu-id="afda7-183">Schijf ruimte: 32 GB</span><span class="sxs-lookup"><span data-stu-id="afda7-183">Disk Space: 32 GB</span></span>
- <span data-ttu-id="afda7-184">Netwerk: Gigabit Ethernet-adapter</span><span class="sxs-lookup"><span data-stu-id="afda7-184">Network: Gigabit Ethernet Adapter</span></span>

<span data-ttu-id="afda7-185">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="afda7-185">Planning task</span></span>

- <span data-ttu-id="afda7-186">Gaat u implementeren op fysieke hardware of op een virtualisatieplatform?</span><span class="sxs-lookup"><span data-stu-id="afda7-186">Will you deploy on physical hardware or on a virtualization platform?</span></span>
- <span data-ttu-id="afda7-187">Wat is het proces voor het aanvragen van een nieuwe server voor uw doel omgeving?</span><span class="sxs-lookup"><span data-stu-id="afda7-187">What is the process to request a new server for your target environment?</span></span>
- <span data-ttu-id="afda7-188">Wat is de gemiddelde verlever tijd voor een server die beschikbaar moet zijn?</span><span class="sxs-lookup"><span data-stu-id="afda7-188">What is the average turnaround time for a server to become available?</span></span>
- <span data-ttu-id="afda7-189">Welke grootte wilt u aanvragen voor de server?</span><span class="sxs-lookup"><span data-stu-id="afda7-189">What size server will you request?</span></span>

### <a name="accounts"></a><span data-ttu-id="afda7-190">Accounts</span><span class="sxs-lookup"><span data-stu-id="afda7-190">Accounts</span></span>

<span data-ttu-id="afda7-191">Er zijn geen service account vereisten voor het implementeren van een pull-Server exemplaar.</span><span class="sxs-lookup"><span data-stu-id="afda7-191">There are no service account requirements to deploy a pull server instance.</span></span> <span data-ttu-id="afda7-192">Er zijn echter scenario's waarin de website kan worden uitgevoerd in de context van een lokale gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="afda7-192">However, there are scenarios where the website could run in the context of a local user account.</span></span> <span data-ttu-id="afda7-193">Als er bijvoorbeeld een opslag share nodig is voor de inhoud van de website en de Windows-Server of het apparaat dat als host fungeert voor de opslag share, geen lid is van een domein.</span><span class="sxs-lookup"><span data-stu-id="afda7-193">For example, if there is a need to access a storage share for website content and either the Windows Server or the device hosting the storage share are not domain joined.</span></span>

### <a name="dns-records"></a><span data-ttu-id="afda7-194">DNS-records</span><span class="sxs-lookup"><span data-stu-id="afda7-194">DNS records</span></span>

<span data-ttu-id="afda7-195">U hebt een server naam nodig om te gebruiken bij het configureren van clients om met een pull-server omgeving te werken.</span><span class="sxs-lookup"><span data-stu-id="afda7-195">You will need a server name to use when configuring clients to work with a pull server environment.</span></span>
<span data-ttu-id="afda7-196">In test omgevingen wordt doorgaans de hostnaam van de server gebruikt, of het IP-adres voor de server kan worden gebruikt als de DNS-naam omzetting niet beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="afda7-196">In test environments, typically the server hostname is used, or the IP address for the server can be used if DNS name resolution is not available.</span></span> <span data-ttu-id="afda7-197">In productie omgevingen of in een test omgeving die bedoeld is voor een productie-implementatie, bestaat de best practice uit het maken van een DNS CNAME-record.</span><span class="sxs-lookup"><span data-stu-id="afda7-197">In production environments or in a lab environment that is intended to represent a production deployment, the best practice is to create a DNS CNAME record.</span></span>

<span data-ttu-id="afda7-198">Met een DNS-CNAME kunt u een alias maken om te verwijzen naar uw host (A)-record.</span><span class="sxs-lookup"><span data-stu-id="afda7-198">A DNS CNAME allows you to create an alias to refer to your host (A) record.</span></span> <span data-ttu-id="afda7-199">Het doel van de aanvullende naam record is om de flexibiliteit te verg Roten, omdat een wijziging in de toekomst nood zakelijk is.</span><span class="sxs-lookup"><span data-stu-id="afda7-199">The intent of the additional name record is to increase flexibility should a change be required in the future.</span></span> <span data-ttu-id="afda7-200">Een CNAME kan u helpen de client configuratie te isoleren zodat wijzigingen in de server omgeving, zoals het vervangen van een pull-server of het toevoegen van extra pull-servers, geen overeenkomstige wijziging in de client configuratie nodig heeft.</span><span class="sxs-lookup"><span data-stu-id="afda7-200">A CNAME can help to isolate the client configuration so that changes to the server environment, such as replacing a pull server or adding additional pull servers, will not require a corresponding change to the client configuration.</span></span>

<span data-ttu-id="afda7-201">Houd bij het kiezen van een naam voor de DNS-record de oplossings architectuur in acht.</span><span class="sxs-lookup"><span data-stu-id="afda7-201">When choosing a name for the DNS record, keep the solution architecture in mind.</span></span>
<span data-ttu-id="afda7-202">Als taak verdeling wordt gebruikt, moet het certificaat dat wordt gebruikt voor het beveiligen van verkeer via HTTPS dezelfde naam hebben als de DNS-record.</span><span class="sxs-lookup"><span data-stu-id="afda7-202">If using load balancing, the certificate used to secure traffic over HTTPS will need to share the same name as the DNS record.</span></span>

|       <span data-ttu-id="afda7-203">Scenario</span><span class="sxs-lookup"><span data-stu-id="afda7-203">Scenario</span></span>        |                                                                                         <span data-ttu-id="afda7-204">Best Practice</span><span class="sxs-lookup"><span data-stu-id="afda7-204">Best Practice</span></span>
|:--------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
|<span data-ttu-id="afda7-205">Testomgeving</span><span class="sxs-lookup"><span data-stu-id="afda7-205">Test Environment</span></span>       | <span data-ttu-id="afda7-206">Reproduceer, indien mogelijk, de geplande productie omgeving.</span><span class="sxs-lookup"><span data-stu-id="afda7-206">Reproduce the planned production environment, if possible.</span></span> <span data-ttu-id="afda7-207">Een hostnaam van een server is geschikt voor eenvoudige configuraties.</span><span class="sxs-lookup"><span data-stu-id="afda7-207">A server hostname is suitable for simple configurations.</span></span> <span data-ttu-id="afda7-208">Als DNS niet beschikbaar is, kan een IP-adres worden gebruikt in plaats van een hostnaam.</span><span class="sxs-lookup"><span data-stu-id="afda7-208">If DNS is not available, an IP address may be used in lieu of a hostname.</span></span>
|<span data-ttu-id="afda7-209">Implementatie met één knoop punt</span><span class="sxs-lookup"><span data-stu-id="afda7-209">Single Node Deployment</span></span> | <span data-ttu-id="afda7-210">Maak een DNS CNAME-record die verwijst naar de hostnaam van de server.</span><span class="sxs-lookup"><span data-stu-id="afda7-210">Create a DNS CNAME record that points to the server hostname.</span></span>

<span data-ttu-id="afda7-211">Zie [Configuring DNS round robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10))(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="afda7-211">For more information, see [Configuring DNS Round Robin in Windows Server](/previous-versions/windows/it-pro/windows-server-2003/cc787484(v=ws.10)).</span></span>

<span data-ttu-id="afda7-212">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="afda7-212">Planning task</span></span>

- <span data-ttu-id="afda7-213">Weet u met wie u contact moet opnemen om DNS-records te maken en te wijzigen?</span><span class="sxs-lookup"><span data-stu-id="afda7-213">Do you know who to contact to have DNS records created and changed?</span></span>
- <span data-ttu-id="afda7-214">Wat is de gemiddelde oplever van een aanvraag voor een DNS-record?</span><span class="sxs-lookup"><span data-stu-id="afda7-214">What is the average turnaround for a request for a DNS record?</span></span>
- <span data-ttu-id="afda7-215">Moet u statische hostname-records (A) aanvragen voor servers?</span><span class="sxs-lookup"><span data-stu-id="afda7-215">Do you need to request static Hostname (A) records for servers?</span></span>
- <span data-ttu-id="afda7-216">Wat gaat u aanvragen als een CNAME?</span><span class="sxs-lookup"><span data-stu-id="afda7-216">What will you request as a CNAME?</span></span>
- <span data-ttu-id="afda7-217">Als dat niet het geval is, welk type taakverdelings oplossing gebruikt u?</span><span class="sxs-lookup"><span data-stu-id="afda7-217">If needed, what type of Load Balancing solution will you utilize?</span></span> <span data-ttu-id="afda7-218">(Zie de sectie taak verdeling voor meer informatie)</span><span class="sxs-lookup"><span data-stu-id="afda7-218">(see section titled Load Balancing for details)</span></span>

### <a name="public-key-infrastructure"></a><span data-ttu-id="afda7-219">Open bare-sleutel infrastructuur</span><span class="sxs-lookup"><span data-stu-id="afda7-219">Public Key Infrastructure</span></span>

<span data-ttu-id="afda7-220">Voor de meeste organisaties moet het netwerk verkeer, met name verkeer dat gevoelige gegevens bevat, worden gevalideerd en/of versleuteld tijdens de overdracht.</span><span class="sxs-lookup"><span data-stu-id="afda7-220">Most organizations today require that network traffic, especially traffic that includes such sensitive data as how servers are configured, must be validated and/or encrypted during transit.</span></span>
<span data-ttu-id="afda7-221">Hoewel het mogelijk is om een pull-server te implementeren met behulp van HTTP, waardoor aanvragen van clients worden vereenvoudigd als ongecodeerde tekst, is het een best practice om verkeer te beveiligen met behulp van HTTPS.</span><span class="sxs-lookup"><span data-stu-id="afda7-221">While it is possible to deploy a pull server using HTTP which facilitates client requests in clear text, it is a best practice to secure traffic using HTTPS.</span></span> <span data-ttu-id="afda7-222">De service kan worden geconfigureerd voor het gebruik van HTTPS met behulp van een set para meters in de DSC-resource **xPSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="afda7-222">The service can be configured to use HTTPS using a set of parameters in the DSC resource **xPSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="afda7-223">De certificaat vereisten voor het beveiligen van HTTPS-verkeer voor de pull-server zijn niet anders dan het beveiligen van elke andere HTTPS-website.</span><span class="sxs-lookup"><span data-stu-id="afda7-223">The certificate requirements to secure HTTPS traffic for pull server are not different than securing any other HTTPS web site.</span></span> <span data-ttu-id="afda7-224">De **webserver** sjabloon in een Windows Server Certificate Services voldoet aan de vereiste mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="afda7-224">The **Web Server** template in a Windows Server Certificate Services satisfies the required capabilities.</span></span>

<span data-ttu-id="afda7-225">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="afda7-225">Planning task</span></span>

- <span data-ttu-id="afda7-226">Als certificaat aanvragen niet worden geautomatiseerd, wie moet u contact opnemen om een certificaat aan te vragen?</span><span class="sxs-lookup"><span data-stu-id="afda7-226">If certificate requests are not automated, who will you need to contact to requests a certificate?</span></span>
- <span data-ttu-id="afda7-227">Wat is de gemiddelde oplever actie voor de aanvraag?</span><span class="sxs-lookup"><span data-stu-id="afda7-227">What is the average turnaround for the request?</span></span>
- <span data-ttu-id="afda7-228">Hoe wordt het certificaat bestand overgezet?</span><span class="sxs-lookup"><span data-stu-id="afda7-228">How will the certificate file be transferred to you?</span></span>
- <span data-ttu-id="afda7-229">Hoe wordt de persoonlijke sleutel van het certificaat overgezet?</span><span class="sxs-lookup"><span data-stu-id="afda7-229">How will the certificate private key be transferred to you?</span></span>
- <span data-ttu-id="afda7-230">Hoe lang is de standaard verloop tijd?</span><span class="sxs-lookup"><span data-stu-id="afda7-230">How long is the default expiration time?</span></span>
- <span data-ttu-id="afda7-231">Hebt u de DNS-naam voor de pull-server omgeving verrekend, die u voor de certificaat naam kunt gebruiken?</span><span class="sxs-lookup"><span data-stu-id="afda7-231">Have you settled on a DNS name for the pull server environment, that you can use for the certificate name?</span></span>

### <a name="choosing-an-architecture"></a><span data-ttu-id="afda7-232">Een architectuur kiezen</span><span class="sxs-lookup"><span data-stu-id="afda7-232">Choosing an architecture</span></span>

<span data-ttu-id="afda7-233">Een pull-server kan worden geïmplementeerd met behulp van een webservice die wordt gehost op IIS of een SMB-bestands share.</span><span class="sxs-lookup"><span data-stu-id="afda7-233">A pull server can be deployed using either a web service hosted on IIS, or an SMB file share.</span></span> <span data-ttu-id="afda7-234">In de meeste gevallen biedt de webservice-optie meer flexibiliteit.</span><span class="sxs-lookup"><span data-stu-id="afda7-234">In most situations, the web service option will provide greater flexibility.</span></span> <span data-ttu-id="afda7-235">Het is niet ongebruikelijk voor HTTPS-verkeer om netwerk grenzen te passeren, terwijl SMB-verkeer vaak wordt gefilterd of geblokkeerd tussen netwerken.</span><span class="sxs-lookup"><span data-stu-id="afda7-235">It is not uncommon for HTTPS traffic to traverse network boundaries, whereas SMB traffic is often filtered or blocked between networks.</span></span> <span data-ttu-id="afda7-236">De webservice biedt ook de mogelijkheid om een conformiteit server of webrapport Manager op te geven (beide onderwerpen moeten worden behandeld in een toekomstige versie van dit document) die een mechanisme bieden voor clients om de status terug te rapporteren aan een server voor gecentraliseerde zicht baarheid.</span><span class="sxs-lookup"><span data-stu-id="afda7-236">The web service also offers the option to include a Conformance Server or Web Reporting Manager (both topics to be addressed in a future version of this document) that provide a mechanism for clients to report status back to a server for centralized visibility.</span></span> <span data-ttu-id="afda7-237">SMB biedt een optie voor omgevingen waarbij beleids regels bepalen dat een webserver niet moet worden gebruikt en voor andere omgevings vereisten die een webserver functie onwenselijk maken.</span><span class="sxs-lookup"><span data-stu-id="afda7-237">SMB provides an option for environments where policy dictates that a web server should not be utilized, and for other environmental requirements that make a web server role undesirable.</span></span> <span data-ttu-id="afda7-238">In beide gevallen moet u de vereisten voor het ondertekenen en versleutelen van verkeer evalueren.</span><span class="sxs-lookup"><span data-stu-id="afda7-238">In either case, remember to evaluate the requirements for signing and encrypting traffic.</span></span> <span data-ttu-id="afda7-239">HTTPS, SMB-ondertekening en IPSEC-beleid zijn alle opties die u moet overwegen.</span><span class="sxs-lookup"><span data-stu-id="afda7-239">HTTPS, SMB signing, and IPSEC policies are all options worth considering.</span></span>

#### <a name="load-balancing"></a><span data-ttu-id="afda7-240">Taakverdeling</span><span class="sxs-lookup"><span data-stu-id="afda7-240">Load balancing</span></span>

<span data-ttu-id="afda7-241">Clients die communiceren met de webservice maken een aanvraag voor informatie die in één antwoord wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="afda7-241">Clients interacting with the web service make a request for information that is returned in a single response.</span></span> <span data-ttu-id="afda7-242">Er zijn geen opeenvolgende aanvragen vereist, dus het is niet nodig om ervoor te zorgen dat sessies op één server op elk moment worden onderhouden.</span><span class="sxs-lookup"><span data-stu-id="afda7-242">No sequential requests are required, so it is not necessary for the load balancing platform to ensure sessions are maintained on a single server at any point in time.</span></span>

<span data-ttu-id="afda7-243">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="afda7-243">Planning task</span></span>

- <span data-ttu-id="afda7-244">Welke oplossing wordt gebruikt voor taak verdeling verkeer tussen servers?</span><span class="sxs-lookup"><span data-stu-id="afda7-244">What solution will be used for load balancing traffic across servers?</span></span>
- <span data-ttu-id="afda7-245">Als er een hardware-load balancer wordt gebruikt, kan deze een nieuwe configuratie toevoegen aan het apparaat?</span><span class="sxs-lookup"><span data-stu-id="afda7-245">If using a hardware load balancer, who will take a request to add a new configuration to the device?</span></span>
- <span data-ttu-id="afda7-246">Wat is de gemiddelde verwerkings tijd voor een aanvraag om een nieuwe webservice met gelijke taak verdeling te configureren?</span><span class="sxs-lookup"><span data-stu-id="afda7-246">What is the average turnaround for a request to configure a new load balanced web service?</span></span>
- <span data-ttu-id="afda7-247">Welke informatie is vereist voor de aanvraag?</span><span class="sxs-lookup"><span data-stu-id="afda7-247">What information will be required for the request?</span></span>
- <span data-ttu-id="afda7-248">Moet u een extra IP-adres aanvragen of wordt het team dat verantwoordelijk is voor de taak verdeling?</span><span class="sxs-lookup"><span data-stu-id="afda7-248">Will you need to request an additional IP or will the team responsible for load balancing handle that?</span></span>
- <span data-ttu-id="afda7-249">Hebt u de DNS-records nodig en is dit vereist voor het team dat verantwoordelijk is voor het configureren van de oplossing voor taak verdeling?</span><span class="sxs-lookup"><span data-stu-id="afda7-249">Do you have the DNS records needed, and will this be required by the team responsible for configuring the load balancing solution?</span></span>
- <span data-ttu-id="afda7-250">Moet de oplossing voor taak verdeling vereisen dat de PKI door het apparaat wordt verwerkt of kan het de taak verdeling van HTTPS-verkeer hebben zolang er geen sessie vereisten zijn?</span><span class="sxs-lookup"><span data-stu-id="afda7-250">Does the load balancing solution require that PKI be handled by the device or can it load balance HTTPS traffic as long as there are no session requirements?</span></span>

### <a name="staging-configurations-and-modules-on-the-pull-server"></a><span data-ttu-id="afda7-251">Faserings configuraties en-modules op de pull-server</span><span class="sxs-lookup"><span data-stu-id="afda7-251">Staging configurations and modules on the pull server</span></span>

<span data-ttu-id="afda7-252">Als onderdeel van de configuratie planning moet u nadenken over welke DSC-modules en configuraties worden gehost door de pull-server.</span><span class="sxs-lookup"><span data-stu-id="afda7-252">As part of configuration planning, you will need to think about which DSC modules and configurations will be hosted by the pull server.</span></span> <span data-ttu-id="afda7-253">Voor het plannen van de configuratie is het belang rijk dat u een basis memorandum hebt van het voorbereiden en implementeren van inhoud op een pull-server.</span><span class="sxs-lookup"><span data-stu-id="afda7-253">For the purpose of configuration planning it is important to have a basic understanding of how to prepare and deploy content to a pull server.</span></span>

<span data-ttu-id="afda7-254">In de toekomst wordt deze sectie uitgebreid en opgenomen in een Operations Guide voor de DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="afda7-254">In the future, this section will be expanded and included in an Operations Guide for DSC Pull Server.</span></span> <span data-ttu-id="afda7-255">In de hand leiding wordt het dagelijkse proces voor het beheren van modules en configuraties in de loop van de tijd met automatisering besproken.</span><span class="sxs-lookup"><span data-stu-id="afda7-255">The guide will discuss the day to day process for managing modules and configurations over time with automation.</span></span>

#### <a name="dsc-modules"></a><span data-ttu-id="afda7-256">DSC-modules</span><span class="sxs-lookup"><span data-stu-id="afda7-256">DSC modules</span></span>

<span data-ttu-id="afda7-257">Clients die een configuratie aanvragen, hebben de vereiste DSC-modules nodig.</span><span class="sxs-lookup"><span data-stu-id="afda7-257">Clients that request a configuration will need the required DSC modules.</span></span> <span data-ttu-id="afda7-258">Een functionaliteit van de pull-server is het automatiseren van de distributie op aanvraag van DSC-modules naar clients.</span><span class="sxs-lookup"><span data-stu-id="afda7-258">A functionality of the pull server is to automate distribution on demand of DSC modules to clients.</span></span> <span data-ttu-id="afda7-259">Als u een pull-server voor de eerste keer implementeert, bijvoorbeeld een Lab of concept, is het waarschijnlijk afhankelijk van de DSC-modules die beschikbaar zijn vanuit open bare opslag plaatsen, zoals de PowerShell Gallery of de PowerShell.org GitHub-opslag plaatsen voor DSC-modules.</span><span class="sxs-lookup"><span data-stu-id="afda7-259">If you are deploying a pull server for the first time, perhaps as a lab or proof of concept, you are likely going to depend on DSC modules that are available from public repositories such as the PowerShell Gallery or the PowerShell.org GitHub repositories for DSC modules.</span></span>

<span data-ttu-id="afda7-260">Het is belang rijk om te onthouden dat zelfs voor vertrouwde online bronnen, zoals de PowerShell Gallery, elke module die wordt gedownload uit een open bare opslag plaats moet worden gecontroleerd door iemand met een Power shell-ervaring en kennis van de omgeving waarin de modules worden gebruikt voordat deze in productie worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="afda7-260">It is critical to remember that even for trusted online sources such as the PowerShell Gallery, any module that is downloaded from a public repository should be reviewed by someone with PowerShell experience and knowledge of the environment where the modules will be used prior to being used in production.</span></span> <span data-ttu-id="afda7-261">Bij het volt ooien van deze taak is het een goed idee om te controleren of er extra Payload in de module is die kan worden verwijderd, zoals documentatie en voorbeeld scripts.</span><span class="sxs-lookup"><span data-stu-id="afda7-261">While completing this task it is a good time to check for any additional payload in the module that can be removed such as documentation and example scripts.</span></span> <span data-ttu-id="afda7-262">Hiermee wordt de netwerk bandbreedte per client in de eerste aanvraag verminderd, wanneer modules via het netwerk van de server naar de client worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="afda7-262">This will reduce the network bandwidth per client in their first request, when modules will be downloaded over the network from server to client.</span></span>

<span data-ttu-id="afda7-263">Elke module moet worden verpakt in een specifieke indeling, een ZIP-bestand met de naam ModuleName_Version. zip dat de module Payload bevat.</span><span class="sxs-lookup"><span data-stu-id="afda7-263">Each module must be packaged in a specific format, a ZIP file named ModuleName_Version.zip that contains the module payload.</span></span> <span data-ttu-id="afda7-264">Nadat het bestand is gekopieerd naar de server, moet er een controlesom bestand worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="afda7-264">After the file is copied to the server a checksum file must be created.</span></span>
<span data-ttu-id="afda7-265">Wanneer clients verbinding maken met de server, wordt de controlesom gebruikt om te controleren of de inhoud van de DSC-module niet is gewijzigd sinds deze is gepubliceerd.</span><span class="sxs-lookup"><span data-stu-id="afda7-265">When clients connect to the server, the checksum is used to verify the content of the DSC module has not changed since it was published.</span></span>

```powershell
New-DscChecksum -ConfigurationPath .\ -OutPath .\
```

<span data-ttu-id="afda7-266">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="afda7-266">Planning task</span></span>

- <span data-ttu-id="afda7-267">Als u van plan bent een test-of lab-omgeving te plannen, welke scenario's zijn de sleutel die moet worden gevalideerd?</span><span class="sxs-lookup"><span data-stu-id="afda7-267">If you are planning a test or lab environment which scenarios are key to validate?</span></span>
- <span data-ttu-id="afda7-268">Zijn er openbaar beschik bare modules die resources bevatten voor alles wat u nodig hebt, of moet u uw eigen resources maken?</span><span class="sxs-lookup"><span data-stu-id="afda7-268">Are there publicly available modules that contain resources to cover everything you need or will you need to author your own resources?</span></span>
- <span data-ttu-id="afda7-269">Heeft uw omgeving Internet toegang om open bare modules op te halen?</span><span class="sxs-lookup"><span data-stu-id="afda7-269">Will your environment have Internet access to retrieve public modules?</span></span>
- <span data-ttu-id="afda7-270">Wie is verantwoordelijk voor het beoordelen van DSC-modules?</span><span class="sxs-lookup"><span data-stu-id="afda7-270">Who will be responsible for reviewing DSC modules?</span></span>
- <span data-ttu-id="afda7-271">Als u een productie omgeving plant, kunt u deze gebruiken als lokale opslag plaats voor het opslaan van DSC-modules?</span><span class="sxs-lookup"><span data-stu-id="afda7-271">If you are planning a production environment what will you use as a local repository for storing DSC modules?</span></span>
- <span data-ttu-id="afda7-272">Wordt een centraal team DSC-modules geaccepteerd van toepassings teams?</span><span class="sxs-lookup"><span data-stu-id="afda7-272">Will a central team accept DSC modules from application teams?</span></span> <span data-ttu-id="afda7-273">Wat is het proces?</span><span class="sxs-lookup"><span data-stu-id="afda7-273">What will the process be?</span></span>
- <span data-ttu-id="afda7-274">Automatiseert u de verpakking, het kopiëren en het maken van een controlesom voor DSC-modules die gereed zijn voor productie naar de-server, vanuit uw bron-opslag plaats?</span><span class="sxs-lookup"><span data-stu-id="afda7-274">Will you automate packaging, copying, and creating a checksum for production-ready DSC modules to the server, from your source repo?</span></span>
- <span data-ttu-id="afda7-275">Is uw team ook verantwoordelijk voor het beheer van het automatiserings platform?</span><span class="sxs-lookup"><span data-stu-id="afda7-275">Will your team be responsible for managing the automation platform as well?</span></span>

#### <a name="dsc-configurations"></a><span data-ttu-id="afda7-276">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="afda7-276">DSC configurations</span></span>

<span data-ttu-id="afda7-277">Het doel van een pull-server is het bieden van een gecentraliseerd mechanisme voor het distribueren van DSC-configuraties naar client knooppunten.</span><span class="sxs-lookup"><span data-stu-id="afda7-277">The purpose of a pull server is to provide a centralized mechanism for distributing DSC configurations to client nodes.</span></span> <span data-ttu-id="afda7-278">De configuraties worden op de server als MOF-documenten opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="afda7-278">The configurations are stored on the server as MOF documents.</span></span> <span data-ttu-id="afda7-279">Elk document krijgt een unieke **GUID**.</span><span class="sxs-lookup"><span data-stu-id="afda7-279">Each document will be named with a unique **Guid**.</span></span> <span data-ttu-id="afda7-280">Wanneer clients zijn geconfigureerd om verbinding te maken met een pull-server, krijgen ze ook de **GUID** voor de configuratie die ze moeten aanvragen.</span><span class="sxs-lookup"><span data-stu-id="afda7-280">When clients are configured to connect with a pull server, they are also given the **Guid** for the configuration they should request.</span></span> <span data-ttu-id="afda7-281">Dit systeem voor het verwijzen naar configuraties door de **GUID** garandeert globale uniekheid en is flexibel, zodat een configuratie kan worden toegepast met granulatie per knoop punt, of als een functie configuratie die veel servers bevat die identieke configuraties moeten hebben.</span><span class="sxs-lookup"><span data-stu-id="afda7-281">This system of referencing configurations by **Guid** guarantees global uniqueness and is flexible such that a configuration can be applied with granularity per node, or as a role configuration that spans many servers that should have identical configurations.</span></span>

#### <a name="guids"></a><span data-ttu-id="afda7-282">Guid's</span><span class="sxs-lookup"><span data-stu-id="afda7-282">Guids</span></span>

<span data-ttu-id="afda7-283">Het plannen van configuratie- **guid's** is extra aandacht wanneer u een pull-Server implementatie overweegt.</span><span class="sxs-lookup"><span data-stu-id="afda7-283">Planning for configuration **Guids** is worth additional attention when thinking through a pull server deployment.</span></span> <span data-ttu-id="afda7-284">Er is geen specifieke vereiste voor het afhandelen van **guid's** en het proces is waarschijnlijk uniek voor elke omgeving.</span><span class="sxs-lookup"><span data-stu-id="afda7-284">There is no specific requirement for how to handle **Guids** and the process is likely to be unique for each environment.</span></span> <span data-ttu-id="afda7-285">Het proces kan variëren van eenvoudig tot complex: een centraal opgeslagen CSV-bestand, een eenvoudige SQL-tabel, een CMDB of een complexe oplossing die integratie met een ander hulp programma of software oplossing vereist.</span><span class="sxs-lookup"><span data-stu-id="afda7-285">The process can range from simple to complex: a centrally stored CSV file, a simple SQL table, a CMDB, or a complex solution requiring integration with another tool or software solution.</span></span> <span data-ttu-id="afda7-286">Er zijn twee algemene benaderingen:</span><span class="sxs-lookup"><span data-stu-id="afda7-286">There are two general approaches:</span></span>

- <span data-ttu-id="afda7-287">Het **toewijzen van guid's per server** — biedt een mate van zekerheid dat elke server configuratie afzonderlijk wordt beheerd.</span><span class="sxs-lookup"><span data-stu-id="afda7-287">**Assigning Guids per server** — Provides a measure of assurance that every server configuration is controlled individually.</span></span> <span data-ttu-id="afda7-288">Dit biedt een nauwkeurigheids niveau voor updates en kan goed worden gebruikt in omgevingen met weinig servers.</span><span class="sxs-lookup"><span data-stu-id="afda7-288">This provides a level of precision around updates and can work well in environments with few servers.</span></span>
- <span data-ttu-id="afda7-289">Het **toewijzen van guid's per serverrol** : alle servers die dezelfde functie uitvoeren, zoals webservers, gebruiken dezelfde GUID om te verwijzen naar de vereiste configuratie gegevens.</span><span class="sxs-lookup"><span data-stu-id="afda7-289">**Assigning Guids per server role** — All servers that perform the same function, such as web servers, use the same GUID to reference the required configuration data.</span></span> <span data-ttu-id="afda7-290">Houd er rekening mee dat als veel servers dezelfde GUID delen, deze allemaal tegelijkertijd worden bijgewerkt wanneer de configuratie wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="afda7-290">Be aware that if many servers share the same GUID, all of them would be updated simultaneously when the configuration changes.</span></span>

  <span data-ttu-id="afda7-291">De GUID is iets wat moet worden beschouwd als gevoelige gegevens omdat deze kan worden gebruikt door iemand met kwaad aardigheid om informatie te verkrijgen over hoe servers worden geïmplementeerd en geconfigureerd in uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="afda7-291">The GUID is something that should be considered sensitive data because it could be leveraged by someone with malicious intent to gain intelligence about how servers are deployed and configured in your environment.</span></span> <span data-ttu-id="afda7-292">Zie voor meer informatie [veilig toewijzing van guid's in Power shell pull-modus voor desired state Configuration](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span><span class="sxs-lookup"><span data-stu-id="afda7-292">For more information, see [Securely allocating Guids in PowerShell Desired State Configuration Pull Mode](https://blogs.msdn.microsoft.com/powershell/2014/12/31/securely-allocating-guids-in-powershell-desired-state-configuration-pull-mode/).</span></span>

<span data-ttu-id="afda7-293">Taak plannen</span><span class="sxs-lookup"><span data-stu-id="afda7-293">Planning task</span></span>

- <span data-ttu-id="afda7-294">Wie is verantwoordelijk voor het kopiëren van configuraties in de map van de pull-server wanneer deze klaar zijn?</span><span class="sxs-lookup"><span data-stu-id="afda7-294">Who will be responsible for copying configurations in to the pull server folder when they are ready?</span></span>
- <span data-ttu-id="afda7-295">Als er configuraties worden gemaakt door een toepassings team, wat moet het proces dan hand matig worden afgebroken?</span><span class="sxs-lookup"><span data-stu-id="afda7-295">If Configurations are authored by an application team, what will the process be to hand them off?</span></span>
- <span data-ttu-id="afda7-296">Maakt u gebruik van een opslag plaats voor het opslaan van configuraties zoals ze worden geschreven in teams?</span><span class="sxs-lookup"><span data-stu-id="afda7-296">Will you leverage a repository to store configurations as they are being authored, across teams?</span></span>
- <span data-ttu-id="afda7-297">Automatiseert u het proces van het kopiëren van configuraties naar de server en het maken van een controlesom wanneer deze klaar zijn?</span><span class="sxs-lookup"><span data-stu-id="afda7-297">Will you automate the process of copying configurations to the server and creating a checksum when they are ready?</span></span>
- <span data-ttu-id="afda7-298">Hoe wijst u Guid's toe aan servers of rollen en waar wordt deze opgeslagen?</span><span class="sxs-lookup"><span data-stu-id="afda7-298">How will you map Guids to servers or roles, and where will this be stored?</span></span>
- <span data-ttu-id="afda7-299">Wat gaat u gebruiken als een proces voor het configureren van client computers en hoe wordt het geïntegreerd met uw proces voor het maken en opslaan van configuratie-Guid's?</span><span class="sxs-lookup"><span data-stu-id="afda7-299">What will you use as a process to configure client machines, and how will it integrate with your process for creating and storing Configuration Guids?</span></span>

## <a name="installation-guide"></a><span data-ttu-id="afda7-300">Installatiehandleiding</span><span class="sxs-lookup"><span data-stu-id="afda7-300">Installation Guide</span></span>

<span data-ttu-id="afda7-301">*De in dit document gegeven scripts zijn stabiele voor beelden. Controleer altijd de scripts zorgvuldig voordat u ze in een productie omgeving uitvoert.*</span><span class="sxs-lookup"><span data-stu-id="afda7-301">*Scripts given in this document are stable examples. Always review scripts carefully before executing them in a production environment.*</span></span>

### <a name="prerequisites"></a><span data-ttu-id="afda7-302">Vereisten</span><span class="sxs-lookup"><span data-stu-id="afda7-302">Prerequisites</span></span>

<span data-ttu-id="afda7-303">Gebruik de volgende opdracht om de versie van Power shell op uw server te controleren.</span><span class="sxs-lookup"><span data-stu-id="afda7-303">To verify the version of PowerShell on your server use the following command.</span></span>

```powershell
$PSVersionTable.PSVersion
```

<span data-ttu-id="afda7-304">Voer, indien mogelijk, een upgrade uit naar de nieuwste versie van Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="afda7-304">If possible, upgrade to the latest version of Windows Management Framework.</span></span> <span data-ttu-id="afda7-305">Down load vervolgens de `xPsDesiredStateConfiguration` module met de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="afda7-305">Next, download the `xPsDesiredStateConfiguration` module using the following command.</span></span>

```powershell
Install-Module xPSDesiredStateConfiguration
```

<span data-ttu-id="afda7-306">De opdracht wordt gevraagd naar uw goed keuring voordat u de module downloadt.</span><span class="sxs-lookup"><span data-stu-id="afda7-306">The command will ask for your approval before downloading the module.</span></span>

### <a name="installation-and-configuration-scripts"></a><span data-ttu-id="afda7-307">Installatie-en configuratie scripts</span><span class="sxs-lookup"><span data-stu-id="afda7-307">Installation and configuration scripts</span></span>

<span data-ttu-id="afda7-308">De beste methode voor het implementeren van een DSC-pull-server is het gebruik van een DSC-configuratie script.</span><span class="sxs-lookup"><span data-stu-id="afda7-308">The best method to deploy a DSC pull server is to use a DSC configuration script.</span></span> <span data-ttu-id="afda7-309">In dit document worden de scripts weer gegeven, inclusief de basis instellingen waarmee alleen de DSC-webservice en geavanceerde instellingen worden geconfigureerd waarmee een end-to-end-service van Windows Server wordt geconfigureerd, inclusief de DSC-webservice.</span><span class="sxs-lookup"><span data-stu-id="afda7-309">This document will present scripts including both basic settings that would configure only the DSC web service and advanced settings that would configure a Windows Server end-to-end including DSC web service.</span></span>

<span data-ttu-id="afda7-310">Opmerking: de `xPSDesiredStateConfiguration` DSC-module vereist momenteel dat de server is ingesteld op de land instelling en-us.</span><span class="sxs-lookup"><span data-stu-id="afda7-310">Note:  Currently the `xPSDesiredStateConfiguration` DSC module requires the server to be EN-US locale.</span></span>

### <a name="basic-configuration-for-windows-server-2012"></a><span data-ttu-id="afda7-311">Basis configuratie voor Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="afda7-311">Basic configuration for Windows Server 2012</span></span>

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

### <a name="advanced-configuration-for-windows-server-2012-r2"></a><span data-ttu-id="afda7-312">Geavanceerde configuratie voor Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="afda7-312">Advanced configuration for Windows Server 2012 R2</span></span>

```powershell
# This is an advanced Configuration example for Pull Server production deployments
# on Windows Server 2012 R2. Many of the features demonstrated are optional and
# provided to demonstrate how to adapt the Configuration for multiple scenarios
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

        # If using a certificate from a local Active Directory Enterprise Root Certificate Authority,
        # complete a request and install the certificate
        xCertReq SSLCert
        {
            CARootName = $Node.CARootName
            CAServerFQDN = $Node.CAServerFQDN
            Subject = $Node.CertSubject
            AutoRenew = $Node.AutoRenew
            Credential = $Node.Credential
        }

        # Use the DSC resource to simplify deployment of the web service.  You might also consider
        # modifying the default port, possibly leveraging port 443 in environments where that is
        # enforced as a standard.
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

### <a name="verify-pull-server-functionality"></a><span data-ttu-id="afda7-313">De functionaliteit van de pull-server controleren</span><span class="sxs-lookup"><span data-stu-id="afda7-313">Verify pull server functionality</span></span>

```powershell
# This function is meant to simplify a check against a DSC pull server. If you do not use the
# default service URL, you will need to adjust accordingly.
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

### <a name="configure-clients"></a><span data-ttu-id="afda7-314">Clients configureren</span><span class="sxs-lookup"><span data-stu-id="afda7-314">Configure clients</span></span>

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

## <a name="additional-references-snippets-and-examples"></a><span data-ttu-id="afda7-315">Aanvullende verwijzingen, fragmenten en voor beelden</span><span class="sxs-lookup"><span data-stu-id="afda7-315">Additional references, snippets, and examples</span></span>

<span data-ttu-id="afda7-316">In dit voor beeld ziet u hoe u hand matig een client verbinding start (vereist WMF5) voor het testen.</span><span class="sxs-lookup"><span data-stu-id="afda7-316">This example shows how to manually initiate a client connection (requires WMF5) for testing.</span></span>

```powershell
Update-DscConfiguration –Wait -Verbose
```

<span data-ttu-id="afda7-317">De cmdlet [add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) wordt gebruikt om een type CNAME-record toe te voegen aan een DNS-zone.</span><span class="sxs-lookup"><span data-stu-id="afda7-317">The [Add-DnsServerResourceRecordName](/powershell/module/dnsserver/add-dnsserverresourcerecordcname) cmdlet is used to add a type CNAME record to a DNS zone.</span></span>

<span data-ttu-id="afda7-318">De Power shell-functie voor het [maken van een controlesom en het publiceren van DSC MOF naar SMB pull-server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) genereert automatisch de vereiste controlesom en kopieert vervolgens zowel de MOF-configuratie als de controlesom bestanden naar de SMB-pull-server.</span><span class="sxs-lookup"><span data-stu-id="afda7-318">The PowerShell Function to [Create a Checksum and Publish DSC MOF to SMB Pull Server](https://gallery.technet.microsoft.com/scriptcenter/PowerShell-Function-to-3bc4b7f0) automatically generates the required checksum, and then copies both the MOF configuration and checksum files to the SMB pull server.</span></span>

## <a name="appendix---understanding-odata-service-data-file-types"></a><span data-ttu-id="afda7-319">Bijlage: informatie over ODATA-service gegevens bestands typen</span><span class="sxs-lookup"><span data-stu-id="afda7-319">Appendix - Understanding ODATA service data file types</span></span>

<span data-ttu-id="afda7-320">Er wordt een gegevens bestand opgeslagen om informatie te maken tijdens de implementatie van een pull-server die de OData-webservice bevat.</span><span class="sxs-lookup"><span data-stu-id="afda7-320">A data file is stored to create information during deployment of a pull server that includes the OData web service.</span></span> <span data-ttu-id="afda7-321">Het type bestand is afhankelijk van het besturings systeem, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="afda7-321">The type of file depends on the operating system, as described below.</span></span>

- <span data-ttu-id="afda7-322">**Windows Server 2012** Het bestands type is altijd. mdb</span><span class="sxs-lookup"><span data-stu-id="afda7-322">**Windows Server 2012** The file type will always be   .mdb</span></span>
- <span data-ttu-id="afda7-323">**Windows Server 2012 R2** Het bestands type wordt standaard ingesteld op. edb tenzij er een. mdb is opgegeven in de configuratie</span><span class="sxs-lookup"><span data-stu-id="afda7-323">**Windows Server 2012 R2** The file type will default to .edb unless a .mdb is specified in the configuration</span></span>

<span data-ttu-id="afda7-324">In het [geavanceerde voorbeeld script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) voor het installeren van een pull-Server vindt u ook een voor beeld van het automatisch beheren van de instellingen van het web. config-bestand om een kans op fouten die door het bestands type wordt veroorzaakt te voor komen.</span><span class="sxs-lookup"><span data-stu-id="afda7-324">In the [Advanced example script](https://github.com/mgreenegit/Whitepapers/blob/Dev/PullServerCPIG.md#installation-and-configuration-scripts) for installing a Pull Server, you will also find an example of how to automatically control the web.config file settings to prevent any chance of error caused by file type.</span></span>
