---
title: PowerShell installeren in macOS
description: Informatie over het installeren van Power shell in macOS
ms.date: 09/23/2020
ms.openlocfilehash: d52595cb7a32a947675486564be2d0230045c709
ms.sourcegitcommit: 745ccd8f7cea8dc3471cccfaa20ec48bba1448c0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/24/2020
ms.locfileid: "91137231"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="383d9-103">PowerShell installeren in macOS</span><span class="sxs-lookup"><span data-stu-id="383d9-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="383d9-104">Power shell ondersteunt macOS 10,12 en hoger.</span><span class="sxs-lookup"><span data-stu-id="383d9-104">PowerShell supports macOS 10.12 and higher.</span></span> <span data-ttu-id="383d9-105">Power shell 7.0.3 of hoger en Power shell preview 7.1.0 of hoger vereisen macOS 10,13 en hoger.</span><span class="sxs-lookup"><span data-stu-id="383d9-105">PowerShell 7.0.3 or higher and PowerShell Preview 7.1.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="383d9-106">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="383d9-106">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="383d9-107">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="383d9-107">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="383d9-108">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="383d9-108">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="383d9-109">De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="383d9-109">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="383d9-110">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="383d9-110">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="383d9-111">Er zijn verschillende manieren om Power shell op macOS te installeren.</span><span class="sxs-lookup"><span data-stu-id="383d9-111">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="383d9-112">Kies één van de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="383d9-112">Choose one of the following methods:</span></span>

- <span data-ttu-id="383d9-113">Installeer met behulp van homebrew.</span><span class="sxs-lookup"><span data-stu-id="383d9-113">Install using Homebrew.</span></span> <span data-ttu-id="383d9-114">Homebrew is de voorkeurs pakket beheerder voor macOS.</span><span class="sxs-lookup"><span data-stu-id="383d9-114">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="383d9-115">Power Shell installeren via [direct downloaden](#installation-via-direct-download)</span><span class="sxs-lookup"><span data-stu-id="383d9-115">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="383d9-116">Installeren vanuit [binaire archieven](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="383d9-116">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="383d9-117">Nadat u Power shell hebt geïnstalleerd, moet u [openssl](#installing-dependencies)installeren.</span><span class="sxs-lookup"><span data-stu-id="383d9-117">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="383d9-118">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="383d9-118">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="383d9-119">Installatie van de laatste stabiele release via homebrew op macOS 10,13 of hoger</span><span class="sxs-lookup"><span data-stu-id="383d9-119">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="383d9-120">Als de `brew` opdracht niet wordt gevonden, moet u homebrew installeren volgens [de instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="383d9-120">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="383d9-121">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="383d9-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="383d9-122">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="383d9-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="383d9-123">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="383d9-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade --cask powershell
```

> [!NOTE]
> <span data-ttu-id="383d9-124">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien en de waarden die worden weer gegeven in te vernieuwen `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="383d9-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="383d9-125">Installatie van de nieuwste preview-versie via homebrew op macOS 10,13 of hoger</span><span class="sxs-lookup"><span data-stu-id="383d9-125">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="383d9-126">Nadat u homebrew hebt geïnstalleerd, kunt u Power Shell installeren.</span><span class="sxs-lookup"><span data-stu-id="383d9-126">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="383d9-127">Installeer eerst het pakket met [Cask versies][cask-versions] waarmee u alternatieve versies van Cask-pakketten kunt installeren:</span><span class="sxs-lookup"><span data-stu-id="383d9-127">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="383d9-128">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="383d9-128">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="383d9-129">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="383d9-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="383d9-130">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="383d9-130">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade --cask powershell-preview
```

> [!NOTE]
> <span data-ttu-id="383d9-131">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="383d9-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="383d9-132">en vernieuw de waarden die worden weer gegeven in `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="383d9-132">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="383d9-133">Het installeren van Power shell met de methode homebrew tap wordt ook ondersteund voor stabiele en LTS-versies.</span><span class="sxs-lookup"><span data-stu-id="383d9-133">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="383d9-134">U kunt nu uw installatie controleren</span><span class="sxs-lookup"><span data-stu-id="383d9-134">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="383d9-135">Wanneer er nieuwe versies van Power shell worden uitgebracht, voert u gewoon de volgende opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="383d9-135">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="383d9-136">Ongeacht of u de Cask of de methode tap gebruikt wanneer u een update uitvoert naar een nieuwere versie van Power shell, gebruikt u dezelfde methode die u hebt gebruikt om Power shell voor het eerst te installeren.</span><span class="sxs-lookup"><span data-stu-id="383d9-136">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="383d9-137">Als u een andere methode gebruikt, blijft het openen van een nieuwe pwsh-sessie de oudere versie van Power shell blijven gebruiken.</span><span class="sxs-lookup"><span data-stu-id="383d9-137">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="383d9-138">Als u besluit verschillende methoden te gebruiken, zijn er manieren om het probleem op te lossen met behulp van de [homebrew-koppelings methode](https://docs.brew.sh/Manpage#link-ln-options-formula).</span><span class="sxs-lookup"><span data-stu-id="383d9-138">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="383d9-139">Installatie via direct downloaden</span><span class="sxs-lookup"><span data-stu-id="383d9-139">Installation via Direct Download</span></span>

<span data-ttu-id="383d9-140">Down load het pakket Package `powershell-lts-7.0.3-osx-x64.pkg` van de pagina [releases][] op uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="383d9-140">Download the PKG package `powershell-lts-7.0.3-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="383d9-141">U kunt dubbel klikken op het bestand en de prompts volgen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="383d9-141">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.3-osx-x64.pkg -target /
```

<span data-ttu-id="383d9-142">Installeer [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="383d9-142">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="383d9-143">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="383d9-143">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="383d9-144">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="383d9-144">Install as a .NET Global tool</span></span>

<span data-ttu-id="383d9-145">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="383d9-145">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="383d9-146">Het hulp programma DotNet tool wordt toegevoegd `~/.dotnet/tools` aan de `PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="383d9-146">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="383d9-147">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `PATH` .</span><span class="sxs-lookup"><span data-stu-id="383d9-147">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="383d9-148">U moet Power shell kunnen starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="383d9-148">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="383d9-149">Installeer [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="383d9-149">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="383d9-150">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="383d9-150">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="383d9-151">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="383d9-151">Binary Archives</span></span>

<span data-ttu-id="383d9-152">Er zijn binaire Power shell- `tar.gz` archieven beschikbaar voor het macOS-platform om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="383d9-152">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="383d9-153">Wanneer u met deze methode installeert, moet u ook hand matig afhankelijkheden installeren.</span><span class="sxs-lookup"><span data-stu-id="383d9-153">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="383d9-154">Installeer [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="383d9-154">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="383d9-155">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="383d9-155">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="383d9-156">Binaire archieven installeren op macOS</span><span class="sxs-lookup"><span data-stu-id="383d9-156">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.3

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.3

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.3/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.3/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="383d9-157">Afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="383d9-157">Installing dependencies</span></span>

<span data-ttu-id="383d9-158">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="383d9-158">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="383d9-159">U kunt OpenSSL installeren via MacPorts, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="383d9-159">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="383d9-160">MacPorts en homebrew kunnen problemen ondervinden wanneer ze worden gebruikt voor samen werking op hetzelfde systeem.</span><span class="sxs-lookup"><span data-stu-id="383d9-160">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="383d9-161">Homebrew heeft echter geen pakket voor OpenSSL 1,0.</span><span class="sxs-lookup"><span data-stu-id="383d9-161">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="383d9-162">Zie de [Veelgestelde vragen over MacPorts](https://trac.macports.org/wiki/FAQ)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="383d9-162">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="383d9-163">Installeer de Xcode-opdracht regel Programma's.</span><span class="sxs-lookup"><span data-stu-id="383d9-163">Install the Xcode command-line tools.</span></span> <span data-ttu-id="383d9-164">De Xcode-hulpprogram ma's zijn vereist door MacPorts.</span><span class="sxs-lookup"><span data-stu-id="383d9-164">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="383d9-165">Installeer MacPorts.</span><span class="sxs-lookup"><span data-stu-id="383d9-165">Install MacPorts.</span></span> <span data-ttu-id="383d9-166">Raadpleeg de [installatie handleiding](https://www.macports.org/install.php)als u instructies nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="383d9-166">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="383d9-167">Werk MacPorts bij door uit te voeren `sudo port selfupdate` .</span><span class="sxs-lookup"><span data-stu-id="383d9-167">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="383d9-168">Upgrade MacPorts packages door uit te voeren `sudo port upgrade outdated` .</span><span class="sxs-lookup"><span data-stu-id="383d9-168">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="383d9-169">Installeer OpenSSL door uit te voeren `sudo port install openssl10` .</span><span class="sxs-lookup"><span data-stu-id="383d9-169">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="383d9-170">Koppel de bibliotheken om ze beschikbaar te maken voor Power shell:</span><span class="sxs-lookup"><span data-stu-id="383d9-170">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="383d9-171">Power shell verwijderen</span><span class="sxs-lookup"><span data-stu-id="383d9-171">Uninstalling PowerShell</span></span>

<span data-ttu-id="383d9-172">Als u Power shell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="383d9-172">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="383d9-173">Als u Power shell hebt geïnstalleerd via direct downloaden, moet Power shell hand matig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="383d9-173">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="383d9-174">Als u de extra Power shell-paden wilt verwijderen, raadpleegt u de sectie [paden](#paths) in dit document en verwijdert u de paden met `sudo rm` .</span><span class="sxs-lookup"><span data-stu-id="383d9-174">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="383d9-175">Dit is niet nodig als u hebt geïnstalleerd met homebrew.</span><span class="sxs-lookup"><span data-stu-id="383d9-175">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="383d9-176">Paden</span><span class="sxs-lookup"><span data-stu-id="383d9-176">Paths</span></span>

- <span data-ttu-id="383d9-177">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.3/`</span><span class="sxs-lookup"><span data-stu-id="383d9-177">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.3/`</span></span>
- <span data-ttu-id="383d9-178">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="383d9-178">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="383d9-179">Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="383d9-179">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="383d9-180">Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="383d9-180">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="383d9-181">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="383d9-181">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="383d9-182">Standaard modules worden gelezen van `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="383d9-182">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="383d9-183">De PSReadline-geschiedenis wordt vastgelegd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="383d9-183">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="383d9-184">De profielen respecteren de configuratie van de Power shell per host.</span><span class="sxs-lookup"><span data-stu-id="383d9-184">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="383d9-185">Het standaard-host-profiel bestaat dus op `Microsoft.PowerShell_profile.ps1` dezelfde locatie.</span><span class="sxs-lookup"><span data-stu-id="383d9-185">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="383d9-186">Power shell respecteert de [XDG-basis directory specificatie][xdg-bds] op macOS.</span><span class="sxs-lookup"><span data-stu-id="383d9-186">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="383d9-187">Omdat macOS een afleiding van BSD is, wordt het voor voegsel `/usr/local` gebruikt in plaats van `/opt` .</span><span class="sxs-lookup"><span data-stu-id="383d9-187">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="383d9-188">Dat `$PSHOME` wil zeggen `/usr/local/microsoft/powershell/7.0.3/` , en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="383d9-188">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.3/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="383d9-189">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="383d9-189">Installation support</span></span>

<span data-ttu-id="383d9-190">Micro soft ondersteunt de installatie methoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="383d9-190">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="383d9-191">Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="383d9-191">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="383d9-192">Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="383d9-192">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="383d9-193">Aanvullende resources</span><span class="sxs-lookup"><span data-stu-id="383d9-193">Additional Resources</span></span>

- <span data-ttu-id="383d9-194">[Homebrew-Web][brew]</span><span class="sxs-lookup"><span data-stu-id="383d9-194">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="383d9-195">[Homebrew github-opslag plaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="383d9-195">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="383d9-196">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="383d9-196">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[shell]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
