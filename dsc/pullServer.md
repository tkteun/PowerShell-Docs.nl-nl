---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-pull-service
ms.openlocfilehash: 075487be68de82074750e5344a24d6d4c2f2bec5
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2018
---
# <a name="desired-state-configuration-pull-service"></a><span data-ttu-id="acc89-103">Pull-desired State Configuration-Service</span><span class="sxs-lookup"><span data-stu-id="acc89-103">Desired State Configuration Pull Service</span></span>

> <span data-ttu-id="acc89-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="acc89-104">Applies To: Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="acc89-105">De Pull-Server (Windows-onderdeel *DSC-Service*) is een ondersteunde onderdeel van Windows Server maar er zijn geen plannen om de nieuwe functies en mogelijkheden bieden.</span><span class="sxs-lookup"><span data-stu-id="acc89-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="acc89-106">Het verdient aanbeveling om te beginnen met een overgang clients beheerd [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inclusief functies dan Pull-Server op Windows Server) of een van de community-oplossingen vermeld [hier](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="acc89-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="acc89-107">Lokale Configuration Manager kunnen centraal worden beheerd door een oplossing voor Pull-Service.</span><span class="sxs-lookup"><span data-stu-id="acc89-107">Local Configuration Manager can be centrally managed by a Pull Service solution.</span></span>
<span data-ttu-id="acc89-108">Wanneer u deze methode gebruikt, wordt het knooppunt dat wordt beheerd geregistreerd bij een service en een configuratie in LCM instellingen toegewezen.</span><span class="sxs-lookup"><span data-stu-id="acc89-108">When using this approach, the node that is being managed is registered with a service and assigned a configuration in LCM settings.</span></span>
<span data-ttu-id="acc89-109">De configuratie en alle benodigde als afhankelijkheden voor de configuratie van de DSC-resources zijn gedownload naar de computer en gebruikt door LCM voor het beheren van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="acc89-109">The configuration and all DSC resources needed as dependencies for the configuration are downloaded to the machine and used by LCM to manage the configuration.</span></span>
<span data-ttu-id="acc89-110">Informatie over de status van de machine wordt beheerd, is geüpload naar de service voor rapportage.</span><span class="sxs-lookup"><span data-stu-id="acc89-110">Information about the state of the machine being managed is uploaded to the service for reporting.</span></span>
<span data-ttu-id="acc89-111">Dit concept wordt aangeduid als 'pull service'.</span><span class="sxs-lookup"><span data-stu-id="acc89-111">This concept is referred to as "pull service."</span></span>

<span data-ttu-id="acc89-112">De huidige opties voor het pull-service zijn onder andere:</span><span class="sxs-lookup"><span data-stu-id="acc89-112">The current options for pull service include:</span></span>

- <span data-ttu-id="acc89-113">Azure Automation gewenst State Configuration-service</span><span class="sxs-lookup"><span data-stu-id="acc89-113">Azure Automation Desired State Configuration service</span></span>
- <span data-ttu-id="acc89-114">Een pull-service op Windows Server</span><span class="sxs-lookup"><span data-stu-id="acc89-114">A pull service running on Windows Server</span></span>
- <span data-ttu-id="acc89-115">Community open source-oplossingen onderhouden</span><span class="sxs-lookup"><span data-stu-id="acc89-115">Community maintained open-source solutions</span></span>
- <span data-ttu-id="acc89-116">Een SMB-share</span><span class="sxs-lookup"><span data-stu-id="acc89-116">An SMB share</span></span>

<span data-ttu-id="acc89-117">**De aanbevolen oplossing**, en de optie met de meeste functies die beschikbaar is, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="acc89-117">**The recommended solution**, and the option with the most features available, is [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

<span data-ttu-id="acc89-118">De Azure-service kunt knooppunten lokale in datacenters persoonlijke of openbare clouds, zoals Azure en AWS beheren.</span><span class="sxs-lookup"><span data-stu-id="acc89-118">The Azure service can manage nodes on-premises in private datacenters, or in public clouds such as Azure and AWS.</span></span>
<span data-ttu-id="acc89-119">Persoonlijke omgevingen waarin servers kunnen niet rechtstreeks verbinding met Internet maken, Beperk uitgaand verkeer naar de gepubliceerde Azure IP-bereik (Zie [Azure Datacenter IP-adresbereiken](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span><span class="sxs-lookup"><span data-stu-id="acc89-119">For private environments where servers cannot directly connect to the Internet, consider limiting outbound traffic to only the published Azure IP range (see [Azure Datacenter IP Ranges](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).</span></span>

<span data-ttu-id="acc89-120">Functies van de online service die momenteel niet beschikbaar in de pull-service op Windows Server zijn:</span><span class="sxs-lookup"><span data-stu-id="acc89-120">Features of the online service that are not currently available in the pull service on Windows Server include:</span></span>
- <span data-ttu-id="acc89-121">Alle gegevens worden versleuteld in rust en onderweg</span><span class="sxs-lookup"><span data-stu-id="acc89-121">All data is encrypted in transit and at rest</span></span>
- <span data-ttu-id="acc89-122">Clientcertificaten worden gemaakt en automatisch beheerd</span><span class="sxs-lookup"><span data-stu-id="acc89-122">Client certificates are created and managed automatically</span></span>
- <span data-ttu-id="acc89-123">Geheimen opslaan voor het centraal beheren van [wachtwoorden/referenties](/azure/automation/automation-credentials), of [variabelen](/azure/automation/automation-variables) zoals servernamen of verbindingsreeksen</span><span class="sxs-lookup"><span data-stu-id="acc89-123">Secrets store for centrally managing [passwords/credentials](/azure/automation/automation-credentials), or [variables](/azure/automation/automation-variables) such as server names or connection strings</span></span>
- <span data-ttu-id="acc89-124">Centraal beheren knooppunt [LCM configuratie](metaConfig.md#basic-settings)</span><span class="sxs-lookup"><span data-stu-id="acc89-124">Centrally manage node [LCM configuration](metaConfig.md#basic-settings)</span></span>
- <span data-ttu-id="acc89-125">Centraal toewijzen configuraties aan client-knooppunten</span><span class="sxs-lookup"><span data-stu-id="acc89-125">Centrally assign configurations to client nodes</span></span>
- <span data-ttu-id="acc89-126">Release-configuratie voor het testen alvorens productie gewijzigd in 'kokospalm groepen'</span><span class="sxs-lookup"><span data-stu-id="acc89-126">Release configuration changes to "canary groups" for testing before reaching production</span></span>
- <span data-ttu-id="acc89-127">Grafische rapportage</span><span class="sxs-lookup"><span data-stu-id="acc89-127">Graphical reporting</span></span>
  - <span data-ttu-id="acc89-128">Details van de status op het niveau van de resource DSC van granulatie</span><span class="sxs-lookup"><span data-stu-id="acc89-128">Status detail at the DSC resource level of granularity</span></span>
  - <span data-ttu-id="acc89-129">Uitgebreide foutberichten van clientcomputers voor probleemoplossing</span><span class="sxs-lookup"><span data-stu-id="acc89-129">Verbose error messages from client machines for troubleshooting</span></span>
- <span data-ttu-id="acc89-130">[Integratie met Azure-logboekanalyse](/azure/automation/automation-dsc-diagnostics) voor waarschuwingen, geautomatiseerde taken Android/iOS-app voor rapportage en waarschuwingen</span><span class="sxs-lookup"><span data-stu-id="acc89-130">[Integration with Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) for alerting, automated tasks, Android/iOS app for reporting and alerting</span></span>

## <a name="dsc-pull-service-in-windows-server"></a><span data-ttu-id="acc89-131">DSC-pull-service in Windows Server</span><span class="sxs-lookup"><span data-stu-id="acc89-131">DSC pull service in Windows Server</span></span>

<span data-ttu-id="acc89-132">Het is mogelijk met het configureren van een pull-service uit te voeren op Windows Server.</span><span class="sxs-lookup"><span data-stu-id="acc89-132">It is possible to configuring a pull service to run on Windows Server.</span></span>
<span data-ttu-id="acc89-133">Gewezen dat het pull-serviceoplossing opgenomen in Windows Server alleen mogelijkheden bevat van het opslaan van configuraties/modules voor het downloaden en vastleggen van gegevens in database.</span><span class="sxs-lookup"><span data-stu-id="acc89-133">Be advised that the pull service solution included in Windows Server includes only capabilities of storing configurations/modules for download and capturing report data in to database.</span></span>
<span data-ttu-id="acc89-134">Hierbij worden veel van de mogelijkheden die worden aangeboden door de service in Azure en is dus niet een goede hulpprogramma voor het evalueren van hoe de service moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="acc89-134">It does not include many of the capabilities offered by the service in Azure and so is not a good tool for evaluating how the service would be used.</span></span>

<span data-ttu-id="acc89-135">De pull-service wordt aangeboden op Windows Server is een webservice in IIS die gebruikmaakt van een OData-interface om DSC-configuratiebestanden te doelknooppunten wanneer die knooppunten van deze vragen.</span><span class="sxs-lookup"><span data-stu-id="acc89-135">The pull service offered in Windows Server is a web service in IIS that uses an OData interface to make DSC configuration files available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="acc89-136">Vereisten voor het gebruik van een pull-server:</span><span class="sxs-lookup"><span data-stu-id="acc89-136">Requirements for using a pull server:</span></span>

- <span data-ttu-id="acc89-137">Een server met:</span><span class="sxs-lookup"><span data-stu-id="acc89-137">A server running:</span></span>
  - <span data-ttu-id="acc89-138">WMF/PowerShell 5.0 of hoger</span><span class="sxs-lookup"><span data-stu-id="acc89-138">WMF/PowerShell 5.0 or greater</span></span>
  - <span data-ttu-id="acc89-139">IIS-serverrol</span><span class="sxs-lookup"><span data-stu-id="acc89-139">IIS server role</span></span>
  - <span data-ttu-id="acc89-140">DSC-Service</span><span class="sxs-lookup"><span data-stu-id="acc89-140">DSC Service</span></span>
- <span data-ttu-id="acc89-141">In het ideale geval sommige betekent dat voor het genereren van een certificaat voor het beveiligen van referenties die zijn doorgegeven aan de lokale Configuration Manager (LCM) op de doelknooppunten</span><span class="sxs-lookup"><span data-stu-id="acc89-141">Ideally, some means of generating a certificate, to secure credentials passed to the Local Configuration Manager (LCM) on target nodes</span></span>

<span data-ttu-id="acc89-142">De beste manier om Windows Server configureren voor pull-hostservice is een DSC-configuratie te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="acc89-142">The best way to configure Windows Server to host pull service is to use a DSC configuration.</span></span>
<span data-ttu-id="acc89-143">Hieronder vindt u een voorbeeldscript.</span><span class="sxs-lookup"><span data-stu-id="acc89-143">An example script is provided below.</span></span>

### <a name="supported-database-systems"></a><span data-ttu-id="acc89-144">Ondersteunde databasesystemen</span><span class="sxs-lookup"><span data-stu-id="acc89-144">Supported database systems</span></span>

|<span data-ttu-id="acc89-145">WMF 4.0</span><span class="sxs-lookup"><span data-stu-id="acc89-145">WMF 4.0</span></span>   |<span data-ttu-id="acc89-146">WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="acc89-146">WMF 5.0</span></span>  |<span data-ttu-id="acc89-147">WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="acc89-147">WMF 5.1</span></span> |<span data-ttu-id="acc89-148">WMF 5.1 (Windows Server Insider Preview 17090)</span><span class="sxs-lookup"><span data-stu-id="acc89-148">WMF 5.1 (Windows Server Insider Preview 17090)</span></span>|
|---------|---------|---------|---------|
|<span data-ttu-id="acc89-149">MDB</span><span class="sxs-lookup"><span data-stu-id="acc89-149">MDB</span></span>     |<span data-ttu-id="acc89-150">ESENT (standaard), MDB</span><span class="sxs-lookup"><span data-stu-id="acc89-150">ESENT (Default), MDB</span></span> |<span data-ttu-id="acc89-151">ESENT (standaard), MDB</span><span class="sxs-lookup"><span data-stu-id="acc89-151">ESENT (Default), MDB</span></span>|<span data-ttu-id="acc89-152">ESENT (standaard), SQL Server, MDB</span><span class="sxs-lookup"><span data-stu-id="acc89-152">ESENT (Default), SQL Server, MDB</span></span>

<span data-ttu-id="acc89-153">Vanaf de release 17090 van [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is een ondersteunde optie voor het Pull-Service (Windows-onderdeel *DSC-Service*).</span><span class="sxs-lookup"><span data-stu-id="acc89-153">Starting in release 17090 of [Windows Server Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server is a supported option for the Pull Service (Windows Feature *DSC-Service*).</span></span>  <span data-ttu-id="acc89-154">Dit biedt een nieuwe optie voor het schalen van grote DSC-omgevingen die niet gemigreerd naar [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span><span class="sxs-lookup"><span data-stu-id="acc89-154">This provides a new option for scaling large DSC environments that have not migrated to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).</span></span>

> <span data-ttu-id="acc89-155">**Opmerking**: ondersteuning voor SQL Server wordt niet toegevoegd met eerdere versies van WMF 5.1 (of lager) en is alleen beschikbaar op Windows Server-versies groter dan of gelijk zijn aan 17090.</span><span class="sxs-lookup"><span data-stu-id="acc89-155">**Note**: SQL Server support will not be added to previous versions of WMF 5.1 (or earlier) and will only be available on Windows Server versions greater than or equal to 17090.</span></span>

<span data-ttu-id="acc89-156">Voor het configureren van de pull-server voor het gebruik van SQL Server instellen **SqlProvider** naar `$true` en **SqlConnectionString** op een geldige SQL Server-verbindingsreeks.</span><span class="sxs-lookup"><span data-stu-id="acc89-156">To configure the pull server to use SQL Server, set **SqlProvider** to `$true` and **SqlConnectionString** to a valid SQL Server Connection String.</span></span>  <span data-ttu-id="acc89-157">Zie voor meer informatie [SqlClient-verbindingsreeksen](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span><span class="sxs-lookup"><span data-stu-id="acc89-157">For more information, see [SqlClient Connection Strings](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).</span></span>
<span data-ttu-id="acc89-158">Voor een voorbeeld van SQL Server-configuratiebestand met **xDscWebService**, lees eerst [met behulp van de resource xDscWebService](#using-the-xdscwebservice-resource) en bekijk vervolgens [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 op GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span><span class="sxs-lookup"><span data-stu-id="acc89-158">For an example of SQL Server configuration with **xDscWebService**, first read [Using the xDscWebService resource](#using-the-xdscwebservice-resource) and then review [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 on GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).</span></span>

### <a name="using-the-xdscwebservice-resource"></a><span data-ttu-id="acc89-159">Met behulp van de resource xDscWebService</span><span class="sxs-lookup"><span data-stu-id="acc89-159">Using the xDscWebService resource</span></span>

<span data-ttu-id="acc89-160">De eenvoudigste manier voor het instellen van een pull-webserver is met de **xDscWebService** resource, opgenomen in de **xPSDesiredStateConfiguration** module.</span><span class="sxs-lookup"><span data-stu-id="acc89-160">The easiest way to set up a web pull server is to use the **xDscWebService** resource, included in the **xPSDesiredStateConfiguration** module.</span></span>
<span data-ttu-id="acc89-161">De volgende stappen wordt uitgelegd hoe u de bron in een configuratie die de webservice heeft ingesteld.</span><span class="sxs-lookup"><span data-stu-id="acc89-161">The following steps explain how to use the resource in a configuration that sets up the web service.</span></span>

1. <span data-ttu-id="acc89-162">Roep de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet voor het installeren van de **xPSDesiredStateConfiguration** module.</span><span class="sxs-lookup"><span data-stu-id="acc89-162">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xPSDesiredStateConfiguration** module.</span></span> <span data-ttu-id="acc89-163">**Opmerking**: **Install-Module** is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="acc89-163">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="acc89-164">U kunt downloaden via de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="acc89-164">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
1. <span data-ttu-id="acc89-165">Een SSL-certificaat ophalen voor de DSC-Pull-server via een vertrouwde certificeringsinstantie zich binnen uw organisatie of een openbare CA.</span><span class="sxs-lookup"><span data-stu-id="acc89-165">Get an SSL certificate for the DSC Pull server from a trusted Certificate Authority, either within your organization or a public authority.</span></span> <span data-ttu-id="acc89-166">Het certificaat dat is ontvangen van de instantie is meestal de PFX-indeling.</span><span class="sxs-lookup"><span data-stu-id="acc89-166">The certificate received from the authority is usually in the PFX format.</span></span> <span data-ttu-id="acc89-167">Installeer het certificaat op het knooppunt dat de DSC-Pull-server in de standaardlocatie bevindt, CERT: \LocalMachine\My moet worden.</span><span class="sxs-lookup"><span data-stu-id="acc89-167">Install the certificate on the node that will become the DSC Pull server in the default location, which should be CERT:\LocalMachine\My.</span></span> <span data-ttu-id="acc89-168">Noteer de certificaatvingerafdruk van het.</span><span class="sxs-lookup"><span data-stu-id="acc89-168">Make a note of the certificate thumbprint.</span></span>
1. <span data-ttu-id="acc89-169">Selecteer een GUID moet worden gebruikt als de registratiesleutel.</span><span class="sxs-lookup"><span data-stu-id="acc89-169">Select a GUID to be used as the Registration Key.</span></span> <span data-ttu-id="acc89-170">Voor het genereren van een met behulp van PowerShell, typ het volgende achter de PS-prompt en druk op enter: '``` [guid]::newGuid()```'of'```New-Guid```'.</span><span class="sxs-lookup"><span data-stu-id="acc89-170">To generate one using PowerShell enter the following at the PS prompt and press enter: '``` [guid]::newGuid()```' or '```New-Guid```'.</span></span> <span data-ttu-id="acc89-171">Deze sleutel wordt door de knooppunten van de client worden gebruikt als een gedeelde sleutel om te verifiëren tijdens de registratie.</span><span class="sxs-lookup"><span data-stu-id="acc89-171">This key will be used by client nodes as a shared key to authenticate during registration.</span></span> <span data-ttu-id="acc89-172">Zie de sectie registratiesleutel hieronder voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="acc89-172">For more information, see the Registration Key section below.</span></span>
1. <span data-ttu-id="acc89-173">Start in de PowerShell ISE (F5) het volgende configuratiescript (opgenomen in de map met voorbeelden van de **xPSDesiredStateConfiguration** module als Sample_xDscWebServiceRegistration.ps1).</span><span class="sxs-lookup"><span data-stu-id="acc89-173">In the PowerShell ISE, start (F5) the following configuration script (included in the Examples folder of the  **xPSDesiredStateConfiguration** module as Sample_xDscWebServiceRegistration.ps1).</span></span> <span data-ttu-id="acc89-174">Dit script is ingesteld van de pull-server.</span><span class="sxs-lookup"><span data-stu-id="acc89-174">This script sets up the pull server.</span></span>

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

1. <span data-ttu-id="acc89-175">Voer de configuratie, voor het doorgeven van de vingerafdruk van het SSL-certificaat als de **certificateThumbPrint** parameter en de registratie van een GUID sleutel als de **RegistrationKey** parameter:</span><span class="sxs-lookup"><span data-stu-id="acc89-175">Run the configuration, passing the thumbprint of the SSL certificate as the **certificateThumbPrint** parameter and a GUID registration key as the **RegistrationKey** parameter:</span></span>

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a><span data-ttu-id="acc89-176">Registratiesleutel</span><span class="sxs-lookup"><span data-stu-id="acc89-176">Registration Key</span></span>

<span data-ttu-id="acc89-177">Als u wilt toestaan client knooppunten om te registreren bij de server, zodat ze configuratienamen in plaats van een configuratie-ID gebruiken kunnen, een registratiesleutel die is gemaakt door de bovenstaande configuratie wordt opgeslagen in een bestand met de naam `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span><span class="sxs-lookup"><span data-stu-id="acc89-177">To allow client nodes to register with the server so that they can use configuration names instead of a configuration ID, a registration key that was created by the above configuration is saved in a file named `RegistrationKeys.txt` in `C:\Program Files\WindowsPowerShell\DscService`.</span></span> <span data-ttu-id="acc89-178">De registratiesleutel fungeert als een gedeeld geheim gebruikt tijdens de initiële registratie door de client met de pull-server.</span><span class="sxs-lookup"><span data-stu-id="acc89-178">The registration key functions as a shared secret used during the initial registration by the client with the pull server.</span></span> <span data-ttu-id="acc89-179">De client genereert een zelfondertekend certificaat dat wordt gebruikt voor een unieke verificatie naar de pull-server wanneer de registratie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="acc89-179">The client will generate a self-signed certificate that is used to uniquely authenticate to the pull server once registration is successfully completed.</span></span> <span data-ttu-id="acc89-180">De vingerafdruk van dit certificaat wordt lokaal opgeslagen en die zijn gekoppeld aan de URL van de pull-server.</span><span class="sxs-lookup"><span data-stu-id="acc89-180">The thumbprint of this certificate is stored locally and associated with the URL of the pull server.</span></span>
> <span data-ttu-id="acc89-181">**Opmerking**: registratiesleutels worden niet ondersteund in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="acc89-181">**Note**: Registration keys are not supported in PowerShell 4.0.</span></span>

<span data-ttu-id="acc89-182">Voordat u een knooppunt te verifiëren met de pull-server configureren, moet de registratiesleutel in de metaconfiguratie voor elk doelknooppunt die zal worden geregistreerd met deze pull-server.</span><span class="sxs-lookup"><span data-stu-id="acc89-182">In order to configure a node to authenticate with the pull server, the registration key needs to be in the metaconfiguration for any target node that will be registering with this pull server.</span></span> <span data-ttu-id="acc89-183">Houd er rekening mee dat de **RegistrationKey** in de onderstaande metaconfiguratie wordt verwijderd nadat de doelmachine heeft geregistreerd en de waarde '140a952b-b9d6-406b-b416-e0f759c9c0e4' moet overeenkomen met de waarde die is opgeslagen in de RegistrationKeys.txt-bestand op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="acc89-183">Note that the **RegistrationKey** in the metaconfiguration below is removed after the target machine has successfully registered, and that the value '140a952b-b9d6-406b-b416-e0f759c9c0e4' must match the value stored in the RegistrationKeys.txt file on the pull server.</span></span> <span data-ttu-id="acc89-184">Altijd worden beschouwd door de waarde van de registratie-sleutel veilig, omdat elke doelcomputer registreren bij de pull-server geïnstalleerd is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="acc89-184">Always treat the registration key value securely, because knowing it allows any target machine to register with the pull server.</span></span>

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

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

> <span data-ttu-id="acc89-185">**Opmerking**: de **ReportServerWeb** sectie kan worden verzonden naar de pull-server melden.</span><span class="sxs-lookup"><span data-stu-id="acc89-185">**Note**: The **ReportServerWeb** section allows reporting data to be sent to the pull server.</span></span>

<span data-ttu-id="acc89-186">Het ontbreken van de **ConfigurationID** eigenschap in het bestand metaconfiguratie impliciet betekent dat pull-server ondersteunt de V2-versie van het protocol voor pull-server zodat een initiële registratie is vereist.</span><span class="sxs-lookup"><span data-stu-id="acc89-186">The lack of the **ConfigurationID** property in the metaconfiguration file implicitly means that pull server is supporting the V2 version of the pull server protocol so an initial registration is required.</span></span>
<span data-ttu-id="acc89-187">Als u daarentegen de aanwezigheid van een **ConfigurationID** betekent dat de V1-versie van het pull-protocol wordt gebruikt en er geen registratie-verwerking is.</span><span class="sxs-lookup"><span data-stu-id="acc89-187">Conversely, the presence of a **ConfigurationID** means that the V1 version of the pull server protocol is used and there is no registration processing.</span></span>

><span data-ttu-id="acc89-188">**Opmerking**: In een PUSH-scenario is een fout bestaat in de huidige release die nodig is voor het definiëren van een eigenschap ConfigurationID in het bestand metaconfiguratie voor knooppunten die nooit zijn geregistreerd bij een pull-server.</span><span class="sxs-lookup"><span data-stu-id="acc89-188">**Note**: In a PUSH scenario, a bug exists in the current release that makes it necessary to define a ConfigurationID property in the metaconfiguration file for nodes that have never registered with a pull server.</span></span> <span data-ttu-id="acc89-189">Hiermee wordt het protocol V1-Pull-Server dwingen en registratie foutberichten voorkomen.</span><span class="sxs-lookup"><span data-stu-id="acc89-189">This will force the V1 Pull Server protocol and avoid registration failure messages.</span></span>

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="acc89-190">Configuraties en resources plaatsen</span><span class="sxs-lookup"><span data-stu-id="acc89-190">Placing configurations and resources</span></span>

<span data-ttu-id="acc89-191">Nadat de pull server setup is voltooid, de mappen die zijn gedefinieerd door de **ConfigurationPath** en **ModulePath** eigenschappen in de configuratie van de pull-server zijn waar u modules en configuraties worden geplaatst die beschikbaar zal zijn voor de doelknooppunten om op te halen.</span><span class="sxs-lookup"><span data-stu-id="acc89-191">After the pull server setup completes, the folders defined by the **ConfigurationPath** and **ModulePath** properties in the pull server configuration are where you will place modules and configurations that will be available for target nodes to pull.</span></span>
<span data-ttu-id="acc89-192">Deze bestanden moeten in een specifieke indeling om de pull-server ze correct te verwerken.</span><span class="sxs-lookup"><span data-stu-id="acc89-192">These files need to be in a specific format in order for the pull server to correctly process them.</span></span>

### <a name="dsc-resource-module-package-format"></a><span data-ttu-id="acc89-193">DSC-resource module pakket-indeling</span><span class="sxs-lookup"><span data-stu-id="acc89-193">DSC resource module package format</span></span>

<span data-ttu-id="acc89-194">Elke resource module moet worden ingepakt en een naam volgens het volgende patroon volgen `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="acc89-194">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span>
<span data-ttu-id="acc89-195">Bijvoorbeeld, een module met de naam xWebAdminstration met een moduleversie van 3.1.2.0 de naam 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="acc89-195">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span>
<span data-ttu-id="acc89-196">Elke versie van een module moet worden opgenomen in een enkel zip-bestand.</span><span class="sxs-lookup"><span data-stu-id="acc89-196">Each version of a module must be contained in a single zip file.</span></span>
<span data-ttu-id="acc89-197">Omdat er slechts één versie van een resource in het zipbestand, wordt de indeling van de module toegevoegd in WMF 5.0 met ondersteuning voor meerdere moduleversies van de in een enkele map wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="acc89-197">Since there is only a single version of a resource in each zip file, the module format added in WMF 5.0 with support for multiple module versions in a single directory is not supported.</span></span>
<span data-ttu-id="acc89-198">Dit betekent dat voordat verpakking van DSC-resource-modules voor gebruik met pull-server u moet een kleine wijziging aanbrengen in de mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="acc89-198">This means that before packaging up DSC resource modules for use with pull server you will need to make a small change to the directory structure.</span></span>
<span data-ttu-id="acc89-199">De standaardindeling van modules met van DSC-resource in WMF 5.0 is ' {Modulemap}\{moduleversie} \DscResources\{DSC-Resourcemap}\'.</span><span class="sxs-lookup"><span data-stu-id="acc89-199">The default format of modules containing DSC resource in WMF 5.0 is '{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="acc89-200">Verwijder, voordat de pakketten voor de pull-server, de **{moduleversie}** map zodat het pad ' {Modulemap} \DscResources\{DSC-Resourcemap}\'.</span><span class="sxs-lookup"><span data-stu-id="acc89-200">Before packaging up for the pull server, remove the **{Module version}** folder so the path becomes '{Module Folder}\DscResources\{DSC Resource Folder}\'.</span></span>
<span data-ttu-id="acc89-201">Zip de map met deze wijziging, zoals hierboven wordt beschreven op en plaats deze zip-bestanden in de **ModulePath** map.</span><span class="sxs-lookup"><span data-stu-id="acc89-201">With this change, zip the folder as described above and place these zip files in the **ModulePath** folder.</span></span>

<span data-ttu-id="acc89-202">Gebruik `New-DscChecksum {module zip file}` een controlesom-bestand voor de toegevoegde module te maken.</span><span class="sxs-lookup"><span data-stu-id="acc89-202">Use `New-DscChecksum {module zip file}` to create a checksum file for the newly added module.</span></span>

### <a name="configuration-mof-format"></a><span data-ttu-id="acc89-203">Configuratie MOF-indeling</span><span class="sxs-lookup"><span data-stu-id="acc89-203">Configuration MOF format</span></span>

<span data-ttu-id="acc89-204">Een configuratie MOF-bestand moet worden gekoppeld aan een bestand controlesom zodat een LCM in een doelknooppunt kunt de configuratie valideren.</span><span class="sxs-lookup"><span data-stu-id="acc89-204">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="acc89-205">Aanroepen voor het maken van een controlesom, de [nieuw DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="acc89-205">To create a checksum, call the [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.</span></span>
<span data-ttu-id="acc89-206">De cmdlet heeft een **pad** parameter waarmee de map waarin de configuratie van de MOF zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="acc89-206">The cmdlet takes a **Path** parameter that specifies the folder where the configuration MOF is located.</span></span>
<span data-ttu-id="acc89-207">De cmdlet maakt een controlesom-bestand met de naam `ConfigurationMOFName.mof.checksum`, waarbij `ConfigurationMOFName` is de naam van het mof-bestand voor configuratie.</span><span class="sxs-lookup"><span data-stu-id="acc89-207">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="acc89-208">Als er meer dan één configuratie MOF-bestanden in de opgegeven map, wordt een controlesom gemaakt voor elke configuratie in de map.</span><span class="sxs-lookup"><span data-stu-id="acc89-208">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>
<span data-ttu-id="acc89-209">Plaats de MOF-bestanden en hun bijbehorende controlesom-bestanden in de **ConfigurationPath** map.</span><span class="sxs-lookup"><span data-stu-id="acc89-209">Place the MOF files and their associated checksum files in the **ConfigurationPath** folder.</span></span>

><span data-ttu-id="acc89-210">**Opmerking**: als u het MOF-bestand van de configuratie op een manier wijzigt, moet u ook het bestand controlesom opnieuw.</span><span class="sxs-lookup"><span data-stu-id="acc89-210">**Note**: If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

### <a name="tooling"></a><span data-ttu-id="acc89-211">Tooling</span><span class="sxs-lookup"><span data-stu-id="acc89-211">Tooling</span></span>

<span data-ttu-id="acc89-212">Om de instelling gezamenlijk valideren en het beheren van de eenvoudiger, pull-server de volgende hulpprogramma's zijn opgenomen als voorbeelden in de meest recente versie van de module xPSDesiredStateConfiguration:</span><span class="sxs-lookup"><span data-stu-id="acc89-212">In order to make setting up, validating and managing the pull server easier, the following tools are included as examples in the latest version of the xPSDesiredStateConfiguration module:</span></span>

1. <span data-ttu-id="acc89-213">Een module die u helpt met het verpakken van DSC-resource-modules en de configuratiebestanden voor gebruik op de pull-server.</span><span class="sxs-lookup"><span data-stu-id="acc89-213">A module that will help with packaging DSC resource modules and configuration files for use on the pull server.</span></span> <span data-ttu-id="acc89-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span><span class="sxs-lookup"><span data-stu-id="acc89-214">[PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).</span></span> <span data-ttu-id="acc89-215">De volgende voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="acc89-215">Examples below:</span></span>

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. <span data-ttu-id="acc89-216">Een script dat de pull-server valideert is correct geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="acc89-216">A script that validates the pull server is configured correctly.</span></span> <span data-ttu-id="acc89-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span><span class="sxs-lookup"><span data-stu-id="acc89-217">[PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).</span></span>

## <a name="community-solutions-for-pull-service"></a><span data-ttu-id="acc89-218">Community-oplossingen voor Pull-Service</span><span class="sxs-lookup"><span data-stu-id="acc89-218">Community Solutions for Pull Service</span></span>

<span data-ttu-id="acc89-219">De DSC-community heeft meerdere oplossingen voor het implementeren van het protocol van de service pull geschreven.</span><span class="sxs-lookup"><span data-stu-id="acc89-219">The DSC community has authored multiple solutions to implement the pull service protocol.</span></span>
<span data-ttu-id="acc89-220">On-premises omgevingen bieden deze mogelijkheden voor pull-service en een kans om bij te dragen naar de community met incrementele verbeteringen.</span><span class="sxs-lookup"><span data-stu-id="acc89-220">For on-premises environments, these offer pull service capabilities and an opportunity to contribute back to the community with incremental enhancements.</span></span>

- [<span data-ttu-id="acc89-221">Tug</span><span class="sxs-lookup"><span data-stu-id="acc89-221">Tug</span></span>](https://github.com/powershellorg/tug)
- [<span data-ttu-id="acc89-222">DSC-TRÆK</span><span class="sxs-lookup"><span data-stu-id="acc89-222">DSC-TRÆK</span></span>](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a><span data-ttu-id="acc89-223">Pull-clientconfiguratie</span><span class="sxs-lookup"><span data-stu-id="acc89-223">Pull client configuration</span></span>

<span data-ttu-id="acc89-224">De volgende onderwerpen wordt instellen van de pull-clients in detail beschreven:</span><span class="sxs-lookup"><span data-stu-id="acc89-224">The following topics describe setting up pull clients in detail:</span></span>

- [<span data-ttu-id="acc89-225">Instellen van een DSC-pull-client met behulp van een configuratie-ID</span><span class="sxs-lookup"><span data-stu-id="acc89-225">Setting up a DSC pull client using a configuration ID</span></span>](pullClientConfigID.md)
- [<span data-ttu-id="acc89-226">Instellen van een DSC-pull-client met behulp van configuratienamen</span><span class="sxs-lookup"><span data-stu-id="acc89-226">Setting up a DSC pull client using configuration names</span></span>](pullClientConfigNames.md)
- [<span data-ttu-id="acc89-227">Gedeeltelijke configuraties</span><span class="sxs-lookup"><span data-stu-id="acc89-227">Partial configurations</span></span>](partialConfigs.md)

## <a name="see-also"></a><span data-ttu-id="acc89-228">Zie ook</span><span class="sxs-lookup"><span data-stu-id="acc89-228">See also</span></span>

- [<span data-ttu-id="acc89-229">Windows PowerShell Desired State Configuration-overzicht</span><span class="sxs-lookup"><span data-stu-id="acc89-229">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="acc89-230">Configuraties doorvoeren</span><span class="sxs-lookup"><span data-stu-id="acc89-230">Enacting configurations</span></span>](enactingConfigurations.md)
- [<span data-ttu-id="acc89-231">Een DSC-rapportserver gebruiken</span><span class="sxs-lookup"><span data-stu-id="acc89-231">Using a DSC report server</span></span>](reportServer.md)
- <span data-ttu-id="acc89-232">[[MS-DSCPM]: Desired State Configuration Pull-Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span><span class="sxs-lookup"><span data-stu-id="acc89-232">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol](https://msdn.microsoft.com/library/dn393548.aspx)</span></span>
- <span data-ttu-id="acc89-233">[[MS-DSCPM]: Desired State Configuration Pull-Model Protocol fouten](https://msdn.microsoft.com/library/mt612824.aspx)</span><span class="sxs-lookup"><span data-stu-id="acc89-233">[[MS-DSCPM]: Desired State Configuration Pull Model Protocol Errata](https://msdn.microsoft.com/library/mt612824.aspx)</span></span>