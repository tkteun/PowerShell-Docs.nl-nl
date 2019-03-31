---
title: PowerShell Core in Windows installeren
description: Informatie over PowerShell Core in Windows installeren
ms.date: 08/06/2018
ms.openlocfilehash: 450a38a1ef2e2890059094774fcc3f2ad4fcda6e
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2019
ms.locfileid: "58748959"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="8a151-103">PowerShell Core in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="8a151-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="8a151-104">MSI</span><span class="sxs-lookup"><span data-stu-id="8a151-104">MSI</span></span>

<span data-ttu-id="8a151-105">PowerShell installeren op een Windows-client of Windows Server (werkt op Windows 7 SP1, Server 2008 R2 en hoger), het MSI-pakket downloaden in onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="8a151-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>  <span data-ttu-id="8a151-106">Schuif omlaag naar de **activa** sectie van de versie die u wilt installeren.</span><span class="sxs-lookup"><span data-stu-id="8a151-106">Scroll down to the **Assets** section of the Release you want to install.</span></span>  <span data-ttu-id="8a151-107">De sectie activa kan worden samengevouwen, dus misschien moet u klikt u op te geven.</span><span class="sxs-lookup"><span data-stu-id="8a151-107">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="8a151-108">Het MSI-bestand er als volgt uitzien: `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="8a151-108">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="8a151-109">Nadat u hebt gedownload, dubbelklikt u op het installatieprogramma en volg de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="8a151-109">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="8a151-110">Er is een snelkoppeling geplaatst in het Menu Start na de installatie.</span><span class="sxs-lookup"><span data-stu-id="8a151-110">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="8a151-111">Het pakket wordt standaard geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="8a151-111">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="8a151-112">U kunt PowerShell via het Menu Start starten of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="8a151-112">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8a151-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8a151-113">Prerequisites</span></span>

<span data-ttu-id="8a151-114">Om in te schakelen PowerShell voor externe toegang via WSMan, moeten de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="8a151-114">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="8a151-115">Installeer de [universeel C-Runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies voorafgaand aan Windows 10.</span><span class="sxs-lookup"><span data-stu-id="8a151-115">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="8a151-116">Het is beschikbaar via de directe download of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="8a151-116">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="8a151-117">Volledig hersteld (inclusief optionele pakketten), heeft ondersteunde systemen al dit geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="8a151-117">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="8a151-118">Installeer de Windows Management Framework (WMF) 4.0 of hoger op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="8a151-118">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="8a151-119">ZIP</span><span class="sxs-lookup"><span data-stu-id="8a151-119">ZIP</span></span>

<span data-ttu-id="8a151-120">PowerShell binaire ZIP-archieven zijn opgegeven voor het inschakelen van geavanceerde implementatiescenario's.</span><span class="sxs-lookup"><span data-stu-id="8a151-120">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="8a151-121">Worden opgemerkt bij het gebruik van het ZIP-archief, kunt u de controle van vereisten zoals in het MSI-pakket wordt niet ophalen.</span><span class="sxs-lookup"><span data-stu-id="8a151-121">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="8a151-122">In de volgorde voor externe toegang via WSMan goed werken op Windows-versies voorafgaand aan Windows 10, moet u om te controleren of de [vereisten](#prerequisites) wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="8a151-122">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="8a151-123">Implementeren op Windows IoT</span><span class="sxs-lookup"><span data-stu-id="8a151-123">Deploying on Windows IoT</span></span>

<span data-ttu-id="8a151-124">Windows IoT is al wordt geleverd met Windows PowerShell die zullen worden gebruikt voor het implementeren van PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="8a151-124">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="8a151-125">Maak `PSSession` doelapparaat</span><span class="sxs-lookup"><span data-stu-id="8a151-125">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="8a151-126">Kopieer het ZIP-pakket naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="8a151-126">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="8a151-127">Verbinding maken met het apparaat en vouw het archief</span><span class="sxs-lookup"><span data-stu-id="8a151-127">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="8a151-128">Instellingen voor externe toegang tot en met 6 voor PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8a151-128">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="8a151-129">Verbinding maken met PowerShell Core 6-eindpunt op apparaat</span><span class="sxs-lookup"><span data-stu-id="8a151-129">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="8a151-130">Implementatie van op Nano Server</span><span class="sxs-lookup"><span data-stu-id="8a151-130">Deploying on Nano Server</span></span>

<span data-ttu-id="8a151-131">Deze instructies wordt ervan uitgegaan dat een versie van PowerShell al wordt uitgevoerd op de Nano Server-installatiekopie en dat deze is gegenereerd door de [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="8a151-131">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="8a151-132">Nano Server is een 'headless' besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="8a151-132">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="8a151-133">Kan de belangrijke binaire kunt implementeren met behulp van twee verschillende methoden.</span><span class="sxs-lookup"><span data-stu-id="8a151-133">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="8a151-134">Offline - de Nano Server-VHD koppelen en pak deze uit de inhoud van het zip-bestand naar uw gekozen locatie binnen de gekoppelde installatiekopie.</span><span class="sxs-lookup"><span data-stu-id="8a151-134">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="8a151-135">Online - overdragen van het zip-bestand via een PowerShell-sessie en pak het uit in uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="8a151-135">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="8a151-136">In beide gevallen moet u de versie van Windows 10 x64 ZIP verpakt en moet de opdrachten binnen een exemplaar 'Beheerder' PowerShell uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="8a151-136">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="8a151-137">Offline implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8a151-137">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="8a151-138">Gebruik uw favoriete zip-hulpprogramma voor het uitpakken van het pakket naar een map in de gekoppelde Nano Server-installatiekopie.</span><span class="sxs-lookup"><span data-stu-id="8a151-138">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="8a151-139">Ontkoppelen van de installatiekopie en het opstarten.</span><span class="sxs-lookup"><span data-stu-id="8a151-139">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="8a151-140">Verbinding maken met het exemplaar van het postvak in van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a151-140">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="8a151-141">Volg de instructies voor het maken van een externe toegang-eindpunt met de ["een ander exemplaar techniek"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="8a151-141">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="8a151-142">Online implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8a151-142">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="8a151-143">De volgende stappen begeleiden u bij de implementatie van PowerShell Core een exemplaar van de Nano Server en de configuratie van het externe eindpunt.</span><span class="sxs-lookup"><span data-stu-id="8a151-143">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="8a151-144">Verbinding maken met het exemplaar van het postvak in van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8a151-144">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="8a151-145">Kopieer het bestand naar de Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="8a151-145">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="8a151-146">De sessie</span><span class="sxs-lookup"><span data-stu-id="8a151-146">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="8a151-147">Pak het ZIP-bestand</span><span class="sxs-lookup"><span data-stu-id="8a151-147">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="8a151-148">Als u externe toegang op basis van WSMan wilt, volg de instructies voor het maken van een externe toegang-eindpunt met de ["een ander exemplaar techniek"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="8a151-148">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="8a151-149">Instructies voor het maken van een eindpunt voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="8a151-149">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="8a151-150">PowerShell Core biedt ondersteuning voor de PowerShell Remoting Protocol (PSRP) via WSMan- en SSH.</span><span class="sxs-lookup"><span data-stu-id="8a151-150">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="8a151-151">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="8a151-151">For more information, see:</span></span>

- <span data-ttu-id="8a151-152">[SSH in PowerShell Core voor externe toegang][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="8a151-152">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="8a151-153">[Externe communicatie van WSMan in PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="8a151-153">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="8a151-154">Artefact installatie-instructies</span><span class="sxs-lookup"><span data-stu-id="8a151-154">Artifact Installation Instructions</span></span>

<span data-ttu-id="8a151-155">We een archief met CoreCLR bits op elke CI-build met publiceren [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="8a151-155">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="8a151-156">PowerShell Core installeren van het artefact CoreCLR:</span><span class="sxs-lookup"><span data-stu-id="8a151-156">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="8a151-157">Download ZIP-pakket van **artefacten** tabblad van de specifieke build.</span><span class="sxs-lookup"><span data-stu-id="8a151-157">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="8a151-158">Opheffen van blokkeringen ZIP-bestand: klik met de rechtermuisknop in Verkenner -> Eigenschappen selectievakje deblokkeren box -> toepassen -></span><span class="sxs-lookup"><span data-stu-id="8a151-158">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="8a151-159">Zip-bestand uitpakken `bin` directory</span><span class="sxs-lookup"><span data-stu-id="8a151-159">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
