---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 4.0
ms.openlocfilehash: 9adc767e91ff19d373c122a0d493e7b8703d5476
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079469"
---
# <a name="set-up-a-pull-client-using-configuration-ids-in-powershell-40"></a><span data-ttu-id="7f00d-103">Instellen van een Pull-Client met behulp van configuratie-ID's in PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="7f00d-103">Set up a Pull Client using Configuration IDs in PowerShell 4.0</span></span>

><span data-ttu-id="7f00d-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7f00d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f00d-105">De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="7f00d-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="7f00d-106">Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="7f00d-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="7f00d-107">Voordat u een pull-client instelt, moet u een pull-server instellen.</span><span class="sxs-lookup"><span data-stu-id="7f00d-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="7f00d-108">Al deze order niet vereist is, helpt bij het oplossen van problemen en kunt u ervoor zorgen dat de registratie geslaagd is.</span><span class="sxs-lookup"><span data-stu-id="7f00d-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="7f00d-109">Als u een pull-server instelt, kunt u de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="7f00d-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="7f00d-110">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="7f00d-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="7f00d-111">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="7f00d-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="7f00d-112">Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren.</span><span class="sxs-lookup"><span data-stu-id="7f00d-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="7f00d-113">De volgende secties laten zien hoe u een pull-client configureren met een SMB-share of een HTTP-DSC-Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="7f00d-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="7f00d-114">Wanneer van het knooppunt LCM vernieuwd, wordt het contact opnemen met de geconfigureerde locatie voor het downloaden van de toegewezen configuraties.</span><span class="sxs-lookup"><span data-stu-id="7f00d-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="7f00d-115">Als alle vereiste resources niet aanwezig zijn op het knooppunt, wordt deze ze automatisch downloaden van de geconfigureerde locatie.</span><span class="sxs-lookup"><span data-stu-id="7f00d-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="7f00d-116">Als het knooppunt is geconfigureerd met een [Report Server](reportServer.md), deze wordt vervolgens rapporteert de status van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="7f00d-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="7f00d-117">De pull-client LCM configureren</span><span class="sxs-lookup"><span data-stu-id="7f00d-117">Configure the pull client LCM</span></span>

<span data-ttu-id="7f00d-118">Uitvoeren van een van de voorbeelden hieronder maakt u een nieuwe map voor uitvoer met de naam **PullClientConfigID** en er een metaconfiguration MOF-bestand geplaatst.</span><span class="sxs-lookup"><span data-stu-id="7f00d-118">Executing any of the examples below creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="7f00d-119">In dit geval het metaconfiguration MOF-bestand de naam `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="7f00d-119">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="7f00d-120">Aanroepen om toe te passen de configuratie, de **Set-DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguration MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="7f00d-120">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="7f00d-121">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7f00d-121">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigId –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="7f00d-122">Configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="7f00d-122">Configuration ID</span></span>

<span data-ttu-id="7f00d-123">De volgende set voorbeelden de **ConfigurationID** eigenschap van de LCM om een **Guid** die eerder is gemaakt voor dit doel.</span><span class="sxs-lookup"><span data-stu-id="7f00d-123">The examples below set the **ConfigurationID** property of the LCM to a **Guid** that had been previously created for this purpose.</span></span> <span data-ttu-id="7f00d-124">De **ConfigurationID** is wat de LCM gebruikt om te vinden van de juiste configuratie op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="7f00d-124">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="7f00d-125">Het MOF-configuratiebestand op de pull-server moet de naam `ConfigurationID.mof`, waarbij *ConfigurationID* is de waarde van de **ConfigurationID** eigenschap van het doelknooppunt LCM.</span><span class="sxs-lookup"><span data-stu-id="7f00d-125">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="7f00d-126">Zie voor meer informatie, [configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="7f00d-126">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

<span data-ttu-id="7f00d-127">U kunt een willekeurige maken **Guid** met behulp van het voorbeeld hieronder.</span><span class="sxs-lookup"><span data-stu-id="7f00d-127">You can create a random **Guid** using the example below.</span></span>

```powershell
[System.Guid]::NewGuid()
```

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="7f00d-128">Instellen van een Pull-Client voor het downloaden van configuraties</span><span class="sxs-lookup"><span data-stu-id="7f00d-128">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="7f00d-129">Elke client moet worden geconfigureerd in **Pull** modus en de url van de pull-server waar de configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="7f00d-129">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="7f00d-130">Om dit te doen, moet u de lokale Configuration Manager (LCM) configureren met de benodigde informatie.</span><span class="sxs-lookup"><span data-stu-id="7f00d-130">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="7f00d-131">Als u wilt de LCM configureren, u een speciaal soort configuratie maken met een **LocalConfigurationManager** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="7f00d-131">To configure the LCM, you create a special type of configuration, with a **LocalConfigurationManager** block.</span></span> <span data-ttu-id="7f00d-132">Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="7f00d-132">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig4.md).</span></span>

## <a name="http-dsc-pull-server"></a><span data-ttu-id="7f00d-133">HTTP DSC Pull Server</span><span class="sxs-lookup"><span data-stu-id="7f00d-133">HTTP DSC Pull Server</span></span>

<span data-ttu-id="7f00d-134">Als de pull-server is ingesteld als een webservice, stelt u de **DownloadManagerName** naar **WebDownloadManager**.</span><span class="sxs-lookup"><span data-stu-id="7f00d-134">If the pull server is set up as a web service, you set the **DownloadManagerName** to **WebDownloadManager**.</span></span> <span data-ttu-id="7f00d-135">De **WebDownloadManager** dat u opgeeft moet een **ServerUrl** naar de **DownloadManagerCustomData** sleutel.</span><span class="sxs-lookup"><span data-stu-id="7f00d-135">The **WebDownloadManager** requires that you specify a **ServerUrl** to the **DownloadManagerCustomData** key.</span></span> <span data-ttu-id="7f00d-136">U kunt ook een waarde voor opgeven **AllowUnsecureConnection**, zoals in het onderstaande voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="7f00d-136">You can also specify a value for **AllowUnsecureConnection**, as in the example below.</span></span> <span data-ttu-id="7f00d-137">Het volgende script wordt de LCM geconfigureerd voor pull-configuraties van een server met de naam 'PullServer'.</span><span class="sxs-lookup"><span data-stu-id="7f00d-137">The following script configures the LCM to pull configurations from a server named "PullServer".</span></span>

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
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
PullClientConfigId -Output "."
```

## <a name="smb-share"></a><span data-ttu-id="7f00d-138">SMB-Share</span><span class="sxs-lookup"><span data-stu-id="7f00d-138">SMB Share</span></span>

<span data-ttu-id="7f00d-139">Als de pull-server is ingesteld als een SMB-bestandsshare in plaats van een webservice, stelt u de **DownloadManagerName** naar **DscFileDownloadManager** in plaats van de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="7f00d-139">If the pull server is set up as an SMB file share, rather than a web service, you set the **DownloadManagerName** to **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span> <span data-ttu-id="7f00d-140">De **DscFileDownloadManager** dat u opgeeft moet een **bronpad** eigenschap in de **DownloadManagerCustomData**.</span><span class="sxs-lookup"><span data-stu-id="7f00d-140">The **DscFileDownloadManager** requires that you specify a **SourcePath** property in the **DownloadManagerCustomData**.</span></span> <span data-ttu-id="7f00d-141">Het volgende script configureert de LCM om op te halen van configuraties van een SMB-share met de naam "SmbDscShare" op een server met de naam 'CONTOSO-SERVER'.</span><span class="sxs-lookup"><span data-stu-id="7f00d-141">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER".</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="7f00d-142">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="7f00d-142">Next Steps</span></span>

<span data-ttu-id="7f00d-143">Nadat de pull-client is geconfigureerd, kunt u de volgende handleidingen gebruiken om uit te voeren van de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="7f00d-143">Once the pull client has been configured, you can use the following guides to perform the next steps:</span></span>

- [<span data-ttu-id="7f00d-144">Configuraties publiceren naar een Pull-Server (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="7f00d-144">Publish Configurations to a Pull Server (v4/v5)</span></span>](publishConfigs.md)
- [<span data-ttu-id="7f00d-145">Pakket- en Resources uploaden naar een Pull-Server (v4)</span><span class="sxs-lookup"><span data-stu-id="7f00d-145">Package and Upload Resources to a Pull Server (v4)</span></span>](package-upload-resources.md)

## <a name="see-also"></a><span data-ttu-id="7f00d-146">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7f00d-146">See Also</span></span>

- [<span data-ttu-id="7f00d-147">Instellen van een DSC-pull-endwebserver</span><span class="sxs-lookup"><span data-stu-id="7f00d-147">Set up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="7f00d-148">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="7f00d-148">Set up a DSC SMB pull server</span></span>](pullServerSMB.md)
