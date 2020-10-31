---
title: PowerShell installeren in Windows
description: Informatie over het installeren van Power shell in Windows
ms.date: 10/30/2020
ms.openlocfilehash: 1b341b496cef34a2a98afeac9d24f0a51e8dbda0
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142783"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="27caf-103">PowerShell installeren in Windows</span><span class="sxs-lookup"><span data-stu-id="27caf-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="27caf-104">Er zijn meerdere manieren om Power shell in Windows te installeren.</span><span class="sxs-lookup"><span data-stu-id="27caf-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27caf-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="27caf-105">Prerequisites</span></span>

<span data-ttu-id="27caf-106">De meest recente versie van Power shell wordt ondersteund op Windows 7 SP1, Server 2008 R2 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="27caf-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="27caf-107">Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="27caf-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="27caf-108">Installeer de [universele C-runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="27caf-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="27caf-109">Het is beschikbaar via direct downloaden of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="27caf-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="27caf-110">Dit pakket is al geïnstalleerd op systemen met volledige patches.</span><span class="sxs-lookup"><span data-stu-id="27caf-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="27caf-111">Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="27caf-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="27caf-112">Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.</span><span class="sxs-lookup"><span data-stu-id="27caf-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="27caf-113">Het installatie pakket downloaden</span><span class="sxs-lookup"><span data-stu-id="27caf-113">Download the installer package</span></span>

<span data-ttu-id="27caf-114">Als u Power shell in Windows wilt installeren, downloadt u het installatie pakket van onze pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="27caf-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="27caf-115">Schuif omlaag naar de sectie **assets** van de pagina release.</span><span class="sxs-lookup"><span data-stu-id="27caf-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="27caf-116">De sectie **assets** kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="27caf-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="27caf-117"><a id="msi" />Het MSI-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="27caf-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="27caf-118">Het MSI-bestand ziet er als volgt uit `PowerShell-<version>-win-<os-arch>.msi` .</span><span class="sxs-lookup"><span data-stu-id="27caf-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="27caf-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="27caf-119">For example:</span></span>

- `PowerShell-7.0.3-win-x64.msi`
- `PowerShell-7.0.3-win-x86.msi`

<span data-ttu-id="27caf-120">Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="27caf-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="27caf-121">Het installatie programma maakt een snelkoppeling in het menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="27caf-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="27caf-122">Het pakket is standaard geïnstalleerd voor `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="27caf-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="27caf-123">U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="27caf-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="27caf-124">Power shell 7 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="27caf-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="27caf-125">Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="27caf-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="27caf-126">Power shell 7 is geïnstalleerd op `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="27caf-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="27caf-127">De `$env:ProgramFiles\PowerShell\7` map wordt toegevoegd aan `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="27caf-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="27caf-128">De `$env:ProgramFiles\PowerShell\6` map wordt verwijderd</span><span class="sxs-lookup"><span data-stu-id="27caf-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="27caf-129">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met de methode [zip-installatie](#zip) .</span><span class="sxs-lookup"><span data-stu-id="27caf-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="27caf-130">Beheerders installatie vanaf de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="27caf-130">Administrative install from the command line</span></span>

<span data-ttu-id="27caf-131">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel zodat beheerders pakketten kunnen implementeren zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="27caf-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="27caf-132">Het MSI-pakket bevat de volgende eigenschappen om de installatie opties te beheren:</span><span class="sxs-lookup"><span data-stu-id="27caf-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="27caf-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="27caf-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="27caf-134">**ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="27caf-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="27caf-135">**REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="27caf-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="27caf-136">In het volgende voor beeld ziet u hoe u Power shell op de achtergrond installeert met alle installatie opties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="27caf-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="27caf-137">`Msiexec.exe`Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor.</span><span class="sxs-lookup"><span data-stu-id="27caf-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="27caf-138">Register sleutels die tijdens de installatie zijn gemaakt</span><span class="sxs-lookup"><span data-stu-id="27caf-138">Registry keys created during installation</span></span>

<span data-ttu-id="27caf-139">Vanaf Power shell 7,1 maakt het MSI-pakket register sleutels waarin de installatie locatie en de versie van Power shell worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="27caf-139">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="27caf-140">Deze waarden bevinden zich in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` .</span><span class="sxs-lookup"><span data-stu-id="27caf-140">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="27caf-141">De waarde van `<GUID>` is uniek voor elk type Build (release of preview), de primaire versie en de architectuur.</span><span class="sxs-lookup"><span data-stu-id="27caf-141">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="27caf-142">Release</span><span class="sxs-lookup"><span data-stu-id="27caf-142">Release</span></span>    | <span data-ttu-id="27caf-143">Architectuur</span><span class="sxs-lookup"><span data-stu-id="27caf-143">Architecture</span></span> |                                          <span data-ttu-id="27caf-144">Registersleutel</span><span class="sxs-lookup"><span data-stu-id="27caf-144">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="27caf-145">Versie 7.1. x</span><span class="sxs-lookup"><span data-stu-id="27caf-145">7.1.x Release</span></span> |     <span data-ttu-id="27caf-146">x86</span><span class="sxs-lookup"><span data-stu-id="27caf-146">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="27caf-147">Versie 7.1. x</span><span class="sxs-lookup"><span data-stu-id="27caf-147">7.1.x Release</span></span> |     <span data-ttu-id="27caf-148">x64</span><span class="sxs-lookup"><span data-stu-id="27caf-148">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="27caf-149">7.1. x preview</span><span class="sxs-lookup"><span data-stu-id="27caf-149">7.1.x Preview</span></span> |     <span data-ttu-id="27caf-150">x86</span><span class="sxs-lookup"><span data-stu-id="27caf-150">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="27caf-151">7.1. x preview</span><span class="sxs-lookup"><span data-stu-id="27caf-151">7.1.x Preview</span></span> |     <span data-ttu-id="27caf-152">x64</span><span class="sxs-lookup"><span data-stu-id="27caf-152">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="27caf-153">Dit kan worden gebruikt door beheerders en ontwikkel aars om het pad naar Power shell te vinden.</span><span class="sxs-lookup"><span data-stu-id="27caf-153">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="27caf-154">De `<GUID>` waarden zijn hetzelfde voor alle versies van de preview-versie en secundaire versies.</span><span class="sxs-lookup"><span data-stu-id="27caf-154">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="27caf-155">De `<GUID>` waarden voor elke grote release worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="27caf-155">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="27caf-156"><a id="msix" />Het MSIX-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="27caf-156"><a id="msix" />Installing the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="27caf-157">Het MSIX-pakket wordt op dit moment niet officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="27caf-157">The MSIX package is not officially supported at this time.</span></span> <span data-ttu-id="27caf-158">We blijven het pakket alleen voor interne test doeleinden bouwen.</span><span class="sxs-lookup"><span data-stu-id="27caf-158">We continue to build the package for internal testing purposes only.</span></span>

<span data-ttu-id="27caf-159">Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="27caf-159">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="27caf-160">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="27caf-160">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="27caf-161">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="27caf-161">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="27caf-162">Het MSIX-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="27caf-162">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="27caf-163">Als u het pakket wilt installeren, moet u de `Add-AppxPackage` cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="27caf-163">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="installing-the-zip-package"></a><span data-ttu-id="27caf-164"><a id="zip" />Het ZIP-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="27caf-164"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="27caf-165">Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="27caf-165">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="27caf-166">Down load een van de volgende ZIP-archieven op de pagina [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="27caf-166">Download one of the following ZIP archives from the [releases][releases] page.</span></span>

- <span data-ttu-id="27caf-167">PowerShell-7.0.3-win-x64.zip</span><span class="sxs-lookup"><span data-stu-id="27caf-167">PowerShell-7.0.3-win-x64.zip</span></span>
- <span data-ttu-id="27caf-168">PowerShell-7.0.3-win-x86.zip</span><span class="sxs-lookup"><span data-stu-id="27caf-168">PowerShell-7.0.3-win-x86.zip</span></span>
- <span data-ttu-id="27caf-169">PowerShell-7.0.3-win-arm64.zip</span><span class="sxs-lookup"><span data-stu-id="27caf-169">PowerShell-7.0.3-win-arm64.zip</span></span>
- <span data-ttu-id="27caf-170">PowerShell-7.0.3-win-arm32.zip</span><span class="sxs-lookup"><span data-stu-id="27caf-170">PowerShell-7.0.3-win-arm32.zip</span></span>

<span data-ttu-id="27caf-171">Afhankelijk van hoe u het bestand downloadt, moet u het bestand mogelijk deblokkeren met de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27caf-171">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="27caf-172">Pak de inhoud uit naar de gewenste locatie en voer deze `pwsh.exe` uit.</span><span class="sxs-lookup"><span data-stu-id="27caf-172">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="27caf-173">In tegens telling tot de installatie van de MSI-pakketten controleert de installatie van het ZIP-archief niet op vereisten.</span><span class="sxs-lookup"><span data-stu-id="27caf-173">Unlike installing the MSI packages, installing the ZIP archive doesn't check for prerequisites.</span></span> <span data-ttu-id="27caf-174">Zorg ervoor dat u aan de [vereisten](#prerequisites)voldoet om externe toegang tot WSMan goed te laten werken.</span><span class="sxs-lookup"><span data-stu-id="27caf-174">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

<span data-ttu-id="27caf-175">Gebruik deze methode om de ARM-gebaseerde versie van Power shell te installeren op computers zoals micro soft Surface Pro X. Voor de beste resultaten installeert u Power shell op de `$env:ProgramFiles\PowerShell\7` map aan.</span><span class="sxs-lookup"><span data-stu-id="27caf-175">Use this method to install the ARM-based version of PowerShell on computers like the Microsoft Surface Pro X. For best results, install PowerShell to the to `$env:ProgramFiles\PowerShell\7` folder.</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="27caf-176">Implementeren in Windows 10 IoT Enter prise</span><span class="sxs-lookup"><span data-stu-id="27caf-176">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="27caf-177">Windows 10 IoT Enter prise wordt geleverd met Windows Power shell en kan worden gebruikt voor het implementeren van Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="27caf-177">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="27caf-178">Maken `PSSession` op doel apparaat</span><span class="sxs-lookup"><span data-stu-id="27caf-178">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="27caf-179">Het ZIP-pakket kopiëren naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="27caf-179">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="27caf-180">Verbinding maken met het apparaat en het archief uitvouwen</span><span class="sxs-lookup"><span data-stu-id="27caf-180">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="27caf-181">Externe toegang instellen met Power shell 7</span><span class="sxs-lookup"><span data-stu-id="27caf-181">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. <span data-ttu-id="27caf-182">Verbinding maken met het Power shell 7-eind punt op het apparaat</span><span class="sxs-lookup"><span data-stu-id="27caf-182">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="27caf-183">Implementeren in Windows 10 IoT core</span><span class="sxs-lookup"><span data-stu-id="27caf-183">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="27caf-184">Windows 10 IoT core voegt Windows Power shell toe wanneer u _IOT_POWERSHELL_ -functie opneemt, die we kunnen gebruiken om Power shell 7 te implementeren.</span><span class="sxs-lookup"><span data-stu-id="27caf-184">Windows 10 IoT Core adds Windows PowerShell when you include _IOT_POWERSHELL_ feature, which we can use to deploy PowerShell 7.</span></span> <span data-ttu-id="27caf-185">De stappen die hierboven voor Windows 10 IoT Enter prise zijn gedefinieerd, kunnen ook worden gevolgd voor IoT core.</span><span class="sxs-lookup"><span data-stu-id="27caf-185">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="27caf-186">Voor het toevoegen van de meest recente Power shell in de verzend installatie kopie gebruikt u de opdracht [import-PSCoreRelease][] om het pakket op te zetten in de workarea en voegt u _OPENSRC_POWERSHELL_ functie toe aan uw installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27caf-186">For adding the latest PowerShell in the shipping image, use [Import-PSCoreRelease][] command to include the package in the workarea and add _OPENSRC_POWERSHELL_ feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="27caf-187">Voor ARM64-architectuur wordt Windows Power shell niet toegevoegd wanneer u _IOT_POWERSHELL_ opneemt.</span><span class="sxs-lookup"><span data-stu-id="27caf-187">For ARM64 architecture, Windows PowerShell is not added when you include _IOT_POWERSHELL_ .</span></span> <span data-ttu-id="27caf-188">De op ZIP gebaseerde installatie werkt dus niet.</span><span class="sxs-lookup"><span data-stu-id="27caf-188">So the zip based install will not work.</span></span> <span data-ttu-id="27caf-189">U moet `Import-PSCoreRelease` de opdracht gebruiken om deze toe te voegen aan de installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27caf-189">You will need to use `Import-PSCoreRelease` command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="27caf-190">Implementeren op nano server</span><span class="sxs-lookup"><span data-stu-id="27caf-190">Deploying on Nano Server</span></span>

<span data-ttu-id="27caf-191">Bij deze instructies wordt ervan uitgegaan dat de nano server een ' headless ' besturings systeem is waarop al een versie van Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="27caf-191">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="27caf-192">Zie de documentatie van [nano server Image Builder](/windows-server/get-started/deploy-nano-server) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="27caf-192">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="27caf-193">Binaire Power Shell-bestanden kunnen met twee verschillende methoden worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="27caf-193">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="27caf-194">De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27caf-194">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="27caf-195">Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="27caf-195">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="27caf-196">In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig.</span><span class="sxs-lookup"><span data-stu-id="27caf-196">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="27caf-197">Voer de opdrachten uit in een ' beheerder ' exemplaar van Power shell.</span><span class="sxs-lookup"><span data-stu-id="27caf-197">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="27caf-198">Offline-implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="27caf-198">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="27caf-199">Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27caf-199">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="27caf-200">Ontkoppel de installatie kopie en start deze op.</span><span class="sxs-lookup"><span data-stu-id="27caf-200">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="27caf-201">Maak verbinding met het ingebouwde exemplaar van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="27caf-201">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="27caf-202">Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"][].</span><span class="sxs-lookup"><span data-stu-id="27caf-202">Follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="27caf-203">Online implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="27caf-203">Online Deployment of PowerShell</span></span>

<span data-ttu-id="27caf-204">Implementeer Power shell naar nano server met behulp van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="27caf-204">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="27caf-205">Verbinding maken met het ingebouwde exemplaar van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="27caf-205">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="27caf-206">Kopieer het bestand naar het Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="27caf-206">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="27caf-207">De sessie invoeren</span><span class="sxs-lookup"><span data-stu-id="27caf-207">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="27caf-208">Het ZIP-bestand uitpakken</span><span class="sxs-lookup"><span data-stu-id="27caf-208">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="27caf-209">Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"][].</span><span class="sxs-lookup"><span data-stu-id="27caf-209">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="27caf-210">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="27caf-210">Install as a .NET Global tool</span></span>

<span data-ttu-id="27caf-211">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="27caf-211">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="27caf-212">Het hulp programma DotNet tool wordt toegevoegd `$env:USERPROFILE\dotnet\tools` aan de `$env:PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="27caf-212">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="27caf-213">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `$env:PATH` .</span><span class="sxs-lookup"><span data-stu-id="27caf-213">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="27caf-214">U kunt Power shell starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="27caf-214">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-winget"></a><span data-ttu-id="27caf-215">Power Shell installeren via Winget</span><span class="sxs-lookup"><span data-stu-id="27caf-215">Install PowerShell via Winget</span></span>

<span data-ttu-id="27caf-216">`winget`Met het opdracht regel programma kunnen ontwikkel aars toepassingen op Windows 10-computers detecteren, installeren, upgraden, verwijderen en configureren.</span><span class="sxs-lookup"><span data-stu-id="27caf-216">The `winget` command-line tool enables developers to discover, install, upgrade, remove, and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="27caf-217">Dit hulp programma is de client interface voor de Windows Package Manager-service.</span><span class="sxs-lookup"><span data-stu-id="27caf-217">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="27caf-218">Het `winget` hulp programma is momenteel een preview-versie.</span><span class="sxs-lookup"><span data-stu-id="27caf-218">The `winget` tool is currently a preview.</span></span> <span data-ttu-id="27caf-219">Niet alle geplande functionaliteit is op dit moment beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="27caf-219">Not all planned functionality is available at this time.</span></span>
> <span data-ttu-id="27caf-220">U moet deze methode niet gebruiken in een scenario voor productie-implementatie.</span><span class="sxs-lookup"><span data-stu-id="27caf-220">You should not use this method in a production deployment scenario.</span></span> <span data-ttu-id="27caf-221">Raadpleeg de [Winget] -documentatie voor een lijst met systeem vereisten en installatie-instructies.</span><span class="sxs-lookup"><span data-stu-id="27caf-221">See the [winget] documentation for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="27caf-222">De volgende opdrachten kunnen worden gebruikt om Power shell te installeren met behulp van de gepubliceerde `winget` pakketten:</span><span class="sxs-lookup"><span data-stu-id="27caf-222">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="27caf-223">Zoeken naar de meest recente versie van Power shell</span><span class="sxs-lookup"><span data-stu-id="27caf-223">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.0.3
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.0-preview.5
   ```

1. <span data-ttu-id="27caf-224">Een versie van Power Shell installeren met behulp van de `--exact` para meter</span><span class="sxs-lookup"><span data-stu-id="27caf-224">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="27caf-225">Een extern eind punt maken</span><span class="sxs-lookup"><span data-stu-id="27caf-225">How to create a remoting endpoint</span></span>

<span data-ttu-id="27caf-226">Power shell ondersteunt het Power shell Remoting Protocol (PSRP) voor zowel WSMan als SSH.</span><span class="sxs-lookup"><span data-stu-id="27caf-226">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="27caf-227">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="27caf-227">For more information, see:</span></span>

- <span data-ttu-id="27caf-228">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="27caf-228">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="27caf-229">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="27caf-229">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="upgrading-an-existing-installation"></a><span data-ttu-id="27caf-230">Een bestaande installatie upgraden</span><span class="sxs-lookup"><span data-stu-id="27caf-230">Upgrading an existing installation</span></span>

<span data-ttu-id="27caf-231">Voor de beste resultaten bij het uitvoeren van een upgrade moet u dezelfde installatie methode gebruiken die u hebt gebruikt toen u Power shell voor het eerst installeerde.</span><span class="sxs-lookup"><span data-stu-id="27caf-231">For best results when upgrading, you should use the same install method you used when you first installed PowerShell.</span></span> <span data-ttu-id="27caf-232">Elke installatie methode installeert Power shell op een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="27caf-232">Each installation method installs PowerShell in a different location.</span></span> <span data-ttu-id="27caf-233">Als u niet zeker weet hoe Power shell is geïnstalleerd, kunt u de geïnstalleerde locatie vergelijken met de pakket gegevens in dit artikel.</span><span class="sxs-lookup"><span data-stu-id="27caf-233">If you are not sure how PowerShell was installed, you can compare the installed location with the package information in this article.</span></span> <span data-ttu-id="27caf-234">Als u via het MSI-pakket hebt geïnstalleerd, wordt die informatie weer gegeven in het onderdeel **Program ma's en onderdelen** van het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="27caf-234">If you installed via the MSI package, that information appears in the **Programs and Features** Control Panel.</span></span>

## <a name="installation-support"></a><span data-ttu-id="27caf-235">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="27caf-235">Installation support</span></span>

<span data-ttu-id="27caf-236">Micro soft ondersteunt de installatie methoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="27caf-236">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="27caf-237">Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="27caf-237">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="27caf-238">Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="27caf-238">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["een andere instantie-techniek"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
