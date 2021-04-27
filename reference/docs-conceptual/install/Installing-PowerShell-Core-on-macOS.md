---
title: PowerShell installeren in macOS
description: Informatie over het installeren van PowerShell in macOS
ms.date: 04/26/2021
ms.openlocfilehash: ea878dad1ce4d2ab2b48a34b5f89ba8ebb7c82c3
ms.sourcegitcommit: 1e1535cb22d16de06f80beafe77a37a7c77de6d3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025610"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="c388e-103">PowerShell installeren in macOS</span><span class="sxs-lookup"><span data-stu-id="c388e-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="c388e-104">Voor PowerShell 7.0 of hoger is macOS 10.13 en hoger vereist.</span><span class="sxs-lookup"><span data-stu-id="c388e-104">PowerShell 7.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="c388e-105">Alle pakketten zijn beschikbaar op onze pagina met [GitHub-releases.][]</span><span class="sxs-lookup"><span data-stu-id="c388e-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="c388e-106">Nadat het pakket is geïnstalleerd, moet u `pwsh` uitvoeren vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="c388e-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="c388e-107">PowerShell 7.1 is een in-place upgrade die PowerShell Core 6.x en 7.0 verwijdert.</span><span class="sxs-lookup"><span data-stu-id="c388e-107">PowerShell 7.1 is an in-place upgrade that removes PowerShell Core 6.x and 7.0.</span></span>
>
> <span data-ttu-id="c388e-108">De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="c388e-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="c388e-109">Als u een oudere versie van PowerShell Core naast PowerShell 7.1 wilt uitvoeren, installeert u de versie die u wilt gebruiken met behulp van de [binaire archiefmethode.](#binary-archives)</span><span class="sxs-lookup"><span data-stu-id="c388e-109">If you need to run and older version of PowerShell core side-by-side with PowerShell 7.1, install the version you want using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="c388e-110">Er zijn verschillende manieren om PowerShell in macOS te installeren.</span><span class="sxs-lookup"><span data-stu-id="c388e-110">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="c388e-111">Kies één van de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="c388e-111">Choose one of the following methods:</span></span>

- <span data-ttu-id="c388e-112">Installeer met [behulp van Homebrew][brew].</span><span class="sxs-lookup"><span data-stu-id="c388e-112">Install using [Homebrew][brew].</span></span> <span data-ttu-id="c388e-113">Homebrew is het voorkeurspakketbeheer voor macOS.</span><span class="sxs-lookup"><span data-stu-id="c388e-113">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="c388e-114">PowerShell installeren via [Direct downloaden](#installation-via-direct-download)</span><span class="sxs-lookup"><span data-stu-id="c388e-114">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="c388e-115">Installeer vanuit [binaire archieven.](#binary-archives)</span><span class="sxs-lookup"><span data-stu-id="c388e-115">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="c388e-116">Nadat u PowerShell hebt geïnstalleerd, moet u [OpenSSL installeren.](#installing-dependencies)</span><span class="sxs-lookup"><span data-stu-id="c388e-116">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c388e-117">OpenSSL is nodig voor remoting- en CIM-bewerkingen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c388e-117">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="c388e-118">Installatie van de nieuwste stabiele release via Homebrew in macOS 10.13 of hoger</span><span class="sxs-lookup"><span data-stu-id="c388e-118">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="c388e-119">Als de `brew` opdracht niet wordt gevonden, moet u Homebrew installeren volgens [de instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="c388e-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

<span data-ttu-id="c388e-120">U kunt nu PowerShell installeren:</span><span class="sxs-lookup"><span data-stu-id="c388e-120">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell
```

<span data-ttu-id="c388e-121">Controleer ten slotte of de installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="c388e-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="c388e-122">Wanneer er nieuwe versies van PowerShell worden uitgebracht, moet u de formule van Homebrew bijwerken en PowerShell upgraden:</span><span class="sxs-lookup"><span data-stu-id="c388e-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> <span data-ttu-id="c388e-123">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een PowerShell-host (pwsh), maar vervolgens moet de PowerShell-shell worden afgesloten en opnieuw worden gestart om de upgrade te voltooien en de waarden in te `$PSVersionTable` vernieuwen.</span><span class="sxs-lookup"><span data-stu-id="c388e-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="c388e-124">Installatie van de nieuwste preview-versie via Homebrew in macOS 10.13 of hoger</span><span class="sxs-lookup"><span data-stu-id="c388e-124">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="c388e-125">Nadat u Homebrew hebt geïnstalleerd, kunt u PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="c388e-125">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="c388e-126">Installeer eerst het [pakket Cask-Versions][cask-versions] waarmee u alternatieve versies van cask-pakketten kunt installeren:</span><span class="sxs-lookup"><span data-stu-id="c388e-126">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="c388e-127">Nu kunt u PowerShell installeren:</span><span class="sxs-lookup"><span data-stu-id="c388e-127">Now, you can install PowerShell:</span></span>

```sh
brew install --cask powershell-preview
```

<span data-ttu-id="c388e-128">Controleer ten slotte of de installatie goed werkt:</span><span class="sxs-lookup"><span data-stu-id="c388e-128">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="c388e-129">Wanneer er nieuwe versies van PowerShell worden uitgebracht, kunt u de formules van Homebrew bijwerken en PowerShell upgraden:</span><span class="sxs-lookup"><span data-stu-id="c388e-129">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> <span data-ttu-id="c388e-130">De bovenstaande opdrachten kunnen worden aangeroepen vanuit een PowerShell-host (pwsh), maar vervolgens moet de PowerShell-shell worden afgesloten en opnieuw worden gestart om de upgrade te voltooien.</span><span class="sxs-lookup"><span data-stu-id="c388e-130">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="c388e-131">en vernieuw de waarden die worden weergegeven in `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="c388e-131">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="c388e-132">Het installeren van PowerShell met behulp van de Homebrew-tikmethode wordt ook ondersteund voor stabiele en LTS-versies.</span><span class="sxs-lookup"><span data-stu-id="c388e-132">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="c388e-133">U kunt nu uw installatie controleren</span><span class="sxs-lookup"><span data-stu-id="c388e-133">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="c388e-134">Wanneer er nieuwe versies van PowerShell worden uitgebracht, kunt u gewoon de volgende opdracht uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c388e-134">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="c388e-135">Of u nu het cask- of de tikmethode gebruikt, bij het bijwerken naar een nieuwere versie van PowerShell gebruikt u dezelfde methode die u hebt gebruikt om PowerShell in eerste instantie te installeren.</span><span class="sxs-lookup"><span data-stu-id="c388e-135">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="c388e-136">Als u een andere methode gebruikt, blijft het openen van een nieuwe pwsh-sessie de oudere versie van PowerShell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c388e-136">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="c388e-137">Als u besluit verschillende methoden te gebruiken, zijn er manieren om het probleem op te lossen met behulp van de [Homebrew-koppelingsmethode](https://docs.brew.sh/Manpage#link-ln-options-formula).</span><span class="sxs-lookup"><span data-stu-id="c388e-137">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="c388e-138">Installatie via Direct downloaden</span><span class="sxs-lookup"><span data-stu-id="c388e-138">Installation via Direct Download</span></span>

<span data-ttu-id="c388e-139">Download het PKG-pakket `powershell-7.1.3-osx-x64.pkg` van de [releasepagina][] op uw macOS-computer.</span><span class="sxs-lookup"><span data-stu-id="c388e-139">Download the PKG package `powershell-7.1.3-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="c388e-140">U kunt dubbelklikken op het bestand en de aanwijzingen volgen of het installeren vanuit de terminal:</span><span class="sxs-lookup"><span data-stu-id="c388e-140">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-7.1.3-osx-x64.pkg -target /
```

<span data-ttu-id="c388e-141">Installeer [OpenSSL.](#installing-dependencies)</span><span class="sxs-lookup"><span data-stu-id="c388e-141">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c388e-142">OpenSSL is nodig voor remoting- en CIM-bewerkingen van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c388e-142">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="c388e-143">Installeren als een .NET Global-hulpprogramma</span><span class="sxs-lookup"><span data-stu-id="c388e-143">Install as a .NET Global tool</span></span>

<span data-ttu-id="c388e-144">Als u de .NET Core SDK [al](/dotnet/core/sdk) hebt geïnstalleerd, kunt u PowerShell eenvoudig installeren als [een .NET Global-hulpprogramma.](/dotnet/core/tools/global-tools)</span><span class="sxs-lookup"><span data-stu-id="c388e-144">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="c388e-145">Het dotnet-hulpprogramma-installatieprogramma wordt `~/.dotnet/tools` toegevoegd aan uw `PATH` omgevingsvariabele.</span><span class="sxs-lookup"><span data-stu-id="c388e-145">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="c388e-146">De momenteel lopende shell heeft echter niet de bijgewerkte `PATH` .</span><span class="sxs-lookup"><span data-stu-id="c388e-146">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="c388e-147">U moet PowerShell vanuit een nieuwe shell kunnen starten door te `pwsh` typen.</span><span class="sxs-lookup"><span data-stu-id="c388e-147">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="c388e-148">Installeer [OpenSSL.](#installing-dependencies)</span><span class="sxs-lookup"><span data-stu-id="c388e-148">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c388e-149">OpenSSL is nodig voor remoting- en CIM-bewerkingen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c388e-149">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="c388e-150">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="c388e-150">Binary Archives</span></span>

<span data-ttu-id="c388e-151">Er zijn binaire `tar.gz` PowerShell-archieven beschikbaar voor het macOS-platform om geavanceerde implementatiescenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="c388e-151">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="c388e-152">Wanneer u met deze methode installeert, moet u ook handmatig eventuele afhankelijkheden installeren.</span><span class="sxs-lookup"><span data-stu-id="c388e-152">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="c388e-153">Installeer [OpenSSL.](#installing-dependencies)</span><span class="sxs-lookup"><span data-stu-id="c388e-153">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="c388e-154">OpenSSL is nodig voor remoting- en CIM-bewerkingen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c388e-154">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

> [!NOTE]
> <span data-ttu-id="c388e-155">U kunt deze methode gebruiken om elke versie van PowerShell te installeren, inclusief de nieuwste versie:</span><span class="sxs-lookup"><span data-stu-id="c388e-155">You can use this method to install any version of PowerShell including the latest:</span></span>
> - <span data-ttu-id="c388e-156">Stabiele release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)</span><span class="sxs-lookup"><span data-stu-id="c388e-156">Stable release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)</span></span>
> - <span data-ttu-id="c388e-157">Preview-versie: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)</span><span class="sxs-lookup"><span data-stu-id="c388e-157">Preview release: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)</span></span>
> - <span data-ttu-id="c388e-158">LTS-release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)</span><span class="sxs-lookup"><span data-stu-id="c388e-158">LTS release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="c388e-159">Binaire archieven installeren in macOS</span><span class="sxs-lookup"><span data-stu-id="c388e-159">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.3/powershell-7.1.3-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.3

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.3

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.3/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.3/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="c388e-160">Afhankelijkheden installeren</span><span class="sxs-lookup"><span data-stu-id="c388e-160">Installing dependencies</span></span>

<span data-ttu-id="c388e-161">OpenSSL is vereist voor remoting- en CIM-bewerkingen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c388e-161">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="c388e-162">U kunt OpenSSL indien nodig installeren via MacPorts.</span><span class="sxs-lookup"><span data-stu-id="c388e-162">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="c388e-163">MacPorts en Homebrew kunnen problemen hebben wanneer ze worden gebruikt in hetzelfde systeem.</span><span class="sxs-lookup"><span data-stu-id="c388e-163">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="c388e-164">Homebrew heeft echter geen pakket voor OpenSSL 1.0.</span><span class="sxs-lookup"><span data-stu-id="c388e-164">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="c388e-165">Zie de Veelgestelde vragen over [MacPorts voor meer informatie.](https://trac.macports.org/wiki/FAQ)</span><span class="sxs-lookup"><span data-stu-id="c388e-165">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="c388e-166">Installeer de Xcode-opdrachtregelprogramma's.</span><span class="sxs-lookup"><span data-stu-id="c388e-166">Install the Xcode command-line tools.</span></span> <span data-ttu-id="c388e-167">De Xcode-hulpprogramma's zijn vereist voor MacPorts.</span><span class="sxs-lookup"><span data-stu-id="c388e-167">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="c388e-168">Installeer MacPorts.</span><span class="sxs-lookup"><span data-stu-id="c388e-168">Install MacPorts.</span></span> <span data-ttu-id="c388e-169">Raadpleeg de installatiehandleiding als u [instructies nodig hebt.](https://www.macports.org/install.php)</span><span class="sxs-lookup"><span data-stu-id="c388e-169">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="c388e-170">Werk MacPorts bij door uit te `sudo port selfupdate` werken.</span><span class="sxs-lookup"><span data-stu-id="c388e-170">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="c388e-171">Upgrade MacPorts-pakketten door uit te `sudo port upgrade outdated` voeren.</span><span class="sxs-lookup"><span data-stu-id="c388e-171">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="c388e-172">Installeer OpenSSL door uit te `sudo port install openssl10` gaan.</span><span class="sxs-lookup"><span data-stu-id="c388e-172">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="c388e-173">Koppel de bibliotheken om ze beschikbaar te maken voor PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c388e-173">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="c388e-174">PowerShell verwijderen</span><span class="sxs-lookup"><span data-stu-id="c388e-174">Uninstalling PowerShell</span></span>

<span data-ttu-id="c388e-175">Als u PowerShell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:</span><span class="sxs-lookup"><span data-stu-id="c388e-175">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew --cask uninstall powershell
```

<span data-ttu-id="c388e-176">Als u PowerShell hebt geïnstalleerd via direct downloaden, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="c388e-176">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="c388e-177">Als u de extra PowerShell-paden wilt verwijderen, raadpleegt u de [sectie paden](#paths) in dit document en verwijdert u de paden met behulp van `sudo rm` .</span><span class="sxs-lookup"><span data-stu-id="c388e-177">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="c388e-178">Dit is niet nodig als u hebt geïnstalleerd met Homebrew.</span><span class="sxs-lookup"><span data-stu-id="c388e-178">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="c388e-179">Paden</span><span class="sxs-lookup"><span data-stu-id="c388e-179">Paths</span></span>

- <span data-ttu-id="c388e-180">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.3/`</span><span class="sxs-lookup"><span data-stu-id="c388e-180">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.3/`</span></span>
- <span data-ttu-id="c388e-181">Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c388e-181">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="c388e-182">Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c388e-182">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="c388e-183">Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c388e-183">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="c388e-184">Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c388e-184">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="c388e-185">Standaardmodules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c388e-185">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="c388e-186">De PSReadline-geschiedenis wordt vastgelegd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c388e-186">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c388e-187">De profielen respecteren de configuratie per host van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c388e-187">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="c388e-188">Het standaard hostspecifieke profiel bevindt zich dus `Microsoft.PowerShell_profile.ps1` op dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="c388e-188">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c388e-189">PowerShell respecteert de [XDG-basismapspecificatie][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="c388e-189">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="c388e-190">Omdat macOS een afleiding van BSD is, wordt het voorvoegsel `/usr/local` gebruikt in plaats van `/opt` .</span><span class="sxs-lookup"><span data-stu-id="c388e-190">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="c388e-191">Is dus `$PSHOME` `/usr/local/microsoft/powershell/7.1.3/` en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="c388e-191">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.1.3/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="c388e-192">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="c388e-192">Installation support</span></span>

<span data-ttu-id="c388e-193">Microsoft ondersteunt de installatiemethoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="c388e-193">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="c388e-194">Er zijn mogelijk andere installatiemethoden beschikbaar vanuit andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="c388e-194">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="c388e-195">Hoewel deze hulpprogramma's en methoden kunnen werken, biedt Microsoft geen ondersteuning voor deze methoden.</span><span class="sxs-lookup"><span data-stu-id="c388e-195">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c388e-196">Aanvullende resources</span><span class="sxs-lookup"><span data-stu-id="c388e-196">Additional Resources</span></span>

- <span data-ttu-id="c388e-197">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="c388e-197">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="c388e-198">[Homebrew Github-opslagplaats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="c388e-198">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="c388e-199">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="c388e-199">[Homebrew-Cask][cask]</span></span>

[brew]: https://docs.brew.sh/Installation
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Releases]: https://aka.ms/powershell-release?tag=stable
[releases]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
