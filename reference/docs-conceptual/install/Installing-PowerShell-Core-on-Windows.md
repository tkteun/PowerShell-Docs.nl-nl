---
title: PowerShell installeren in Windows
description: Informatie over het installeren van PowerShell in Windows
ms.date: 04/27/2021
ms.openlocfilehash: 24f5687411004ebc6f84a76493ded46b7b30b0d2
ms.sourcegitcommit: afbcc8675107ad9ec6afff91ef4a42b2953121cc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108121642"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="26fd0-103">PowerShell installeren in Windows</span><span class="sxs-lookup"><span data-stu-id="26fd0-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="26fd0-104">Er zijn meerdere manieren om PowerShell in Windows te installeren.</span><span class="sxs-lookup"><span data-stu-id="26fd0-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26fd0-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="26fd0-105">Prerequisites</span></span>

<span data-ttu-id="26fd0-106">De nieuwste versie van PowerShell wordt ondersteund in Windows 7 SP1, Server 2008 R2 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="26fd0-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="26fd0-107">Aan de volgende vereisten moet worden voldaan om powershell voor remoting via WSMan in te kunnenschakelen:</span><span class="sxs-lookup"><span data-stu-id="26fd0-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="26fd0-108">Installeer universal [C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) in Windows-versies die voorafgaan aan Windows 10.</span><span class="sxs-lookup"><span data-stu-id="26fd0-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="26fd0-109">Deze is beschikbaar via direct downloaden of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="26fd0-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="26fd0-110">Dit pakket is al geïnstalleerd op volledig gepatchte systemen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="26fd0-111">Installeer de Windows Management Framework (WMF) 4.0 of hoger op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="26fd0-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="26fd0-112">Zie WMF-overzicht voor meer informatie [over WMF.](/powershell/scripting/wmf/overview)</span><span class="sxs-lookup"><span data-stu-id="26fd0-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="26fd0-113">Het installatiepakket downloaden</span><span class="sxs-lookup"><span data-stu-id="26fd0-113">Download the installer package</span></span>

<span data-ttu-id="26fd0-114">Als u PowerShell in Windows wilt installeren, downloadt u [het meest][] recente installatiepakket van GitHub.</span><span class="sxs-lookup"><span data-stu-id="26fd0-114">To install PowerShell on Windows, download the [latest][] install package from GitHub.</span></span> <span data-ttu-id="26fd0-115">U kunt ook de nieuwste [preview-versie][] vinden.</span><span class="sxs-lookup"><span data-stu-id="26fd0-115">You can also find the latest [preview][] version.</span></span> <span data-ttu-id="26fd0-116">Schuif omlaag naar de **sectie Assets** van de pagina Release.</span><span class="sxs-lookup"><span data-stu-id="26fd0-116">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="26fd0-117">De **sectie** Assets is mogelijk samengevouwen, dus mogelijk moet u erop klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-117">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="26fd0-118"><a id="msi" />Het MSI-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="26fd0-118"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="26fd0-119">Het MSI-bestand ziet er als `PowerShell-<version>-win-<os-arch>.msi` uit.</span><span class="sxs-lookup"><span data-stu-id="26fd0-119">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="26fd0-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="26fd0-120">For example:</span></span>

- `PowerShell-7.1.3-win-x64.msi`
- `PowerShell-7.1.3-win-x86.msi`

<span data-ttu-id="26fd0-121">Dubbelklik na het downloaden op het installatieprogramma en volg de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-121">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="26fd0-122">Het installatieprogramma maakt een snelkoppeling in het menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="26fd0-122">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="26fd0-123">Het pakket is standaard geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="26fd0-123">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="26fd0-124">U kunt PowerShell starten via het startmenu of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="26fd0-124">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="26fd0-125">PowerShell 7.1 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows PowerShell 5.1.</span><span class="sxs-lookup"><span data-stu-id="26fd0-125">PowerShell 7.1 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span>
> <span data-ttu-id="26fd0-126">PowerShell 7.1 is een in-place upgrade powershell 6.x vervangt.</span><span class="sxs-lookup"><span data-stu-id="26fd0-126">PowerShell 7.1 is an in-place upgrade that replaces PowerShell 6.x.</span></span> <span data-ttu-id="26fd0-127">of PowerShell 7.0.</span><span class="sxs-lookup"><span data-stu-id="26fd0-127">or PowerShell 7.0.</span></span>
>
> - <span data-ttu-id="26fd0-128">PowerShell 7.1 is geïnstalleerd op `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="26fd0-128">PowerShell 7.1 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="26fd0-129">De `$env:ProgramFiles\PowerShell\7` map wordt toegevoegd aan `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="26fd0-129">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="26fd0-130">De `$env:ProgramFiles\PowerShell\6` map is verwijderd</span><span class="sxs-lookup"><span data-stu-id="26fd0-130">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="26fd0-131">Als u PowerShell 7.1 naast andere versies moet uitvoeren, [](#zip) gebruikt u de zip-installatiemethode om de andere versie in een andere map te installeren.</span><span class="sxs-lookup"><span data-stu-id="26fd0-131">If you need to run PowerShell 7.1 side-by-side with other versions, use the [ZIP install](#zip) method to install the other version to a different folder.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="26fd0-132">Beheer installeren vanaf de opdrachtregel</span><span class="sxs-lookup"><span data-stu-id="26fd0-132">Administrative install from the command line</span></span>

<span data-ttu-id="26fd0-133">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdrachtregel, zodat beheerders pakketten kunnen implementeren zonder tussenkomst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="26fd0-133">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="26fd0-134">Het MSI-pakket bevat de volgende eigenschappen om de installatieopties te bepalen:</span><span class="sxs-lookup"><span data-stu-id="26fd0-134">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="26fd0-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL:** met deze eigenschap bepaalt u de optie voor het toevoegen van het **open PowerShell-item** aan het contextmenu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="26fd0-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="26fd0-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL:** met deze eigenschap bepaalt u de optie voor het toevoegen van het item Uitvoeren met **PowerShell** aan het contextmenu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="26fd0-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** - This property controls the option for adding the **Run with PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="26fd0-137">**ENABLE_PSREMOTING:** met deze eigenschap bepaalt u de optie voor het inschakelen van de toegang tot powershell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="26fd0-137">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="26fd0-138">**REGISTER_MANIFEST:** met deze eigenschap bepaalt u de optie voor het registreren van het Windows Event Logging-manifest.</span><span class="sxs-lookup"><span data-stu-id="26fd0-138">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="26fd0-139">In het volgende voorbeeld ziet u hoe u PowerShell op de stille manier installeert met alle installatieopties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="26fd0-139">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.1.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="26fd0-140">Zie Opdrachtregelopties voor een volledige lijst met `Msiexec.exe` [opdrachtregelopties voor](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="26fd0-140">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="26fd0-141">Registersleutels die tijdens de installatie zijn gemaakt</span><span class="sxs-lookup"><span data-stu-id="26fd0-141">Registry keys created during installation</span></span>

<span data-ttu-id="26fd0-142">Vanaf PowerShell 7.1 maakt het MSI-pakket registersleutels waarin de installatielocatie en versie van PowerShell worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-142">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="26fd0-143">Deze waarden bevinden zich in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` .</span><span class="sxs-lookup"><span data-stu-id="26fd0-143">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="26fd0-144">De waarde van `<GUID>` is uniek voor elk buildtype (release of preview), de belangrijkste versie en architectuur.</span><span class="sxs-lookup"><span data-stu-id="26fd0-144">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="26fd0-145">Release</span><span class="sxs-lookup"><span data-stu-id="26fd0-145">Release</span></span>    | <span data-ttu-id="26fd0-146">Architectuur</span><span class="sxs-lookup"><span data-stu-id="26fd0-146">Architecture</span></span> |                                          <span data-ttu-id="26fd0-147">Registersleutel</span><span class="sxs-lookup"><span data-stu-id="26fd0-147">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="26fd0-148">7.1.x Release</span><span class="sxs-lookup"><span data-stu-id="26fd0-148">7.1.x Release</span></span> |     <span data-ttu-id="26fd0-149">x86</span><span class="sxs-lookup"><span data-stu-id="26fd0-149">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="26fd0-150">7.1.x Release</span><span class="sxs-lookup"><span data-stu-id="26fd0-150">7.1.x Release</span></span> |     <span data-ttu-id="26fd0-151">x64</span><span class="sxs-lookup"><span data-stu-id="26fd0-151">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="26fd0-152">7.1.x Preview</span><span class="sxs-lookup"><span data-stu-id="26fd0-152">7.1.x Preview</span></span> |     <span data-ttu-id="26fd0-153">x86</span><span class="sxs-lookup"><span data-stu-id="26fd0-153">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="26fd0-154">7.1.x Preview</span><span class="sxs-lookup"><span data-stu-id="26fd0-154">7.1.x Preview</span></span> |     <span data-ttu-id="26fd0-155">x64</span><span class="sxs-lookup"><span data-stu-id="26fd0-155">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="26fd0-156">Dit kan worden gebruikt door beheerders en ontwikkelaars om het pad naar PowerShell te vinden.</span><span class="sxs-lookup"><span data-stu-id="26fd0-156">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="26fd0-157">De waarden zijn hetzelfde voor alle preview- en `<GUID>` secundaire versiereleases.</span><span class="sxs-lookup"><span data-stu-id="26fd0-157">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="26fd0-158">De `<GUID>` waarden worden voor elke belangrijke release gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="26fd0-158">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="26fd0-159"><a id="zip" />Het ZIP-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="26fd0-159"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="26fd0-160">Binaire ZIP-archieven van PowerShell worden geleverd om geavanceerde implementatiescenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="26fd0-160">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="26fd0-161">Download een van de volgende ZIP-archieven op de pagina [releases][releases].</span><span class="sxs-lookup"><span data-stu-id="26fd0-161">Download one of the following ZIP archives from the [releases][releases] page.</span></span>

- <span data-ttu-id="26fd0-162">PowerShell-7.1.3-win-x64.zip</span><span class="sxs-lookup"><span data-stu-id="26fd0-162">PowerShell-7.1.3-win-x64.zip</span></span>
- <span data-ttu-id="26fd0-163">PowerShell-7.1.3-win-x86.zip</span><span class="sxs-lookup"><span data-stu-id="26fd0-163">PowerShell-7.1.3-win-x86.zip</span></span>
- <span data-ttu-id="26fd0-164">PowerShell-7.1.3-win-arm64.zip</span><span class="sxs-lookup"><span data-stu-id="26fd0-164">PowerShell-7.1.3-win-arm64.zip</span></span>
- <span data-ttu-id="26fd0-165">PowerShell-7.1.3-win-arm32.zip</span><span class="sxs-lookup"><span data-stu-id="26fd0-165">PowerShell-7.1.3-win-arm32.zip</span></span>

<span data-ttu-id="26fd0-166">Afhankelijk van hoe u het bestand downloadt, moet u het bestand mogelijk deblokkeren met behulp van de `Unblock-File` cmdlet .</span><span class="sxs-lookup"><span data-stu-id="26fd0-166">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="26fd0-167">Voer de inhoud uit op de locatie van uw keuze en voer `pwsh.exe` deze uit.</span><span class="sxs-lookup"><span data-stu-id="26fd0-167">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="26fd0-168">In tegenstelling tot het installeren van de MSI-pakketten, wordt bij het installeren van het ZIP-archief niet op vereisten gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="26fd0-168">Unlike installing the MSI packages, installing the ZIP archive doesn't check for prerequisites.</span></span> <span data-ttu-id="26fd0-169">Voor een goede werking van remoting via WSMan moet u ervoor zorgen dat u aan de [vereisten hebt voldaan.](#prerequisites)</span><span class="sxs-lookup"><span data-stu-id="26fd0-169">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

<span data-ttu-id="26fd0-170">Gebruik deze methode om de op ARM gebaseerde versie van PowerShell te installeren op computers zoals de Microsoft Surface Pro X. Voor het beste resultaat installeert u PowerShell in de map `$env:ProgramFiles\PowerShell\7` to.</span><span class="sxs-lookup"><span data-stu-id="26fd0-170">Use this method to install the ARM-based version of PowerShell on computers like the Microsoft Surface Pro X. For best results, install PowerShell to the to `$env:ProgramFiles\PowerShell\7` folder.</span></span>

> [!NOTE]
> <span data-ttu-id="26fd0-171">U kunt deze methode gebruiken om elke versie van PowerShell te installeren, inclusief de nieuwste versie:</span><span class="sxs-lookup"><span data-stu-id="26fd0-171">You can use this method to install any version of PowerShell including the latest:</span></span>
> - <span data-ttu-id="26fd0-172">Stabiele release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)</span><span class="sxs-lookup"><span data-stu-id="26fd0-172">Stable release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)</span></span>
> - <span data-ttu-id="26fd0-173">Preview-versie: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)</span><span class="sxs-lookup"><span data-stu-id="26fd0-173">Preview release: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)</span></span>
> - <span data-ttu-id="26fd0-174">LTS-release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)</span><span class="sxs-lookup"><span data-stu-id="26fd0-174">LTS release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="26fd0-175">Implementeren op Windows 10 IoT Enterprise</span><span class="sxs-lookup"><span data-stu-id="26fd0-175">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="26fd0-176">Windows 10 IoT Enterprise wordt geleverd met Windows PowerShell, die we kunnen gebruiken om PowerShell 7 te implementeren.</span><span class="sxs-lookup"><span data-stu-id="26fd0-176">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="26fd0-177">Maken `PSSession` om het doelapparaat te maken</span><span class="sxs-lookup"><span data-stu-id="26fd0-177">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="26fd0-178">Het ZIP-pakket naar het apparaat kopiëren</span><span class="sxs-lookup"><span data-stu-id="26fd0-178">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="26fd0-179">Verbinding maken met het apparaat en het archief uitbreiden</span><span class="sxs-lookup"><span data-stu-id="26fd0-179">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="26fd0-180">Moting instellen voor PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="26fd0-180">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. <span data-ttu-id="26fd0-181">Verbinding maken met het PowerShell 7-eindpunt op het apparaat</span><span class="sxs-lookup"><span data-stu-id="26fd0-181">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="26fd0-182">Implementeren op Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="26fd0-182">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="26fd0-183">Windows 10 IoT Core voegt Windows PowerShell toe wanneer u de _functie IOT_POWERSHELL,_ die we kunnen gebruiken om PowerShell 7 te implementeren.</span><span class="sxs-lookup"><span data-stu-id="26fd0-183">Windows 10 IoT Core adds Windows PowerShell when you include _IOT_POWERSHELL_ feature, which we can use to deploy PowerShell 7.</span></span> <span data-ttu-id="26fd0-184">De bovenstaande stappen voor Windows 10 IoT Enterprise kunnen ook worden gevolgd voor IoT Core.</span><span class="sxs-lookup"><span data-stu-id="26fd0-184">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="26fd0-185">Als u de nieuwste versie van PowerShell wilt toevoegen aan de verzendafbeelding, gebruikt u de opdracht [Import-PSCoreRelease][] om het pakket op te nemen in de workarea en voegt u OPENSRC_POWERSHELL-functie _toe_ aan uw afbeelding.</span><span class="sxs-lookup"><span data-stu-id="26fd0-185">For adding the latest PowerShell in the shipping image, use [Import-PSCoreRelease][] command to include the package in the workarea and add _OPENSRC_POWERSHELL_ feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="26fd0-186">Voor arm64-architectuur wordt Windows PowerShell niet toegevoegd wanneer u de _IOT_POWERSHELL._</span><span class="sxs-lookup"><span data-stu-id="26fd0-186">For ARM64 architecture, Windows PowerShell is not added when you include _IOT_POWERSHELL_.</span></span> <span data-ttu-id="26fd0-187">De zip-installatie werkt dus niet.</span><span class="sxs-lookup"><span data-stu-id="26fd0-187">So the zip based install will not work.</span></span> <span data-ttu-id="26fd0-188">U moet de opdracht gebruiken `Import-PSCoreRelease` om deze toe te voegen aan de afbeelding.</span><span class="sxs-lookup"><span data-stu-id="26fd0-188">You will need to use `Import-PSCoreRelease` command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="26fd0-189">Implementeren op Nano Server</span><span class="sxs-lookup"><span data-stu-id="26fd0-189">Deploying on Nano Server</span></span>

<span data-ttu-id="26fd0-190">In deze instructies wordt ervan uitgenomen dat de Nano Server een 'headless' besturingssysteem is met een versie van PowerShell die al wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="26fd0-190">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="26fd0-191">Zie de Documentatie over [nanoserver-Image Builder](/windows-server/get-started/deploy-nano-server) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="26fd0-191">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="26fd0-192">Binaire PowerShell-bestanden kunnen op twee verschillende manieren worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="26fd0-192">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="26fd0-193">Offline: bevestig de Nano Server-VHD en los de inhoud van het zip-bestand uit op de locatie die u hebt gekozen in de bevestigingsafbeelding.</span><span class="sxs-lookup"><span data-stu-id="26fd0-193">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="26fd0-194">Online: breng het ZIP-bestand over via een PowerShell-sessie en pakken het uit op de door u gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="26fd0-194">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="26fd0-195">In beide gevallen hebt u het Windows 10 x64 ZIP-releasepakket nodig.</span><span class="sxs-lookup"><span data-stu-id="26fd0-195">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="26fd0-196">Voer de opdrachten uit in een administrator-exemplaar van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26fd0-196">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="26fd0-197">Offlineimplementatie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="26fd0-197">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="26fd0-198">Gebruik uw favoriete zip-hulpprogramma om het pakket uit te pak in een map in de bevestigd Nano Server-afbeelding.</span><span class="sxs-lookup"><span data-stu-id="26fd0-198">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="26fd0-199">Ontkoppel de afbeelding en start deze op.</span><span class="sxs-lookup"><span data-stu-id="26fd0-199">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="26fd0-200">Maak verbinding met het ingebouwde exemplaar van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26fd0-200">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="26fd0-201">Volg de instructies voor het maken van een eindpunt voor remoting met behulp van [de 'techniek van een ander exemplaar'.][]</span><span class="sxs-lookup"><span data-stu-id="26fd0-201">Follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="26fd0-202">Onlineimplementatie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="26fd0-202">Online Deployment of PowerShell</span></span>

<span data-ttu-id="26fd0-203">Implementeer PowerShell in Nano Server met behulp van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-203">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="26fd0-204">Verbinding maken met het ingebouwde exemplaar van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="26fd0-204">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="26fd0-205">Het bestand kopiëren naar het Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="26fd0-205">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="26fd0-206">Voer de sessie in</span><span class="sxs-lookup"><span data-stu-id="26fd0-206">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="26fd0-207">Het ZIP-bestand uitpakken</span><span class="sxs-lookup"><span data-stu-id="26fd0-207">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="26fd0-208">Als u op WSMan gebaseerde remoting wilt, volgt u de instructies voor het maken van een remoting-eindpunt met behulp van [de 'andere instantietechniek'.][]</span><span class="sxs-lookup"><span data-stu-id="26fd0-208">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="26fd0-209">Installeren als een .NET Global-hulpprogramma</span><span class="sxs-lookup"><span data-stu-id="26fd0-209">Install as a .NET Global tool</span></span>

<span data-ttu-id="26fd0-210">Als u de .NET Core SDK [hebt](/dotnet/core/sdk) geïnstalleerd, kunt u PowerShell eenvoudig installeren als [een .NET Global-hulpprogramma.](/dotnet/core/tools/global-tools)</span><span class="sxs-lookup"><span data-stu-id="26fd0-210">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="26fd0-211">Het installatieprogramma dotnet voegt toe `$env:USERPROFILE\.dotnet\tools` aan uw `$env:PATH` omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="26fd0-211">The dotnet tool installer adds `$env:USERPROFILE\.dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="26fd0-212">De momenteel lopende shell heeft echter niet de bijgewerkte `$env:PATH` .</span><span class="sxs-lookup"><span data-stu-id="26fd0-212">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="26fd0-213">U kunt PowerShell starten vanuit een nieuwe shell door te `pwsh` typen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-213">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-the-windows-package-manager"></a><span data-ttu-id="26fd0-214">Installeer PowerShell via de Windows-pakketbeheerder</span><span class="sxs-lookup"><span data-stu-id="26fd0-214">Install PowerShell via the Windows Package Manager</span></span>

<span data-ttu-id="26fd0-215">Het `winget` opdrachtregelprogramma stelt ontwikkelaars in staat om toepassingen te ontdekken, installeren, upgraden, verwijderen en configureren op Windows 10 computers.</span><span class="sxs-lookup"><span data-stu-id="26fd0-215">The `winget` command-line tool enables developers to discover, install, upgrade, remove, and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="26fd0-216">Dit hulpprogramma is de clientinterface voor de Windows-pakketbeheerder service.</span><span class="sxs-lookup"><span data-stu-id="26fd0-216">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="26fd0-217">Windows-pakketbeheerder en het hulpprogramma zijn in openbare preview en kunnen aanzienlijk worden `winget` gewijzigd voordat ze algemeen beschikbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="26fd0-217">Windows Package Manager and the `winget` tool are in public preview and may be substantially modified before they are generally available.</span></span> <span data-ttu-id="26fd0-218">Zie de [documentatie voor][winget] een lijst met systeemvereisten en installatie-instructies.</span><span class="sxs-lookup"><span data-stu-id="26fd0-218">See the [documentation][winget] for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="26fd0-219">De volgende opdrachten kunnen worden gebruikt om PowerShell te installeren met behulp van de `winget` gepubliceerde pakketten:</span><span class="sxs-lookup"><span data-stu-id="26fd0-219">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="26fd0-220">Zoek naar de nieuwste versie van PowerShell</span><span class="sxs-lookup"><span data-stu-id="26fd0-220">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name                      Id                                Version
   ---------------------------------------------------------------------------
   PowerShell                Microsoft.PowerShell              7.1.3
   PowerShell Preview (MSIX) Microsoft.PowerShell-Preview-MSIX 7.0.2
   PowerShell-Preview        Microsoft.PowerShell-Preview      7.2.0-preview.5
   ```

1. <span data-ttu-id="26fd0-221">Een versie van PowerShell installeren met behulp van de `--exact` parameter</span><span class="sxs-lookup"><span data-stu-id="26fd0-221">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><span data-ttu-id="26fd0-222"><a id="msix" />Installeren vanaf de Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="26fd0-222"><a id="msix" />Installing from the Microsoft Store</span></span>

<span data-ttu-id="26fd0-223">PowerShell 7.1 is gepubliceerd op de Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="26fd0-223">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="26fd0-224">U vindt de PowerShell-release op de [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website of in de Store-toepassing in Windows.</span><span class="sxs-lookup"><span data-stu-id="26fd0-224">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="26fd0-225">Voordelen van het Microsoft Store pakket:</span><span class="sxs-lookup"><span data-stu-id="26fd0-225">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="26fd0-226">Automatische updates ingebouwd in Windows 10</span><span class="sxs-lookup"><span data-stu-id="26fd0-226">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="26fd0-227">Kan worden geïntegreerd met andere softwaredistributiemechanismen, zoals Intune en SCCM</span><span class="sxs-lookup"><span data-stu-id="26fd0-227">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

<span data-ttu-id="26fd0-228">Beperkingen:</span><span class="sxs-lookup"><span data-stu-id="26fd0-228">Limitations:</span></span>

<span data-ttu-id="26fd0-229">MSIX-pakketten worden uitgevoerd in een toepassings-sandbox die de toegang tot sommige bestandssysteem- en registerlocaties virtualiseert.</span><span class="sxs-lookup"><span data-stu-id="26fd0-229">MSIX packages run in an application sandbox that virtualizes access to some filesystem and registry locations.</span></span>

- <span data-ttu-id="26fd0-230">Alle registerwijzigingen onder HKEY_CURRENT_USER worden gekopieerd bij schrijven naar een privélocatie per gebruiker, per app.</span><span class="sxs-lookup"><span data-stu-id="26fd0-230">All registry changes under HKEY_CURRENT_USER are copied on write to a private, per-user, per-app location.</span></span> <span data-ttu-id="26fd0-231">Deze waarden zijn daarom niet beschikbaar voor andere toepassingen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-231">Therefore, those values are not available to other applications.</span></span>
- <span data-ttu-id="26fd0-232">Configuratie-instellingen op systeemniveau die zijn opgeslagen in `$PSHOME` , kunnen niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="26fd0-232">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="26fd0-233">Dit omvat de WSMAN-configuratie.</span><span class="sxs-lookup"><span data-stu-id="26fd0-233">This includes the WSMAN configuration.</span></span> <span data-ttu-id="26fd0-234">Dit voorkomt dat externe sessies verbinding maken met op de Store gebaseerde installaties van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26fd0-234">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="26fd0-235">Configuraties op gebruikersniveau en SSH-remoting worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="26fd0-235">User-level configurations and SSH remoting are supported.</span></span>

<span data-ttu-id="26fd0-236">Zie Understanding [how packaged desktop apps run on Windows (Begrijpen hoe verpakte bureaublad-apps worden uitgevoerd in Windows) voor meer informatie.](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes)</span><span class="sxs-lookup"><span data-stu-id="26fd0-236">For more information, see [Understanding how packaged desktop apps run on Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span></span>

### <a name="using-the-msix-package"></a><span data-ttu-id="26fd0-237">Het MSIX-pakket gebruiken</span><span class="sxs-lookup"><span data-stu-id="26fd0-237">Using the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="26fd0-238">De preview-builds van PowerShell bevatten een MSIX-pakket.</span><span class="sxs-lookup"><span data-stu-id="26fd0-238">The preview builds of PowerShell include an MSIX package.</span></span> <span data-ttu-id="26fd0-239">Het MSIX-pakket wordt niet officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="26fd0-239">The MSIX package is not officially supported.</span></span> <span data-ttu-id="26fd0-240">Het pakket is gebouwd voor testdoeleinden tijdens de preview-periode.</span><span class="sxs-lookup"><span data-stu-id="26fd0-240">The package is built for testing purposes during the preview period.</span></span>

<span data-ttu-id="26fd0-241">Als u het MSIX-pakket handmatig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket op onze pagina GitHub [releases][releases].</span><span class="sxs-lookup"><span data-stu-id="26fd0-241">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="26fd0-242">Schuif omlaag naar de **sectie Assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="26fd0-242">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="26fd0-243">De sectie Assets kan worden samengevouwen, dus mogelijk moet u erop klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-243">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="26fd0-244">Het MSIX-bestand ziet er als deze uit: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="26fd0-244">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="26fd0-245">Als u het pakket wilt installeren, moet u de `Add-AppxPackage` cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="26fd0-245">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="26fd0-246">Een eindpunt voor remoting maken</span><span class="sxs-lookup"><span data-stu-id="26fd0-246">How to create a remoting endpoint</span></span>

<span data-ttu-id="26fd0-247">PowerShell ondersteunt het PowerShell Remoting Protocol (PSRP) via zowel WSMan als SSH.</span><span class="sxs-lookup"><span data-stu-id="26fd0-247">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="26fd0-248">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="26fd0-248">For more information, see:</span></span>

- <span data-ttu-id="26fd0-249">[SSH-remoting in PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="26fd0-249">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="26fd0-250">[WSMan Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="26fd0-250">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="upgrading-an-existing-installation"></a><span data-ttu-id="26fd0-251">Een bestaande installatie upgraden</span><span class="sxs-lookup"><span data-stu-id="26fd0-251">Upgrading an existing installation</span></span>

<span data-ttu-id="26fd0-252">Voor de beste resultaten bij het upgraden moet u dezelfde installatiemethode gebruiken die u hebt gebruikt toen u PowerShell voor het eerst installeerde.</span><span class="sxs-lookup"><span data-stu-id="26fd0-252">For best results when upgrading, you should use the same install method you used when you first installed PowerShell.</span></span> <span data-ttu-id="26fd0-253">Elke installatiemethode installeert PowerShell op een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="26fd0-253">Each installation method installs PowerShell in a different location.</span></span> <span data-ttu-id="26fd0-254">Als u niet zeker weet hoe PowerShell is geïnstalleerd, kunt u de geïnstalleerde locatie vergelijken met de pakketgegevens in dit artikel.</span><span class="sxs-lookup"><span data-stu-id="26fd0-254">If you are not sure how PowerShell was installed, you can compare the installed location with the package information in this article.</span></span> <span data-ttu-id="26fd0-255">Als u hebt geïnstalleerd via het MSI-pakket, wordt die informatie weergegeven in **de** Configuratiescherm.</span><span class="sxs-lookup"><span data-stu-id="26fd0-255">If you installed via the MSI package, that information appears in the **Programs and Features** Control Panel.</span></span>

## <a name="installation-support"></a><span data-ttu-id="26fd0-256">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="26fd0-256">Installation support</span></span>

<span data-ttu-id="26fd0-257">Microsoft ondersteunt de installatiemethoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="26fd0-257">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="26fd0-258">Er zijn mogelijk andere installatiemethoden beschikbaar vanuit andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="26fd0-258">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="26fd0-259">Hoewel deze hulpprogramma's en methoden kunnen werken, biedt Microsoft geen ondersteuning voor deze methoden.</span><span class="sxs-lookup"><span data-stu-id="26fd0-259">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[Voorbeeld]: https://aka.ms/powershell-release?tag=preview
[preview]: https://aka.ms/powershell-release?tag=preview
[meest recente]: https://aka.ms/powershell-release?tag=stable
[latest]: https://aka.ms/powershell-release?tag=stable
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
['een andere instantietechniek']: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
