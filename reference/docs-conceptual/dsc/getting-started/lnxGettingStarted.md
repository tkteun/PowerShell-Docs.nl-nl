---
ms.date: 01/07/2021
keywords: DSC, Power shell, configuratie, installatie
title: Aan de slag met de desired state Configuration (DSC) voor Linux
description: In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Linux.
ms.openlocfilehash: 6f0dea956b16c0828964a10b43abbbc65879ea33
ms.sourcegitcommit: b9826dcf402db8a2b6d3eab37edb82c6af113343
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2021
ms.locfileid: "98040919"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="ae177-104">Aan de slag met de desired state Configuration (DSC) voor Linux</span><span class="sxs-lookup"><span data-stu-id="ae177-104">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="ae177-105">In dit onderwerp wordt uitgelegd hoe u aan de slag kunt gaan met behulp van Power shell desired state Configuration (DSC) voor Linux.</span><span class="sxs-lookup"><span data-stu-id="ae177-105">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span>
<span data-ttu-id="ae177-106">Zie [aan de slag met Windows Power shell desired state Configuration](../overview/overview.md)(Engelstalig) voor algemene informatie over DSC.</span><span class="sxs-lookup"><span data-stu-id="ae177-106">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="ae177-107">Ondersteunde versies van Linux-besturings systeem</span><span class="sxs-lookup"><span data-stu-id="ae177-107">Supported Linux operation system versions</span></span>

<span data-ttu-id="ae177-108">De volgende versies van Linux-besturings systemen worden ondersteund door DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="ae177-108">The following Linux operating system versions are supported by DSC for Linux.</span></span>

- <span data-ttu-id="ae177-109">CentOS 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="ae177-109">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="ae177-110">Debian GNU/Linux 6, 7 en 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="ae177-110">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="ae177-111">Oracle Linux 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="ae177-111">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="ae177-112">Red Hat Enterprise Linux Server 5, 6 en 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="ae177-112">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="ae177-113">SUSE Linux Enterprise Server 10, 11 en 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="ae177-113">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="ae177-114">Ubuntu Server 12,04 LTS, 14,04 LTS, 16,04 LTS, 18,04 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="ae177-114">Ubuntu Server 12.04 LTS, 14.04 LTS, 16.04 LTS, 18.04 (x86/x64)</span></span>

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="ae177-115">DSC voor Linux installeren</span><span class="sxs-lookup"><span data-stu-id="ae177-115">Installing DSC for Linux</span></span>

<span data-ttu-id="ae177-116">U moet de [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi) installeren voordat u DSC voor Linux installeert.</span><span class="sxs-lookup"><span data-stu-id="ae177-116">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="ae177-117">OMI installeren</span><span class="sxs-lookup"><span data-stu-id="ae177-117">Installing OMI</span></span>

<span data-ttu-id="ae177-118">De desired state Configuration voor Linux vereist de open Management Infrastructure (OMI) CIM-Server versie 1.0.8.1 of hoger.</span><span class="sxs-lookup"><span data-stu-id="ae177-118">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="ae177-119">OMI kan worden gedownload uit de geopende groep: [Open Management Infrastructure (Omi)](https://github.com/Microsoft/omi).</span><span class="sxs-lookup"><span data-stu-id="ae177-119">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="ae177-120">Als u OMI wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="ae177-120">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="ae177-121">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="ae177-121">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="ae177-122">DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="ae177-122">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="ae177-123">De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is geïnstalleerd terwijl de ssl_100 pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ae177-123">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="ae177-124">Voer de opdracht uit om de geïnstalleerde versie van OpenSSL te bepalen `openssl version` .</span><span class="sxs-lookup"><span data-stu-id="ae177-124">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="ae177-125">Voer de volgende opdracht uit om OMI te installeren op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="ae177-125">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="ae177-126">DSC installeren</span><span class="sxs-lookup"><span data-stu-id="ae177-126">Installing DSC</span></span>

<span data-ttu-id="ae177-127">DSC voor Linux kan worden gedownload via de [Power shell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-926) -opslag plaats in de opslag plaats.</span><span class="sxs-lookup"><span data-stu-id="ae177-127">DSC for Linux is available for download from the [PowerShell-DSC-for-Linux](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-926) repository in the repository.</span></span>

<span data-ttu-id="ae177-128">Als u DSC wilt installeren, installeert u het pakket dat geschikt is voor uw Linux-systeem (. rpm of. deb) en OpenSSL-versie (ssl_098 of ssl_100) en architectuur (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="ae177-128">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="ae177-129">RPM-pakketten zijn geschikt voor CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server en Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="ae177-129">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="ae177-130">DEB-pakketten zijn geschikt voor Debian GNU/Linux en Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="ae177-130">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="ae177-131">De ssl_098-pakketten zijn geschikt voor computers waarop OpenSSL 0.9.8 is geïnstalleerd terwijl de ssl_100 pakketten geschikt zijn voor computers waarop OpenSSL 1,0 is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ae177-131">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="ae177-132">Voer de opdracht openssl versie uit om de geïnstalleerde versie van OpenSSL te bepalen.</span><span class="sxs-lookup"><span data-stu-id="ae177-132">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="ae177-133">Voer de volgende opdracht uit om DSC te installeren op een CentOS 7 x64-systeem.</span><span class="sxs-lookup"><span data-stu-id="ae177-133">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="ae177-134">DSC voor Linux gebruiken</span><span class="sxs-lookup"><span data-stu-id="ae177-134">Using DSC for Linux</span></span>

<span data-ttu-id="ae177-135">In de volgende secties wordt uitgelegd hoe u DSC-configuraties op Linux-computers maakt en uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ae177-135">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="ae177-136">Een configuratie-MOF-document maken</span><span class="sxs-lookup"><span data-stu-id="ae177-136">Creating a configuration MOF document</span></span>

<span data-ttu-id="ae177-137">Het sleutel woord Windows Power shell-configuratie wordt gebruikt voor het maken van een configuratie voor Linux-computers, net als bij Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="ae177-137">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="ae177-138">De volgende stappen beschrijven het maken van een configuratie document voor een Linux-computer met behulp van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="ae177-138">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="ae177-139">Importeer de NX-module.</span><span class="sxs-lookup"><span data-stu-id="ae177-139">Import the nx module.</span></span> <span data-ttu-id="ae177-140">De NX Windows Power shell-module bevat het schema voor Built-In resources voor DSC voor Linux, en moet op uw lokale computer zijn geïnstalleerd en in de configuratie worden geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="ae177-140">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="ae177-141">Als u de NX-module wilt installeren, kopieert u de map van de NX-module naar ofwel `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` of `$PSHOME\Modules` .</span><span class="sxs-lookup"><span data-stu-id="ae177-141">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="ae177-142">De NX-module is opgenomen in het installatie pakket voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="ae177-142">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="ae177-143">Als u de NX-module in uw configuratie wilt importeren, gebruikt u de `Import-DSCResource` opdracht:</span><span class="sxs-lookup"><span data-stu-id="ae177-143">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="ae177-144">Definieer een configuratie en Genereer het configuratie document:</span><span class="sxs-lookup"><span data-stu-id="ae177-144">Define a configuration and generate the configuration document:</span></span>

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

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="ae177-145">De configuratie naar de Linux-computer pushen</span><span class="sxs-lookup"><span data-stu-id="ae177-145">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="ae177-146">Configuratie documenten (MOF-bestanden) kunnen worden gepusht naar de Linux-computer met behulp van de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="ae177-146">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="ae177-147">Als u deze cmdlet wilt gebruiken, samen met de cmdlets [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)of [test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) , op afstand naar een Linux-computer, moet u een CIMSession gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ae177-147">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="ae177-148">De cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) wordt gebruikt om een **CimSession** te maken op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="ae177-148">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a **CIMSession** to the Linux computer.</span></span>

<span data-ttu-id="ae177-149">De volgende code laat zien hoe u een CIMSession maakt voor DSC voor Linux.</span><span class="sxs-lookup"><span data-stu-id="ae177-149">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
# $opt = New-CimSessionOption -UseSsl -SkipCACheck -SkipCNCheck -SkipRevocationCheck

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl

$sessParams = @{
    Credential = $credential
    ComputerName = $Node
    Port = 5986
    Authentication = 'basic'
    SessionOption = $opt
    OperationTimeoutSec = 90
}

$Sess = New-CimSession @sessParams
```

> [!NOTE]
> <span data-ttu-id="ae177-150">De gebruikers referenties voor de push-modus moeten de hoofd gebruiker zijn op de Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="ae177-150">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span> <span data-ttu-id="ae177-151">Alleen SSL/TLS-verbindingen worden ondersteund voor DSC voor Linux, de `New-CimSession` moet worden gebruikt met de para meter – UseSSL die is ingesteld op $True.</span><span class="sxs-lookup"><span data-stu-id="ae177-151">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span> <span data-ttu-id="ae177-152">Het SSL-certificaat dat wordt gebruikt door OMI (voor DSC) is opgegeven in het bestand: `/etc/opt/omi/conf/omiserver.conf` met de eigenschappen: pemfile en keyfile.</span><span class="sxs-lookup"><span data-stu-id="ae177-152">The SSL certificate used by OMI (for DSC) is specified in the file: `/etc/opt/omi/conf/omiserver.conf` with the properties: pemfile and keyfile.</span></span> <span data-ttu-id="ae177-153">Als dit certificaat niet wordt vertrouwd door de Windows-computer waarop u de cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) uitvoert, kunt u certificaat validatie negeren met de CimSession-opties: `-SkipCACheck -SkipCNCheck -SkipRevocationCheck`</span><span class="sxs-lookup"><span data-stu-id="ae177-153">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck -SkipCNCheck -SkipRevocationCheck`</span></span>

<span data-ttu-id="ae177-154">Voer de volgende opdracht uit om de DSC-configuratie naar het Linux-knoop punt te pushen.</span><span class="sxs-lookup"><span data-stu-id="ae177-154">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="ae177-155">De configuratie distribueren met een pull-server</span><span class="sxs-lookup"><span data-stu-id="ae177-155">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="ae177-156">Configuraties kunnen worden gedistribueerd naar een Linux-computer met een pull-server, net zoals voor Windows-computers.</span><span class="sxs-lookup"><span data-stu-id="ae177-156">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="ae177-157">Zie [Windows Power shell desired state Configuration pull servers](../pull-server/pullServer.md)(Engelstalig) voor hulp bij het gebruik van een pull-server.</span><span class="sxs-lookup"><span data-stu-id="ae177-157">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="ae177-158">Voor aanvullende informatie en beperkingen met betrekking tot het gebruik van Linux-computers met een pull-Server raadpleegt u de release opmerkingen voor de gewenste status configuratie voor Linux.</span><span class="sxs-lookup"><span data-stu-id="ae177-158">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="ae177-159">Lokaal met configuraties werken</span><span class="sxs-lookup"><span data-stu-id="ae177-159">Working with configurations locally</span></span>

<span data-ttu-id="ae177-160">DSC voor Linux bevat scripts voor het werken met de configuratie van de lokale Linux-computer.</span><span class="sxs-lookup"><span data-stu-id="ae177-160">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="ae177-161">Deze scripts zijn te vinden in `/opt/microsoft/dsc/Scripts` en bevatten het volgende:</span><span class="sxs-lookup"><span data-stu-id="ae177-161">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="ae177-162">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="ae177-162">GetDscConfiguration.py</span></span>

  <span data-ttu-id="ae177-163">Retourneert de huidige configuratie die op de computer is toegepast.</span><span class="sxs-lookup"><span data-stu-id="ae177-163">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="ae177-164">Vergelijkbaar met de cmdlet Windows Power shell cmdlet `Get-DscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ae177-164">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

  `# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="ae177-165">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="ae177-165">GetDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="ae177-166">Retourneert de huidige meta-configuratie die op de computer is toegepast.</span><span class="sxs-lookup"><span data-stu-id="ae177-166">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="ae177-167">Vergelijkbaar met de cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae177-167">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

  `# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="ae177-168">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="ae177-168">InstallModule.py</span></span>

  <span data-ttu-id="ae177-169">Hiermee wordt een aangepaste DSC-resource module geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ae177-169">Installs a custom DSC resource module.</span></span> <span data-ttu-id="ae177-170">Vereist het pad naar een zip-bestand met de module gedeelde object bibliotheek en schema-MOF-bestanden.</span><span class="sxs-lookup"><span data-stu-id="ae177-170">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

  `# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="ae177-171">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="ae177-171">RemoveModule.py</span></span>

  <span data-ttu-id="ae177-172">Hiermee verwijdert u een aangepaste DSC-resource module.</span><span class="sxs-lookup"><span data-stu-id="ae177-172">Removes a custom DSC resource module.</span></span> <span data-ttu-id="ae177-173">Vereist de naam van de module die u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ae177-173">Requires the name of the module to remove.</span></span>

  `# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="ae177-174">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="ae177-174">StartDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="ae177-175">Past een MOF-configuratie bestand op de computer toe.</span><span class="sxs-lookup"><span data-stu-id="ae177-175">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="ae177-176">Vergelijkbaar met de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="ae177-176">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="ae177-177">Vereist het pad naar de configuratie-MOF die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="ae177-177">Requires the path to the configuration MOF to apply.</span></span>

  `# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="ae177-178">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="ae177-178">SetDscLocalConfigurationManager.py</span></span>

  <span data-ttu-id="ae177-179">Past een MOF-bestand van de meta configuratie toe op de computer.</span><span class="sxs-lookup"><span data-stu-id="ae177-179">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="ae177-180">Vergelijkbaar met de cmdlet [set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) .</span><span class="sxs-lookup"><span data-stu-id="ae177-180">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="ae177-181">Vereist het pad naar de meta configuratie-MOF die moet worden toegepast.</span><span class="sxs-lookup"><span data-stu-id="ae177-181">Requires the path to the Meta Configuration MOF to apply.</span></span>

  `# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="ae177-182">Power shell desired state Configuration voor Linux-logboek bestanden</span><span class="sxs-lookup"><span data-stu-id="ae177-182">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="ae177-183">De volgende logboek bestanden worden gegenereerd voor DSC voor Linux-berichten.</span><span class="sxs-lookup"><span data-stu-id="ae177-183">The following log files are generated for DSC for Linux messages.</span></span>

|     <span data-ttu-id="ae177-184">Logboekbestand</span><span class="sxs-lookup"><span data-stu-id="ae177-184">Log file</span></span>      |     <span data-ttu-id="ae177-185">Directory</span><span class="sxs-lookup"><span data-stu-id="ae177-185">Directory</span></span>      |                                               <span data-ttu-id="ae177-186">Description</span><span class="sxs-lookup"><span data-stu-id="ae177-186">Description</span></span>                                                |
| ----------------- | ------------------ | -------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="ae177-187">**omiserver. log**</span><span class="sxs-lookup"><span data-stu-id="ae177-187">**omiserver.log**</span></span> | `/var/opt/omi/log` | <span data-ttu-id="ae177-188">Berichten met betrekking tot de werking van de OMI CIM-server.</span><span class="sxs-lookup"><span data-stu-id="ae177-188">Messages relating to the operation of the OMI CIM server.</span></span>                                                |
| <span data-ttu-id="ae177-189">**DSC. log**</span><span class="sxs-lookup"><span data-stu-id="ae177-189">**dsc.log**</span></span>       | `/var/opt/omi/log` | <span data-ttu-id="ae177-190">Berichten met betrekking tot de werking van de lokale Configuration Manager (LCM) en DSC-bron bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ae177-190">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span> |
