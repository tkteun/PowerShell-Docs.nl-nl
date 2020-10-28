---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Een pull-client instellen met configuratie-Id's in Power Shell 4,0
description: In dit artikel wordt uitgelegd hoe u een pull-client instelt met behulp van configuratie-Id's in Power Shell 4,0
ms.openlocfilehash: 2a3d7b79f29030620cddc2b2131cb4432e41e4eb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649003"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="9410c-104">Een pull-client instellen met configuratie-Id's in Power Shell 4,0</span><span class="sxs-lookup"><span data-stu-id="9410c-104">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="9410c-105">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="9410c-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9410c-106">De pull-server (Windows *-functie DSC-service* ) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="9410c-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="9410c-107">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="9410c-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="9410c-108">Voordat u een pull-client instelt, moet u een pull-server instellen.</span><span class="sxs-lookup"><span data-stu-id="9410c-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="9410c-109">Deze volg orde is niet vereist, maar helpt bij het oplossen van problemen en helpt u ervoor te zorgen dat de registratie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="9410c-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="9410c-110">U kunt de volgende hand leidingen gebruiken om een pull-server in te stellen:</span><span class="sxs-lookup"><span data-stu-id="9410c-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="9410c-111">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="9410c-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9410c-112">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="9410c-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="9410c-113">Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan.</span><span class="sxs-lookup"><span data-stu-id="9410c-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="9410c-114">In de volgende secties ziet u hoe u een pull-client kunt configureren met een SMB-share of een HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="9410c-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="9410c-115">Wanneer de LCM van het knoop punt wordt vernieuwd, neemt het contact op met de geconfigureerde locatie voor het downloaden van toegewezen configuraties.</span><span class="sxs-lookup"><span data-stu-id="9410c-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="9410c-116">Als er vereiste bronnen niet aanwezig zijn op het knoop punt, worden deze automatisch gedownload vanaf de geconfigureerde locatie.</span><span class="sxs-lookup"><span data-stu-id="9410c-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="9410c-117">Als het knoop punt is geconfigureerd met een [rapport server](reportServer.md), wordt de status van de bewerking gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="9410c-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="9410c-118">De pull-client LCM configureren</span><span class="sxs-lookup"><span data-stu-id="9410c-118">Configure the pull client LCM</span></span>

<span data-ttu-id="9410c-119">Als u een van de onderstaande voor beelden uitvoert, maakt u een nieuwe uitvoermap met de naam **PullClientConfigID** en plaatst u daar een MOF-bestand met de meta configuratie.</span><span class="sxs-lookup"><span data-stu-id="9410c-119">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="9410c-120">In dit geval wordt het MOF-bestand van de meta configuratie aangeduid met de naam `localhost.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="9410c-120">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="9410c-121">Als u de configuratie wilt Toep assen, roept u de cmdlet **set-DscLocalConfigurationManager** aan, waarbij het **pad** is ingesteld op de locatie van het MOF-bestand met de meta configuratie.</span><span class="sxs-lookup"><span data-stu-id="9410c-121">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="9410c-122">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="9410c-122">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="9410c-123">Configuratie-id</span><span class="sxs-lookup"><span data-stu-id="9410c-123">Configuration ID</span></span>

<span data-ttu-id="9410c-124">In de onderstaande voor beelden wordt de eigenschap **ConfigurationID** van de LCM ingesteld op een **GUID** die eerder is gemaakt voor dit doel.</span><span class="sxs-lookup"><span data-stu-id="9410c-124">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="9410c-125">De **ConfigurationID** is wat de LCM gebruikt om de juiste configuratie op de pull-server te vinden.</span><span class="sxs-lookup"><span data-stu-id="9410c-125">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="9410c-126">Het MOF-configuratie bestand op de pull-server moet een naam `ConfigurationID.mof` hebben, waarbij *ConfigurationID* de waarde is van de eigenschap **ConfigurationID** van de LCM van het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="9410c-126">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="9410c-127">Zie [configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9410c-127">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="9410c-128">U kunt een wille keurige **GUID** maken met behulp van het onderstaande voor beeld.</span><span class="sxs-lookup"><span data-stu-id="9410c-128">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="9410c-129">Een pull-client instellen om configuraties te downloaden</span><span class="sxs-lookup"><span data-stu-id="9410c-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="9410c-130">Elke client moet worden geconfigureerd in de **pull** -modus en krijgt de URL van de pull-server waar de configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="9410c-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="9410c-131">Hiervoor moet u de lokale Configuration Manager (LCM) configureren met de benodigde gegevens.</span><span class="sxs-lookup"><span data-stu-id="9410c-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="9410c-132">Als u de LCM wilt configureren, maakt u een speciaal type configuratie, met een **LocalConfigurationManager** -blok.</span><span class="sxs-lookup"><span data-stu-id="9410c-132">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="9410c-133">Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md)(Engelstalig) voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="9410c-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="9410c-134">HTTP DSC-pull-server</span><span class="sxs-lookup"><span data-stu-id="9410c-134">HTTP DSC Pull Server</span></span>

<span data-ttu-id="9410c-135">Als de pull-server is ingesteld als een webservice, stelt u de **DownloadManagerName** in op **WebDownloadManager** .</span><span class="sxs-lookup"><span data-stu-id="9410c-135">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager** .</span></span> <span data-ttu-id="9410c-136">De **WebDownloadManager** vereist dat u een **ServerUrl** opgeeft bij de **DownloadManagerCustomData** -sleutel.</span><span class="sxs-lookup"><span data-stu-id="9410c-136">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="9410c-137">U kunt ook een waarde opgeven voor **AllowUnsecureConnection** , zoals in het onderstaande voor beeld.</span><span class="sxs-lookup"><span data-stu-id="9410c-137">You can also specify a value for **AllowUnsecureConnection** , as in the example below.</span></span> <span data-ttu-id="9410c-138">Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een server met de naam ' PullServer '.</span><span class="sxs-lookup"><span data-stu-id="9410c-138">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = "TRUE"}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="9410c-139">SMB-share</span><span class="sxs-lookup"><span data-stu-id="9410c-139">SMB Share</span></span>

<span data-ttu-id="9410c-140">Als de pull-server is ingesteld als een SMB-bestands share in plaats van een webservice, stelt u de **DownloadManagerName** in op **DscFileDownloadManager** in plaats van de **WebDownLoadManager** .</span><span class="sxs-lookup"><span data-stu-id="9410c-140">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager** .</span></span> <span data-ttu-id="9410c-141">De **DscFileDownloadManager** vereist dat u een eigenschap **SourcePath** opgeeft in de **DownloadManagerCustomData** .</span><span class="sxs-lookup"><span data-stu-id="9410c-141">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData** .</span></span> <span data-ttu-id="9410c-142">Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een SMB-share met de naam ' SmbDscShare ' op een server met de naam ' CONTOSO-SERVER '.</span><span class="sxs-lookup"><span data-stu-id="9410c-142">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

```powershell
Configuration PullClientConfigId
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
PullClientConfigId -Output "."
```

## <a name="next-steps"></a><span data-ttu-id="9410c-143">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="9410c-143">Next Steps</span></span>

<span data-ttu-id="9410c-144">Zodra de pull-client is geconfigureerd, kunt u de volgende hand leidingen gebruiken om de volgende stappen uit te voeren:</span><span class="sxs-lookup"><span data-stu-id="9410c-144">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="9410c-145">Configuraties publiceren naar een pull-server (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="9410c-145">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="9410c-146">Resources verpakken en uploaden naar een pull-server (v4)</span><span class="sxs-lookup"><span data-stu-id="9410c-146">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="9410c-147">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9410c-147">See Also</span></span>

- [<span data-ttu-id="9410c-148">Een DSC Web-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="9410c-148">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="9410c-149">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="9410c-149">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
