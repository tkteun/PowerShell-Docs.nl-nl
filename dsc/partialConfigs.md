---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Gedeeltelijke PowerShell Desired State Configuration-configuraties
ms.openlocfilehash: 2c5f29ee2940f4b7955219e97275ffa2695f9dee
ms.sourcegitcommit: aa6890031dad3f2981b24c58893d134bdf4e8655
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/08/2017
---
# <a name="powershell-desired-state-configuration-partial-configurations"></a><span data-ttu-id="e3a00-103">Gedeeltelijke PowerShell Desired State Configuration-configuraties</span><span class="sxs-lookup"><span data-stu-id="e3a00-103">PowerShell Desired State Configuration partial configurations</span></span>

><span data-ttu-id="e3a00-104">Van toepassing op: Windows PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="e3a00-104">Applies To: Windows PowerShell 5.0 and later.</span></span>

<span data-ttu-id="e3a00-105">In PowerShell 5.0 kan Desired State Configuration (DSC) configuraties moeten worden geleverd in fragmenten en uit meerdere bronnen.</span><span class="sxs-lookup"><span data-stu-id="e3a00-105">In PowerShell 5.0, Desired State Configuration (DSC) allows configurations to be delivered in fragments and from multiple sources.</span></span> <span data-ttu-id="e3a00-106">De lokale Configuration Manager (LCM) in het doelknooppunt plaatst de fragmenten samen voordat u deze als een configuratie voor één toepast.</span><span class="sxs-lookup"><span data-stu-id="e3a00-106">The Local Configuration Manager (LCM) on the target node puts the fragments together before applying them as a single configuration.</span></span> <span data-ttu-id="e3a00-107">Deze mogelijkheid ondersteunt het beheer van de configuratie tussen teams of personen delen.</span><span class="sxs-lookup"><span data-stu-id="e3a00-107">This capability allows sharing control of configuration between teams or individuals.</span></span> <span data-ttu-id="e3a00-108">Bijvoorbeeld, als twee of meer teams van ontwikkelaars aan een service samenwerken, ze mogelijk elk wilt configuraties voor het beheren van hun deel van de service maken.</span><span class="sxs-lookup"><span data-stu-id="e3a00-108">For example, if two or more teams of developers are collaborating on a service, they might each want to create configurations to manage their part of the service.</span></span> <span data-ttu-id="e3a00-109">Elk van deze configuraties kan worden opgehaald uit verschillende pull-servers en ze in verschillende stadia van de ontwikkeling van kunnen worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="e3a00-109">Each of these configurations could be pulled from different pull servers, and they could be added at different stages of development.</span></span> <span data-ttu-id="e3a00-110">Gedeeltelijke configuraties kunnen ook verschillende personen of teams verschillende aspecten van de knooppunten configureren zonder dat voor het coördineren van het bewerken van een configuratie voor één document te bepalen.</span><span class="sxs-lookup"><span data-stu-id="e3a00-110">Partial configurations also allow different individuals or teams to control different aspects of configuring nodes without having to coordinate the editing of a single configuration document.</span></span> <span data-ttu-id="e3a00-111">Een team worden verantwoordelijk voor het implementeren van een virtuele machine en het besturingssysteem, terwijl een ander team andere toepassingen en services op deze virtuele machine kunt implementeren.</span><span class="sxs-lookup"><span data-stu-id="e3a00-111">For example, one team might be responsible for deploying a VM and operating system, while another team might deploy other applications and services on that VM.</span></span> <span data-ttu-id="e3a00-112">Met gedeeltelijke configuraties kunt elk team maken van een eigen configuratie, zonder een van beide wordt onnodig ingewikkeld.</span><span class="sxs-lookup"><span data-stu-id="e3a00-112">With partial configurations, each team can create its own configuration, without either of them being unnecessarily complicated.</span></span>

<span data-ttu-id="e3a00-113">U kunt gedeeltelijke configuraties in push-modus, pull-modus of een combinatie van beide gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e3a00-113">You can use partial configurations in push mode, pull mode, or a combination of the two.</span></span>

## <a name="partial-configurations-in-push-mode"></a><span data-ttu-id="e3a00-114">Gedeeltelijke configuraties in de modus push</span><span class="sxs-lookup"><span data-stu-id="e3a00-114">Partial configurations in push mode</span></span>
<span data-ttu-id="e3a00-115">Voor het gebruik van gedeeltelijke configuraties in de modus push, configureert u de LCM op het doelknooppunt voor het ontvangen van de gedeeltelijk configuraties.</span><span class="sxs-lookup"><span data-stu-id="e3a00-115">To use partial configurations in push mode, you configure the LCM on the target node to receive the partial configurations.</span></span> <span data-ttu-id="e3a00-116">Elke gedeeltelijke configuratie moet worden geactiveerd met de doel-met de cmdlet Publish-DSCConfiguration.</span><span class="sxs-lookup"><span data-stu-id="e3a00-116">Each partial configuration must be pushed to the target by using the Publish-DSCConfiguration cmdlet.</span></span> <span data-ttu-id="e3a00-117">Het doelknooppunt vervolgens combineert de gedeeltelijke configuratie in een configuratie voor één, en u kunt de configuratie toepassen door het aanroepen van de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e3a00-117">The target node then combines the partial configuration into a single configuration, and you can apply the configuration by calling the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span>

### <a name="configuring-the-lcm-for-push-mode-partial-configurations"></a><span data-ttu-id="e3a00-118">De LCM voor push-modus gedeeltelijke configuraties configureren</span><span class="sxs-lookup"><span data-stu-id="e3a00-118">Configuring the LCM for push-mode partial configurations</span></span>
<span data-ttu-id="e3a00-119">Voor het configureren van de LCM voor gedeeltelijke configuraties in push-modus, die u maakt een **DSCLocalConfigurationManager** configuratie met een **PartialConfiguration** blok voor elke gedeeltelijke configuratie.</span><span class="sxs-lookup"><span data-stu-id="e3a00-119">To configure the LCM for partial configurations in push mode, you create a **DSCLocalConfigurationManager** configuration with one **PartialConfiguration** block for each partial configuration.</span></span> <span data-ttu-id="e3a00-120">Zie voor meer informatie over het configureren van de LCM [Windows configureren van de lokale Configuration Manager](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span><span class="sxs-lookup"><span data-stu-id="e3a00-120">For more information about configuring the LCM, see [Windows Configuring the Local Configuration Manager](https://technet.microsoft.com/en-us/library/mt421188.aspx).</span></span> <span data-ttu-id="e3a00-121">Het volgende voorbeeld ziet u de configuratie van een LCM die twee gedeeltelijke configuraties verwacht: één waarmee het besturingssysteem wordt geïmplementeerd en één die wordt geïmplementeerd en SharePoint configureert.</span><span class="sxs-lookup"><span data-stu-id="e3a00-121">The following example shows an LCM configuration that expects two partial configurations—one that deploys the OS, and one that deploys and configures SharePoint.</span></span>

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

<span data-ttu-id="e3a00-122">De **RefreshMode** voor elke gedeeltelijke configuratie is ingesteld op 'Push'.</span><span class="sxs-lookup"><span data-stu-id="e3a00-122">The **RefreshMode** for each partial configuration is set to "Push".</span></span> <span data-ttu-id="e3a00-123">De namen van de **PartialConfiguration** blokken (in dit geval 'ServiceAccountConfig' en "SharePointConfig") moeten overeenkomen met precies de namen van de configuraties die naar het doelknooppunt worden gepusht.</span><span class="sxs-lookup"><span data-stu-id="e3a00-123">The names of the **PartialConfiguration** blocks (in this case, "ServiceAccountConfig" and "SharePointConfig") must match exactly the names of the configurations that are pushed to the target node.</span></span>

><span data-ttu-id="e3a00-124">**Opmerking:** de benoemde van elke **PartialConfiguration** blok moet overeenkomen met de werkelijke naam van de configuratie zoals deze is opgegeven in het configuratiescript, niet de naam van het MOF-bestand dat moet de naam van de doelknooppunt of `localhost`.</span><span class="sxs-lookup"><span data-stu-id="e3a00-124">**Note:** The named of each **PartialConfiguration** block must match the actual name of the configuration as it is specified in the configuration script, not the name of the MOF file, which should be either the name of the target node or `localhost`.</span></span>

### <a name="publishing-and-starting-push-mode-partial-configurations"></a><span data-ttu-id="e3a00-125">Publiceren en starten van de push-modus gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="e3a00-125">Publishing and starting push-mode partial configurations</span></span>

<span data-ttu-id="e3a00-126">Vervolgens aanroepen [publiceren DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) voor elke configuratie de configuratiedocumenten als de mappen die wordt doorgegeven bevatten de **pad** parameters.</span><span class="sxs-lookup"><span data-stu-id="e3a00-126">You then call [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) for each configuration, passing the folders that contain the configuration documents as the **Path** parameters.</span></span> <span data-ttu-id="e3a00-127">`Publish-DSCConfiguration`de configuratie MOF-bestanden naar de doelknooppunten plaatst.</span><span class="sxs-lookup"><span data-stu-id="e3a00-127">`Publish-DSCConfiguration`places the configuration MOF files to the target nodes.</span></span> <span data-ttu-id="e3a00-128">Na het publiceren van beide configuraties die u kunt aanroepen `Start-DSCConfiguration –UseExisting` in het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="e3a00-128">After publishing both configurations, you can call `Start-DSCConfiguration –UseExisting` on the target node.</span></span>

<span data-ttu-id="e3a00-129">Bijvoorbeeld, als u hebt de volgende configuratie MOF-documenten op het knooppunt authoring gecompileerd:</span><span class="sxs-lookup"><span data-stu-id="e3a00-129">For example, if you have compiled the following configuration MOF documents on the authoring node:</span></span>

```powershell
PS C:\PartialConfigTest> Get-ChildItem -Recurse


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

<span data-ttu-id="e3a00-130">U wilt publiceren en de configuraties als volgt uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="e3a00-130">You would publish and run the configurations as follows:</span></span>

```powershell
PS C:\PartialConfigTest> Publish-DscConfiguration .\ServiceAccountConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Publish-DscConfiguration .\SharePointConfig -ComputerName 'TestVM'
PS C:\PartialConfigTest> Start-DscConfiguration -UseExisting -ComputerName 'TestVM'

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command                  
--     ----            -------------   -----         -----------     --------             -------                  
17     Job17           Configuratio... Running       True            TestVM            Start-DscConfiguration...
```

><span data-ttu-id="e3a00-131">**Opmerking:** de gebruiker die de [publiceren DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet moet beheerdersbevoegdheden hebben op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="e3a00-131">**Note:** The user running the [Publish-DSCConfiguration](https://msdn.microsoft.com/en-us/powershell/reference/5.1/psdesiredstateconfiguration/publish-dscconfiguration) cmdlet must have administrator privileges on the target node.</span></span>

## <a name="partial-configurations-in-pull-mode"></a><span data-ttu-id="e3a00-132">Gedeeltelijke configuraties in pull-modus</span><span class="sxs-lookup"><span data-stu-id="e3a00-132">Partial configurations in pull mode</span></span>

<span data-ttu-id="e3a00-133">Gedeeltelijke configuraties kunnen worden opgehaald uit een of meer pull-servers (Zie voor meer informatie over pull-servers [Windows PowerShell Desired status Pull configuratieservers](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="e3a00-133">Partial configurations can be pulled from one or more pull servers (for more information about pull servers, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="e3a00-134">Om dit te doen, moet u de LCM configureren op het doelknooppunt voor de gedeeltelijke configuraties ophalen, naam en zoek de configuratiedocumenten correct op de pull-servers.</span><span class="sxs-lookup"><span data-stu-id="e3a00-134">To do this, you have to configure the LCM on the target node to pull the partial configurations, and name and locate the configuration documents properly on the pull servers.</span></span>

### <a name="configuring-the-lcm-for-pull-node-configurations"></a><span data-ttu-id="e3a00-135">De LCM voor pull-knooppuntconfiguraties configureren</span><span class="sxs-lookup"><span data-stu-id="e3a00-135">Configuring the LCM for pull node configurations</span></span>

<span data-ttu-id="e3a00-136">Voor het configureren van de LCM om op te halen van gedeeltelijke configuraties van een pull-server, u de pull-server definiëren in hetzij een **ConfigurationRepositoryWeb** (voor een HTTP-pull-server) of **ConfigurationRepositoryShare** () voor een SMB-pull-server) blokkeren.</span><span class="sxs-lookup"><span data-stu-id="e3a00-136">To configure the LCM to pull partial configurations from a pull server, you define the pull server in either a **ConfigurationRepositoryWeb** (for an HTTP pull server) or **ConfigurationRepositoryShare** (for an SMB pull server) block.</span></span> <span data-ttu-id="e3a00-137">Vervolgens maakt u **PartialConfiguration** blokken die naar de pull-server met behulp van verwijzen de **ConfigurationSource** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="e3a00-137">You then create **PartialConfiguration** blocks that refer to the pull server by using the **ConfigurationSource** property.</span></span> <span data-ttu-id="e3a00-138">U moet ook maken een **instellingen** blok om op te geven dat de LCM pull-modus gebruikt en op te geven de **ConfigurationNames** of **ConfigurationID** die de pull-server en doel knooppunt gebruiken om te bepalen van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="e3a00-138">You also need to create a **Settings** block to specify that the LCM uses pull mode, and to specify the **ConfigurationNames** or **ConfigurationID** that the pull server and target node use to identify the configurations.</span></span> <span data-ttu-id="e3a00-139">De volgende meta-configuratie definieert een HTTP-pull-server met de naam CONTOSO PullSrv en twee gedeeltelijke configuraties die gebruikmaken van die pull-server.</span><span class="sxs-lookup"><span data-stu-id="e3a00-139">The following meta-configuration defines an HTTP pull server named CONTOSO-PullSrv and two partial configurations that use that pull server.</span></span>

<span data-ttu-id="e3a00-140">Voor meer informatie over het configureren van het gebruik van LCM **ConfigurationNames**, Zie [instellen van een pull-client met behulp van configuratienamen](pullClientConfigNames.md).</span><span class="sxs-lookup"><span data-stu-id="e3a00-140">For more information about configuring the LCM using **ConfigurationNames**, see [Setting up a pull client using configuration names](pullClientConfigNames.md).</span></span> <span data-ttu-id="e3a00-141">Voor informatie over het configureren van het gebruik van LCM **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="e3a00-141">For information about configuring the LCM using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configuration-names"></a><span data-ttu-id="e3a00-142">De LCM voor pull-modus configuraties met configuratienamen configureren</span><span class="sxs-lookup"><span data-stu-id="e3a00-142">Configuring the LCM for pull mode configurations using configuration names</span></span>

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

#### <a name="configuring-the-lcm-for-pull-mode-configurations-using-configurationid"></a><span data-ttu-id="e3a00-143">De LCM voor pull-modus configuraties met ConfigurationID configureren</span><span class="sxs-lookup"><span data-stu-id="e3a00-143">Configuring the LCM for pull mode configurations using ConfigurationID</span></span>

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

<span data-ttu-id="e3a00-144">U kunt gedeeltelijke configuraties uit meer dan één pull-server ophalen, moet u alleen voor het definiëren van elk pull-server en vervolgens verwijzen naar de juiste pull-server in elk **PartialConfiguration** blok.</span><span class="sxs-lookup"><span data-stu-id="e3a00-144">You can pull partial configurations from more than one pull server—you would just need to define each pull server, and then refer to the appropriate pull server in each **PartialConfiguration** block.</span></span>

<span data-ttu-id="e3a00-145">Nadat de meta-configuratie is gemaakt, moet u het voor het maken van een configuratie-document (een MOF-bestand) en vervolgens aanroepen uitvoeren [Set DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) de LCM configureren.</span><span class="sxs-lookup"><span data-stu-id="e3a00-145">After creating the meta-configuration, you must run it to create a configuration document (a MOF file), and then call [Set-DscLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621(v=wps.630).aspx) to configure the LCM.</span></span>

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationnames"></a><span data-ttu-id="e3a00-146">Naamgeving en de configuratiedocumenten te plaatsen op de pull-server (ConfigurationNames)</span><span class="sxs-lookup"><span data-stu-id="e3a00-146">Naming and placing the configuration documents on the pull server (ConfigurationNames)</span></span>

<span data-ttu-id="e3a00-147">De configuratiedocumenten gedeeltelijke moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="e3a00-147">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> 

#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-51"></a><span data-ttu-id="e3a00-148">Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e3a00-148">Naming configuration documents on the pull server in PowerShell 5.1</span></span>

<span data-ttu-id="e3a00-149">Als u van slechts één gedeeltelijke configuratie van een afzonderlijke pull-server binnenhalen, kan het configuratiebestand voor elke naam hebben.</span><span class="sxs-lookup"><span data-stu-id="e3a00-149">If you are pulling only one partial configuration from an individual pull server, the configuration document can have any name.</span></span> <span data-ttu-id="e3a00-150">Als u van meer dan één gedeeltelijke configuratie van een pull-server binnenhalen, de configuratie-document kan worden benoemd ofwel `<ConfigurationName>.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijke of `<ConfigurationName>.<NodeName>.mof`, waarbij  _ConfigurationName_ is de naam van de configuratie van de gedeeltelijk en _NodeName_ is de naam van het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="e3a00-150">If you are pulling more than one partial configuration from a pull server, the configuration document can be named either `<ConfigurationName>.mof`, where _ConfigurationName_ is the name of the partial configuration, or `<ConfigurationName>.<NodeName>.mof`, where  _ConfigurationName_ is the name of the partial configuration, and _NodeName_ is the name of the target node.</span></span> <span data-ttu-id="e3a00-151">Hiermee kunt u pull-configuraties van Azure Automation DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="e3a00-151">This allows you to pull configurations from Azure Automation DSC pull server.</span></span>


#### <a name="naming-configuration-documents-on-the-pull-server-in-powershell-50"></a><span data-ttu-id="e3a00-152">Naamgeving van configuratiedocumenten op de pull-server in PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e3a00-152">Naming configuration documents on the pull server in PowerShell 5.0</span></span>

<span data-ttu-id="e3a00-153">De configuratiedocumenten moeten als volgt de naam: `ConfigurationName.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijk.</span><span class="sxs-lookup"><span data-stu-id="e3a00-153">The configuration documents must be named as follows: `ConfigurationName.mof`, where _ConfigurationName_ is the name of the partial configuration.</span></span> <span data-ttu-id="e3a00-154">De configuratiedocumenten moeten als volgt worden genoemd in ons voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e3a00-154">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.mof
ServiceAccountConfig.mof.checksum
SharePointConfig.mof
SharePointConfig.mof.checksum
```

### <a name="naming-and-placing-the-configuration-documents-on-the-pull-server-configurationid"></a><span data-ttu-id="e3a00-155">Naamgeving en de configuratiedocumenten te plaatsen op de pull-server (ConfigurationID)</span><span class="sxs-lookup"><span data-stu-id="e3a00-155">Naming and placing the configuration documents on the pull server (ConfigurationID)</span></span>

<span data-ttu-id="e3a00-156">De configuratiedocumenten gedeeltelijke moeten worden geplaatst in de map die is opgegeven als de **ConfigurationPath** in de `web.config` -bestand voor de pull-server (meestal `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span><span class="sxs-lookup"><span data-stu-id="e3a00-156">The partial configuration documents must be placed in the folder specified as the **ConfigurationPath** in the `web.config` file for the pull server (typically `C:\Program Files\WindowsPowerShell\DscService\Configuration`).</span></span> <span data-ttu-id="e3a00-157">De configuratiedocumenten moeten als volgt de naam: _ConfigurationName_.</span><span class="sxs-lookup"><span data-stu-id="e3a00-157">The configuration documents must be named as follows: _ConfigurationName_.</span></span> <span data-ttu-id="e3a00-158">_ConfigurationID_`.mof`, waarbij _ConfigurationName_ is de naam van de configuratie van de gedeeltelijk en _ConfigurationID_ wordt de configuratie-ID gedefinieerd in de LCM op de doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="e3a00-158">_ConfigurationID_`.mof`, where _ConfigurationName_ is the name of the partial configuration and _ConfigurationID_ is the configuration ID defined in the LCM on the target node.</span></span> <span data-ttu-id="e3a00-159">De configuratiedocumenten moeten als volgt worden genoemd in ons voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e3a00-159">For our example, the configuration documents should be named as follows:</span></span>

```
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
ServiceAccountConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof
SharePointConfig.1d545e3b-60c3-47a0-bf65-5afc05182fd0.mof.checksum
```


### <a name="running-partial-configurations-from-a-pull-server"></a><span data-ttu-id="e3a00-160">Gedeeltelijke configuraties uitvoert vanuit een pull-server</span><span class="sxs-lookup"><span data-stu-id="e3a00-160">Running partial configurations from a pull server</span></span>

<span data-ttu-id="e3a00-161">Nadat de LCM in het doelknooppunt is geconfigureerd en de configuratie van documenten hebt gemaakt en correct met de naam op de pull-server, het doelknooppunt haalt binnen de gedeeltelijke configuraties, ze combineren en de resulterende configuratie tegen de gebruikelijke toepassen intervallen zoals opgegeven door de **RefreshFrequencyMins** eigenschap van de LCM.</span><span class="sxs-lookup"><span data-stu-id="e3a00-161">After the LCM on the target node has been configured, and the configuration documents have been created and properly named on the pull server, the target node will pull the partial configurations, combine them, and apply the resulting configuration at regular intervals as specified by the **RefreshFrequencyMins** property of the LCM.</span></span> <span data-ttu-id="e3a00-162">Als u vernieuwen wilt, belt u het [Update DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet voor het ophalen van de configuraties en vervolgens `Start-DSCConfiguration –UseExisting` om toe te passen.</span><span class="sxs-lookup"><span data-stu-id="e3a00-162">If you want to force a refresh, you can call the [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541.aspx) cmdlet, to pull the configurations, and then `Start-DSCConfiguration –UseExisting` to apply them.</span></span>


## <a name="partial-configurations-in-mixed-push-and-pull-modes"></a><span data-ttu-id="e3a00-163">Gedeeltelijke configuraties in gemengde push als pull-modi</span><span class="sxs-lookup"><span data-stu-id="e3a00-163">Partial configurations in mixed push and pull modes</span></span>

<span data-ttu-id="e3a00-164">U kunt ook push mix en pull-modi voor gedeeltelijke configuraties.</span><span class="sxs-lookup"><span data-stu-id="e3a00-164">You can also mix push and pull modes for partial configurations.</span></span> <span data-ttu-id="e3a00-165">U kunt één gedeeltelijke configuratie die is opgehaald uit een pull-server, terwijl een andere gedeeltelijke configuratie wordt doorgeschoven, dat wil zeggen, kunnen hebben.</span><span class="sxs-lookup"><span data-stu-id="e3a00-165">That is, you could have one partial configuration that is pulled from a pull server, while another partial configuration is pushed.</span></span> <span data-ttu-id="e3a00-166">Geef de vernieuwingsmodus voor elke gedeeltelijke configuratie zoals beschreven in de vorige secties.</span><span class="sxs-lookup"><span data-stu-id="e3a00-166">Specify the refresh mode for each partial configuration as described in the previous sections.</span></span> <span data-ttu-id="e3a00-167">Bijvoorbeeld de volgende meta-configuratie wordt beschreven in het hetzelfde voorbeeld door de `ServiceAccountConfig` gedeeltelijke configuratie in pull-modus en de `SharePointConfig` gedeeltelijke configuratie in de modus push.</span><span class="sxs-lookup"><span data-stu-id="e3a00-167">For example, the following meta-configuration describes the same example, with the `ServiceAccountConfig` partial configuration in pull mode and the `SharePointConfig` partial configuration in push mode.</span></span>

### <a name="mixed-push-and-pull-modes-using-configurationnames"></a><span data-ttu-id="e3a00-168">Gemengde push als pull-modi met ConfigurationNames</span><span class="sxs-lookup"><span data-stu-id="e3a00-168">Mixed push and pull modes using ConfigurationNames</span></span>

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

### <a name="mixed-push-and-pull-modes-using-configurationid"></a><span data-ttu-id="e3a00-169">Gemengde push als pull-modi met ConfigurationID</span><span class="sxs-lookup"><span data-stu-id="e3a00-169">Mixed push and pull modes using ConfigurationID</span></span>

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

<span data-ttu-id="e3a00-170">Houd er rekening mee dat de **RefreshMode** opgegeven in het instellingenblok is 'Pull', maar de **RefreshMode** voor de `SharePointConfig` gedeeltelijke configuratie is 'Push'.</span><span class="sxs-lookup"><span data-stu-id="e3a00-170">Note that the **RefreshMode** specified in the Settings block is "Pull", but the **RefreshMode** for the `SharePointConfig` partial configuration is "Push".</span></span>

<span data-ttu-id="e3a00-171">Naam en de configuratiebestanden van de MOF vinden, zoals hierboven beschreven voor de modi van hun respectieve vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="e3a00-171">Name and locate the configuration MOF files as described above for their respective refresh modes.</span></span> <span data-ttu-id="e3a00-172">Aanroepen **publiceren DSCConfiguration** voor het publiceren van de `SharePointConfig` gedeeltelijke configuratie vallen of wacht u totdat de `ServiceAccountConfig` configuratie die moet worden opgehaald uit de pull-server of een vernieuwing forceren door het aanroepen van [ Update DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span><span class="sxs-lookup"><span data-stu-id="e3a00-172">Call **Publish-DSCConfiguration** to publish the `SharePointConfig` partial configuration, and either wait for the `ServiceAccountConfig` configuration to be pulled from the pull server, or force a refresh by calling [Update-DscConfiguration](https://technet.microsoft.com/en-us/library/mt143541(v=wps.630).aspx).</span></span>

## <a name="example-serviceaccountconfig-partial-configuration"></a><span data-ttu-id="e3a00-173">Voorbeeld ServiceAccountConfig gedeeltelijk configuratie</span><span class="sxs-lookup"><span data-stu-id="e3a00-173">Example ServiceAccountConfig Partial Configuration</span></span>

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
## <a name="example-sharepointconfig-partial-configuration"></a><span data-ttu-id="e3a00-174">Voorbeeld SharePointConfig gedeeltelijk configuratie</span><span class="sxs-lookup"><span data-stu-id="e3a00-174">Example SharePointConfig Partial Configuration</span></span>
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
##<a name="see-also"></a><span data-ttu-id="e3a00-175">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e3a00-175">See Also</span></span> 

<span data-ttu-id="e3a00-176">**Concepten**
[Windows PowerShell Desired State Configuration Pull-Servers](pullServer.md)</span><span class="sxs-lookup"><span data-stu-id="e3a00-176">**Concepts**
[Windows PowerShell Desired State Configuration Pull Servers](pullServer.md)</span></span> 

[<span data-ttu-id="e3a00-177">Windows configureren van de lokale Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="e3a00-177">Windows Configuring the Local Configuration Manager</span></span>](https://technet.microsoft.com/en-us/library/mt421188.aspx) 

