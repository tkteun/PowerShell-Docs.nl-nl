---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Het bouwen van een pijplijn continue integratie en continue implementatie met DSC
ms.openlocfilehash: faeef5022cbd984cab0620b69db19de8b84cca0e
ms.sourcegitcommit: 68093cc12a7a22c53d11ce7d33c18622921a0dd1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36940341"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="4735b-103">Het bouwen van een pijplijn continue integratie en continue implementatie met DSC</span><span class="sxs-lookup"><span data-stu-id="4735b-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="4735b-104">In dit voorbeeld laat zien hoe een continue integratie met doorlopend implementatie (CI/CD)-pijplijn maken met behulp van PowerShell, DSC, Pester en Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="4735b-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="4735b-105">Nadat de pijplijn is gemaakt en geconfigureerd, kunt u gebruiken deze volledig implementeren, configureren en testen van een DNS-server en host-records die zijn gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="4735b-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="4735b-106">Dit proces wordt het eerste deel van een pijplijn die moet worden gebruikt in een ontwikkelingsomgeving gesimuleerd.</span><span class="sxs-lookup"><span data-stu-id="4735b-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="4735b-107">Een geautomatiseerde CI/CD-pijplijn, kunt u software sneller en betrouwbaarder, ervoor te zorgen dat alle code wordt getest en dat er een huidige build van uw code is beschikbaar te allen tijde.</span><span class="sxs-lookup"><span data-stu-id="4735b-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4735b-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4735b-108">Prerequisites</span></span>

<span data-ttu-id="4735b-109">Dit voorbeeld kunt gebruiken, moet u bekend bent met het volgende:</span><span class="sxs-lookup"><span data-stu-id="4735b-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="4735b-110">Concepten van CI-CD.</span><span class="sxs-lookup"><span data-stu-id="4735b-110">CI-CD concepts.</span></span> <span data-ttu-id="4735b-111">De verwijzing naar een goede kan worden gevonden op [de Release pijplijn Model](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="4735b-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="4735b-112">[GIT](https://git-scm.com/) besturingselement voor de gegevensbron</span><span class="sxs-lookup"><span data-stu-id="4735b-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="4735b-113">De [Pester](https://github.com/pester/Pester) framework testen</span><span class="sxs-lookup"><span data-stu-id="4735b-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="4735b-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="4735b-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="4735b-115">Wat u nodig hebt</span><span class="sxs-lookup"><span data-stu-id="4735b-115">What you will need</span></span>

<span data-ttu-id="4735b-116">Voor het bouwen en uitvoeren van dit voorbeeld, moet u een omgeving met meerdere computers en/of virtuele machines.</span><span class="sxs-lookup"><span data-stu-id="4735b-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="4735b-117">Client</span><span class="sxs-lookup"><span data-stu-id="4735b-117">Client</span></span>

<span data-ttu-id="4735b-118">Dit is de computer waar u doet al het werk instellen en uitvoeren in het voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="4735b-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="4735b-119">De clientcomputer moet een Windows-computer met het volgende zijn geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="4735b-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="4735b-120">GIT</span><span class="sxs-lookup"><span data-stu-id="4735b-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="4735b-121">een lokale git-opslagplaats gekloond van https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="4735b-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="4735b-122">een teksteditor, zoals [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="4735b-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="4735b-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="4735b-123">TFSSrv1</span></span>

<span data-ttu-id="4735b-124">De computer die als host fungeert voor de TFS-server waar u uw build definieert en release.</span><span class="sxs-lookup"><span data-stu-id="4735b-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="4735b-125">Deze computer [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="4735b-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="4735b-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="4735b-126">BuildAgent</span></span>

<span data-ttu-id="4735b-127">De computer met de Windows-agent die wordt gemaakt van het project bouwen.</span><span class="sxs-lookup"><span data-stu-id="4735b-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="4735b-128">Deze computer moet een agent geïnstalleerd en uitgevoerd bouwen Windows hebben.</span><span class="sxs-lookup"><span data-stu-id="4735b-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="4735b-129">Zie [implementeren van een agent op Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) voor instructies over het installeren en uitvoeren van een Windows-build agent.</span><span class="sxs-lookup"><span data-stu-id="4735b-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="4735b-130">U moet ook installeren op zowel de `xDnsServer` en `xNetworking` DSC-modules op deze computer.</span><span class="sxs-lookup"><span data-stu-id="4735b-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="4735b-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="4735b-131">TestAgent1</span></span>

<span data-ttu-id="4735b-132">Dit is de computer die is geconfigureerd als een DNS-server door de DSC-configuratie in dit voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="4735b-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="4735b-133">De computer moet worden uitgevoerd [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="4735b-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="4735b-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="4735b-134">TestAgent2</span></span>

<span data-ttu-id="4735b-135">Dit is de computer die als host fungeert voor de website die in dit voorbeeld configureert.</span><span class="sxs-lookup"><span data-stu-id="4735b-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="4735b-136">De computer moet worden uitgevoerd [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="4735b-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="4735b-137">Voeg de code naar TFS</span><span class="sxs-lookup"><span data-stu-id="4735b-137">Add the code to TFS</span></span>

<span data-ttu-id="4735b-138">We beginnen uit door het maken van een Git-opslagplaats in TFS en importeren van de code van uw lokale opslagplaats op de clientcomputer.</span><span class="sxs-lookup"><span data-stu-id="4735b-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="4735b-139">Als u de opslagplaats Demo_CI hebt niet op uw clientcomputer hebt gekloond, dit nu doen met de volgende git-opdracht:</span><span class="sxs-lookup"><span data-stu-id="4735b-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="4735b-140">Navigeer naar de TFS-server in een webbrowser op de clientcomputer.</span><span class="sxs-lookup"><span data-stu-id="4735b-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="4735b-141">In TFS, [maken van een nieuw teamproject](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) Demo_CI met de naam.</span><span class="sxs-lookup"><span data-stu-id="4735b-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

   <span data-ttu-id="4735b-142">Zorg ervoor dat **versiebeheer** is ingesteld op **Git**.</span><span class="sxs-lookup"><span data-stu-id="4735b-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="4735b-143">Op de clientcomputer voegt u een externe toe aan de opslagplaats die u zojuist hebt gemaakt in TFS met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="4735b-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="4735b-144">Waar `<YourTFSRepoURL>` de kloon-URL naar de TFS-opslagplaats die u in de vorige stap hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4735b-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="4735b-145">Als u niet waar deze URL zoeken weet, Zie [klonen van een bestaande Git-opslagplaats](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span><span class="sxs-lookup"><span data-stu-id="4735b-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="4735b-146">De code van uw lokale opslagplaats pushen naar uw opslagplaats TFS met de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="4735b-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="4735b-147">De opslagplaats TFS worden ingevuld met de code Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="4735b-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="4735b-148">In dit voorbeeld wordt de code in de `ci-cd-example` vertakking van de Git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="4735b-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="4735b-149">Zorg ervoor dat de vertakking opgeven als de standaardvertakking in TFS-project en voor de CI/CD-triggers die u maakt.</span><span class="sxs-lookup"><span data-stu-id="4735b-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="4735b-150">Wat is de code?</span><span class="sxs-lookup"><span data-stu-id="4735b-150">Understanding the code</span></span>

<span data-ttu-id="4735b-151">Voordat we het build- en pijplijnen maken, bekijken we enkele van de code te begrijpen wat er gebeurt.</span><span class="sxs-lookup"><span data-stu-id="4735b-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="4735b-152">Open uw favoriete teksteditor op de clientcomputer en navigeer naar de hoofdmap van uw Demo_CI Git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="4735b-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="4735b-153">De DSC-configuratie</span><span class="sxs-lookup"><span data-stu-id="4735b-153">The DSC configuration</span></span>

<span data-ttu-id="4735b-154">Open het bestand `DNSServer.ps1` (in de hoofdmap van de lokale Demo_CI opslagplaats `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="4735b-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="4735b-155">Dit bestand bevat de DSC-configuratie instellen van de DNS-server.</span><span class="sxs-lookup"><span data-stu-id="4735b-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="4735b-156">Dit is in zijn geheel:</span><span class="sxs-lookup"><span data-stu-id="4735b-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="4735b-157">U ziet de `Node` instructie:</span><span class="sxs-lookup"><span data-stu-id="4735b-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="4735b-158">Hiermee vindt u alle knooppunten die zijn gedefinieerd als bestanden met de rol `DNSServer` in de [configuratiegegevens](configData.md), die wordt gemaakt door de `DevEnv.ps1` script.</span><span class="sxs-lookup"><span data-stu-id="4735b-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="4735b-159">U kunt meer lezen over de `Where` methode in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="4735b-159">You can read more about the `Where` method in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

<span data-ttu-id="4735b-160">Met behulp van de configuratiegegevens voor het definiëren van knooppunten is belangrijk bij het uitvoeren van CI omdat knooppunt informatie waarschijnlijk tussen omgevingen veranderen zullen en configuratiegegevens met kunt u gemakkelijk wijzigingen aanbrengen in knooppunt informatie zonder de configuratiecode te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="4735b-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="4735b-161">In de eerste resource blok, de configuratie roept de [WindowsFeature](windowsFeatureResource.md) om ervoor te zorgen dat de DNS-functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="4735b-161">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="4735b-162">De resource-blokken die resources van de aanroep van volgen de [xDnsServer](https://github.com/PowerShell/xDnsServer) module voor het configureren van de primaire zone en DNS-records.</span><span class="sxs-lookup"><span data-stu-id="4735b-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="4735b-163">U ziet dat de twee `xDnsRecord` blokken zijn samengevoegd in `foreach` lussen die matrices in de configuratiegegevens doorlopen.</span><span class="sxs-lookup"><span data-stu-id="4735b-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="4735b-164">De configuratiegegevens wordt opnieuw gemaakt door de `DevEnv.ps1` script, dat zullen we op volgende.</span><span class="sxs-lookup"><span data-stu-id="4735b-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="4735b-165">Configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="4735b-165">Configuration data</span></span>

<span data-ttu-id="4735b-166">De `DevEnv.ps1` bestand (in de hoofdmap van de lokale Demo_CI opslagplaats `./InfraDNS/DevEnv.ps1`) Hiermee geeft u de omgeving-specifieke configuratiegegevens in een hashtabel en vervolgens die hashtabel doorgegeven aan een aanroep van de `New-DscConfigurationDataDocument` functie, die is gedefinieerd in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="4735b-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="4735b-167">De `DevEnv.ps1` bestand:</span><span class="sxs-lookup"><span data-stu-id="4735b-167">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="4735b-168">De `New-DscConfigurationDataDocument` functie (gedefinieerd in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) via een programma maakt een configuratiebestand voor de gegevens van de hash-tabel (knooppuntgegevens) en de matrix (niet-knooppunt gegevens) die worden doorgegeven als de `RawEnvData` en `OtherEnvData` parameters.</span><span class="sxs-lookup"><span data-stu-id="4735b-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="4735b-169">In ons geval alleen de `RawEnvData` parameter wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4735b-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="4735b-170">Het psake build script</span><span class="sxs-lookup"><span data-stu-id="4735b-170">The psake build script</span></span>

<span data-ttu-id="4735b-171">De [psake](https://github.com/psake/psake) bouwen script gedefinieerd in `Build.ps1` (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Build.ps1`) taken die deel van de build uitmaken definieert.</span><span class="sxs-lookup"><span data-stu-id="4735b-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="4735b-172">Het definieert ook welke andere elke taak afhankelijk van is taken.</span><span class="sxs-lookup"><span data-stu-id="4735b-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="4735b-173">Als deze wordt aangeroepen, het script psake zorgt ervoor dat de opgegeven taak (of de taak met de naam `Default` als niets wordt opgegeven) wordt uitgevoerd en dat alle afhankelijkheden ook uitvoeren (dit is recursieve, zodat de afhankelijkheden van afhankelijkheden hebt uitgevoerd, enzovoort).</span><span class="sxs-lookup"><span data-stu-id="4735b-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="4735b-174">In dit voorbeeld wordt de `Default` taak is gedefinieerd als:</span><span class="sxs-lookup"><span data-stu-id="4735b-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="4735b-175">De `Default` taak geen implementatie zelf, maar afhankelijk is van de `CompileConfigs` taak.</span><span class="sxs-lookup"><span data-stu-id="4735b-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="4735b-176">De resulterende reeks taakafhankelijkheden zorgt ervoor dat alle taken in het build-script worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4735b-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="4735b-177">In dit voorbeeld wordt het script psake opgeroepen door een aanroep naar `Invoke-PSake` in de `Initiate.ps1` bestand (te vinden in de hoofdmap van de opslagplaats Demo_CI):</span><span class="sxs-lookup"><span data-stu-id="4735b-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="4735b-178">Wanneer de build-definitie we in ons voorbeeld in TFS maken, geven we onze scriptbestand psake als de `fileName` parameter voor dit script.</span><span class="sxs-lookup"><span data-stu-id="4735b-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="4735b-179">Het script build definieert de volgende taken:</span><span class="sxs-lookup"><span data-stu-id="4735b-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="4735b-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="4735b-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="4735b-181">Wordt uitgevoerd `DevEnv.ps1`, die het bestand met configuratiegegevens genereert.</span><span class="sxs-lookup"><span data-stu-id="4735b-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="4735b-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="4735b-182">InstallModules</span></span>

<span data-ttu-id="4735b-183">De door de configuratie van de vereiste modules installeert `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4735b-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="4735b-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="4735b-184">ScriptAnalysis</span></span>

<span data-ttu-id="4735b-185">Aanroepen van de [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="4735b-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="4735b-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="4735b-186">UnitTests</span></span>

<span data-ttu-id="4735b-187">Voert de [Pester](https://github.com/pester/Pester/wiki) eenheidstests.</span><span class="sxs-lookup"><span data-stu-id="4735b-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="4735b-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="4735b-188">CompileConfigs</span></span>

<span data-ttu-id="4735b-189">De configuratie wordt gecompileerd (`DNSServer.ps1`) naar een MOF-bestand met behulp van de configuratiegegevens die worden gegenereerd door de `GenerateEnvironmentFiles` taak.</span><span class="sxs-lookup"><span data-stu-id="4735b-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="4735b-190">Opruimen</span><span class="sxs-lookup"><span data-stu-id="4735b-190">Clean</span></span>

<span data-ttu-id="4735b-191">De mappen die wordt gebruikt voor het voorbeeld maakt en verwijdert u alle testresultaten, gegevens configuratiebestanden en modules uit vorige wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4735b-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="4735b-192">De psake script wilt implementeren</span><span class="sxs-lookup"><span data-stu-id="4735b-192">The psake deploy script</span></span>

<span data-ttu-id="4735b-193">De [psake](https://github.com/psake/psake) gedefinieerd in een script voor implementatie `Deploy.ps1` (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Deploy.ps1`) taken die implementeren en uitvoeren van de configuratie definieert.</span><span class="sxs-lookup"><span data-stu-id="4735b-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="4735b-194">`Deploy.ps1` definieert de volgende taken:</span><span class="sxs-lookup"><span data-stu-id="4735b-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="4735b-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="4735b-195">DeployModules</span></span>

<span data-ttu-id="4735b-196">Een PowerShell-sessie begint op `TestAgent1` en installeert u de modules die met de DSC-resources die vereist zijn voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="4735b-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="4735b-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="4735b-197">DeployConfigs</span></span>

<span data-ttu-id="4735b-198">Aanroepen van de [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet uit te voeren van de configuratie op `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="4735b-198">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="4735b-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="4735b-199">IntegrationTests</span></span>

<span data-ttu-id="4735b-200">Voert de [Pester](https://github.com/pester/Pester/wiki) integratie tests.</span><span class="sxs-lookup"><span data-stu-id="4735b-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="4735b-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="4735b-201">AcceptanceTests</span></span>

<span data-ttu-id="4735b-202">Voert de [Pester](https://github.com/pester/Pester/wiki) acceptatie tests.</span><span class="sxs-lookup"><span data-stu-id="4735b-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="4735b-203">Opruimen</span><span class="sxs-lookup"><span data-stu-id="4735b-203">Clean</span></span>

<span data-ttu-id="4735b-204">Hiermee verwijdert u alle modules geïnstalleerd in de vorige wordt uitgevoerd en zorgt ervoor dat de map test resultaat bestaat.</span><span class="sxs-lookup"><span data-stu-id="4735b-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="4735b-205">Scripts testen</span><span class="sxs-lookup"><span data-stu-id="4735b-205">Test scripts</span></span>

<span data-ttu-id="4735b-206">Acceptatie, integratie en eenheid tests worden gedefinieerd in scripts in de `Tests` map (in de hoofdmap van de opslagplaats Demo_CI `./InfraDNS/Tests`), elk in bestanden met de naam `DNSServer.tests.ps1` in de bijbehorende mappen.</span><span class="sxs-lookup"><span data-stu-id="4735b-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="4735b-207">De test scripts gebruik [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.</span><span class="sxs-lookup"><span data-stu-id="4735b-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="4735b-208">Eenheidstests</span><span class="sxs-lookup"><span data-stu-id="4735b-208">Unit tests</span></span>

<span data-ttu-id="4735b-209">De eenheid test test de DSC-configuraties zelf om ervoor te zorgen dat de configuraties wordt verwacht doet wanneer ze worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4735b-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="4735b-210">De eenheid testen script gebruikt [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="4735b-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="4735b-211">Integratie-tests</span><span class="sxs-lookup"><span data-stu-id="4735b-211">Integration tests</span></span>

<span data-ttu-id="4735b-212">De tests integratie test de configuratie van het systeem om ervoor te zorgen dat indien geïntegreerd met andere onderdelen, het systeem is geconfigureerd zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="4735b-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="4735b-213">Deze tests uitgevoerd op het doelknooppunt nadat deze is geconfigureerd met DSC.</span><span class="sxs-lookup"><span data-stu-id="4735b-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="4735b-214">Het testscript integratie maakt gebruik van een combinatie van [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.</span><span class="sxs-lookup"><span data-stu-id="4735b-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="4735b-215">Acceptatie van de tests</span><span class="sxs-lookup"><span data-stu-id="4735b-215">Acceptance tests</span></span>

<span data-ttu-id="4735b-216">Acceptatie van de tests test het systeem om ervoor te zorgen dat deze functie werkt zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="4735b-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="4735b-217">Bijvoorbeeld: test om te controleren of dat een webpagina retourneert de juiste informatie wanneer opgevraagd.</span><span class="sxs-lookup"><span data-stu-id="4735b-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="4735b-218">Deze tests uitvoeren op afstand vanaf het doelknooppunt real-world scenario's testen.</span><span class="sxs-lookup"><span data-stu-id="4735b-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="4735b-219">Het testscript integratie maakt gebruik van een combinatie van [Pester](https://github.com/pester/Pester/wiki) en [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntaxis.</span><span class="sxs-lookup"><span data-stu-id="4735b-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="4735b-220">Definieer de build</span><span class="sxs-lookup"><span data-stu-id="4735b-220">Define the build</span></span>

<span data-ttu-id="4735b-221">Nu dat we onze code hebt geüpload naar TFS en bekeken wat het geval is, gaan we onze build definiëren.</span><span class="sxs-lookup"><span data-stu-id="4735b-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="4735b-222">Hier komen aan bod de build-stappen die u aan de build toevoegen zult.</span><span class="sxs-lookup"><span data-stu-id="4735b-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="4735b-223">Zie voor instructies over het maken van een definitie van de build in TFS [maken en de definitie van een build wachtrij](https://www.visualstudio.com/en-us/docs/build/define/create).</span><span class="sxs-lookup"><span data-stu-id="4735b-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="4735b-224">Een nieuwe build-definitie maken (Selecteer de **leeg** sjabloon) met de naam 'InfraDNS'.</span><span class="sxs-lookup"><span data-stu-id="4735b-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="4735b-225">Voeg dat de volgende stappen uit om u te bouwen definitie:</span><span class="sxs-lookup"><span data-stu-id="4735b-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="4735b-226">PowerShell-Script</span><span class="sxs-lookup"><span data-stu-id="4735b-226">PowerShell Script</span></span>
- <span data-ttu-id="4735b-227">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="4735b-227">Publish Test Results</span></span>
- <span data-ttu-id="4735b-228">Bestanden kopiëren</span><span class="sxs-lookup"><span data-stu-id="4735b-228">Copy Files</span></span>
- <span data-ttu-id="4735b-229">Publiceren van artefacten</span><span class="sxs-lookup"><span data-stu-id="4735b-229">Publish Artifact</span></span>

<span data-ttu-id="4735b-230">Na het toevoegen van deze stappen te bouwen, bewerk de eigenschappen van elke stap als volgt:</span><span class="sxs-lookup"><span data-stu-id="4735b-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4735b-231">PowerShell-Script</span><span class="sxs-lookup"><span data-stu-id="4735b-231">PowerShell Script</span></span>

1. <span data-ttu-id="4735b-232">Stel de **Type** eigenschap `File Path`.</span><span class="sxs-lookup"><span data-stu-id="4735b-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="4735b-233">Stel de **scriptpad** eigenschap `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4735b-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="4735b-234">Voeg `-fileName build` naar de **argumenten** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="4735b-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="4735b-235">Deze stap build wordt uitgevoerd de `initiate.ps1` -bestand, dat het psake build script aanroept.</span><span class="sxs-lookup"><span data-stu-id="4735b-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="4735b-236">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="4735b-236">Publish Test Results</span></span>

1. <span data-ttu-id="4735b-237">Stel **Resultaatindeling testen** naar `NUnit`</span><span class="sxs-lookup"><span data-stu-id="4735b-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="4735b-238">Stel **testresultaten bestanden** naar `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="4735b-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="4735b-239">Stel **testen uitvoeren titel** naar `Unit`.</span><span class="sxs-lookup"><span data-stu-id="4735b-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="4735b-240">Zorg ervoor dat **beheeropties** **ingeschakeld** en **altijd uitgevoerd** zijn beide ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="4735b-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="4735b-241">Deze stap build wordt uitgevoerd de eenheidstests in het Pester-script dat we eerder bekeken en slaat de resultaten in de `InfraDNS/Tests/Results/*.xml` map.</span><span class="sxs-lookup"><span data-stu-id="4735b-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="4735b-242">Bestanden kopiëren</span><span class="sxs-lookup"><span data-stu-id="4735b-242">Copy Files</span></span>

1. <span data-ttu-id="4735b-243">Elk van de volgende regels toevoegen **inhoud**:</span><span class="sxs-lookup"><span data-stu-id="4735b-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="4735b-244">Stel **TargetFolder** naar `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="4735b-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="4735b-245">Deze stap kopieert de build en test scripts aan de staging-map zodanig dat het kan worden gepubliceerd als artefacten bouwen door de volgende stap.</span><span class="sxs-lookup"><span data-stu-id="4735b-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="4735b-246">Publiceren van artefacten</span><span class="sxs-lookup"><span data-stu-id="4735b-246">Publish Artifact</span></span>

1. <span data-ttu-id="4735b-247">Stel **pad voor het publiceren van** naar `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="4735b-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="4735b-248">Stel **artefact naam** naar `Deploy`</span><span class="sxs-lookup"><span data-stu-id="4735b-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="4735b-249">Stel **artefact Type** naar `Server`</span><span class="sxs-lookup"><span data-stu-id="4735b-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="4735b-250">Selecteer `Enabled` in **opties instellen**</span><span class="sxs-lookup"><span data-stu-id="4735b-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="4735b-251">Continue integratie inschakelen</span><span class="sxs-lookup"><span data-stu-id="4735b-251">Enable continuous integration</span></span>

<span data-ttu-id="4735b-252">Nu we een trigger die ervoor zorgt het project stellen dat voor het bouwen van elk gewenst moment een wijziging wordt ingecheckt bij de `ci-cd-example` vertakking van de git-opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="4735b-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="4735b-253">In TFS, klikt u op de **bouwen & Release** tabblad</span><span class="sxs-lookup"><span data-stu-id="4735b-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="4735b-254">Selecteer de `DNS Infra` definitie bouwen en klikt u op **bewerken**</span><span class="sxs-lookup"><span data-stu-id="4735b-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="4735b-255">Klik op de **Triggers** tabblad</span><span class="sxs-lookup"><span data-stu-id="4735b-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="4735b-256">Selecteer **continue integratie (CI)**, en selecteer `refs/heads/ci-cd-example` in de vervolgkeuzelijst vertakking</span><span class="sxs-lookup"><span data-stu-id="4735b-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="4735b-257">Klik op **opslaan** en vervolgens **OK**</span><span class="sxs-lookup"><span data-stu-id="4735b-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="4735b-258">Nu wijziging elke in de TFS git-opslagplaats triggers een geautomatiseerde build.</span><span class="sxs-lookup"><span data-stu-id="4735b-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="4735b-259">De release-definitie maken</span><span class="sxs-lookup"><span data-stu-id="4735b-259">Create the release definition</span></span>

<span data-ttu-id="4735b-260">De definitie van een release we maken zodat het project wordt geïmplementeerd op de ontwikkelomgeving met elke code incheckt.</span><span class="sxs-lookup"><span data-stu-id="4735b-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="4735b-261">U doet dit door een nieuwe toevoegen release die zijn gekoppeld aan de `InfraDNS` bouwen definitie die u eerder hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4735b-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="4735b-262">Selecteer **continue implementatie** zodat een nieuwe release geactiveerd elk gewenst moment een nieuwe build is voltooid.</span><span class="sxs-lookup"><span data-stu-id="4735b-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="4735b-263">([How to: werken met release definities](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) en configureer deze als volgt:</span><span class="sxs-lookup"><span data-stu-id="4735b-263">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="4735b-264">De volgende stappen toevoegen aan de definitie van de release:</span><span class="sxs-lookup"><span data-stu-id="4735b-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="4735b-265">PowerShell-Script</span><span class="sxs-lookup"><span data-stu-id="4735b-265">PowerShell Script</span></span>
- <span data-ttu-id="4735b-266">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="4735b-266">Publish Test Results</span></span>
- <span data-ttu-id="4735b-267">Testresultaten publiceren</span><span class="sxs-lookup"><span data-stu-id="4735b-267">Publish Test Results</span></span>

<span data-ttu-id="4735b-268">Bewerk de stappen uit als volgt:</span><span class="sxs-lookup"><span data-stu-id="4735b-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="4735b-269">PowerShell-Script</span><span class="sxs-lookup"><span data-stu-id="4735b-269">PowerShell Script</span></span>

1. <span data-ttu-id="4735b-270">Stel de **scriptpad** veld `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="4735b-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="4735b-271">Stel de **argumenten** veld `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="4735b-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="4735b-272">Testresultaten eerst publiceren</span><span class="sxs-lookup"><span data-stu-id="4735b-272">First Publish Test Results</span></span>

1. <span data-ttu-id="4735b-273">Selecteer `NUnit` voor de **Resultaatindeling Test** veld</span><span class="sxs-lookup"><span data-stu-id="4735b-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="4735b-274">Stel de **resultaat testbestanden** veld `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="4735b-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="4735b-275">Stel de **testen uitvoeren titel** naar `Integration`</span><span class="sxs-lookup"><span data-stu-id="4735b-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="4735b-276">Onder **beheeropties**, Controleer **altijd worden uitgevoerd**</span><span class="sxs-lookup"><span data-stu-id="4735b-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="4735b-277">Tweede publiceren testresultaten</span><span class="sxs-lookup"><span data-stu-id="4735b-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="4735b-278">Selecteer `NUnit` voor de **Resultaatindeling Test** veld</span><span class="sxs-lookup"><span data-stu-id="4735b-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="4735b-279">Stel de **resultaat testbestanden** veld `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="4735b-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="4735b-280">Stel de **testen uitvoeren titel** naar `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="4735b-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="4735b-281">Onder **beheeropties**, Controleer **altijd worden uitgevoerd**</span><span class="sxs-lookup"><span data-stu-id="4735b-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="4735b-282">De resultaten controleren</span><span class="sxs-lookup"><span data-stu-id="4735b-282">Verify your results</span></span>

<span data-ttu-id="4735b-283">Nu elk gewenst moment u push-wijzigingen de `ci-cd-example` vertakking naar TFS, een nieuwe build wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="4735b-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="4735b-284">Als de build voltooid is, wordt een nieuwe implementatie wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="4735b-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="4735b-285">U kunt het resultaat van de implementatie controleren door een browser op de clientcomputer openen en te navigeren naar `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4735b-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4735b-286">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="4735b-286">Next steps</span></span>

<span data-ttu-id="4735b-287">In dit voorbeeld configureert de DNS-server `TestAgent1` zodat de URL `www.contoso.com` wordt omgezet naar `TestAgent2`, maar deze een website niet daadwerkelijk implementeren.</span><span class="sxs-lookup"><span data-stu-id="4735b-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="4735b-288">Het basisproject hiertoe vindt u in de opslagplaats onder de `WebApp` map.</span><span class="sxs-lookup"><span data-stu-id="4735b-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="4735b-289">U kunt de stubs voor het maken van psake scripts, Pester tests en DSC-configuraties gebruiken voor het implementeren van uw eigen website.</span><span class="sxs-lookup"><span data-stu-id="4735b-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>