---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Met Desired State Configuration (DSC) aan de slag voor Linux
ms.openlocfilehash: 0534cede979eb2917adb608dba622539fe4bdc45
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="3125b-103">Met Desired State Configuration (DSC) aan de slag voor Linux</span><span class="sxs-lookup"><span data-stu-id="3125b-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="3125b-104">In dit onderwerp wordt uitgelegd hoe u aan de slag met behulp van PowerShell Desired State Configuration (DSC) voor Linux.</span><span class="sxs-lookup"><span data-stu-id="3125b-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="3125b-105">Raadpleeg voor algemene informatie over DSC [aan de slag met Windows PowerShell Desired State Configuration](overview.md).</span><span class="sxs-lookup"><span data-stu-id="3125b-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="3125b-106">Ondersteunde versies van Linux bewerking systeem</span><span class="sxs-lookup"><span data-stu-id="3125b-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="3125b-107">De volgende versies van Linux-besturingssystemen worden ondersteund voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="3125b-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>
- <span data-ttu-id="3125b-108">CentOS 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3125b-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="3125b-109">Debian GNU/Linux 6, 7 en 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3125b-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="3125b-110">Oracle Linux 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3125b-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="3125b-111">Red Hat Enterprise Linux Server 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3125b-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="3125b-112">SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3125b-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="3125b-113">Ubuntu Server 12.04 TNS, 14.04 TNS en 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="3125b-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="3125b-114">De volgende tabel beschrijft de afhankelijkheden vereist pakket voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="3125b-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="3125b-115">Vereist pakket</span><span class="sxs-lookup"><span data-stu-id="3125b-115">Required package</span></span> |  <span data-ttu-id="3125b-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3125b-116">Description</span></span> |  <span data-ttu-id="3125b-117">Minimale versie</span><span class="sxs-lookup"><span data-stu-id="3125b-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="3125b-118">Glibc</span><span class="sxs-lookup"><span data-stu-id="3125b-118">glibc</span></span>| <span data-ttu-id="3125b-119">GNU-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="3125b-119">GNU Library</span></span>| <span data-ttu-id="3125b-120">2... 4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="3125b-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="3125b-121">Python</span><span class="sxs-lookup"><span data-stu-id="3125b-121">python</span></span>| <span data-ttu-id="3125b-122">Python</span><span class="sxs-lookup"><span data-stu-id="3125b-122">Python</span></span>| <span data-ttu-id="3125b-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="3125b-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="3125b-124">omniserver</span><span class="sxs-lookup"><span data-stu-id="3125b-124">omiserver</span></span>| <span data-ttu-id="3125b-125">Open Management Infrastructure</span><span class="sxs-lookup"><span data-stu-id="3125b-125">Open Management Infrastructure</span></span>| <span data-ttu-id="3125b-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="3125b-126">1.0.8.1</span></span>|
| <span data-ttu-id="3125b-127">Openssl</span><span class="sxs-lookup"><span data-stu-id="3125b-127">openssl</span></span>| <span data-ttu-id="3125b-128">OpenSSL-bibliotheken</span><span class="sxs-lookup"><span data-stu-id="3125b-128">OpenSSL Libraries</span></span>| <span data-ttu-id="3125b-129">0.9.8 of 1.0</span><span class="sxs-lookup"><span data-stu-id="3125b-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="3125b-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="3125b-130">ctypes</span></span>| <span data-ttu-id="3125b-131">CTypes Python-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="3125b-131">Python CTypes library</span></span>| <span data-ttu-id="3125b-132">Moet overeenkomen met de versie van Python</span><span class="sxs-lookup"><span data-stu-id="3125b-132">Must match Python version</span></span>|
| <span data-ttu-id="3125b-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="3125b-133">libcurl</span></span>| <span data-ttu-id="3125b-134">http-clientbibliotheek cURL</span><span class="sxs-lookup"><span data-stu-id="3125b-134">cURL http client library</span></span>| <span data-ttu-id="3125b-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="3125b-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="3125b-136">DSC voor Linux installeren</span><span class="sxs-lookup"><span data-stu-id="3125b-136">Installing DSC for Linux</span></span>

<span data-ttu-id="3125b-137">U moet installeren de [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) voordat DSC voor Linux installeren.</span><span class="sxs-lookup"><span data-stu-id="3125b-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="3125b-138">OMI installeren</span><span class="sxs-lookup"><span data-stu-id="3125b-138">Installing OMI</span></span>

<span data-ttu-id="3125b-139">Desired State Configuration voor Linux de Open Management Infrastructure (OMI) CIM-server, versie 1.0.8.1 vereist of hoger.</span><span class="sxs-lookup"><span data-stu-id="3125b-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="3125b-140">OMI kan worden gedownload uit de Open groep: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="3125b-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="3125b-141">Installeer het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86) voor het installeren van OMI.</span><span class="sxs-lookup"><span data-stu-id="3125b-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="3125b-142">RPM pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="3125b-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="3125b-143">DEB pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="3125b-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="3125b-144">De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 hebt geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.</span><span class="sxs-lookup"><span data-stu-id="3125b-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="3125b-145">**Opmerking**: Voer de opdracht uit om te bepalen van de geïnstalleerde versie van OpenSSL, `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="3125b-145">**Note**: To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="3125b-146">Voer de volgende opdracht voor het installeren van OMI op een systeem CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="3125b-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="3125b-147">DSC installeren</span><span class="sxs-lookup"><span data-stu-id="3125b-147">Installing DSC</span></span>

<span data-ttu-id="3125b-148">DSC voor Linux is beschikbaar als download [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="3125b-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest).</span></span>

<span data-ttu-id="3125b-149">Installeer het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86) voor het installeren van DSC.</span><span class="sxs-lookup"><span data-stu-id="3125b-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="3125b-150">RPM pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="3125b-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="3125b-151">DEB pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="3125b-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="3125b-152">De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 hebt geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.</span><span class="sxs-lookup"><span data-stu-id="3125b-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> <span data-ttu-id="3125b-153">**Opmerking**: om te bepalen van de geïnstalleerde versie van OpenSSL, voert u de opdracht openssl-versie.</span><span class="sxs-lookup"><span data-stu-id="3125b-153">**Note**: To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="3125b-154">Voer de volgende opdracht DSC installeren op een systeem CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="3125b-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a><span data-ttu-id="3125b-155">Gebruik van DSC voor Linux</span><span class="sxs-lookup"><span data-stu-id="3125b-155">Using DSC for Linux</span></span>

<span data-ttu-id="3125b-156">De volgende secties wordt uitgelegd hoe maken en uitvoeren van DSC-configuraties op Linux-computers.</span><span class="sxs-lookup"><span data-stu-id="3125b-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="3125b-157">Maken van een document van de MOF-configuratie</span><span class="sxs-lookup"><span data-stu-id="3125b-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="3125b-158">De configuratie van Windows PowerShell-sleutelwoord gebruikt voor het maken van een configuratie voor Linux-computers, net als voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="3125b-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="3125b-159">De volgende stappen beschrijven het maken van een document van de configuratie voor een Linux-computer met Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3125b-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="3125b-160">Importeer de module NX inschakelen.</span><span class="sxs-lookup"><span data-stu-id="3125b-160">Import the nx module.</span></span> <span data-ttu-id="3125b-161">De nx Windows PowerShell-module moet bevat het schema voor ingebouwde bronnen voor DSC voor Linux en worden geïnstalleerd op uw lokale computer en geïmporteerd in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="3125b-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

    <span data-ttu-id="3125b-162">-Voor het installeren van de module nx, kopieert u de modulemap nx naar elk `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` of `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="3125b-162">-To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="3125b-163">De module nx is opgenomen in de DSC voor Linux-installatiepakket (MSI).</span><span class="sxs-lookup"><span data-stu-id="3125b-163">The nx module is included in the DSC for Linux installation package (MSI).</span></span> <span data-ttu-id="3125b-164">Gebruik de module nx in uw configuratie importeren de __importeren DSCResource__ opdracht:</span><span class="sxs-lookup"><span data-stu-id="3125b-164">To import the nx module in your configuration, use the __Import-DSCResource__ command:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

}
```
2. <span data-ttu-id="3125b-165">Definieer een configuratie en genereren van het configuratiebestand:</span><span class="sxs-lookup"><span data-stu-id="3125b-165">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration ExampleConfiguration{

    Import-DscResource -Module nx

    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp"
```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="3125b-166">De configuratie van de push naar de Linux-computer</span><span class="sxs-lookup"><span data-stu-id="3125b-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="3125b-167">Van configuratiedocumenten (MOF-bestanden) kunnen worden geactiveerd met het Linux-computer via de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3125b-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="3125b-168">Als u wilt gebruiken van deze cmdlet, samen met de [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), of [Test DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, naar een Linux-computer, moet u op afstand een CIMSession gebruiken.</span><span class="sxs-lookup"><span data-stu-id="3125b-168">In order to use this cmdlet, along with the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx), or [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="3125b-169">De [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet gebruikt voor het maken van een CIMSession naar de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="3125b-169">The [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="3125b-170">De volgende code laat zien hoe een CIMSession voor DSC voor Linux maken.</span><span class="sxs-lookup"><span data-stu-id="3125b-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90
```

> <span data-ttu-id="3125b-171">**Opmerking**:</span><span class="sxs-lookup"><span data-stu-id="3125b-171">**Note**:</span></span>
* <span data-ttu-id="3125b-172">Voor de modus 'Push' moet de gebruikersreferentie de hoofdgebruiker op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="3125b-172">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
* <span data-ttu-id="3125b-173">Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, de New-CimSession moet worden gebruikt met de parameter – UseSSL is ingesteld op $true.</span><span class="sxs-lookup"><span data-stu-id="3125b-173">Only SSL/TLS connections are supported for DSC for Linux, the New-CimSession must be used with the –UseSSL parameter set to $true.</span></span>
* <span data-ttu-id="3125b-174">Het SSL-certificaat gebruikt door OMI (DSC) is opgegeven in het bestand: `/opt/omi/etc/omiserver.conf` met de eigenschappen: pemfile en keyfile.</span><span class="sxs-lookup"><span data-stu-id="3125b-174">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
<span data-ttu-id="3125b-175">Als dit certificaat niet wordt vertrouwd door de Windows-computer die u gebruikt de [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet op, kunt u voor het negeren van validatie van het servercertificaat met de opties CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span><span class="sxs-lookup"><span data-stu-id="3125b-175">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`</span></span>

<span data-ttu-id="3125b-176">Voer de volgende opdracht om de DSC-configuratie naar de Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="3125b-176">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="3125b-177">De configuratie met een pull-server distribueren</span><span class="sxs-lookup"><span data-stu-id="3125b-177">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="3125b-178">Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net als voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="3125b-178">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="3125b-179">Zie voor instructies over het gebruik van een pull-server, [Windows PowerShell Desired status Pull configuratieservers](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="3125b-179">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](pullServer.md).</span></span> <span data-ttu-id="3125b-180">Zie voor meer informatie en beperkingen bij het gebruik van Linux-computers met een pull-server, de Release-opmerkingen voor Desired State Configuration voor Linux.</span><span class="sxs-lookup"><span data-stu-id="3125b-180">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="3125b-181">Werken met lokaal configuraties</span><span class="sxs-lookup"><span data-stu-id="3125b-181">Working with configurations locally</span></span>

<span data-ttu-id="3125b-182">DSC voor Linux bevat scripts werken met de configuratie van de lokale Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="3125b-182">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="3125b-183">Deze scripts zijn niet vinden in `/opt/microsoft/dsc/Scripts` en neem het volgende:</span><span class="sxs-lookup"><span data-stu-id="3125b-183">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>
* <span data-ttu-id="3125b-184">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="3125b-184">GetDscConfiguration.py</span></span>

 <span data-ttu-id="3125b-185">Retourneert de huidige configuratie toegepast op de computer.</span><span class="sxs-lookup"><span data-stu-id="3125b-185">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="3125b-186">Vergelijkbaar met de cmdlet Get-DscConfiguration Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3125b-186">Similar to the Windows PowerShell cmdlet Get-DscConfiguration cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

* <span data-ttu-id="3125b-187">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="3125b-187">GetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="3125b-188">Retourneert de huidige meta-configuratie toegepast op de computer.</span><span class="sxs-lookup"><span data-stu-id="3125b-188">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="3125b-189">Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3125b-189">Similar to the cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

* <span data-ttu-id="3125b-190">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="3125b-190">InstallModule.py</span></span>

 <span data-ttu-id="3125b-191">Hiermee installeert een aangepaste module van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="3125b-191">Installs a custom DSC resource module.</span></span> <span data-ttu-id="3125b-192">Het pad naar een ZIP-bestand met de module Gedeelde objectbibliotheek en schema MOF-bestanden vereist.</span><span class="sxs-lookup"><span data-stu-id="3125b-192">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* <span data-ttu-id="3125b-193">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="3125b-193">RemoveModule.py</span></span>

 <span data-ttu-id="3125b-194">Hiermee verwijdert u een aangepaste module van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="3125b-194">Removes a custom DSC resource module.</span></span> <span data-ttu-id="3125b-195">Vereist de naam van de module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="3125b-195">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

* <span data-ttu-id="3125b-196">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="3125b-196">StartDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="3125b-197">Geldt een MOF-bestand voor configuratie voor de computer.</span><span class="sxs-lookup"><span data-stu-id="3125b-197">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="3125b-198">Net als bij de [Start DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3125b-198">Similar to the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet.</span></span> <span data-ttu-id="3125b-199">Het pad naar MOF toepassen van de configuratie vereist.</span><span class="sxs-lookup"><span data-stu-id="3125b-199">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* <span data-ttu-id="3125b-200">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="3125b-200">SetDscLocalConfigurationManager.py</span></span>

 <span data-ttu-id="3125b-201">Geldt een Meta configuratie MOF-bestand voor de computer.</span><span class="sxs-lookup"><span data-stu-id="3125b-201">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="3125b-202">Net als bij de [Set DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3125b-202">Similar to the [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx) cmdlet.</span></span> <span data-ttu-id="3125b-203">Vereist het pad naar het MOF Meta configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="3125b-203">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="3125b-204">PowerShell Desired State Configuration voor Linux-logboekbestanden</span><span class="sxs-lookup"><span data-stu-id="3125b-204">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="3125b-205">De volgende logboekbestanden worden gegenereerd voor DSC voor Linux-berichten.</span><span class="sxs-lookup"><span data-stu-id="3125b-205">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="3125b-206">Logboekbestand</span><span class="sxs-lookup"><span data-stu-id="3125b-206">Log file</span></span>|<span data-ttu-id="3125b-207">Adreslijst</span><span class="sxs-lookup"><span data-stu-id="3125b-207">Directory</span></span>|<span data-ttu-id="3125b-208">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3125b-208">Description</span></span>|
|---|---|---|
|<span data-ttu-id="3125b-209">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="3125b-209">omiserver.log</span></span>|<span data-ttu-id="3125b-210">/var/opt/OMI/log</span><span class="sxs-lookup"><span data-stu-id="3125b-210">/var/opt/omi/log</span></span>|<span data-ttu-id="3125b-211">Berichten met betrekking tot de werking van de OMI-CIM-server.</span><span class="sxs-lookup"><span data-stu-id="3125b-211">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="3125b-212">DSC.log</span><span class="sxs-lookup"><span data-stu-id="3125b-212">dsc.log</span></span>|<span data-ttu-id="3125b-213">/var/opt/OMI/log</span><span class="sxs-lookup"><span data-stu-id="3125b-213">/var/opt/omi/log</span></span>|<span data-ttu-id="3125b-214">Berichten met betrekking tot de werking van de bewerkingen van de lokale Configuration Manager (LCM) en DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="3125b-214">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|