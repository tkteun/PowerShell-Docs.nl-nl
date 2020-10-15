---
title: PowerShell installeren in Linux
description: Informatie over het installeren van Power shell op diverse Linux-distributies
ms.date: 07/30/2020
ms.openlocfilehash: f35366b5b1a0f54ce2c90d0e3cba59be7b9ce82c
ms.sourcegitcommit: 2ca12827dc64198b4263e8873a45b9466f22a67c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2020
ms.locfileid: "92079792"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="7181c-103">PowerShell installeren in Linux</span><span class="sxs-lookup"><span data-stu-id="7181c-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="7181c-104">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="7181c-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="7181c-105">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="7181c-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="7181c-106">Voer uit `pwsh-preview` Als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7181c-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-107">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7181c-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="7181c-108">De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="7181c-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="7181c-109">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="7181c-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="7181c-110">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="7181c-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="7181c-111">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks te implementeren met behulp van het Linux- [ `tar.gz` Archief][tar], maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="7181c-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="7181c-112">Officieel ondersteunde releases</span><span class="sxs-lookup"><span data-stu-id="7181c-112">Officially supported releases</span></span>

- <span data-ttu-id="7181c-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7181c-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="7181c-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7181c-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="7181c-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="7181c-115">Debian 8</span></span>
- <span data-ttu-id="7181c-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7181c-116">Debian 9</span></span>
- <span data-ttu-id="7181c-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="7181c-117">Debian 10</span></span>
- <span data-ttu-id="7181c-118">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="7181c-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="7181c-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7181c-119">CentOS 7</span></span>
- <span data-ttu-id="7181c-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7181c-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="7181c-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7181c-121">Fedora 28</span></span>
- <span data-ttu-id="7181c-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="7181c-122">Fedora 29</span></span>
- <span data-ttu-id="7181c-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="7181c-123">Fedora 30</span></span>
- <span data-ttu-id="7181c-124">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="7181c-124">openSUSE 42.3</span></span>
- <span data-ttu-id="7181c-125">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7181c-125">openSUSE Leap 15</span></span>

<span data-ttu-id="7181c-126">Door de Community ondersteunde releases</span><span class="sxs-lookup"><span data-stu-id="7181c-126">Community supported releases</span></span>

- <span data-ttu-id="7181c-127">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="7181c-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="7181c-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="7181c-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="7181c-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7181c-129">Arch Linux</span></span>
- <span data-ttu-id="7181c-130">Kali</span><span class="sxs-lookup"><span data-stu-id="7181c-130">Kali</span></span>
- <span data-ttu-id="7181c-131">Raspbian (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="7181c-131">Raspbian (experimental)</span></span>

<span data-ttu-id="7181c-132">Alternatieve installatie methoden</span><span class="sxs-lookup"><span data-stu-id="7181c-132">Alternate install methods</span></span>

- <span data-ttu-id="7181c-133">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="7181c-133">Snap Package</span></span>
- <span data-ttu-id="7181c-134">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="7181c-134">Binary Archives</span></span>
- <span data-ttu-id="7181c-135">Hulp programma .NET Global</span><span class="sxs-lookup"><span data-stu-id="7181c-135">.NET Global tool</span></span>

<span data-ttu-id="7181c-136">Momenteel niet ondersteund</span><span class="sxs-lookup"><span data-stu-id="7181c-136">Not currently supported</span></span>

- <span data-ttu-id="7181c-137">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="7181c-137">Ubuntu 20.04</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-138">Power shell kan alleen de distributies ondersteunen die door .NET worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7181c-138">PowerShell can only support the distributions that are supported by .NET.</span></span> <span data-ttu-id="7181c-139">Zie de [opmerkingen bij de release van .net core][distros] voor een lijst met ondersteunde distributies.</span><span class="sxs-lookup"><span data-stu-id="7181c-139">See the [.NET Core release notes][distros] for a list of supported distributions.</span></span> <span data-ttu-id="7181c-140">Als er een distributie wordt ondersteund door .NET die hier niet wordt vermeld, kunt u een aanvraag indienen om de ondersteuning voor de distributie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="7181c-140">If there is a distribution supported by .NET that is not listed here, you can request that support for the distribution be added.</span></span> <span data-ttu-id="7181c-141">U kunt een aanvraag indienen via de sjabloon voor de [ondersteunings aanvraag voor distributie][] .</span><span class="sxs-lookup"><span data-stu-id="7181c-141">Please file a request using the [Distribution Support Request][] template.</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="7181c-142">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7181c-142">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="7181c-143">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7181c-143">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="7181c-144">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-144">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7181c-145">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7181c-145">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of packages after we added packages.microsoft.com
sudo apt-get update
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="7181c-146">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7181c-146">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7181c-147">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="7181c-147">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="7181c-148">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7181c-148">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="7181c-149">Down load het Debian-pakket `powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="7181c-149">Download the Debian package `powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7181c-150">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-150">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7181c-151">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7181c-151">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="7181c-152">Met de volgende opdracht worden `apt-get install -f` deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="7181c-152">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="7181c-153">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7181c-153">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="7181c-154">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7181c-154">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="7181c-155">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7181c-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="7181c-156">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-156">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7181c-157">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7181c-157">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of products
sudo apt-get update
# Enable the "universe" repositories
sudo add-apt-repository universe
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="7181c-158">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7181c-158">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7181c-159">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="7181c-159">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="7181c-160">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7181c-160">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="7181c-161">Down load het Debian-pakket `powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="7181c-161">Download the Debian package `powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7181c-162">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-162">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7181c-163">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7181c-163">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="7181c-164">Met de volgende opdracht worden `apt-get install -f` deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="7181c-164">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="7181c-165">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7181c-165">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="7181c-166">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="7181c-166">Ubuntu 18.10</span></span>

<span data-ttu-id="7181c-167">De installatie wordt ondersteund via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="7181c-167">Installation is supported via `snapd`.</span></span> <span data-ttu-id="7181c-168">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="7181c-168">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-169">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="7181c-169">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="7181c-170">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="7181c-170">Ubuntu 19.04</span></span>

<span data-ttu-id="7181c-171">De installatie wordt ondersteund via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="7181c-171">Installation is supported via `snapd`.</span></span> <span data-ttu-id="7181c-172">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="7181c-172">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-173">Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="7181c-173">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-2004"></a><span data-ttu-id="7181c-174">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="7181c-174">Ubuntu 20.04</span></span>

<span data-ttu-id="7181c-175">Ubuntu 20,04 is een LTS-release.</span><span class="sxs-lookup"><span data-stu-id="7181c-175">Ubuntu 20.04 is an LTS release.</span></span> <span data-ttu-id="7181c-176">Power shell biedt momenteel geen ondersteuning voor deze versie.</span><span class="sxs-lookup"><span data-stu-id="7181c-176">PowerShell does not currently support this version.</span></span> <span data-ttu-id="7181c-177">Ondersteuning voor deze versie wordt overwogen voor de Power shell 7,1-release.</span><span class="sxs-lookup"><span data-stu-id="7181c-177">Support for this version is being considered for the PowerShell 7.1 release.</span></span> <span data-ttu-id="7181c-178">Ga naar deze [aanvraag](https://github.com/PowerShell/PowerShell/issues/12626) als u ondersteuning wilt voor Ubuntu 20,04.</span><span class="sxs-lookup"><span data-stu-id="7181c-178">Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.</span></span>

## <a name="debian-8"></a><span data-ttu-id="7181c-179">Debian 8</span><span class="sxs-lookup"><span data-stu-id="7181c-179">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="7181c-180">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="7181c-180">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="7181c-181">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-181">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7181c-182">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7181c-182">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7181c-183">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7181c-183">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7181c-184">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="7181c-184">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="7181c-185">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7181c-185">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="7181c-186">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7181c-186">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="7181c-187">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-187">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7181c-188">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7181c-188">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7181c-189">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7181c-189">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7181c-190">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="7181c-190">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="7181c-191">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7181c-191">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="7181c-192">Down load het Debian-pakket `powershell-lts_7.0.3-1.debian.9_amd64.deb` van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="7181c-192">Download the Debian package `powershell-lts_7.0.3-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7181c-193">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-193">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.3-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="7181c-194">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7181c-194">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="7181c-195">Debian 10</span><span class="sxs-lookup"><span data-stu-id="7181c-195">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-196">Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7181c-196">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="7181c-197">Installatie via pakket opslagplaats-Debian 10</span><span class="sxs-lookup"><span data-stu-id="7181c-197">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="7181c-198">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-198">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7181c-199">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7181c-199">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="7181c-200">Installatie via direct downloaden-Debian 10</span><span class="sxs-lookup"><span data-stu-id="7181c-200">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="7181c-201">Down load het pakket tar. gz `powershell-7.0.3-linux-x64.tar.gz` van de pagina [releases][] op de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="7181c-201">Download the tar.gz package `powershell-7.0.3-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7181c-202">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-202">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="7181c-203">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="7181c-203">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-204">Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7181c-204">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="7181c-205">Installatie via direct downloaden-Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="7181c-205">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="7181c-206">Down load het pakket tar. gz `powershell-7.0.3-linux-alpine-x64.tar.gz` van de pagina [releases][] op de Alpine machine.</span><span class="sxs-lookup"><span data-stu-id="7181c-206">Download the tar.gz package `powershell-7.0.3-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="7181c-207">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-207">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a><span data-ttu-id="7181c-208">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7181c-208">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-209">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="7181c-209">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="7181c-210">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7181c-210">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="7181c-211">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7181c-212">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7181c-212">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7181c-213">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="7181c-213">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="7181c-214">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7181c-214">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="7181c-215">Gebruik [CentOS 7][]om het rpm-pakket te downloaden `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="7181c-215">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="7181c-216">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-216">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7181c-217">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7181c-217">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="7181c-218">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7181c-218">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7181c-220">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7181c-220">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7181c-221">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7181c-221">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7181c-222">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-222">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7181c-223">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7181c-223">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7181c-224">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="7181c-224">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7181c-225">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7181c-225">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7181c-226">Down load het RPM-pakket `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="7181c-226">Download the RPM package `powershell-lts-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="7181c-227">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-227">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7181c-228">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7181c-228">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-lts-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7181c-229">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7181c-229">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="7181c-230">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7181c-230">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="7181c-231">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="7181c-231">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="7181c-232">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7181c-232">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="7181c-233">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7181c-233">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="7181c-234">Fedora</span><span class="sxs-lookup"><span data-stu-id="7181c-234">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-235">Fedora 28 wordt alleen ondersteund in Power shell 6,1 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7181c-235">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-236">Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7181c-236">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="7181c-237">Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="7181c-237">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="7181c-238">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-238">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="7181c-239">Installatie via direct downloaden-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="7181c-239">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="7181c-240">Down load het RPM-pakket `powershell-7.0.3-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="7181c-240">Download the RPM package `powershell-7.0.3-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="7181c-241">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7181c-241">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.3-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7181c-242">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7181c-242">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="7181c-243">Installatie ongedaan maken-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="7181c-243">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="7181c-244">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7181c-244">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-245">Arch-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="7181c-245">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="7181c-246">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="7181c-246">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="7181c-247">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="7181c-247">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="7181c-248">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="7181c-248">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="7181c-249">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="7181c-249">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="7181c-250">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="7181c-250">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="7181c-251">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of [Power shell in docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="7181c-251">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="7181c-253">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="7181c-253">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="7181c-254">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="7181c-254">Getting snapd</span></span>

<span data-ttu-id="7181c-255">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="7181c-255">`snapd` is required to run snaps.</span></span> <span data-ttu-id="7181c-256">Volg [deze instructies](https://docs.snapcraft.io/core/install) om te controleren of u hebt `snapd` geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7181c-256">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="7181c-257">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="7181c-257">Installation via Snap</span></span>

<span data-ttu-id="7181c-258">Power shell voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7181c-258">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="7181c-259">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7181c-259">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="7181c-260">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="7181c-260">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="7181c-261">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="7181c-261">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="7181c-262">U kunt een upgrade activeren met `sudo snap refresh powershell` of `sudo snap refresh powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="7181c-262">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="7181c-263">Installatie ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="7181c-263">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="7181c-264">of</span><span class="sxs-lookup"><span data-stu-id="7181c-264">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="7181c-265">Kali</span><span class="sxs-lookup"><span data-stu-id="7181c-265">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-266">Kali-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="7181c-266">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="7181c-267">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="7181c-267">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="7181c-268">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="7181c-268">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="7181c-269">Raspbian</span><span class="sxs-lookup"><span data-stu-id="7181c-269">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="7181c-270">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="7181c-270">Raspbian support is experimental.</span></span>

<span data-ttu-id="7181c-271">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="7181c-271">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="7181c-272">CoreCLR en Power shell werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="7181c-272">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="7181c-273">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="7181c-273">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="7181c-274">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="7181c-274">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.3-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="7181c-275">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar het `pwsh` binaire bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="7181c-275">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="7181c-276">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="7181c-276">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="7181c-277">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="7181c-277">Installing Preview Releases</span></span>

<span data-ttu-id="7181c-278">Wanneer u een Power shell preview-release voor Linux installeert via een pakket opslagplaats, wordt de naam van het pakket gewijzigd van `powershell` in `powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="7181c-278">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="7181c-279">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="7181c-279">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="7181c-280">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="7181c-280">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="7181c-281">Distributie(s)</span><span class="sxs-lookup"><span data-stu-id="7181c-281">Distribution(s)</span></span> |            <span data-ttu-id="7181c-282">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="7181c-282">Stable Command</span></span>            |               <span data-ttu-id="7181c-283">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="7181c-283">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="7181c-284">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="7181c-284">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="7181c-285">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="7181c-285">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="7181c-286">Fedora</span><span class="sxs-lookup"><span data-stu-id="7181c-286">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="7181c-287">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="7181c-287">Install as a .NET Global tool</span></span>

<span data-ttu-id="7181c-288">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="7181c-288">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="7181c-289">Het hulp programma DotNet tool wordt toegevoegd `~/.dotnet/tools` aan de `PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="7181c-289">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="7181c-290">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `PATH` .</span><span class="sxs-lookup"><span data-stu-id="7181c-290">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="7181c-291">U moet Power shell kunnen starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="7181c-291">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="7181c-292">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="7181c-292">Binary Archives</span></span>

<span data-ttu-id="7181c-293">Er zijn binaire Power shell- `tar.gz` archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="7181c-293">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="7181c-294">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="7181c-294">Dependencies</span></span>

<span data-ttu-id="7181c-295">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="7181c-295">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="7181c-296">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="7181c-296">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="7181c-297">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="7181c-297">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="7181c-298">OS</span><span class="sxs-lookup"><span data-stu-id="7181c-298">OS</span></span>                 | <span data-ttu-id="7181c-299">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="7181c-299">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="7181c-300">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7181c-300">Ubuntu 16.04</span></span>       | <span data-ttu-id="7181c-301">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7181c-301">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7181c-302">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="7181c-302">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="7181c-303">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="7181c-303">Ubuntu 17.10</span></span>       | <span data-ttu-id="7181c-304">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7181c-304">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7181c-305">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="7181c-305">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="7181c-306">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7181c-306">Ubuntu 18.04</span></span>       | <span data-ttu-id="7181c-307">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7181c-307">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7181c-308">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="7181c-308">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="7181c-309">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="7181c-309">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="7181c-310">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7181c-310">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7181c-311">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7181c-311">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7181c-312">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="7181c-312">Debian 9 (Stretch)</span></span> | <span data-ttu-id="7181c-313">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7181c-313">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7181c-314">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="7181c-314">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="7181c-315">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7181c-315">CentOS 7</span></span> <br> <span data-ttu-id="7181c-316">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7181c-316">Oracle Linux 7</span></span> <br> <span data-ttu-id="7181c-317">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="7181c-317">RHEL 7</span></span> | <span data-ttu-id="7181c-318">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="7181c-318">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="7181c-319">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="7181c-319">openSUSE 42.3</span></span> | <span data-ttu-id="7181c-320">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="7181c-320">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="7181c-321">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7181c-321">openSUSE Leap 15</span></span> | <span data-ttu-id="7181c-322">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="7181c-322">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="7181c-323">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="7181c-323">Fedora 27</span></span> <br> <span data-ttu-id="7181c-324">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7181c-324">Fedora 28</span></span> | <span data-ttu-id="7181c-325">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="7181c-325">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="7181c-326">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="7181c-326">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="7181c-327">Bijvoorbeeld, onze [Amazon Linux-dockerfile][amazon-dockerfile] installeert eerst afhankelijkheden en extraheert vervolgens het Linux- `tar.gz` Archief.</span><span class="sxs-lookup"><span data-stu-id="7181c-327">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="7181c-328">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="7181c-328">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="7181c-329">Linux</span><span class="sxs-lookup"><span data-stu-id="7181c-329">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="7181c-330">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="7181c-330">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="7181c-331">Paden</span><span class="sxs-lookup"><span data-stu-id="7181c-331">Paths</span></span>

- <span data-ttu-id="7181c-332">`$PSHOME` is `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="7181c-332">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="7181c-333">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7181c-333">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="7181c-334">Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7181c-334">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="7181c-335">Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7181c-335">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="7181c-336">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7181c-336">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="7181c-337">Standaard modules worden gelezen van `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="7181c-337">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="7181c-338">De PSReadLine-geschiedenis wordt vastgelegd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="7181c-338">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7181c-339">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="7181c-339">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7181c-340">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="7181c-340">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="7181c-341">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="7181c-341">Installation support</span></span>

<span data-ttu-id="7181c-342">Micro soft ondersteunt de installatie methoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="7181c-342">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="7181c-343">Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="7181c-343">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="7181c-344">Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7181c-344">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[shell]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Aanvraag voor distributie ondersteuning]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
