---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Een pull-client instellen met configuratie-Id's in Power shell 5,0 en hoger
description: In dit artikel wordt uitgelegd hoe u een pull-client instelt met configuratie-Id's in Power shell 5,0 en hoger
ms.openlocfilehash: 601858c08ce9a893a8941823d27fef3a60882b48
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664317"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-50-and-later"></a><span data-ttu-id="b1895-104">Een pull-client instellen met configuratie-Id's in Power shell 5,0 en hoger</span><span class="sxs-lookup"><span data-stu-id="b1895-104">Set up a Pull Client using Configuration IDs in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="b1895-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="b1895-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1895-106">De pull-server (Windows *-functie DSC-service* ) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="b1895-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b1895-107">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="b1895-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b1895-108">Voordat u een pull-client instelt, moet u een pull-server instellen.</span><span class="sxs-lookup"><span data-stu-id="b1895-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="b1895-109">Deze volg orde is niet vereist, maar helpt bij het oplossen van problemen en helpt u ervoor te zorgen dat de registratie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="b1895-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="b1895-110">U kunt de volgende hand leidingen gebruiken om een pull-server in te stellen:</span><span class="sxs-lookup"><span data-stu-id="b1895-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="b1895-111">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="b1895-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b1895-112">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="b1895-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b1895-113">Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan.</span><span class="sxs-lookup"><span data-stu-id="b1895-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b1895-114">In de volgende secties ziet u hoe u een pull-client kunt configureren met een SMB-share of een HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="b1895-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="b1895-115">Wanneer de LCM van het knoop punt wordt vernieuwd, neemt het contact op met de geconfigureerde locatie voor het downloaden van toegewezen configuraties.</span><span class="sxs-lookup"><span data-stu-id="b1895-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="b1895-116">Als er vereiste bronnen niet aanwezig zijn op het knoop punt, worden deze automatisch gedownload vanaf de geconfigureerde locatie.</span><span class="sxs-lookup"><span data-stu-id="b1895-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="b1895-117">Als het knoop punt is geconfigureerd met een [rapport server](reportServer.md), wordt de status van de bewerking gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="b1895-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="b1895-118">Dit onderwerp is van toepassing op Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="b1895-118">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="b1895-119">Zie [een pull-client instellen met configuratie-ID in Power shell 4,0](pullClientConfigID4.md) voor informatie over het instellen van een pull-client in power Shell 4,0</span><span class="sxs-lookup"><span data-stu-id="b1895-119">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="b1895-120">De pull-client LCM configureren</span><span class="sxs-lookup"><span data-stu-id="b1895-120">Configure the pull client LCM</span></span>

<span data-ttu-id="b1895-121">Als u een van de onderstaande voor beelden uitvoert, maakt u een nieuwe uitvoermap met de naam **PullClientConfigID** en plaatst u daar een MOF-bestand met de meta configuratie.</span><span class="sxs-lookup"><span data-stu-id="b1895-121">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="b1895-122">In dit geval wordt het MOF-bestand van de meta configuratie aangeduid met de naam `localhost.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="b1895-122">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="b1895-123">Als u de configuratie wilt Toep assen, roept u de cmdlet **set-DscLocalConfigurationManager** aan, waarbij het **pad** is ingesteld op de locatie van het MOF-bestand met de meta configuratie.</span><span class="sxs-lookup"><span data-stu-id="b1895-123">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="b1895-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b1895-124">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="b1895-125">Configuratie-id</span><span class="sxs-lookup"><span data-stu-id="b1895-125">Configuration ID</span></span>

<span data-ttu-id="b1895-126">In de onderstaande voor beelden wordt de eigenschap **ConfigurationID** van de LCM ingesteld op een **GUID** die eerder is gemaakt voor dit doel.</span><span class="sxs-lookup"><span data-stu-id="b1895-126">The examples below sets the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="b1895-127">De **ConfigurationID** is wat de LCM gebruikt om de juiste configuratie op de pull-server te vinden.</span><span class="sxs-lookup"><span data-stu-id="b1895-127">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="b1895-128">Het MOF-configuratie bestand op de pull-server moet een naam `ConfigurationID.mof` hebben, waarbij *ConfigurationID* de waarde is van de eigenschap **ConfigurationID** van de LCM van het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="b1895-128">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="b1895-129">Zie [configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b1895-129">For more information see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="b1895-130">U kunt een wille keurige **GUID** maken met behulp van het voor beeld hieronder of met de cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .</span><span class="sxs-lookup"><span data-stu-id="b1895-130">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="b1895-131">Zie voor meer informatie over het gebruik van **guid's** in uw omgeving [plan for guid's](secureserver.md#guids).</span><span class="sxs-lookup"><span data-stu-id="b1895-131">For more information about using **Guids** in your environment, see [Plan for Guids](secureserver.md#guids).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="b1895-132">Een pull-client instellen om configuraties te downloaden</span><span class="sxs-lookup"><span data-stu-id="b1895-132">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="b1895-133">Elke client moet worden geconfigureerd in de **pull** -modus en krijgt de URL van de pull-server waar de configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b1895-133">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="b1895-134">Hiervoor moet u de lokale Configuration Manager (LCM) configureren met de benodigde gegevens.</span><span class="sxs-lookup"><span data-stu-id="b1895-134">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="b1895-135">Als u de LCM wilt configureren, maakt u een speciaal type configuratie, gedecoreerd met het kenmerk **DSCLocalConfigurationManager** .</span><span class="sxs-lookup"><span data-stu-id="b1895-135">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="b1895-136">Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)(Engelstalig) voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="b1895-136">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="b1895-137">HTTP DSC-pull-server</span><span class="sxs-lookup"><span data-stu-id="b1895-137">HTTP DSC Pull Server</span></span>

<span data-ttu-id="b1895-138">Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een server met de naam ' CONTOSO-PullSrv '.</span><span class="sxs-lookup"><span data-stu-id="b1895-138">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="b1895-139">In het script definieert de pull-server in het **ConfigurationRepositoryWeb** -blok.</span><span class="sxs-lookup"><span data-stu-id="b1895-139">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="b1895-140">De **ServerUrl** Hiermee wordt de URL van de DSC-pull opgegeven</span><span class="sxs-lookup"><span data-stu-id="b1895-140">The **ServerUrl** specifies the url of the DSC Pull</span></span>

### <a name="smb-share"></a><span data-ttu-id="b1895-141">SMB-share</span><span class="sxs-lookup"><span data-stu-id="b1895-141">SMB Share</span></span>

<span data-ttu-id="b1895-142">Met het volgende script wordt de LCM geconfigureerd om configuraties te halen uit de SMB-share `\\SMBPullServer\Pull` .</span><span class="sxs-lookup"><span data-stu-id="b1895-142">The following script configures the LCM to pull configurations from the SMB Share `\\SMBPullServer\Pull`.</span></span>

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

<span data-ttu-id="b1895-143">In het script definieert het **ConfigurationRepositoryShare** -blok de pull-server, in dit geval alleen een SMB-share.</span><span class="sxs-lookup"><span data-stu-id="b1895-143">In the script, the **ConfigurationRepositoryShare** block defines the pull server, which in this case, is just an SMB share.</span></span>

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="b1895-144">Een pull-client instellen om resources te downloaden</span><span class="sxs-lookup"><span data-stu-id="b1895-144">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="b1895-145">Als u alleen het **ConfigurationRepositoryWeb** -of **ConfigurationRepositoryShare** -blok in uw LCM-configuratie opgeeft (zoals in de voor gaande voor beelden), haalt de pull-client resources op dezelfde locatie op die de configuraties ervan ophaalt.</span><span class="sxs-lookup"><span data-stu-id="b1895-145">If you specify only the **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous examples), the pull client will pull resources from the same location it retrieves its configurations.</span></span> <span data-ttu-id="b1895-146">U kunt ook afzonderlijke locaties voor bronnen opgeven.</span><span class="sxs-lookup"><span data-stu-id="b1895-146">You can also specify separate locations for resources.</span></span> <span data-ttu-id="b1895-147">Gebruik het **ResourceRepositoryWeb** -blok om een resource locatie als een afzonderlijke server op te geven.</span><span class="sxs-lookup"><span data-stu-id="b1895-147">To specify a resource location as a separate server, use the **ResourceRepositoryWeb** block.</span></span> <span data-ttu-id="b1895-148">Als u een resource locatie als SMB-share wilt opgeven, gebruikt u het **ResourceRepositoryShare** -blok.</span><span class="sxs-lookup"><span data-stu-id="b1895-148">To specify a resource location as an SMB share, use the **ResourceRepositoryShare** block.</span></span>

> [!NOTE]
> <span data-ttu-id="b1895-149">U kunt **ConfigurationRepositoryWeb** combi neren met **ResourceRepositoryShare** of **ConfigurationRepositoryShare** met **ResourceRepositoryWeb** .</span><span class="sxs-lookup"><span data-stu-id="b1895-149">You can combine **ConfigurationRepositoryWeb** with **ResourceRepositoryShare** or **ConfigurationRepositoryShare** with **ResourceRepositoryWeb** .</span></span> <span data-ttu-id="b1895-150">Voor beelden hiervan worden hieronder niet weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b1895-150">Examples of this are not shown below.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="b1895-151">HTTP DSC-pull-server</span><span class="sxs-lookup"><span data-stu-id="b1895-151">HTTP DSC Pull Server</span></span>

<span data-ttu-id="b1895-152">Met de volgende configuratie wordt een pull-client geconfigureerd voor het ophalen van de configuraties van **Contoso-PullSrv** en de bijbehorende resources van **Contoso-ResourceSrv** .</span><span class="sxs-lookup"><span data-stu-id="b1895-152">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv** .</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="b1895-153">SMB-share</span><span class="sxs-lookup"><span data-stu-id="b1895-153">SMB Share</span></span>

<span data-ttu-id="b1895-154">In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van configuraties van de SMB `\\SMBPullServer\Configurations` -share en bronnen van de SMB-share `\\SMBPullServer\Resources` .</span><span class="sxs-lookup"><span data-stu-id="b1895-154">The following example shows a metaconfiguration that sets up a client to pull configurations from the SMB share `\\SMBPullServer\Configurations`, and resources from the SMB share `\\SMBPullServer\Resources`.</span></span>

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

#### <a name="automatically-download-resources-in-push-mode"></a><span data-ttu-id="b1895-155">Automatisch bronnen in de push-modus downloaden</span><span class="sxs-lookup"><span data-stu-id="b1895-155">Automatically download Resources in Push Mode</span></span>

<span data-ttu-id="b1895-156">Vanaf Power shell 5,0 kunnen uw pull-clients modules downloaden van een SMB-share, zelfs wanneer ze zijn geconfigureerd voor de **Push** -modus.</span><span class="sxs-lookup"><span data-stu-id="b1895-156">Beginning in PowerShell 5.0, your pull clients can download modules from an SMB share, even when they are configured for **Push** mode.</span></span> <span data-ttu-id="b1895-157">Dit is vooral handig in scenario's waarin u geen pull-server wilt instellen.</span><span class="sxs-lookup"><span data-stu-id="b1895-157">This is especially useful in scenarios where you do not want to set up a Pull Server.</span></span> <span data-ttu-id="b1895-158">Het **ResourceRepositoryShare** -blok kan worden gebruikt zonder een **ConfigurationRepositoryShare** op te geven.</span><span class="sxs-lookup"><span data-stu-id="b1895-158">The **ResourceRepositoryShare** block can be used without specifying a **ConfigurationRepositoryShare** .</span></span> <span data-ttu-id="b1895-159">In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van resources van een SMB-share `\\SMBPullServer\Resources` .</span><span class="sxs-lookup"><span data-stu-id="b1895-159">The following example shows a metaconfiguration that sets up a client to pull resources from an SMB Share `\\SMBPullServer\Resources`.</span></span> <span data-ttu-id="b1895-160">Wanneer het knoop punt een configuratie heeft **gepusht** , worden de vereiste resources automatisch gedownload van de opgegeven share.</span><span class="sxs-lookup"><span data-stu-id="b1895-160">When the Node is **PUSHED** a configuration, it will automatically download any required resources, from the share specified.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="b1895-161">Een pull-client instellen om de status te rapporteren</span><span class="sxs-lookup"><span data-stu-id="b1895-161">Set up a Pull Client to report status</span></span>

<span data-ttu-id="b1895-162">Standaard worden door knoop punten geen rapporten naar een geconfigureerde pull-server verzonden.</span><span class="sxs-lookup"><span data-stu-id="b1895-162">By default, Nodes will not send reports to a configured Pull Server.</span></span> <span data-ttu-id="b1895-163">U kunt één pull-server gebruiken voor configuraties, resources en rapporten, maar u moet een **ReportRepositoryWeb** -blok maken om rapportage in te stellen.</span><span class="sxs-lookup"><span data-stu-id="b1895-163">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

### <a name="http-dsc-pull-server"></a><span data-ttu-id="b1895-164">HTTP DSC-pull-server</span><span class="sxs-lookup"><span data-stu-id="b1895-164">HTTP DSC Pull Server</span></span>

<span data-ttu-id="b1895-165">In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van configuraties en resources, en het verzenden van rapportage gegevens naar één pull-server.</span><span class="sxs-lookup"><span data-stu-id="b1895-165">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="b1895-166">Als u een rapport server wilt opgeven, gebruikt u een **ReportRepositoryWeb** -blok.</span><span class="sxs-lookup"><span data-stu-id="b1895-166">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="b1895-167">Een rapport server kan geen SMB-server zijn.</span><span class="sxs-lookup"><span data-stu-id="b1895-167">A report server cannot be an SMB server.</span></span> <span data-ttu-id="b1895-168">Met de volgende configuratie wordt een pull-client geconfigureerd voor het ophalen van de configuraties van **Contoso-PullSrv** en de bijbehorende resources van **Contoso-ResourceSrv** , en het verzenden van status rapporten naar **CONTOSO-ReportSrv** :</span><span class="sxs-lookup"><span data-stu-id="b1895-168">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv** , and to send status reports to **CONTOSO-ReportSrv** :</span></span>

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

### <a name="smb-share"></a><span data-ttu-id="b1895-169">SMB-share</span><span class="sxs-lookup"><span data-stu-id="b1895-169">SMB Share</span></span>

<span data-ttu-id="b1895-170">Een rapport server kan geen SMB-share zijn.</span><span class="sxs-lookup"><span data-stu-id="b1895-170">A report server cannot be an SMB share.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1895-171">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="b1895-171">Next Steps</span></span>

<span data-ttu-id="b1895-172">Zodra de pull-client is geconfigureerd, kunt u de volgende hand leidingen gebruiken om de volgende stappen uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="b1895-172">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="b1895-173">Configuraties publiceren naar een pull-server (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="b1895-173">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="b1895-174">Resources verpakken en uploaden naar een pull-server (v4)</span><span class="sxs-lookup"><span data-stu-id="b1895-174">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="b1895-175">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b1895-175">See Also</span></span>

- [<span data-ttu-id="b1895-176">Een pull-client met configuratie namen instellen</span><span class="sxs-lookup"><span data-stu-id="b1895-176">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)
