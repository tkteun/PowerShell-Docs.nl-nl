---
ms.date: 01/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-pull-service
ms.openlocfilehash: f171c3dc579dfb24a8c9fb87fbb50dccae619091
ms.sourcegitcommit: aaf1284dfec2e4c698009d6dc27ff103aaafd581
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885384"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="81410-103">Pull-service desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="81410-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81410-104">De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="81410-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="81410-105">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) of een van de [hieronder vermelde Community](pullserver.md#community-solutions-for-pull-service)-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="81410-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="81410-106">Local Configuration Manager (LCM) kan centraal worden beheerd door een pull-service oplossing.</span><span class="sxs-lookup"><span data-stu-id="81410-106">Local Configuration Manager (LCM) can be centrally managed by a Pull Service solution.</span></span> <span data-ttu-id="81410-107">Wanneer u deze methode gebruikt, wordt het knoop punt dat wordt beheerd, geregistreerd bij een service en een configuratie toegewezen in de instellingen van de LCM.</span><span class="sxs-lookup"><span data-stu-id="81410-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span> <span data-ttu-id="81410-108">De configuratie en alle DSC-resources die nodig zijn als afhankelijkheden voor de configuratie, worden gedownload naar de computer en gebruikt door LCM voor het beheren van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="81410-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span> <span data-ttu-id="81410-109">Informatie over de status van de computer die wordt beheerd, wordt geüpload naar de service voor rapportage.</span><span class="sxs-lookup"><span data-stu-id="81410-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span> <span data-ttu-id="81410-110">Dit concept wordt ' pull-service ' genoemd.</span><span class="sxs-lookup"><span data-stu-id="81410-110">This concept is referred to as "pull service".</span></span>

<span data-ttu-id="81410-111">De huidige opties voor de pull-service zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="81410-111">The current options for pull service include:</span></span>

- <span data-ttu-id="81410-112">Azure Automation desired state Configuration-service</span><span class="sxs-lookup"><span data-stu-id="81410-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="81410-113">Een pull-service die wordt uitgevoerd op Windows Server</span><span class="sxs-lookup"><span data-stu-id="81410-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="81410-114">Door de Community beheerde open-source-oplossingen</span><span class="sxs-lookup"><span data-stu-id="81410-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="81410-115">Een SMB-share</span><span class="sxs-lookup"><span data-stu-id="81410-115">An SMB share</span></span>

<span data-ttu-id="81410-116">De aanbevolen schaal voor elke oplossing is als volgt:</span><span class="sxs-lookup"><span data-stu-id="81410-116">The recommended scale for each solution is as follows:</span></span>

|                   <span data-ttu-id="81410-117">Oplossing</span><span class="sxs-lookup"><span data-stu-id="81410-117">Solution</span></span>                   |              <span data-ttu-id="81410-118">Client knooppunten</span><span class="sxs-lookup"><span data-stu-id="81410-118">Client nodes</span></span>              |
| -------------------------------------------- | -------------------------------------- |
| <span data-ttu-id="81410-119">Windows pull-server met MDB/ESENT-data base</span><span class="sxs-lookup"><span data-stu-id="81410-119">Windows Pull Server using MDB/ESENT database</span></span> | <span data-ttu-id="81410-120">Maxi maal 500 knoop punten</span><span class="sxs-lookup"><span data-stu-id="81410-120">Up to 500 nodes</span></span>                        |
| <span data-ttu-id="81410-121">Windows pull-server met SQL database</span><span class="sxs-lookup"><span data-stu-id="81410-121">Windows Pull Server using SQL database</span></span>       | <span data-ttu-id="81410-122">Maxi maal 1000 knoop punten</span><span class="sxs-lookup"><span data-stu-id="81410-122">Up to 1000 nodes</span></span>                       |
| <span data-ttu-id="81410-123">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="81410-123">Azure Automation DSC</span></span>                         | <span data-ttu-id="81410-124">Scenario's met meer dan 1000 knoop punten</span><span class="sxs-lookup"><span data-stu-id="81410-124">Scenarios with greater than 1000 nodes</span></span> |

<span data-ttu-id="81410-125">**De aanbevolen oplossing**en de optie met de meeste beschik bare functies is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="81410-125">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="81410-126">Met de Azure-service kunt u knoop punten on-premises beheren in particuliere data centers of in open bare Clouds, zoals Azure en AWS.</span><span class="sxs-lookup"><span data-stu-id="81410-126">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span> <span data-ttu-id="81410-127">Voor particuliere omgevingen waarbij servers niet rechtstreeks verbinding kunnen maken met internet, kunt u overwegen om uitgaand verkeer alleen te beperken tot het gepubliceerde Azure IP-bereik (Zie [IP-bereiken van Azure-data centers](https://www.microsoft.com/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="81410-127">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="81410-128">De functies van de online service die momenteel niet beschikbaar zijn in de pull-service op Windows Server zijn:</span><span class="sxs-lookup"><span data-stu-id="81410-128">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="81410-129">Alle gegevens worden versleuteld tijdens de overdracht en in rust</span><span class="sxs-lookup"><span data-stu-id="81410-129">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="81410-130">Client certificaten worden automatisch gemaakt en beheerd</span><span class="sxs-lookup"><span data-stu-id="81410-130">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="81410-131">Archief geheimen voor het centraal beheren van [wacht woorden/referenties](/azure/automation/automation-credentials)of [variabelen](/azure/automation/automation-variables) zoals server namen of verbindings reeksen</span><span class="sxs-lookup"><span data-stu-id="81410-131">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="81410-132">De configuratie van het knoop punt [LCM](../managing-nodes/metaConfig.md#basic-settings) centraal beheren</span><span class="sxs-lookup"><span data-stu-id="81410-132">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="81410-133">Configuraties centraal toewijzen aan client knooppunten</span><span class="sxs-lookup"><span data-stu-id="81410-133">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="81410-134">Wijzigingen in de configuratie van ' Canarische groups ' vrijgeven voordat de productie wordt bereikt</span><span class="sxs-lookup"><span data-stu-id="81410-134">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="81410-135">Grafische rapportage</span><span class="sxs-lookup"><span data-stu-id="81410-135">Graphical reporting</span></span>
  - <span data-ttu-id="81410-136">Status Details op DSC-resource niveau granulatie</span><span class="sxs-lookup"><span data-stu-id="81410-136">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="81410-137">Uitgebreide fout berichten van client computers voor het oplossen van problemen</span><span class="sxs-lookup"><span data-stu-id="81410-137">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="81410-138">[Integratie met Azure log Analytics](/azure/automation/automation-dsc-diagnostics) voor waarschuwingen, geautomatiseerde taken, Android/IOS-app voor rapportage en waarschuwingen</span><span class="sxs-lookup"><span data-stu-id="81410-138">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="81410-139">DSC-pull-service in Windows Server</span><span class="sxs-lookup"><span data-stu-id="81410-139">DSC pull service in Windows Server</span></span>

<span data-ttu-id="81410-140">Het is mogelijk om een pull-service te configureren om te worden uitgevoerd op Windows Server.</span><span class="sxs-lookup"><span data-stu-id="81410-140">It is possible to configure a pull service to run on Windows Server.</span></span> <span data-ttu-id="81410-141">U wordt aangeraden dat de pull-service oplossing die is opgenomen in Windows Server, alleen mogelijkheden bevat voor het opslaan van configuraties/modules voor het downloaden en vastleggen van rapport gegevens in een Data Base.</span><span class="sxs-lookup"><span data-stu-id="81410-141">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data into a database.</span></span> <span data-ttu-id="81410-142">Het bevat niet veel van de mogelijkheden die de service in Azure biedt, en is dus geen goed hulp programma voor het evalueren van de manier waarop de service wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="81410-142">It does not include many of the capabilities offered by the service in Azure and so, is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="81410-143">De pull-service in Windows Server is een webservice in IIS die gebruikmaakt van een OData-interface om DSC-configuratie bestanden beschikbaar te maken voor doel knooppunten wanneer deze knoop punten hen vragen.</span><span class="sxs-lookup"><span data-stu-id="81410-143">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="81410-144">Vereisten voor het gebruik van een pull-server:</span><span class="sxs-lookup"><span data-stu-id="81410-144">Requirements for using a pull server:</span></span>

- <span data-ttu-id="81410-145">Een server met:</span><span class="sxs-lookup"><span data-stu-id="81410-145">A server running:</span></span>
  - <span data-ttu-id="81410-146">WMF/Power Shell 4,0 of hoger</span><span class="sxs-lookup"><span data-stu-id="81410-146">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="81410-147">IIS-serverrol</span><span class="sxs-lookup"><span data-stu-id="81410-147">IIS server role</span></span>
  - <span data-ttu-id="81410-148">DSC Service</span><span class="sxs-lookup"><span data-stu-id="81410-148">DSC Service</span></span>
- <span data-ttu-id="81410-149">In het ideale geval wordt een certificaat gegenereerd voor het beveiligen van referenties die worden door gegeven aan de lokale Configuration Manager (LCM) op doel knooppunten</span><span class="sxs-lookup"><span data-stu-id="81410-149">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="81410-150">De beste manier om Windows Server te configureren voor het hosten van pull-service is het gebruik van een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="81410-150">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span> <span data-ttu-id="81410-151">Hieronder vindt u een voorbeeld script.</span><span class="sxs-lookup"><span data-stu-id="81410-151">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="81410-152">Ondersteunde database systemen</span><span class="sxs-lookup"><span data-stu-id="81410-152">Supported database systems</span></span>

| <span data-ttu-id="81410-153">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="81410-153">WMF 4.0</span></span> |       <span data-ttu-id="81410-154">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="81410-154">WMF 5.0</span></span>        |       <span data-ttu-id="81410-155">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="81410-155">WMF 5.1</span></span>        | <span data-ttu-id="81410-156">WMF 5,1 (Windows Server Insider preview 17090)</span><span class="sxs-lookup"><span data-stu-id="81410-156">WMF 5.1 (Windows Server Insider Preview 17090)</span></span> |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| <span data-ttu-id="81410-157">EXTENSIE</span><span class="sxs-lookup"><span data-stu-id="81410-157">MDB</span></span>     | <span data-ttu-id="81410-158">ESENT (standaard), MDB</span><span class="sxs-lookup"><span data-stu-id="81410-158">ESENT (Default), MDB</span></span> | <span data-ttu-id="81410-159">ESENT (standaard), MDB</span><span class="sxs-lookup"><span data-stu-id="81410-159">ESENT (Default), MDB</span></span> | <span data-ttu-id="81410-160">ESENT (standaard), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="81410-160">ESENT (Default), SQL Server, MDB</span></span>               |

<span data-ttu-id="81410-161">Vanaf release 17090 van [Windows Server Insider preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver)is SQL Server een ondersteunde optie voor de pull-service (Windows-functie *DSC-service*).</span><span class="sxs-lookup"><span data-stu-id="81410-161">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="81410-162">Dit biedt een nieuwe optie voor het schalen van grote DSC-omgevingen die niet zijn gemigreerd naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="81410-162">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="81410-163">SQL Server ondersteuning wordt niet toegevoegd aan eerdere versies van WMF 5,1 (of eerder) en is alleen beschikbaar op Windows Server-versies die groter zijn dan of gelijk zijn aan 17090.</span><span class="sxs-lookup"><span data-stu-id="81410-163">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="81410-164">Als u de pull-server wilt configureren voor het gebruik van SQL Server, stelt u **SqlProvider** in op `$true` en **SqlConnectionString** op een geldige SQL Server verbindings reeks.</span><span class="sxs-lookup"><span data-stu-id="81410-164">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="81410-165">Zie voor meer informatie [SqlClient-verbindings reeksen](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="81410-165">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="81410-166">Voor een voor beeld van SQL Server configuratie met **xDscWebService**, lees dan eerst [met behulp van de xDscWebService-resource](#using-the-xdscwebservice-resource) en controleer vervolgens [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 op github](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="81410-166">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="81410-167">De xDscWebService-Resource gebruiken</span><span class="sxs-lookup"><span data-stu-id="81410-167">Using the xDscWebService resource</span></span>

<span data-ttu-id="81410-168">De eenvoudigste manier om een webpull-server in te stellen, is door gebruik te maken van de **xDscWebService** -resource die is opgenomen in de **xPSDesiredStateConfiguration** -module.</span><span class="sxs-lookup"><span data-stu-id="81410-168">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="81410-169">In de volgende stappen wordt uitgelegd hoe u de resource gebruikt in een `Configuration` waarmee de webservice wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="81410-169">The following steps explain how to use the resource in a `Configuration` that sets up the web service.</span></span>

1. <span data-ttu-id="81410-170">Roep de cmdlet [install-module](/reference/6/PowerShellGet/Install-Module.md) aan om de **xPSDesiredStateConfiguration** -module te installeren.</span><span class="sxs-lookup"><span data-stu-id="81410-170">Call the [Install-Module](/reference/6/PowerShellGet/Install-Module.md) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>

   > [!NOTE]
   > <span data-ttu-id="81410-171">`Install-Module` is opgenomen in de **PowerShellGet** -module, die is opgenomen in power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="81410-171">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0 and higher.</span></span>

1. <span data-ttu-id="81410-172">Een SSL-certificaat voor de DSC-pull-server ophalen van een vertrouwde certificerings instantie, binnen uw organisatie of een open bare instantie.</span><span class="sxs-lookup"><span data-stu-id="81410-172">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="81410-173">Het certificaat dat is ontvangen van de certificerings instantie is meestal in de PFX-indeling.</span><span class="sxs-lookup"><span data-stu-id="81410-173">The certificate received from the authority is usually in the PFX format.</span></span>
1. <span data-ttu-id="81410-174">Installeer het certificaat op het knoop punt dat de DSC-pull-server wordt op de standaard locatie, dat moet worden `CERT:\LocalMachine\My`.</span><span class="sxs-lookup"><span data-stu-id="81410-174">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="81410-175">Noteer de vinger afdruk van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="81410-175">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="81410-176">Selecteer een GUID die moet worden gebruikt als de registratie sleutel.</span><span class="sxs-lookup"><span data-stu-id="81410-176">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="81410-177">Als u een rapport wilt genereren met Power shell, voert u het volgende in bij de PS-prompt en drukt u op ENTER: `[guid]::newGuid()` of `New-Guid`.</span><span class="sxs-lookup"><span data-stu-id="81410-177">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="81410-178">Deze sleutel wordt gebruikt door client knooppunten als een gedeelde sleutel voor verificatie tijdens de registratie.</span><span class="sxs-lookup"><span data-stu-id="81410-178">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="81410-179">Zie de sectie registratie sleutel hieronder voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="81410-179">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="81410-180">In het Power shell-ISE start (<kbd>F5</kbd>) het volgende configuratie script (opgenomen in de map van de **xPSDesiredStateConfiguration** -module als `Sample_xDscWebServiceRegistration.ps1`).</span><span class="sxs-lookup"><span data-stu-id="81410-180">In the PowerShell ISE, start (<kbd>F5</kbd>) the following configuration script (included in the folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`) .</span></span> <span data-ttu-id="81410-181">Met dit script wordt de pull-server ingesteld.</span><span class="sxs-lookup"><span data-stu-id="81410-181">This script sets up the pull server.</span></span>

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

1. <span data-ttu-id="81410-182">Voer de configuratie uit, waarbij de vinger afdruk van het SSL-certificaat wordt door gegeven als de para meter **certificateThumbPrint** en een GUID-registratie sleutel als de para meter **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="81410-182">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="81410-183">Registratie sleutel</span><span class="sxs-lookup"><span data-stu-id="81410-183">Registration Key</span></span>

<span data-ttu-id="81410-184">Als u client knooppunten wilt toestaan om te registreren bij de server, zodat ze configuratie namen kunnen gebruiken in plaats van een configuratie-ID, wordt een registratie sleutel die is gemaakt met de bovenstaande configuratie opgeslagen in een bestand met de naam `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="81410-184">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="81410-185">De registratie sleutel functioneert als een gedeeld geheim dat wordt gebruikt tijdens de eerste registratie door de client met de pull-server.</span><span class="sxs-lookup"><span data-stu-id="81410-185">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="81410-186">De client genereert een zelfondertekend certificaat dat wordt gebruikt om een unieke verificatie uit te dienen bij de pull-server zodra de registratie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="81410-186">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="81410-187">De vinger afdruk van dit certificaat wordt lokaal opgeslagen en gekoppeld aan de URL van de pull-server.</span><span class="sxs-lookup"><span data-stu-id="81410-187">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="81410-188">Registratie sleutels worden niet ondersteund in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="81410-188">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="81410-189">Als u een knoop punt wilt configureren voor verificatie met de pull-server, moet de registratie sleutel zich in de-configuratie voor elk doel knooppunt bevindt dat wordt geregistreerd bij deze pull-server.</span><span class="sxs-lookup"><span data-stu-id="81410-189">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="81410-190">Houd er rekening mee dat de **RegistrationKey** in de onderstaande meta configuratie wordt verwijderd nadat de doel computer is geregistreerd en dat de waarde moet overeenkomen met de waarde die is opgeslagen in het `RegistrationKeys.txt` bestand op de pull-server (' 140a952b-b9d6-406b-b416-e0f759c9c0e4 ' voor dit voor beeld).</span><span class="sxs-lookup"><span data-stu-id="81410-190">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="81410-191">De registratie sleutel waarde altijd veilig behandelen, omdat een doel machine kan worden geregistreerd bij de pull-server.</span><span class="sxs-lookup"><span data-stu-id="81410-191">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> <span data-ttu-id="81410-192">Met de sectie **ReportServerWeb** kunnen rapport gegevens naar de pull-server worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="81410-192">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="81410-193">Het ontbreken van de eigenschap **ConfigurationID** in het meta configuratie bestand betekent impliciet dat de pull-server de v2-versie van het pull-server protocol ondersteunt, zodat er een eerste registratie nodig is.</span><span class="sxs-lookup"><span data-stu-id="81410-193">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span> <span data-ttu-id="81410-194">De aanwezigheid van een **ConfigurationID** betekent echter wel dat de V1-versie van het pull-server protocol wordt gebruikt en dat er geen registratie verwerking is.</span><span class="sxs-lookup"><span data-stu-id="81410-194">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="81410-195">In een PUSH scenario bestaat er een fout in de huidige release waardoor het nodig is om een eigenschap ConfigurationID te definiëren in het meta configuratie bestand voor knoop punten die nooit zijn geregistreerd bij een pull-server.</span><span class="sxs-lookup"><span data-stu-id="81410-195">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="81410-196">Hiermee wordt het v1 pull server-protocol geforceerd en kunnen er geen registratie fout berichten worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="81410-196">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="81410-197">Configuraties en resources plaatsen</span><span class="sxs-lookup"><span data-stu-id="81410-197">Placing configurations and resources</span></span>

<span data-ttu-id="81410-198">Nadat de installatie van de pull-server is voltooid, worden in de mappen die zijn gedefinieerd door de eigenschappen **ConfigurationPath** en **para modulepath in** in de configuratie van de pull-server, de modules en configuraties geplaatst die beschikbaar zijn voor doel knooppunten die kunnen worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="81410-198">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span> <span data-ttu-id="81410-199">Deze bestanden moeten een specifieke indeling hebben zodat de pull-server deze op de juiste wijze kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="81410-199">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="81410-200">Pakket indeling voor DSC-resource module</span><span class="sxs-lookup"><span data-stu-id="81410-200">DSC resource module package format</span></span>

<span data-ttu-id="81410-201">Elke resource module moet een gezipte en een naam hebben volgens het volgende patroon `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="81410-201">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="81410-202">Een module met de naam **xWebAdminstration** met een module versie van 3.1.2.0 krijgt bijvoorbeeld de naam `xWebAdministration_3.1.2.0.zip`.</span><span class="sxs-lookup"><span data-stu-id="81410-202">For example, a module named **xWebAdminstration** with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span> <span data-ttu-id="81410-203">Elke versie van een module moet zich in één ZIP-bestand bevinden.</span><span class="sxs-lookup"><span data-stu-id="81410-203">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="81410-204">Omdat er slechts één versie van een resource in elk zip-bestand is, wordt de module-indeling die is toegevoegd in WMF 5,0 met ondersteuning voor meerdere module versies in één map niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="81410-204">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span> <span data-ttu-id="81410-205">Dit betekent dat voordat u DSC-resource modules inpakt voor gebruik met een pull-server, een kleine wijziging in de directory structuur moet worden aangebracht.</span><span class="sxs-lookup"><span data-stu-id="81410-205">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span> <span data-ttu-id="81410-206">De standaard indeling van modules met DSC-resource in WMF 5,0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="81410-206">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="81410-207">Voordat u de pull-server inpakt, verwijdert u de map **{module versie}** zodat het pad wordt `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="81410-207">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="81410-208">Ga met deze wijziging naar de map die hierboven is beschreven en plaats deze zip-bestanden in de map **para modulepath in** .</span><span class="sxs-lookup"><span data-stu-id="81410-208">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="81410-209">Gebruik `New-DscChecksum {module zip file}` om een controlesom bestand te maken voor de zojuist toegevoegde module.</span><span class="sxs-lookup"><span data-stu-id="81410-209">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="81410-210">MOF-indeling voor configuratie</span><span class="sxs-lookup"><span data-stu-id="81410-210">Configuration MOF format</span></span>

<span data-ttu-id="81410-211">Een configuratie-MOF-bestand moet worden gekoppeld aan een controlesom bestand zodat een LCM op een doel knooppunt de configuratie kan valideren.</span><span class="sxs-lookup"><span data-stu-id="81410-211">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span> <span data-ttu-id="81410-212">Als u een controlesom wilt maken, roept u de cmdlet [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) aan.</span><span class="sxs-lookup"><span data-stu-id="81410-212">To create a checksum, call the [New-DscChecksum](/reference/6/PSDesiredStateConfiguration/New-DSCCheckSum.md) cmdlet.</span></span> <span data-ttu-id="81410-213">De cmdlet neemt een para meter **Path** op die de map specificeert waarin de configuratie-MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="81410-213">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="81410-214">De cmdlet maakt een controlesom bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` de naam is van het MOF-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="81410-214">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span> <span data-ttu-id="81410-215">Als er meer dan één configuratie-MOF-bestanden in de opgegeven map zijn, wordt er een controlesom gemaakt voor elke configuratie in de map.</span><span class="sxs-lookup"><span data-stu-id="81410-215">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span> <span data-ttu-id="81410-216">Plaats de MOF-bestanden en de bijbehorende controlesom bestanden in de map **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="81410-216">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="81410-217">Als u het MOF-configuratie bestand op een wille keurige manier wijzigt, moet u het controlesom bestand ook opnieuw maken.</span><span class="sxs-lookup"><span data-stu-id="81410-217">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="81410-218">Hulpprogram ma's</span><span class="sxs-lookup"><span data-stu-id="81410-218">Tooling</span></span>

<span data-ttu-id="81410-219">De volgende hulpprogram ma's zijn opgenomen in de meest recente versie van de xPSDesiredStateConfiguration-module, zodat het instellen, valideren en beheren van de pull-server eenvoudiger wordt.</span><span class="sxs-lookup"><span data-stu-id="81410-219">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="81410-220">Een module die u helpt bij het inpakken van DSC-resource modules en configuratie bestanden die op de pull-server kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="81410-220">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="81410-221">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span><span class="sxs-lookup"><span data-stu-id="81410-221">[PublishModulesAndMofsToPullServer.psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).</span></span>
   <span data-ttu-id="81410-222">Voor beelden:</span><span class="sxs-lookup"><span data-stu-id="81410-222">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="81410-223">Een script dat de pull-server valideert, is op de juiste wijze geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="81410-223">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="81410-224">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span><span class="sxs-lookup"><span data-stu-id="81410-224">[PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="81410-225">Community-oplossingen voor pull-service</span><span class="sxs-lookup"><span data-stu-id="81410-225">Community Solutions for Pull Service</span></span>

<span data-ttu-id="81410-226">De DSC-Community heeft meerdere oplossingen ontworpen om het pull-service protocol te implementeren.</span><span class="sxs-lookup"><span data-stu-id="81410-226">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span> <span data-ttu-id="81410-227">Voor on-premises omgevingen bieden deze pull-service mogelijkheden en een kans om een bijdrage te leveren aan de community met incrementele uitbrei dingen.</span><span class="sxs-lookup"><span data-stu-id="81410-227">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="81410-228">Tug</span><span class="sxs-lookup"><span data-stu-id="81410-228">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="81410-229">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="81410-229">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="81410-230">Pull-client configuratie</span><span class="sxs-lookup"><span data-stu-id="81410-230">Pull client configuration</span></span>

<span data-ttu-id="81410-231">In de volgende onderwerpen wordt beschreven hoe u pull-clients in detail instelt:</span><span class="sxs-lookup"><span data-stu-id="81410-231">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="81410-232">Een DSC-pull-client instellen met behulp van een configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="81410-232">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="81410-233">Een DSC-pull-client instellen met behulp van configuratie namen</span><span class="sxs-lookup"><span data-stu-id="81410-233">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="81410-234">Gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="81410-234">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="81410-235">Zie ook</span><span class="sxs-lookup"><span data-stu-id="81410-235">See also</span></span>

- [<span data-ttu-id="81410-236">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="81410-236">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="81410-237">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="81410-237">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="81410-238">Een DSC-rapportserver gebruiken</span><span class="sxs-lookup"><span data-stu-id="81410-238">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="81410-239">[[MS-DSCPM]: gewenst status configuratie pull model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span><span class="sxs-lookup"><span data-stu-id="81410-239">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://docs.microsoft.com/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)</span></span>
- <span data-ttu-id="81410-240">[[MS-DSCPM]: desired state Configuration pull model protocol errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span><span class="sxs-lookup"><span data-stu-id="81410-240">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://docs.microsoft.com/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)</span></span>
