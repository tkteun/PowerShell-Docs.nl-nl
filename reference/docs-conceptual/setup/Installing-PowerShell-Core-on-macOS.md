# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="97ffa-101">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="97ffa-101">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="97ffa-102">PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="97ffa-102">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="97ffa-103">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="97ffa-103">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="97ffa-104">Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="97ffa-104">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="97ffa-105">Installatie via Homebrew in macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="97ffa-105">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="97ffa-106">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="97ffa-106">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="97ffa-107">Typ in een terminalvenster `brew` om uit te voeren van Homebrew.</span><span class="sxs-lookup"><span data-stu-id="97ffa-107">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="97ffa-108">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="97ffa-108">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="97ffa-109">Als u Homebrew in het verleden hebt geïnstalleerd, is het altijd een goed idee om uit te voeren "brew bijwerken naar de fabrieksinstellingen" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="97ffa-109">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="97ffa-110">Oudere versies van Homebrew gebruikt de tikt u op 'caskroom/cask', die is afgeschaft, en naar homebrew/cask gemigreerd.</span><span class="sxs-lookup"><span data-stu-id="97ffa-110">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="97ffa-111">Meer informatie kunt vinden op [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="97ffa-111">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="97ffa-112">Gebruik de opdracht 'homebrew tikt u op' om uw huidige tap's weer te geven.</span><span class="sxs-lookup"><span data-stu-id="97ffa-112">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="97ffa-113">Als u ' caskroom/cask' ziet u 'update brew' kunt gebruiken om de tap's migreren Homebrew.</span><span class="sxs-lookup"><span data-stu-id="97ffa-113">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="97ffa-114">Nadat u geïnstalleerd / Homebrew bijgewerkt hebt, is het eenvoudig om PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="97ffa-114">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="97ffa-115">Voor het installeren van PowerShell:</span><span class="sxs-lookup"><span data-stu-id="97ffa-115">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="97ffa-116">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="97ffa-116">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="97ffa-117">Als u PowerShell sluiten en keer terug naar bash-, gebruikt u de opdracht 'exit'.</span><span class="sxs-lookup"><span data-stu-id="97ffa-117">To exit PowerShell, and return to bash, use the 'exit' command.</span></span> 
```sh
exit
```

<span data-ttu-id="97ffa-118">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="97ffa-118">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="97ffa-119">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="97ffa-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="97ffa-120">Preview-versie via Homebrew in macOS 10.12 + installeren</span><span class="sxs-lookup"><span data-stu-id="97ffa-120">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="97ffa-121">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="97ffa-121">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="97ffa-122">Typ in een terminalvenster `brew` om uit te voeren van Homebrew.</span><span class="sxs-lookup"><span data-stu-id="97ffa-122">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="97ffa-123">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="97ffa-123">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="97ffa-124">Als u Homebrew in het verleden hebt geïnstalleerd, is het altijd een goed idee om uit te voeren "brew bijwerken naar de fabrieksinstellingen" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="97ffa-124">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="97ffa-125">U moet vervolgens, tik op de `versions` fusten opslagplaats om op te halen van de preview-pakket:</span><span class="sxs-lookup"><span data-stu-id="97ffa-125">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="97ffa-126">Voor het installeren van PowerShell-voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="97ffa-126">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="97ffa-127">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="97ffa-127">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="97ffa-128">Wanneer er nieuwe versies van PowerShell worden uitgebracht, bijwerken van Homebrew-formules en bijwerken van de PowerShell-voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="97ffa-128">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="97ffa-129">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="97ffa-129">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="97ffa-130">Installatie via directe downloaden</span><span class="sxs-lookup"><span data-stu-id="97ffa-130">Installation via Direct Download</span></span>

<span data-ttu-id="97ffa-131">Pak het pakket downloaden `powershell-6.0.2-osx.10.12-x64.pkg` uit de [releases][] pagina naar uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="97ffa-131">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="97ffa-132">U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="97ffa-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="97ffa-133">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="97ffa-133">Binary Archives</span></span>

<span data-ttu-id="97ffa-134">PowerShell binaire `tar.gz` archieven voor macOS en Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="97ffa-134">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="97ffa-135">Installeren van de binaire archieven in macOS</span><span class="sxs-lookup"><span data-stu-id="97ffa-135">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="97ffa-136">PowerShell Core verwijderen</span><span class="sxs-lookup"><span data-stu-id="97ffa-136">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="97ffa-137">Als u PowerShell hebt geïnstalleerd met Homebrew, is verwijderen is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="97ffa-137">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="97ffa-138">Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="97ffa-138">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="97ffa-139">Als u wilt verwijderen van de extra PowerShell-paden, raadpleegt u de [paden][] sectie in dit document en verwijder de paden met behulp van de gewenste `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="97ffa-139">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="97ffa-140">Dit is niet nodig als u met Homebrew hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="97ffa-140">This is not necessary if you installed with Homebrew.</span></span>

[Paden]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="97ffa-142">Paden</span><span class="sxs-lookup"><span data-stu-id="97ffa-142">Paths</span></span>

* <span data-ttu-id="97ffa-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="97ffa-143">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="97ffa-144">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="97ffa-144">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="97ffa-145">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="97ffa-145">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="97ffa-146">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="97ffa-146">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="97ffa-147">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="97ffa-147">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="97ffa-148">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="97ffa-148">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="97ffa-149">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="97ffa-149">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="97ffa-150">De profielen met inachtneming van de PowerShell-per-host-configuratie.</span><span class="sxs-lookup"><span data-stu-id="97ffa-150">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="97ffa-151">Zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="97ffa-151">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="97ffa-152">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="97ffa-152">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="97ffa-153">Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="97ffa-153">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="97ffa-154">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="97ffa-154">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="97ffa-155">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="97ffa-155">Additional Resources</span></span>

* <span data-ttu-id="97ffa-156">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="97ffa-156">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="97ffa-157">[Homebrew Github-opslagplaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="97ffa-157">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="97ffa-158">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="97ffa-158">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
