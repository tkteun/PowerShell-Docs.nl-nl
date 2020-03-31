---
title: PowerShell installeren in macOS
description: Informatie over het installeren van Power shell in macOS
ms.date: 12/12/2018
ms.openlocfilehash: 3a5e71d0f69d0c39f9b7f3fa667863d7ec0a31dd
ms.sourcegitcommit: bf71c8c5e2a4fc7d5c3a67a537db1285089d03a7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80394999"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="b95ed-103">PowerShell installeren in macOS</span><span class="sxs-lookup"><span data-stu-id="b95ed-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="b95ed-104">Power shell ondersteunt macOS 10,12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="b95ed-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="b95ed-105">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="b95ed-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b95ed-106">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="b95ed-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="b95ed-107">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b95ed-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="b95ed-108">De map `/usr/local/microsoft/powershell/6` wordt vervangen door `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="b95ed-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="b95ed-109">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="b95ed-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="b95ed-110">Over Brew</span><span class="sxs-lookup"><span data-stu-id="b95ed-110">About Brew</span></span>

<span data-ttu-id="b95ed-111">[Homebrew][brew] is de voorkeurs pakket beheerder voor macOS.</span><span class="sxs-lookup"><span data-stu-id="b95ed-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="b95ed-112">Als de `brew` opdracht niet wordt gevonden, moet u homebrew installeren volgens [de instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="b95ed-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="b95ed-113">Anders kunt u Power Shell installeren via [direct downloaden](#installation-via-direct-download) of vanuit [binaire archieven](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="b95ed-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b95ed-114">Installatie van de laatste stabiele release via homebrew op macOS 10,12 of hoger</span><span class="sxs-lookup"><span data-stu-id="b95ed-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b95ed-115">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="b95ed-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b95ed-116">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="b95ed-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="b95ed-117">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="b95ed-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="b95ed-118">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="b95ed-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="b95ed-119">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien en de waarden te vernieuwen die worden weer gegeven in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="b95ed-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b95ed-120">Installatie van de nieuwste preview-versie via homebrew op macOS 10,12 of hoger</span><span class="sxs-lookup"><span data-stu-id="b95ed-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b95ed-121">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="b95ed-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b95ed-122">Nadat u homebrew hebt geïnstalleerd, kunt u Power Shell installeren.</span><span class="sxs-lookup"><span data-stu-id="b95ed-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="b95ed-123">Installeer eerst het pakket met [Cask versies][cask-versions] waarmee u alternatieve versies van Cask-pakketten kunt installeren:</span><span class="sxs-lookup"><span data-stu-id="b95ed-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="b95ed-124">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="b95ed-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="b95ed-125">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="b95ed-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="b95ed-126">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="b95ed-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="b95ed-127">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b95ed-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="b95ed-128">en de waarden vernieuwen die worden weer gegeven in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="b95ed-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="b95ed-129">Installatie via direct downloaden</span><span class="sxs-lookup"><span data-stu-id="b95ed-129">Installation via Direct Download</span></span>

<span data-ttu-id="b95ed-130">Down load het pakket package `powershell-lts-7.0.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="b95ed-130">Download the PKG package `powershell-lts-7.0.0-osx-x64.pkg`</span></span>
<span data-ttu-id="b95ed-131">van de pagina [releases][] op uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="b95ed-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="b95ed-132">U kunt dubbel klikken op het bestand en de prompts volgen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="b95ed-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.0-osx-x64.pkg -target /
```

<span data-ttu-id="b95ed-133">Installeer [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="b95ed-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="b95ed-134">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="b95ed-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="b95ed-135">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="b95ed-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="b95ed-136">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="b95ed-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="b95ed-137">Het installatie programma voor het DotNet-hulp programma voegt `~/.dotnet/tools` toe aan de omgevings variabele `PATH`.</span><span class="sxs-lookup"><span data-stu-id="b95ed-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="b95ed-138">De momenteel actieve shell beschikt echter niet over de bijgewerkte `PATH`.</span><span class="sxs-lookup"><span data-stu-id="b95ed-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="b95ed-139">U moet Power shell kunnen starten vanuit een nieuwe shell door `pwsh`te typen.</span><span class="sxs-lookup"><span data-stu-id="b95ed-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="b95ed-140">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="b95ed-140">Binary Archives</span></span>

<span data-ttu-id="b95ed-141">Er zijn binaire Power shell-`tar.gz` archieven beschikbaar voor het macOS-platform om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="b95ed-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="b95ed-142">Binaire archieven installeren op macOS</span><span class="sxs-lookup"><span data-stu-id="b95ed-142">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="b95ed-143">Installeer [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="b95ed-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="b95ed-144">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="b95ed-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="b95ed-145">Afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="b95ed-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="b95ed-146">Opdracht regel Programma's voor XCode installeren</span><span class="sxs-lookup"><span data-stu-id="b95ed-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="b95ed-147">OpenSSL installeren</span><span class="sxs-lookup"><span data-stu-id="b95ed-147">Install OpenSSL</span></span>

<span data-ttu-id="b95ed-148">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="b95ed-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="b95ed-149">U kunt installeren via MacPorts of Brew.</span><span class="sxs-lookup"><span data-stu-id="b95ed-149">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="b95ed-150">OpenSSL installeren via Brew</span><span class="sxs-lookup"><span data-stu-id="b95ed-150">Install OpenSSL via Brew</span></span>

<span data-ttu-id="b95ed-151">Zie [about Brew](#about-brew) voor informatie over Brew.</span><span class="sxs-lookup"><span data-stu-id="b95ed-151">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b95ed-152">Voer `brew install openssl`uit om OpenSSL te installeren.</span><span class="sxs-lookup"><span data-stu-id="b95ed-152">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="b95ed-153">OpenSSL installeren via MacPorts</span><span class="sxs-lookup"><span data-stu-id="b95ed-153">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="b95ed-154">Installeer de [Xcode-opdracht regel Programma's](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="b95ed-154">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="b95ed-155">Installeer MacPorts.</span><span class="sxs-lookup"><span data-stu-id="b95ed-155">Install MacPorts.</span></span>
   <span data-ttu-id="b95ed-156">Raadpleeg de [installatie handleiding](https://guide.macports.org/chunked/installing.macports.html)als u instructies nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="b95ed-156">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="b95ed-157">Werk MacPorts bij door `sudo port selfupdate`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b95ed-157">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="b95ed-158">Upgrade MacPorts-pakketten door `sudo port upgrade outdated`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b95ed-158">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="b95ed-159">Installeer OpenSSL door `sudo port install openssl`uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b95ed-159">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="b95ed-160">Koppel de bibliotheken om ze beschikbaar te maken voor Power shell:</span><span class="sxs-lookup"><span data-stu-id="b95ed-160">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="b95ed-161">Power shell verwijderen</span><span class="sxs-lookup"><span data-stu-id="b95ed-161">Uninstalling PowerShell</span></span>

<span data-ttu-id="b95ed-162">Als u Power shell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="b95ed-162">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="b95ed-163">Als u Power shell hebt geïnstalleerd via direct downloaden, moet Power shell hand matig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="b95ed-163">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="b95ed-164">Als u de extra Power shell-paden wilt verwijderen, raadpleegt u de sectie [paden](#paths) in dit document en verwijdert u de paden met behulp van `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="b95ed-164">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="b95ed-165">Dit is niet nodig als u hebt geïnstalleerd met homebrew.</span><span class="sxs-lookup"><span data-stu-id="b95ed-165">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="b95ed-166">Paden</span><span class="sxs-lookup"><span data-stu-id="b95ed-166">Paths</span></span>

* <span data-ttu-id="b95ed-167">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`</span><span class="sxs-lookup"><span data-stu-id="b95ed-167">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`</span></span>
* <span data-ttu-id="b95ed-168">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b95ed-168">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b95ed-169">Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b95ed-169">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b95ed-170">Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b95ed-170">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b95ed-171">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b95ed-171">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b95ed-172">Standaard modules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="b95ed-172">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b95ed-173">De PSReadline-geschiedenis wordt geregistreerd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b95ed-173">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b95ed-174">De profielen respecteren de configuratie van de Power shell per host.</span><span class="sxs-lookup"><span data-stu-id="b95ed-174">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="b95ed-175">Het standaard-host-profiel bestaat dus op `Microsoft.PowerShell_profile.ps1` op dezelfde locatie.</span><span class="sxs-lookup"><span data-stu-id="b95ed-175">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b95ed-176">Power shell respecteert de [XDG-basis directory specificatie][xdg-bds] op macOS.</span><span class="sxs-lookup"><span data-stu-id="b95ed-176">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="b95ed-177">Omdat macOS een afleiding van BSD is, wordt het voor voegsel `/usr/local` gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="b95ed-177">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="b95ed-178">`$PSHOME` is dus `/usr/local/microsoft/powershell/7.0.0/`en de symbolische koppeling wordt in `/usr/local/bin/pwsh`geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b95ed-178">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b95ed-179">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="b95ed-179">Additional Resources</span></span>

* <span data-ttu-id="b95ed-180">[Homebrew-Web][brew]</span><span class="sxs-lookup"><span data-stu-id="b95ed-180">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="b95ed-181">[Homebrew github-opslag plaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="b95ed-181">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="b95ed-182">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="b95ed-182">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
