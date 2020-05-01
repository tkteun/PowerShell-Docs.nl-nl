---
title: PowerShell installeren in Linux
description: Informatie over het installeren van Power shell op diverse Linux-distributies
ms.date: 03/09/2020
ms.openlocfilehash: 6ad637bd30e5e40ccc9532bae6f1171ecf79734a
ms.sourcegitcommit: e0a737961280026832cff9c658ed1468dc904e80
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605846"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="0ed15-103">PowerShell installeren in Linux</span><span class="sxs-lookup"><span data-stu-id="0ed15-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="0ed15-104">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="0ed15-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="0ed15-105">Nadat het pakket is geïnstalleerd, voert `pwsh` u uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="0ed15-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="0ed15-106">Voer `pwsh-preview` uit als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="0ed15-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-107">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="0ed15-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="0ed15-108">De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="0ed15-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="0ed15-109">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="0ed15-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="0ed15-110">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="0ed15-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="0ed15-111">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks [ `tar.gz` ][tar]te implementeren met behulp van het Linux-archief, maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="0ed15-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="0ed15-112">Officieel ondersteunde releases</span><span class="sxs-lookup"><span data-stu-id="0ed15-112">Officially supported releases</span></span>

- <span data-ttu-id="0ed15-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0ed15-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="0ed15-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0ed15-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="0ed15-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="0ed15-115">Debian 8</span></span>
- <span data-ttu-id="0ed15-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="0ed15-116">Debian 9</span></span>
- <span data-ttu-id="0ed15-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="0ed15-117">Debian 10</span></span>
- <span data-ttu-id="0ed15-118">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="0ed15-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="0ed15-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-119">CentOS 7</span></span>
- <span data-ttu-id="0ed15-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="0ed15-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0ed15-121">Fedora 28</span></span>
- <span data-ttu-id="0ed15-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="0ed15-122">Fedora 29</span></span>
- <span data-ttu-id="0ed15-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="0ed15-123">Fedora 30</span></span>
- <span data-ttu-id="0ed15-124">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="0ed15-124">openSUSE 42.3</span></span>
- <span data-ttu-id="0ed15-125">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="0ed15-125">openSUSE Leap 15</span></span>

<span data-ttu-id="0ed15-126">Door de Community ondersteunde releases</span><span class="sxs-lookup"><span data-stu-id="0ed15-126">Community supported releases</span></span>

- <span data-ttu-id="0ed15-127">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="0ed15-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="0ed15-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="0ed15-129">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="0ed15-129">Arch Linux</span></span>
- <span data-ttu-id="0ed15-130">Kali</span><span class="sxs-lookup"><span data-stu-id="0ed15-130">Kali</span></span>
- <span data-ttu-id="0ed15-131">Raspbian (experimenteel)</span><span class="sxs-lookup"><span data-stu-id="0ed15-131">Raspbian (experimental)</span></span>

<span data-ttu-id="0ed15-132">Alternatieve installatie methoden</span><span class="sxs-lookup"><span data-stu-id="0ed15-132">Alternate install methods</span></span>

- <span data-ttu-id="0ed15-133">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="0ed15-133">Snap Package</span></span>
- <span data-ttu-id="0ed15-134">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="0ed15-134">Binary Archives</span></span>
- <span data-ttu-id="0ed15-135">Hulp programma .NET Global</span><span class="sxs-lookup"><span data-stu-id="0ed15-135">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="0ed15-136">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0ed15-136">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="0ed15-137">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-137">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="0ed15-138">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-138">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="0ed15-139">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="0ed15-139">The preferred method is as follows:</span></span>

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

<span data-ttu-id="0ed15-140">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="0ed15-140">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="0ed15-141">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="0ed15-141">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="0ed15-142">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-142">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="0ed15-143">Down load het Debian `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` -pakket van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-143">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0ed15-144">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-144">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0ed15-145">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="0ed15-145">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="0ed15-146">Met de volgende opdracht `apt-get install -f` worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="0ed15-146">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="0ed15-147">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-147">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="0ed15-148">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0ed15-148">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="0ed15-149">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-149">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="0ed15-150">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-150">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="0ed15-151">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="0ed15-151">The preferred method is as follows:</span></span>

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

<span data-ttu-id="0ed15-152">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="0ed15-152">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="0ed15-153">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="0ed15-153">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="0ed15-154">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-154">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="0ed15-155">Down load het Debian `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` -pakket van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-155">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="0ed15-156">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-156">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="0ed15-157">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="0ed15-157">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="0ed15-158">Met de volgende opdracht `apt-get install -f` worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="0ed15-158">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="0ed15-159">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-159">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="0ed15-160">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="0ed15-160">Ubuntu 18.10</span></span>

<span data-ttu-id="0ed15-161">De installatie wordt ondersteund `snapd`via.</span><span class="sxs-lookup"><span data-stu-id="0ed15-161">Installation is supported via `snapd`.</span></span> <span data-ttu-id="0ed15-162">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="0ed15-162">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-163">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="0ed15-163">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="0ed15-164">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="0ed15-164">Ubuntu 19.04</span></span>

<span data-ttu-id="0ed15-165">De installatie wordt ondersteund `snapd`via.</span><span class="sxs-lookup"><span data-stu-id="0ed15-165">Installation is supported via `snapd`.</span></span> <span data-ttu-id="0ed15-166">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="0ed15-166">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-167">Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="0ed15-167">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="0ed15-168">Debian 8</span><span class="sxs-lookup"><span data-stu-id="0ed15-168">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="0ed15-169">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="0ed15-169">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="0ed15-170">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-170">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="0ed15-171">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="0ed15-171">The preferred method is as follows:</span></span>

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

<span data-ttu-id="0ed15-172">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="0ed15-172">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="0ed15-173">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="0ed15-173">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="0ed15-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="0ed15-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="0ed15-175">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="0ed15-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="0ed15-176">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-176">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="0ed15-177">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="0ed15-177">The preferred method is as follows:</span></span>

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

<span data-ttu-id="0ed15-178">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="0ed15-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="0ed15-179">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="0ed15-179">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="0ed15-180">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="0ed15-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="0ed15-181">Down load het Debian `powershell-lts_7.0.0-1.debian.9_amd64.deb` -pakket van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-181">Download the Debian package `powershell-lts_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0ed15-182">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="0ed15-183">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="0ed15-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="0ed15-184">Debian 10</span><span class="sxs-lookup"><span data-stu-id="0ed15-184">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-185">Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-185">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="0ed15-186">Installatie via pakket opslagplaats-Debian 10</span><span class="sxs-lookup"><span data-stu-id="0ed15-186">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="0ed15-187">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-187">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="0ed15-188">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="0ed15-188">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="0ed15-189">Installatie via direct downloaden-Debian 10</span><span class="sxs-lookup"><span data-stu-id="0ed15-189">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="0ed15-190">Down load het pakket `powershell_7.0.0-linux-x64.tar.gz` tar. gz van de pagina [releases][] op de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="0ed15-190">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="0ed15-191">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-191">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="0ed15-192">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="0ed15-192">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-193">Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-193">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="0ed15-194">Installatie via direct downloaden-Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="0ed15-194">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="0ed15-195">Down load het pakket `powershell-7.0.0-linux-alpine-x64.tar.gz` tar. gz van de pagina [releases][] op de Alpine machine.</span><span class="sxs-lookup"><span data-stu-id="0ed15-195">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="0ed15-196">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-196">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="0ed15-197">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-197">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-198">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="0ed15-198">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="0ed15-199">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-199">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="0ed15-200">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-200">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0ed15-201">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="0ed15-201">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="0ed15-202">Na de registratie kunt u Power shell bijwerken `sudo yum update powershell`met.</span><span class="sxs-lookup"><span data-stu-id="0ed15-202">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="0ed15-203">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-203">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="0ed15-204">Gebruik [CentOS 7][]om het rpm-pakket `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` te downloaden van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-204">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="0ed15-205">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-205">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0ed15-206">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="0ed15-206">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="0ed15-207">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-207">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0ed15-209">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-209">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0ed15-210">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-210">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0ed15-211">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="0ed15-212">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="0ed15-212">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="0ed15-213">Na de registratie kunt u Power shell bijwerken `sudo yum update powershell`met.</span><span class="sxs-lookup"><span data-stu-id="0ed15-213">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0ed15-214">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-214">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="0ed15-215">Down load het RPM `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` -pakket van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="0ed15-215">Download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="0ed15-216">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-216">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0ed15-217">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="0ed15-217">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="0ed15-218">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-218">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="0ed15-219">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0ed15-219">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="0ed15-220">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="0ed15-220">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="0ed15-221">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="0ed15-221">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="0ed15-222">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="0ed15-222">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="0ed15-223">Fedora</span><span class="sxs-lookup"><span data-stu-id="0ed15-223">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-224">Fedora 28 wordt alleen ondersteund in Power shell 6,1 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-224">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-225">Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="0ed15-225">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="0ed15-226">Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="0ed15-226">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="0ed15-227">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-227">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="0ed15-228">Installatie via direct downloaden-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="0ed15-228">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="0ed15-229">Down load het RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` -pakket van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="0ed15-229">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="0ed15-230">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="0ed15-230">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="0ed15-231">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="0ed15-231">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="0ed15-232">Installatie ongedaan maken-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="0ed15-232">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="0ed15-233">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="0ed15-233">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-234">Arch-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="0ed15-234">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="0ed15-235">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="0ed15-235">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="0ed15-236">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="0ed15-236">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="0ed15-237">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="0ed15-237">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="0ed15-238">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="0ed15-238">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="0ed15-239">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="0ed15-239">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="0ed15-240">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of [Power shell in docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="0ed15-240">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="0ed15-242">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="0ed15-242">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="0ed15-243">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="0ed15-243">Getting snapd</span></span>

<span data-ttu-id="0ed15-244">`snapd`is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="0ed15-244">`snapd` is required to run snaps.</span></span> <span data-ttu-id="0ed15-245">Volg [deze instructies](https://docs.snapcraft.io/core/install) om te controleren of u `snapd` hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="0ed15-245">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="0ed15-246">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="0ed15-246">Installation via Snap</span></span>

<span data-ttu-id="0ed15-247">Power shell voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="0ed15-247">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="0ed15-248">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="0ed15-248">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="0ed15-249">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="0ed15-249">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="0ed15-250">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="0ed15-250">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="0ed15-251">U kunt een upgrade activeren met `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="0ed15-251">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="0ed15-252">Installatie ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="0ed15-252">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="0ed15-253">of</span><span class="sxs-lookup"><span data-stu-id="0ed15-253">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="0ed15-254">Kali</span><span class="sxs-lookup"><span data-stu-id="0ed15-254">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-255">Kali-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="0ed15-255">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="0ed15-256">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="0ed15-256">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="0ed15-257">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="0ed15-257">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="0ed15-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="0ed15-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="0ed15-259">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="0ed15-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="0ed15-260">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="0ed15-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="0ed15-261">CoreCLR en Power shell werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="0ed15-261">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="0ed15-262">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="0ed15-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="0ed15-263">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="0ed15-263">Installation - Raspbian</span></span>

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

<span data-ttu-id="0ed15-264">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar het `pwsh` binaire bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="0ed15-264">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="0ed15-265">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="0ed15-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="0ed15-266">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="0ed15-266">Installing Preview Releases</span></span>

<span data-ttu-id="0ed15-267">Wanneer u een Power shell preview-release voor Linux installeert via een pakket opslagplaats, wordt de `powershell` naam `powershell-preview`van het pakket gewijzigd van in.</span><span class="sxs-lookup"><span data-stu-id="0ed15-267">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="0ed15-268">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="0ed15-268">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="0ed15-269">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="0ed15-269">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="0ed15-270">Distributie(s)</span><span class="sxs-lookup"><span data-stu-id="0ed15-270">Distribution(s)</span></span> |            <span data-ttu-id="0ed15-271">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="0ed15-271">Stable Command</span></span>            |               <span data-ttu-id="0ed15-272">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="0ed15-272">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="0ed15-273">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="0ed15-273">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="0ed15-274">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="0ed15-274">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="0ed15-275">Fedora</span><span class="sxs-lookup"><span data-stu-id="0ed15-275">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="0ed15-276">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="0ed15-276">Install as a .NET Global tool</span></span>

<span data-ttu-id="0ed15-277">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="0ed15-277">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="0ed15-278">Het hulp programma DotNet tool `~/.dotnet/tools` wordt toegevoegd `PATH` aan de omgevings variabele.</span><span class="sxs-lookup"><span data-stu-id="0ed15-278">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="0ed15-279">De momenteel actieve shell beschikt echter niet over de bijgewerkte `PATH`versie.</span><span class="sxs-lookup"><span data-stu-id="0ed15-279">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="0ed15-280">U moet Power shell kunnen starten vanuit een nieuwe shell door te typen `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="0ed15-280">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="0ed15-281">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="0ed15-281">Binary Archives</span></span>

<span data-ttu-id="0ed15-282">Er zijn `tar.gz` binaire Power shell-archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="0ed15-282">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="0ed15-283">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="0ed15-283">Dependencies</span></span>

<span data-ttu-id="0ed15-284">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="0ed15-284">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="0ed15-285">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="0ed15-285">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="0ed15-286">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="0ed15-286">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="0ed15-287">OS</span><span class="sxs-lookup"><span data-stu-id="0ed15-287">OS</span></span>                 | <span data-ttu-id="0ed15-288">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="0ed15-288">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="0ed15-289">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="0ed15-289">Ubuntu 16.04</span></span>       | <span data-ttu-id="0ed15-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="0ed15-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0ed15-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="0ed15-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="0ed15-292">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="0ed15-292">Ubuntu 17.10</span></span>       | <span data-ttu-id="0ed15-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="0ed15-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0ed15-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="0ed15-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="0ed15-295">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="0ed15-295">Ubuntu 18.04</span></span>       | <span data-ttu-id="0ed15-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="0ed15-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0ed15-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="0ed15-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="0ed15-298">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="0ed15-298">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="0ed15-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="0ed15-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0ed15-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="0ed15-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="0ed15-301">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="0ed15-301">Debian 9 (Stretch)</span></span> | <span data-ttu-id="0ed15-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="0ed15-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="0ed15-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="0ed15-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="0ed15-304">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-304">CentOS 7</span></span> <br> <span data-ttu-id="0ed15-305">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-305">Oracle Linux 7</span></span> <br> <span data-ttu-id="0ed15-306">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="0ed15-306">RHEL 7</span></span> | <span data-ttu-id="0ed15-307">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="0ed15-307">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="0ed15-308">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="0ed15-308">openSUSE 42.3</span></span> | <span data-ttu-id="0ed15-309">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="0ed15-309">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="0ed15-310">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="0ed15-310">openSUSE Leap 15</span></span> | <span data-ttu-id="0ed15-311">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="0ed15-311">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="0ed15-312">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="0ed15-312">Fedora 27</span></span> <br> <span data-ttu-id="0ed15-313">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="0ed15-313">Fedora 28</span></span> | <span data-ttu-id="0ed15-314">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="0ed15-314">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="0ed15-315">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="0ed15-315">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="0ed15-316">Bijvoorbeeld, onze [Amazon Linux-dockerfile][amazon-dockerfile] installeert eerst afhankelijkheden en extraheert vervolgens het Linux `tar.gz` -archief.</span><span class="sxs-lookup"><span data-stu-id="0ed15-316">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="0ed15-317">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="0ed15-317">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="0ed15-318">Linux</span><span class="sxs-lookup"><span data-stu-id="0ed15-318">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="0ed15-319">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="0ed15-319">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="0ed15-320">Paden</span><span class="sxs-lookup"><span data-stu-id="0ed15-320">Paths</span></span>

- <span data-ttu-id="0ed15-321">`$PSHOME` is `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="0ed15-321">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="0ed15-322">Gebruikers profielen worden gelezen van`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0ed15-322">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="0ed15-323">Standaard profielen worden gelezen uit`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0ed15-323">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="0ed15-324">Gebruikers modules worden gelezen uit`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0ed15-324">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="0ed15-325">Gedeelde modules worden gelezen van`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0ed15-325">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="0ed15-326">Standaard modules worden gelezen van`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="0ed15-326">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="0ed15-327">De PSReadLine-geschiedenis wordt vastgelegd in`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0ed15-327">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0ed15-328">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="0ed15-328">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0ed15-329">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="0ed15-329">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[shell]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
