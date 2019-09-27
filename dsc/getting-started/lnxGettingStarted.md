---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Aan de slag met de desired state Configuration (DSC) voor Linux
ms.openlocfilehash: 523b91741dba57a98ac6e7ba660a776568af7065
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323540"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="e83ad-103">Aan de slag met de desired state Configuration (DSC) voor Linux</span><span class="sxs-lookup"><span data-stu-id="e83ad-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="e83ad-104">In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Linux.</span><span class="sxs-lookup"><span data-stu-id="e83ad-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="e83ad-105">Zie [aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)(Engelstalig) voor algemene informatie over DSC.</span><span class="sxs-lookup"><span data-stu-id="e83ad-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="e83ad-106">Ondersteunde versies van Linux-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="e83ad-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="e83ad-107">De volgende versies van Linux-besturings systemen worden ondersteund voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="e83ad-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="e83ad-108">CentOS 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e83ad-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="e83ad-109">Debian GNU/Linux 6, 7 en 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e83ad-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="e83ad-110">Oracle Linux 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e83ad-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="e83ad-111">Red Hat Enterprise Linux Server 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e83ad-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="e83ad-112">SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e83ad-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="e83ad-113">Ubuntu Server 12,04 LTS, 14,04 LTS en 16,04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e83ad-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="e83ad-114">In de volgende tabel worden de vereiste pakket afhankelijkheden voor DSC voor Linux beschreven.</span><span class="sxs-lookup"><span data-stu-id="e83ad-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="e83ad-115">Vereist pakket</span><span class="sxs-lookup"><span data-stu-id="e83ad-115">Required package</span></span> |  <span data-ttu-id="e83ad-116">Description</span><span class="sxs-lookup"><span data-stu-id="e83ad-116">Description</span></span> |  <span data-ttu-id="e83ad-117">Minimale versie</span><span class="sxs-lookup"><span data-stu-id="e83ad-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="e83ad-118">glibc</span><span class="sxs-lookup"><span data-stu-id="e83ad-118">glibc</span></span>| <span data-ttu-id="e83ad-119">GNU-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="e83ad-119">GNU Library</span></span>| <span data-ttu-id="e83ad-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="e83ad-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="e83ad-121">Python</span><span class="sxs-lookup"><span data-stu-id="e83ad-121">python</span></span>| <span data-ttu-id="e83ad-122">Python</span><span class="sxs-lookup"><span data-stu-id="e83ad-122">Python</span></span>| <span data-ttu-id="e83ad-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="e83ad-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="e83ad-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="e83ad-124">omiserver</span></span>| <span data-ttu-id="e83ad-125">Open-beheer infrastructuur</span><span class="sxs-lookup"><span data-stu-id="e83ad-125">Open Management Infrastructure</span></span>| <span data-ttu-id="e83ad-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="e83ad-126">1.0.8.1</span></span>|
| <span data-ttu-id="e83ad-127">openssl</span><span class="sxs-lookup"><span data-stu-id="e83ad-127">openssl</span></span>| <span data-ttu-id="e83ad-128">OpenSSL-bibliotheken</span><span class="sxs-lookup"><span data-stu-id="e83ad-128">OpenSSL Libraries</span></span>| <span data-ttu-id="e83ad-129">0.9.8 of 1,0</span><span class="sxs-lookup"><span data-stu-id="e83ad-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="e83ad-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="e83ad-130">ctypes</span></span>| <span data-ttu-id="e83ad-131">Python CTypes-bibliotheek</span><span class="sxs-lookup"><span data-stu-id="e83ad-131">Python CTypes library</span></span>| <span data-ttu-id="e83ad-132">Moet overeenkomen met python-versie</span><span class="sxs-lookup"><span data-stu-id="e83ad-132">Must match Python version</span></span>|
| <span data-ttu-id="e83ad-133">libkrul</span><span class="sxs-lookup"><span data-stu-id="e83ad-133">libcurl</span></span>| <span data-ttu-id="e83ad-134">Krul HTTP-client bibliotheek</span><span class="sxs-lookup"><span data-stu-id="e83ad-134">cURL http client library</span></span>| <span data-ttu-id="e83ad-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="e83ad-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="e83ad-136">DSC voor Linux installeren</span><span class="sxs-lookup"><span data-stu-id="e83ad-136">Installing DSC for Linux</span></span>

<span data-ttu-id="e83ad-137">U moet de [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi) installeren voordat u DSC voor Linux installeert.</span><span class="sxs-lookup"><span data-stu-id="e83ad-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="e83ad-138">OMI installeren</span><span class="sxs-lookup"><span data-stu-id="e83ad-138">Installing OMI</span></span>

<span data-ttu-id="e83ad-139">De desired state Configuration voor Linux vereist de open Management Infrastructure (OMI) CIM-Server versie 1.0.8.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="e83ad-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="e83ad-140">OMI kunnen worden gedownload uit de geopende groep: [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="e83ad-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="e83ad-141">Als u OMI wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="e83ad-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="e83ad-142">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="e83ad-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="e83ad-143">DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="e83ad-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="e83ad-144">De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is geïnstalleerd terwijl de ssl_100-pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e83ad-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="e83ad-145">Voer de opdracht `openssl version`uit om de geïnstalleerde versie van openssl te bepalen.</span><span class="sxs-lookup"><span data-stu-id="e83ad-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="e83ad-146">Voer de volgende opdracht uit om OMI te installeren op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="e83ad-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="e83ad-147">DSC installeren</span><span class="sxs-lookup"><span data-stu-id="e83ad-147">Installing DSC</span></span>

<span data-ttu-id="e83ad-148">DSC voor Linux kan [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294)worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="e83ad-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="e83ad-149">Als u DSC wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="e83ad-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="e83ad-150">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="e83ad-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="e83ad-151">DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="e83ad-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="e83ad-152">De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is geïnstalleerd terwijl de ssl_100-pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e83ad-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="e83ad-153">Voer de opdracht openssl versie uit om de geïnstalleerde versie van OpenSSL te bepalen.</span><span class="sxs-lookup"><span data-stu-id="e83ad-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="e83ad-154">Voer de volgende opdracht uit om DSC te installeren op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="e83ad-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="e83ad-155">DSC voor Linux gebruiken</span><span class="sxs-lookup"><span data-stu-id="e83ad-155">Using DSC for Linux</span></span>

<span data-ttu-id="e83ad-156">In de volgende secties wordt uitgelegd hoe u DSC-configuraties op Linux-computers maakt en uitvoert.</span><span class="sxs-lookup"><span data-stu-id="e83ad-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="e83ad-157">Een configuratie-MOF-document maken</span><span class="sxs-lookup"><span data-stu-id="e83ad-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="e83ad-158">Het sleutel woord Windows Power shell-configuratie wordt gebruikt voor het maken van een configuratie voor Linux-computers, net als bij Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="e83ad-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="e83ad-159">De volgende stappen beschrijven het maken van een configuratie document voor een Linux-computer met behulp van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="e83ad-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="e83ad-160">Importeer de NX-module.</span><span class="sxs-lookup"><span data-stu-id="e83ad-160">Import the nx module.</span></span> <span data-ttu-id="e83ad-161">De NX Windows Power shell-module bevat het schema voor ingebouwde resources voor DSC voor Linux en moet worden geïnstalleerd op uw lokale computer en worden geïmporteerd in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="e83ad-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="e83ad-162">Als u de NX-module wilt installeren, kopieert u de map `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` van `$PSHOME\Modules`de NX-module naar ofwel of.</span><span class="sxs-lookup"><span data-stu-id="e83ad-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="e83ad-163">De NX-module is opgenomen in het installatie pakket voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="e83ad-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="e83ad-164">Als u de NX-module in uw configuratie wilt importeren `Import-DSCResource` , gebruikt u de opdracht:</span><span class="sxs-lookup"><span data-stu-id="e83ad-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="e83ad-165">Definieer een configuratie en Genereer het configuratie document:</span><span class="sxs-lookup"><span data-stu-id="e83ad-165">Define a configuration and generate the configuration document:</span></span>

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

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="e83ad-166">De configuratie naar de Linux-computer pushen</span><span class="sxs-lookup"><span data-stu-id="e83ad-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="e83ad-167">Configuratie documenten (MOF-bestanden) kunnen worden gepusht naar de Linux-computer met behulp van de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="e83ad-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="e83ad-168">Als u deze cmdlet wilt gebruiken, samen met de cmdlets [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)of [test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) , op afstand naar een Linux-computer, moet u een CIMSession gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e83ad-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="e83ad-169">De cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) wordt gebruikt om een CimSession te maken op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="e83ad-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="e83ad-170">De volgende code laat zien hoe u een CIMSession maakt voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="e83ad-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

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
> <span data-ttu-id="e83ad-171">De gebruikers referenties voor de push-modus moeten de hoofd gebruiker zijn op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="e83ad-171">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="e83ad-172">Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, `New-CimSession` de moet worden gebruikt met de para meter – UseSSL die is ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="e83ad-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="e83ad-173">Het SSL-certificaat dat wordt gebruikt door Omi (voor DSC) is opgegeven in `/opt/omi/etc/omiserver.conf` het bestand: met de eigenschappen: pemfile en keyfile.</span><span class="sxs-lookup"><span data-stu-id="e83ad-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/opt/omi/etc/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="e83ad-174">Als dit certificaat niet wordt vertrouwd door de Windows-computer waarop u de cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) uitvoert, kunt u certificaat validatie negeren met de CimSession-opties:`-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span><span class="sxs-lookup"><span data-stu-id="e83ad-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="e83ad-175">Voer de volgende opdracht uit om de DSC-configuratie naar het Linux-knoop punt te pushen.</span><span class="sxs-lookup"><span data-stu-id="e83ad-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="e83ad-176">De configuratie distribueren met een pull-server</span><span class="sxs-lookup"><span data-stu-id="e83ad-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="e83ad-177">Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net zoals voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="e83ad-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="e83ad-178">Zie [Windows Power shell desired state Configuration pull servers](../pull-server/pullServer.md)(Engelstalig) voor hulp bij het gebruik van een pull-server.</span><span class="sxs-lookup"><span data-stu-id="e83ad-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="e83ad-179">Voor aanvullende informatie en beperkingen met betrekking tot het gebruik van Linux-computers met een pull-Server raadpleegt u de release opmerkingen voor de gewenste status configuratie voor Linux.</span><span class="sxs-lookup"><span data-stu-id="e83ad-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="e83ad-180">Lokaal met configuraties werken</span><span class="sxs-lookup"><span data-stu-id="e83ad-180">Working with configurations locally</span></span>

<span data-ttu-id="e83ad-181">DSC voor Linux bevat scripts voor het werken met de configuratie van de lokale Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="e83ad-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="e83ad-182">Deze scripts zijn te vinden `/opt/microsoft/dsc/Scripts` in en bevatten het volgende:</span><span class="sxs-lookup"><span data-stu-id="e83ad-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="e83ad-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="e83ad-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="e83ad-184">Retourneert de huidige configuratie die op de computer is toegepast.</span><span class="sxs-lookup"><span data-stu-id="e83ad-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="e83ad-185">Vergelijkbaar met de cmdlet Windows Power `Get-DscConfiguration` shell cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e83ad-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="e83ad-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e83ad-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="e83ad-187">Retourneert de huidige meta-configuratie die op de computer is toegepast.</span><span class="sxs-lookup"><span data-stu-id="e83ad-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="e83ad-188">Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e83ad-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="e83ad-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="e83ad-189">InstallModule.py</span></span>

<span data-ttu-id="e83ad-190">Hiermee wordt een aangepaste DSC-resource module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e83ad-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="e83ad-191">Vereist het pad naar een zip-bestand met de module gedeelde object bibliotheek en schema-MOF-bestanden.</span><span class="sxs-lookup"><span data-stu-id="e83ad-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="e83ad-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="e83ad-192">RemoveModule.py</span></span>

<span data-ttu-id="e83ad-193">Hiermee verwijdert u een aangepaste DSC-resource module.</span><span class="sxs-lookup"><span data-stu-id="e83ad-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="e83ad-194">Vereist de naam van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e83ad-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="e83ad-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e83ad-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="e83ad-196">Past een MOF-configuratie bestand op de computer toe.</span><span class="sxs-lookup"><span data-stu-id="e83ad-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="e83ad-197">Vergelijkbaar met de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="e83ad-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="e83ad-198">Vereist het pad naar de configuratie-MOF die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="e83ad-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="e83ad-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e83ad-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="e83ad-200">Past een MOF-bestand van de meta configuratie toe op de computer.</span><span class="sxs-lookup"><span data-stu-id="e83ad-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="e83ad-201">Vergelijkbaar met de cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="e83ad-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="e83ad-202">Vereist het pad naar de meta configuratie-MOF die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="e83ad-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="e83ad-203">Power shell desired state Configuration voor Linux-logboek bestanden</span><span class="sxs-lookup"><span data-stu-id="e83ad-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="e83ad-204">De volgende logboek bestanden worden gegenereerd voor DSC voor Linux-berichten.</span><span class="sxs-lookup"><span data-stu-id="e83ad-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="e83ad-205">Logboek bestand</span><span class="sxs-lookup"><span data-stu-id="e83ad-205">Log file</span></span>|<span data-ttu-id="e83ad-206">Directory</span><span class="sxs-lookup"><span data-stu-id="e83ad-206">Directory</span></span>|<span data-ttu-id="e83ad-207">Description</span><span class="sxs-lookup"><span data-stu-id="e83ad-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="e83ad-208">**omiserver. log**</span><span class="sxs-lookup"><span data-stu-id="e83ad-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="e83ad-209">Berichten met betrekking tot de werking van de OMI CIM-server.</span><span class="sxs-lookup"><span data-stu-id="e83ad-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="e83ad-210">**DSC. log**</span><span class="sxs-lookup"><span data-stu-id="e83ad-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="e83ad-211">Berichten met betrekking tot de werking van de lokale Configuration Manager (LCM) en DSC-bron bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="e83ad-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
