---
title: PowerShell Core in Windows installeren
description: Informatie over het installeren van Power shell core in Windows
ms.date: 08/06/2018
ms.openlocfilehash: 00a1d8064a3c1ec6608a46415bbabb8d98d880f0
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416784"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="f39e4-103">PowerShell Core in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="f39e4-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="f39e4-104">Er zijn meerdere manieren om Power shell core in Windows te installeren.</span><span class="sxs-lookup"><span data-stu-id="f39e4-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

> [!TIP]
> <span data-ttu-id="f39e4-105">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="f39e4-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a><span data-ttu-id="f39e4-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f39e4-106">Prerequisites</span></span>

<span data-ttu-id="f39e4-107">Als u externe communicatie van Power shell wilt inschakelen via WSMan, moeten aan de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="f39e4-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="f39e4-108">Installeer de [Universal C runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies ouder dan Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f39e4-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="f39e4-109">Het is beschikbaar via direct downloaden of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="f39e4-109">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="f39e4-110">Volledige patches (inclusief optionele pakketten), de ondersteunde systemen hebben dit al geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f39e4-110">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="f39e4-111">Installeer Windows Management Framework (WMF) 4,0 of nieuwer op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="f39e4-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="f39e4-112">Zie [overzicht van WMF](/powershell/scripting/wmf/overview)voor meer informatie over WMF.</span><span class="sxs-lookup"><span data-stu-id="f39e4-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="f39e4-113"><a id="msi" />het MSI-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="f39e4-113"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="f39e4-114">Als u Power shell wilt installeren op een Windows-client of Windows-Server (werkt met Windows 7 SP1, Server 2008 R2 en hoger), downloadt u het MSI-pakket van onze pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="f39e4-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="f39e4-115">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="f39e4-115">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="f39e4-116">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="f39e4-116">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="f39e4-117">Het MSI-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="f39e4-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="f39e4-118">Na het downloaden dubbelklikt u op het installatie programma en volgt u de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="f39e4-118">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="f39e4-119">Het installatie programma maakt een snelkoppeling in het menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="f39e4-119">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="f39e4-120">Standaard wordt het pakket geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="f39e4-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="f39e4-121">U kunt Power shell starten via het menu Start of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="f39e4-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="f39e4-122">Beheerders installatie vanaf de opdracht regel</span><span class="sxs-lookup"><span data-stu-id="f39e4-122">Administrative install from the command line</span></span>

<span data-ttu-id="f39e4-123">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="f39e4-123">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="f39e4-124">Hiermee kunnen beheerders pakketten implementeren zonder tussen komst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f39e4-124">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="f39e4-125">Het MSI-pakket voor Power shell bevat de volgende eigenschappen voor het beheren van de installatie opties:</span><span class="sxs-lookup"><span data-stu-id="f39e4-125">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="f39e4-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** : met deze eigenschap bepaalt u de optie voor het toevoegen van het **geopende Power shell** -item aan het context menu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="f39e4-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="f39e4-127">**ENABLE_PSREMOTING** : deze eigenschap bepaalt de optie voor het inschakelen van externe communicatie van Power shell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="f39e4-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="f39e4-128">**REGISTER_MANIFEST** -met deze eigenschap bepaalt u de optie voor het registreren van het Windows-logboek voor gebeurtenis logboek registratie.</span><span class="sxs-lookup"><span data-stu-id="f39e4-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="f39e4-129">In de volgende voor beelden ziet u hoe u Power shell Core op de achtergrond installeert met alle installatie opties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="f39e4-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="f39e4-130">Zie [opdracht regel opties](/windows/desktop/Msi/command-line-options)voor een volledige lijst met opdracht regel opties voor Msiexec. exe.</span><span class="sxs-lookup"><span data-stu-id="f39e4-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idmsix-installing-the-msix-package"></a><span data-ttu-id="f39e4-131"><a id="msix" />het MSIX-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="f39e4-131"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="f39e4-132">Als u het MSIX-pakket hand matig wilt installeren op een Windows 10-client, downloadt u het MSIX-pakket van de pagina met GitHub- [releases][releases] .</span><span class="sxs-lookup"><span data-stu-id="f39e4-132">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="f39e4-133">Schuif omlaag naar de sectie **assets** van de release die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="f39e4-133">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="f39e4-134">De sectie assets kan worden samengevouwen, dus u moet mogelijk op klikken om deze uit te vouwen.</span><span class="sxs-lookup"><span data-stu-id="f39e4-134">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="f39e4-135">Het MSI-bestand ziet er als volgt uit: `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="f39e4-135">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="f39e4-136">Nadat u het installatie programma hebt gedownload, kunt u het niet gewoon dubbel klikken. dit pakket vereist het gebruik van niet-gevirtualiseerde resources.</span><span class="sxs-lookup"><span data-stu-id="f39e4-136">Once downloaded, you cannot simply double-click on the installer as this package requires use of un-virtualized resources.</span></span>  <span data-ttu-id="f39e4-137">Als u wilt installeren, moet u de cmdlet `Add-AppxPackage` gebruiken:</span><span class="sxs-lookup"><span data-stu-id="f39e4-137">To install, you must use the `Add-AppxPackage` cmdlet:</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="f39e4-138"><a id="zip" />het ZIP-pakket niet installeren</span><span class="sxs-lookup"><span data-stu-id="f39e4-138"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="f39e4-139">Binaire ZIP-archieven van Power shell zijn beschikbaar om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="f39e4-139">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="f39e4-140">Wanneer u het ZIP-archief gebruikt, wordt de controle van vereisten niet weer gegeven als in het MSI-pakket.</span><span class="sxs-lookup"><span data-stu-id="f39e4-140">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="f39e4-141">Zorg ervoor dat u aan de [vereisten](#prerequisites)hebt voldaan voor externe communicatie via WSMan.</span><span class="sxs-lookup"><span data-stu-id="f39e4-141">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="f39e4-142">Implementeren op Windows IoT</span><span class="sxs-lookup"><span data-stu-id="f39e4-142">Deploying on Windows IoT</span></span>

<span data-ttu-id="f39e4-143">Windows IoT wordt al geleverd met Windows Power shell en wordt gebruikt voor het implementeren van Power shell Core 6.</span><span class="sxs-lookup"><span data-stu-id="f39e4-143">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="f39e4-144">`PSSession` maken op doel apparaat</span><span class="sxs-lookup"><span data-stu-id="f39e4-144">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="f39e4-145">Het ZIP-pakket kopiëren naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="f39e4-145">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="f39e4-146">Verbinding maken met het apparaat en het archief uitvouwen</span><span class="sxs-lookup"><span data-stu-id="f39e4-146">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="f39e4-147">Externe toegang tot Power shell Core 6 instellen</span><span class="sxs-lookup"><span data-stu-id="f39e4-147">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="f39e4-148">Verbinding maken met het Power shell Core 6-eind punt op het apparaat</span><span class="sxs-lookup"><span data-stu-id="f39e4-148">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="f39e4-149">Implementeren op nano server</span><span class="sxs-lookup"><span data-stu-id="f39e4-149">Deploying on Nano Server</span></span>

<span data-ttu-id="f39e4-150">Bij deze instructies wordt ervan uitgegaan dat er al een versie van Power shell wordt uitgevoerd op de nano server-installatie kopie en dat deze is gegenereerd door de [Image Builder-installatie kopie van nano server](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="f39e4-150">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="f39e4-151">Nano server is een ' headless ' besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="f39e4-151">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="f39e4-152">Kern-binaire bestanden kunnen worden geïmplementeerd met twee verschillende methoden.</span><span class="sxs-lookup"><span data-stu-id="f39e4-152">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="f39e4-153">De nano server-VHD offline koppelen en de inhoud van het zip-bestand uitpakken naar de gekozen locatie in de gekoppelde installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="f39e4-153">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="f39e4-154">Online: zet het zip-bestand over een Power shell-sessie over en pak het uit op uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="f39e4-154">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="f39e4-155">In beide gevallen hebt u het Windows 10 x64 ZIP-release pakket nodig en moet u de opdrachten uitvoeren in het Power shell-exemplaar ' Administrator '.</span><span class="sxs-lookup"><span data-stu-id="f39e4-155">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="f39e4-156">Offline-implementatie van Power shell core</span><span class="sxs-lookup"><span data-stu-id="f39e4-156">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="f39e4-157">Gebruik uw favoriete zip-hulp programma om het pakket uit te pakken naar een map in de gekoppelde nano server-installatie kopie.</span><span class="sxs-lookup"><span data-stu-id="f39e4-157">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="f39e4-158">Ontkoppel de installatie kopie en start deze op.</span><span class="sxs-lookup"><span data-stu-id="f39e4-158">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="f39e4-159">Verbinding maken met het postvak in van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="f39e4-159">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="f39e4-160">Volg de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="f39e4-160">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="f39e4-161">Online implementatie van Power shell core</span><span class="sxs-lookup"><span data-stu-id="f39e4-161">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="f39e4-162">De volgende stappen begeleiden u bij de implementatie van Power shell core naar een actief exemplaar van nano server en de configuratie van het externe eind punt.</span><span class="sxs-lookup"><span data-stu-id="f39e4-162">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="f39e4-163">Verbinding maken met het postvak in van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="f39e4-163">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="f39e4-164">Kopieer het bestand naar het Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="f39e4-164">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="f39e4-165">De sessie invoeren</span><span class="sxs-lookup"><span data-stu-id="f39e4-165">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="f39e4-166">Het ZIP-bestand uitpakken</span><span class="sxs-lookup"><span data-stu-id="f39e4-166">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="f39e4-167">Als u externe toegang op basis van WSMan wilt gebruiken, volgt u de instructies voor het maken van een extern eind punt met behulp van de ["andere instantie techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="f39e4-167">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="f39e4-168">Een extern eind punt maken</span><span class="sxs-lookup"><span data-stu-id="f39e4-168">How to create a remoting endpoint</span></span>

<span data-ttu-id="f39e4-169">Power shell core ondersteunt het PSRP (Power shell Remoting Protocol) voor zowel WSMan als SSH.</span><span class="sxs-lookup"><span data-stu-id="f39e4-169">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="f39e4-170">Zie voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="f39e4-170">For more information, see:</span></span>

- <span data-ttu-id="f39e4-171">[Externe SSH-communicatie in Power shell core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="f39e4-171">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="f39e4-172">[Externe WSMan-communicatie in Power shell core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="f39e4-172">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
