---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403980"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="73e86-103">PowerShell Core in macOS installeren</span><span class="sxs-lookup"><span data-stu-id="73e86-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="73e86-104">PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="73e86-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="73e86-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="73e86-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="73e86-106">Nadat het pakket is geïnstalleerd, voert u `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="73e86-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="73e86-107">Over Homebrew</span><span class="sxs-lookup"><span data-stu-id="73e86-107">About Brew</span></span>

<span data-ttu-id="73e86-108">[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="73e86-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="73e86-109">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="73e86-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="73e86-110">Installatie van de nieuwste stabiele versie via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="73e86-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="73e86-111">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="73e86-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="73e86-112">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="73e86-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="73e86-113">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="73e86-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="73e86-114">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="73e86-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="73e86-115">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en vernieuwen van de waarden in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="73e86-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="73e86-116">Installatie van de meest recente preview release via Homebrew in macOS 10.12 of hoger</span><span class="sxs-lookup"><span data-stu-id="73e86-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="73e86-117">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="73e86-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="73e86-118">Nadat u Homebrew hebt geïnstalleerd, kunt u PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="73e86-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="73e86-119">Installeer eerst de [Cask-versies] [ cask-versions] pakket waarmee u alternatieve versies van cask pakketten installeren:</span><span class="sxs-lookup"><span data-stu-id="73e86-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="73e86-120">Nu kunt u PowerShell hebt geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="73e86-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="73e86-121">Controleer ten slotte of het installeren van uw correct werkt:</span><span class="sxs-lookup"><span data-stu-id="73e86-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="73e86-122">Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:</span><span class="sxs-lookup"><span data-stu-id="73e86-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="73e86-123">De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.</span><span class="sxs-lookup"><span data-stu-id="73e86-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="73e86-124">en vernieuw de waarden in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="73e86-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="73e86-125">Installatie via directe downloaden</span><span class="sxs-lookup"><span data-stu-id="73e86-125">Installation via Direct Download</span></span>

<span data-ttu-id="73e86-126">Pak het pakket downloaden `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="73e86-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="73e86-127">uit de [releases][] pagina naar uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="73e86-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="73e86-128">U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="73e86-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="73e86-129">Installeer [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="73e86-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="73e86-130">OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="73e86-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="73e86-131">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="73e86-131">Binary Archives</span></span>

<span data-ttu-id="73e86-132">PowerShell binaire `tar.gz` archieven worden opgegeven voor het macOS-platform om in te schakelen geavanceerde implementatiescenario's.</span><span class="sxs-lookup"><span data-stu-id="73e86-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="73e86-133">Installeren van de binaire archieven in macOS</span><span class="sxs-lookup"><span data-stu-id="73e86-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="73e86-134">Installeer [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="73e86-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="73e86-135">OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="73e86-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="73e86-136">Installatie van afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="73e86-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="73e86-137">Opdrachtregelprogramma's van XCode installeren</span><span class="sxs-lookup"><span data-stu-id="73e86-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="73e86-138">OpenSSL installeren</span><span class="sxs-lookup"><span data-stu-id="73e86-138">Install OpenSSL</span></span>

<span data-ttu-id="73e86-139">OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="73e86-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="73e86-140">U kunt installeren via MacPorts of Homebrew.</span><span class="sxs-lookup"><span data-stu-id="73e86-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="73e86-141">OpenSSL via Homebrew installeren</span><span class="sxs-lookup"><span data-stu-id="73e86-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="73e86-142">Zie [over Brew](#about-brew) voor informatie over Homebrew.</span><span class="sxs-lookup"><span data-stu-id="73e86-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="73e86-143">Voer voor het installeren van OpenSSL `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="73e86-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="73e86-144">OpenSSL via MacPorts installeren</span><span class="sxs-lookup"><span data-stu-id="73e86-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="73e86-145">Installeer de [XCode vanaf de opdrachtregel-hulpprogramma's](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="73e86-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="73e86-146">MacPorts installeren.</span><span class="sxs-lookup"><span data-stu-id="73e86-146">Install MacPorts.</span></span>
   <span data-ttu-id="73e86-147">Als u instructies nodig hebt, raadpleegt u de [installatiehandleiding](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="73e86-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="73e86-148">MacPorts bijwerken door te voeren `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="73e86-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="73e86-149">Upgradepakketten voor besturings MacPorts door uit te voeren `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="73e86-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="73e86-150">OpenSSL installeren door te voeren `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="73e86-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="73e86-151">Koppel de bibliotheken om deze beschikbaar maken voor PowerShell:</span><span class="sxs-lookup"><span data-stu-id="73e86-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="73e86-152">PowerShell Core verwijderen</span><span class="sxs-lookup"><span data-stu-id="73e86-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="73e86-153">Als u PowerShell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht uit om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="73e86-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="73e86-154">Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="73e86-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="73e86-155">Als u wilt verwijderen van de extra PowerShell-paden, verwijzen naar de [paden](#paths) sectie in dit document en verwijder de paden met behulp van `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="73e86-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="73e86-156">Dit is niet nodig als u met Homebrew hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="73e86-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="73e86-157">Paden</span><span class="sxs-lookup"><span data-stu-id="73e86-157">Paths</span></span>

* <span data-ttu-id="73e86-158">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="73e86-158">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="73e86-159">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="73e86-159">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="73e86-160">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="73e86-160">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="73e86-161">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="73e86-161">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="73e86-162">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="73e86-162">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="73e86-163">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="73e86-163">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="73e86-164">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="73e86-164">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="73e86-165">De profielen met inachtneming van de PowerShell-per-host-configuratie.</span><span class="sxs-lookup"><span data-stu-id="73e86-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="73e86-166">Zodat het standaardprofiel voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="73e86-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="73e86-167">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="73e86-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="73e86-168">Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.</span><span class="sxs-lookup"><span data-stu-id="73e86-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="73e86-169">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="73e86-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="73e86-170">Aanvullende bronnen</span><span class="sxs-lookup"><span data-stu-id="73e86-170">Additional Resources</span></span>

* <span data-ttu-id="73e86-171">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="73e86-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="73e86-172">[Homebrew Github-opslagplaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="73e86-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="73e86-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="73e86-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
