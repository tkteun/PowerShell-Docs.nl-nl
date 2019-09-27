---
title: PowerShell Core in macOS installeren
description: Informatie over het installeren van Power shell core in macOS
ms.date: 12/12/2018
ms.openlocfilehash: a53cb5b7e159635dac45fb9ca3df28e86dffc653
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325267"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="ada13-103">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="ada13-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="ada13-104">Power shell core ondersteunt macOS 10,12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ada13-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="ada13-105">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="ada13-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="ada13-106">Nadat het pakket is geïnstalleerd, voert `pwsh` u uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="ada13-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="ada13-107">Over Brew</span><span class="sxs-lookup"><span data-stu-id="ada13-107">About Brew</span></span>

<span data-ttu-id="ada13-108">[Homebrew][brew] is de voorkeurs pakket beheerder voor macOS.</span><span class="sxs-lookup"><span data-stu-id="ada13-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="ada13-109">Als de `brew` opdracht niet wordt gevonden, moet u homebrew installeren volgens [de instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="ada13-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="ada13-110">Anders kunt u Power Shell installeren via [direct downloaden](#installation-via-direct-download) of vanuit [binaire archieven](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="ada13-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="ada13-111">Installatie van de laatste stabiele release via homebrew op macOS 10,12 of hoger</span><span class="sxs-lookup"><span data-stu-id="ada13-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="ada13-112">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="ada13-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="ada13-113">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="ada13-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="ada13-114">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="ada13-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="ada13-115">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="ada13-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="ada13-116">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien `$PSVersionTable`en de waarden die worden weer gegeven in te vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="ada13-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="ada13-117">Installatie van de nieuwste preview-versie via homebrew op macOS 10,12 of hoger</span><span class="sxs-lookup"><span data-stu-id="ada13-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="ada13-118">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="ada13-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="ada13-119">Nadat u homebrew hebt geïnstalleerd, kunt u Power Shell installeren.</span><span class="sxs-lookup"><span data-stu-id="ada13-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="ada13-120">Installeer eerst het pakket met [Cask versies][cask-versions] waarmee u alternatieve versies van Cask-pakketten kunt installeren:</span><span class="sxs-lookup"><span data-stu-id="ada13-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="ada13-121">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="ada13-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="ada13-122">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="ada13-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="ada13-123">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="ada13-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="ada13-124">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="ada13-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="ada13-125">en vernieuw de waarden die worden `$PSVersionTable`weer gegeven in.</span><span class="sxs-lookup"><span data-stu-id="ada13-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="ada13-126">Installatie via direct downloaden</span><span class="sxs-lookup"><span data-stu-id="ada13-126">Installation via Direct Download</span></span>

<span data-ttu-id="ada13-127">Pakket downloaden`powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="ada13-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="ada13-128">van de pagina [releases][] op uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="ada13-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="ada13-129">U kunt dubbel klikken op het bestand en de prompts volgen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="ada13-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="ada13-130">Installeer [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="ada13-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="ada13-131">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ada13-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="ada13-132">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="ada13-132">Binary Archives</span></span>

<span data-ttu-id="ada13-133">Er zijn `tar.gz` binaire Power shell-archieven beschikbaar voor het macOS-platform om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="ada13-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="ada13-134">Binaire archieven installeren op macOS</span><span class="sxs-lookup"><span data-stu-id="ada13-134">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="ada13-135">Installeer [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="ada13-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="ada13-136">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ada13-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="ada13-137">Afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="ada13-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="ada13-138">Opdracht regel Programma's voor XCode installeren</span><span class="sxs-lookup"><span data-stu-id="ada13-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="ada13-139">OpenSSL installeren</span><span class="sxs-lookup"><span data-stu-id="ada13-139">Install OpenSSL</span></span>

<span data-ttu-id="ada13-140">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="ada13-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="ada13-141">U kunt installeren via MacPorts of Brew.</span><span class="sxs-lookup"><span data-stu-id="ada13-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="ada13-142">OpenSSL installeren via Brew</span><span class="sxs-lookup"><span data-stu-id="ada13-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="ada13-143">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="ada13-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="ada13-144">Voer uit `brew install openssl`om openssl te installeren.</span><span class="sxs-lookup"><span data-stu-id="ada13-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="ada13-145">OpenSSL installeren via MacPorts</span><span class="sxs-lookup"><span data-stu-id="ada13-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="ada13-146">Installeer de [Xcode-opdracht regel Programma's](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="ada13-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="ada13-147">Installeer MacPorts.</span><span class="sxs-lookup"><span data-stu-id="ada13-147">Install MacPorts.</span></span>
   <span data-ttu-id="ada13-148">Raadpleeg de [installatie handleiding](https://guide.macports.org/chunked/installing.macports.html)als u instructies nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="ada13-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="ada13-149">Werk MacPorts bij door `sudo port selfupdate`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ada13-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="ada13-150">Upgrade MacPorts packages door `sudo port upgrade outdated`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ada13-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="ada13-151">Installeer OpenSSL door uit `sudo port install openssl`te voeren.</span><span class="sxs-lookup"><span data-stu-id="ada13-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="ada13-152">Koppel de bibliotheken om ze beschikbaar te maken voor Power shell:</span><span class="sxs-lookup"><span data-stu-id="ada13-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="ada13-153">Power shell core verwijderen</span><span class="sxs-lookup"><span data-stu-id="ada13-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="ada13-154">Als u Power shell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="ada13-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="ada13-155">Als u Power shell hebt geïnstalleerd via direct downloaden, moet Power shell hand matig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="ada13-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="ada13-156">Als u de extra Power shell-paden wilt verwijderen, raadpleegt u de sectie [paden](#paths) in dit document `sudo rm`en verwijdert u de paden met.</span><span class="sxs-lookup"><span data-stu-id="ada13-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="ada13-157">Dit is niet nodig als u hebt geïnstalleerd met homebrew.</span><span class="sxs-lookup"><span data-stu-id="ada13-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="ada13-158">Paden</span><span class="sxs-lookup"><span data-stu-id="ada13-158">Paths</span></span>

* <span data-ttu-id="ada13-159">`$PSHOME`ontbreekt`/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="ada13-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="ada13-160">Gebruikers profielen worden gelezen van`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ada13-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="ada13-161">Standaard profielen worden gelezen uit`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ada13-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="ada13-162">Gebruikers modules worden gelezen uit`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ada13-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ada13-163">Gedeelde modules worden gelezen van`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ada13-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ada13-164">Standaard modules worden gelezen van`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="ada13-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="ada13-165">De PSReadline-geschiedenis wordt vastgelegd in`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="ada13-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ada13-166">De profielen respecteren de configuratie van de Power shell per host.</span><span class="sxs-lookup"><span data-stu-id="ada13-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="ada13-167">Het standaard-host-profiel bestaat dus op `Microsoft.PowerShell_profile.ps1` dezelfde locatie.</span><span class="sxs-lookup"><span data-stu-id="ada13-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ada13-168">Power shell respecteert de [XDG-basis directory specificatie][xdg-bds] op macOS.</span><span class="sxs-lookup"><span data-stu-id="ada13-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="ada13-169">Omdat macOS een afleiding van BSD is, wordt `/usr/local` het voor voegsel gebruikt `/opt`in plaats van.</span><span class="sxs-lookup"><span data-stu-id="ada13-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="ada13-170">Dat wil zeggen `/usr/local/microsoft/powershell/6.2.0/`, en de symbolische koppeling wordt geplaatst `/usr/local/bin/pwsh`op. `$PSHOME`</span><span class="sxs-lookup"><span data-stu-id="ada13-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ada13-171">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="ada13-171">Additional Resources</span></span>

* <span data-ttu-id="ada13-172">[Homebrew-Web][brew]</span><span class="sxs-lookup"><span data-stu-id="ada13-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="ada13-173">[Homebrew github-opslag plaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="ada13-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="ada13-174">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="ada13-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
