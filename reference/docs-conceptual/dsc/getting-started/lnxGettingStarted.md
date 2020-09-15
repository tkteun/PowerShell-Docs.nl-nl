---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Aan de slag met de desired state Configuration (DSC) voor Linux
ms.openlocfilehash: 64657dda04fa2df97fa2ad7c7a5c2d15b66a270a
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301332"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="5a82e-103">Aan de slag met de desired state Configuration (DSC) voor Linux</span><span class="sxs-lookup"><span data-stu-id="5a82e-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="5a82e-104">In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5a82e-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="5a82e-105">Zie [aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)(Engelstalig) voor algemene informatie over DSC.</span><span class="sxs-lookup"><span data-stu-id="5a82e-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="5a82e-106">Ondersteunde versies van Linux-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="5a82e-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="5a82e-107">De volgende versies van Linux-besturings systemen worden ondersteund door DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5a82e-107">The following Linux operating system versions are supported by DSC for Linux.</span></span>

- <span data-ttu-id="5a82e-108">CentOS 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5a82e-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="5a82e-109">Debian GNU/Linux 6, 7 en 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5a82e-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="5a82e-110">Oracle Linux 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5a82e-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="5a82e-111">Red Hat Enterprise Linux Server 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5a82e-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="5a82e-112">SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5a82e-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="5a82e-113">Ubuntu Server 12,04 LTS, 14,04 LTS, 16,04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="5a82e-113">Ubuntu Server 12.04 LTS, 14.04 LTS, 16.04 LTS (x86/x64)</span></span>

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="5a82e-114">DSC voor Linux installeren</span><span class="sxs-lookup"><span data-stu-id="5a82e-114">Installing DSC for Linux</span></span>

<span data-ttu-id="5a82e-115">U moet de [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi) installeren voordat u DSC voor Linux installeert.</span><span class="sxs-lookup"><span data-stu-id="5a82e-115">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="5a82e-116">OMI installeren</span><span class="sxs-lookup"><span data-stu-id="5a82e-116">Installing OMI</span></span>

<span data-ttu-id="5a82e-117">De desired state Configuration voor Linux vereist de open Management Infrastructure (OMI) CIM-Server versie 1.0.8.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="5a82e-117">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="5a82e-118">OMI kan worden gedownload uit de geopende groep: [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="5a82e-118">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="5a82e-119">Als u OMI wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="5a82e-119">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="5a82e-120">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="5a82e-120">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="5a82e-121">DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="5a82e-121">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="5a82e-122">De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is geïnstalleerd terwijl de ssl_100 pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5a82e-122">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="5a82e-123">Voer de opdracht uit om de geïnstalleerde versie van OpenSSL te bepalen `openssl version` .</span><span class="sxs-lookup"><span data-stu-id="5a82e-123">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="5a82e-124">Voer de volgende opdracht uit om OMI te installeren op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="5a82e-124">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="5a82e-125">DSC installeren</span><span class="sxs-lookup"><span data-stu-id="5a82e-125">Installing DSC</span></span>

<span data-ttu-id="5a82e-126">DSC voor Linux kan [hier](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294)worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="5a82e-126">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="5a82e-127">Als u DSC wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="5a82e-127">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="5a82e-128">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="5a82e-128">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="5a82e-129">DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="5a82e-129">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="5a82e-130">De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is geïnstalleerd terwijl de ssl_100 pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5a82e-130">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="5a82e-131">Voer de opdracht openssl versie uit om de geïnstalleerde versie van OpenSSL te bepalen.</span><span class="sxs-lookup"><span data-stu-id="5a82e-131">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="5a82e-132">Voer de volgende opdracht uit om DSC te installeren op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="5a82e-132">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="5a82e-133">DSC voor Linux gebruiken</span><span class="sxs-lookup"><span data-stu-id="5a82e-133">Using DSC for Linux</span></span>

<span data-ttu-id="5a82e-134">In de volgende secties wordt uitgelegd hoe u DSC-configuraties op Linux-computers maakt en uitvoert.</span><span class="sxs-lookup"><span data-stu-id="5a82e-134">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="5a82e-135">Een configuratie-MOF-document maken</span><span class="sxs-lookup"><span data-stu-id="5a82e-135">Creating a configuration MOF document</span></span>

<span data-ttu-id="5a82e-136">Het sleutel woord Windows Power shell-configuratie wordt gebruikt voor het maken van een configuratie voor Linux-computers, net als bij Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="5a82e-136">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="5a82e-137">De volgende stappen beschrijven het maken van een configuratie document voor een Linux-computer met behulp van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="5a82e-137">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="5a82e-138">Importeer de NX-module.</span><span class="sxs-lookup"><span data-stu-id="5a82e-138">Import the nx module.</span></span> <span data-ttu-id="5a82e-139">De NX Windows Power shell-module bevat het schema voor ingebouwde resources voor DSC voor Linux en moet worden geïnstalleerd op uw lokale computer en worden geïmporteerd in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="5a82e-139">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="5a82e-140">Als u de NX-module wilt installeren, kopieert u de map van de NX-module naar ofwel `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` of `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="5a82e-140">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="5a82e-141">De NX-module is opgenomen in het installatie pakket voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5a82e-141">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="5a82e-142">Als u de NX-module in uw configuratie wilt importeren, gebruikt u de `Import-DSCResource` opdracht:</span><span class="sxs-lookup"><span data-stu-id="5a82e-142">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="5a82e-143">Definieer een configuratie en Genereer het configuratie document:</span><span class="sxs-lookup"><span data-stu-id="5a82e-143">Define a configuration and generate the configuration document:</span></span>

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

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="5a82e-144">De configuratie naar de Linux-computer pushen</span><span class="sxs-lookup"><span data-stu-id="5a82e-144">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="5a82e-145">Configuratie documenten (MOF-bestanden) kunnen worden gepusht naar de Linux-computer met behulp van de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="5a82e-145">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="5a82e-146">Als u deze cmdlet wilt gebruiken, samen met de cmdlets [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)of [test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) , op afstand naar een Linux-computer, moet u een CIMSession gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5a82e-146">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="5a82e-147">De cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) wordt gebruikt om een CimSession te maken op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="5a82e-147">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="5a82e-148">De volgende code laat zien hoe u een CIMSession maakt voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5a82e-148">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

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
> <span data-ttu-id="5a82e-149">De gebruikers referenties voor de push-modus moeten de hoofd gebruiker zijn op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="5a82e-149">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="5a82e-150">Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, de `New-CimSession` moet worden gebruikt met de para meter – UseSSL die is ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="5a82e-150">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="5a82e-151">Het SSL-certificaat dat wordt gebruikt door OMI (voor DSC) is opgegeven in het bestand: `/etc/opt/omi/conf/omiserver.conf` met de eigenschappen: pemfile en keyfile.</span><span class="sxs-lookup"><span data-stu-id="5a82e-151">The SSL certificate used by OMI (for DSC) is specified in the file: `/etc/opt/omi/conf/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="5a82e-152">Als dit certificaat niet wordt vertrouwd door de Windows-computer waarop u de cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) uitvoert, kunt u certificaat validatie negeren met de CimSession-opties: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span><span class="sxs-lookup"><span data-stu-id="5a82e-152">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="5a82e-153">Voer de volgende opdracht uit om de DSC-configuratie naar het Linux-knoop punt te pushen.</span><span class="sxs-lookup"><span data-stu-id="5a82e-153">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="5a82e-154">De configuratie distribueren met een pull-server</span><span class="sxs-lookup"><span data-stu-id="5a82e-154">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="5a82e-155">Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net zoals voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="5a82e-155">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="5a82e-156">Zie [Windows Power shell desired state Configuration pull servers](../pull-server/pullServer.md)(Engelstalig) voor hulp bij het gebruik van een pull-server.</span><span class="sxs-lookup"><span data-stu-id="5a82e-156">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="5a82e-157">Voor aanvullende informatie en beperkingen met betrekking tot het gebruik van Linux-computers met een pull-Server raadpleegt u de release opmerkingen voor de gewenste status configuratie voor Linux.</span><span class="sxs-lookup"><span data-stu-id="5a82e-157">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="5a82e-158">Lokaal met configuraties werken</span><span class="sxs-lookup"><span data-stu-id="5a82e-158">Working with configurations locally</span></span>

<span data-ttu-id="5a82e-159">DSC voor Linux bevat scripts voor het werken met de configuratie van de lokale Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="5a82e-159">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="5a82e-160">Deze scripts zijn te vinden in `/opt/microsoft/dsc/Scripts` en bevatten het volgende:</span><span class="sxs-lookup"><span data-stu-id="5a82e-160">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="5a82e-161">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="5a82e-161">GetDscConfiguration.py</span></span>

<span data-ttu-id="5a82e-162">Retourneert de huidige configuratie die op de computer is toegepast.</span><span class="sxs-lookup"><span data-stu-id="5a82e-162">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="5a82e-163">Vergelijkbaar met de cmdlet Windows Power shell cmdlet `Get-DscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5a82e-163">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="5a82e-164">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="5a82e-164">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="5a82e-165">Retourneert de huidige meta-configuratie die op de computer is toegepast.</span><span class="sxs-lookup"><span data-stu-id="5a82e-165">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="5a82e-166">Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a82e-166">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="5a82e-167">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="5a82e-167">InstallModule.py</span></span>

<span data-ttu-id="5a82e-168">Hiermee wordt een aangepaste DSC-resource module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="5a82e-168">Installs a custom DSC resource module.</span></span> <span data-ttu-id="5a82e-169">Vereist het pad naar een zip-bestand met de module gedeelde object bibliotheek en schema-MOF-bestanden.</span><span class="sxs-lookup"><span data-stu-id="5a82e-169">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="5a82e-170">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="5a82e-170">RemoveModule.py</span></span>

<span data-ttu-id="5a82e-171">Hiermee verwijdert u een aangepaste DSC-resource module.</span><span class="sxs-lookup"><span data-stu-id="5a82e-171">Removes a custom DSC resource module.</span></span> <span data-ttu-id="5a82e-172">Vereist de naam van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5a82e-172">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="5a82e-173">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="5a82e-173">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="5a82e-174">Past een MOF-configuratie bestand op de computer toe.</span><span class="sxs-lookup"><span data-stu-id="5a82e-174">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="5a82e-175">Vergelijkbaar met de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="5a82e-175">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="5a82e-176">Vereist het pad naar de configuratie-MOF die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="5a82e-176">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="5a82e-177">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="5a82e-177">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="5a82e-178">Past een MOF-bestand van de meta configuratie toe op de computer.</span><span class="sxs-lookup"><span data-stu-id="5a82e-178">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="5a82e-179">Vergelijkbaar met de cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="5a82e-179">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="5a82e-180">Vereist het pad naar de meta configuratie-MOF die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="5a82e-180">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="5a82e-181">Power shell desired state Configuration voor Linux-logboek bestanden</span><span class="sxs-lookup"><span data-stu-id="5a82e-181">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="5a82e-182">De volgende logboek bestanden worden gegenereerd voor DSC voor Linux-berichten.</span><span class="sxs-lookup"><span data-stu-id="5a82e-182">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="5a82e-183">Logboekbestand</span><span class="sxs-lookup"><span data-stu-id="5a82e-183">Log file</span></span>|<span data-ttu-id="5a82e-184">Directory</span><span class="sxs-lookup"><span data-stu-id="5a82e-184">Directory</span></span>|<span data-ttu-id="5a82e-185">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5a82e-185">Description</span></span>|
|---|---|---|
|<span data-ttu-id="5a82e-186">**omiserver. log**</span><span class="sxs-lookup"><span data-stu-id="5a82e-186">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="5a82e-187">Berichten met betrekking tot de werking van de OMI CIM-server.</span><span class="sxs-lookup"><span data-stu-id="5a82e-187">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="5a82e-188">**DSC. log**</span><span class="sxs-lookup"><span data-stu-id="5a82e-188">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="5a82e-189">Berichten met betrekking tot de werking van de lokale Configuration Manager (LCM) en DSC-bron bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="5a82e-189">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
