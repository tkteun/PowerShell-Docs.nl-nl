---
title: PowerShell installeren in macOS
description: Informatie over het installeren van Power shell in macOS
ms.date: 11/11/2020
ms.openlocfilehash: c64edd202de90cb4e7a335376c60a0bba0633baa
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524371"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="c638e-103">PowerShell installeren in macOS</span><span class="sxs-lookup"><span data-stu-id="c638e-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="c638e-104">Voor Power shell 7,0 of hoger is macOS 10,13 en hoger vereist.</span><span class="sxs-lookup"><span data-stu-id="c638e-104">PowerShell 7.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="c638e-105">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="c638e-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="c638e-106">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="c638e-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="c638e-107">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c638e-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="c638e-108">De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="c638e-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="c638e-109">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="c638e-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="c638e-110">Er zijn verschillende manieren om Power shell op macOS te installeren.</span><span class="sxs-lookup"><span data-stu-id="c638e-110">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="c638e-111">Kies één van de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="c638e-111">Choose one of the following methods:</span></span>

- <span data-ttu-id="c638e-112">Installeer met behulp van homebrew.</span><span class="sxs-lookup"><span data-stu-id="c638e-112">Install using Homebrew.</span></span> <span data-ttu-id="c638e-113">Homebrew is de voorkeurs pakket beheerder voor macOS.</span><span class="sxs-lookup"><span data-stu-id="c638e-113">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="c638e-114">Power Shell installeren via [direct downloaden](#installation-via-direct-download)</span><span class="sxs-lookup"><span data-stu-id="c638e-114">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="c638e-115">Installeren vanuit [binaire archieven](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="c638e-115">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="c638e-116">Nadat u Power shell hebt geïnstalleerd, moet u [openssl](#installing-dependencies)installeren.</span><span class="sxs-lookup"><span data-stu-id="c638e-116">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c638e-117">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c638e-117">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="c638e-118">Installatie van de laatste stabiele release via homebrew op macOS 10,13 of hoger</span><span class="sxs-lookup"><span data-stu-id="c638e-118">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="c638e-119">Als de `brew` opdracht niet wordt gevonden, moet u homebrew installeren volgens [de instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="c638e-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="c638e-120">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="c638e-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="c638e-121">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="c638e-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="c638e-122">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="c638e-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> <span data-ttu-id="c638e-123">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien en de waarden die worden weer gegeven in te vernieuwen `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="c638e-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="c638e-124">Installatie van de nieuwste preview-versie via homebrew op macOS 10,13 of hoger</span><span class="sxs-lookup"><span data-stu-id="c638e-124">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="c638e-125">Nadat u homebrew hebt geïnstalleerd, kunt u Power Shell installeren.</span><span class="sxs-lookup"><span data-stu-id="c638e-125">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="c638e-126">Installeer eerst het pakket met [Cask versies][cask-versions] waarmee u alternatieve versies van Cask-pakketten kunt installeren:</span><span class="sxs-lookup"><span data-stu-id="c638e-126">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="c638e-127">U kunt nu Power Shell installeren:</span><span class="sxs-lookup"><span data-stu-id="c638e-127">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="c638e-128">Controleer ten slotte of uw installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="c638e-128">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="c638e-129">Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:</span><span class="sxs-lookup"><span data-stu-id="c638e-129">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> <span data-ttu-id="c638e-130">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="c638e-130">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="c638e-131">en vernieuw de waarden die worden weer gegeven in `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="c638e-131">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="c638e-132">Het installeren van Power shell met de methode homebrew tap wordt ook ondersteund voor stabiele en LTS-versies.</span><span class="sxs-lookup"><span data-stu-id="c638e-132">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="c638e-133">U kunt nu uw installatie controleren</span><span class="sxs-lookup"><span data-stu-id="c638e-133">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="c638e-134">Wanneer er nieuwe versies van Power shell worden uitgebracht, voert u gewoon de volgende opdracht uit.</span><span class="sxs-lookup"><span data-stu-id="c638e-134">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="c638e-135">Ongeacht of u de Cask of de methode tap gebruikt wanneer u een update uitvoert naar een nieuwere versie van Power shell, gebruikt u dezelfde methode die u hebt gebruikt om Power shell voor het eerst te installeren.</span><span class="sxs-lookup"><span data-stu-id="c638e-135">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="c638e-136">Als u een andere methode gebruikt, blijft het openen van een nieuwe pwsh-sessie de oudere versie van Power shell blijven gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c638e-136">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="c638e-137">Als u besluit verschillende methoden te gebruiken, zijn er manieren om het probleem op te lossen met behulp van de [homebrew-koppelings methode](https://docs.brew.sh/Manpage#link-ln-options-formula).</span><span class="sxs-lookup"><span data-stu-id="c638e-137">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="c638e-138">Installatie via direct downloaden</span><span class="sxs-lookup"><span data-stu-id="c638e-138">Installation via Direct Download</span></span>

<span data-ttu-id="c638e-139">Down load het pakket Package `powershell-lts-7.1.0-osx-x64.pkg` van de pagina [releases][] op uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="c638e-139">Download the PKG package `powershell-lts-7.1.0-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="c638e-140">U kunt dubbel klikken op het bestand en de prompts volgen of installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="c638e-140">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="c638e-141">Installeer [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="c638e-141">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c638e-142">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c638e-142">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="c638e-143">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="c638e-143">Install as a .NET Global tool</span></span>

<span data-ttu-id="c638e-144">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="c638e-144">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="c638e-145">Het hulp programma DotNet tool wordt toegevoegd `~/.dotnet/tools` aan de `PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="c638e-145">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="c638e-146">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `PATH` .</span><span class="sxs-lookup"><span data-stu-id="c638e-146">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="c638e-147">U moet Power shell kunnen starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="c638e-147">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="c638e-148">Installeer [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="c638e-148">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c638e-149">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c638e-149">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="c638e-150">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="c638e-150">Binary Archives</span></span>

<span data-ttu-id="c638e-151">Er zijn binaire Power shell- `tar.gz` archieven beschikbaar voor het macOS-platform om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="c638e-151">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="c638e-152">Wanneer u met deze methode installeert, moet u ook hand matig afhankelijkheden installeren.</span><span class="sxs-lookup"><span data-stu-id="c638e-152">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="c638e-153">Installeer [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="c638e-153">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c638e-154">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c638e-154">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="c638e-155">Binaire archieven installeren op macOS</span><span class="sxs-lookup"><span data-stu-id="c638e-155">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="c638e-156">Afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="c638e-156">Installing dependencies</span></span>

<span data-ttu-id="c638e-157">OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="c638e-157">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="c638e-158">U kunt OpenSSL installeren via MacPorts, indien nodig.</span><span class="sxs-lookup"><span data-stu-id="c638e-158">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="c638e-159">MacPorts en homebrew kunnen problemen ondervinden wanneer ze worden gebruikt voor samen werking op hetzelfde systeem.</span><span class="sxs-lookup"><span data-stu-id="c638e-159">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="c638e-160">Homebrew heeft echter geen pakket voor OpenSSL 1,0.</span><span class="sxs-lookup"><span data-stu-id="c638e-160">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="c638e-161">Zie de [Veelgestelde vragen over MacPorts](https://trac.macports.org/wiki/FAQ)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c638e-161">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="c638e-162">Installeer de Xcode-opdracht regel Programma's.</span><span class="sxs-lookup"><span data-stu-id="c638e-162">Install the Xcode command-line tools.</span></span> <span data-ttu-id="c638e-163">De Xcode-hulpprogram ma's zijn vereist door MacPorts.</span><span class="sxs-lookup"><span data-stu-id="c638e-163">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="c638e-164">Installeer MacPorts.</span><span class="sxs-lookup"><span data-stu-id="c638e-164">Install MacPorts.</span></span> <span data-ttu-id="c638e-165">Raadpleeg de [installatie handleiding](https://www.macports.org/install.php)als u instructies nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="c638e-165">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="c638e-166">Werk MacPorts bij door uit te voeren `sudo port selfupdate` .</span><span class="sxs-lookup"><span data-stu-id="c638e-166">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="c638e-167">Upgrade MacPorts packages door uit te voeren `sudo port upgrade outdated` .</span><span class="sxs-lookup"><span data-stu-id="c638e-167">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="c638e-168">Installeer OpenSSL door uit te voeren `sudo port install openssl10` .</span><span class="sxs-lookup"><span data-stu-id="c638e-168">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="c638e-169">Koppel de bibliotheken om ze beschikbaar te maken voor Power shell:</span><span class="sxs-lookup"><span data-stu-id="c638e-169">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="c638e-170">Power shell verwijderen</span><span class="sxs-lookup"><span data-stu-id="c638e-170">Uninstalling PowerShell</span></span>

<span data-ttu-id="c638e-171">Als u Power shell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="c638e-171">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="c638e-172">Als u Power shell hebt geïnstalleerd via direct downloaden, moet Power shell hand matig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="c638e-172">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="c638e-173">Als u de extra Power shell-paden wilt verwijderen, raadpleegt u de sectie [paden](#paths) in dit document en verwijdert u de paden met `sudo rm` .</span><span class="sxs-lookup"><span data-stu-id="c638e-173">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="c638e-174">Dit is niet nodig als u hebt geïnstalleerd met homebrew.</span><span class="sxs-lookup"><span data-stu-id="c638e-174">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="c638e-175">Paden</span><span class="sxs-lookup"><span data-stu-id="c638e-175">Paths</span></span>

- <span data-ttu-id="c638e-176">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.0/`</span><span class="sxs-lookup"><span data-stu-id="c638e-176">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.0/`</span></span>
- <span data-ttu-id="c638e-177">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c638e-177">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="c638e-178">Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c638e-178">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="c638e-179">Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c638e-179">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="c638e-180">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c638e-180">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="c638e-181">Standaard modules worden gelezen van `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c638e-181">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="c638e-182">De PSReadline-geschiedenis wordt vastgelegd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c638e-182">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c638e-183">De profielen respecteren de configuratie van de Power shell per host.</span><span class="sxs-lookup"><span data-stu-id="c638e-183">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="c638e-184">Het standaard-host-profiel bestaat dus op `Microsoft.PowerShell_profile.ps1` dezelfde locatie.</span><span class="sxs-lookup"><span data-stu-id="c638e-184">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c638e-185">Power shell respecteert de [XDG-basis directory specificatie][xdg-bds] op macOS.</span><span class="sxs-lookup"><span data-stu-id="c638e-185">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="c638e-186">Omdat macOS een afleiding van BSD is, wordt het voor voegsel `/usr/local` gebruikt in plaats van `/opt` .</span><span class="sxs-lookup"><span data-stu-id="c638e-186">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="c638e-187">Dat `$PSHOME` wil zeggen `/usr/local/microsoft/powershell/7.1.0/` , en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="c638e-187">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="c638e-188">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="c638e-188">Installation support</span></span>

<span data-ttu-id="c638e-189">Micro soft ondersteunt de installatie methoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="c638e-189">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="c638e-190">Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="c638e-190">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="c638e-191">Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c638e-191">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c638e-192">Aanvullende resources</span><span class="sxs-lookup"><span data-stu-id="c638e-192">Additional Resources</span></span>

- <span data-ttu-id="c638e-193">[Homebrew-Web][brew]</span><span class="sxs-lookup"><span data-stu-id="c638e-193">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="c638e-194">[Homebrew github-opslag plaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="c638e-194">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="c638e-195">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="c638e-195">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[shell]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
