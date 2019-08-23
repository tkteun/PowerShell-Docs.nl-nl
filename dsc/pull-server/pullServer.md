---
ms.date: 03/04/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC-pull-service
ms.openlocfilehash: 865eae5813e0c7b656a4158f0b1350e60f1e3291
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986541"
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="5874c-103">Pull-service desired state Configuration</span><span class="sxs-lookup"><span data-stu-id="5874c-103">Desired State Configuration Pull Service</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5874c-104">De pull-server (Windows *-functie DSC-service*) is een ondersteund onderdeel van Windows Server, maar er zijn geen plannen om nieuwe functies of mogelijkheden aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="5874c-104">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="5874c-105">Het wordt aangeraden om te beginnen met het overschakelen van beheerde clients naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies die verder gaan dan pull server op Windows Server) [](pullserver.md#community-solutions-for-pull-service)of een van de hieronder vermelde Community-oplossingen.</span><span class="sxs-lookup"><span data-stu-id="5874c-105">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="5874c-106">Lokale Configuration Manager kunnen centraal worden beheerd door een pull-service oplossing.</span><span class="sxs-lookup"><span data-stu-id="5874c-106">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="5874c-107">Wanneer u deze methode gebruikt, wordt het knoop punt dat wordt beheerd, geregistreerd bij een service en een configuratie toegewezen in de instellingen van de LCM.</span><span class="sxs-lookup"><span data-stu-id="5874c-107">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="5874c-108">De configuratie en alle DSC-resources die nodig zijn als afhankelijkheden voor de configuratie, worden gedownload naar de computer en gebruikt door LCM voor het beheren van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="5874c-108">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="5874c-109">Informatie over de status van de computer die wordt beheerd, wordt geüpload naar de service voor rapportage.</span><span class="sxs-lookup"><span data-stu-id="5874c-109">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="5874c-110">Dit concept wordt ' pull-service ' genoemd.</span><span class="sxs-lookup"><span data-stu-id="5874c-110">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="5874c-111">De huidige opties voor de pull-service zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="5874c-111">The current options for pull service include:</span></span>

- <span data-ttu-id="5874c-112">Azure Automation desired state Configuration-service</span><span class="sxs-lookup"><span data-stu-id="5874c-112">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="5874c-113">Een pull-service die wordt uitgevoerd op Windows Server</span><span class="sxs-lookup"><span data-stu-id="5874c-113">A pull service running on Windows Server</span></span>
- <span data-ttu-id="5874c-114">Door de Community beheerde open-source-oplossingen</span><span class="sxs-lookup"><span data-stu-id="5874c-114">Community maintained open-source solutions</span></span>
- <span data-ttu-id="5874c-115">Een SMB-share</span><span class="sxs-lookup"><span data-stu-id="5874c-115">An SMB share</span></span>

<span data-ttu-id="5874c-116">**De aanbevolen oplossing**en de optie met de meeste beschik bare functies is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="5874c-116">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="5874c-117">Met de Azure-service kunt u knoop punten on-premises beheren in particuliere data centers of in open bare Clouds, zoals Azure en AWS.</span><span class="sxs-lookup"><span data-stu-id="5874c-117">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="5874c-118">Voor particuliere omgevingen waarbij servers niet rechtstreeks verbinding kunnen maken met internet, kunt u overwegen om uitgaand verkeer alleen te beperken tot het gepubliceerde Azure IP-bereik (Zie [IP-bereiken van Azure-data centers](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="5874c-118">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="5874c-119">De functies van de online service die momenteel niet beschikbaar zijn in de pull-service op Windows Server zijn:</span><span class="sxs-lookup"><span data-stu-id="5874c-119">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>

- <span data-ttu-id="5874c-120">Alle gegevens worden versleuteld tijdens de overdracht en in rust</span><span class="sxs-lookup"><span data-stu-id="5874c-120">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="5874c-121">Client certificaten worden automatisch gemaakt en beheerd</span><span class="sxs-lookup"><span data-stu-id="5874c-121">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="5874c-122">Archief geheimen voor het centraal beheren van [wacht woorden/referenties](/azure/automation/automation-credentials)of [variabelen](/azure/automation/automation-variables) zoals server namen of verbindings reeksen</span><span class="sxs-lookup"><span data-stu-id="5874c-122">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="5874c-123">De configuratie van het knoop punt [LCM](../managing-nodes/metaConfig.md#basic-settings) centraal beheren</span><span class="sxs-lookup"><span data-stu-id="5874c-123">Centrally manage node [LCM configuration](../managing-nodes/metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="5874c-124">Configuraties centraal toewijzen aan client knooppunten</span><span class="sxs-lookup"><span data-stu-id="5874c-124">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="5874c-125">Wijzigingen in de configuratie van ' Canarische groups ' vrijgeven voordat de productie wordt bereikt</span><span class="sxs-lookup"><span data-stu-id="5874c-125">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="5874c-126">Grafische rapportage</span><span class="sxs-lookup"><span data-stu-id="5874c-126">Graphical reporting</span></span>
  - <span data-ttu-id="5874c-127">Status Details op DSC-resource niveau granulatie</span><span class="sxs-lookup"><span data-stu-id="5874c-127">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="5874c-128">Uitgebreide fout berichten van client computers voor het oplossen van problemen</span><span class="sxs-lookup"><span data-stu-id="5874c-128">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="5874c-129">[Integratie met Azure log Analytics](/azure/automation/automation-dsc-diagnostics) voor waarschuwingen, geautomatiseerde taken, Android/IOS-app voor rapportage en waarschuwingen</span><span class="sxs-lookup"><span data-stu-id="5874c-129">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="5874c-130">DSC-pull-service in Windows Server</span><span class="sxs-lookup"><span data-stu-id="5874c-130">DSC pull service in Windows Server</span></span>

<span data-ttu-id="5874c-131">Het is mogelijk om een pull-service te configureren om te worden uitgevoerd op Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5874c-131">It is possible to configure a pull service to run on Windows Server.</span></span>
<span data-ttu-id="5874c-132">U wordt aangeraden dat de pull-service oplossing die is opgenomen in Windows Server, alleen mogelijkheden heeft voor het opslaan van configuraties/modules voor het downloaden en vastleggen van rapport gegevens in de data base.</span><span class="sxs-lookup"><span data-stu-id="5874c-132">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="5874c-133">Het bevat niet veel van de mogelijkheden die de service in Azure biedt en is dus geen goed hulp middel om te evalueren hoe de service zou worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5874c-133">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="5874c-134">De pull-service in Windows Server is een webservice in IIS die gebruikmaakt van een OData-interface om DSC-configuratie bestanden beschikbaar te maken voor doel knooppunten wanneer deze knoop punten hen vragen.</span><span class="sxs-lookup"><span data-stu-id="5874c-134">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="5874c-135">Vereisten voor het gebruik van een pull-server:</span><span class="sxs-lookup"><span data-stu-id="5874c-135">Requirements for using a pull server:</span></span>

- <span data-ttu-id="5874c-136">Een server met:</span><span class="sxs-lookup"><span data-stu-id="5874c-136">A server running:</span></span>
  - <span data-ttu-id="5874c-137">WMF/Power Shell 4,0 of hoger</span><span class="sxs-lookup"><span data-stu-id="5874c-137">WMF/PowerShell 4.0 or greater</span></span>
  - <span data-ttu-id="5874c-138">IIS-serverrol</span><span class="sxs-lookup"><span data-stu-id="5874c-138">IIS server role</span></span>
  - <span data-ttu-id="5874c-139">DSC Service</span><span class="sxs-lookup"><span data-stu-id="5874c-139">DSC Service</span></span>
- <span data-ttu-id="5874c-140">In het ideale geval wordt een certificaat gegenereerd voor het beveiligen van referenties die worden door gegeven aan de lokale Configuration Manager (LCM) op doel knooppunten</span><span class="sxs-lookup"><span data-stu-id="5874c-140">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="5874c-141">De beste manier om Windows Server te configureren voor het hosten van pull-service is het gebruik van een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="5874c-141">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="5874c-142">Hieronder vindt u een voorbeeld script.</span><span class="sxs-lookup"><span data-stu-id="5874c-142">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="5874c-143">Ondersteunde database systemen</span><span class="sxs-lookup"><span data-stu-id="5874c-143">Supported database systems</span></span>

|<span data-ttu-id="5874c-144">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="5874c-144">WMF 4.0</span></span>   |<span data-ttu-id="5874c-145">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="5874c-145">WMF 5.0</span></span>  |<span data-ttu-id="5874c-146">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="5874c-146">WMF 5.1</span></span> |<span data-ttu-id="5874c-147">WMF 5,1 (Windows Server Insider preview 17090)</span><span class="sxs-lookup"><span data-stu-id="5874c-147">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="5874c-148">EXTENSIE</span><span class="sxs-lookup"><span data-stu-id="5874c-148">MDB</span></span>     |<span data-ttu-id="5874c-149">ESENT (standaard), MDB</span><span class="sxs-lookup"><span data-stu-id="5874c-149">ESENT (Default), MDB</span></span> |<span data-ttu-id="5874c-150">ESENT (standaard), MDB</span><span class="sxs-lookup"><span data-stu-id="5874c-150">ESENT (Default), MDB</span></span>|<span data-ttu-id="5874c-151">ESENT (standaard), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="5874c-151">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="5874c-152">Vanaf release 17090 van [Windows Server Insider preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver)is SQL Server een ondersteunde optie voor de pull-service (Windows-functie *DSC-service*).</span><span class="sxs-lookup"><span data-stu-id="5874c-152">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span> <span data-ttu-id="5874c-153">Dit biedt een nieuwe optie voor het schalen van grote DSC-omgevingen die niet zijn gemigreerd naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="5874c-153">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> [!NOTE]
> <span data-ttu-id="5874c-154">SQL Server ondersteuning wordt niet toegevoegd aan eerdere versies van WMF 5,1 (of eerder) en is alleen beschikbaar op Windows Server-versies die groter zijn dan of gelijk zijn aan 17090.</span><span class="sxs-lookup"><span data-stu-id="5874c-154">SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="5874c-155">Als u de pull-server wilt configureren voor het gebruik van `$true` SQL Server, stelt u **SqlProvider** in op en **SqlConnectionString** naar een geldige SQL Server verbindings reeks.</span><span class="sxs-lookup"><span data-stu-id="5874c-155">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span> <span data-ttu-id="5874c-156">Zie voor meer informatie [SqlClient-verbindings reeksen](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="5874c-156">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="5874c-157">Voor een voor beeld van SQL Server configuratie met **xDscWebService**, lees dan eerst [met behulp van de xDscWebService-resource](#using-the-xdscwebservice-resource) en controleer vervolgens [Sample_xDscWebServiceRegistration_UseSQLProvider. ps1 op github](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="5874c-157">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="5874c-158">De xDscWebService-Resource gebruiken</span><span class="sxs-lookup"><span data-stu-id="5874c-158">Using the xDscWebService resource</span></span>

<span data-ttu-id="5874c-159">De eenvoudigste manier om een webpull-server in te stellen, is door gebruik te maken van de **xDscWebService** -resource die is opgenomen in de **xPSDesiredStateConfiguration** -module.</span><span class="sxs-lookup"><span data-stu-id="5874c-159">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="5874c-160">In de volgende stappen wordt uitgelegd hoe u de bron gebruikt in een configuratie waarmee de webservice wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="5874c-160">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="5874c-161">Roep de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) aan om de **xPSDesiredStateConfiguration** -module te installeren.</span><span class="sxs-lookup"><span data-stu-id="5874c-161">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span>
   > [!NOTE]
   > <span data-ttu-id="5874c-162">**Install-module** is opgenomen in de **PowerShellGet** -module, die is opgenomen in Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="5874c-162">**Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="5874c-163">U kunt de **PowerShellGet** -module voor power Shell 3,0 en 4,0 downloaden van [Package Management Power shell-modules preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="5874c-163">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
2. <span data-ttu-id="5874c-164">Een SSL-certificaat voor de DSC-pull-server ophalen van een vertrouwde certificerings instantie, binnen uw organisatie of een open bare instantie.</span><span class="sxs-lookup"><span data-stu-id="5874c-164">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="5874c-165">Het certificaat dat is ontvangen van de certificerings instantie is meestal in de PFX-indeling.</span><span class="sxs-lookup"><span data-stu-id="5874c-165">The certificate received from the authority is usually in the PFX format.</span></span>
3. <span data-ttu-id="5874c-166">Installeer het certificaat op het knoop punt dat de DSC-pull-server wordt op de standaard locatie, dat `CERT:\LocalMachine\My`wil zeggen.</span><span class="sxs-lookup"><span data-stu-id="5874c-166">Install the certificate on the node that will become the DSC Pull server in the default location, which should be `CERT:\LocalMachine\My`.</span></span>
   - <span data-ttu-id="5874c-167">Noteer de vinger afdruk van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="5874c-167">Make a note of the certificate thumbprint.</span></span>
4. <span data-ttu-id="5874c-168">Selecteer een GUID die moet worden gebruikt als de registratie sleutel.</span><span class="sxs-lookup"><span data-stu-id="5874c-168">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="5874c-169">Als u een rapport wilt genereren met Power shell, voert u het volgende in bij `[guid]::newGuid()` de `New-Guid`PS-prompt en drukt u op ENTER: of.</span><span class="sxs-lookup"><span data-stu-id="5874c-169">To generate one using PowerShell enter the following at the PS prompt and press enter: `[guid]::newGuid()` or `New-Guid`.</span></span> <span data-ttu-id="5874c-170">Deze sleutel wordt gebruikt door client knooppunten als een gedeelde sleutel voor verificatie tijdens de registratie.</span><span class="sxs-lookup"><span data-stu-id="5874c-170">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="5874c-171">Zie de sectie registratie sleutel hieronder voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="5874c-171">For more information, see the Registration Key section below.</span></span>
5. <span data-ttu-id="5874c-172">Begin in het Power shell-ISE (F5) het volgende configuratie script (dat is opgenomen in de map met voor beelden `Sample_xDscWebServiceRegistration.ps1`van de module xPSDesiredStateConfiguration als).</span><span class="sxs-lookup"><span data-stu-id="5874c-172">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the **xPSDesiredStateConfiguration** module as `Sample_xDscWebServiceRegistration.ps1`).</span></span> <span data-ttu-id="5874c-173">Met dit script wordt de pull-server ingesteld.</span><span class="sxs-lookup"><span data-stu-id="5874c-173">This script sets up the pull server.</span></span>

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

6. <span data-ttu-id="5874c-174">Voer de configuratie uit, waarbij de vinger afdruk van het SSL-certificaat wordt door gegeven als de para meter **certificateThumbPrint** en een GUID-registratie sleutel als de para meter **RegistrationKey** :</span><span class="sxs-lookup"><span data-stu-id="5874c-174">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a><span data-ttu-id="5874c-175">Registratie sleutel</span><span class="sxs-lookup"><span data-stu-id="5874c-175">Registration Key</span></span>

<span data-ttu-id="5874c-176">Als u client knooppunten wilt toestaan om te registreren bij de server, zodat ze configuratie namen kunnen gebruiken in plaats van een configuratie-ID, wordt een registratie sleutel die is gemaakt met de bovenstaande configuratie `RegistrationKeys.txt` opgeslagen `C:\Program Files\WindowsPowerShell\DscService`in een bestand met de naam in.</span><span class="sxs-lookup"><span data-stu-id="5874c-176">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="5874c-177">De registratie sleutel functioneert als een gedeeld geheim dat wordt gebruikt tijdens de eerste registratie door de client met de pull-server.</span><span class="sxs-lookup"><span data-stu-id="5874c-177">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="5874c-178">De client genereert een zelfondertekend certificaat dat wordt gebruikt om een unieke verificatie uit te dienen bij de pull-server zodra de registratie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="5874c-178">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="5874c-179">De vinger afdruk van dit certificaat wordt lokaal opgeslagen en gekoppeld aan de URL van de pull-server.</span><span class="sxs-lookup"><span data-stu-id="5874c-179">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>

> [!NOTE]
> <span data-ttu-id="5874c-180">Registratie sleutels worden niet ondersteund in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="5874c-180">Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="5874c-181">Als u een knoop punt wilt configureren voor verificatie met de pull-server, moet de registratie sleutel zich in de-configuratie voor elk doel knooppunt bevindt dat wordt geregistreerd bij deze pull-server.</span><span class="sxs-lookup"><span data-stu-id="5874c-181">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="5874c-182">Houd er rekening mee dat de **RegistrationKey** in de onderstaande meta configuratie wordt verwijderd nadat de doel computer is geregistreerd en dat de waarde moet overeenkomen met de waarde `RegistrationKeys.txt` die is opgeslagen in het bestand op de pull-server (' 140a952b-b9d6-406b-b416-e0f759c9c0e4 ' voor dit voor beeld).</span><span class="sxs-lookup"><span data-stu-id="5874c-182">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value must match the value stored in the `RegistrationKeys.txt` file on the pull server ('140a952b-b9d6-406b-b416-e0f759c9c0e4' for this example).</span></span> <span data-ttu-id="5874c-183">De registratie sleutel waarde altijd veilig behandelen, omdat een doel machine kan worden geregistreerd bij de pull-server.</span><span class="sxs-lookup"><span data-stu-id="5874c-183">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

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
> <span data-ttu-id="5874c-184">Met de sectie **ReportServerWeb** kunnen rapport gegevens naar de pull-server worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="5874c-184">The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="5874c-185">Het ontbreken van de eigenschap **ConfigurationID** in het meta configuratie bestand betekent impliciet dat de pull-server de v2-versie van het pull-server protocol ondersteunt, zodat er een eerste registratie nodig is.</span><span class="sxs-lookup"><span data-stu-id="5874c-185">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="5874c-186">De aanwezigheid van een **ConfigurationID** betekent echter wel dat de V1-versie van het pull-server protocol wordt gebruikt en dat er geen registratie verwerking is.</span><span class="sxs-lookup"><span data-stu-id="5874c-186">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

> [!NOTE]
> <span data-ttu-id="5874c-187">In een PUSH scenario bestaat er een fout in de huidige release waardoor het nodig is om een eigenschap ConfigurationID te definiëren in het meta configuratie bestand voor knoop punten die nooit zijn geregistreerd bij een pull-server.</span><span class="sxs-lookup"><span data-stu-id="5874c-187">In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="5874c-188">Hiermee wordt het v1 pull server-protocol geforceerd en kunnen er geen registratie fout berichten worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="5874c-188">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="5874c-189">Configuraties en resources plaatsen</span><span class="sxs-lookup"><span data-stu-id="5874c-189">Placing configurations and resources</span></span>

<span data-ttu-id="5874c-190">Nadat de installatie van de pull-server is voltooid, worden in de mappen die zijn gedefinieerd door de eigenschappen **ConfigurationPath** en **para modulepath in** in de configuratie van de pull-server, de modules en configuraties geplaatst die beschikbaar zijn voor doel knooppunten die kunnen worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="5874c-190">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="5874c-191">Deze bestanden moeten een specifieke indeling hebben zodat de pull-server deze op de juiste wijze kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="5874c-191">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="5874c-192">Pakket indeling voor DSC-resource module</span><span class="sxs-lookup"><span data-stu-id="5874c-192">DSC resource module package format</span></span>

<span data-ttu-id="5874c-193">Elke resource module moet een gezipte en een naam hebben op basis van `{Module Name}_{Module Version}.zip`het volgende patroon.</span><span class="sxs-lookup"><span data-stu-id="5874c-193">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>

<span data-ttu-id="5874c-194">Een module met de naam xWebAdminstration met een module versie van 3.1.2.0 zou bijvoorbeeld een naam `xWebAdministration_3.1.2.0.zip`hebben.</span><span class="sxs-lookup"><span data-stu-id="5874c-194">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named `xWebAdministration_3.1.2.0.zip`.</span></span>
<span data-ttu-id="5874c-195">Elke versie van een module moet zich in één ZIP-bestand bevinden.</span><span class="sxs-lookup"><span data-stu-id="5874c-195">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="5874c-196">Omdat er slechts één versie van een resource in elk zip-bestand is, wordt de module-indeling die is toegevoegd in WMF 5,0 met ondersteuning voor meerdere module versies in één map niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5874c-196">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="5874c-197">Dit betekent dat voordat u DSC-resource modules inpakt voor gebruik met een pull-server, een kleine wijziging in de directory structuur moet worden aangebracht.</span><span class="sxs-lookup"><span data-stu-id="5874c-197">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="5874c-198">De standaard indeling van modules met DSC-resource in WMF 5,0 `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`is.</span><span class="sxs-lookup"><span data-stu-id="5874c-198">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="5874c-199">Voordat u de pull-server inpakt, verwijdert u de map **{module versie}** zodat het `{Module Folder}\DscResources\{DSC Resource Folder}\`pad wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="5874c-199">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span>
<span data-ttu-id="5874c-200">Ga met deze wijziging naar de map die hierboven is beschreven en plaats deze zip-bestanden in de map **para modulepath in** .</span><span class="sxs-lookup"><span data-stu-id="5874c-200">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="5874c-201">Gebruik `New-DscChecksum {module zip file}` om een controlesom bestand te maken voor de zojuist toegevoegde module.</span><span class="sxs-lookup"><span data-stu-id="5874c-201">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="5874c-202">MOF-indeling voor configuratie</span><span class="sxs-lookup"><span data-stu-id="5874c-202">Configuration MOF format</span></span>

<span data-ttu-id="5874c-203">Een configuratie-MOF-bestand moet worden gekoppeld aan een controlesom bestand zodat een LCM op een doel knooppunt de configuratie kan valideren.</span><span class="sxs-lookup"><span data-stu-id="5874c-203">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="5874c-204">Als u een controlesom wilt maken, roept u de cmdlet [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) aan.</span><span class="sxs-lookup"><span data-stu-id="5874c-204">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="5874c-205">De cmdlet neemt een para meter **Path** op die de map specificeert waarin de configuratie-MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="5874c-205">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="5874c-206">De cmdlet maakt een controlesom bestand `ConfigurationMOFName.mof.checksum`met de naam, waarbij `ConfigurationMOFName` de naam is van het MOF-configuratie bestand.</span><span class="sxs-lookup"><span data-stu-id="5874c-206">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="5874c-207">Als er meer dan één configuratie-MOF-bestanden in de opgegeven map zijn, wordt er een controlesom gemaakt voor elke configuratie in de map.</span><span class="sxs-lookup"><span data-stu-id="5874c-207">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="5874c-208">Plaats de MOF-bestanden en de bijbehorende controlesom bestanden in de map **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="5874c-208">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

> [!NOTE]
> <span data-ttu-id="5874c-209">Als u het MOF-configuratie bestand op een wille keurige manier wijzigt, moet u het controlesom bestand ook opnieuw maken.</span><span class="sxs-lookup"><span data-stu-id="5874c-209">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="5874c-210">Hulpprogram ma's</span><span class="sxs-lookup"><span data-stu-id="5874c-210">Tooling</span></span>

<span data-ttu-id="5874c-211">De volgende hulpprogram ma's zijn opgenomen in de meest recente versie van de xPSDesiredStateConfiguration-module, zodat het instellen, valideren en beheren van de pull-server eenvoudiger wordt.</span><span class="sxs-lookup"><span data-stu-id="5874c-211">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="5874c-212">Een module die u helpt bij het inpakken van DSC-resource modules en configuratie bestanden die op de pull-server kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5874c-212">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span>
   <span data-ttu-id="5874c-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="5874c-213">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span>
   <span data-ttu-id="5874c-214">Voor beelden:</span><span class="sxs-lookup"><span data-stu-id="5874c-214">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="5874c-215">Een script dat de pull-server valideert, is op de juiste wijze geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="5874c-215">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="5874c-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="5874c-216">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="5874c-217">Community-oplossingen voor pull-service</span><span class="sxs-lookup"><span data-stu-id="5874c-217">Community Solutions for Pull Service</span></span>

<span data-ttu-id="5874c-218">De DSC-Community heeft meerdere oplossingen ontworpen om het pull-service protocol te implementeren.</span><span class="sxs-lookup"><span data-stu-id="5874c-218">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="5874c-219">Voor on-premises omgevingen bieden deze pull-service mogelijkheden en een kans om een bijdrage te leveren aan de community met incrementele uitbrei dingen.</span><span class="sxs-lookup"><span data-stu-id="5874c-219">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="5874c-220">Tug</span><span class="sxs-lookup"><span data-stu-id="5874c-220">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="5874c-221">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="5874c-221">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="5874c-222">Pull-client configuratie</span><span class="sxs-lookup"><span data-stu-id="5874c-222">Pull client configuration</span></span>

<span data-ttu-id="5874c-223">In de volgende onderwerpen wordt beschreven hoe u pull-clients in detail instelt:</span><span class="sxs-lookup"><span data-stu-id="5874c-223">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="5874c-224">Een DSC-pull-client instellen met behulp van een configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="5874c-224">Set up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="5874c-225">Een DSC-pull-client instellen met behulp van configuratie namen</span><span class="sxs-lookup"><span data-stu-id="5874c-225">Set up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="5874c-226">Gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="5874c-226">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="5874c-227">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5874c-227">See also</span></span>

- [<span data-ttu-id="5874c-228">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="5874c-228">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="5874c-229">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="5874c-229">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="5874c-230">Een DSC-rapportserver gebruiken</span><span class="sxs-lookup"><span data-stu-id="5874c-230">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="5874c-231">[[MS-DSCPM]: Pull model protocol voor desired state Configuration](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="5874c-231">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="5874c-232">[[MS-DSCPM]: Desired state configuratie pull model protocol errata](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="5874c-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>
