---
title: PowerShell Core in macOS installeren
description: Informatie over het installeren van Power shell core in macOS
ms.date: 12/12/2018
ms.openlocfilehash: ad1306e99261e8e6e2fd49d3199d863929c31e92
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444439"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="b664b-103">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="b664b-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="b664b-104">Power shell core ondersteunt macOS 10,12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="b664b-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="b664b-105">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="b664b-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b664b-106">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="b664b-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!TIP]
> <span data-ttu-id="b664b-107">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="b664b-107">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="about-brew"></a><span data-ttu-id="b664b-108">Over Brew</span><span class="sxs-lookup"><span data-stu-id="b664b-108">About Brew</span></span>

<span data-ttu-id="b664b-109">[Homebrew][brew] is de voorkeurs pakket beheerder voor macOS.</span><span class="sxs-lookup"><span data-stu-id="b664b-109">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="b664b-110">Als de `brew` opdracht niet wordt gevonden, moet u homebrew installeren volgens [de instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="b664b-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="b664b-111">Anders kunt u Power Shell installeren via [direct downloaden](#installation-via-direct-download) of vanuit [binaire archieven](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="b664b-111">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b664b-112">Installatie van de laatste stabiele release via homebrew op macOS 10,12 of hoger</span><span class="sxs-lookup"><span data-stu-id="b664b-112">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b664b-113">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="b664b-113">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b664b-114">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="b664b-114">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="b664b-115">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="b664b-115">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="b664b-116">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="b664b-116">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="b664b-117">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien en de waarden te vernieuwen die worden weer gegeven in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="b664b-117">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b664b-118">Installatie van de nieuwste preview-versie via homebrew op macOS 10,12 of hoger</span><span class="sxs-lookup"><span data-stu-id="b664b-118">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b664b-119">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="b664b-119">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b664b-120">Nadat u homebrew hebt geïnstalleerd, kunt u Power Shell installeren.</span><span class="sxs-lookup"><span data-stu-id="b664b-120">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="b664b-121">Installeer eerst het pakket met [Cask versies][cask-versions] waarmee u alternatieve versies van Cask-pakketten kunt installeren:</span><span class="sxs-lookup"><span data-stu-id="b664b-121">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="b664b-122">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="b664b-122">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="b664b-123">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="b664b-123">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="b664b-124">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="b664b-124">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="b664b-125">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b664b-125">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="b664b-126">en de waarden vernieuwen die worden weer gegeven in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="b664b-126">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="b664b-127">Installatie via direct downloaden</span><span class="sxs-lookup"><span data-stu-id="b664b-127">Installation via Direct Download</span></span>

<span data-ttu-id="b664b-128">Down load het pakket package `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="b664b-128">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="b664b-129">van de pagina [releases][] op uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="b664b-129">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="b664b-130">U kunt dubbel klikken op het bestand en de prompts volgen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="b664b-130">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="b664b-131">Installeer [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="b664b-131">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="b664b-132">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="b664b-132">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="b664b-133">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="b664b-133">Binary Archives</span></span>

<span data-ttu-id="b664b-134">Er zijn binaire Power shell-`tar.gz` archieven beschikbaar voor het macOS-platform om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="b664b-134">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="b664b-135">Binaire archieven installeren op macOS</span><span class="sxs-lookup"><span data-stu-id="b664b-135">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="b664b-136">Installeer [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="b664b-136">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="b664b-137">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="b664b-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="b664b-138">Afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="b664b-138">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="b664b-139">Opdracht regel Programma's voor XCode installeren</span><span class="sxs-lookup"><span data-stu-id="b664b-139">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="b664b-140">OpenSSL installeren</span><span class="sxs-lookup"><span data-stu-id="b664b-140">Install OpenSSL</span></span>

<span data-ttu-id="b664b-141">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="b664b-141">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="b664b-142">U kunt installeren via MacPorts of Brew.</span><span class="sxs-lookup"><span data-stu-id="b664b-142">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="b664b-143">OpenSSL installeren via Brew</span><span class="sxs-lookup"><span data-stu-id="b664b-143">Install OpenSSL via Brew</span></span>

<span data-ttu-id="b664b-144">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="b664b-144">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b664b-145">Voer `brew install openssl`uit om OpenSSL te installeren.</span><span class="sxs-lookup"><span data-stu-id="b664b-145">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="b664b-146">OpenSSL installeren via MacPorts</span><span class="sxs-lookup"><span data-stu-id="b664b-146">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="b664b-147">Installeer de [Xcode-opdracht regel Programma's](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="b664b-147">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="b664b-148">Installeer MacPorts.</span><span class="sxs-lookup"><span data-stu-id="b664b-148">Install MacPorts.</span></span>
   <span data-ttu-id="b664b-149">Raadpleeg de [installatie handleiding](https://guide.macports.org/chunked/installing.macports.html)als u instructies nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="b664b-149">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="b664b-150">Werk MacPorts bij door `sudo port selfupdate`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b664b-150">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="b664b-151">Upgrade MacPorts-pakketten door `sudo port upgrade outdated`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b664b-151">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="b664b-152">Installeer OpenSSL door `sudo port install openssl`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b664b-152">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="b664b-153">Koppel de bibliotheken om ze beschikbaar te maken voor Power shell:</span><span class="sxs-lookup"><span data-stu-id="b664b-153">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="b664b-154">Power shell core verwijderen</span><span class="sxs-lookup"><span data-stu-id="b664b-154">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="b664b-155">Als u Power shell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="b664b-155">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="b664b-156">Als u Power shell hebt geïnstalleerd via direct downloaden, moet Power shell hand matig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="b664b-156">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="b664b-157">Als u de extra Power shell-paden wilt verwijderen, raadpleegt u de sectie [paden](#paths) in dit document en verwijdert u de paden met behulp van `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="b664b-157">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="b664b-158">Dit is niet nodig als u hebt geïnstalleerd met homebrew.</span><span class="sxs-lookup"><span data-stu-id="b664b-158">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="b664b-159">Paden</span><span class="sxs-lookup"><span data-stu-id="b664b-159">Paths</span></span>

* <span data-ttu-id="b664b-160">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="b664b-160">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="b664b-161">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b664b-161">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b664b-162">Standaard profielen worden gelezen van `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b664b-162">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b664b-163">Gebruikers modules worden gelezen van `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b664b-163">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b664b-164">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b664b-164">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b664b-165">Standaard modules worden gelezen van `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="b664b-165">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b664b-166">De PSReadline-geschiedenis wordt geregistreerd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b664b-166">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b664b-167">De profielen respecteren de configuratie van de Power shell per host.</span><span class="sxs-lookup"><span data-stu-id="b664b-167">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="b664b-168">Het standaard-host-profiel bestaat dus op `Microsoft.PowerShell_profile.ps1` op dezelfde locatie.</span><span class="sxs-lookup"><span data-stu-id="b664b-168">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b664b-169">Power shell respecteert de [XDG-basis directory specificatie][xdg-bds] op macOS.</span><span class="sxs-lookup"><span data-stu-id="b664b-169">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="b664b-170">Omdat macOS een afleiding van BSD is, wordt het voor voegsel `/usr/local` gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="b664b-170">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="b664b-171">`$PSHOME` is dus `/usr/local/microsoft/powershell/6.2.0/`en de symbolische koppeling wordt in `/usr/local/bin/pwsh`geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b664b-171">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b664b-172">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="b664b-172">Additional Resources</span></span>

* <span data-ttu-id="b664b-173">[Homebrew-Web][brew]</span><span class="sxs-lookup"><span data-stu-id="b664b-173">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="b664b-174">[Homebrew github-opslag plaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="b664b-174">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="b664b-175">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="b664b-175">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
