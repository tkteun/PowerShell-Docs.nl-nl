---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 08/06/2018
ms.openlocfilehash: e226cd64f8788ae74dc72fdc0cd219923b7a2cd6
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002356"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="2d5d0-103">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="2d5d0-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="2d5d0-104">PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="2d5d0-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="2d5d0-106">Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="2d5d0-107">Installatie van de nieuwste stabiele versie via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="2d5d0-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="2d5d0-108">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="2d5d0-109">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="2d5d0-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="2d5d0-110">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="2d5d0-111">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="2d5d0-112">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="2d5d0-113">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="2d5d0-114">Installatie van de meest recente preview release via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="2d5d0-114">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="2d5d0-115">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-115">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="2d5d0-116">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="2d5d0-116">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="2d5d0-117">Nadat u Homebrew hebt geïnstalleerd, is het eenvoudig om PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-117">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="2d5d0-118">Installeer eerst [Cask-versies] [ cask-versions] waarmee u alternatieve versies van cask pakketten installeren:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-118">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="2d5d0-119">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-119">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="2d5d0-120">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-120">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="2d5d0-121">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-121">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="2d5d0-122">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-122">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="2d5d0-123">en vernieuw de waarden in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-123">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="2d5d0-124">Installatie via directe downloaden</span><span class="sxs-lookup"><span data-stu-id="2d5d0-124">Installation via Direct Download</span></span>

<span data-ttu-id="2d5d0-125">Pak het pakket downloaden `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-125">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="2d5d0-126">uit de [releases][] pagina naar uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-126">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="2d5d0-127">U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-127">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="2d5d0-128">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="2d5d0-128">Binary Archives</span></span>

<span data-ttu-id="2d5d0-129">PowerShell binaire `tar.gz` archieven worden opgegeven voor het macOS-platform om in te schakelen geavanceerde implementatiescenario's.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-129">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="2d5d0-130">Installeren van de binaire archieven in macOS</span><span class="sxs-lookup"><span data-stu-id="2d5d0-130">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="2d5d0-131">PowerShell Core verwijderen</span><span class="sxs-lookup"><span data-stu-id="2d5d0-131">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="2d5d0-132">Als u PowerShell hebt geïnstalleerd met Homebrew, is verwijderen is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-132">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="2d5d0-133">Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="2d5d0-133">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="2d5d0-134">Als u wilt verwijderen van de extra PowerShell-paden, raadpleegt u de [paden](#paths) sectie in dit document en verwijder de paden met behulp van de gewenste `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-134">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="2d5d0-135">Dit is niet nodig als u met Homebrew hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-135">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="2d5d0-136">Paden</span><span class="sxs-lookup"><span data-stu-id="2d5d0-136">Paths</span></span>

* <span data-ttu-id="2d5d0-137">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-137">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="2d5d0-138">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-138">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="2d5d0-139">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-139">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="2d5d0-140">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-140">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2d5d0-141">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-141">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2d5d0-142">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-142">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="2d5d0-143">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="2d5d0-143">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="2d5d0-144">De profielen met inachtneming van de PowerShell-per-host-configuratie.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-144">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="2d5d0-145">Zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-145">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="2d5d0-146">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-146">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="2d5d0-147">Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-147">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="2d5d0-148">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="2d5d0-148">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2d5d0-149">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="2d5d0-149">Additional Resources</span></span>

* <span data-ttu-id="2d5d0-150">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="2d5d0-150">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="2d5d0-151">[Homebrew Github-opslagplaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="2d5d0-151">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="2d5d0-152">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="2d5d0-152">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
