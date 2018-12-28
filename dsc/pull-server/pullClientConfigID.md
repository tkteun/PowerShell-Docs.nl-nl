---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 5.0 en hoger
ms.openlocfilehash: 8d8cf478f9127e1b7005d1b9e832e84b11612c9c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404293"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="667a4-103">Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="667a4-103">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="667a4-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="667a4-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="667a4-105">De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="667a4-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="667a4-106">Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="667a4-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="667a4-107">Voordat u een pull-client instelt, moet u een pull-server instellen.</span><span class="sxs-lookup"><span data-stu-id="667a4-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="667a4-108">Al deze order niet vereist is, helpt bij het oplossen van problemen en kunt u ervoor zorgen dat de registratie geslaagd is.</span><span class="sxs-lookup"><span data-stu-id="667a4-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="667a4-109">Als u een pull-server instelt, kunt u de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="667a4-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="667a4-110">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="667a4-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="667a4-111">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="667a4-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="667a4-112">Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren.</span><span class="sxs-lookup"><span data-stu-id="667a4-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="667a4-113">De volgende secties laten zien hoe u een pull-client configureren met een SMB-share of een HTTP-DSC-Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="667a4-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="667a4-114">Wanneer van het knooppunt LCM vernieuwd, wordt het contact opnemen met de geconfigureerde locatie voor het downloaden van de toegewezen configuraties.</span><span class="sxs-lookup"><span data-stu-id="667a4-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="667a4-115">Als alle vereiste resources niet aanwezig zijn op het knooppunt, wordt deze ze automatisch downloaden van de geconfigureerde locatie.</span><span class="sxs-lookup"><span data-stu-id="667a4-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="667a4-116">Als het knooppunt is geconfigureerd met een [Report Server](reportServer.md), deze wordt vervolgens rapporteert de status van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="667a4-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="667a4-117">**Houd er rekening mee**: In dit onderwerp is van toepassing op PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="667a4-117">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="667a4-118">Zie voor meer informatie over het instellen van een pull-client in PowerShell 4.0 [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="667a4-118">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="667a4-119">De pull-client LCM configureren</span><span class="sxs-lookup"><span data-stu-id="667a4-119">Configure the pull client LCM</span></span>

<span data-ttu-id="667a4-120">Uitvoeren van een van de voorbeelden hieronder maakt u een nieuwe map voor uitvoer met de naam **PullClientConfigID** en er een metaconfiguration MOF-bestand geplaatst.</span><span class="sxs-lookup"><span data-stu-id="667a4-120">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="667a4-121">In dit geval het metaconfiguration MOF-bestand de naam `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="667a4-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="667a4-122">Aanroepen om toe te passen de configuratie, de **Set-DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguration MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="667a4-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="667a4-123">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="667a4-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="667a4-124">Configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="667a4-124">Configuration ID</span></span>

<span data-ttu-id="667a4-125">De voorbeelden hieronder wordt de **ConfigurationID** eigenschap van de LCM om een **Guid** die eerder is gemaakt voor dit doel.</span><span class="sxs-lookup"><span data-stu-id="667a4-125">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="667a4-126">De **ConfigurationID** is wat de LCM gebruikt om te vinden van de juiste configuratie op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="667a4-126">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="667a4-127">Het MOF-configuratiebestand op de pull-server moet de naam `ConfigurationID.mof`, waarbij *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM.</span><span class="sxs-lookup"><span data-stu-id="667a4-127">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="667a4-128">Zie voor meer informatie [configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="667a4-128">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="667a4-129">U kunt een willekeurige maken **Guid** met behulp van het voorbeeld hieronder of met behulp van de [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="667a4-129">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="667a4-130">Voor meer informatie over het gebruik van **GUID's** in uw omgeving, Zie [plannen voor GUID's](/powershell/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="667a4-130">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/dsc/secureserver#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="667a4-131">Instellen van een Pull-Client voor het downloaden van configuraties</span><span class="sxs-lookup"><span data-stu-id="667a4-131">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="667a4-132">Elke client moet worden geconfigureerd in **Pull** modus en de url van de pull-server waar de configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="667a4-132">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="667a4-133">Om dit te doen, moet u de lokale Configuration Manager (LCM) configureren met de benodigde informatie.</span><span class="sxs-lookup"><span data-stu-id="667a4-133">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="667a4-134">Als u wilt de LCM configureren, maakt u een speciaal soort configuratie, voorzien van de **DSCLocalConfigurationManager** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="667a4-134">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="667a4-135">Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="667a4-135">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="667a4-136">HTTP-DSC-Pull-Server</span><span class="sxs-lookup"><span data-stu-id="667a4-136">HTTP DSC Pull Server</span></span>

<span data-ttu-id="667a4-137">Het volgende script wordt de LCM geconfigureerd voor pull-configuraties van een server met de naam 'CONTOSO-PullSrv'.</span><span class="sxs-lookup"><span data-stu-id="667a4-137">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }
    }
}
PullClientConfigID
```

<span data-ttu-id="667a4-138">In het script de **ConfigurationRepositoryWeb** blok definieert de pull-server.</span><span class="sxs-lookup"><span data-stu-id="667a4-138">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="667a4-139">De **ServerUrl** geeft de url van de DSC-Pull</span><span class="sxs-lookup"><span data-stu-id="667a4-139">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="667a4-140">SMB-Share</span><span class="sxs-lookup"><span data-stu-id="667a4-140">SMB Share</span></span>

<span data-ttu-id="667a4-141">Het volgende script configureert u de LCM met pull-configuraties van de SMB-Share `\\SMBPullServer\Pull`.</span><span class="sxs-lookup"><span data-stu-id="667a4-141">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Pull'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="667a4-142">In het script de **ConfigurationRepositoryShare** blok definieert de pull-server, die in dit geval een SMB-share is.</span><span class="sxs-lookup"><span data-stu-id="667a4-142">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="667a4-143">Instellen van een Pull-Client voor het downloaden van Resources</span><span class="sxs-lookup"><span data-stu-id="667a4-143">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="667a4-144">Als u alleen opgeeft de **ConfigurationRepositoryWeb** of **ConfigurationRepositoryShare** blokkeren in uw configuratie LCM (zoals in de vorige voorbeelden), de pull-client-resources van hetzelfde wordt opgehaald locatie van het ophalen van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="667a4-144">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="667a4-145">U kunt ook afzonderlijke locaties voor bronnen opgeven.</span><span class="sxs-lookup"><span data-stu-id="667a4-145">You can also specify separate locations for resources.</span></span> <span data-ttu-id="667a4-146">Als u de Resourcelocatie van een als een afzonderlijke server, gebruikt de **ResourceRepositoryWeb** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="667a4-146">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="667a4-147">Als u de Resourcelocatie van een als een SMB-share, gebruikt de **ResourceRepositoryShare** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="667a4-147">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="667a4-148">U kunt combineren **ConfigurationRepositoryWeb** met **ResourceRepositoryShare** of **ConfigurationRepositoryShare** met **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="667a4-148">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb**.</span></span> <span data-ttu-id="667a4-149">Voorbeelden van deze worden hieronder niet weergegeven.</span><span class="sxs-lookup"><span data-stu-id="667a4-149">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="667a4-150">HTTP-DSC-Pull-Server</span><span class="sxs-lookup"><span data-stu-id="667a4-150">HTTP DSC Pull Server</span></span>

<span data-ttu-id="667a4-151">De volgende metaconfiguration configureert u een pull-client om de configuraties van **CONTOSO-PullSrv** en de daarbij behorende bronnen uit **CONTOSO-ResourceSrv**.</span><span class="sxs-lookup"><span data-stu-id="667a4-151">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="667a4-152">SMB-Share</span><span class="sxs-lookup"><span data-stu-id="667a4-152">SMB Share</span></span>

<span data-ttu-id="667a4-153">Het volgende voorbeeld ziet u een metaconfiguration die u een client naar pull-configuraties van de SMB-share stelt `\\SMBPullServer\Configurations`, en bronnen van de SMB-share `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="667a4-153">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryShare SMBPullServer
        {
            SourcePath = '\\SMBPullServer\Configurations'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="667a4-154">Automatisch downloaden van Resources in de Push-modus</span><span class="sxs-lookup"><span data-stu-id="667a4-154">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="667a4-155">Begin in PowerShell 5.0, uw pull-clients kunnen modules downloaden van een SMB-share, zelfs wanneer ze zijn geconfigureerd voor **Push** modus.</span><span class="sxs-lookup"><span data-stu-id="667a4-155">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="667a4-156">Dit is vooral nuttig in scenario's waar u niet wilt instellen van een Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="667a4-156">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="667a4-157">De **ResourceRepositoryShare** blok kan worden gebruikt zonder op te geven een **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="667a4-157">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare**.</span></span> <span data-ttu-id="667a4-158">Het volgende voorbeeld ziet u een metaconfiguration die u een client naar pull-bronnen van een SMB-Share stelt `\\SMBPullServer\Resources`.</span><span class="sxs-lookup"><span data-stu-id="667a4-158">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="667a4-159">Wanneer het knooppunt is **PUSHED** een configuratie worden automatisch gedownload die alle vereiste resources van de opgegeven share.</span><span class="sxs-lookup"><span data-stu-id="667a4-159">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Push'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
        }

        ResourceRepositoryShare SMBResourceServer
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigID
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="667a4-160">Instellen van een Pull-Client voor statusrapportage</span><span class="sxs-lookup"><span data-stu-id="667a4-160">Set up a Pull Client to report status</span></span>

<span data-ttu-id="667a4-161">Standaard worden knooppunten rapporten niet verzenden naar een geconfigureerde Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="667a4-161">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="667a4-162">U kunt een enkel pull-server gebruiken voor configuraties, resources en rapportage, maar u moet maken een **ReportRepositoryWeb** blokkeren voor het instellen van rapportage.</span><span class="sxs-lookup"><span data-stu-id="667a4-162">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="667a4-163">HTTP-DSC-Pull-Server</span><span class="sxs-lookup"><span data-stu-id="667a4-163">HTTP DSC Pull Server</span></span>

<span data-ttu-id="667a4-164">Het volgende voorbeeld ziet een metaconfiguration instellen van een client pull-configuraties, resources en verzenden gegevens rapporteren aan een enkele pull-server.</span><span class="sxs-lookup"><span data-stu-id="667a4-164">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

<span data-ttu-id="667a4-165">Als u een rapportserver, gebruikt u een **ReportRepositoryWeb** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="667a4-165">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="667a4-166">Een rapportserver mag niet een SMB-server.</span><span class="sxs-lookup"><span data-stu-id="667a4-166">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="667a4-167">De volgende metaconfiguration configureert u een pull-client om de configuraties van **CONTOSO-PullSrv** en de daarbij behorende bronnen uit **CONTOSO-ResourceSrv**, en voor het verzenden van rapporten naar  **CONTOSO-ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="667a4-167">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            ConfigurationID = '1d545e3b-60c3-47a0-bf65-5afc05182fd0'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'

        }

        ResourceRepositoryWeb CONTOSO-ResourceSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }

        ReportServerWeb CONTOSO-ReportSrv
        {
            ServerURL = 'https://CONTOSO-REsourceSrv:8080/PSDSCPullServer.svc'
        }
    }
}
PullClientConfigID
```

### <a name="smb-share"></a><span data-ttu-id="667a4-168">SMB-Share</span><span class="sxs-lookup"><span data-stu-id="667a4-168">SMB Share</span></span>

<span data-ttu-id="667a4-169">Een rapportserver mag niet een SMB-share.</span><span class="sxs-lookup"><span data-stu-id="667a4-169">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="667a4-170">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="667a4-170">Next Steps</span></span>

<span data-ttu-id="667a4-171">Nadat de pull-client is geconfigureerd, kunt u de volgende handleidingen gebruiken om uit te voeren van de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="667a4-171">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="667a4-172">Configuraties publiceren naar een Pull-Server (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="667a4-172">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="667a4-173">Pakket- en Resources uploaden naar een Pull-Server (v4)</span><span class="sxs-lookup"><span data-stu-id="667a4-173">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="667a4-174">Zie ook</span><span class="sxs-lookup"><span data-stu-id="667a4-174">See Also</span></span>

* [<span data-ttu-id="667a4-175">Instellen van een pull-client met configuratienamen</span><span class="sxs-lookup"><span data-stu-id="667a4-175">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
