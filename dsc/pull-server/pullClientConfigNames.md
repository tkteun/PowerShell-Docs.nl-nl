---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Instellen van een Pull-Client met behulp van configuratienamen in PowerShell 5.0 en hoger
ms.openlocfilehash: fd038a105da7a83ecad9b571e611b65c8ec847b3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688075"
---
# <a name="set-up-a-pull-client-using-configuration-names-in-powershell-50-and-later"></a><span data-ttu-id="02f53-103">Instellen van een Pull-Client met behulp van configuratienamen in PowerShell 5.0 en hoger</span><span class="sxs-lookup"><span data-stu-id="02f53-103">Set up a Pull Client using Configuration Names in PowerShell 5.0 and later</span></span>

> <span data-ttu-id="02f53-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="02f53-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02f53-105">De Pull-Server (Windows-functie *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="02f53-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="02f53-106">Het verdient aanbeveling om te beginnen met het overstappen clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen die zijn opgenomen [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="02f53-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="02f53-107">Voordat u een pull-client instelt, moet u een pull-server instellen.</span><span class="sxs-lookup"><span data-stu-id="02f53-107">Before setting up a pull client, you should set up a pull server.</span></span> <span data-ttu-id="02f53-108">Al deze order niet vereist is, helpt bij het oplossen van problemen en kunt u ervoor zorgen dat de registratie geslaagd is.</span><span class="sxs-lookup"><span data-stu-id="02f53-108">Though this order is not required, it helps with troubleshooting, and helps you ensure that the registration was successful.</span></span> <span data-ttu-id="02f53-109">Als u een pull-server instelt, kunt u de volgende handleidingen:</span><span class="sxs-lookup"><span data-stu-id="02f53-109">To set up a pull server, you can use the following guides:</span></span>

- [<span data-ttu-id="02f53-110">Een DSC SMB-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="02f53-110">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="02f53-111">Een DSC HTTP-Pull-Server instellen</span><span class="sxs-lookup"><span data-stu-id="02f53-111">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="02f53-112">Elk doelknooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources, en zelfs de status rapporteren.</span><span class="sxs-lookup"><span data-stu-id="02f53-112">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="02f53-113">De volgende secties laten zien hoe u een pull-client configureren met een SMB-share of een HTTP-DSC-Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="02f53-113">The sections below show you how to configure a pull client with an SMB share or HTTP DSC Pull Server.</span></span> <span data-ttu-id="02f53-114">Wanneer van het knooppunt LCM vernieuwd, wordt het contact opnemen met de geconfigureerde locatie voor het downloaden van de toegewezen configuraties.</span><span class="sxs-lookup"><span data-stu-id="02f53-114">When the Node's LCM refreshes, it will reach out to the configured location to download any assigned configurations.</span></span> <span data-ttu-id="02f53-115">Als alle vereiste resources niet aanwezig zijn op het knooppunt, wordt deze ze automatisch downloaden van de geconfigureerde locatie.</span><span class="sxs-lookup"><span data-stu-id="02f53-115">If any required resources do not exist on the Node, it will automatically download them from the configured location.</span></span> <span data-ttu-id="02f53-116">Als het knooppunt is geconfigureerd met een [Report Server](reportServer.md), deze wordt vervolgens rapporteert de status van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="02f53-116">If the Node is configured with a [Report Server](reportServer.md), it will then report the status of the operation.</span></span>

> <span data-ttu-id="02f53-117">**Houd er rekening mee**: In dit onderwerp is van toepassing op PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="02f53-117">**Note**: This topic applies to PowerShell 5.0.</span></span>
<span data-ttu-id="02f53-118">Zie voor meer informatie over het instellen van een pull-client in PowerShell 4.0 [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="02f53-118">For information on setting up a pull client in PowerShell 4.0, see [Set up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

## <a name="configure-the-pull-client-lcm"></a><span data-ttu-id="02f53-119">De pull-client LCM configureren</span><span class="sxs-lookup"><span data-stu-id="02f53-119">Configure the pull client LCM</span></span>

<span data-ttu-id="02f53-120">Uitvoeren van een van de voorbeelden hieronder maakt u een nieuwe map voor uitvoer met de naam **PullClientConfigName** en er een metaconfiguration MOF-bestand geplaatst.</span><span class="sxs-lookup"><span data-stu-id="02f53-120">Executing any of the examples below creates a new output folder named **PullClientConfigName** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="02f53-121">In dit geval het metaconfiguration MOF-bestand de naam `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="02f53-121">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="02f53-122">Aanroepen om toe te passen de configuratie, de **Set-DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguration MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="02f53-122">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="02f53-123">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="02f53-123">For example:</span></span>

```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path .\PullClientConfigName –Verbose.
```

## <a name="configuration-name"></a><span data-ttu-id="02f53-124">Naam van de configuratie</span><span class="sxs-lookup"><span data-stu-id="02f53-124">Configuration Name</span></span>

<span data-ttu-id="02f53-125">De voorbeelden hieronder wordt de **ConfigurationName** eigenschap van de LCM op de naam van een eerder gecompileerde configuratie gemaakt voor dit doel.</span><span class="sxs-lookup"><span data-stu-id="02f53-125">The examples below sets the **ConfigurationName** property of the LCM to the name of a previously compiled Configuration, created for this purpose.</span></span> <span data-ttu-id="02f53-126">De **ConfigurationName** is wat de LCM gebruikt om te vinden van de juiste configuratie op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="02f53-126">The **ConfigurationName** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="02f53-127">Het MOF-configuratiebestand op de pull-server moet de naam `<ConfigurationName>.mof`, in dit geval 'ClientConfig.mof'.</span><span class="sxs-lookup"><span data-stu-id="02f53-127">The configuration MOF file on the pull server must be named `<ConfigurationName>.mof`, in this case, "ClientConfig.mof".</span></span> <span data-ttu-id="02f53-128">Zie voor meer informatie, [configuraties publiceren naar een Pull-Server (v4/v5)](publishConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="02f53-128">For more information, see [Publish Configurations to a Pull Server (v4/v5)](publishConfigs.md).</span></span>

## <a name="set-up-a-pull-client-to-download-configurations"></a><span data-ttu-id="02f53-129">Instellen van een Pull-Client voor het downloaden van configuraties</span><span class="sxs-lookup"><span data-stu-id="02f53-129">Set up a Pull Client to download Configurations</span></span>

<span data-ttu-id="02f53-130">Elke client moet worden geconfigureerd in **Pull** modus en de url van de pull-server waar de configuratie is opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="02f53-130">Each client must be configured in **Pull** mode and given the pull server url where its configuration is stored.</span></span> <span data-ttu-id="02f53-131">Om dit te doen, moet u de lokale Configuration Manager (LCM) configureren met de benodigde informatie.</span><span class="sxs-lookup"><span data-stu-id="02f53-131">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="02f53-132">Als u wilt de LCM configureren, maakt u een speciaal soort configuratie, voorzien van de **DSCLocalConfigurationManager** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="02f53-132">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="02f53-133">Zie voor meer informatie over het configureren van de LCM [de Local Configuration Manager configureren](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="02f53-133">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="02f53-134">Het volgende script wordt de LCM geconfigureerd voor pull-configuraties van een server met de naam 'CONTOSO-PullSrv'.</span><span class="sxs-lookup"><span data-stu-id="02f53-134">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

- <span data-ttu-id="02f53-135">In het script de **ConfigurationRepositoryWeb** blok definieert de pull-server.</span><span class="sxs-lookup"><span data-stu-id="02f53-135">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="02f53-136">De **ServerURL** eigenschap geeft u het eindpunt voor de pull-server.</span><span class="sxs-lookup"><span data-stu-id="02f53-136">The **ServerURL** property specifies the endpoint for the pull server.</span></span>

- <span data-ttu-id="02f53-137">De **RegistrationKey** eigenschap is een gedeelde sleutel tussen alle knooppunten van de client voor een pull-server en die pull-server.</span><span class="sxs-lookup"><span data-stu-id="02f53-137">The **RegistrationKey** property is a shared key between all client nodes for a pull server and that pull server.</span></span> <span data-ttu-id="02f53-138">De dezelfde waarde wordt opgeslagen in een bestand op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="02f53-138">The same value is stored in a file on the pull server.</span></span>
  > <span data-ttu-id="02f53-139">**Houd er rekening mee**: Registratiesleutels werken alleen met **web** pull-servers.</span><span class="sxs-lookup"><span data-stu-id="02f53-139">**Note**: Registration keys work only with **web** pull servers.</span></span> <span data-ttu-id="02f53-140">U moet nog steeds gebruiken **ConfigurationID** met een **SMB** pull-server.</span><span class="sxs-lookup"><span data-stu-id="02f53-140">You must still use **ConfigurationID** with an **SMB** pull server.</span></span>
  > <span data-ttu-id="02f53-141">Voor informatie over het configureren van een pull-server met behulp van **ConfigurationID**, Zie [instellen van een pull-client met behulp van configuratie-ID](pullClientConfigId.md)</span><span class="sxs-lookup"><span data-stu-id="02f53-141">For information about configuring a pull server by using **ConfigurationID**, see [Setting up a pull client using configuration ID](pullClientConfigId.md)</span></span>

- <span data-ttu-id="02f53-142">De **ConfigurationNames** eigenschap is een matrix die Hiermee geeft u de namen van de configuraties die bestemd zijn voor de client-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="02f53-142">The **ConfigurationNames** property is an array that specifies the names of the configurations intended for the client node.</span></span>
  ><span data-ttu-id="02f53-143">**Opmerking:** Als u meer dan één waarde in de **ConfigurationNames**, moet u ook opgeven **PartialConfiguration** blokkeert in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="02f53-143">**Note:** If you specify more than one value in the **ConfigurationNames**, you must also specify **PartialConfiguration** blocks in your configuration.</span></span>
  ><span data-ttu-id="02f53-144">Zie voor meer informatie over het gedeeltelijke configuraties [PowerShell Desired State Configuration gedeeltelijke configuraties](partialConfigs.md).</span><span class="sxs-lookup"><span data-stu-id="02f53-144">For information about partial configurations, see [PowerShell Desired State Configuration partial configurations](partialConfigs.md).</span></span>

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

## <a name="set-up-a-pull-client-to-download-resources"></a><span data-ttu-id="02f53-145">Instellen van een Pull-Client voor het downloaden van Resources</span><span class="sxs-lookup"><span data-stu-id="02f53-145">Set up a Pull Client to download Resources</span></span>

<span data-ttu-id="02f53-146">Als u alleen opgeeft, een **ConfigurationRepositoryWeb** of **ConfigurationRepositoryShare** blokkeren in uw configuratie LCM (zoals in het vorige voorbeeld), de pull-client-resources van hetzelfde wordt opgehaald de locatie waar "uw MOF-bestanden worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="02f53-146">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from same location where your ".mof" files are stored.</span></span> <span data-ttu-id="02f53-147">Ook kunt u verschillende locaties waar resources op clients kunnen downloaden.</span><span class="sxs-lookup"><span data-stu-id="02f53-147">You can also specify different locations where clients can download resources.</span></span> <span data-ttu-id="02f53-148">Als u een resource-server, u een gebruiken een **ResourceRepositoryWeb** (voor een web-pull-server) of een **ResourceRepositoryShare** blokkeren (voor een SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="02f53-148">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>

<span data-ttu-id="02f53-149">Het volgende voorbeeld ziet een metaconfiguration instellen van een client te downloaden van configuraties van een Pull-Server en bronnen van een SMB-share.</span><span class="sxs-lookup"><span data-stu-id="02f53-149">The following example shows a metaconfiguration that sets up a client to download configurations from a Pull Server, and resources from an SMB share.</span></span>

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

## <a name="set-up-a-pull-client-to-report-status"></a><span data-ttu-id="02f53-150">Instellen van een Pull-Client voor statusrapportage</span><span class="sxs-lookup"><span data-stu-id="02f53-150">Set up a Pull Client to report status</span></span>

<span data-ttu-id="02f53-151">U kunt een enkel pull-server gebruiken voor configuraties, resources en rapportage.</span><span class="sxs-lookup"><span data-stu-id="02f53-151">You can use a single pull server for configurations, resources, and reporting.</span></span> <span data-ttu-id="02f53-152">Rapportage is niet geconfigureerd voor clients standaard.</span><span class="sxs-lookup"><span data-stu-id="02f53-152">Reporting is not configured for clients by default.</span></span> <span data-ttu-id="02f53-153">Als u een client voor statusrapportage configureren, moet u maken een **ReportRepositoryWeb** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="02f53-153">To configure a client to report status, you have to create a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="02f53-154">Het volgende voorbeeld ziet een metaconfiguration instellen van een client pull-configuraties, resources en verzenden gegevens rapporteren aan een enkele pull-server.</span><span class="sxs-lookup"><span data-stu-id="02f53-154">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="02f53-155">Een rapportserver mag niet een SMB-share.</span><span class="sxs-lookup"><span data-stu-id="02f53-155">A report server cannot be an SMB share.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="02f53-156">Zie ook</span><span class="sxs-lookup"><span data-stu-id="02f53-156">See Also</span></span>

* [<span data-ttu-id="02f53-157">Instellen van een pull-client met configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="02f53-157">Setting up a pull client with configuration ID</span></span>](PullClientConfigNames.md)
* [<span data-ttu-id="02f53-158">Instellen van een DSC-pull-endwebserver</span><span class="sxs-lookup"><span data-stu-id="02f53-158">Setting up a DSC web pull server</span></span>](pullServer.md)
