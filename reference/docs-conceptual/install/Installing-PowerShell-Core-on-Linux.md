---
title: PowerShell installeren in Linux
description: Informatie over het installeren van Power shell op diverse Linux-distributies
ms.date: 03/09/2020
ms.openlocfilehash: e04d8a91999cd6e9b2d669230c7a1b412f11eeb8
ms.sourcegitcommit: 4eda0bc902658d4a188159bd7310e64399f6e178
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83271896"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="561b5-103">PowerShell installeren in Linux</span><span class="sxs-lookup"><span data-stu-id="561b5-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="561b5-104">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="561b5-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="561b5-105">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="561b5-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="561b5-106">Voer uit `pwsh-preview` Als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="561b5-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-107">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="561b5-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="561b5-108">De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="561b5-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="561b5-109">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="561b5-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="561b5-110">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="561b5-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="561b5-111">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks te implementeren met behulp van het Linux- [ `tar.gz` Archief][tar], maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="561b5-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="561b5-112">Officieel ondersteunde releases</span><span class="sxs-lookup"><span data-stu-id="561b5-112">Officially supported releases</span></span>

- <span data-ttu-id="561b5-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="561b5-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="561b5-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="561b5-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="561b5-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="561b5-115">Debian 8</span></span>
- <span data-ttu-id="561b5-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="561b5-116">Debian 9</span></span>
- <span data-ttu-id="561b5-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="561b5-117">Debian 10</span></span>
- <span data-ttu-id="561b5-118">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="561b5-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="561b5-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="561b5-119">CentOS 7</span></span>
- <span data-ttu-id="561b5-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="561b5-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="561b5-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="561b5-121">Fedora 28</span></span>
- <span data-ttu-id="561b5-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="561b5-122">Fedora 29</span></span>
- <span data-ttu-id="561b5-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="561b5-123">Fedora 30</span></span>
- <span data-ttu-id="561b5-124">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="561b5-124">openSUSE 42.3</span></span>
- <span data-ttu-id="561b5-125">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="561b5-125">openSUSE Leap 15</span></span>

<span data-ttu-id="561b5-126">Door de Community ondersteunde releases</span><span class="sxs-lookup"><span data-stu-id="561b5-126">Community supported releases</span></span>

- <span data-ttu-id="561b5-127">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="561b5-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="561b5-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="561b5-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="561b5-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="561b5-129">Arch Linux</span></span>
- <span data-ttu-id="561b5-130">Kali</span><span class="sxs-lookup"><span data-stu-id="561b5-130">Kali</span></span>
- <span data-ttu-id="561b5-131">Raspbian (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="561b5-131">Raspbian (experimental)</span></span>

<span data-ttu-id="561b5-132">Alternatieve installatie methoden</span><span class="sxs-lookup"><span data-stu-id="561b5-132">Alternate install methods</span></span>

- <span data-ttu-id="561b5-133">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="561b5-133">Snap Package</span></span>
- <span data-ttu-id="561b5-134">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="561b5-134">Binary Archives</span></span>
- <span data-ttu-id="561b5-135">Hulp programma .NET Global</span><span class="sxs-lookup"><span data-stu-id="561b5-135">.NET Global tool</span></span>

<span data-ttu-id="561b5-136">Momenteel niet ondersteund</span><span class="sxs-lookup"><span data-stu-id="561b5-136">Not currently supported</span></span> 

- <span data-ttu-id="561b5-137">Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="561b5-137">Ubuntu 20.04</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="561b5-138">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="561b5-138">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="561b5-139">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="561b5-139">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="561b5-140">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-140">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="561b5-141">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="561b5-141">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="561b5-142">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="561b5-142">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="561b5-143">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell` .</span><span class="sxs-lookup"><span data-stu-id="561b5-143">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="561b5-144">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="561b5-144">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="561b5-145">Down load het Debian-pakket `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="561b5-145">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="561b5-146">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-146">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="561b5-147">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="561b5-147">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="561b5-148">Met de volgende opdracht worden `apt-get install -f` deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="561b5-148">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="561b5-149">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="561b5-149">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="561b5-150">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="561b5-150">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="561b5-151">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="561b5-151">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="561b5-152">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-152">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="561b5-153">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="561b5-153">The preferred method is as follows:</span></span>

```sh
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

<span data-ttu-id="561b5-154">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="561b5-154">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="561b5-155">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell` .</span><span class="sxs-lookup"><span data-stu-id="561b5-155">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="561b5-156">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="561b5-156">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="561b5-157">Down load het Debian-pakket `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="561b5-157">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="561b5-158">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-158">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="561b5-159">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="561b5-159">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="561b5-160">Met de volgende opdracht worden `apt-get install -f` deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="561b5-160">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="561b5-161">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="561b5-161">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="561b5-162">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="561b5-162">Ubuntu 18.10</span></span>

<span data-ttu-id="561b5-163">De installatie wordt ondersteund via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="561b5-163">Installation is supported via `snapd`.</span></span> <span data-ttu-id="561b5-164">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="561b5-164">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-165">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="561b5-165">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="561b5-166">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="561b5-166">Ubuntu 19.04</span></span>

<span data-ttu-id="561b5-167">De installatie wordt ondersteund via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="561b5-167">Installation is supported via `snapd`.</span></span> <span data-ttu-id="561b5-168">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="561b5-168">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-169">Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="561b5-169">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-2004"></a><span data-ttu-id="561b5-170">Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="561b5-170">Ubuntu 20.04</span></span>

<span data-ttu-id="561b5-171">Ubuntu 20,04 is een LTS-release.</span><span class="sxs-lookup"><span data-stu-id="561b5-171">Ubuntu 20.04 is an LTS release.</span></span> <span data-ttu-id="561b5-172">Power shell biedt momenteel geen ondersteuning voor deze versie.</span><span class="sxs-lookup"><span data-stu-id="561b5-172">PowerShell does not currently support this version.</span></span> <span data-ttu-id="561b5-173">Ondersteuning voor deze versie wordt overwogen voor de Power shell 7,1-release.</span><span class="sxs-lookup"><span data-stu-id="561b5-173">Support for this version is being considered for the PowerShell 7.1 release.</span></span> <span data-ttu-id="561b5-174">Ga naar deze [aanvraag](https://github.com/PowerShell/PowerShell/issues/12626) als u ondersteuning wilt voor Ubuntu 20,04.</span><span class="sxs-lookup"><span data-stu-id="561b5-174">Please upvote this [request](https://github.com/PowerShell/PowerShell/issues/12626) if you would like support for Ubuntu 20.04.</span></span>

## <a name="debian-8"></a><span data-ttu-id="561b5-175">Debian 8</span><span class="sxs-lookup"><span data-stu-id="561b5-175">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="561b5-176">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="561b5-176">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="561b5-177">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-177">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="561b5-178">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="561b5-178">The preferred method is as follows:</span></span>

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

<span data-ttu-id="561b5-179">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="561b5-179">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="561b5-180">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell` .</span><span class="sxs-lookup"><span data-stu-id="561b5-180">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="561b5-181">Debian 9</span><span class="sxs-lookup"><span data-stu-id="561b5-181">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="561b5-182">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="561b5-182">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="561b5-183">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-183">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="561b5-184">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="561b5-184">The preferred method is as follows:</span></span>

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

<span data-ttu-id="561b5-185">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="561b5-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="561b5-186">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell` .</span><span class="sxs-lookup"><span data-stu-id="561b5-186">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="561b5-187">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="561b5-187">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="561b5-188">Down load het Debian-pakket `powershell-lts_7.0.0-1.debian.9_amd64.deb` van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="561b5-188">Download the Debian package `powershell-lts_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="561b5-189">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="561b5-190">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="561b5-190">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="561b5-191">Debian 10</span><span class="sxs-lookup"><span data-stu-id="561b5-191">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-192">Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="561b5-192">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="561b5-193">Installatie via pakket opslagplaats-Debian 10</span><span class="sxs-lookup"><span data-stu-id="561b5-193">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="561b5-194">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-194">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="561b5-195">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="561b5-195">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="561b5-196">Installatie via direct downloaden-Debian 10</span><span class="sxs-lookup"><span data-stu-id="561b5-196">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="561b5-197">Down load het pakket tar. gz `powershell_7.0.0-linux-x64.tar.gz` van de pagina [releases][] op de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="561b5-197">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="561b5-198">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-198">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="561b5-199">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="561b5-199">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-200">Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="561b5-200">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="561b5-201">Installatie via direct downloaden-Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="561b5-201">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="561b5-202">Down load het pakket tar. gz `powershell-7.0.0-linux-alpine-x64.tar.gz` van de pagina [releases][] op de Alpine machine.</span><span class="sxs-lookup"><span data-stu-id="561b5-202">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="561b5-203">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-203">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="561b5-204">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="561b5-204">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-205">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="561b5-205">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="561b5-206">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="561b5-206">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="561b5-207">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-207">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="561b5-208">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="561b5-208">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="561b5-209">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="561b5-209">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="561b5-210">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="561b5-210">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="561b5-211">Gebruik [CentOS 7][]om het rpm-pakket te downloaden `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="561b5-211">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="561b5-212">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-212">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="561b5-213">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="561b5-213">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="561b5-214">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="561b5-214">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="561b5-216">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="561b5-216">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="561b5-217">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="561b5-217">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="561b5-218">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-218">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="561b5-219">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="561b5-219">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="561b5-220">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="561b5-220">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="561b5-221">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="561b5-221">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="561b5-222">Down load het RPM-pakket `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="561b5-222">Download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="561b5-223">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-223">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="561b5-224">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="561b5-224">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="561b5-225">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="561b5-225">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="561b5-226">openSUSE</span><span class="sxs-lookup"><span data-stu-id="561b5-226">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="561b5-227">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="561b5-227">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="561b5-228">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="561b5-228">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="561b5-229">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="561b5-229">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="561b5-230">Fedora</span><span class="sxs-lookup"><span data-stu-id="561b5-230">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-231">Fedora 28 wordt alleen ondersteund in Power shell 6,1 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="561b5-231">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-232">Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="561b5-232">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="561b5-233">Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="561b5-233">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="561b5-234">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-234">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="561b5-235">Installatie via direct downloaden-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="561b5-235">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="561b5-236">Down load het RPM-pakket `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="561b5-236">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="561b5-237">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="561b5-237">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="561b5-238">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="561b5-238">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="561b5-239">Installatie ongedaan maken-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="561b5-239">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="561b5-240">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="561b5-240">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-241">Arch-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="561b5-241">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="561b5-242">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="561b5-242">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="561b5-243">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="561b5-243">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="561b5-244">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="561b5-244">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="561b5-245">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="561b5-245">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="561b5-246">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="561b5-246">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="561b5-247">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of [Power shell in docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="561b5-247">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="561b5-249">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="561b5-249">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="561b5-250">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="561b5-250">Getting snapd</span></span>

<span data-ttu-id="561b5-251">`snapd`is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="561b5-251">`snapd` is required to run snaps.</span></span> <span data-ttu-id="561b5-252">Volg [deze instructies](https://docs.snapcraft.io/core/install) om te controleren of u hebt `snapd` geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="561b5-252">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="561b5-253">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="561b5-253">Installation via Snap</span></span>

<span data-ttu-id="561b5-254">Power shell voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="561b5-254">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="561b5-255">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="561b5-255">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="561b5-256">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="561b5-256">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="561b5-257">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="561b5-257">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="561b5-258">U kunt een upgrade activeren met `sudo snap refresh powershell` of `sudo snap refresh powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="561b5-258">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="561b5-259">Installatie ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="561b5-259">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="561b5-260">of</span><span class="sxs-lookup"><span data-stu-id="561b5-260">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="561b5-261">Kali</span><span class="sxs-lookup"><span data-stu-id="561b5-261">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-262">Kali-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="561b5-262">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="561b5-263">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="561b5-263">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="561b5-264">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="561b5-264">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="561b5-265">Raspbian</span><span class="sxs-lookup"><span data-stu-id="561b5-265">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="561b5-266">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="561b5-266">Raspbian support is experimental.</span></span>

<span data-ttu-id="561b5-267">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="561b5-267">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="561b5-268">CoreCLR en Power shell werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="561b5-268">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="561b5-269">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="561b5-269">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="561b5-270">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="561b5-270">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="561b5-271">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar het `pwsh` binaire bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="561b5-271">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="561b5-272">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="561b5-272">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="561b5-273">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="561b5-273">Installing Preview Releases</span></span>

<span data-ttu-id="561b5-274">Wanneer u een Power shell preview-release voor Linux installeert via een pakket opslagplaats, wordt de naam van het pakket gewijzigd van `powershell` in `powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="561b5-274">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="561b5-275">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="561b5-275">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="561b5-276">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="561b5-276">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="561b5-277">Distributie(s)</span><span class="sxs-lookup"><span data-stu-id="561b5-277">Distribution(s)</span></span> |            <span data-ttu-id="561b5-278">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="561b5-278">Stable Command</span></span>            |               <span data-ttu-id="561b5-279">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="561b5-279">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="561b5-280">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="561b5-280">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="561b5-281">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="561b5-281">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="561b5-282">Fedora</span><span class="sxs-lookup"><span data-stu-id="561b5-282">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="561b5-283">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="561b5-283">Install as a .NET Global tool</span></span>

<span data-ttu-id="561b5-284">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="561b5-284">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="561b5-285">Het hulp programma DotNet tool wordt toegevoegd `~/.dotnet/tools` aan de `PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="561b5-285">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="561b5-286">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `PATH` .</span><span class="sxs-lookup"><span data-stu-id="561b5-286">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="561b5-287">U moet Power shell kunnen starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="561b5-287">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="561b5-288">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="561b5-288">Binary Archives</span></span>

<span data-ttu-id="561b5-289">Er zijn binaire Power shell- `tar.gz` archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="561b5-289">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="561b5-290">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="561b5-290">Dependencies</span></span>

<span data-ttu-id="561b5-291">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="561b5-291">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="561b5-292">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="561b5-292">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="561b5-293">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="561b5-293">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="561b5-294">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="561b5-294">OS</span></span>                 | <span data-ttu-id="561b5-295">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="561b5-295">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="561b5-296">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="561b5-296">Ubuntu 16.04</span></span>       | <span data-ttu-id="561b5-297">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="561b5-297">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="561b5-298">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="561b5-298">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="561b5-299">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="561b5-299">Ubuntu 17.10</span></span>       | <span data-ttu-id="561b5-300">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="561b5-300">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="561b5-301">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="561b5-301">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="561b5-302">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="561b5-302">Ubuntu 18.04</span></span>       | <span data-ttu-id="561b5-303">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="561b5-303">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="561b5-304">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="561b5-304">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="561b5-305">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="561b5-305">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="561b5-306">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="561b5-306">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="561b5-307">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="561b5-307">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="561b5-308">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="561b5-308">Debian 9 (Stretch)</span></span> | <span data-ttu-id="561b5-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="561b5-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="561b5-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="561b5-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="561b5-311">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="561b5-311">CentOS 7</span></span> <br> <span data-ttu-id="561b5-312">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="561b5-312">Oracle Linux 7</span></span> <br> <span data-ttu-id="561b5-313">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="561b5-313">RHEL 7</span></span> | <span data-ttu-id="561b5-314">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="561b5-314">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="561b5-315">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="561b5-315">openSUSE 42.3</span></span> | <span data-ttu-id="561b5-316">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="561b5-316">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="561b5-317">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="561b5-317">openSUSE Leap 15</span></span> | <span data-ttu-id="561b5-318">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="561b5-318">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="561b5-319">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="561b5-319">Fedora 27</span></span> <br> <span data-ttu-id="561b5-320">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="561b5-320">Fedora 28</span></span> | <span data-ttu-id="561b5-321">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="561b5-321">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="561b5-322">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="561b5-322">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="561b5-323">Bijvoorbeeld, onze [Amazon Linux-dockerfile][amazon-dockerfile] installeert eerst afhankelijkheden en extraheert vervolgens het Linux- `tar.gz` Archief.</span><span class="sxs-lookup"><span data-stu-id="561b5-323">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="561b5-324">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="561b5-324">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="561b5-325">Linux</span><span class="sxs-lookup"><span data-stu-id="561b5-325">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="561b5-326">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="561b5-326">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="561b5-327">Paden</span><span class="sxs-lookup"><span data-stu-id="561b5-327">Paths</span></span>

- <span data-ttu-id="561b5-328">`$PSHOME` is `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="561b5-328">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="561b5-329">Gebruikers profielen worden gelezen van`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="561b5-329">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="561b5-330">Standaard profielen worden gelezen uit`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="561b5-330">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="561b5-331">Gebruikers modules worden gelezen uit`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="561b5-331">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="561b5-332">Gedeelde modules worden gelezen van`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="561b5-332">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="561b5-333">Standaard modules worden gelezen van`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="561b5-333">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="561b5-334">De PSReadLine-geschiedenis wordt vastgelegd in`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="561b5-334">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="561b5-335">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="561b5-335">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="561b5-336">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="561b5-336">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[shell]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
