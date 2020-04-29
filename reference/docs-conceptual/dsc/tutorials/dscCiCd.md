---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een continue integratie en een pijp lijn voor continue implementatie bouwen met DSC
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942144"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="e4bd3-103">Een continue integratie en een pijp lijn voor continue implementatie bouwen met DSC</span><span class="sxs-lookup"><span data-stu-id="e4bd3-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="e4bd3-104">Dit voor beeld laat zien hoe u met behulp van Power shell, DSC, pester en Visual Studio Team Foundation Server (TFS) een continue integratie/CD-pijp lijn kunt maken.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="e4bd3-105">Nadat de pijp lijn is gebouwd en geconfigureerd, kunt u deze gebruiken om een DNS-server en bijbehorende host-records volledig te implementeren, te configureren en te testen.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="e4bd3-106">Dit proces simuleert het eerste deel van een pijp lijn dat in een ontwikkel omgeving zou worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="e4bd3-107">Een geautomatiseerde CI/CD-pijp lijn helpt u software sneller en betrouwbaarder bij te werken, zodat alle code wordt getest en dat de huidige versie van uw code altijd beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e4bd3-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e4bd3-108">Prerequisites</span></span>

<span data-ttu-id="e4bd3-109">Als u dit voor beeld wilt gebruiken, moet u vertrouwd zijn met het volgende:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="e4bd3-110">CI-CD-concepten.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-110">CI-CD concepts.</span></span> <span data-ttu-id="e4bd3-111">Een goede verwijzing vindt u in [het model van de release pijplijn](https://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="e4bd3-111">A good reference can be found at [The Release Pipeline Model](https://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="e4bd3-112">[Git](https://git-scm.com/) -bron beheer</span><span class="sxs-lookup"><span data-stu-id="e4bd3-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="e4bd3-113">Het [ziekte](https://github.com/pester/Pester) test-framework</span><span class="sxs-lookup"><span data-stu-id="e4bd3-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="e4bd3-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="e4bd3-114">Team Foundation Server</span></span>](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="e4bd3-115">Wat u nodig hebt</span><span class="sxs-lookup"><span data-stu-id="e4bd3-115">What you will need</span></span>

<span data-ttu-id="e4bd3-116">Als u dit voor beeld wilt bouwen en uitvoeren, hebt u een omgeving met meerdere computers en/of virtuele machines nodig.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="e4bd3-117">Client</span><span class="sxs-lookup"><span data-stu-id="e4bd3-117">Client</span></span>

<span data-ttu-id="e4bd3-118">Dit is de computer waarop u alle werk instellingen gaat uitvoeren en het voor beeld uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="e4bd3-119">De client computer moet een Windows-computer zijn waarop het volgende is geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="e4bd3-120">Git</span><span class="sxs-lookup"><span data-stu-id="e4bd3-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="e4bd3-121">een lokale Git-opslag plaats die is gekloond vanhttps://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="e4bd3-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="e4bd3-122">een tekst editor, zoals [Visual Studio code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="e4bd3-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="e4bd3-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="e4bd3-123">TFSSrv1</span></span>

<span data-ttu-id="e4bd3-124">De computer die als host fungeert voor de TFS-server waarop u uw build en release wilt definiëren.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="e4bd3-125">Op deze computer moet [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-125">This computer must have [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="e4bd3-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="e4bd3-126">BuildAgent</span></span>

<span data-ttu-id="e4bd3-127">De computer waarop de Windows Build-agent wordt uitgevoerd, die het project bouwt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="e4bd3-128">Op deze computer moet een Windows-Build-agent zijn geïnstalleerd en worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="e4bd3-129">Zie [een agent implementeren in Windows](/azure/devops/pipelines/agents/v2-windows) voor instructies over het installeren en uitvoeren van een Windows Build-agent.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="e4bd3-130">U moet ook de `xDnsServer` -en `xNetworking` DSC-modules op deze computer installeren.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="e4bd3-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="e4bd3-131">TestAgent1</span></span>

<span data-ttu-id="e4bd3-132">Dit is de computer die is geconfigureerd als een DNS-server door de DSC-configuratie in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="e4bd3-133">Op de computer moet [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="e4bd3-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="e4bd3-134">TestAgent2</span></span>

<span data-ttu-id="e4bd3-135">Dit is de computer die als host fungeert voor de website in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="e4bd3-136">Op de computer moet [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="e4bd3-137">De code toevoegen aan TFS</span><span class="sxs-lookup"><span data-stu-id="e4bd3-137">Add the code to TFS</span></span>

<span data-ttu-id="e4bd3-138">We beginnen met het maken van een Git-opslag plaats in TFS en het importeren van de code uit de lokale opslag plaats op de client computer.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="e4bd3-139">Als u de Demo_CI opslag plaats nog niet hebt gekloond op uw client computer, doet u dat nu door de volgende Git-opdracht uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="e4bd3-140">Ga op de client computer naar uw TFS-server in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="e4bd3-141">Maak in TFS [een nieuw team project met de](/azure/devops/organizations/projects/create-project) naam Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="e4bd3-142">Zorg ervoor dat **versie beheer** is ingesteld op **Git**.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="e4bd3-143">Voeg op de client computer een extern onderdeel toe aan de opslag plaats die u zojuist hebt gemaakt in TFS met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="e4bd3-144">Waar `<YourTFSRepoURL>` bevindt zich de kloon-URL naar de tFS-opslag plaats die u in de vorige stap hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="e4bd3-145">Zie [een bestaand Git-opslag plaats klonen](/azure/devops/repos/git/clone)als u niet weet waar u deze URL kunt vinden.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="e4bd3-146">Push de code van uw lokale opslag plaats naar uw TFS-opslag plaats met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="e4bd3-147">De TFS-opslag plaats wordt gevuld met de Demo_CI-code.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="e4bd3-148">In dit voor beeld wordt de code `ci-cd-example` in de vertakking van het git-opslag plaats gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="e4bd3-149">Zorg ervoor dat u deze vertakking opgeeft als de standaard vertakking in uw TFS-project en voor de CI/CD-triggers die u maakt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="e4bd3-150">De code begrijpen</span><span class="sxs-lookup"><span data-stu-id="e4bd3-150">Understanding the code</span></span>

<span data-ttu-id="e4bd3-151">Voordat we de builds-en implementatie pijplijnen maken, kijken we naar een aantal code om te begrijpen wat er gebeurt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="e4bd3-152">Open uw favoriete tekst editor op de client computer en ga naar de hoofdmap van uw Demo_CI Git-opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="e4bd3-153">De DSC-configuratie</span><span class="sxs-lookup"><span data-stu-id="e4bd3-153">The DSC configuration</span></span>

<span data-ttu-id="e4bd3-154">Open het bestand `DNSServer.ps1` (in de hoofdmap van de lokale Demo_CI opslag plaats `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="e4bd3-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="e4bd3-155">Dit bestand bevat de DSC-configuratie waarmee de DNS-server wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="e4bd3-156">Hier is het een volledige oplossing:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-156">Here it is in its entirety:</span></span>

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

<span data-ttu-id="e4bd3-157">Let op `Node` de instructie:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="e4bd3-158">Hiermee worden knoop punten gevonden die zijn gedefinieerd als een rol van `DNSServer` in de [configuratie gegevens](../configurations/configData.md), die door het `DevEnv.ps1` script wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="e4bd3-159">Meer informatie over de `Where` methode vindt u in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span><span class="sxs-lookup"><span data-stu-id="e4bd3-159">You can read more about the `Where` method in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

<span data-ttu-id="e4bd3-160">Het gebruik van configuratie gegevens voor het definiëren van knoop punten is belang rijk bij het uitvoeren van CI omdat knooppunt informatie waarschijnlijk wordt gewijzigd tussen omgevingen en u met configuratie gegevens eenvoudig wijzigingen kunt aanbrengen in knooppunt gegevens zonder de configuratie code te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="e4bd3-161">In het eerste bron blok roept de configuratie de **WindowsFeature** aan om ervoor te zorgen dat de DNS-functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="e4bd3-162">De resource blokken die volgen resources aanroepen vanuit de [xDnsServer](https://github.com/PowerShell/xDnsServer) -module om de primaire zone en DNS-records te configureren.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="e4bd3-163">U ziet dat de `xDnsRecord` twee blokken zijn verpakt `foreach` in lussen die door matrices in de configuratie gegevens worden herhaald.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="e4bd3-164">Opnieuw worden de configuratie gegevens gemaakt door het `DevEnv.ps1` script, die we nu bekijken.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="e4bd3-165">Configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="e4bd3-165">Configuration data</span></span>

<span data-ttu-id="e4bd3-166">Het `DevEnv.ps1` bestand (uit de hoofdmap van de lokale Demo_CI opslag plaats `./InfraDNS/DevEnv.ps1`) geeft de omgeving-specifieke configuratie gegevens in een hashtabel en geeft die hashtabel door aan een aanroep van de `New-DscConfigurationDataDocument` functie die is gedefinieerd in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="e4bd3-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="e4bd3-167">Het `DevEnv.ps1` bestand:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-167">The `DevEnv.ps1` file:</span></span>

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

<span data-ttu-id="e4bd3-168">Met `New-DscConfigurationDataDocument` de functie (gedefinieerd `\Assets\DscPipelineTools\DscPipelineTools.psm1`in) kunt u via programma code een document met configuratie gegevens maken op basis van de hashtabel (knooppunt gegevens) en matrix (niet-knooppunt `RawEnvData` gegevens `OtherEnvData` ) die worden door gegeven als de para meters en.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="e4bd3-169">In ons geval wordt alleen de `RawEnvData` para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="e4bd3-170">Het psake-bouw script</span><span class="sxs-lookup"><span data-stu-id="e4bd3-170">The psake build script</span></span>

<span data-ttu-id="e4bd3-171">Het [psake](https://github.com/psake/psake) `./InfraDNS/Build.ps1`-bouw script dat `Build.ps1` is gedefinieerd in (vanuit de hoofdmap van de opslag plaats Demo_CI) definieert de taken die deel uitmaken van de build.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="e4bd3-172">Er wordt ook gedefinieerd voor welke andere taken elke taak afhankelijk is.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="e4bd3-173">Wanneer het psake-script wordt aangeroepen, wordt de opgegeven taak (of de taak met `Default` de naam als er geen is opgegeven) uitgevoerd en worden alle afhankelijkheden ook uitgevoerd (dit is recursief, zodat afhankelijkheden van de afhankelijkheden worden uitgevoerd, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="e4bd3-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="e4bd3-174">In dit voor beeld wordt `Default` de taak gedefinieerd als:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="e4bd3-175">De `Default` taak heeft geen implementatie zelf, maar heeft een afhankelijkheid voor `CompileConfigs` de taak.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="e4bd3-176">De resulterende keten van taak afhankelijkheden zorgt ervoor dat alle taken in het build-script worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="e4bd3-177">In dit voor beeld wordt het psake-script aangeroepen door een aanroep naar `Invoke-PSake` in het `Initiate.ps1` bestand (dat zich in de hoofdmap van de Demo_CI opslag plaats bevindt):</span><span class="sxs-lookup"><span data-stu-id="e4bd3-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

<span data-ttu-id="e4bd3-178">Wanneer we de build-definitie voor het voor beeld in TFS maken, leveren we ons psake-script bestand `fileName` als de para meter voor dit script.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="e4bd3-179">Het build-script definieert de volgende taken:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="e4bd3-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="e4bd3-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="e4bd3-181">Wordt `DevEnv.ps1`uitgevoerd, waarmee het bestand met configuratie gegevens wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="e4bd3-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="e4bd3-182">InstallModules</span></span>

<span data-ttu-id="e4bd3-183">Installeert de modules die vereist zijn voor `DNSServer.ps1`de configuratie.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="e4bd3-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="e4bd3-184">ScriptAnalysis</span></span>

<span data-ttu-id="e4bd3-185">Hiermee wordt de [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer)aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="e4bd3-186">Unit tests</span><span class="sxs-lookup"><span data-stu-id="e4bd3-186">UnitTests</span></span>

<span data-ttu-id="e4bd3-187">Voert de tests voor de ziekte van de [Inpest](https://github.com/pester/Pester/wiki) -eenheid uit.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="e4bd3-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="e4bd3-188">CompileConfigs</span></span>

<span data-ttu-id="e4bd3-189">Compileert de configuratie (`DNSServer.ps1`) in een MOF-bestand met behulp van de configuratie gegevens `GenerateEnvironmentFiles` die door de taak worden gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="e4bd3-190">Hygiëne</span><span class="sxs-lookup"><span data-stu-id="e4bd3-190">Clean</span></span>

<span data-ttu-id="e4bd3-191">Hiermee maakt u de mappen die worden gebruikt voor het voor beeld en worden alle test resultaten, configuratie gegevensbestand en modules uit eerdere uitvoeringen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="e4bd3-192">Het psake-implementatie script</span><span class="sxs-lookup"><span data-stu-id="e4bd3-192">The psake deploy script</span></span>

<span data-ttu-id="e4bd3-193">Het [psake](https://github.com/psake/psake) -implementatie script dat `Deploy.ps1` is `./InfraDNS/Deploy.ps1`gedefinieerd in (vanuit de hoofdmap van de opslag plaats Demo_CI) definieert taken waarmee de configuratie wordt geïmplementeerd en uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="e4bd3-194">`Deploy.ps1`Hiermee definieert u de volgende taken:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="e4bd3-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="e4bd3-195">DeployModules</span></span>

<span data-ttu-id="e4bd3-196">Hiermee wordt een Power shell `TestAgent1` -sessie gestart op en worden de modules geïnstalleerd met de DSC-resources die vereist zijn voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="e4bd3-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="e4bd3-197">DeployConfigs</span></span>

<span data-ttu-id="e4bd3-198">Roept de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) op om de configuratie uit `TestAgent1`te voeren.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="e4bd3-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="e4bd3-199">IntegrationTests</span></span>

<span data-ttu-id="e4bd3-200">Voert de tests voor de integratie van de [ziekte](https://github.com/pester/Pester/wiki) uit.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="e4bd3-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="e4bd3-201">AcceptanceTests</span></span>

<span data-ttu-id="e4bd3-202">Voert de acceptatie tests van de [ziekte](https://github.com/pester/Pester/wiki) uit.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="e4bd3-203">Hygiëne</span><span class="sxs-lookup"><span data-stu-id="e4bd3-203">Clean</span></span>

<span data-ttu-id="e4bd3-204">Hiermee verwijdert u alle modules die zijn geïnstalleerd in eerdere uitvoeringen en zorgt u ervoor dat de map test resultaat bestaat.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="e4bd3-205">Test scripts</span><span class="sxs-lookup"><span data-stu-id="e4bd3-205">Test scripts</span></span>

<span data-ttu-id="e4bd3-206">Acceptatie, integratie en eenheids tests worden gedefinieerd in scripts in de `Tests` map (in de hoofdmap van de opslag plaats van `./InfraDNS/Tests`Demo_CI), elk in de `DNSServer.tests.ps1` bestanden die in hun respectieve mappen worden genoemd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="e4bd3-207">De test scripts gebruiken de syntaxis van [parasieten](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) .</span><span class="sxs-lookup"><span data-stu-id="e4bd3-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="e4bd3-208">Eenheids tests</span><span class="sxs-lookup"><span data-stu-id="e4bd3-208">Unit tests</span></span>

<span data-ttu-id="e4bd3-209">De eenheids tests testen de DSC-configuraties zelf om ervoor te zorgen dat de configuraties te maken krijgen met wat er wordt verwacht wanneer ze worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="e4bd3-210">Het test script voor de eenheid maakt gebruik van [parasieten](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="e4bd3-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="e4bd3-211">Integratie tests</span><span class="sxs-lookup"><span data-stu-id="e4bd3-211">Integration tests</span></span>

<span data-ttu-id="e4bd3-212">De integratie tests testen de configuratie van het systeem om ervoor te zorgen dat het systeem zoals verwacht is geconfigureerd wanneer het is geïntegreerd met andere onderdelen.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="e4bd3-213">Deze tests worden uitgevoerd op het doel knooppunt nadat het is geconfigureerd met DSC.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="e4bd3-214">Het integratie test script maakt gebruik van een combi natie van [ziekteloze](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxis.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="e4bd3-215">Acceptatie tests</span><span class="sxs-lookup"><span data-stu-id="e4bd3-215">Acceptance tests</span></span>

<span data-ttu-id="e4bd3-216">Acceptatie tests testen het systeem om ervoor te zorgen dat deze naar verwachting werkt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="e4bd3-217">Zo wordt bijvoorbeeld getest of een webpagina de juiste informatie retourneert wanneer er een query wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="e4bd3-218">Deze tests worden op afstand uitgevoerd vanaf het doel knooppunt om praktijk scenario's te testen.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="e4bd3-219">Het integratie test script maakt gebruik van een combi natie van [ziekteloze](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxis.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="e4bd3-220">De build definiëren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-220">Define the build</span></span>

<span data-ttu-id="e4bd3-221">Nu onze code is geüpload naar TFS en u hebt bekeken wat er gebeurt, gaan we onze build definiëren.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="e4bd3-222">Hier worden alleen de build-stappen besproken die u aan de build gaat toevoegen.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="e4bd3-223">Zie [een build-definitie maken en in de wachtrij plaatsen](/azure/devops/pipelines/create-first-pipeline)voor instructies over het maken van een build-definitie in tFS.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/create-first-pipeline).</span></span>

<span data-ttu-id="e4bd3-224">Maak een nieuwe build-definitie (Selecteer de **lege** sjabloon) met de naam ' InfraDNS '.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="e4bd3-225">Voeg de volgende stappen toe om de definitie te bouwen:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="e4bd3-226">Power shell-script</span><span class="sxs-lookup"><span data-stu-id="e4bd3-226">PowerShell Script</span></span>
- <span data-ttu-id="e4bd3-227">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-227">Publish Test Results</span></span>
- <span data-ttu-id="e4bd3-228">Bestanden kopiëren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-228">Copy Files</span></span>
- <span data-ttu-id="e4bd3-229">Artefact publiceren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-229">Publish Artifact</span></span>

<span data-ttu-id="e4bd3-230">Nadat u deze build-stappen hebt toegevoegd, bewerkt u de eigenschappen van elke stap als volgt:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="e4bd3-231">Power shell-script</span><span class="sxs-lookup"><span data-stu-id="e4bd3-231">PowerShell Script</span></span>

1. <span data-ttu-id="e4bd3-232">Stel de eigenschap **type** in `File Path`op.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="e4bd3-233">Stel de eigenschap **script pad** in `initiate.ps1`op.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="e4bd3-234">Voeg `-fileName build` toe aan de eigenschap **Arguments** .</span><span class="sxs-lookup"><span data-stu-id="e4bd3-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="e4bd3-235">Met deze build-stap `initiate.ps1` wordt het bestand uitgevoerd, dat het psake-build-script aanroept.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="e4bd3-236">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-236">Publish Test Results</span></span>

1. <span data-ttu-id="e4bd3-237">De **indeling van het test resultaat** instellen op`NUnit`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="e4bd3-238">**Testresultaten-bestanden** instellen op`InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="e4bd3-239">Stel de titel van de `Unit` **test uitvoering** in op.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="e4bd3-240">Zorg ervoor dat de **optie opties** **ingeschakeld** en **altijd uitvoeren** zijn geselecteerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="e4bd3-241">Met deze build-stap worden de eenheids tests uitgevoerd in het schadelijke script dat we eerder hebben bekeken en worden de `InfraDNS/Tests/Results/*.xml` resultaten opgeslagen in de map.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="e4bd3-242">Bestanden kopiëren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-242">Copy Files</span></span>

1. <span data-ttu-id="e4bd3-243">Voeg de volgende regels toe aan de **inhoud**:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="e4bd3-244">Stel **TargetFolder** in op`$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="e4bd3-245">Met deze stap worden de build-en test scripts gekopieerd naar de staging-directory, zodat de volgende stap kan worden gepubliceerd als constructie-artefacten.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="e4bd3-246">Artefact publiceren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-246">Publish Artifact</span></span>

1. <span data-ttu-id="e4bd3-247">**Pad naar publicatie** instellen`$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="e4bd3-248">**Artefact naam** instellen op`Deploy`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="e4bd3-249">**Type artefact** instellen op`Server`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="e4bd3-250">Opties `Enabled` selecteren in **besturings elementen**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="e4bd3-251">Continue integratie inschakelen</span><span class="sxs-lookup"><span data-stu-id="e4bd3-251">Enable continuous integration</span></span>

<span data-ttu-id="e4bd3-252">Nu gaan we een trigger instellen die ervoor zorgt dat het project op elk gewenst moment een wijziging in de `ci-cd-example` vertakking van de Git-opslag plaats wordt ingecheckt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="e4bd3-253">Klik in TFS op het tabblad **Build & release**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="e4bd3-254">Selecteer de `DNS Infra` definitie van de build en klik op **bewerken**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="e4bd3-255">Klik op het tabblad **Triggers**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="e4bd3-256">Selecteer **doorlopende integratie (CI)** en `refs/heads/ci-cd-example` Selecteer in de vervolg keuzelijst vertakking</span><span class="sxs-lookup"><span data-stu-id="e4bd3-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="e4bd3-257">Klik op **Opslaan** en vervolgens op **OK**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="e4bd3-258">Elke wijziging in de TFS Git-opslag plaats activeert nu een geautomatiseerde build.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="e4bd3-259">De release definitie maken</span><span class="sxs-lookup"><span data-stu-id="e4bd3-259">Create the release definition</span></span>

<span data-ttu-id="e4bd3-260">We gaan een release definitie maken zodat het project wordt geïmplementeerd in de ontwikkel omgeving met elke code inchecken.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="e4bd3-261">Als u dit wilt doen, voegt u een nieuwe release definitie `InfraDNS` toe die is gekoppeld aan de build-definitie die u eerder hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="e4bd3-262">Zorg ervoor dat u **doorlopende implementatie** selecteert zodat een nieuwe release wordt geactiveerd wanneer een nieuwe build wordt voltooid.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="e4bd3-263">([Wat zijn release pijplijnen?](/azure/devops/pipelines/release/)) en configureer deze als volgt:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-263">([What are release pipelines?](/azure/devops/pipelines/release/)) and configure it as follows:</span></span>

<span data-ttu-id="e4bd3-264">Voeg de volgende stappen toe aan de release definitie:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="e4bd3-265">Power shell-script</span><span class="sxs-lookup"><span data-stu-id="e4bd3-265">PowerShell Script</span></span>
- <span data-ttu-id="e4bd3-266">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-266">Publish Test Results</span></span>
- <span data-ttu-id="e4bd3-267">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-267">Publish Test Results</span></span>

<span data-ttu-id="e4bd3-268">Bewerk de stappen als volgt:</span><span class="sxs-lookup"><span data-stu-id="e4bd3-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="e4bd3-269">Power shell-script</span><span class="sxs-lookup"><span data-stu-id="e4bd3-269">PowerShell Script</span></span>

1. <span data-ttu-id="e4bd3-270">Stel het veld **scriptpad** in op`$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="e4bd3-271">Stel het veld **Arguments** in op`-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="e4bd3-272">Eerste publicatie Testresultaten</span><span class="sxs-lookup"><span data-stu-id="e4bd3-272">First Publish Test Results</span></span>

1. <span data-ttu-id="e4bd3-273">Selecteren `NUnit` voor het veld met de indeling van het **test resultaat**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="e4bd3-274">Stel het veld **test resultaat bestanden** in op`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="e4bd3-275">Stel de **titel van de test uitvoering** in op`Integration`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="e4bd3-276">Schakel onder **controle opties de optie** **altijd uitvoeren**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="e4bd3-277">Tweede publicatie Testresultaten</span><span class="sxs-lookup"><span data-stu-id="e4bd3-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="e4bd3-278">Selecteren `NUnit` voor het veld met de indeling van het **test resultaat**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="e4bd3-279">Stel het veld **test resultaat bestanden** in op`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="e4bd3-280">Stel de **titel van de test uitvoering** in op`Acceptance`</span><span class="sxs-lookup"><span data-stu-id="e4bd3-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="e4bd3-281">Schakel onder **controle opties de optie** **altijd uitvoeren**</span><span class="sxs-lookup"><span data-stu-id="e4bd3-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="e4bd3-282">Uw resultaten controleren</span><span class="sxs-lookup"><span data-stu-id="e4bd3-282">Verify your results</span></span>

<span data-ttu-id="e4bd3-283">Telkens wanneer u wijzigingen in de `ci-cd-example` vertakking naar tFS pusht, wordt een nieuwe build gestart.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="e4bd3-284">Als de build is voltooid, wordt er een nieuwe implementatie geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="e4bd3-285">U kunt het resultaat van de implementatie controleren door een browser te openen op de client computer en naar te `www.contoso.com`navigeren.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e4bd3-286">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="e4bd3-286">Next steps</span></span>

<span data-ttu-id="e4bd3-287">In dit voor beeld wordt de DNS `TestAgent1` -server zo geconfigureerd `www.contoso.com` , dat de `TestAgent2`URL wordt omgezet naar, maar een website niet daad werkelijk wordt geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="e4bd3-288">Het skelet hiervoor is te zien in de opslag plaats onder de `WebApp` map.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="e4bd3-289">U kunt de beschik bare stubs gebruiken voor het maken van psake-scripts, ziekte tests en DSC-configuraties om uw eigen website te implementeren.</span><span class="sxs-lookup"><span data-stu-id="e4bd3-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
