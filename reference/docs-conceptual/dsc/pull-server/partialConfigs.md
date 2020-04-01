---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Gedeeltelijke configuraties van de desired state Configuration van Power shell
ms.openlocfilehash: 842acad221d468ca5e4c9e660f0205c567bcc220
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500777"
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="5284d-103">Gedeeltelijke configuraties van de desired state Configuration van Power shell</span><span class="sxs-lookup"><span data-stu-id="5284d-103">PowerShell Desired State Configuration partial configurations</span></span>

<span data-ttu-id="5284d-104">_Van toepassing op: Windows Power shell 5,0 en hoger._</span><span class="sxs-lookup"><span data-stu-id="5284d-104">_Applies To: Windows PowerShell 5.0 and later._</span></span>

<span data-ttu-id="5284d-105">In Power shell 5,0 kunnen configuraties met desired state Configuration (DSC) worden geleverd in fragmenten en uit meerdere bronnen.</span><span class="sxs-lookup"><span data-stu-id="5284d-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="5284d-106">De lokale Configuration Manager (LCM) op het doel knooppunt plaatst de fragmenten samen voordat ze als één configuratie worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="5284d-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="5284d-107">Met deze functie kunt u het beheer van de configuratie tussen teams of individuen delen.</span><span class="sxs-lookup"><span data-stu-id="5284d-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="5284d-108">Als bijvoorbeeld twee of meer teams van ontwikkel aars samen werken aan een service, kunnen ze elk een configuratie maken om hun onderdeel van de service te beheren.</span><span class="sxs-lookup"><span data-stu-id="5284d-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="5284d-109">Elk van deze configuraties kan worden opgehaald van verschillende pull-servers en ze kunnen worden toegevoegd tijdens verschillende ontwikkelings fasen.</span><span class="sxs-lookup"><span data-stu-id="5284d-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="5284d-110">Gedeeltelijke configuraties staan ook toe dat verschillende personen of teams verschillende aspecten van het configureren van knoop punten beheren zonder dat ze het bewerken van één configuratie document hoeven te coördineren.</span><span class="sxs-lookup"><span data-stu-id="5284d-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="5284d-111">Het is bijvoorbeeld mogelijk dat een team verantwoordelijk is voor de implementatie van een virtuele machine en een besturings systeem, terwijl een ander team mogelijk andere toepassingen en services op die virtuele machine implementeert.</span><span class="sxs-lookup"><span data-stu-id="5284d-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="5284d-112">Met gedeeltelijke configuraties kan elk team een eigen configuratie maken, zonder dat ze onnodig ingewikkeld zijn.</span><span class="sxs-lookup"><span data-stu-id="5284d-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="5284d-113">U kunt gedeeltelijke configuraties gebruiken in de push-modus, de pull-modus of een combi natie van beide.</span><span class="sxs-lookup"><span data-stu-id="5284d-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="5284d-114">Gedeeltelijke configuraties in push-modus</span><span class="sxs-lookup"><span data-stu-id="5284d-114">Partial configurations in push mode</span></span>

<span data-ttu-id="5284d-115">Als u gedeeltelijke configuraties wilt gebruiken in de push-modus, configureert u de LCM op het doel knooppunt om de gedeeltelijke configuraties te ontvangen.</span><span class="sxs-lookup"><span data-stu-id="5284d-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="5284d-116">Elke gedeeltelijke configuratie moet worden gepusht naar het doel met behulp van de cmdlet `Publish-DSCConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="5284d-116">Each partial configuration must be pushed to the target by using the `Publish-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="5284d-117">Op het doel knooppunt wordt de gedeeltelijke configuratie vervolgens gecombineerd tot één configuratie en kunt u de configuratie Toep assen door de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) -cmdlet aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="5284d-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="5284d-118">De LCM configureren voor gedeeltelijke configuratie van de push modus</span><span class="sxs-lookup"><span data-stu-id="5284d-118">Configuring the LCM for push-mode partial configurations</span></span>

<span data-ttu-id="5284d-119">Als u de LCM wilt configureren voor gedeeltelijke configuraties in de push-modus, maakt u een **DSCLocalConfigurationManager** -configuratie met één **PartialConfiguration** -blok voor elke gedeeltelijke configuratie.</span><span class="sxs-lookup"><span data-stu-id="5284d-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="5284d-120">Zie [Windows Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="5284d-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span> <span data-ttu-id="5284d-121">In het volgende voor beeld ziet u een configuratie van de LCM die twee gedeeltelijke configuraties verwacht, een die het besturings systeem implementeert en een die share point implementeert en configureert.</span><span class="sxs-lookup"><span data-stu-id="5284d-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="5284d-122">De **RefreshMode** voor elke gedeeltelijke configuratie is ingesteld op push.</span><span class="sxs-lookup"><span data-stu-id="5284d-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="5284d-123">De namen van de **PartialConfiguration** -blokken (in dit geval ' ServiceAccountConfig ' en ' SharePointConfig ') moeten exact overeenkomen met de namen van de configuraties die naar het doel knooppunt worden gepusht.</span><span class="sxs-lookup"><span data-stu-id="5284d-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

> [!Note]
> <span data-ttu-id="5284d-124">De naam van elk **PartialConfiguration** -blok moet overeenkomen met de werkelijke naam van de configuratie zoals die is opgegeven in het configuratie script, niet de naam van het MOF-bestand. dit moet de naam van het doel knooppunt of `localhost`zijn.</span><span class="sxs-lookup"><span data-stu-id="5284d-124">The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="5284d-125">Gedeeltelijke configuraties van push-modus publiceren en starten</span><span class="sxs-lookup"><span data-stu-id="5284d-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="5284d-126">Vervolgens roept u [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) aan voor elke configuratie, waarbij de mappen die de configuratie documenten bevatten worden door gegeven als de para meters voor het **pad** .</span><span class="sxs-lookup"><span data-stu-id="5284d-126">You then call [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="5284d-127">`Publish-DSCConfiguration`plaatst de configuratie-MOF-bestanden naar de doel knooppunten.</span><span class="sxs-lookup"><span data-stu-id="5284d-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="5284d-128">Na het publiceren van beide configuraties kunt u `Start-DSCConfiguration –UseExisting` aanroepen op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5284d-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="5284d-129">Als u bijvoorbeeld de volgende configuratie-MOF-documenten hebt gecompileerd op het knoop punt voor ontwerpen:</span><span class="sxs-lookup"><span data-stu-id="5284d-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

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

    Directory: C:\PartialConfigTest\SharePointConfig

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       11/17/2016   4:14 PM           1930 TestVM.mof
```

<span data-ttu-id="5284d-130">U publiceert en voert de volgende configuraties uit:</span><span class="sxs-lookup"><span data-stu-id="5284d-130">You would publish and run the configurations as follows:</span></span>

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
> <span data-ttu-id="5284d-131">De gebruiker die de cmdlet [Publish-DSCConfiguration uitvoert,](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) moet Administrator bevoegdheden hebben op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5284d-131">The user running the [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="5284d-132">Gedeeltelijke configuraties in de pull-modus</span><span class="sxs-lookup"><span data-stu-id="5284d-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="5284d-133">Gedeeltelijke configuraties kunnen worden opgehaald van een of meer pull-servers (Zie [Windows Power shell desired state Configuration pull servers](pullServer.md)voor meer informatie over pull-servers.</span><span class="sxs-lookup"><span data-stu-id="5284d-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="5284d-134">Als u dit wilt doen, moet u de LCM op het doel knooppunt configureren om de gedeeltelijke configuraties te halen en de configuratie documenten op de pull-servers goed te vinden.</span><span class="sxs-lookup"><span data-stu-id="5284d-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="5284d-135">De LCM configureren voor pull-knooppunt configuraties</span><span class="sxs-lookup"><span data-stu-id="5284d-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="5284d-136">Als u de LCM wilt configureren voor het verzamelen van gedeeltelijke configuraties van een pull-server, definieert u de pull-server in een **ConfigurationRepositoryWeb** (voor een http-pull-server) of **ConfigurationRepositoryShare** (voor een SMB pull-server)-blok.</span><span class="sxs-lookup"><span data-stu-id="5284d-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="5284d-137">Vervolgens maakt u **PartialConfiguration** -blokken die verwijzen naar de pull-server met behulp van de eigenschap **ConfigurationSource** .</span><span class="sxs-lookup"><span data-stu-id="5284d-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="5284d-138">U moet ook een **instellingen** blok maken om op te geven dat de LCM de pull-modus gebruikt en om de **ConfigurationNames** of **ConfigurationID** op te geven die door de pull-server en het doel knooppunt wordt gebruikt om de configuraties te identificeren.</span><span class="sxs-lookup"><span data-stu-id="5284d-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="5284d-139">De volgende meta configuratie definieert een HTTP-pull-server met de naam CONTOSO-PullSrv en twee gedeeltelijke configuraties die deze pull-server gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5284d-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="5284d-140">Zie [een pull-client instellen met behulp van configuratie namen](pullClientConfigNames.md)voor meer informatie over het configureren van de LCM met behulp van **ConfigurationNames**.</span><span class="sxs-lookup"><span data-stu-id="5284d-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="5284d-141">Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigID.md)voor meer informatie over het configureren van de LCM met behulp van **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="5284d-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="5284d-142">De LCM configureren voor pull-modus configuraties met configuratie namen</span><span class="sxs-lookup"><span data-stu-id="5284d-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="5284d-143">De LCM configureren voor pull-modus configuraties met behulp van ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="5284d-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="5284d-144">U kunt gedeeltelijke configuraties van meer dan één pull-server halen: u hoeft alleen elke pull-server te definiëren en vervolgens naar de juiste pull-server in elk **PartialConfiguration** -blok te verwijzen.</span><span class="sxs-lookup"><span data-stu-id="5284d-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="5284d-145">Nadat u de meta configuratie hebt gemaakt, moet u deze uitvoeren om een configuratie document (een MOF-bestand) te maken en vervolgens [set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) aanroepen om de LCM te configureren.</span><span class="sxs-lookup"><span data-stu-id="5284d-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="5284d-146">Naamgeving en plaatsen van de configuratie documenten op de pull-server (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="5284d-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="5284d-147">De gedeeltelijke configuratie documenten moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in het `web.config`-bestand voor de pull-server (meestal `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="5284d-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program
Files\WindowsPowerShell\DscService\Configuration`).</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="5284d-148">Naamgeving van configuratie documenten op de pull-server in Power shell 5,1</span><span class="sxs-lookup"><span data-stu-id="5284d-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="5284d-149">Als u slechts één gedeeltelijke configuratie van een afzonderlijke pull-server haalt, kan het configuratie document een wille keurige naam hebben.</span><span class="sxs-lookup"><span data-stu-id="5284d-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="5284d-150">Als u meer dan één gedeeltelijke configuratie haalt van een pull-server, kan het configuratie document een naam hebben van `<ConfigurationName>.mof`, waarbij *configuratiepad* de naam van de gedeeltelijke configuratie is, of `<ConfigurationName>.<NodeName>.mof`, waarbij *configuratiepad* de naam van de gedeeltelijke configuratie is en *knooppunt* naam het doel knooppunt is.</span><span class="sxs-lookup"><span data-stu-id="5284d-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where *ConfigurationName* is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where *ConfigurationName* is the name of the partial configuration, and *NodeName* is the name of the target node.</span></span> <span data-ttu-id="5284d-151">Hierdoor kunt u configuraties van Azure Automation DSC-pull-server ophalen.</span><span class="sxs-lookup"><span data-stu-id="5284d-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="5284d-152">Naamgeving van configuratie documenten op de pull-server in Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="5284d-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="5284d-153">De configuratie documenten moeten de volgende naam hebben: `ConfigurationName.mof`, waarbij *configuratiepad* de naam van de gedeeltelijke configuratie is.</span><span class="sxs-lookup"><span data-stu-id="5284d-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where *ConfigurationName* is the name of the partial configuration.</span></span> <span data-ttu-id="5284d-154">In ons voor beeld moeten de configuratie documenten de volgende naam hebben:</span><span class="sxs-lookup"><span data-stu-id="5284d-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="5284d-155">Naamgeving en plaatsen van de configuratie documenten op de pull-server (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="5284d-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="5284d-156">De gedeeltelijke configuratie documenten moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in het `web.config`-bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="5284d-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="5284d-157">De configuratie documenten moeten de volgende naam hebben: `<ConfigurationName>.<ConfigurationID>.mof`, waarbij _configuratiepad_ de naam is van de gedeeltelijke configuratie en _ConfigurationID_ is de configuratie-id die is gedefinieerd in de LCM op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5284d-157">The configuration documents must be named as follows: `<ConfigurationName>.<ConfigurationID>.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="5284d-158">In ons voor beeld moeten de configuratie documenten de volgende naam hebben:</span><span class="sxs-lookup"><span data-stu-id="5284d-158">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```

### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="5284d-159">Gedeeltelijke configuraties uitvoeren vanaf een pull-server</span><span class="sxs-lookup"><span data-stu-id="5284d-159">Running partial configurations from a pull server</span></span>

<span data-ttu-id="5284d-160">Nadat de LCM op het doel knooppunt is geconfigureerd en de configuratie documenten zijn gemaakt en op de juiste manier zijn benoemd op de pull-server, haalt het doel knooppunt de gedeeltelijke configuraties op, combineert ze en past de resulterende configuratie met regel matige tussen pozen toe zoals opgegeven door de eigenschap **RefreshFrequencyMins** van de LCM.</span><span class="sxs-lookup"><span data-stu-id="5284d-160">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="5284d-161">Als u het vernieuwen wilt forceren, kunt u de cmdlet [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) aanroepen om de configuraties op te halen en vervolgens `Start-DSCConfiguration –UseExisting` om ze toe te passen.</span><span class="sxs-lookup"><span data-stu-id="5284d-161">If you want to force a refresh, you can call the [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>

## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="5284d-162">Gedeeltelijke configuraties in gemengde push-en pull-modi</span><span class="sxs-lookup"><span data-stu-id="5284d-162">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="5284d-163">U kunt ook push-en pull-modi combi neren voor gedeeltelijke configuraties.</span><span class="sxs-lookup"><span data-stu-id="5284d-163">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="5284d-164">Dat wil zeggen dat u één gedeeltelijke configuratie kunt hebben die wordt opgehaald van een pull-server, terwijl een andere gedeeltelijke configuratie wordt gepusht.</span><span class="sxs-lookup"><span data-stu-id="5284d-164">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="5284d-165">Geef de vernieuwings modus voor elke gedeeltelijke configuratie op, zoals beschreven in de vorige secties.</span><span class="sxs-lookup"><span data-stu-id="5284d-165">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="5284d-166">De volgende meta configuratie bevat bijvoorbeeld hetzelfde voor beeld, met de `ServiceAccountConfig` gedeeltelijke configuratie in de pull-modus en de `SharePointConfig` gedeeltelijke configuratie in de push-modus.</span><span class="sxs-lookup"><span data-stu-id="5284d-166">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="5284d-167">Gemengde push-en pull-modi met ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="5284d-167">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="5284d-168">Gemengde push-en pull-modi met ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="5284d-168">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="5284d-169">Houd er rekening mee dat de **RefreshMode** die zijn opgegeven in het instellingen blok pull is, maar dat de **RefreshMode** voor de `SharePointConfig` gedeeltelijke configuratie ' push ' is.</span><span class="sxs-lookup"><span data-stu-id="5284d-169">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="5284d-170">Naam en zoek de MOF-bestanden van de configuratie zoals hierboven wordt beschreven voor de respectieve vernieuwings modi.</span><span class="sxs-lookup"><span data-stu-id="5284d-170">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span>
<span data-ttu-id="5284d-171">Roep `Publish-DSCConfiguration` aan om de `SharePointConfig` gedeeltelijke configuratie te publiceren en wacht totdat de `ServiceAccountConfig` configuratie wordt opgehaald van de pull-server of dwing een vernieuwing af door [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="5284d-171">Call `Publish-DSCConfiguration` to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="5284d-172">Voor beeld van een gedeeltelijke configuratie van ServiceAccountConfig</span><span class="sxs-lookup"><span data-stu-id="5284d-172">Example ServiceAccountConfig Partial Configuration</span></span>

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

## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="5284d-173">Voor beeld van een gedeeltelijke configuratie van SharePointConfig</span><span class="sxs-lookup"><span data-stu-id="5284d-173">Example SharePointConfig Partial Configuration</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5284d-174">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5284d-174">See Also</span></span>

[<span data-ttu-id="5284d-175">Windows Power shell desired state Configuration pull-servers</span><span class="sxs-lookup"><span data-stu-id="5284d-175">Windows PowerShell Desired State Configuration Pull Servers</span></span>](pullServer.md)

[<span data-ttu-id="5284d-176">Windows configureren van de lokale Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="5284d-176">Windows Configuring the Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
