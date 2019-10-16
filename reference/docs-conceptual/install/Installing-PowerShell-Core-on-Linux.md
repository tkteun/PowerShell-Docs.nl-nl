---
title: PowerShell Core in Linux installeren
description: Informatie over het installeren van Power shell Core op diverse Linux-distributies
ms.date: 07/19/2019
ms.openlocfilehash: fc5a278f0fc10733a0d60fb856d0400332ba2719
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350197"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="1210d-103">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="1210d-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="1210d-104">Ondersteunt [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE schrikkel 15 ][opensuse], [Fedora 27][fedora], [Fedora 28][fedora]en [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="1210d-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="1210d-105">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="1210d-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="1210d-106">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks te implementeren met behulp van het Linux [`tar.gz`-archief][tar], maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="1210d-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="1210d-107">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="1210d-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="1210d-108">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="1210d-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="1210d-109">Voer `pwsh-preview` uit als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1210d-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="1210d-110">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="1210d-110">Installing Preview Releases</span></span>

<span data-ttu-id="1210d-111">Wanneer u een Power shell core preview-versie voor Linux installeert via een pakket opslagplaats, wordt de naam van het pakket gewijzigd van `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="1210d-111">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="1210d-112">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="1210d-112">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="1210d-113">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="1210d-113">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="1210d-114">Distributie (s)</span><span class="sxs-lookup"><span data-stu-id="1210d-114">Distribution(s)</span></span>|<span data-ttu-id="1210d-115">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="1210d-115">Stable Command</span></span> | <span data-ttu-id="1210d-116">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="1210d-116">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="1210d-117">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="1210d-117">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="1210d-118">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="1210d-118">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="1210d-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="1210d-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="1210d-120">Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1210d-120">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="1210d-121">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1210d-121">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="1210d-122">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-122">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1210d-123">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1210d-123">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1210d-124">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="1210d-124">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1210d-125">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="1210d-125">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="1210d-126">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1210d-126">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="1210d-127">Down load het Debian-pakket `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="1210d-127">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1210d-128">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-128">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1210d-129">De `dpkg -i`-opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="1210d-129">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="1210d-130">Met de volgende opdracht, `apt-get install -f`, worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="1210d-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="1210d-131">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1210d-131">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="1210d-132">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1210d-132">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="1210d-133">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1210d-133">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="1210d-134">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-134">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1210d-135">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1210d-135">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1210d-136">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="1210d-136">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1210d-137">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="1210d-137">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="1210d-138">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1210d-138">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="1210d-139">Down load het Debian-pakket `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="1210d-139">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1210d-140">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-140">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1210d-141">De `dpkg -i`-opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="1210d-141">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="1210d-142">Met de volgende opdracht, `apt-get install -f`, worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="1210d-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="1210d-143">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1210d-143">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="1210d-144">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="1210d-144">Ubuntu 18.10</span></span>

<span data-ttu-id="1210d-145">De installatie wordt ondersteund via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="1210d-145">Installation is supported via `snapd`.</span></span> <span data-ttu-id="1210d-146">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="1210d-146">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-147">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="1210d-147">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="1210d-148">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="1210d-148">Ubuntu 19.04</span></span>

<span data-ttu-id="1210d-149">De installatie wordt ondersteund via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="1210d-149">Installation is supported via `snapd`.</span></span> <span data-ttu-id="1210d-150">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="1210d-150">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-151">Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="1210d-151">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="1210d-152">Debian 8</span><span class="sxs-lookup"><span data-stu-id="1210d-152">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="1210d-153">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="1210d-153">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="1210d-154">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-154">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1210d-155">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1210d-155">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1210d-156">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="1210d-156">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1210d-157">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="1210d-157">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="1210d-158">Debian 9</span><span class="sxs-lookup"><span data-stu-id="1210d-158">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="1210d-159">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="1210d-159">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="1210d-160">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-160">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1210d-161">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1210d-161">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1210d-162">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="1210d-162">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1210d-163">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="1210d-163">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="1210d-164">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="1210d-164">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="1210d-165">Down load het Debian-pakket `powershell_6.2.0-1.debian.9_amd64.deb` van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="1210d-165">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1210d-166">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-166">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="1210d-167">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="1210d-167">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="1210d-168">Debian 10</span><span class="sxs-lookup"><span data-stu-id="1210d-168">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-169">Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="1210d-169">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="1210d-170">Installatie via direct downloaden-Debian 10</span><span class="sxs-lookup"><span data-stu-id="1210d-170">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="1210d-171">Down load het tar. gz-pakket `powershell_7.0.0-preview-7-linux-x64.tar.gz` van de pagina [releases][] op de computer Debian.</span><span class="sxs-lookup"><span data-stu-id="1210d-171">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1210d-172">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-172">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="1210d-173">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="1210d-173">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-174">Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="1210d-174">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="1210d-175">Installatie via direct downloaden-Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="1210d-175">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="1210d-176">Down load het tar. gz-pakket `powershell_7.0.0-preview-7-linux-x64.tar.gz` van de pagina [releases][] op de Alpine machine.</span><span class="sxs-lookup"><span data-stu-id="1210d-176">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="1210d-177">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-177">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="centos-7"></a><span data-ttu-id="1210d-178">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1210d-178">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-179">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="1210d-179">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="1210d-180">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1210d-180">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="1210d-181">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1210d-182">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="1210d-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1210d-183">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="1210d-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="1210d-184">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1210d-184">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="1210d-185">Gebruik [CentOS 7][]om het rpm-pakket `powershell-6.2.0-1.rhel.7.x86_64.rpm` te downloaden van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="1210d-185">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="1210d-186">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1210d-187">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="1210d-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="1210d-188">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1210d-188">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1210d-190">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1210d-190">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1210d-191">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1210d-191">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1210d-192">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1210d-193">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="1210d-193">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1210d-194">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="1210d-194">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1210d-195">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1210d-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1210d-196">Down load het RPM-pakket `powershell-6.2.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="1210d-196">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="1210d-197">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-197">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1210d-198">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="1210d-198">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1210d-199">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1210d-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="1210d-200">openSUSE</span><span class="sxs-lookup"><span data-stu-id="1210d-200">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="1210d-201">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="1210d-201">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="1210d-202">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="1210d-202">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="1210d-203">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="1210d-203">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="1210d-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="1210d-204">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-205">Fedora 28 wordt alleen ondersteund in Power shell Core 6,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="1210d-205">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-206">Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="1210d-206">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="1210d-207">Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="1210d-207">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="1210d-208">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-208">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="1210d-209">Installatie via direct downloaden-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="1210d-209">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="1210d-210">Down load het RPM-pakket `powershell-6.2.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Fedora-machine.</span><span class="sxs-lookup"><span data-stu-id="1210d-210">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="1210d-211">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="1210d-211">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1210d-212">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="1210d-212">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="1210d-213">Installatie ongedaan maken-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="1210d-213">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="1210d-214">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="1210d-214">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-215">Arch-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="1210d-215">Arch support is experimental.</span></span>

<span data-ttu-id="1210d-216">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="1210d-216">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="1210d-217">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="1210d-217">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="1210d-218">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="1210d-218">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="1210d-219">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="1210d-219">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="1210d-220">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="1210d-220">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="1210d-221">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="1210d-221">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="1210d-223">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="1210d-223">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="1210d-224">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="1210d-224">Getting snapd</span></span>

<span data-ttu-id="1210d-225">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="1210d-225">`snapd` is required to run snaps.</span></span> <span data-ttu-id="1210d-226">Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om ervoor te zorgen dat `snapd` is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1210d-226">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="1210d-227">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="1210d-227">Installation via Snap</span></span>

<span data-ttu-id="1210d-228">Power shell core voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="1210d-228">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="1210d-229">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="1210d-229">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="1210d-230">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="1210d-230">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="1210d-231">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="1210d-231">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="1210d-232">U kunt een upgrade activeren met behulp van `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="1210d-232">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="1210d-233">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="1210d-233">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="1210d-234">of</span><span class="sxs-lookup"><span data-stu-id="1210d-234">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="1210d-235">Kali</span><span class="sxs-lookup"><span data-stu-id="1210d-235">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="1210d-236">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="1210d-236">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="1210d-237">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="1210d-237">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="1210d-238">Raspbian</span><span class="sxs-lookup"><span data-stu-id="1210d-238">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="1210d-239">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="1210d-239">Raspbian support is experimental.</span></span>

<span data-ttu-id="1210d-240">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="1210d-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="1210d-241">CoreCLR en Power shell core werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="1210d-241">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="1210d-242">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="1210d-242">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="1210d-243">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="1210d-243">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="1210d-244">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar het binaire `pwsh` op te geven.</span><span class="sxs-lookup"><span data-stu-id="1210d-244">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="1210d-245">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="1210d-245">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="1210d-246">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="1210d-246">Binary Archives</span></span>

<span data-ttu-id="1210d-247">Voor Linux-platforms zijn binaire Power shell-`tar.gz`-archieven beschikbaar om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="1210d-247">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="1210d-248">Elkaar</span><span class="sxs-lookup"><span data-stu-id="1210d-248">Dependencies</span></span>

<span data-ttu-id="1210d-249">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="1210d-249">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="1210d-250">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="1210d-250">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="1210d-251">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="1210d-251">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="1210d-252">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="1210d-252">OS</span></span>                 | <span data-ttu-id="1210d-253">Elkaar</span><span class="sxs-lookup"><span data-stu-id="1210d-253">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="1210d-254">Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1210d-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="1210d-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1210d-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1210d-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="1210d-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="1210d-257">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="1210d-257">Ubuntu 17.10</span></span>       | <span data-ttu-id="1210d-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1210d-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1210d-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="1210d-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="1210d-260">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1210d-260">Ubuntu 18.04</span></span>       | <span data-ttu-id="1210d-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1210d-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1210d-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="1210d-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="1210d-263">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="1210d-263">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="1210d-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1210d-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1210d-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="1210d-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="1210d-266">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="1210d-266">Debian 9 (Stretch)</span></span> | <span data-ttu-id="1210d-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1210d-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1210d-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="1210d-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="1210d-269">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1210d-269">CentOS 7</span></span> <br> <span data-ttu-id="1210d-270">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="1210d-270">Oracle Linux 7</span></span> <br> <span data-ttu-id="1210d-271">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="1210d-271">RHEL 7</span></span> | <span data-ttu-id="1210d-272">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="1210d-272">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="1210d-273">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="1210d-273">openSUSE 42.3</span></span> | <span data-ttu-id="1210d-274">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="1210d-274">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="1210d-275">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="1210d-275">openSUSE Leap 15</span></span> | <span data-ttu-id="1210d-276">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="1210d-276">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="1210d-277">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="1210d-277">Fedora 27</span></span> <br> <span data-ttu-id="1210d-278">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1210d-278">Fedora 28</span></span> | <span data-ttu-id="1210d-279">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="1210d-279">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="1210d-280">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="1210d-280">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="1210d-281">Zo installeert onze [Amazon Linux dockerfile][amazon-dockerfile] eerst afhankelijkheden en extraheert vervolgens het archief Linux `tar.gz`.</span><span class="sxs-lookup"><span data-stu-id="1210d-281">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="1210d-282">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="1210d-282">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="1210d-283">Linux</span><span class="sxs-lookup"><span data-stu-id="1210d-283">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="1210d-284">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="1210d-284">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="1210d-285">Paden</span><span class="sxs-lookup"><span data-stu-id="1210d-285">Paths</span></span>

* <span data-ttu-id="1210d-286">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="1210d-286">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="1210d-287">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1210d-287">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="1210d-288">Standaard profielen worden gelezen van `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1210d-288">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="1210d-289">Gebruikers modules worden gelezen van `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1210d-289">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="1210d-290">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1210d-290">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="1210d-291">Standaard modules worden gelezen van `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="1210d-291">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="1210d-292">De PSReadline-geschiedenis wordt geregistreerd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="1210d-292">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="1210d-293">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen bestaan op `Microsoft.PowerShell_profile.ps1` op dezelfde locatie.</span><span class="sxs-lookup"><span data-stu-id="1210d-293">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="1210d-294">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="1210d-294">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
