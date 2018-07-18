---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Gedeeltelijke configuraties van PowerShell Desired State Configuration
ms.openlocfilehash: 6d344b666421aba5745945f6148570e4c8229c1a
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093929"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="45731-103">Gedeeltelijke configuraties van PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="45731-103">PowerShell Desired State Configuration partial configurations</span></span>

> <span data-ttu-id="45731-104">Van toepassing op: Windows PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="45731-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="45731-105">In PowerShell 5.0 kunt Desired State Configuration (DSC) configuraties moeten worden geleverd in fragmenten en uit meerdere bronnen.</span><span class="sxs-lookup"><span data-stu-id="45731-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="45731-106">De lokale Configuration Manager (LCM) op het doelknooppunt wordt de fragmenten samen geplaatst voordat u deze als een configuratie voor één toepast.</span><span class="sxs-lookup"><span data-stu-id="45731-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="45731-107">Op deze manier kunt delen van de controle van de configuratie tussen teams of personen.</span><span class="sxs-lookup"><span data-stu-id="45731-107">This capability allows sharing control of configuration between teams or individuals.</span></span>
<span data-ttu-id="45731-108">Bijvoorbeeld, als twee of meer teams van ontwikkelaars aan een service samenwerken, ze mogelijk elke wilt configuraties voor het beheren van hun onderdeel van de service maken.</span><span class="sxs-lookup"><span data-stu-id="45731-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="45731-109">Elk van deze configuraties kan worden opgehaald uit verschillende pull-servers en ze in verschillende stadia van de ontwikkeling kunnen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="45731-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="45731-110">Gedeeltelijke configuraties kunnen ook verschillende personen of teams voor het beheren van verschillende aspecten van het configureren van knooppunten zonder voor de coördinatie van het bewerken van een configuratie voor één document.</span><span class="sxs-lookup"><span data-stu-id="45731-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="45731-111">Bijvoorbeeld, kan één team zijn verantwoordelijk voor het implementeren van een virtuele machine en het besturingssysteem, terwijl een ander team zou kunnen voor andere toepassingen en services op deze VM implementeren.</span><span class="sxs-lookup"><span data-stu-id="45731-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="45731-112">Gedeeltelijke configuraties kan elk team een eigen configuratie, zonder een van beide wordt onnodig ingewikkeld maken.</span><span class="sxs-lookup"><span data-stu-id="45731-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="45731-113">U kunt gedeeltelijke configuraties in push-modus, pull-modus of een combinatie van beide.</span><span class="sxs-lookup"><span data-stu-id="45731-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="45731-114">Gedeeltelijke configuraties in de pushmodus gebruikt</span><span class="sxs-lookup"><span data-stu-id="45731-114">Partial configurations in push mode</span></span>

<span data-ttu-id="45731-115">Voor het gebruik van gedeeltelijke configuraties in de pushmodus gebruikt, kunt u de LCM configureren in het doelknooppunt voor het ontvangen van de gedeeltelijke configuraties.</span><span class="sxs-lookup"><span data-stu-id="45731-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="45731-116">Elke gedeeltelijke configuratie moet worden gepusht naar het doel met behulp van de `Publish-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45731-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="45731-117">Het doelknooppunt vervolgens combineert de gedeeltelijke configuratie in een configuratie voor één, en u kunt de configuratie toepassen door het aanroepen van de [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="45731-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="45731-118">De LCM voor push-modus gedeeltelijke configuraties configureren</span><span class="sxs-lookup"><span data-stu-id="45731-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="45731-119">Als u wilt configureren de LCM voor gedeeltelijke configuraties in de pushmodus gebruikt, maakt u een **DSCLocalConfigurationManager** configuratie met een **PartialConfiguration** blokkeren voor elke gedeeltelijke configuratie.</span><span class="sxs-lookup"><span data-stu-id="45731-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="45731-120">Zie voor meer informatie over het configureren van de LCM [Windows de Local Configuration Manager configureren](/powershell/dsc/metaConfig).</span><span class="sxs-lookup"><span data-stu-id="45731-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](/powershell/dsc/metaConfig).</span></span>
<span data-ttu-id="45731-121">Het volgende voorbeeld ziet u een LCM-configuratie die wordt verwacht twee gedeeltelijke configuraties dat: één waarmee het besturingssysteem wordt geïmplementeerd, en één die wordt geïmplementeerd en geconfigureerd van SharePoint.</span><span class="sxs-lookup"><span data-stu-id="45731-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {

        PartialConfiguration ServiceAccountConfig
        {
            Description = 'Configuration to add the SharePoint service account to the Administrators group.'
            RefreshMode = 'Push'
        }
           PartialConfiguration SharePointConfig
        {
            Description = 'Configuration for the SharePoint server'
            RefreshMode = 'Push'
        }
    }
}

PartialConfigDemo
```

<span data-ttu-id="45731-122">De **RefreshMode** voor elke gedeeltelijke configuratie is ingesteld op 'Push'.</span><span class="sxs-lookup"><span data-stu-id="45731-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="45731-123">De namen van de **PartialConfiguration** blokken (in dit geval "ServiceAccountConfig" en "SharePointConfig") moeten overeenkomen met precies de namen van de configuraties die worden gepusht naar het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="45731-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="45731-124">De naam van elk **PartialConfiguration** blok moet overeenkomen met de werkelijke naam van de configuratie als deze is opgegeven in het configuratiescript, niet de naam van het MOF-bestand de naam van het doelknooppunt of moet`localhost`.</span><span class="sxs-lookup"><span data-stu-id="45731-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="45731-125">Publiceren en starten van push-modus gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="45731-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="45731-126">Vervolgens aanroepen [publiceren-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) voor elke configuratie geven de mappen die de van configuratiedocumenten als bevatten de **pad** parameters.</span><span class="sxs-lookup"><span data-stu-id="45731-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="45731-127">`Publish-DSCConfiguration`Hiermee plaatst u de configuratie van MOF-bestanden naar de doelknooppunten.</span><span class="sxs-lookup"><span data-stu-id="45731-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="45731-128">Na het publiceren van beide configuraties, u kunt aanroepen `Start-DSCConfiguration –UseExisting` op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="45731-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="45731-129">Bijvoorbeeld, als u hebt de volgende configuratie MOF-documenten op het knooppunt authoring gecompileerd:</span><span class="sxs-lookup"><span data-stu-id="45731-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
Get-ChildItem -Recurse
```

```output
    Directory: C:\PartialConfigTest

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        8/11/2016   1:55 PM                ServiceAccountConfig
d-----       11/17/2016   4:14 PM                SharePointConfig

    Directory: C:\PartialConfigTest\ServiceAccountConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/11/2016   2:02 PM           2034 TestVM.mof

    Directory: C:\DscTests\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="45731-130">U zou publiceren en voer de configuraties als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="45731-130">You would publish and run the configurations as follows:</span></span>

```powershell
Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
Start-DscConfiguration -UseExisting -ComputerName 'TestVM'
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

> [!Note]
> <span data-ttu-id="45731-131">De gebruiker die de [publiceren-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet moet beheerdersbevoegdheden hebben op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="45731-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="45731-132">Gedeeltelijke configuraties in de pull-modus</span><span class="sxs-lookup"><span data-stu-id="45731-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="45731-133">Gedeeltelijke configuraties kunnen worden opgehaald uit een of meer pull-servers (Zie voor meer informatie over pull-servers, [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="45731-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="45731-134">Om dit te doen, moet u de LCM configureren op het doelknooppunt voor het ophalen van de gedeeltelijke configuraties, en geef de naam en zoek de configuratiedocumenten correct op de pull-servers.</span><span class="sxs-lookup"><span data-stu-id="45731-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="45731-135">De LCM voor pull-knooppuntconfiguraties configureren</span><span class="sxs-lookup"><span data-stu-id="45731-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="45731-136">Als u wilt de LCM om op te halen van gedeeltelijke configuraties van een pull-server is geconfigureerd, definieert u de pull-server in een een **ConfigurationRepositoryWeb** (voor een HTTP-pull-server) of **ConfigurationRepositoryShare** () voor een SMB-pull-server) blokkeren.</span><span class="sxs-lookup"><span data-stu-id="45731-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="45731-137">Vervolgens maakt u **PartialConfiguration** blokken die naar de pull-server met behulp van verwijzen de **ConfigurationSource** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="45731-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="45731-138">U moet ook maken een **instellingen** blokkeren om op te geven dat de LCM pull-modus gebruikt, en om op te geven de **ConfigurationNames** of **ConfigurationID** die de pull-server en doel-knooppunt gebruiken om u te identificeren van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="45731-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="45731-139">De volgende meta-configuratie definieert een HTTP-pull-server met de naam CONTOSO-PullSrv en twee gedeeltelijke configuraties die gebruikmaken van die pull-server.</span><span class="sxs-lookup"><span data-stu-id="45731-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="45731-140">Voor meer informatie over het configureren van de LCM via **ConfigurationNames**, Zie [instellen van een pull-client met behulp van configuratienamen](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="45731-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span>
<span data-ttu-id="45731-141">Voor informatie over het configureren van de LCM via **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="45731-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="45731-142">De LCM voor pull-modus configuraties met behulp van configuratienamen configureren</span><span class="sxs-lookup"><span data-stu-id="45731-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               ="ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
        }
}
```

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="45731-143">De LCM voor pull-modus configuraties met behulp van ConfigurationID configureren</span><span class="sxs-lookup"><span data-stu-id="45731-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemoConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode                     = 'Pull'
            ConfigurationID                 = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins            = 30
            RebootNodeIfNeeded              = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description                     = 'Configuration for the Base OS'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode                     = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description                     = 'Configuration for the Sharepoint Server'
            ConfigurationSource             = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Pull'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="45731-144">U kunt gedeeltelijke configuraties van meer dan één pull-server ophalen, moet u alleen voor het definiëren van elke pull-server en vervolgens verwijzen naar de juiste pull-server in elk **PartialConfiguration** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="45731-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="45731-145">Nadat de configuratie van de metagegevens is gemaakt, moet u het voor het maken van een configuratiedocument (een MOF-bestand) en roep vervolgens uitvoeren [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) de LCM configureren.</span><span class="sxs-lookup"><span data-stu-id="45731-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="45731-146">Naamgeving en het plaatsen van de van configuratiedocumenten op de pull-server (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="45731-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="45731-147">De documenten gedeeltelijke configuratie moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="45731-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="45731-148">Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="45731-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="45731-149">Als u van slechts een gedeeltelijke configuratie van een afzonderlijke pull-server binnenhalen, kan het configuratiebestand voor elke naam hebben.</span><span class="sxs-lookup"><span data-stu-id="45731-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span>
<span data-ttu-id="45731-150">Als u van meer dan een gedeeltelijke configuratie van een pull-server binnenhalen, het configuratiebestand kan worden met de naam `<ConfigurationName>.mof`, waarbij *ConfigurationName* is de naam van de gedeeltelijke configuratie of `<ConfigurationName>.<NodeName>.mof`, waarbij  *ConfigurationName* is de naam van de gedeeltelijke configuratie en *knooppuntnaam* is de naam van het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="45731-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span>
<span data-ttu-id="45731-151">Hiermee kunt u pull-configuraties van Azure Automation DSC pull-server.</span><span class="sxs-lookup"><span data-stu-id="45731-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="45731-152">Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="45731-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="45731-153">De configuratiedocumenten moeten de naam als volgt: `ConfigurationName.mof`, waarbij *ConfigurationName* is de naam van de gedeeltelijke configuratie.</span><span class="sxs-lookup"><span data-stu-id="45731-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="45731-154">In ons voorbeeld moeten u als volgt de van configuratiedocumenten krijgen:</span><span class="sxs-lookup"><span data-stu-id="45731-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="45731-155">Naamgeving en het plaatsen van de van configuratiedocumenten op de pull-server (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="45731-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="45731-156">De documenten gedeeltelijke configuratie moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="45731-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="45731-157">De configuratiedocumenten moeten de naam als volgt: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="45731-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="45731-158">\* ConfigurationID8`.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijke en _ConfigurationID_ is de configuratie-ID is gedefinieerd in de LCM op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="45731-158">\*ConfigurationID8`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="45731-159">In ons voorbeeld moeten u als volgt de van configuratiedocumenten krijgen:</span><span class="sxs-lookup"><span data-stu-id="45731-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="45731-160">Gedeeltelijke configuraties uitvoeren vanaf een pull-server</span><span class="sxs-lookup"><span data-stu-id="45731-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="45731-161">Nadat de LCM op het doelknooppunt is geconfigureerd en de configuratiedocumenten zijn gemaakt en naar behoren met de naam van de pull-server, wordt het doelknooppunt de gedeeltelijke configuraties ophalen, deze combineren en de resulterende configuratie tegen de normale toepassen intervallen zoals opgegeven door de **RefreshFrequencyMins** eigenschap van de LCM.</span><span class="sxs-lookup"><span data-stu-id="45731-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="45731-162">Als u wilt vernieuwen wilt afdwingen, u kunt aanroepen de [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) -cmdlet voor het ophalen van de configuraties, en vervolgens `Start-DSCConfiguration –UseExisting` om toe te passen.</span><span class="sxs-lookup"><span data-stu-id="45731-162">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="45731-163">Gedeeltelijke configuraties in gemengde push als pull-modi</span><span class="sxs-lookup"><span data-stu-id="45731-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="45731-164">U kunt ook push combineren en pull-modi voor gedeeltelijke configuraties.</span><span class="sxs-lookup"><span data-stu-id="45731-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="45731-165">Dat wil zeggen, hebt u kunnen een gedeeltelijke configuratie die is opgehaald uit een pull-server, terwijl een andere gedeeltelijke configuratie wordt gepusht.</span><span class="sxs-lookup"><span data-stu-id="45731-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="45731-166">Geef de vernieuwingsmodus voor voor elke gedeeltelijke configuratie zoals beschreven in de vorige secties.</span><span class="sxs-lookup"><span data-stu-id="45731-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span>
<span data-ttu-id="45731-167">Bijvoorbeeld, de volgende meta-configuratie wordt beschreven hoe u het hetzelfde voorbeeld het `ServiceAccountConfig` gedeeltelijke configuratie in de pull-modus en de `SharePointConfig` gedeeltelijke configuratie in de pushmodus gebruikt.</span><span class="sxs-lookup"><span data-stu-id="45731-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="45731-168">Gemengde push als pull-modi ConfigurationNames gebruiken</span><span class="sxs-lookup"><span data-stu-id="45731-168">Mixed push and pull modes using ConfigurationNames</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration PartialConfigDemoConfigNames
{
        Settings
        {
            RefreshFrequencyMins            = 30;
            RefreshMode                     = "PULL";
            ConfigurationMode               = "ApplyAndAutocorrect";
            AllowModuleOverwrite            = $true;
            RebootNodeIfNeeded              = $true;
            ConfigurationModeFrequencyMins  = 60;
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL                       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey                 = 5b41f4e6-5e6d-45f5-8102-f2227468ef38
            ConfigurationNames              = @("ServiceAccountConfig", "SharePointConfig")
        }

        PartialConfiguration ServiceAccountConfig
        {
            Description                     = "ServiceAccountConfig"
            ConfigurationSource             = @("[ConfigurationRepositoryWeb]CONTOSO-PullSrv")
            RefreshMode                     = 'Pull'
        }

        PartialConfiguration SharePointConfig
        {
            Description                     = "SharePointConfig"
            DependsOn                       = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode                     = 'Push'
        }

}
```

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="45731-169">Gemengde push als pull-modi ConfigurationID gebruiken</span><span class="sxs-lookup"><span data-stu-id="45731-169">Mixed push and pull modes using ConfigurationID</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PartialConfigDemo
{
    Node localhost
    {
        Settings
        {
            RefreshMode             = 'Pull'
            ConfigurationID         = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins    = 30
            RebootNodeIfNeeded      = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL               = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

           PartialConfiguration ServiceAccountConfig
        {
            Description             = 'Configuration for the Base OS'
            ConfigurationSource     = '[ConfigurationRepositoryWeb]CONTOSO-PullSrv'
            RefreshMode             = 'Pull'
        }
           PartialConfiguration SharePointConfig
        {
            Description             = 'Configuration for the Sharepoint Server'
            DependsOn               = '[PartialConfiguration]ServiceAccountConfig'
            RefreshMode             = 'Push'
        }
    }
}
PartialConfigDemo
```

<span data-ttu-id="45731-170">Houd er rekening mee dat de **RefreshMode** die is opgegeven in het blok instellingen is 'Pull', maar de **RefreshMode** voor de `SharePointConfig` gedeeltelijke configuratie is 'Push'.</span><span class="sxs-lookup"><span data-stu-id="45731-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="45731-171">Geef de naam en zoek de configuratiebestanden van de MOF zoals hierboven beschreven voor de modi van hun respectieve vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="45731-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="45731-172">Bel `Publish-DSCConfiguration` publiceren de `SharePointConfig` gedeeltelijke configuratie, en een wachten op de `ServiceAccountConfig` configuratie die moet worden opgehaald uit de pull-server of een vernieuwing forceren door het aanroepen van [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span><span class="sxs-lookup"><span data-stu-id="45731-172">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="45731-173">Voorbeeldconfiguratie ServiceAccountConfig gedeeltelijk</span><span class="sxs-lookup"><span data-stu-id="45731-173">Example ServiceAccountConfig Partial Configuration</span></span>

```powershell
Configuration ServiceAccountConfig
{
    Param (
        [Parameter(Mandatory,
                   HelpMessage="Domain credentials required to add domain\sharepoint_svc to the local Administrators group.")]
        [ValidateNotNullOrEmpty()]
        [pscredential]$Credential
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Group LocalAdmins
        {
            GroupName           = 'Administrators'
            MembersToInclude    = 'domain\sharepoint_svc',
                                  'admins@example.domain'
            Ensure              = 'Present'
            Credential          = $Credential
        }

        WindowsFeature Telnet
        {
            Name                = 'Telnet-Server'
            Ensure              = 'Absent'
        }
    }
}
ServiceAccountConfig
```

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="45731-174">Voorbeeldconfiguratie SharePointConfig gedeeltelijk</span><span class="sxs-lookup"><span data-stu-id="45731-174">Example SharePointConfig Partial Configuration</span></span>

```powershell
Configuration SharePointConfig
{
    Param (
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [pscredential]$ProductKey
    )

    Import-DscResource -ModuleName xSharePoint

    Node localhost
    {
        xSPInstall SharePointDefault
        {
            Ensure      = 'Present'
            BinaryDir   = '\\FileServer\Installers\Sharepoint\'
            ProductKey  = $ProductKey
        }
    }
}
SharePointConfig
```

## <a name="see-also"></a><span data-ttu-id="45731-175">Zie ook</span><span class="sxs-lookup"><span data-stu-id="45731-175">See Also</span></span>

[<span data-ttu-id="45731-176">Windows PowerShell Desired State Configuration Pull-Servers</span><span class="sxs-lookup"><span data-stu-id="45731-176">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="45731-177">Windows de Local Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="45731-177">Windows Configuring the Local Configuration Manager</span></span>](/powershell/dsc/metaConfig)