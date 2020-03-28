---
title: PowerShell installeren in Windows
description: Informatie over het installeren van Power shell in Windows
ms.date: 08/06/2018
ms.openlocfilehash: ea5432725f4baea8c688fb8e67482910e2c3981e
ms.sourcegitcommit: b6cf10224eb9f32919a505cdffbe5968241c18a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/28/2020
ms.locfileid: "80374896"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="7aa3f-103">PowerShell installeren in Windows</span><span class="sxs-lookup"><span data-stu-id="7aa3f-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="7aa3f-104">Er zijn meerdere manieren om Power shell in Windows te installeren.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7aa3f-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7aa3f-105">Prerequisites</span></span>

<span data-ttu-id="7aa3f-106">De meest recente versie van Power shell wordt ondersteund op Windows 7 SP1, Server 2008 R2 en latere versies.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="7aa3f-107">Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="7aa3f-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="7aa3f-108">Installeer de [universele C-runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies predating Windows 10.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="7aa3f-109">Het is beschikbaar via direct downloaden of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="7aa3f-110">Dit pakket is al geïnstalleerd op systemen met volledige patches.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="7aa3f-111">Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="7aa3f-112">Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="7aa3f-113">Het installatie pakket downloaden</span><span class="sxs-lookup"><span data-stu-id="7aa3f-113">Download the installer package</span></span>

<span data-ttu-id="7aa3f-114">Als u Power shell in Windows wilt installeren, downloadt u het installatie pakket van onze pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="7aa3f-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="7aa3f-115">Schuif omlaag naar de sectie **assets** van de pagina release.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="7aa3f-116">De sectie **assets** kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="7aa3f-117"><a id="msi" />het MSI-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="7aa3f-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="7aa3f-118">Het MSI-bestand ziet eruit als `PowerShell-<version>-win-<os-arch>.msi`.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="7aa3f-119">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7aa3f-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="7aa3f-120">Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="7aa3f-121">Het installatie programma maakt een snelkoppeling in het menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="7aa3f-122">Standaard wordt het pakket geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="7aa3f-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="7aa3f-123">U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="7aa3f-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="7aa3f-124">Power shell 7 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="7aa3f-125">Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="7aa3f-126">Power shell 7 is geïnstalleerd op `$env:ProgramFiles\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="7aa3f-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="7aa3f-127">De map `$env:ProgramFiles\PowerShell\7` wordt toegevoegd aan `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="7aa3f-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="7aa3f-128">De map `$env:ProgramFiles\PowerShell\6` wordt verwijderd</span><span class="sxs-lookup"><span data-stu-id="7aa3f-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="7aa3f-129">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met de methode [zip-installatie](#zip) .</span><span class="sxs-lookup"><span data-stu-id="7aa3f-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="7aa3f-130">Beheerders installatie vanaf de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="7aa3f-130">Administrative install from the command line</span></span>

<span data-ttu-id="7aa3f-131">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel zodat beheerders pakketten kunnen implementeren zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="7aa3f-132">Het MSI-pakket bevat de volgende eigenschappen om de installatie opties te beheren:</span><span class="sxs-lookup"><span data-stu-id="7aa3f-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="7aa3f-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="7aa3f-134">**ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="7aa3f-135">**REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="7aa3f-136">In het volgende voor beeld ziet u hoe u Power shell op de achtergrond installeert met alle installatie opties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="7aa3f-137">Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor `Msiexec.exe`.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="7aa3f-138"><a id="msix" />het MSIX-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="7aa3f-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="7aa3f-139">Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="7aa3f-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="7aa3f-140">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="7aa3f-141">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="7aa3f-142">Het MSIX-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="7aa3f-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="7aa3f-143">Als u het pakket wilt installeren, moet u de cmdlet `Add-AppxPackage` gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="7aa3f-144">Het MSIX-pakket is nog niet vrijgegeven.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="7aa3f-145">Wanneer het pakket is vrijgegeven, is het beschikbaar in het Microsoft Store en op de pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="7aa3f-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="7aa3f-146"><a id="zip" />het ZIP-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="7aa3f-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="7aa3f-147">Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="7aa3f-148">Het installeren van het ZIP-archief controleert niet de vereisten zoals de MSI-pakketten.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="7aa3f-149">Zorg ervoor dat u aan de [vereisten](#prerequisites)voldoet om externe toegang tot WSMan goed te laten werken.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-149">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="7aa3f-150">Implementeren op Windows IoT</span><span class="sxs-lookup"><span data-stu-id="7aa3f-150">Deploying on Windows IoT</span></span>

<span data-ttu-id="7aa3f-151">Windows IoT wordt geleverd met Windows Power shell en kan worden gebruikt voor het implementeren van Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-151">Windows IoT comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="7aa3f-152">`PSSession` maken op doel apparaat</span><span class="sxs-lookup"><span data-stu-id="7aa3f-152">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="7aa3f-153">Het ZIP-pakket kopiëren naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="7aa3f-153">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="7aa3f-154">Verbinding maken met het apparaat en het archief uitvouwen</span><span class="sxs-lookup"><span data-stu-id="7aa3f-154">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="7aa3f-155">Externe toegang instellen met Power shell 7</span><span class="sxs-lookup"><span data-stu-id="7aa3f-155">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="7aa3f-156">Verbinding maken met het Power shell 7-eind punt op het apparaat</span><span class="sxs-lookup"><span data-stu-id="7aa3f-156">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="7aa3f-157">Implementeren op nano server</span><span class="sxs-lookup"><span data-stu-id="7aa3f-157">Deploying on Nano Server</span></span>

<span data-ttu-id="7aa3f-158">Bij deze instructies wordt ervan uitgegaan dat de nano server een ' headless ' besturings systeem is waarop al een versie van Power shell wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-158">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="7aa3f-159">Zie de documentatie van [nano server Image Builder](/windows-server/get-started/deploy-nano-server) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-159">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="7aa3f-160">Binaire Power Shell-bestanden kunnen met twee verschillende methoden worden geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-160">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="7aa3f-161">De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-161">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="7aa3f-162">Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-162">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="7aa3f-163">In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-163">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="7aa3f-164">Voer de opdrachten uit in een ' beheerder ' exemplaar van Power shell.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-164">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="7aa3f-165">Offline-implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="7aa3f-165">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="7aa3f-166">Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-166">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="7aa3f-167">Ontkoppel de installatie kopie en start deze op.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-167">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="7aa3f-168">Verbinding maken met het postvak in van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-168">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="7aa3f-169">Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="7aa3f-169">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="7aa3f-170">Online implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="7aa3f-170">Online Deployment of PowerShell</span></span>

<span data-ttu-id="7aa3f-171">Implementeer Power shell naar nano server met behulp van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-171">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="7aa3f-172">Verbinding maken met het postvak in van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="7aa3f-172">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="7aa3f-173">Kopieer het bestand naar het Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="7aa3f-173">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="7aa3f-174">De sessie invoeren</span><span class="sxs-lookup"><span data-stu-id="7aa3f-174">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="7aa3f-175">Het ZIP-bestand uitpakken</span><span class="sxs-lookup"><span data-stu-id="7aa3f-175">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="7aa3f-176">Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="7aa3f-176">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="7aa3f-177">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="7aa3f-177">Install as a .NET Global tool</span></span>

<span data-ttu-id="7aa3f-178">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="7aa3f-178">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="7aa3f-179">Het installatie programma voor het DotNet-hulp programma voegt `$env:USERPROFILE\dotnet\tools` toe aan de omgevings variabele `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-179">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="7aa3f-180">De momenteel actieve shell beschikt echter niet over de bijgewerkte `$env:PATH`.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-180">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="7aa3f-181">U kunt Power shell starten vanuit een nieuwe shell door `pwsh`te typen.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-181">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="7aa3f-182">Een extern eind punt maken</span><span class="sxs-lookup"><span data-stu-id="7aa3f-182">How to create a remoting endpoint</span></span>

<span data-ttu-id="7aa3f-183">Power shell ondersteunt het Power shell Remoting Protocol (PSRP) voor zowel WSMan als SSH.</span><span class="sxs-lookup"><span data-stu-id="7aa3f-183">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="7aa3f-184">Ga voor meer informatie naar:</span><span class="sxs-lookup"><span data-stu-id="7aa3f-184">For more information, see:</span></span>

- <span data-ttu-id="7aa3f-185">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="7aa3f-185">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="7aa3f-186">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="7aa3f-186">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
