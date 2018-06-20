---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Een pull-client instellen met behulp van het configuratie-id
ms.openlocfilehash: b4a45c4d014b3c4fc0140ad492f81474b260065a
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187490"
---
# <a name="setting-up-a-pull-client-using-configuration-id"></a><span data-ttu-id="1523a-103">Een pull-client instellen met behulp van het configuratie-id</span><span class="sxs-lookup"><span data-stu-id="1523a-103">Setting up a pull client using configuration ID</span></span>

> <span data-ttu-id="1523a-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1523a-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1523a-105">De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="1523a-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="1523a-106">Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="1523a-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="1523a-107">Elk doelknooppunt heeft adviseert het gebruik van pull-modus en de URL opgegeven waar deze contact opnemen met de pull-server configuraties ophalen.</span><span class="sxs-lookup"><span data-stu-id="1523a-107">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="1523a-108">U moet de lokale Configuration Manager (LCM) configureren met de benodigde informatie om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="1523a-108">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="1523a-109">Voor het configureren van de LCM die u maakt een speciaal soort configuratie, gedecoreerd worden met de **DSCLocalConfigurationManager** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="1523a-109">To configure the LCM, you create a special type of configuration, decorated with the **DSCLocalConfigurationManager** attribute.</span></span> <span data-ttu-id="1523a-110">Zie voor meer informatie over het configureren van de LCM [configureren van de lokale Configuration Manager](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="1523a-110">For more information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

> <span data-ttu-id="1523a-111">**Opmerking**: dit onderwerp geldt voor PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="1523a-111">**Note**: This topic applies to PowerShell 5.0.</span></span> <span data-ttu-id="1523a-112">Zie voor meer informatie over het instellen van een pull-client in PowerShell 4.0 [instellen van een pull-client met behulp van configuratie-ID in PowerShell 4.0](pullClientConfigID4.md)</span><span class="sxs-lookup"><span data-stu-id="1523a-112">For information on setting up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md)</span></span>

<span data-ttu-id="1523a-113">Het volgende script configureert de LCM naar pull-configuraties van een server met de naam 'CONTOSO-PullSrv'.</span><span class="sxs-lookup"><span data-stu-id="1523a-113">The following script configures the LCM to pull configurations from a server named "CONTOSO-PullSrv".</span></span>

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

<span data-ttu-id="1523a-114">In het script wordt de **ConfigurationRepositoryWeb** blok definieert de pull-server.</span><span class="sxs-lookup"><span data-stu-id="1523a-114">In the script, the **ConfigurationRepositoryWeb** block defines the pull server.</span></span> <span data-ttu-id="1523a-115">De **ServerURL**</span><span class="sxs-lookup"><span data-stu-id="1523a-115">The **ServerURL**</span></span>

<span data-ttu-id="1523a-116">Nadat dit script wordt uitgevoerd, maakt deze een nieuwe map voor uitvoer met de naam **PullClientConfigID** en er een MOF-bestand metaconfiguratie plaatst.</span><span class="sxs-lookup"><span data-stu-id="1523a-116">After this script runs, it creates a new output folder named **PullClientConfigID** and puts a metaconfiguration MOF file there.</span></span> <span data-ttu-id="1523a-117">In dit geval wordt het MOF-bestand metaconfiguratie worden benoemd `localhost.meta.mof`.</span><span class="sxs-lookup"><span data-stu-id="1523a-117">In this case, the metaconfiguration MOF file will be named `localhost.meta.mof`.</span></span>

<span data-ttu-id="1523a-118">Aanroepen om toe te passen op de configuratie, de **Set DscLocalConfigurationManager** -cmdlet met de **pad** ingesteld op de locatie van het metaconfiguratie MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="1523a-118">To apply the configuration, call the **Set-DscLocalConfigurationManager** cmdlet, with the **Path** set to the location of the metaconfiguration MOF file.</span></span> <span data-ttu-id="1523a-119">Bijvoorbeeld: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span><span class="sxs-lookup"><span data-stu-id="1523a-119">For example: `Set-DSCLocalConfigurationManager localhost –Path .\PullClientConfigID –Verbose.`</span></span>

## <a name="configuration-id"></a><span data-ttu-id="1523a-120">Configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="1523a-120">Configuration ID</span></span>

<span data-ttu-id="1523a-121">Het script wordt de **ConfigurationID** eigenschap van LCM naar een GUID die eerder is gemaakt voor dit doel (u kunt een GUID maken met behulp van de **New-Guid** cmdlet).</span><span class="sxs-lookup"><span data-stu-id="1523a-121">The script sets the **ConfigurationID** property of LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="1523a-122">De **ConfigurationID** is de LCM gebruikt de juiste configuratie vinden op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="1523a-122">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="1523a-123">Het MOF-bestand van de configuratie op de pull-server moet de naam _ConfigurationID_MOF, waarbij _ConfigurationID_ is de waarde van de **ConfigurationID** eigenschap van het doel LCM van het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="1523a-123">The configuration MOF file on the pull server must be named _ConfigurationID_.mof, where _ConfigurationID_ is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="smb-pull-server"></a><span data-ttu-id="1523a-124">SMB pull-server</span><span class="sxs-lookup"><span data-stu-id="1523a-124">SMB pull server</span></span>

<span data-ttu-id="1523a-125">Gebruiken om een client te pull configuraties stellen van een SMB-server, een **ConfigurationRepositoryShare** blok.</span><span class="sxs-lookup"><span data-stu-id="1523a-125">To set up a client to pull configurations from an SMB server, use a **ConfigurationRepositoryShare** block.</span></span> <span data-ttu-id="1523a-126">In een **ConfigurationRepositoryShare** blok, u het pad naar de server opgeven door de **bronpad** eigenschap.</span><span class="sxs-lookup"><span data-stu-id="1523a-126">In a **ConfigurationRepositoryShare** block, you specify the path to the server by setting the **SourcePath** property.</span></span> <span data-ttu-id="1523a-127">De volgende metaconfiguratie configureert het doelknooppunt voor het ophalen van een SMB-pull-server met de naam **SMBPullServer**.</span><span class="sxs-lookup"><span data-stu-id="1523a-127">The following metaconfiguration configures the target node to pull from an SMB pull server named **SMBPullServer**.</span></span>

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
            SourcePath = '\\SMBPullServer\PullSource'

        }
    }
}
PullClientConfigID
```

## <a name="resource-and-report-servers"></a><span data-ttu-id="1523a-128">Bron- en -servers</span><span class="sxs-lookup"><span data-stu-id="1523a-128">Resource and report servers</span></span>

<span data-ttu-id="1523a-129">Als u alleen een **ConfigurationRepositoryWeb** of **ConfigurationRepositoryShare** blokkeren in uw configuratie LCM (zoals in het vorige voorbeeld), haalt de pull-client binnen resources uit de opgegeven server, maar wordt u rapporten niet naar verzenden.</span><span class="sxs-lookup"><span data-stu-id="1523a-129">If you specify only a **ConfigurationRepositoryWeb** or **ConfigurationRepositoryShare** block in your LCM configuration (as in the previous example), the pull client will pull resources from the specified server, but it will not send reports to it.</span></span> <span data-ttu-id="1523a-130">U kunt een enkel pull-server gebruiken voor configuraties, bronnen en rapportage, maar u moet maken een **ReportRepositoryWeb** blok voor het instellen van rapportage.</span><span class="sxs-lookup"><span data-stu-id="1523a-130">You can use a single pull server for configurations, resources, and reporting, but you have to create a **ReportRepositoryWeb** block to set up reporting.</span></span>

<span data-ttu-id="1523a-131">Het volgende voorbeeld ziet een metaconfiguratie instellen van een client voor het pull-configuraties en resources en verzenden gegevens rapporteren aan een enkele pull-server.</span><span class="sxs-lookup"><span data-stu-id="1523a-131">The following example shows a metaconfiguration that sets up a client to pull configurations and resources, and send reporting data, to a single pull server.</span></span>

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

<span data-ttu-id="1523a-132">U kunt ook verschillende pull-servers voor resources en rapportage opgeven.</span><span class="sxs-lookup"><span data-stu-id="1523a-132">You can also specify different pull servers for resources and reporting.</span></span> <span data-ttu-id="1523a-133">Als u wilt opgeven van een resource-server u een gebruiken een **ResourceRepositoryWeb** (voor een pull-webserver) of een **ResourceRepositoryShare** blok (voor een SMB-pull-server).</span><span class="sxs-lookup"><span data-stu-id="1523a-133">To specify a resource server, you use either a **ResourceRepositoryWeb** (for a web pull server) or a **ResourceRepositoryShare** block (for an SMB pull server).</span></span>
<span data-ttu-id="1523a-134">Om een rapportserver die u gebruikt een **ReportRepositoryWeb** blok.</span><span class="sxs-lookup"><span data-stu-id="1523a-134">To specify a report server, you use a **ReportRepositoryWeb** block.</span></span> <span data-ttu-id="1523a-135">Een rapportserver mag niet een SMB-server.</span><span class="sxs-lookup"><span data-stu-id="1523a-135">A report server cannot be an SMB server.</span></span>
<span data-ttu-id="1523a-136">De volgende metaconfiguratie configureert u een pull-client om de configuraties van **CONTOSO PullSrv** en de daarbij behorende bronnen uit **CONTOSO ResourceSrv**, en voor het verzenden van statusrapporten aan  **CONTOSO ReportSrv**:</span><span class="sxs-lookup"><span data-stu-id="1523a-136">The following metaconfiguration configures a pull client to get its configurations from **CONTOSO-PullSrv** and its resources from **CONTOSO-ResourceSrv**, and to send status reports to **CONTOSO-ReportSrv**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1523a-137">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1523a-137">See Also</span></span>

* [<span data-ttu-id="1523a-138">Een pull-client met de configuratienamen instellen</span><span class="sxs-lookup"><span data-stu-id="1523a-138">Setting up a pull client with configuration names</span></span>](pullClientConfigNames.md)