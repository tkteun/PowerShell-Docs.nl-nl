---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998500"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="60e48-103">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="60e48-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="60e48-104">PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="60e48-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="60e48-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="60e48-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="60e48-106">Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="60e48-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="60e48-107">Over Homebrew</span><span class="sxs-lookup"><span data-stu-id="60e48-107">About Brew</span></span>

<span data-ttu-id="60e48-108">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="60e48-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="60e48-109">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="60e48-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="60e48-110">Installatie van de nieuwste stabiele versie via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="60e48-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="60e48-111">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="60e48-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="60e48-112">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="60e48-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="60e48-113">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="60e48-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="60e48-114">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="60e48-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="60e48-115">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="60e48-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="60e48-116">Installatie van de meest recente preview release via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="60e48-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="60e48-117">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="60e48-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="60e48-118">Nadat u Homebrew hebt geïnstalleerd, is het eenvoudig om PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="60e48-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="60e48-119">Installeer eerst [Cask-versies] [ cask-versions] waarmee u alternatieve versies van cask pakketten installeren:</span><span class="sxs-lookup"><span data-stu-id="60e48-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="60e48-120">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="60e48-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="60e48-121">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="60e48-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="60e48-122">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="60e48-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="60e48-123">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.</span><span class="sxs-lookup"><span data-stu-id="60e48-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="60e48-124">en vernieuw de waarden in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="60e48-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="60e48-125">Installatie via directe downloaden</span><span class="sxs-lookup"><span data-stu-id="60e48-125">Installation via Direct Download</span></span>

<span data-ttu-id="60e48-126">Pak het pakket downloaden `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="60e48-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="60e48-127">uit de [releases][] pagina naar uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="60e48-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="60e48-128">U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="60e48-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="60e48-129">Installeer [OpenSSL](#install-openssl) als dit is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="60e48-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="60e48-130">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="60e48-130">Binary Archives</span></span>

<span data-ttu-id="60e48-131">PowerShell binaire `tar.gz` archieven worden opgegeven voor het macOS-platform om in te schakelen geavanceerde implementatiescenario's.</span><span class="sxs-lookup"><span data-stu-id="60e48-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="60e48-132">Installeren van de binaire archieven in macOS</span><span class="sxs-lookup"><span data-stu-id="60e48-132">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="60e48-133">Installeer [OpenSSL](#install-openssl) als dit is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="60e48-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="60e48-134">Installatie van afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="60e48-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="60e48-135">XCode vanaf de opdrachtregel-hulpprogramma's installeren</span><span class="sxs-lookup"><span data-stu-id="60e48-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="60e48-136">OpenSSL installeren</span><span class="sxs-lookup"><span data-stu-id="60e48-136">Install OpenSSL</span></span>

<span data-ttu-id="60e48-137">OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="60e48-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="60e48-138">U kunt installeren via MacPorts of Homebrew.</span><span class="sxs-lookup"><span data-stu-id="60e48-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="60e48-139">OpenSSL via Homebrew installeren</span><span class="sxs-lookup"><span data-stu-id="60e48-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="60e48-140">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="60e48-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="60e48-141">Voer `brew install openssl` OpenSSL installeren.</span><span class="sxs-lookup"><span data-stu-id="60e48-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="60e48-142">OpenSSL via MacPorts installeren</span><span class="sxs-lookup"><span data-stu-id="60e48-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="60e48-143">Installeren de [XCode vanaf de opdrachtregel-hulpprogramma's](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="60e48-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="60e48-144">MacPorts installeren.</span><span class="sxs-lookup"><span data-stu-id="60e48-144">Install MacPorts.</span></span>
   <span data-ttu-id="60e48-145">Zie de [installatiehandleiding](https://guide.macports.org/chunked/installing.macports.html) als u instructies nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="60e48-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="60e48-146">MacPorts bijwerken door te voeren `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="60e48-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="60e48-147">Upgradepakketten voor MacPorts door uit te voeren `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="60e48-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="60e48-148">OpenSSL installeren door te voeren door te voeren `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="60e48-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="60e48-149">De bibliotheken koppelen zodat PowerShell kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="60e48-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="60e48-150">PowerShell Core verwijderen</span><span class="sxs-lookup"><span data-stu-id="60e48-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="60e48-151">Als u PowerShell hebt geïnstalleerd met Homebrew, is verwijderen is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="60e48-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="60e48-152">Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="60e48-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="60e48-153">Als u wilt verwijderen van de extra PowerShell-paden, raadpleegt u de [paden](#paths) sectie in dit document en verwijder de paden met behulp van de gewenste `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="60e48-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="60e48-154">Dit is niet nodig als u met Homebrew hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="60e48-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="60e48-155">Paden</span><span class="sxs-lookup"><span data-stu-id="60e48-155">Paths</span></span>

* <span data-ttu-id="60e48-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="60e48-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="60e48-157">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="60e48-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="60e48-158">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="60e48-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="60e48-159">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="60e48-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="60e48-160">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="60e48-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="60e48-161">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="60e48-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="60e48-162">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="60e48-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="60e48-163">De profielen met inachtneming van de PowerShell-per-host-configuratie.</span><span class="sxs-lookup"><span data-stu-id="60e48-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="60e48-164">Zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="60e48-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="60e48-165">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="60e48-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="60e48-166">Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="60e48-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="60e48-167">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="60e48-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="60e48-168">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="60e48-168">Additional Resources</span></span>

* <span data-ttu-id="60e48-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="60e48-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="60e48-170">[Homebrew Github-opslagplaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="60e48-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="60e48-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="60e48-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
