---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 12/12/2018
ms.openlocfilehash: 70f5d64aa8a697a9011d07fbcb2bb821463827e1
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229732"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="f18c0-103">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="f18c0-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="f18c0-104">PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="f18c0-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="f18c0-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="f18c0-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="f18c0-106">Nadat het pakket is geïnstalleerd, voert u `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="f18c0-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="f18c0-107">Over Homebrew</span><span class="sxs-lookup"><span data-stu-id="f18c0-107">About Brew</span></span>

<span data-ttu-id="f18c0-108">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="f18c0-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="f18c0-109">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="f18c0-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="f18c0-110">Anders kunt u PowerShell via hebt geïnstalleerd [rechtstreeks downloaden](#installation-via-direct-download) of [binaire archieven](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="f18c0-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="f18c0-111">Installatie van de nieuwste stabiele versie via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="f18c0-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="f18c0-112">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="f18c0-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="f18c0-113">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="f18c0-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="f18c0-114">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="f18c0-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="f18c0-115">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="f18c0-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="f18c0-116">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en vernieuwen van de waarden in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="f18c0-117">Installatie van de meest recente preview release via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="f18c0-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="f18c0-118">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="f18c0-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="f18c0-119">Nadat u Homebrew hebt geïnstalleerd, kunt u PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="f18c0-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="f18c0-120">Installeer eerst de [Cask-versies] [ cask-versions] pakket waarmee u alternatieve versies van cask pakketten installeren:</span><span class="sxs-lookup"><span data-stu-id="f18c0-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="f18c0-121">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="f18c0-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="f18c0-122">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="f18c0-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="f18c0-123">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="f18c0-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="f18c0-124">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.</span><span class="sxs-lookup"><span data-stu-id="f18c0-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="f18c0-125">en vernieuw de waarden in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="f18c0-126">Installatie via directe downloaden</span><span class="sxs-lookup"><span data-stu-id="f18c0-126">Installation via Direct Download</span></span>

<span data-ttu-id="f18c0-127">Pak het pakket downloaden `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="f18c0-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="f18c0-128">uit de [releases][] pagina naar uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="f18c0-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="f18c0-129">U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="f18c0-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="f18c0-130">Installeer [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="f18c0-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="f18c0-131">OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="f18c0-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="f18c0-132">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="f18c0-132">Binary Archives</span></span>

<span data-ttu-id="f18c0-133">PowerShell binaire `tar.gz` archieven worden opgegeven voor het macOS-platform om in te schakelen geavanceerde implementatiescenario's.</span><span class="sxs-lookup"><span data-stu-id="f18c0-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="f18c0-134">Installeren van de binaire archieven in macOS</span><span class="sxs-lookup"><span data-stu-id="f18c0-134">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="f18c0-135">Installeer [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="f18c0-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="f18c0-136">OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="f18c0-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="f18c0-137">Installatie van afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="f18c0-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="f18c0-138">Opdrachtregelprogramma's van XCode installeren</span><span class="sxs-lookup"><span data-stu-id="f18c0-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="f18c0-139">OpenSSL installeren</span><span class="sxs-lookup"><span data-stu-id="f18c0-139">Install OpenSSL</span></span>

<span data-ttu-id="f18c0-140">OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="f18c0-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="f18c0-141">U kunt installeren via MacPorts of Homebrew.</span><span class="sxs-lookup"><span data-stu-id="f18c0-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="f18c0-142">OpenSSL via Homebrew installeren</span><span class="sxs-lookup"><span data-stu-id="f18c0-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="f18c0-143">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="f18c0-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="f18c0-144">Voer voor het installeren van OpenSSL `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="f18c0-145">OpenSSL via MacPorts installeren</span><span class="sxs-lookup"><span data-stu-id="f18c0-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="f18c0-146">Installeer de [XCode vanaf de opdrachtregel-hulpprogramma's](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="f18c0-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="f18c0-147">MacPorts installeren.</span><span class="sxs-lookup"><span data-stu-id="f18c0-147">Install MacPorts.</span></span>
   <span data-ttu-id="f18c0-148">Als u instructies nodig hebt, raadpleegt u de [installatiehandleiding](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="f18c0-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="f18c0-149">MacPorts bijwerken door te voeren `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="f18c0-150">Upgradepakketten voor besturings MacPorts door uit te voeren `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="f18c0-151">OpenSSL installeren door te voeren `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="f18c0-152">Koppel de bibliotheken om deze beschikbaar maken voor PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f18c0-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="f18c0-153">PowerShell Core verwijderen</span><span class="sxs-lookup"><span data-stu-id="f18c0-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="f18c0-154">Als u PowerShell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht uit om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="f18c0-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="f18c0-155">Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="f18c0-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="f18c0-156">Als u wilt verwijderen van de extra PowerShell-paden, verwijzen naar de [paden](#paths) sectie in dit document en verwijder de paden met behulp van `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="f18c0-157">Dit is niet nodig als u met Homebrew hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f18c0-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="f18c0-158">Paden</span><span class="sxs-lookup"><span data-stu-id="f18c0-158">Paths</span></span>

* <span data-ttu-id="f18c0-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="f18c0-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="f18c0-160">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="f18c0-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="f18c0-161">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="f18c0-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="f18c0-162">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="f18c0-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="f18c0-163">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="f18c0-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="f18c0-164">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="f18c0-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="f18c0-165">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="f18c0-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="f18c0-166">De profielen met inachtneming van de PowerShell-per-host-configuratie.</span><span class="sxs-lookup"><span data-stu-id="f18c0-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="f18c0-167">Zodat het standaardprofiel voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="f18c0-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="f18c0-168">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="f18c0-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="f18c0-169">Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="f18c0-170">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="f18c0-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f18c0-171">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="f18c0-171">Additional Resources</span></span>

* <span data-ttu-id="f18c0-172">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="f18c0-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="f18c0-173">[Homebrew Github-opslagplaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="f18c0-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="f18c0-174">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="f18c0-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
