---
title: PowerShell installeren in Windows
description: Informatie over het installeren van Power shell in Windows
ms.date: 08/06/2018
ms.openlocfilehash: 77da64b9692b326d83c04ce329675cdfd942e64c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691936"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="d541c-103">PowerShell installeren in Windows</span><span class="sxs-lookup"><span data-stu-id="d541c-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="d541c-104">Er zijn meerdere manieren om Power shell in Windows te installeren.</span><span class="sxs-lookup"><span data-stu-id="d541c-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d541c-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d541c-105">Prerequisites</span></span>

<span data-ttu-id="d541c-106">De meest recente versie van Power shell wordt ondersteund op Windows 7 SP1, Server 2008 R2 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="d541c-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="d541c-107">Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="d541c-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="d541c-108">Installeer de [universele C-runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="d541c-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="d541c-109">Het is beschikbaar via direct downloaden of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="d541c-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="d541c-110">Dit pakket is al geïnstalleerd op systemen met volledige patches.</span><span class="sxs-lookup"><span data-stu-id="d541c-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="d541c-111">Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="d541c-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="d541c-112">Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.</span><span class="sxs-lookup"><span data-stu-id="d541c-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="d541c-113">Het installatie pakket downloaden</span><span class="sxs-lookup"><span data-stu-id="d541c-113">Download the installer package</span></span>

<span data-ttu-id="d541c-114">Als u Power shell in Windows wilt installeren, downloadt u het installatie pakket van onze pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="d541c-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="d541c-115">Schuif omlaag naar de sectie **assets** van de pagina release.</span><span class="sxs-lookup"><span data-stu-id="d541c-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="d541c-116">De sectie **assets** kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="d541c-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="d541c-117"><a id="msi" />Het MSI-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="d541c-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="d541c-118">Het MSI-bestand ziet er als volgt uit `PowerShell-<version>-win-<os-arch>.msi` .</span><span class="sxs-lookup"><span data-stu-id="d541c-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="d541c-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d541c-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="d541c-120">Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="d541c-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="d541c-121">Het installatie programma maakt een snelkoppeling in het menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="d541c-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="d541c-122">Het pakket is standaard geïnstalleerd voor`$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="d541c-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="d541c-123">U kunt Power shell starten via het menu Start of`$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="d541c-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="d541c-124">Power shell 7 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="d541c-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="d541c-125">Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d541c-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="d541c-126">Power shell 7 is geïnstalleerd op`$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="d541c-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="d541c-127">De `$env:ProgramFiles\PowerShell\7` map wordt toegevoegd aan`$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="d541c-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="d541c-128">De `$env:ProgramFiles\PowerShell\6` map wordt verwijderd</span><span class="sxs-lookup"><span data-stu-id="d541c-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="d541c-129">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met de methode [zip-installatie](#zip) .</span><span class="sxs-lookup"><span data-stu-id="d541c-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="d541c-130">Beheerders installatie vanaf de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="d541c-130">Administrative install from the command line</span></span>

<span data-ttu-id="d541c-131">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel zodat beheerders pakketten kunnen implementeren zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d541c-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="d541c-132">Het MSI-pakket bevat de volgende eigenschappen om de installatie opties te beheren:</span><span class="sxs-lookup"><span data-stu-id="d541c-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="d541c-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="d541c-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="d541c-134">**ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="d541c-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="d541c-135">**REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="d541c-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="d541c-136">In het volgende voor beeld ziet u hoe u Power shell op de achtergrond installeert met alle installatie opties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d541c-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="d541c-137">`Msiexec.exe`Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor.</span><span class="sxs-lookup"><span data-stu-id="d541c-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="d541c-138"><a id="msix" />Het MSIX-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="d541c-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="d541c-139">Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="d541c-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="d541c-140">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="d541c-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="d541c-141">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="d541c-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="d541c-142">Het MSIX-bestand ziet er als volgt uit:`PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="d541c-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="d541c-143">Als u het pakket wilt installeren, moet u de `Add-AppxPackage` cmdlet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d541c-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="d541c-144">Het MSIX-pakket is nog niet vrijgegeven.</span><span class="sxs-lookup"><span data-stu-id="d541c-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="d541c-145">Wanneer het pakket is vrijgegeven, is het beschikbaar in het Microsoft Store en op de pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="d541c-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="d541c-146"><a id="zip" />Het ZIP-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="d541c-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="d541c-147">Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="d541c-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="d541c-148">Het installeren van het ZIP-archief controleert niet de vereisten zoals de MSI-pakketten.</span><span class="sxs-lookup"><span data-stu-id="d541c-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="d541c-149">Down load het ZIP-archief vanaf de pagina [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="d541c-149">Download the ZIP archive from the [releases][releases] page.</span></span> <span data-ttu-id="d541c-150">Afhankelijk van hoe u het bestand downloadt, moet u het bestand mogelijk deblokkeren met de `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d541c-150">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="d541c-151">Pak de inhoud uit naar de gewenste locatie en voer deze `pwsh.exe` uit.</span><span class="sxs-lookup"><span data-stu-id="d541c-151">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="d541c-152">Zorg ervoor dat u aan de [vereisten](#prerequisites)voldoet om externe toegang tot WSMan goed te laten werken.</span><span class="sxs-lookup"><span data-stu-id="d541c-152">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="d541c-153">Implementeren in Windows 10 IoT Enter prise</span><span class="sxs-lookup"><span data-stu-id="d541c-153">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="d541c-154">Windows 10 IoT Enter prise wordt geleverd met Windows Power shell en kan worden gebruikt voor het implementeren van Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="d541c-154">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="d541c-155">Maken `PSSession` op doel apparaat</span><span class="sxs-lookup"><span data-stu-id="d541c-155">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="d541c-156">Het ZIP-pakket kopiëren naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="d541c-156">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="d541c-157">Verbinding maken met het apparaat en het archief uitvouwen</span><span class="sxs-lookup"><span data-stu-id="d541c-157">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="d541c-158">Externe toegang instellen met Power shell 7</span><span class="sxs-lookup"><span data-stu-id="d541c-158">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="d541c-159">Verbinding maken met het Power shell 7-eind punt op het apparaat</span><span class="sxs-lookup"><span data-stu-id="d541c-159">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="d541c-160">Implementeren in Windows 10 IoT core</span><span class="sxs-lookup"><span data-stu-id="d541c-160">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="d541c-161">Windows 10 IoT core voegt Windows Power shell toe wanneer u *IOT_POWERSHELL* -functie opneemt, die we kunnen gebruiken om Power shell 7 te implementeren.</span><span class="sxs-lookup"><span data-stu-id="d541c-161">Windows 10 IoT Core adds Windows PowerShell when you include *IOT_POWERSHELL* feature, which we can use to deploy PowerShell 7.</span></span>
<span data-ttu-id="d541c-162">De stappen die hierboven voor Windows 10 IoT Enter prise zijn gedefinieerd, kunnen ook worden gevolgd voor IoT core.</span><span class="sxs-lookup"><span data-stu-id="d541c-162">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="d541c-163">Voor het toevoegen van de meest recente Power shell in de verzend installatie kopie gebruikt u de opdracht [import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) om het pakket op te zetten in de workarea en voegt u *OPENSRC_POWERSHELL* functie toe aan uw installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="d541c-163">For adding the latest powershell in the shipping image, use [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) command to include the package in the workarea and add *OPENSRC_POWERSHELL* feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="d541c-164">Voor ARM64-architectuur wordt Windows Power shell niet toegevoegd wanneer u *IOT_POWERSHELL*opneemt.</span><span class="sxs-lookup"><span data-stu-id="d541c-164">For ARM64 architecture, Windows Powershell is not added when you include *IOT_POWERSHELL*.</span></span> <span data-ttu-id="d541c-165">De op ZIP gebaseerde installatie werkt dus niet.</span><span class="sxs-lookup"><span data-stu-id="d541c-165">So the zip based install will not work.</span></span>
> <span data-ttu-id="d541c-166">U moet de opdracht import-PSCoreRelease gebruiken om deze toe te voegen aan de installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="d541c-166">You will need to use Import-PSCoreRelease command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="d541c-167">Implementeren op nano server</span><span class="sxs-lookup"><span data-stu-id="d541c-167">Deploying on Nano Server</span></span>

<span data-ttu-id="d541c-168">Bij deze instructies wordt ervan uitgegaan dat de nano server een ' headless ' besturings systeem is waarop al een versie van Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d541c-168">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="d541c-169">Zie de documentatie van [nano server Image Builder](/windows-server/get-started/deploy-nano-server) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d541c-169">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="d541c-170">Binaire Power Shell-bestanden kunnen met twee verschillende methoden worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="d541c-170">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="d541c-171">De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="d541c-171">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="d541c-172">Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="d541c-172">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="d541c-173">In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig.</span><span class="sxs-lookup"><span data-stu-id="d541c-173">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="d541c-174">Voer de opdrachten uit in een ' beheerder ' exemplaar van Power shell.</span><span class="sxs-lookup"><span data-stu-id="d541c-174">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="d541c-175">Offline-implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="d541c-175">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="d541c-176">Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="d541c-176">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="d541c-177">Ontkoppel de installatie kopie en start deze op.</span><span class="sxs-lookup"><span data-stu-id="d541c-177">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="d541c-178">Verbinding maken met het postvak in van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="d541c-178">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="d541c-179">Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="d541c-179">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="d541c-180">Online implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="d541c-180">Online Deployment of PowerShell</span></span>

<span data-ttu-id="d541c-181">Implementeer Power shell naar nano server met behulp van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="d541c-181">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="d541c-182">Verbinding maken met het postvak in van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="d541c-182">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="d541c-183">Kopieer het bestand naar het Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="d541c-183">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="d541c-184">De sessie invoeren</span><span class="sxs-lookup"><span data-stu-id="d541c-184">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="d541c-185">Het ZIP-bestand uitpakken</span><span class="sxs-lookup"><span data-stu-id="d541c-185">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="d541c-186">Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="d541c-186">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="d541c-187">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="d541c-187">Install as a .NET Global tool</span></span>

<span data-ttu-id="d541c-188">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="d541c-188">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="d541c-189">Het hulp programma DotNet tool wordt toegevoegd `$env:USERPROFILE\dotnet\tools` aan de `$env:PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="d541c-189">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="d541c-190">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `$env:PATH` .</span><span class="sxs-lookup"><span data-stu-id="d541c-190">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="d541c-191">U kunt Power shell starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="d541c-191">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="d541c-192">Een extern eind punt maken</span><span class="sxs-lookup"><span data-stu-id="d541c-192">How to create a remoting endpoint</span></span>

<span data-ttu-id="d541c-193">Power shell ondersteunt het Power shell Remoting Protocol (PSRP) voor zowel WSMan als SSH.</span><span class="sxs-lookup"><span data-stu-id="d541c-193">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="d541c-194">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="d541c-194">For more information, see:</span></span>

- <span data-ttu-id="d541c-195">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="d541c-195">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="d541c-196">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="d541c-196">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
