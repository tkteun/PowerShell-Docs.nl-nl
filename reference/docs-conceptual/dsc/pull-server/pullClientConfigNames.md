---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een pull-client instellen met behulp van configuratie namen in Power shell 5,0 en hoger
description: In het artikel wordt uitgelegd hoe u een pull-client instelt met behulp van configuratie namen in Power shell 5,0 en hoger
ms.openlocfilehash: db2b08605dd8bc7e48d9d5153861ce9b36118e21
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644911"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="985fa-104">Een pull-client instellen met behulp van configuratie namen in Power shell 5,0 en hoger</span><span class="sxs-lookup"><span data-stu-id="985fa-104">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="985fa-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="985fa-105">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="985fa-106">De pull-server (Windows *-functie DSC-service* ) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="985fa-106">The Pull Server (Windows Feature *DSC-Service* ) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="985fa-107">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="985fa-107">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="985fa-108">Voordat u een pull-client instelt, moet u een pull-server instellen.</span><span class="sxs-lookup"><span data-stu-id="985fa-108">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="985fa-109">Deze volg orde is niet vereist, maar helpt bij het oplossen van problemen en helpt u ervoor te zorgen dat de registratie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="985fa-109">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="985fa-110">U kunt de volgende hand leidingen gebruiken om een pull-server in te stellen:</span><span class="sxs-lookup"><span data-stu-id="985fa-110">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="985fa-111">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="985fa-111">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="985fa-112">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="985fa-112">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="985fa-113">Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan.</span><span class="sxs-lookup"><span data-stu-id="985fa-113">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="985fa-114">In de volgende secties ziet u hoe u een pull-client kunt configureren met een SMB-share of een HTTP DSC-pull-server.</span><span class="sxs-lookup"><span data-stu-id="985fa-114">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="985fa-115">Wanneer de LCM van het knoop punt wordt vernieuwd, neemt het contact op met de geconfigureerde locatie voor het downloaden van toegewezen configuraties.</span><span class="sxs-lookup"><span data-stu-id="985fa-115">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="985fa-116">Als er vereiste bronnen niet aanwezig zijn op het knoop punt, worden deze automatisch gedownload vanaf de geconfigureerde locatie.</span><span class="sxs-lookup"><span data-stu-id="985fa-116">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="985fa-117">Als het knoop punt is geconfigureerd met een [rapport server](reportServer.md), wordt de status van de bewerking gerapporteerd.</span><span class="sxs-lookup"><span data-stu-id="985fa-117">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> [!NOTE]
> <span data-ttu-id="985fa-118">Dit onderwerp is van toepassing op Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="985fa-118">This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="985fa-119">Zie [een pull-client instellen met configuratie-ID in Power shell 4,0](pullClientConfigID4.md) voor informatie over het instellen van een pull-client in power Shell 4,0</span><span class="sxs-lookup"><span data-stu-id="985fa-119">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="985fa-120">De pull-client LCM configureren</span><span class="sxs-lookup"><span data-stu-id="985fa-120">Configure the pull client LCM</span></span>

<span data-ttu-id="985fa-121">Als u een van de onderstaande voor beelden uitvoert, maakt u een nieuwe uitvoermap met de naam **PullClientConfigName** en plaatst u daar een MOF-bestand met de meta configuratie.</span><span class="sxs-lookup"><span data-stu-id="985fa-121">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="985fa-122">In dit geval wordt het MOF-bestand van de meta configuratie aangeduid met de naam `localhost.meta.mof` .</span><span class="sxs-lookup"><span data-stu-id="985fa-122">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="985fa-123">Als u de configuratie wilt Toep assen, roept u de cmdlet **set-DscLocalConfigurationManager** aan, waarbij het **pad** is ingesteld op de locatie van het MOF-bestand met de meta configuratie.</span><span class="sxs-lookup"><span data-stu-id="985fa-123">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="985fa-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="985fa-124">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="985fa-125">Configuratie naam</span><span class="sxs-lookup"><span data-stu-id="985fa-125">Configuration Name</span></span>

<span data-ttu-id="985fa-126">In de onderstaande voor beelden wordt de eigenschap **configuratiepad** van de LCM ingesteld op de naam van een eerder gecompileerde configuratie die is gemaakt voor dit doel.</span><span class="sxs-lookup"><span data-stu-id="985fa-126">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="985fa-127">De **configuratie** naam is wat de LCM gebruikt om de juiste configuratie op de pull-server te vinden.</span><span class="sxs-lookup"><span data-stu-id="985fa-127">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="985fa-128">Het MOF-configuratie bestand op de pull-server moet een naam `<ConfigurationName>.mof` hebben, in dit geval ' ClientConfig. mof '.</span><span class="sxs-lookup"><span data-stu-id="985fa-128">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="985fa-129">Zie [configuraties publiceren naar een pull-server (v4/V5)](publishConfigs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="985fa-129">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="985fa-130">Een pull-client instellen om configuraties te downloaden</span><span class="sxs-lookup"><span data-stu-id="985fa-130">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="985fa-131">Elke client moet worden geconfigureerd in de **pull** -modus en krijgt de URL van de pull-server waar de configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="985fa-131">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="985fa-132">Hiervoor moet u de lokale Configuration Manager (LCM) configureren met de benodigde gegevens.</span><span class="sxs-lookup"><span data-stu-id="985fa-132">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="985fa-133">Als u de LCM wilt configureren, maakt u een speciaal type configuratie, gedecoreerd met het kenmerk **DSCLocalConfigurationManager** .</span><span class="sxs-lookup"><span data-stu-id="985fa-133">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="985fa-134">Zie [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md)(Engelstalig) voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="985fa-134">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="985fa-135">Met het volgende script wordt de LCM geconfigureerd voor het ophalen van configuraties van een server met de naam ' CONTOSO-PullSrv '.</span><span class="sxs-lookup"><span data-stu-id="985fa-135">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="985fa-136">In het script definieert de pull-server in het **ConfigurationRepositoryWeb** -blok.</span><span class="sxs-lookup"><span data-stu-id="985fa-136">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="985fa-137">De eigenschap **ServerURL** geeft u het eind punt voor de pull-server op.</span><span class="sxs-lookup"><span data-stu-id="985fa-137">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="985fa-138">De eigenschap **RegistrationKey** is een gedeelde sleutel tussen alle client knooppunten voor een pull-server en die pull-server.</span><span class="sxs-lookup"><span data-stu-id="985fa-138">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="985fa-139">Dezelfde waarde wordt opgeslagen in een bestand op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="985fa-139">The same value is stored in a file on the pull server.</span></span><span data-ttu-id="985fa-140"> > [!NOTE] > registratie sleutels werken alleen met **Web** -pull-servers.</span><span class="sxs-lookup"><span data-stu-id="985fa-140"> > [!NOTE] > Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="985fa-141">U moet **ConfigurationID** nog steeds gebruiken met een **SMB** -pull-server.</span><span class="sxs-lookup"><span data-stu-id="985fa-141">You must still use **ConfigurationID** with an **SMB** pull server.</span></span> <span data-ttu-id="985fa-142">Zie [een pull-client instellen met behulp van de configuratie-ID](pullClientConfigId.md) > voor meer informatie over het configureren van een pull-server met behulp van **ConfigurationID**</span><span class="sxs-lookup"><span data-stu-id="985fa-142">> For information about configuring a pull server by using **ConfigurationID** , see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="985fa-143">De eigenschap **ConfigurationNames** is een matrix die de namen specificeert van de configuraties die zijn bedoeld voor het client knooppunt.</span><span class="sxs-lookup"><span data-stu-id="985fa-143">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span><span data-ttu-id="985fa-144"> >**Opmerking:** Als u meer dan één waarde in de **ConfigurationNames** opgeeft, moet u ook **PartialConfiguration** -blokken in uw configuratie opgeven.</span><span class="sxs-lookup"><span data-stu-id="985fa-144"> >**Note:** If you specify more than one value in the **ConfigurationNames** , you must also specify **PartialConfiguration** blocks in your configuration.</span></span> <span data-ttu-id="985fa-145">Zie voor meer informatie over gedeeltelijke configuraties de gedeeltelijke configuratie van de [desired state Configuration van Power shell](partialConfigs.md). ></span><span class="sxs-lookup"><span data-stu-id="985fa-145">>For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="985fa-146">Een pull-client instellen om resources te downloaden</span><span class="sxs-lookup"><span data-stu-id="985fa-146">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="985fa-147">Als u alleen een **ConfigurationRepositoryWeb** -of **ConfigurationRepositoryShare** -blok in uw LCM-configuratie opgeeft (zoals in het voor gaande voor beeld), haalt de pull-client bronnen van dezelfde locatie op waar uw mof-bestanden worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="985fa-147">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="985fa-148">U kunt ook verschillende locaties opgeven waar clients bronnen kunnen downloaden.</span><span class="sxs-lookup"><span data-stu-id="985fa-148">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="985fa-149">Als u een bron server wilt opgeven, gebruikt u een **ResourceRepositoryWeb** (voor een webpull-server) of een **ResourceRepositoryShare** -blok (voor een SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="985fa-149">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="985fa-150">In het volgende voor beeld ziet u een-configuratie die een client instelt voor het downloaden van configuraties van een pull-server en bronnen van een SMB-share.</span><span class="sxs-lookup"><span data-stu-id="985fa-150">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ResourceRepositoryShare SMBResources
        {
            SourcePath = '\\SMBPullServer\Resources'
        }
    }
}
PullClientConfigNames
```

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="985fa-151">Een pull-client instellen om de status te rapporteren</span><span class="sxs-lookup"><span data-stu-id="985fa-151">Set up a Pull Client to report status</span></span>

<span data-ttu-id="985fa-152">U kunt één pull-server gebruiken voor configuraties, resources en rapportage.</span><span class="sxs-lookup"><span data-stu-id="985fa-152">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="985fa-153">Rapportage is standaard niet geconfigureerd voor clients.</span><span class="sxs-lookup"><span data-stu-id="985fa-153">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="985fa-154">Als u een client wilt configureren voor het rapporteren van de status, moet u een **ReportRepositoryWeb** -blok maken.</span><span class="sxs-lookup"><span data-stu-id="985fa-154">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="985fa-155">In het volgende voor beeld ziet u een-configuratie die een client instelt voor het ophalen van configuraties en resources, en het verzenden van rapportage gegevens naar één pull-server.</span><span class="sxs-lookup"><span data-stu-id="985fa-155">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="985fa-156">Een rapport server kan geen SMB-share zijn.</span><span class="sxs-lookup"><span data-stu-id="985fa-156">A report server cannot be an SMB share.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigNames
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = 'fbc6ef09-ad98-4aad-a062-92b0e0327562'
        }
    }
}
PullClientConfigNames
```

## <a name="see-also"></a><span data-ttu-id="985fa-157">Zie ook</span><span class="sxs-lookup"><span data-stu-id="985fa-157">See Also</span></span>

- [<span data-ttu-id="985fa-158">Instellen van een pull-client met configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="985fa-158">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
- [<span data-ttu-id="985fa-159">Een DSC Web-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="985fa-159">Setting up a DSC web pull server</span></span>](pullServer.md)
