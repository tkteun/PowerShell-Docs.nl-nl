# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="f54f1-101">PowerShell Core in Windows installeren</span><span class="sxs-lookup"><span data-stu-id="f54f1-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="f54f1-102">MSI</span><span class="sxs-lookup"><span data-stu-id="f54f1-102">MSI</span></span>

<span data-ttu-id="f54f1-103">PowerShell installeren op een Windows-client of Windows Server (werkt op Windows 7 SP1 Server 2008 R2 en hoger), het downloaden van het MSI-pakket van onze pagina met GitHub [releases] [].</span><span class="sxs-lookup"><span data-stu-id="f54f1-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="f54f1-104">Het MSI-bestand ziet er zo- `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="f54f1-104">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="f54f1-105">Zodra u hebt gedownload, dubbelklikt u op het installatieprogramma en volg de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="f54f1-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="f54f1-106">Er is een snelkoppeling geplaatst in het Menu Start na de installatie.</span><span class="sxs-lookup"><span data-stu-id="f54f1-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="f54f1-107">Het pakket wordt standaard geïnstalleerd op `$env:ProgramFiles\PowerShell\<version>`</span><span class="sxs-lookup"><span data-stu-id="f54f1-107">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="f54f1-108">U kunt PowerShell via het Menu Start starten of `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="f54f1-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f54f1-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f54f1-109">Prerequisites</span></span>

<span data-ttu-id="f54f1-110">Voor meer informatie over het inschakelen van PowerShell voor externe toegang via WSMan moeten de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="f54f1-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="f54f1-111">Installeer de [universeel C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies voor Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f54f1-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="f54f1-112">Het is beschikbaar via de directe download of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="f54f1-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="f54f1-113">Volledig hersteld (inclusief optionele pakketten), ondersteunde systemen beschikt al over deze software al geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f54f1-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="f54f1-114">Installeer de Windows Management Framework (WMF) 4.0 of hoger op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="f54f1-114">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="f54f1-115">POSTCODE</span><span class="sxs-lookup"><span data-stu-id="f54f1-115">ZIP</span></span>

<span data-ttu-id="f54f1-116">PowerShell binaire ZIP-archief zijn bedoeld om geavanceerde implementatiescenario's inschakelen.</span><span class="sxs-lookup"><span data-stu-id="f54f1-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="f54f1-117">Worden opgemerkt dat de controle van vereisten zoals in het MSI-pakket bij gebruik van het ZIP-archief krijgen Won't.</span><span class="sxs-lookup"><span data-stu-id="f54f1-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="f54f1-118">Dus voor externe toegang via WSMan goed werken op Windows-versies voor Windows 10, u moet controleren of de [vereisten](#prerequisites) wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="f54f1-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="f54f1-119">Op Windows IoT is geïmplementeerd</span><span class="sxs-lookup"><span data-stu-id="f54f1-119">Deploying on Windows IoT</span></span>

<span data-ttu-id="f54f1-120">Windows IoT is al wordt geleverd met Windows PowerShell die zullen worden gebruikt voor het implementeren van PowerShell Core 6.</span><span class="sxs-lookup"><span data-stu-id="f54f1-120">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="f54f1-121">Maak `PSSession` doelapparaat</span><span class="sxs-lookup"><span data-stu-id="f54f1-121">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="f54f1-122">Het ZIP-pakket kopiëren naar het apparaat</span><span class="sxs-lookup"><span data-stu-id="f54f1-122">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.0.2-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="f54f1-123">Verbinding met het apparaat en vouw het archief</span><span class="sxs-lookup"><span data-stu-id="f54f1-123">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   cd u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.0.2-win-arm32.zip
   ```

4. <span data-ttu-id="f54f1-124">Instellingen voor externe toegang tot en met PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="f54f1-124">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   cd .\PowerShell-6.0.2-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="f54f1-125">Verbinding maken met PowerShell Core 6-eindpunt op apparaat</span><span class="sxs-lookup"><span data-stu-id="f54f1-125">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.0.2
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="f54f1-126">Op Nano Server implementeren</span><span class="sxs-lookup"><span data-stu-id="f54f1-126">Deploying on Nano Server</span></span>

<span data-ttu-id="f54f1-127">Deze instructies wordt ervan uitgegaan dat een versie van PowerShell al wordt uitgevoerd op de installatiekopie van het Nano Server en dat deze is gegenereerd door de [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="f54f1-127">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="f54f1-128">Nano Server is een 'headless' besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="f54f1-128">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="f54f1-129">Kan de binaire bestanden Core kunt implementeren met behulp van twee verschillende methoden.</span><span class="sxs-lookup"><span data-stu-id="f54f1-129">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="f54f1-130">Offline - de Nano Server-VHD koppelen en pak de inhoud van het zip-bestand naar uw gekozen locatie binnen de gekoppelde installatiekopie.</span><span class="sxs-lookup"><span data-stu-id="f54f1-130">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="f54f1-131">Online - zet het zip-bestand via een PowerShell-sessie en pak deze in uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="f54f1-131">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="f54f1-132">In beide gevallen moet u de Windows 10 x64 ZIP-release van het pakket en moet de opdrachten binnen een exemplaar van 'Administrator' PowerShell uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f54f1-132">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="f54f1-133">Offline implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f54f1-133">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="f54f1-134">Uw favoriete zip-hulpprogramma gebruiken voor het uitpakken van het pakket naar een map in de gekoppelde installatiekopie van de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="f54f1-134">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="f54f1-135">Ontkoppelen van de installatiekopie en het opstarten.</span><span class="sxs-lookup"><span data-stu-id="f54f1-135">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="f54f1-136">Verbinding maken met het postvak in-exemplaar van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f54f1-136">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="f54f1-137">Volg de instructies voor het maken van een externe eindpunt met de ['een ander exemplaar techniek'](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="f54f1-137">Follow the instructions to create a remoting endpoint using the ["another instance technique"](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="f54f1-138">Online implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f54f1-138">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="f54f1-139">De volgende stappen helpen u bij de implementatie van PowerShell Core naar een actief exemplaar van de Nano Server en de configuratie van het externe eindpunt.</span><span class="sxs-lookup"><span data-stu-id="f54f1-139">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="f54f1-140">Verbinding met het postvak in-exemplaar van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f54f1-140">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="f54f1-141">Kopieer het bestand naar de Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="f54f1-141">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="f54f1-142">Voer de sessie</span><span class="sxs-lookup"><span data-stu-id="f54f1-142">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="f54f1-143">Pak het ZIP-bestand</span><span class="sxs-lookup"><span data-stu-id="f54f1-143">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="f54f1-144">Als u externe toegang op basis van WSMan wilt, volg de instructies voor het maken van een externe eindpunt met de ['een ander exemplaar techniek'](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="f54f1-144">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="f54f1-145">Instructies voor het maken van een eindpunt voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="f54f1-145">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="f54f1-146">PowerShell Core ondersteunt de PowerShell Remoting Protocol (PSRP) via WSMan- en SSH.</span><span class="sxs-lookup"><span data-stu-id="f54f1-146">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="f54f1-147">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="f54f1-147">For more information, see:</span></span>

- <span data-ttu-id="f54f1-148">[SSH Remoting in PowerShell Core] [de ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="f54f1-148">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="f54f1-149">[WSMan Remoting in PowerShell Core] [wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="f54f1-149">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="f54f1-150">Artefacten installatie-instructies</span><span class="sxs-lookup"><span data-stu-id="f54f1-150">Artifact Installation Instructions</span></span>

<span data-ttu-id="f54f1-151">We publiceren een archief met CoreCLR bits elke CI-versie met [AppVeyor] [].</span><span class="sxs-lookup"><span data-stu-id="f54f1-151">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="f54f1-152">PowerShell-kern van het artefact CoreCLR installeren:</span><span class="sxs-lookup"><span data-stu-id="f54f1-152">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="f54f1-153">Download ZIP-pakket van **artefacten** tabblad van de bepaalde build.</span><span class="sxs-lookup"><span data-stu-id="f54f1-153">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="f54f1-154">Opheffen van blokkeringen ZIP-bestand: klik met de rechtermuisknop in Verkenner -> Eigenschappen -> selectievakje blokkering vak -> toepassen</span><span class="sxs-lookup"><span data-stu-id="f54f1-154">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="f54f1-155">Pak het zipbestand naar `bin` directory</span><span class="sxs-lookup"><span data-stu-id="f54f1-155">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<span data-ttu-id="f54f1-156"><!-- [download-center]: TODO --> [releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]:... /Core-PowerShell/SSH-Remoting-in-PowerShell-Core.MD [wsman-remoting]:... /Core-PowerShell/WSMan-Remoting-in-PowerShell-Core.MD [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span><span class="sxs-lookup"><span data-stu-id="f54f1-156"><!-- [download-center]: TODO --> [releases]: https://github.com/PowerShell/PowerShell/releases [ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md [wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md [AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell</span></span>