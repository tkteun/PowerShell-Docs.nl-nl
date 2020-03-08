---
title: Power shell in Windows installeren
description: Informatie over het installeren van Power shell in Windows
ms.date: 08/06/2018
ms.openlocfilehash: df05a16bcf7a81d43d24535e50517fa217f82e7a
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78405090"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="0f37e-103">Power shell in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="0f37e-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="0f37e-104">Er zijn meerdere manieren om Power shell in Windows te installeren.</span><span class="sxs-lookup"><span data-stu-id="0f37e-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f37e-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0f37e-105">Prerequisites</span></span>

<span data-ttu-id="0f37e-106">Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="0f37e-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="0f37e-107">Installeer de [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies ouder dan Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0f37e-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="0f37e-108">Het is beschikbaar via direct downloaden of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0f37e-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="0f37e-109">Volledige patches (inclusief optionele pakketten), de ondersteunde systemen hebben dit al geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="0f37e-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="0f37e-110">Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="0f37e-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="0f37e-111">Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.</span><span class="sxs-lookup"><span data-stu-id="0f37e-111">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="0f37e-112"><a id="msi" />het MSI-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="0f37e-112"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="0f37e-113">Als u Power shell wilt installeren op een Windows-client of Windows-Server (werkt met Windows 7 SP1, Server 2008 R2 en hoger), downloadt u het MSI-pakket van onze pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="0f37e-113">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="0f37e-114">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="0f37e-114">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="0f37e-115">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="0f37e-115">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="0f37e-116">Het MSI-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="0f37e-116">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>

<span data-ttu-id="0f37e-117">Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="0f37e-117">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="0f37e-118">Het installatie programma maakt een snelkoppeling in het menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="0f37e-118">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="0f37e-119">Standaard wordt het pakket geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="0f37e-119">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="0f37e-120">U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="0f37e-120">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="0f37e-121">Power shell 7 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows Power shell 5,1.</span><span class="sxs-lookup"><span data-stu-id="0f37e-121">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="0f37e-122">Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0f37e-122">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="0f37e-123">Power shell 7 is geïnstalleerd op `%programfiles%\PowerShell\7`</span><span class="sxs-lookup"><span data-stu-id="0f37e-123">PowerShell 7 is installed to `%programfiles%\PowerShell\7`</span></span>
> - <span data-ttu-id="0f37e-124">De map `%programfiles%\PowerShell\7` wordt toegevoegd aan `$env:PATH`</span><span class="sxs-lookup"><span data-stu-id="0f37e-124">The `%programfiles%\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="0f37e-125">De map `%programfiles%\PowerShell\6` wordt verwijderd</span><span class="sxs-lookup"><span data-stu-id="0f37e-125">The `%programfiles%\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="0f37e-126">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met de methode [zip-installatie](#zip) .</span><span class="sxs-lookup"><span data-stu-id="0f37e-126">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="0f37e-127">Beheerders installatie vanaf de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="0f37e-127">Administrative install from the command line</span></span>

<span data-ttu-id="0f37e-128">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="0f37e-128">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="0f37e-129">Hiermee kunnen beheerders pakketten implementeren zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0f37e-129">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="0f37e-130">Het MSI-pakket voor Power shell bevat de volgende eigenschappen voor het beheren van de installatie opties:</span><span class="sxs-lookup"><span data-stu-id="0f37e-130">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="0f37e-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="0f37e-131">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="0f37e-132">**ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="0f37e-132">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="0f37e-133">**REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="0f37e-133">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="0f37e-134">In de volgende voor beelden ziet u hoe u Power shell op de achtergrond installeert met alle installatie opties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="0f37e-134">The following examples shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="0f37e-135">Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor Msiexec. exe.</span><span class="sxs-lookup"><span data-stu-id="0f37e-135">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idmsix-installing-the-msix-package"></a><span data-ttu-id="0f37e-136"><a id="msix" />het MSIX-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="0f37e-136"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="0f37e-137">Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="0f37e-137">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="0f37e-138">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="0f37e-138">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="0f37e-139">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="0f37e-139">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="0f37e-140">Het MSIX-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="0f37e-140">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="0f37e-141">Nadat u het installatie programma hebt gedownload, kunt u het niet gewoon dubbel klikken. dit pakket vereist het gebruik van niet-gevirtualiseerde resources.</span><span class="sxs-lookup"><span data-stu-id="0f37e-141">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="0f37e-142">Als u wilt installeren, moet u de cmdlet `Add-AppxPackage` gebruiken:</span><span class="sxs-lookup"><span data-stu-id="0f37e-142">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="0f37e-143"><a id="zip" />het ZIP-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="0f37e-143"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="0f37e-144">Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="0f37e-144">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="0f37e-145">Wanneer u het ZIP-archief gebruikt, wordt de controle van vereisten niet weer gegeven als in het MSI-pakket.</span><span class="sxs-lookup"><span data-stu-id="0f37e-145">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="0f37e-146">Zorg ervoor dat u aan de [vereisten](#prerequisites)hebt voldaan voor externe communicatie via WSMan.</span><span class="sxs-lookup"><span data-stu-id="0f37e-146">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="0f37e-147">Implementeren op Windows IoT</span><span class="sxs-lookup"><span data-stu-id="0f37e-147">Deploying on Windows IoT</span></span>

<span data-ttu-id="0f37e-148">Windows IoT wordt al geleverd met Windows Power shell en kan worden gebruikt voor het implementeren van Power shell 7.</span><span class="sxs-lookup"><span data-stu-id="0f37e-148">Windows IoT already comes with Windows PowerShell which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="0f37e-149">`PSSession` maken op doel apparaat</span><span class="sxs-lookup"><span data-stu-id="0f37e-149">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="0f37e-150">Het ZIP-pakket kopiëren naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="0f37e-150">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="0f37e-151">Verbinding maken met het apparaat en het archief uitvouwen</span><span class="sxs-lookup"><span data-stu-id="0f37e-151">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="0f37e-152">Externe toegang tot Power shell 7 instellen</span><span class="sxs-lookup"><span data-stu-id="0f37e-152">Setup remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="0f37e-153">Verbinding maken met het Power shell 7-eind punt op het apparaat</span><span class="sxs-lookup"><span data-stu-id="0f37e-153">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="0f37e-154">Implementeren op nano server</span><span class="sxs-lookup"><span data-stu-id="0f37e-154">Deploying on Nano Server</span></span>

<span data-ttu-id="0f37e-155">Bij deze instructies wordt ervan uitgegaan dat er al een versie van Power shell wordt uitgevoerd op de nano server-installatie kopie en dat deze is gegenereerd door de [Image Builder-installatie kopie van nano server](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="0f37e-155">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="0f37e-156">Nano server is een ' headless ' besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="0f37e-156">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="0f37e-157">Binaire Power Shell-bestanden kunnen worden geïmplementeerd met twee verschillende methoden.</span><span class="sxs-lookup"><span data-stu-id="0f37e-157">PowerShell binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="0f37e-158">De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="0f37e-158">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="0f37e-159">Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="0f37e-159">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="0f37e-160">In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig en moet u de opdrachten uitvoeren in het Power shell-exemplaar ' Administrator '.</span><span class="sxs-lookup"><span data-stu-id="0f37e-160">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="0f37e-161">Offline-implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="0f37e-161">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="0f37e-162">Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="0f37e-162">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="0f37e-163">Ontkoppel de installatie kopie en start deze op.</span><span class="sxs-lookup"><span data-stu-id="0f37e-163">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="0f37e-164">Verbinding maken met het postvak in van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="0f37e-164">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="0f37e-165">Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="0f37e-165">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="0f37e-166">Online implementatie van Power shell</span><span class="sxs-lookup"><span data-stu-id="0f37e-166">Online Deployment of PowerShell</span></span>

<span data-ttu-id="0f37e-167">De volgende stappen begeleiden u bij de implementatie van Power shell naar een actief exemplaar van nano server en de configuratie van het externe eind punt.</span><span class="sxs-lookup"><span data-stu-id="0f37e-167">The following steps guide you through the deployment of PowerShell to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="0f37e-168">Verbinding maken met het postvak in van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="0f37e-168">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="0f37e-169">Kopieer het bestand naar het Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="0f37e-169">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="0f37e-170">De sessie invoeren</span><span class="sxs-lookup"><span data-stu-id="0f37e-170">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="0f37e-171">Het ZIP-bestand uitpakken</span><span class="sxs-lookup"><span data-stu-id="0f37e-171">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="0f37e-172">Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="0f37e-172">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="0f37e-173">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="0f37e-173">Install as a .NET Global tool</span></span>

<span data-ttu-id="0f37e-174">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="0f37e-174">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="0f37e-175">Een extern eind punt maken</span><span class="sxs-lookup"><span data-stu-id="0f37e-175">How to create a remoting endpoint</span></span>

<span data-ttu-id="0f37e-176">Power shell ondersteunt het Power shell Remoting Protocol (PSRP) voor zowel WSMan als SSH.</span><span class="sxs-lookup"><span data-stu-id="0f37e-176">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="0f37e-177">Ga voor meer informatie naar:</span><span class="sxs-lookup"><span data-stu-id="0f37e-177">For more information, see:</span></span>

- <span data-ttu-id="0f37e-178">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="0f37e-178">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="0f37e-179">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="0f37e-179">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
