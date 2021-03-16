---
title: PowerShell installeren in Windows
description: Informatie over het installeren van Power shell in Windows
ms.date: 02/02/2021
ms.openlocfilehash: bd3643c1ca6beb60a8727478a1ae612dcb34c7fb
ms.sourcegitcommit: 080c8b05a1242348c365fe1684457e873325f11e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483433"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="27faa-103">PowerShell installeren in Windows</span><span class="sxs-lookup"><span data-stu-id="27faa-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="27faa-104">Er zijn meerdere manieren om Power shell in Windows te installeren.</span><span class="sxs-lookup"><span data-stu-id="27faa-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27faa-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="27faa-105">Prerequisites</span></span>

<span data-ttu-id="27faa-106">De meest recente versie van Power shell wordt ondersteund op Windows 7 SP1, Server 2008 R2 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="27faa-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="27faa-107">Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="27faa-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="27faa-108">Installeer de [universele C-runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="27faa-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="27faa-109">Het is beschikbaar via direct downloaden of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="27faa-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="27faa-110">Dit pakket is al geïnstalleerd op systemen met volledige patches.</span><span class="sxs-lookup"><span data-stu-id="27faa-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="27faa-111">Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="27faa-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="27faa-112">Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.</span><span class="sxs-lookup"><span data-stu-id="27faa-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="27faa-113">Het installatie pakket downloaden</span><span class="sxs-lookup"><span data-stu-id="27faa-113">Download the installer package</span></span>

<span data-ttu-id="27faa-114">Als u Power shell in Windows wilt installeren, downloadt u het [meest recente][] installatie pakket van github.</span><span class="sxs-lookup"><span data-stu-id="27faa-114">To install PowerShell on Windows, download the [latest][] install package from GitHub.</span></span> <span data-ttu-id="27faa-115">U kunt ook de nieuwste [Preview][] -versie vinden.</span><span class="sxs-lookup"><span data-stu-id="27faa-115">You can also find the latest [preview][] version.</span></span> <span data-ttu-id="27faa-116">Schuif omlaag naar de sectie **assets** van de pagina release.</span><span class="sxs-lookup"><span data-stu-id="27faa-116">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="27faa-117">De sectie **assets** kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="27faa-117">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="27faa-118"><a id="msi" />Het MSI-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="27faa-118"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="27faa-119">Het MSI-bestand ziet er als volgt uit `PowerShell-<version>-win-<os-arch>.msi` .</span><span class="sxs-lookup"><span data-stu-id="27faa-119">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="27faa-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="27faa-120">For example:</span></span>

- `PowerShell-7.1.3-win-x64.msi`
- `PowerShell-7.1.3-win-x86.msi`

<span data-ttu-id="27faa-121">Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="27faa-121">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="27faa-122">Het installatie programma maakt een snelkoppeling in het menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="27faa-122">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="27faa-123">Het pakket is standaard geïnstalleerd voor `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="27faa-123">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="27faa-124">U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="27faa-124">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="27faa-125">Power shell 7,1 wordt geïnstalleerd in een nieuwe map en kan naast Windows Power shell 5,1 worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="27faa-125">PowerShell 7.1 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span>
> <span data-ttu-id="27faa-126">Power shell 7,1 is een in-place upgrade waarmee Power shell 6. x wordt vervangen.</span><span class="sxs-lookup"><span data-stu-id="27faa-126">PowerShell 7.1 is an in-place upgrade that replaces PowerShell 6.x.</span></span> <span data-ttu-id="27faa-127">of Power shell 7,0.</span><span class="sxs-lookup"><span data-stu-id="27faa-127">or PowerShell 7.0.</span></span>
>
> - <span data-ttu-id="27faa-128">Power shell 7,1 is geïnstalleerd voor `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="27faa-128">PowerShell 7.1 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="27faa-129">De `$env:ProgramFiles\PowerShell\7` map wordt toegevoegd aan `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="27faa-129">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="27faa-130">De `$env:ProgramFiles\PowerShell\6` map wordt verwijderd</span><span class="sxs-lookup"><span data-stu-id="27faa-130">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="27faa-131">Als u Power shell 7,1 naast andere versies moet uitvoeren, gebruikt u de methode [zip-installatie](#zip) om de andere versie te installeren in een andere map.</span><span class="sxs-lookup"><span data-stu-id="27faa-131">If you need to run PowerShell 7.1 side-by-side with other versions, use the [ZIP install](#zip) method to install the other version to a different folder.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="27faa-132">Beheerders installatie vanaf de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="27faa-132">Administrative install from the command line</span></span>

<span data-ttu-id="27faa-133">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel zodat beheerders pakketten kunnen implementeren zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="27faa-133">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="27faa-134">Het MSI-pakket bevat de volgende eigenschappen om de installatie opties te beheren:</span><span class="sxs-lookup"><span data-stu-id="27faa-134">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="27faa-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="27faa-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="27faa-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** : deze eigenschap bepaalt de optie voor het toevoegen van het item **uitvoeren met Power shell** in het context menu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="27faa-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** - This property controls the option for adding the **Run with PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="27faa-137">**ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="27faa-137">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="27faa-138">**REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="27faa-138">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="27faa-139">In het volgende voor beeld ziet u hoe u Power shell op de achtergrond installeert met alle installatie opties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="27faa-139">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.1.3-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="27faa-140">`Msiexec.exe`Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor.</span><span class="sxs-lookup"><span data-stu-id="27faa-140">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="27faa-141">Register sleutels die tijdens de installatie zijn gemaakt</span><span class="sxs-lookup"><span data-stu-id="27faa-141">Registry keys created during installation</span></span>

<span data-ttu-id="27faa-142">Vanaf Power shell 7,1 maakt het MSI-pakket register sleutels waarin de installatie locatie en de versie van Power shell worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="27faa-142">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="27faa-143">Deze waarden bevinden zich in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>` .</span><span class="sxs-lookup"><span data-stu-id="27faa-143">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="27faa-144">De waarde van `<GUID>` is uniek voor elk type Build (release of preview), de primaire versie en de architectuur.</span><span class="sxs-lookup"><span data-stu-id="27faa-144">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="27faa-145">Release</span><span class="sxs-lookup"><span data-stu-id="27faa-145">Release</span></span>    | <span data-ttu-id="27faa-146">Architectuur</span><span class="sxs-lookup"><span data-stu-id="27faa-146">Architecture</span></span> |                                          <span data-ttu-id="27faa-147">Registersleutel</span><span class="sxs-lookup"><span data-stu-id="27faa-147">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="27faa-148">Versie 7.1. x</span><span class="sxs-lookup"><span data-stu-id="27faa-148">7.1.x Release</span></span> |     <span data-ttu-id="27faa-149">x86</span><span class="sxs-lookup"><span data-stu-id="27faa-149">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="27faa-150">Versie 7.1. x</span><span class="sxs-lookup"><span data-stu-id="27faa-150">7.1.x Release</span></span> |     <span data-ttu-id="27faa-151">x64</span><span class="sxs-lookup"><span data-stu-id="27faa-151">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="27faa-152">7.1. x preview</span><span class="sxs-lookup"><span data-stu-id="27faa-152">7.1.x Preview</span></span> |     <span data-ttu-id="27faa-153">x86</span><span class="sxs-lookup"><span data-stu-id="27faa-153">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="27faa-154">7.1. x preview</span><span class="sxs-lookup"><span data-stu-id="27faa-154">7.1.x Preview</span></span> |     <span data-ttu-id="27faa-155">x64</span><span class="sxs-lookup"><span data-stu-id="27faa-155">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="27faa-156">Dit kan worden gebruikt door beheerders en ontwikkel aars om het pad naar Power shell te vinden.</span><span class="sxs-lookup"><span data-stu-id="27faa-156">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="27faa-157">De `<GUID>` waarden zijn hetzelfde voor alle versies van de preview-versie en secundaire versies.</span><span class="sxs-lookup"><span data-stu-id="27faa-157">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="27faa-158">De `<GUID>` waarden voor elke grote release worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="27faa-158">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="27faa-159"><a id="zip" />Het ZIP-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="27faa-159"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="27faa-160">Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="27faa-160">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="27faa-161">Down load een van de volgende ZIP-archieven van de pagina [releases] [releases].</span><span class="sxs-lookup"><span data-stu-id="27faa-161">Download one of the following ZIP archives from the [releases][releases] page.</span></span>

- <span data-ttu-id="27faa-162">PowerShell-7.1.3-win-x64.zip</span><span class="sxs-lookup"><span data-stu-id="27faa-162">PowerShell-7.1.3-win-x64.zip</span></span>
- <span data-ttu-id="27faa-163">PowerShell-7.1.3-win-x86.zip</span><span class="sxs-lookup"><span data-stu-id="27faa-163">PowerShell-7.1.3-win-x86.zip</span></span>
- <span data-ttu-id="27faa-164">PowerShell-7.1.3-win-arm64.zip</span><span class="sxs-lookup"><span data-stu-id="27faa-164">PowerShell-7.1.3-win-arm64.zip</span></span>
- <span data-ttu-id="27faa-165">PowerShell-7.1.3-win-arm32.zip</span><span class="sxs-lookup"><span data-stu-id="27faa-165">PowerShell-7.1.3-win-arm32.zip</span></span>

<span data-ttu-id="27faa-166">Afhankelijk van hoe u het bestand downloadt, moet u het bestand mogelijk deblokkeren met de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="27faa-166">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="27faa-167">Pak de inhoud uit naar de gewenste locatie en voer deze `pwsh.exe` uit.</span><span class="sxs-lookup"><span data-stu-id="27faa-167">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="27faa-168">In tegens telling tot de installatie van de MSI-pakketten controleert de installatie van het ZIP-archief niet op vereisten.</span><span class="sxs-lookup"><span data-stu-id="27faa-168">Unlike installing the MSI packages, installing the ZIP archive doesn't check for prerequisites.</span></span> <span data-ttu-id="27faa-169">Zorg ervoor dat u aan de [vereisten](#prerequisites)voldoet om externe toegang tot WSMan goed te laten werken.</span><span class="sxs-lookup"><span data-stu-id="27faa-169">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

<span data-ttu-id="27faa-170">Gebruik deze methode om de ARM-gebaseerde versie van Power shell te installeren op computers zoals micro soft Surface Pro X. Voor de beste resultaten installeert u Power shell op de `$env:ProgramFiles\PowerShell\7` map aan.</span><span class="sxs-lookup"><span data-stu-id="27faa-170">Use this method to install the ARM-based version of PowerShell on computers like the Microsoft Surface Pro X. For best results, install PowerShell to the to `$env:ProgramFiles\PowerShell\7` folder.</span></span>

> [!NOTE]
> <span data-ttu-id="27faa-171">U kunt deze methode gebruiken om een wille keurige versie van Power shell te installeren, met inbegrip van de nieuwste:</span><span class="sxs-lookup"><span data-stu-id="27faa-171">You can use this method to install any version of PowerShell including the latest:</span></span>
> - <span data-ttu-id="27faa-172">Stabiele release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)</span><span class="sxs-lookup"><span data-stu-id="27faa-172">Stable release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)</span></span>
> - <span data-ttu-id="27faa-173">Preview-versie: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)</span><span class="sxs-lookup"><span data-stu-id="27faa-173">Preview release: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)</span></span>
> - <span data-ttu-id="27faa-174">LTS release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)</span><span class="sxs-lookup"><span data-stu-id="27faa-174">LTS release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="27faa-175">Implementeren in Windows 10 IoT Enter prise</span><span class="sxs-lookup"><span data-stu-id="27faa-175">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="27faa-176">Windows 10 IoT Enter prise wordt geleverd met Windows Power shell en kan worden gebruikt voor het implementeren van Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="27faa-176">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="27faa-177">Maken `PSSession` op doel apparaat</span><span class="sxs-lookup"><span data-stu-id="27faa-177">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="27faa-178">Het ZIP-pakket kopiëren naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="27faa-178">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="27faa-179">Verbinding maken met het apparaat en het archief uitvouwen</span><span class="sxs-lookup"><span data-stu-id="27faa-179">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="27faa-180">Externe toegang instellen met Power shell 7</span><span class="sxs-lookup"><span data-stu-id="27faa-180">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. <span data-ttu-id="27faa-181">Verbinding maken met het Power shell 7-eind punt op het apparaat</span><span class="sxs-lookup"><span data-stu-id="27faa-181">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="27faa-182">Implementeren in Windows 10 IoT core</span><span class="sxs-lookup"><span data-stu-id="27faa-182">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="27faa-183">Windows 10 IoT core voegt Windows Power shell toe wanneer u _IOT_POWERSHELL_ -functie opneemt, die we kunnen gebruiken om Power shell 7 te implementeren.</span><span class="sxs-lookup"><span data-stu-id="27faa-183">Windows 10 IoT Core adds Windows PowerShell when you include _IOT_POWERSHELL_ feature, which we can use to deploy PowerShell 7.</span></span> <span data-ttu-id="27faa-184">De stappen die hierboven voor Windows 10 IoT Enter prise zijn gedefinieerd, kunnen ook worden gevolgd voor IoT core.</span><span class="sxs-lookup"><span data-stu-id="27faa-184">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="27faa-185">Voor het toevoegen van de meest recente Power shell in de verzend installatie kopie gebruikt u de opdracht [import-PSCoreRelease][] om het pakket op te zetten in de workarea en voegt u _OPENSRC_POWERSHELL_ functie toe aan uw installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27faa-185">For adding the latest PowerShell in the shipping image, use [Import-PSCoreRelease][] command to include the package in the workarea and add _OPENSRC_POWERSHELL_ feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="27faa-186">Voor ARM64-architectuur wordt Windows Power shell niet toegevoegd wanneer u _IOT_POWERSHELL_ opneemt.</span><span class="sxs-lookup"><span data-stu-id="27faa-186">For ARM64 architecture, Windows PowerShell is not added when you include _IOT_POWERSHELL_.</span></span> <span data-ttu-id="27faa-187">De op ZIP gebaseerde installatie werkt dus niet.</span><span class="sxs-lookup"><span data-stu-id="27faa-187">So the zip based install will not work.</span></span> <span data-ttu-id="27faa-188">U moet `Import-PSCoreRelease` de opdracht gebruiken om deze toe te voegen aan de installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27faa-188">You will need to use `Import-PSCoreRelease` command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="27faa-189">Implementeren op nano server</span><span class="sxs-lookup"><span data-stu-id="27faa-189">Deploying on Nano Server</span></span>

<span data-ttu-id="27faa-190">Bij deze instructies wordt ervan uitgegaan dat de nano server een ' headless ' besturings systeem is waarop al een versie van Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="27faa-190">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="27faa-191">Zie de documentatie van [nano server Image Builder](/windows-server/get-started/deploy-nano-server) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="27faa-191">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="27faa-192">Binaire Power Shell-bestanden kunnen met twee verschillende methoden worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="27faa-192">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="27faa-193">De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27faa-193">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="27faa-194">Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="27faa-194">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="27faa-195">In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig.</span><span class="sxs-lookup"><span data-stu-id="27faa-195">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="27faa-196">Voer de opdrachten uit in een ' beheerder ' exemplaar van Power shell.</span><span class="sxs-lookup"><span data-stu-id="27faa-196">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="27faa-197">Offline-implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="27faa-197">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="27faa-198">Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="27faa-198">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="27faa-199">Ontkoppel de installatie kopie en start deze op.</span><span class="sxs-lookup"><span data-stu-id="27faa-199">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="27faa-200">Maak verbinding met het ingebouwde exemplaar van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="27faa-200">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="27faa-201">Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"][].</span><span class="sxs-lookup"><span data-stu-id="27faa-201">Follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="27faa-202">Online implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="27faa-202">Online Deployment of PowerShell</span></span>

<span data-ttu-id="27faa-203">Implementeer Power shell naar nano server met behulp van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="27faa-203">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="27faa-204">Verbinding maken met het ingebouwde exemplaar van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="27faa-204">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="27faa-205">Kopieer het bestand naar het Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="27faa-205">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="27faa-206">De sessie invoeren</span><span class="sxs-lookup"><span data-stu-id="27faa-206">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="27faa-207">Het ZIP-bestand uitpakken</span><span class="sxs-lookup"><span data-stu-id="27faa-207">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="27faa-208">Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"][].</span><span class="sxs-lookup"><span data-stu-id="27faa-208">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="27faa-209">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="27faa-209">Install as a .NET Global tool</span></span>

<span data-ttu-id="27faa-210">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="27faa-210">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="27faa-211">Het hulp programma DotNet tool wordt toegevoegd `$env:USERPROFILE\dotnet\tools` aan de `$env:PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="27faa-211">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="27faa-212">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `$env:PATH` .</span><span class="sxs-lookup"><span data-stu-id="27faa-212">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="27faa-213">U kunt Power shell starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="27faa-213">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-winget"></a><span data-ttu-id="27faa-214">Power Shell installeren via Winget</span><span class="sxs-lookup"><span data-stu-id="27faa-214">Install PowerShell via Winget</span></span>

<span data-ttu-id="27faa-215">`winget`Met het opdracht regel programma kunnen ontwikkel aars toepassingen op Windows 10-computers detecteren, installeren, upgraden, verwijderen en configureren.</span><span class="sxs-lookup"><span data-stu-id="27faa-215">The `winget` command-line tool enables developers to discover, install, upgrade, remove, and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="27faa-216">Dit hulp programma is de client interface voor de Windows Package Manager-service.</span><span class="sxs-lookup"><span data-stu-id="27faa-216">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="27faa-217">Het `winget` hulp programma is momenteel een preview-versie.</span><span class="sxs-lookup"><span data-stu-id="27faa-217">The `winget` tool is currently a preview.</span></span> <span data-ttu-id="27faa-218">Niet alle geplande functionaliteit is op dit moment beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="27faa-218">Not all planned functionality is available at this time.</span></span>
> <span data-ttu-id="27faa-219">U moet deze methode niet gebruiken in een scenario voor productie-implementatie.</span><span class="sxs-lookup"><span data-stu-id="27faa-219">You should not use this method in a production deployment scenario.</span></span> <span data-ttu-id="27faa-220">Raadpleeg de [Winget] -documentatie voor een lijst met systeem vereisten en installatie-instructies.</span><span class="sxs-lookup"><span data-stu-id="27faa-220">See the [winget] documentation for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="27faa-221">De volgende opdrachten kunnen worden gebruikt om Power shell te installeren met behulp van de gepubliceerde `winget` pakketten:</span><span class="sxs-lookup"><span data-stu-id="27faa-221">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="27faa-222">Zoeken naar de meest recente versie van Power shell</span><span class="sxs-lookup"><span data-stu-id="27faa-222">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name                      Id                                Version
   ---------------------------------------------------------------------------
   PowerShell                Microsoft.PowerShell              7.1.3
   PowerShell Preview (MSIX) Microsoft.PowerShell-Preview-MSIX 7.0.2
   PowerShell-Preview        Microsoft.PowerShell-Preview      7.2.0-preview.3
   ```

1. <span data-ttu-id="27faa-223">Een versie van Power Shell installeren met behulp van de `--exact` para meter</span><span class="sxs-lookup"><span data-stu-id="27faa-223">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><span data-ttu-id="27faa-224"><a id="msix" />Installeren vanuit de Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="27faa-224"><a id="msix" />Installing from the Microsoft Store</span></span>

<span data-ttu-id="27faa-225">Power shell 7,1 is gepubliceerd op de Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="27faa-225">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="27faa-226">U kunt de Power shell-release vinden op de [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website of in de Store-toepassing in Windows.</span><span class="sxs-lookup"><span data-stu-id="27faa-226">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="27faa-227">Voor delen van het Microsoft Store-pakket:</span><span class="sxs-lookup"><span data-stu-id="27faa-227">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="27faa-228">Automatische updates zijn direct in Windows 10 ingebouwd</span><span class="sxs-lookup"><span data-stu-id="27faa-228">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="27faa-229">Kan worden geïntegreerd met andere software distributie mechanismen, zoals intune en SCCM</span><span class="sxs-lookup"><span data-stu-id="27faa-229">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

<span data-ttu-id="27faa-230">Beperkingen:</span><span class="sxs-lookup"><span data-stu-id="27faa-230">Limitations:</span></span>

<span data-ttu-id="27faa-231">MSIX-pakketten worden uitgevoerd in een sandbox voor toepassingen waarmee de toegang tot bepaalde bestands systeem-en register locaties wordt gevirtualeerd.</span><span class="sxs-lookup"><span data-stu-id="27faa-231">MSIX packages run in an application sandbox that virtualizes access to some filesystem and registry locations.</span></span>

- <span data-ttu-id="27faa-232">Alle register wijzigingen onder HKEY_CURRENT_USER worden bij het schrijven naar een persoonlijke, per gebruiker per app-locatie gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="27faa-232">All registry changes under HKEY_CURRENT_USER are copied on write to a private, per-user, per-app location.</span></span> <span data-ttu-id="27faa-233">Daarom zijn deze waarden niet beschikbaar voor andere toepassingen.</span><span class="sxs-lookup"><span data-stu-id="27faa-233">Therefore, those values are not available to other applications.</span></span>
- <span data-ttu-id="27faa-234">Alle configuratie-instellingen op systeem niveau die zijn opgeslagen in, `$PSHOME` kunnen niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="27faa-234">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="27faa-235">Dit omvat de WSMAN-configuratie.</span><span class="sxs-lookup"><span data-stu-id="27faa-235">This includes the WSMAN configuration.</span></span> <span data-ttu-id="27faa-236">Hiermee voor komt u dat externe sessies verbinding maken met op opslag gebaseerde installaties van Power shell.</span><span class="sxs-lookup"><span data-stu-id="27faa-236">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="27faa-237">Configuraties op gebruikers niveau en externe SSH-communicatie worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="27faa-237">User-level configurations and SSH remoting are supported.</span></span>

<span data-ttu-id="27faa-238">Zie [hoe verpakte bureau blad-apps worden uitgevoerd in Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="27faa-238">For more information, see [Understanding how packaged desktop apps run on Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span></span>

### <a name="using-the-msix-package"></a><span data-ttu-id="27faa-239">Het MSIX-pakket gebruiken</span><span class="sxs-lookup"><span data-stu-id="27faa-239">Using the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="27faa-240">De preview-builds van Power shell bevatten een MSIX-pakket.</span><span class="sxs-lookup"><span data-stu-id="27faa-240">The preview builds of PowerShell include an MSIX package.</span></span> <span data-ttu-id="27faa-241">Het MSIX-pakket wordt niet officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="27faa-241">The MSIX package is not officially supported.</span></span> <span data-ttu-id="27faa-242">Het pakket is gebouwd voor test doeleinden tijdens de preview-periode.</span><span class="sxs-lookup"><span data-stu-id="27faa-242">The package is built for testing purposes during the preview period.</span></span>

<span data-ttu-id="27faa-243">Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina GitHub [releases] [releases].</span><span class="sxs-lookup"><span data-stu-id="27faa-243">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="27faa-244">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="27faa-244">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="27faa-245">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="27faa-245">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="27faa-246">Het MSIX-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="27faa-246">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="27faa-247">Als u het pakket wilt installeren, moet u de `Add-AppxPackage` cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="27faa-247">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="27faa-248">Een extern eind punt maken</span><span class="sxs-lookup"><span data-stu-id="27faa-248">How to create a remoting endpoint</span></span>

<span data-ttu-id="27faa-249">Power shell ondersteunt het Power shell Remoting Protocol (PSRP) voor zowel WSMan als SSH.</span><span class="sxs-lookup"><span data-stu-id="27faa-249">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="27faa-250">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="27faa-250">For more information, see:</span></span>

- <span data-ttu-id="27faa-251">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="27faa-251">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="27faa-252">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="27faa-252">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="upgrading-an-existing-installation"></a><span data-ttu-id="27faa-253">Een bestaande installatie upgraden</span><span class="sxs-lookup"><span data-stu-id="27faa-253">Upgrading an existing installation</span></span>

<span data-ttu-id="27faa-254">Voor de beste resultaten bij het uitvoeren van een upgrade moet u dezelfde installatie methode gebruiken die u hebt gebruikt toen u Power shell voor het eerst installeerde.</span><span class="sxs-lookup"><span data-stu-id="27faa-254">For best results when upgrading, you should use the same install method you used when you first installed PowerShell.</span></span> <span data-ttu-id="27faa-255">Elke installatie methode installeert Power shell op een andere locatie.</span><span class="sxs-lookup"><span data-stu-id="27faa-255">Each installation method installs PowerShell in a different location.</span></span> <span data-ttu-id="27faa-256">Als u niet zeker weet hoe Power shell is geïnstalleerd, kunt u de geïnstalleerde locatie vergelijken met de pakket gegevens in dit artikel.</span><span class="sxs-lookup"><span data-stu-id="27faa-256">If you are not sure how PowerShell was installed, you can compare the installed location with the package information in this article.</span></span> <span data-ttu-id="27faa-257">Als u via het MSI-pakket hebt geïnstalleerd, wordt die informatie weer gegeven in het onderdeel **Program ma's en onderdelen** van het configuratie scherm.</span><span class="sxs-lookup"><span data-stu-id="27faa-257">If you installed via the MSI package, that information appears in the **Programs and Features** Control Panel.</span></span>

## <a name="installation-support"></a><span data-ttu-id="27faa-258">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="27faa-258">Installation support</span></span>

<span data-ttu-id="27faa-259">Micro soft ondersteunt de installatie methoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="27faa-259">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="27faa-260">Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="27faa-260">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="27faa-261">Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="27faa-261">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[Voorbeeld]: https://aka.ms/powershell-release?tag=preview
[preview]: https://aka.ms/powershell-release?tag=preview
[meest recente]: https://aka.ms/powershell-release?tag=stable
[latest]: https://aka.ms/powershell-release?tag=stable
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["een andere instantie-techniek"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
