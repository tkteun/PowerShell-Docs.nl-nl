---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Aan de slag met Desired State Configuration (DSC) voor Linux
ms.openlocfilehash: a18b226d4b2d8b8e1ba8b4168ec6ad8f73c73c42
ms.sourcegitcommit: 3f6002e7109373eda31cc65fc84d2600447cb7e9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59506832"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="5e493-103">Aan de slag met Desired State Configuration (DSC) voor Linux</span><span class="sxs-lookup"><span data-stu-id="5e493-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="5e493-104">In dit onderwerp wordt uitgelegd hoe u aan de slag met behulp van PowerShell Desired State Configuration (DSC) voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5e493-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="5e493-105">Raadpleeg voor algemene informatie over DSC [aan de slag met Windows PowerShell Desired State Configuration](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="5e493-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="5e493-106">Ondersteunde versies van Linux bewerking system</span><span class="sxs-lookup"><span data-stu-id="5e493-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="5e493-107">De volgende versies van de Linux-besturingssystemen worden ondersteund voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5e493-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="5e493-108">CentOS 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5e493-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="5e493-109">Debian GNU/Linux 6, 7 en 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5e493-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="5e493-110">Oracle Linux 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5e493-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="5e493-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5e493-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="5e493-112">SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5e493-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="5e493-113">Server Ubuntu 12.04 LTS, 14.04 LTS en 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5e493-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="5e493-114">De volgende tabel beschrijft de vereiste pakketafhankelijkheden voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5e493-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="5e493-115">Vereist pakket</span><span class="sxs-lookup"><span data-stu-id="5e493-115">Required package</span></span> |  <span data-ttu-id="5e493-116">Description</span><span class="sxs-lookup"><span data-stu-id="5e493-116">Description</span></span> |  <span data-ttu-id="5e493-117">Minimale versie</span><span class="sxs-lookup"><span data-stu-id="5e493-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="5e493-118">glibc</span><span class="sxs-lookup"><span data-stu-id="5e493-118">glibc</span></span>| <span data-ttu-id="5e493-119">GNU-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="5e493-119">GNU Library</span></span>| <span data-ttu-id="5e493-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="5e493-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="5e493-121">python</span><span class="sxs-lookup"><span data-stu-id="5e493-121">python</span></span>| <span data-ttu-id="5e493-122">Python</span><span class="sxs-lookup"><span data-stu-id="5e493-122">Python</span></span>| <span data-ttu-id="5e493-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="5e493-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="5e493-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="5e493-124">omiserver</span></span>| <span data-ttu-id="5e493-125">Open Management Infrastructure</span><span class="sxs-lookup"><span data-stu-id="5e493-125">Open Management Infrastructure</span></span>| <span data-ttu-id="5e493-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="5e493-126">1.0.8.1</span></span>|
| <span data-ttu-id="5e493-127">openssl</span><span class="sxs-lookup"><span data-stu-id="5e493-127">openssl</span></span>| <span data-ttu-id="5e493-128">OpenSSL-bibliotheken</span><span class="sxs-lookup"><span data-stu-id="5e493-128">OpenSSL Libraries</span></span>| <span data-ttu-id="5e493-129">versie 0.9.8 of 1.0</span><span class="sxs-lookup"><span data-stu-id="5e493-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="5e493-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="5e493-130">ctypes</span></span>| <span data-ttu-id="5e493-131">CTypes Python-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="5e493-131">Python CTypes library</span></span>| <span data-ttu-id="5e493-132">Moet overeenkomen met de Python-versie</span><span class="sxs-lookup"><span data-stu-id="5e493-132">Must match Python version</span></span>|
| <span data-ttu-id="5e493-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="5e493-133">libcurl</span></span>| <span data-ttu-id="5e493-134">cURL http-clientbibliotheek</span><span class="sxs-lookup"><span data-stu-id="5e493-134">cURL http client library</span></span>| <span data-ttu-id="5e493-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="5e493-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="5e493-136">DSC voor Linux installeren</span><span class="sxs-lookup"><span data-stu-id="5e493-136">Installing DSC for Linux</span></span>

<span data-ttu-id="5e493-137">U moet installeren de [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) voordat u DSC voor Linux installeert.</span><span class="sxs-lookup"><span data-stu-id="5e493-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="5e493-138">OMI installeren</span><span class="sxs-lookup"><span data-stu-id="5e493-138">Installing OMI</span></span>

<span data-ttu-id="5e493-139">Desired State Configuration voor Linux is vereist voor de Open Management Infrastructure (OMI) CIM-server, versie 1.0.8.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="5e493-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="5e493-140">OMI kan worden gedownload uit de Open groep: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="5e493-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="5e493-141">OMI, installeert u het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="5e493-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="5e493-142">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="5e493-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="5e493-143">DEB pakketten zijn geschikt voor Debian GNU/Linux- en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="5e493-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="5e493-144">De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.</span><span class="sxs-lookup"><span data-stu-id="5e493-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="5e493-145">Voer de opdracht uit om te bepalen van de geïnstalleerde versie van OpenSSL, `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="5e493-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="5e493-146">Voer de volgende opdracht te OMI installeren op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="5e493-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="5e493-147">Installeren van DSC</span><span class="sxs-lookup"><span data-stu-id="5e493-147">Installing DSC</span></span>

<span data-ttu-id="5e493-148">DSC voor Linux is beschikbaar als download [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="5e493-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="5e493-149">DSC, installeert u het pakket dat geschikt is voor uw Linux-systeem (.rpm of .deb) en de versie van OpenSSL (ssl_098 of ssl_100) en de architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="5e493-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="5e493-150">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="5e493-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="5e493-151">DEB pakketten zijn geschikt voor Debian GNU/Linux- en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="5e493-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="5e493-152">De ssl_098-pakketten zijn geschikt voor computers met OpenSSL 0.9.8 geïnstalleerd terwijl de ssl_100-pakketten geschikt voor computers met OpenSSL 1.0 is geïnstalleerd zijn.</span><span class="sxs-lookup"><span data-stu-id="5e493-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="5e493-153">Om te bepalen van de geïnstalleerde versie van OpenSSL, de opdracht openssl-versie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5e493-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="5e493-154">Voer de volgende opdracht voor het installeren van DSC op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="5e493-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="5e493-155">Met behulp van DSC voor Linux</span><span class="sxs-lookup"><span data-stu-id="5e493-155">Using DSC for Linux</span></span>

<span data-ttu-id="5e493-156">De volgende secties wordt uitgelegd hoe het maken en uitvoeren van DSC-configuraties op Linux-computers.</span><span class="sxs-lookup"><span data-stu-id="5e493-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="5e493-157">Het maken van een MOF-configuratiebestand</span><span class="sxs-lookup"><span data-stu-id="5e493-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="5e493-158">Het sleutelwoord Windows PowerShell-configuratie wordt gebruikt voor het maken van een configuratie voor Linux-computers, net als voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="5e493-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="5e493-159">De volgende stappen beschrijven het maken van een configuratiebestand voor een Linux-computer met Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e493-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="5e493-160">Importeer de nx-module.</span><span class="sxs-lookup"><span data-stu-id="5e493-160">Import the nx module.</span></span> <span data-ttu-id="5e493-161">De nx Windows PowerShell-module moet bevat het schema voor ingebouwde resources voor DSC voor Linux, en worden geïnstalleerd op uw lokale computer en geïmporteerd in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="5e493-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="5e493-162">Als u wilt de nx-module installeert, kopieert u de modulemap nx naar een `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` of `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="5e493-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="5e493-163">De nx-module is opgenomen in de DSC voor Linux-installatiepakket.</span><span class="sxs-lookup"><span data-stu-id="5e493-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="5e493-164">Als u wilt importeren in de configuratie van de nx-module, gebruikt de `Import-DSCResource` opdracht:</span><span class="sxs-lookup"><span data-stu-id="5e493-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="5e493-165">Een configuratie definiëren en genereren van het configuratiebestand:</span><span class="sxs-lookup"><span data-stu-id="5e493-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="5e493-166">De configuratie van de push naar de Linux-computer</span><span class="sxs-lookup"><span data-stu-id="5e493-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="5e493-167">Van configuratiedocumenten (MOF-bestanden) kunnen worden geactiveerd met de Linux-computer via de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e493-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="5e493-168">Als u wilt gebruiken met deze cmdlet, samen met de [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), of [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, op afstand op een Linux-computer, moet u een CIMSession gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5e493-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="5e493-169">De [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet wordt gebruikt om u te maken van een CIMSession naar de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="5e493-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="5e493-170">De volgende code laat zien hoe een CIMSession maken voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5e493-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="5e493-171">Voor de modus 'Push' moet de referenties van de gebruiker de hoofdgebruiker zijn op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="5e493-171">For “Push” mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="5e493-172">Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, de `New-CimSession` moet worden gebruikt met de parameter – UseSSL is ingesteld op $true.</span><span class="sxs-lookup"><span data-stu-id="5e493-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="5e493-173">Het SSL-certificaat gebruikt door OMI (DSC) is opgegeven in het bestand: `/opt/omi/etc/omiserver.conf` met de eigenschappen: pemfile en keyfile.</span><span class="sxs-lookup"><span data-stu-id="5e493-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="5e493-174">Als dit certificaat niet wordt vertrouwd door de Windows-computer waarop u de [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet op die u kunt kiezen om de validatie van het servercertificaat met de opties CIMSession negeren:</span><span class="sxs-lookup"><span data-stu-id="5e493-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options:</span></span> `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`

<span data-ttu-id="5e493-175">Voer de volgende opdracht om de DSC-configuratie tot de Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5e493-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="5e493-176">Distribueren van de configuratie met een pull-server</span><span class="sxs-lookup"><span data-stu-id="5e493-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="5e493-177">Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net als voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="5e493-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="5e493-178">Zie voor instructies over het gebruik van een pull-server [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="5e493-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="5e493-179">Zie voor meer informatie en beperkingen met betrekking tot het gebruik van Linux-computers met een pull-server, de opmerkingen bij de Release voor Desired State Configuration voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5e493-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="5e493-180">Werken met configuraties lokaal</span><span class="sxs-lookup"><span data-stu-id="5e493-180">Working with configurations locally</span></span>

<span data-ttu-id="5e493-181">DSC voor Linux bevat scripts die worden gebruikt met de configuratie van de lokale Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="5e493-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="5e493-182">Deze scripts zijn niet vinden in `/opt/microsoft/dsc/Scripts` en neem het volgende:</span><span class="sxs-lookup"><span data-stu-id="5e493-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="5e493-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="5e493-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="5e493-184">Retourneert de huidige configuratie is toegepast op de computer.</span><span class="sxs-lookup"><span data-stu-id="5e493-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="5e493-185">Vergelijkbaar met de Windows PowerShell-cmdlet `Get-DscConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e493-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="5e493-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="5e493-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="5e493-187">Retourneert de huidige meta-configuratie op de computer toegepast.</span><span class="sxs-lookup"><span data-stu-id="5e493-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="5e493-188">Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e493-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="5e493-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="5e493-189">InstallModule.py</span></span>

<span data-ttu-id="5e493-190">Hiermee installeert u een aangepaste module van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5e493-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="5e493-191">Het pad naar een ZIP-bestand met de module Gedeelde objectbibliotheek en schema MOF-bestanden vereist.</span><span class="sxs-lookup"><span data-stu-id="5e493-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="5e493-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="5e493-192">RemoveModule.py</span></span>

<span data-ttu-id="5e493-193">Hiermee verwijdert u een aangepaste module van de DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5e493-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="5e493-194">Vereist de naam van de module te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5e493-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="5e493-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="5e493-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="5e493-196">Geldt een MOF-configuratiebestand voor de computer.</span><span class="sxs-lookup"><span data-stu-id="5e493-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="5e493-197">Vergelijkbaar met de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e493-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="5e493-198">Het pad naar MOF om toe te passen van de configuratie vereist.</span><span class="sxs-lookup"><span data-stu-id="5e493-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="5e493-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="5e493-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="5e493-200">Geldt een Meta-configuratie MOF-bestand voor de computer.</span><span class="sxs-lookup"><span data-stu-id="5e493-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="5e493-201">Vergelijkbaar met de [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e493-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="5e493-202">Moet het pad naar het MOF Meta-configuratie om toe te passen.</span><span class="sxs-lookup"><span data-stu-id="5e493-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="5e493-203">PowerShell Desired State Configuration voor Linux-logboekbestanden</span><span class="sxs-lookup"><span data-stu-id="5e493-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="5e493-204">De volgende logboekbestanden worden gegenereerd voor DSC voor Linux-berichten.</span><span class="sxs-lookup"><span data-stu-id="5e493-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="5e493-205">Logboekbestand</span><span class="sxs-lookup"><span data-stu-id="5e493-205">Log file</span></span>|<span data-ttu-id="5e493-206">Adreslijst</span><span class="sxs-lookup"><span data-stu-id="5e493-206">Directory</span></span>|<span data-ttu-id="5e493-207">Description</span><span class="sxs-lookup"><span data-stu-id="5e493-207">Description</span></span>|
|---|---|---|
|**<span data-ttu-id="5e493-208">omiserver.log</span><span class="sxs-lookup"><span data-stu-id="5e493-208">omiserver.log</span></span>**|`/var/opt/omi/log`|<span data-ttu-id="5e493-209">Berichten die betrekking hebben op de werking van de OMI-CIM-server.</span><span class="sxs-lookup"><span data-stu-id="5e493-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|**<span data-ttu-id="5e493-210">dsc.log</span><span class="sxs-lookup"><span data-stu-id="5e493-210">dsc.log</span></span>**|`/var/opt/omi/log`|<span data-ttu-id="5e493-211">Berichten die betrekking hebben op de werking van de lokale Configuration Manager (LCM) en DSC-resource-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="5e493-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
