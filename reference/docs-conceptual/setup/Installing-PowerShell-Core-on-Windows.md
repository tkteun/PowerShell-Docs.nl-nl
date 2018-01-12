# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="6295f-101">PowerShell Core installeren in Windows</span><span class="sxs-lookup"><span data-stu-id="6295f-101">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="6295f-102">MSI</span><span class="sxs-lookup"><span data-stu-id="6295f-102">MSI</span></span>

<span data-ttu-id="6295f-103">PowerShell installeren op een Windows-client of Windows Server (werkt op Windows 7 SP1 Server 2008 R2 en hoger), het downloaden van het MSI-pakket van onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="6295f-103">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="6295f-104">Het MSI-bestand ziet er zo-`PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="6295f-104">The MSI file looks like this - `PowerShell-6.0.0.<buildversion>.<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="6295f-105">Zodra u hebt gedownload, dubbelklikt u op het installatieprogramma en volg de aanwijzingen.</span><span class="sxs-lookup"><span data-stu-id="6295f-105">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="6295f-106">Er is een snelkoppeling geplaatst in het Menu Start na de installatie.</span><span class="sxs-lookup"><span data-stu-id="6295f-106">There is a shortcut placed in the Start Menu upon installation.</span></span>

* <span data-ttu-id="6295f-107">Het pakket wordt standaard geïnstalleerd op`$env:ProgramFiles\PowerShell\`</span><span class="sxs-lookup"><span data-stu-id="6295f-107">By default the package is installed to `$env:ProgramFiles\PowerShell\`</span></span>
* <span data-ttu-id="6295f-108">U kunt PowerShell via het Menu Start starten of`$env:ProgramFiles\PowerShell\pwsh.exe`</span><span class="sxs-lookup"><span data-stu-id="6295f-108">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="6295f-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6295f-109">Prerequisites</span></span>

<span data-ttu-id="6295f-110">Voor meer informatie over het inschakelen van PowerShell voor externe toegang via WSMan moeten de volgende vereisten worden voldaan:</span><span class="sxs-lookup"><span data-stu-id="6295f-110">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

* <span data-ttu-id="6295f-111">Installeer de [universeel C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) op Windows-versies voor Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6295f-111">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="6295f-112">Het is beschikbaar via de directe download of Windows Update.</span><span class="sxs-lookup"><span data-stu-id="6295f-112">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="6295f-113">Volledig hersteld (inclusief optionele pakketten), ondersteunde systemen beschikt al over deze software al geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="6295f-113">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
* <span data-ttu-id="6295f-114">Windows Management Framework (WMF) installeren [4.0](https://www.microsoft.com/download/details.aspx?id=40855) of hoger ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) in Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="6295f-114">Install the Windows Management Framework (WMF) [4.0](https://www.microsoft.com/download/details.aspx?id=40855) or newer ([5.1](https://www.microsoft.com/download/details.aspx?id=54616)) on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="6295f-115">POSTCODE</span><span class="sxs-lookup"><span data-stu-id="6295f-115">ZIP</span></span>

<span data-ttu-id="6295f-116">PowerShell binaire ZIP-archief zijn bedoeld om geavanceerde implementatiescenario's inschakelen.</span><span class="sxs-lookup"><span data-stu-id="6295f-116">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="6295f-117">Worden opgemerkt dat de controle van vereisten zoals in het MSI-pakket bij gebruik van het ZIP-archief krijgen Won't.</span><span class="sxs-lookup"><span data-stu-id="6295f-117">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="6295f-118">Dus voor externe toegang via WSMan goed werken op Windows-versies voor Windows 10, u moet controleren of de [vereisten](#prerequisites) wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="6295f-118">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="6295f-119">Op Nano Server implementeren</span><span class="sxs-lookup"><span data-stu-id="6295f-119">Deploying on Nano Server</span></span>

<span data-ttu-id="6295f-120">Deze instructies wordt ervan uitgegaan dat een versie van PowerShell al wordt uitgevoerd op de installatiekopie van het Nano Server en dat deze is gegenereerd door de [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span><span class="sxs-lookup"><span data-stu-id="6295f-120">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](https://technet.microsoft.com/windows-server-docs/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="6295f-121">Nano Server is een 'headless' besturingssysteem en de implementatie van de binaire bestanden PowerShell Core kan op twee verschillende manieren gebeuren:</span><span class="sxs-lookup"><span data-stu-id="6295f-121">Nano Server is a "headless" OS and deployment of PowerShell Core binaries can happen in two different ways:</span></span>

1. <span data-ttu-id="6295f-122">Offline - de Nano Server-VHD koppelen en pak de inhoud van het zip-bestand naar uw gekozen locatie binnen de gekoppelde installatiekopie.</span><span class="sxs-lookup"><span data-stu-id="6295f-122">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="6295f-123">Online - zet het zip-bestand via een PowerShell-sessie en pak deze in uw gekozen locatie.</span><span class="sxs-lookup"><span data-stu-id="6295f-123">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="6295f-124">In beide gevallen moet u de Windows 10 x64 Zip-release van het pakket en moet de opdrachten binnen een exemplaar van 'Administrator' PowerShell uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="6295f-124">In both cases, you will need the Windows 10 x64 Zip release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="6295f-125">Offline implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6295f-125">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="6295f-126">Uw favoriete zip-hulpprogramma gebruiken voor het uitpakken van het pakket naar een map in de gekoppelde installatiekopie van de Nano Server.</span><span class="sxs-lookup"><span data-stu-id="6295f-126">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="6295f-127">Ontkoppelen van de installatiekopie en het opstarten.</span><span class="sxs-lookup"><span data-stu-id="6295f-127">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="6295f-128">Verbinding maken met het postvak in-exemplaar van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6295f-128">Connect to the inbox instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="6295f-129">Volg de instructies voor het maken van een externe eindpunt met de [een ander exemplaar techniek](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="6295f-129">Follow the instructions to create a remoting endpoint using the [another instance technique](#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="6295f-130">Online implementatie van PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="6295f-130">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="6295f-131">De volgende stappen leidt u door de implementatie van PowerShell Core naar een actief exemplaar van de Nano Server en de configuratie van het externe eindpunt.</span><span class="sxs-lookup"><span data-stu-id="6295f-131">The following steps will guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

* <span data-ttu-id="6295f-132">Verbinding met het postvak in-exemplaar van Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6295f-132">Connect to the inbox instance of Windows PowerShell</span></span>

```powershell
$session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
```

* <span data-ttu-id="6295f-133">Kopieer het bestand naar de Nano Server-exemplaar</span><span class="sxs-lookup"><span data-stu-id="6295f-133">Copy the file to the Nano Server instance</span></span>

```powershell
Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
```

* <span data-ttu-id="6295f-134">Voer de sessie</span><span class="sxs-lookup"><span data-stu-id="6295f-134">Enter the session</span></span>

```powershell
Enter-PSSession $session
```

* <span data-ttu-id="6295f-135">Pak het Zip-bestand</span><span class="sxs-lookup"><span data-stu-id="6295f-135">Extract the Zip file</span></span>

```powershell
# Insert the appropriate version.
Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
```

* <span data-ttu-id="6295f-136">Als u externe toegang op basis van WSMan wilt, volg de instructies voor het maken van een externe eindpunt met de [een ander exemplaar techniek](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span><span class="sxs-lookup"><span data-stu-id="6295f-136">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the [another instance technique](../core-powershell/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="6295f-137">Instructies voor het maken van een eindpunt voor externe toegang</span><span class="sxs-lookup"><span data-stu-id="6295f-137">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="6295f-138">PowerShell Core ondersteunt de PowerShell Remoting Protocol (PSRP) via WSMan- en SSH.</span><span class="sxs-lookup"><span data-stu-id="6295f-138">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="6295f-139">Zie voor meer informatie</span><span class="sxs-lookup"><span data-stu-id="6295f-139">For more information, see:</span></span>

* <span data-ttu-id="6295f-140">[SSH Remoting in PowerShell-kern][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="6295f-140">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="6295f-141">[Externe communicatie van WSMan in PowerShell-kern][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="6295f-141">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="6295f-142">Artefacten installatie-instructies</span><span class="sxs-lookup"><span data-stu-id="6295f-142">Artifact Installation Instructions</span></span>

<span data-ttu-id="6295f-143">We een archief met CoreCLR bits elke CI-versie met publiceren [AppVeyor][].</span><span class="sxs-lookup"><span data-stu-id="6295f-143">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

## <a name="coreclr-artifacts"></a><span data-ttu-id="6295f-144">CoreCLR artefacten</span><span class="sxs-lookup"><span data-stu-id="6295f-144">CoreCLR Artifacts</span></span>

* <span data-ttu-id="6295f-145">Download zip-pakket van **artefacten** tabblad van de bepaalde build.</span><span class="sxs-lookup"><span data-stu-id="6295f-145">Download zip package from **artifacts** tab of the particular build.</span></span>
* <span data-ttu-id="6295f-146">Opheffen van blokkeringen zip-bestand: klik met de rechtermuisknop in Verkenner -> Eigenschappen -> selectievakje blokkering vak -> toepassen</span><span class="sxs-lookup"><span data-stu-id="6295f-146">Unblock zip file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
* <span data-ttu-id="6295f-147">Pak het zipbestand naar `bin` directory</span><span class="sxs-lookup"><span data-stu-id="6295f-147">Extract zip file to `bin` directory</span></span>
* `./bin/pwsh.exe`

<!-- [download-center]: TODO -->
[releases]: https://github.com/PowerShell/PowerShell/releases
[signing]: ../../tools/Sign-Package.ps1
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
