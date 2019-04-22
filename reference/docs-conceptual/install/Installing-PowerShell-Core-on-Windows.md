---
title: PowerShell Core in Windows installeren
description: Informatie over PowerShell Core in Windows installeren
ms.date: 08/06/2018
ms.openlocfilehash: 910ee5a653fc1703bfddaf6367225f3b654d600f
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59293007"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="e2670-103">PowerShell Core in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="e2670-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="e2670-104">Er zijn meerdere manieren voor het installeren van PowerShell Core in Windows.</span><span class="sxs-lookup"><span data-stu-id="e2670-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2670-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e2670-105">Prerequisites</span></span>

<span data-ttu-id="e2670-106">Om in te schakelen PowerShell voor externe toegang via WSMan, moeten de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="e2670-106">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="e2670-107">Installeer de [universeel C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies voorafgaand aan Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e2670-107">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="e2670-108">Het is beschikbaar via de directe download of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="e2670-108">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="e2670-109">Volledig hersteld (inclusief optionele pakketten), heeft ondersteunde systemen al dit geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="e2670-109">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="e2670-110">Installeer de Windows Management Framework (WMF) 4.0 of hoger op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="e2670-110">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="e2670-111"><a id="msi" />Het MSI-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="e2670-111"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="e2670-112">PowerShell installeren op een Windows-client of Windows Server (werkt op Windows 7 SP1, Server 2008 R2 en hoger), het MSI-pakket downloaden van onze GitHub [releases] [].</span><span class="sxs-lookup"><span data-stu-id="e2670-112">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span> <span data-ttu-id="e2670-113">Schuif omlaag naar de **activa** sectie van de versie die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="e2670-113">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="e2670-114">De sectie activa kan worden samengevouwen, dus misschien moet u klikt u op te geven.</span><span class="sxs-lookup"><span data-stu-id="e2670-114">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="e2670-115">Het MSI-bestand er als volgt uitzien: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="e2670-115">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="e2670-116">Nadat u hebt gedownload, dubbelklikt u op het installatieprogramma en volg de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="e2670-116">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="e2670-117">Het installatieprogramma wordt een snelkoppeling gemaakt in het Menu Start van Windows.</span><span class="sxs-lookup"><span data-stu-id="e2670-117">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="e2670-118">Het pakket wordt standaard geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="e2670-118">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="e2670-119">U kunt PowerShell via het Menu Start starten of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="e2670-119">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="e2670-120">Administratieve installeren vanaf de opdrachtregel</span><span class="sxs-lookup"><span data-stu-id="e2670-120">Administrative install from the command line</span></span>

<span data-ttu-id="e2670-121">MSI-pakketten kunnen worden geïnstalleerd vanaf de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="e2670-121">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="e2670-122">Hiermee kunnen beheerders het implementeren van pakketten zonder tussenkomst van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e2670-122">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="e2670-123">Het MSI-pakket voor PowerShell bevat de volgende eigenschappen voor het beheren van de opties voor de installatie:</span><span class="sxs-lookup"><span data-stu-id="e2670-123">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="e2670-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** -bepaalt deze eigenschap de optie voor het toevoegen van de **Open PowerShell** item aan het contextmenu in Windows Verkenner.</span><span class="sxs-lookup"><span data-stu-id="e2670-124">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="e2670-125">**ENABLE_PSREMOTING** -bepaalt deze eigenschap de optie voor het inschakelen van externe communicatie van PowerShell tijdens de installatie.</span><span class="sxs-lookup"><span data-stu-id="e2670-125">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="e2670-126">**REGISTER_MANIFEST** -bepaalt deze eigenschap de optie voor het registreren van het manifest voor logboekregistratie van Windows-gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="e2670-126">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="e2670-127">De volgende voorbeelden ziet hoe u PowerShell Core op de achtergrond installeert met alle van de installatieopties ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="e2670-127">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="e2670-128">Zie voor een volledige lijst met opdrachtregelopties voor Msiexec.exe, [opdrachtregelopties](/windows/desktop/Msi/command-line-options).</span><span class="sxs-lookup"><span data-stu-id="e2670-128">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="e2670-129"><a id="zip" />Het ZIP-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="e2670-129"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="e2670-130">PowerShell binaire ZIP-archieven zijn opgegeven voor het inschakelen van geavanceerde implementatiescenario's.</span><span class="sxs-lookup"><span data-stu-id="e2670-130">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="e2670-131">Worden opgemerkt bij het gebruik van het ZIP-archief, kunt u de controle van vereisten zoals in het MSI-pakket wordt niet ophalen.</span><span class="sxs-lookup"><span data-stu-id="e2670-131">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="e2670-132">Zorg ervoor dat u hebt voldaan voor externe toegang via WSMan goed te laten werken, de [vereisten](#prerequisites).</span><span class="sxs-lookup"><span data-stu-id="e2670-132">For remoting over WSMan to work properly,, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="e2670-133">Implementeren op Windows IoT</span><span class="sxs-lookup"><span data-stu-id="e2670-133">Deploying on Windows IoT</span></span>

<span data-ttu-id="e2670-134">Windows IoT is al wordt geleverd met Windows PowerShell die zullen worden gebruikt voor het implementeren van PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="e2670-134">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="e2670-135">Maak `PSSession` doelapparaat</span><span class="sxs-lookup"><span data-stu-id="e2670-135">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="e2670-136">Kopieer het ZIP-pakket naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="e2670-136">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="e2670-137">Verbinding maken met het apparaat en vouw het archief</span><span class="sxs-lookup"><span data-stu-id="e2670-137">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="e2670-138">Instellingen voor externe toegang tot en met 6 voor PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e2670-138">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="e2670-139">Verbinding maken met PowerShell Core 6-eindpunt op apparaat</span><span class="sxs-lookup"><span data-stu-id="e2670-139">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="e2670-140">Implementatie van op Nano Server</span><span class="sxs-lookup"><span data-stu-id="e2670-140">Deploying on Nano Server</span></span>

<span data-ttu-id="e2670-141">Deze instructies wordt ervan uitgegaan dat een versie van PowerShell al wordt uitgevoerd op de Nano Server-installatiekopie en dat deze is gegenereerd door de [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="e2670-141">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="e2670-142">Nano Server is een 'headless' besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="e2670-142">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="e2670-143">Kan de belangrijke binaire kunt implementeren met behulp van twee verschillende methoden.</span><span class="sxs-lookup"><span data-stu-id="e2670-143">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="e2670-144">Offline - de Nano Server-VHD koppelen en pak deze uit de inhoud van het zip-bestand naar uw gekozen locatie binnen de gekoppelde installatiekopie.</span><span class="sxs-lookup"><span data-stu-id="e2670-144">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="e2670-145">Online - overdragen van het zip-bestand via een PowerShell-sessie en pak het uit in uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="e2670-145">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="e2670-146">In beide gevallen moet u de versie van Windows 10 x64 ZIP verpakt en moet de opdrachten binnen een exemplaar 'Beheerder' PowerShell uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="e2670-146">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="e2670-147">Offline implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e2670-147">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="e2670-148">Gebruik uw favoriete zip-hulpprogramma voor het uitpakken van het pakket naar een map in de gekoppelde Nano Server-installatiekopie.</span><span class="sxs-lookup"><span data-stu-id="e2670-148">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="e2670-149">Ontkoppelen van de installatiekopie en het opstarten.</span><span class="sxs-lookup"><span data-stu-id="e2670-149">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="e2670-150">Verbinding maken met het exemplaar van het postvak in van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2670-150">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="e2670-151">Volg de instructies voor het maken van een externe toegang-eindpunt met de ["een ander exemplaar techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="e2670-151">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="e2670-152">Online implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="e2670-152">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="e2670-153">De volgende stappen begeleiden u bij de implementatie van PowerShell Core een exemplaar van de Nano Server en de configuratie van het externe eindpunt.</span><span class="sxs-lookup"><span data-stu-id="e2670-153">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="e2670-154">Verbinding maken met het exemplaar van het postvak in van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2670-154">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="e2670-155">Kopieer het bestand naar de Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="e2670-155">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="e2670-156">De sessie</span><span class="sxs-lookup"><span data-stu-id="e2670-156">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="e2670-157">Pak het ZIP-bestand</span><span class="sxs-lookup"><span data-stu-id="e2670-157">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="e2670-158">Als u externe toegang op basis van WSMan wilt, volg de instructies voor het maken van een externe toegang-eindpunt met de ["een ander exemplaar techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="e2670-158">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="e2670-159">Over het maken van een eindpunt voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="e2670-159">How to create a remoting endpoint</span></span>

<span data-ttu-id="e2670-160">PowerShell Core biedt ondersteuning voor de PowerShell Remoting Protocol (PSRP) via WSMan- en SSH.</span><span class="sxs-lookup"><span data-stu-id="e2670-160">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="e2670-161">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="e2670-161">For more information, see:</span></span>

- <span data-ttu-id="e2670-162">[SSH voor externe toegang in PowerShell Core] [ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="e2670-162">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="e2670-163">[WSMan Remoting in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="e2670-163">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->
[releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
