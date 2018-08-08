---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587462"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="45d4a-103">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="45d4a-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="45d4a-104">PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="45d4a-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="45d4a-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="45d4a-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="45d4a-106">Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="45d4a-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="45d4a-107">Installatie via Homebrew in macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="45d4a-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="45d4a-108">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="45d4a-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="45d4a-109">Typ in een terminalvenster `brew` om uit te voeren van Homebrew.</span><span class="sxs-lookup"><span data-stu-id="45d4a-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="45d4a-110">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="45d4a-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="45d4a-111">Als u Homebrew in het verleden hebt geïnstalleerd, is het altijd een goed idee om uit te voeren "brew bijwerken naar de fabrieksinstellingen" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="45d4a-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="45d4a-112">Oudere versies van Homebrew gebruikt de tikt u op 'caskroom/cask', die is afgeschaft, en naar homebrew/cask gemigreerd.</span><span class="sxs-lookup"><span data-stu-id="45d4a-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="45d4a-113">Meer informatie kunt vinden op [Homebrew-cask][cask].</span><span class="sxs-lookup"><span data-stu-id="45d4a-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="45d4a-114">Gebruik de opdracht 'homebrew tikt u op' om uw huidige tap's weer te geven.</span><span class="sxs-lookup"><span data-stu-id="45d4a-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="45d4a-115">Als u ' caskroom/cask' ziet u 'update brew' kunt gebruiken om de tap's migreren Homebrew.</span><span class="sxs-lookup"><span data-stu-id="45d4a-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="45d4a-116">Nadat u geïnstalleerd / Homebrew bijgewerkt hebt, is het eenvoudig om PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="45d4a-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="45d4a-117">Voor het installeren van PowerShell:</span><span class="sxs-lookup"><span data-stu-id="45d4a-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="45d4a-118">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="45d4a-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="45d4a-119">Als u PowerShell sluiten en keer terug naar bash-, gebruikt u de opdracht 'exit'.</span><span class="sxs-lookup"><span data-stu-id="45d4a-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="45d4a-120">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="45d4a-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="45d4a-121">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="45d4a-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="45d4a-122">Preview-versie via Homebrew in macOS 10.12 + installeren</span><span class="sxs-lookup"><span data-stu-id="45d4a-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="45d4a-123">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="45d4a-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="45d4a-124">Typ in een terminalvenster `brew` om uit te voeren van Homebrew.</span><span class="sxs-lookup"><span data-stu-id="45d4a-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="45d4a-125">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="45d4a-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="45d4a-126">Als u Homebrew in het verleden hebt geïnstalleerd, is het altijd een goed idee om uit te voeren "brew bijwerken naar de fabrieksinstellingen" & & 'brew update'.</span><span class="sxs-lookup"><span data-stu-id="45d4a-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="45d4a-127">U moet vervolgens, tik op de `versions` fusten opslagplaats om op te halen van de preview-pakket:</span><span class="sxs-lookup"><span data-stu-id="45d4a-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="45d4a-128">Voor het installeren van PowerShell-voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="45d4a-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="45d4a-129">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="45d4a-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="45d4a-130">Wanneer er nieuwe versies van PowerShell worden uitgebracht, bijwerken van Homebrew-formules en bijwerken van de PowerShell-voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="45d4a-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="45d4a-131">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="45d4a-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="45d4a-132">Installatie via directe downloaden</span><span class="sxs-lookup"><span data-stu-id="45d4a-132">Installation via Direct Download</span></span>

<span data-ttu-id="45d4a-133">Pak het pakket downloaden `powershell-6.0.2-osx.10.12-x64.pkg` uit de [releases][] pagina naar uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="45d4a-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="45d4a-134">U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="45d4a-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="45d4a-135">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="45d4a-135">Binary Archives</span></span>

<span data-ttu-id="45d4a-136">PowerShell binaire `tar.gz` archieven voor macOS en Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="45d4a-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="45d4a-137">Installeren van de binaire archieven in macOS</span><span class="sxs-lookup"><span data-stu-id="45d4a-137">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="45d4a-138">PowerShell Core verwijderen</span><span class="sxs-lookup"><span data-stu-id="45d4a-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="45d4a-139">Als u PowerShell hebt geïnstalleerd met Homebrew, is verwijderen is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="45d4a-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="45d4a-140">Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="45d4a-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="45d4a-141">Als u wilt verwijderen van de extra PowerShell-paden, raadpleegt u de [paden][] sectie in dit document en verwijder de paden met behulp van de gewenste `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="45d4a-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="45d4a-142">Dit is niet nodig als u met Homebrew hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="45d4a-142">This is not necessary if you installed with Homebrew.</span></span>

[Paden]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="45d4a-144">Paden</span><span class="sxs-lookup"><span data-stu-id="45d4a-144">Paths</span></span>

* <span data-ttu-id="45d4a-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="45d4a-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="45d4a-146">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="45d4a-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="45d4a-147">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="45d4a-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="45d4a-148">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="45d4a-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="45d4a-149">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="45d4a-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="45d4a-150">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="45d4a-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="45d4a-151">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="45d4a-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="45d4a-152">De profielen met inachtneming van de PowerShell-per-host-configuratie.</span><span class="sxs-lookup"><span data-stu-id="45d4a-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="45d4a-153">Zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="45d4a-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="45d4a-154">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="45d4a-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="45d4a-155">Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="45d4a-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="45d4a-156">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="45d4a-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="45d4a-157">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="45d4a-157">Additional Resources</span></span>

* <span data-ttu-id="45d4a-158">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="45d4a-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="45d4a-159">[Homebrew Github-opslagplaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="45d4a-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="45d4a-160">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="45d4a-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
