# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="4692e-101">PowerShell Core installeert op Mac OS</span><span class="sxs-lookup"><span data-stu-id="4692e-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="4692e-102">PowerShell Core biedt ondersteuning voor Mac OS 10.12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="4692e-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="4692e-103">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="4692e-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="4692e-104">Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.</span><span class="sxs-lookup"><span data-stu-id="4692e-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="4692e-105">Installatie via Homebrew op Mac OS 10,12</span><span class="sxs-lookup"><span data-stu-id="4692e-105">Installation via Homebrew on macOS 10.12</span></span>

<span data-ttu-id="4692e-106">[Homebrew] [ brew] is de voorkeur package manager voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="4692e-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="4692e-107">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew geïnstalleerd [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="4692e-107">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="4692e-108">Zodra u Homebrew hebt geïnstalleerd, is het eenvoudig om PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="4692e-108">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="4692e-109">Installeer eerst [Homebrew Cask][cask], zodat u kunt meer pakketten installeren:</span><span class="sxs-lookup"><span data-stu-id="4692e-109">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="4692e-110">U kunt nu PowerShell installeren:</span><span class="sxs-lookup"><span data-stu-id="4692e-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="4692e-111">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="4692e-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="4692e-112">Wanneer er nieuwe versies van PowerShell zijn uitgebracht, Homebrew van formules bijwerken en upgrade uitvoeren van PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4692e-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="4692e-113">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een host PowerShell (pwsh), maar de PowerShell-shell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.</span><span class="sxs-lookup"><span data-stu-id="4692e-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="4692e-114">en de waarden in $PSVersionTable vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="4692e-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a><span data-ttu-id="4692e-115">Installatie via directe Download</span><span class="sxs-lookup"><span data-stu-id="4692e-115">Installation via Direct Download</span></span>

<span data-ttu-id="4692e-116">Pak het pakket downloaden `powershell-6.0.2-osx.10.12-x64.pkg` van de [releases][] pagina op uw Mac OS-machine.</span><span class="sxs-lookup"><span data-stu-id="4692e-116">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="4692e-117">U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="4692e-117">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="4692e-118">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="4692e-118">Binary Archives</span></span>

<span data-ttu-id="4692e-119">PowerShell binair `tar.gz` archieven voor Mac OS- en Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="4692e-119">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="4692e-120">Installeren van de binaire archieven op Mac OS</span><span class="sxs-lookup"><span data-stu-id="4692e-120">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="4692e-121">PowerShell Core verwijderen</span><span class="sxs-lookup"><span data-stu-id="4692e-121">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="4692e-122">Als u met Homebrew PowerShell hebt geïnstalleerd, is het verwijderen is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="4692e-122">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="4692e-123">Als u via de directe download PowerShell hebt geïnstalleerd, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="4692e-123">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="4692e-124">Als u wilt de aanvullende PowerShell paden verwijderen, raadpleegt u de [paden][] sectie in dit document en verwijdert u de paden met behulp van de gewenste `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="4692e-124">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="4692e-125">Dit is niet nodig als u met Homebrew geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="4692e-125">This is not necessary if you installed with Homebrew.</span></span>

[paden]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="4692e-127">Paden</span><span class="sxs-lookup"><span data-stu-id="4692e-127">Paths</span></span>

* <span data-ttu-id="4692e-128">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="4692e-128">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="4692e-129">Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4692e-129">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="4692e-130">Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="4692e-130">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="4692e-131">Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4692e-131">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4692e-132">Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="4692e-132">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="4692e-133">Standaardmodules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="4692e-133">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="4692e-134">Geschiedenis van PSReadline wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="4692e-134">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="4692e-135">De profielen respecteren van PowerShell per host-configuratie.</span><span class="sxs-lookup"><span data-stu-id="4692e-135">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="4692e-136">Zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="4692e-136">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="4692e-137">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Mac OS.</span><span class="sxs-lookup"><span data-stu-id="4692e-137">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="4692e-138">Omdat Mac OS geen afwijking van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="4692e-138">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="4692e-139">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="4692e-139">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
