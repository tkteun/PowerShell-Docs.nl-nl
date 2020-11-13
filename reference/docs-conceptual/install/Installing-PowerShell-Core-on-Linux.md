---
title: PowerShell installeren in Linux
description: Informatie over het installeren van Power shell op diverse Linux-distributies
ms.date: 11/11/2020
ms.openlocfilehash: c56708ab930a7285de92d657ed12182fc298fb73
ms.sourcegitcommit: e85e56d6614cbd30e01965a5cf03fb3f5ca78103
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "94589105"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="f14ba-103">PowerShell installeren in Linux</span><span class="sxs-lookup"><span data-stu-id="f14ba-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="f14ba-104">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="f14ba-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="f14ba-105">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="f14ba-106">Voer uit `pwsh-preview` Als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f14ba-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-107">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f14ba-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="f14ba-108">De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="f14ba-109">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="f14ba-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="f14ba-110">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="f14ba-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="f14ba-111">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks te implementeren met behulp van het Linux- [ `tar.gz` Archief][tar], maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="f14ba-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

<span data-ttu-id="f14ba-112">Officieel ondersteunde platform releases voor Power shell 7,1</span><span class="sxs-lookup"><span data-stu-id="f14ba-112">Officially supported platform releases for PowerShell 7.1</span></span>

- <span data-ttu-id="f14ba-113">Ubuntu 16.04/18.04/20.04 (inclusief ARM64)</span><span class="sxs-lookup"><span data-stu-id="f14ba-113">Ubuntu 16.04/18.04/20.04 (including ARM64)</span></span>
- <span data-ttu-id="f14ba-114">Ubuntu 19,10 (via snap package)</span><span class="sxs-lookup"><span data-stu-id="f14ba-114">Ubuntu 19.10 (via Snap package)</span></span>
- <span data-ttu-id="f14ba-115">Debian 9/10</span><span class="sxs-lookup"><span data-stu-id="f14ba-115">Debian 9/10</span></span>
- <span data-ttu-id="f14ba-116">CentOS en RHEL 7/8</span><span class="sxs-lookup"><span data-stu-id="f14ba-116">CentOS and RHEL 7/8</span></span>
- <span data-ttu-id="f14ba-117">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="f14ba-117">Fedora 30</span></span>
- <span data-ttu-id="f14ba-118">Alpiene 3.11 + (inclusief ARM64)</span><span class="sxs-lookup"><span data-stu-id="f14ba-118">Alpine 3.11+ (including ARM64)</span></span>

<span data-ttu-id="f14ba-119">Officieel ondersteunde platform releases voor Power shell 7,0</span><span class="sxs-lookup"><span data-stu-id="f14ba-119">Officially supported platform releases for PowerShell 7.0</span></span>

- <span data-ttu-id="f14ba-120">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f14ba-120">Ubuntu 16.04</span></span>
- <span data-ttu-id="f14ba-121">Ubuntu 18,04 en 20,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-121">Ubuntu 18.04 and 20.04</span></span>
- <span data-ttu-id="f14ba-122">Debian 8</span><span class="sxs-lookup"><span data-stu-id="f14ba-122">Debian 8</span></span>
- <span data-ttu-id="f14ba-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="f14ba-123">Debian 9</span></span>
- <span data-ttu-id="f14ba-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="f14ba-124">Debian 10</span></span>
- <span data-ttu-id="f14ba-125">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-125">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="f14ba-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-126">CentOS 7</span></span>
- <span data-ttu-id="f14ba-127">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-127">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="f14ba-128">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="f14ba-128">Fedora 28</span></span>
- <span data-ttu-id="f14ba-129">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="f14ba-129">Fedora 29</span></span>
- <span data-ttu-id="f14ba-130">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="f14ba-130">Fedora 30</span></span>
- <span data-ttu-id="f14ba-131">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="f14ba-131">openSUSE 42.3</span></span>
- <span data-ttu-id="f14ba-132">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="f14ba-132">openSUSE Leap 15</span></span>

<span data-ttu-id="f14ba-133">Door de Community ondersteunde releases</span><span class="sxs-lookup"><span data-stu-id="f14ba-133">Community supported releases</span></span>

- <span data-ttu-id="f14ba-134">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-134">Ubuntu 18.10</span></span>
- <span data-ttu-id="f14ba-135">Ubuntu 19,10 en 20,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-135">Ubuntu 19.10 and 20.10</span></span>
- <span data-ttu-id="f14ba-136">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="f14ba-136">Arch Linux</span></span>
- <span data-ttu-id="f14ba-137">Kali</span><span class="sxs-lookup"><span data-stu-id="f14ba-137">Kali</span></span>
- <span data-ttu-id="f14ba-138">Raspbian (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="f14ba-138">Raspbian (experimental)</span></span>

<span data-ttu-id="f14ba-139">Alternatieve installatie methoden</span><span class="sxs-lookup"><span data-stu-id="f14ba-139">Alternate install methods</span></span>

- <span data-ttu-id="f14ba-140">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="f14ba-140">Snap Package</span></span>
- <span data-ttu-id="f14ba-141">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="f14ba-141">Binary Archives</span></span>
- <span data-ttu-id="f14ba-142">Hulp programma .NET Global</span><span class="sxs-lookup"><span data-stu-id="f14ba-142">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="f14ba-143">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f14ba-143">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="f14ba-144">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-144">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="f14ba-145">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-145">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="f14ba-146">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f14ba-146">The preferred method is as follows:</span></span>

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

<span data-ttu-id="f14ba-147">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-147">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="f14ba-148">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-148">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="f14ba-149">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-149">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="f14ba-150">Down load het Debian-pakket `powershell_7.1.0-1.ubuntu.16.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-150">Download the Debian package `powershell_7.1.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="f14ba-151">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-151">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="f14ba-152">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="f14ba-152">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="f14ba-153">Met de volgende opdracht worden `apt-get install -f` deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="f14ba-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="f14ba-154">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-154">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="f14ba-155">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="f14ba-155">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="f14ba-156">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-156">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="f14ba-157">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="f14ba-158">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f14ba-158">The preferred method is as follows:</span></span>

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

<span data-ttu-id="f14ba-159">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="f14ba-160">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-160">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="f14ba-161">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-161">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="f14ba-162">Down load het Debian-pakket `powershell_7.1.0-1.ubuntu.18.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-162">Download the Debian package `powershell_7.1.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="f14ba-163">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-163">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="f14ba-164">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="f14ba-164">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="f14ba-165">Met de volgende opdracht worden `apt-get install -f` deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="f14ba-165">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="f14ba-166">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-166">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a><span data-ttu-id="f14ba-167">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="f14ba-167">Ubuntu 20.04</span></span>

### <a name="installation-via-package-repository---ubuntu-2004"></a><span data-ttu-id="f14ba-168">Installatie via pakket opslagplaats-Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-168">Installation via Package Repository - Ubuntu 20.04</span></span>

<span data-ttu-id="f14ba-169">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-169">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="f14ba-170">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f14ba-170">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
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

<span data-ttu-id="f14ba-171">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="f14ba-172">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-172">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-2004"></a><span data-ttu-id="f14ba-173">Installatie via direct downloaden-Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-173">Installation via Direct Download - Ubuntu 20.04</span></span>

<span data-ttu-id="f14ba-174">Down load het Debian-pakket `powershell_7.1.0-1.ubuntu.20.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-174">Download the Debian package `powershell_7.1.0-1.ubuntu.20.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="f14ba-175">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.20.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="f14ba-176">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="f14ba-176">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="f14ba-177">Met de volgende opdracht worden `apt-get install -f` deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="f14ba-177">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-2004"></a><span data-ttu-id="f14ba-178">Installatie ongedaan maken-Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="f14ba-178">Uninstallation - Ubuntu 20.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="f14ba-179">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-179">Ubuntu 18.10</span></span>

<span data-ttu-id="f14ba-180">De installatie wordt ondersteund via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-180">Installation is supported via `snapd`.</span></span> <span data-ttu-id="f14ba-181">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="f14ba-181">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-182">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="f14ba-182">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1910-and-2010"></a><span data-ttu-id="f14ba-183">Ubuntu 19,10 en 20,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-183">Ubuntu 19.10 and 20.10</span></span>

<span data-ttu-id="f14ba-184">De installatie wordt ondersteund via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-184">Installation is supported via `snapd`.</span></span> <span data-ttu-id="f14ba-185">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="f14ba-185">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-186">Ubuntu 19,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="f14ba-186">Ubuntu 19.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="f14ba-187">Debian 8</span><span class="sxs-lookup"><span data-stu-id="f14ba-187">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="f14ba-188">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="f14ba-188">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="f14ba-189">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-189">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="f14ba-190">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f14ba-190">The preferred method is as follows:</span></span>

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

<span data-ttu-id="f14ba-191">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-191">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="f14ba-192">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-192">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="f14ba-193">Debian 9</span><span class="sxs-lookup"><span data-stu-id="f14ba-193">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="f14ba-194">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="f14ba-194">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="f14ba-195">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-195">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="f14ba-196">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f14ba-196">The preferred method is as follows:</span></span>

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

<span data-ttu-id="f14ba-197">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-197">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="f14ba-198">Na de registratie kunt u Power shell bijwerken met `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-198">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="f14ba-199">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="f14ba-199">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="f14ba-200">Down load het Debian-pakket `powershell_7.1.0-1.debian.9_amd64.deb` van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-200">Download the Debian package `powershell_7.1.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="f14ba-201">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-201">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="f14ba-202">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="f14ba-202">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="f14ba-203">Debian 10</span><span class="sxs-lookup"><span data-stu-id="f14ba-203">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-204">Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-204">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="f14ba-205">Installatie via pakket opslagplaats-Debian 10</span><span class="sxs-lookup"><span data-stu-id="f14ba-205">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="f14ba-206">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-206">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="f14ba-207">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f14ba-207">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="f14ba-208">Installatie via direct downloaden-Debian 10</span><span class="sxs-lookup"><span data-stu-id="f14ba-208">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="f14ba-209">Down load het pakket tar. gz `powershell-7.1.0-linux-x64.tar.gz` van de pagina [releases][] op de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="f14ba-209">Download the tar.gz package `powershell-7.1.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="f14ba-210">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-210">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="f14ba-211">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-211">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-212">Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-212">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="f14ba-213">Installatie via direct downloaden-Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-213">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="f14ba-214">Down load het pakket tar. gz `powershell-7.1.0-linux-alpine-x64.tar.gz` van de pagina [releases][] op de Alpine machine.</span><span class="sxs-lookup"><span data-stu-id="f14ba-214">Download the tar.gz package `powershell-7.1.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="f14ba-215">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-215">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="f14ba-216">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-216">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-217">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="f14ba-217">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="f14ba-218">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-218">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="f14ba-219">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-219">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="f14ba-220">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-220">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="f14ba-221">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-221">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="f14ba-222">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-222">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="f14ba-223">Gebruik [CentOS 7][]om het rpm-pakket te downloaden `powershell-7.1.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-223">Using [CentOS 7][], download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="f14ba-224">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-224">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f14ba-225">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="f14ba-225">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="f14ba-226">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-226">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f14ba-228">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-228">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f14ba-229">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-229">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="f14ba-230">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-230">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="f14ba-231">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="f14ba-231">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="f14ba-232">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-232">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f14ba-233">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-233">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="f14ba-234">Down load het RPM-pakket `powershell-7.1.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="f14ba-234">Download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="f14ba-235">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-235">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f14ba-236">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="f14ba-236">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="f14ba-237">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-237">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="f14ba-238">openSUSE</span><span class="sxs-lookup"><span data-stu-id="f14ba-238">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="f14ba-239">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="f14ba-239">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="f14ba-240">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="f14ba-240">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="f14ba-241">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="f14ba-241">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="f14ba-242">Fedora</span><span class="sxs-lookup"><span data-stu-id="f14ba-242">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-243">Fedora 28 wordt alleen ondersteund in Power shell 6,1 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-243">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-244">Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="f14ba-244">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="f14ba-245">Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="f14ba-245">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="f14ba-246">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-246">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="f14ba-247">Installatie via direct downloaden-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="f14ba-247">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="f14ba-248">Down load het RPM-pakket `powershell-7.1.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="f14ba-248">Download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="f14ba-249">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="f14ba-249">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="f14ba-250">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="f14ba-250">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="f14ba-251">Installatie ongedaan maken-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="f14ba-251">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="f14ba-252">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="f14ba-252">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-253">Arch-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="f14ba-253">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="f14ba-254">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="f14ba-254">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="f14ba-255">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="f14ba-255">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="f14ba-256">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="f14ba-256">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="f14ba-257">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="f14ba-257">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="f14ba-258">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="f14ba-258">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="f14ba-259">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of [Power shell in docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="f14ba-259">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="f14ba-261">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="f14ba-261">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="f14ba-262">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="f14ba-262">Getting snapd</span></span>

<span data-ttu-id="f14ba-263">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="f14ba-263">`snapd` is required to run snaps.</span></span> <span data-ttu-id="f14ba-264">Volg [deze instructies](https://docs.snapcraft.io/core/install) om te controleren of u hebt `snapd` geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="f14ba-264">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="f14ba-265">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="f14ba-265">Installation via Snap</span></span>

<span data-ttu-id="f14ba-266">Power shell voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="f14ba-266">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="f14ba-267">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f14ba-267">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="f14ba-268">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="f14ba-268">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="f14ba-269">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="f14ba-269">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="f14ba-270">U kunt een upgrade activeren met `sudo snap refresh powershell` of `sudo snap refresh powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-270">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="f14ba-271">Installatie ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="f14ba-271">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="f14ba-272">of</span><span class="sxs-lookup"><span data-stu-id="f14ba-272">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="f14ba-273">Kali</span><span class="sxs-lookup"><span data-stu-id="f14ba-273">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-274">Kali-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="f14ba-274">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="f14ba-275">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="f14ba-275">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="f14ba-276">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="f14ba-276">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="f14ba-277">Raspbian</span><span class="sxs-lookup"><span data-stu-id="f14ba-277">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="f14ba-278">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="f14ba-278">Raspbian support is experimental.</span></span>

<span data-ttu-id="f14ba-279">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="f14ba-279">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="f14ba-280">CoreCLR en Power shell werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="f14ba-280">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="f14ba-281">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="f14ba-281">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="f14ba-282">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="f14ba-282">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="f14ba-283">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar het `pwsh` binaire bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="f14ba-283">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="f14ba-284">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="f14ba-284">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="f14ba-285">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="f14ba-285">Installing Preview Releases</span></span>

<span data-ttu-id="f14ba-286">Wanneer u een Power shell preview-release voor Linux installeert via een pakket opslagplaats, wordt de naam van het pakket gewijzigd van `powershell` in `powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-286">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="f14ba-287">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="f14ba-287">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="f14ba-288">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="f14ba-288">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="f14ba-289">Distributie(s)</span><span class="sxs-lookup"><span data-stu-id="f14ba-289">Distribution(s)</span></span> |            <span data-ttu-id="f14ba-290">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="f14ba-290">Stable Command</span></span>            |               <span data-ttu-id="f14ba-291">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="f14ba-291">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="f14ba-292">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="f14ba-292">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="f14ba-293">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="f14ba-293">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="f14ba-294">Fedora</span><span class="sxs-lookup"><span data-stu-id="f14ba-294">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="f14ba-295">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="f14ba-295">Install as a .NET Global tool</span></span>

<span data-ttu-id="f14ba-296">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="f14ba-296">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="f14ba-297">Het hulp programma DotNet tool wordt toegevoegd `~/.dotnet/tools` aan de `PATH` omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="f14ba-297">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="f14ba-298">De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `PATH` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-298">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="f14ba-299">U moet Power shell kunnen starten vanuit een nieuwe shell door te typen `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="f14ba-299">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="f14ba-300">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="f14ba-300">Binary Archives</span></span>

<span data-ttu-id="f14ba-301">Er zijn binaire Power shell- `tar.gz` archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="f14ba-301">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="f14ba-302">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="f14ba-302">Dependencies</span></span>

<span data-ttu-id="f14ba-303">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="f14ba-303">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="f14ba-304">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="f14ba-304">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="f14ba-305">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="f14ba-305">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="f14ba-306">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="f14ba-306">OS</span></span>                 | <span data-ttu-id="f14ba-307">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="f14ba-307">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="f14ba-308">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="f14ba-308">Ubuntu 16.04</span></span>       | <span data-ttu-id="f14ba-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="f14ba-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f14ba-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="f14ba-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="f14ba-311">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="f14ba-311">Ubuntu 17.10</span></span>       | <span data-ttu-id="f14ba-312">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="f14ba-312">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f14ba-313">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="f14ba-313">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="f14ba-314">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="f14ba-314">Ubuntu 18.04</span></span>       | <span data-ttu-id="f14ba-315">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="f14ba-315">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f14ba-316">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="f14ba-316">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="f14ba-317">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="f14ba-317">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="f14ba-318">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="f14ba-318">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f14ba-319">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="f14ba-319">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="f14ba-320">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="f14ba-320">Debian 9 (Stretch)</span></span> | <span data-ttu-id="f14ba-321">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="f14ba-321">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="f14ba-322">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="f14ba-322">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="f14ba-323">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-323">CentOS 7</span></span> <br> <span data-ttu-id="f14ba-324">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-324">Oracle Linux 7</span></span> <br> <span data-ttu-id="f14ba-325">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="f14ba-325">RHEL 7</span></span> | <span data-ttu-id="f14ba-326">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="f14ba-326">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="f14ba-327">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="f14ba-327">openSUSE 42.3</span></span> | <span data-ttu-id="f14ba-328">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="f14ba-328">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="f14ba-329">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="f14ba-329">openSUSE Leap 15</span></span> | <span data-ttu-id="f14ba-330">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="f14ba-330">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="f14ba-331">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="f14ba-331">Fedora 27</span></span> <br> <span data-ttu-id="f14ba-332">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="f14ba-332">Fedora 28</span></span> | <span data-ttu-id="f14ba-333">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="f14ba-333">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="f14ba-334">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="f14ba-334">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="f14ba-335">Bijvoorbeeld, onze [Amazon Linux-dockerfile][amazon-dockerfile] installeert eerst afhankelijkheden en extraheert vervolgens het Linux- `tar.gz` Archief.</span><span class="sxs-lookup"><span data-stu-id="f14ba-335">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="f14ba-336">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="f14ba-336">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="f14ba-337">Linux</span><span class="sxs-lookup"><span data-stu-id="f14ba-337">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="f14ba-338">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="f14ba-338">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="f14ba-339">Paden</span><span class="sxs-lookup"><span data-stu-id="f14ba-339">Paths</span></span>

- <span data-ttu-id="f14ba-340">`$PSHOME` is `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="f14ba-340">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="f14ba-341">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="f14ba-341">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="f14ba-342">Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="f14ba-342">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="f14ba-343">Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="f14ba-343">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="f14ba-344">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="f14ba-344">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="f14ba-345">Standaard modules worden gelezen van `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="f14ba-345">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="f14ba-346">De PSReadLine-geschiedenis wordt vastgelegd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="f14ba-346">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="f14ba-347">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="f14ba-347">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="f14ba-348">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="f14ba-348">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="f14ba-349">Ondersteuning voor installatie</span><span class="sxs-lookup"><span data-stu-id="f14ba-349">Installation support</span></span>

<span data-ttu-id="f14ba-350">Micro soft ondersteunt de installatie methoden in dit document.</span><span class="sxs-lookup"><span data-stu-id="f14ba-350">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="f14ba-351">Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen.</span><span class="sxs-lookup"><span data-stu-id="f14ba-351">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="f14ba-352">Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="f14ba-352">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[shell]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
