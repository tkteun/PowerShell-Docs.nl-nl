---
title: PowerShell Core in Linux installeren
description: Informatie over het installeren van Power shell Core op diverse Linux-distributies
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68372193"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="7a420-103">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="7a420-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="7a420-104">Ondersteunt [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE schrikkel 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], en [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="7a420-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="7a420-105">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="7a420-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="7a420-106">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks [ `tar.gz` ][tar]te implementeren met behulp van het Linux-archief, maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="7a420-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="7a420-107">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="7a420-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="7a420-108">Nadat het pakket is geïnstalleerd, voert `pwsh` u uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="7a420-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="7a420-109">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="7a420-109">Installing Preview Releases</span></span>

<span data-ttu-id="7a420-110">Wanneer u een Power shell core preview-versie voor Linux installeert via een pakket opslagplaats, wordt de `powershell` naam `powershell-preview`van het pakket gewijzigd van in.</span><span class="sxs-lookup"><span data-stu-id="7a420-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="7a420-111">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="7a420-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="7a420-112">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="7a420-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="7a420-113">Distributie (s)</span><span class="sxs-lookup"><span data-stu-id="7a420-113">Distribution(s)</span></span>|<span data-ttu-id="7a420-114">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="7a420-114">Stable Command</span></span> | <span data-ttu-id="7a420-115">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="7a420-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="7a420-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="7a420-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="7a420-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="7a420-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="7a420-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="7a420-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="7a420-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7a420-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="7a420-120">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7a420-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="7a420-121">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7a420-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7a420-122">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7a420-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="7a420-123">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7a420-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7a420-124">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="7a420-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="7a420-125">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7a420-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="7a420-126">Down load het Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` -pakket van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="7a420-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7a420-127">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7a420-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7a420-128">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7a420-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="7a420-129">Met de volgende opdracht `apt-get install -f` worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="7a420-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="7a420-130">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7a420-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="7a420-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7a420-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="7a420-132">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7a420-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="7a420-133">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7a420-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7a420-134">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7a420-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="7a420-135">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7a420-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7a420-136">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="7a420-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="7a420-137">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7a420-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="7a420-138">Down load het Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` -pakket van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="7a420-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7a420-139">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7a420-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7a420-140">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7a420-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="7a420-141">Met de volgende opdracht `apt-get install -f` worden deze problemen opgelost en wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="7a420-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="7a420-142">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7a420-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="7a420-143">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="7a420-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="7a420-144">Omdat 18,10 een [voorlopige versie](https://www.ubuntu.com/about/release-cycle)is, wordt dit alleen [ondersteund](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6)door de community.</span><span class="sxs-lookup"><span data-stu-id="7a420-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="7a420-145">Installeren op 18,10 wordt ondersteund via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="7a420-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="7a420-146">Zie [snap package][snap] voor volledige instructies;</span><span class="sxs-lookup"><span data-stu-id="7a420-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="7a420-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="7a420-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="7a420-148">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="7a420-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="7a420-149">Power shell core, voor Linux, wordt gepubliceerd op pakket opslagplaatsen voor eenvoudig installeren en bijwerken.</span><span class="sxs-lookup"><span data-stu-id="7a420-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7a420-150">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7a420-150">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

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

<span data-ttu-id="7a420-151">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7a420-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7a420-152">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="7a420-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="7a420-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a420-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="7a420-154">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a420-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="7a420-155">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7a420-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7a420-156">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7a420-156">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

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

<span data-ttu-id="7a420-157">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7a420-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7a420-158">Na de registratie kunt u Power shell bijwerken `sudo apt-get upgrade powershell`met.</span><span class="sxs-lookup"><span data-stu-id="7a420-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="7a420-159">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a420-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="7a420-160">Down load het Debian `powershell_6.2.0-1.debian.9_amd64.deb` -pakket van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="7a420-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7a420-161">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7a420-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="7a420-162">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7a420-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="7a420-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a420-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="7a420-164">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="7a420-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="7a420-165">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a420-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="7a420-166">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7a420-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a420-167">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7a420-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7a420-168">Na de registratie kunt u Power shell bijwerken `sudo yum update powershell`met.</span><span class="sxs-lookup"><span data-stu-id="7a420-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="7a420-169">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a420-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="7a420-170">Gebruik [CentOS 7][]om het rpm-pakket `powershell-6.2.0-1.rhel.7.x86_64.rpm` te downloaden van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="7a420-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="7a420-171">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7a420-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7a420-172">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7a420-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="7a420-173">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a420-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a420-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a420-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a420-176">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a420-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7a420-177">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7a420-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7a420-178">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7a420-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7a420-179">Na de registratie kunt u Power shell bijwerken `sudo yum update powershell`met.</span><span class="sxs-lookup"><span data-stu-id="7a420-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a420-180">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a420-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7a420-181">Down load het rpm `powershell-6.2.0-1.rhel.7.x86_64.rpm` -pakket van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="7a420-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="7a420-182">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7a420-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7a420-183">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7a420-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7a420-184">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7a420-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="7a420-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7a420-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="7a420-186">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="7a420-186">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="7a420-187">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7a420-187">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="7a420-188">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7a420-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="7a420-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="7a420-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="7a420-190">Fedora 28 wordt alleen ondersteund in Power shell Core 6,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="7a420-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="7a420-191">Installatie via pakket opslagplaats (voor keur)-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a420-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="7a420-192">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7a420-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="7a420-193">Installatie via directe down load-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a420-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="7a420-194">Down load het rpm `powershell-6.2.0-1.rhel.7.x86_64.rpm` -pakket van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="7a420-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="7a420-195">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7a420-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7a420-196">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7a420-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="7a420-197">Installatie ongedaan maken-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a420-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="7a420-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7a420-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="7a420-199">Arch-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="7a420-199">Arch support is experimental.</span></span>

<span data-ttu-id="7a420-200">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="7a420-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="7a420-201">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="7a420-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="7a420-202">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="7a420-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="7a420-203">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="7a420-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="7a420-204">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="7a420-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="7a420-205">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="7a420-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="7a420-207">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="7a420-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="7a420-208">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="7a420-208">Getting snapd</span></span>

<span data-ttu-id="7a420-209">`snapd`is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="7a420-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="7a420-210">Volg [deze instructies](https://docs.snapcraft.io/core/install) om te controleren of u `snapd` hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7a420-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="7a420-211">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="7a420-211">Installation via Snap</span></span>

<span data-ttu-id="7a420-212">Power shell core voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7a420-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="7a420-213">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7a420-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="7a420-214">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="7a420-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="7a420-215">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="7a420-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="7a420-216">U kunt een upgrade activeren met `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="7a420-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="7a420-217">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="7a420-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="7a420-218">of</span><span class="sxs-lookup"><span data-stu-id="7a420-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="7a420-219">Kali</span><span class="sxs-lookup"><span data-stu-id="7a420-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="7a420-220">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="7a420-220">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="7a420-221">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="7a420-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="7a420-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="7a420-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="7a420-223">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="7a420-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="7a420-224">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="7a420-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="7a420-225">CoreCLR en Power shell core werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="7a420-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="7a420-226">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="7a420-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="7a420-227">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="7a420-227">Installation - Raspbian</span></span>

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

<span data-ttu-id="7a420-228">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar het `pwsh` binaire bestand op te geven.</span><span class="sxs-lookup"><span data-stu-id="7a420-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="7a420-229">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="7a420-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="7a420-230">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="7a420-230">Binary Archives</span></span>

<span data-ttu-id="7a420-231">Er zijn `tar.gz` binaire Power shell-archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="7a420-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="7a420-232">Elkaar</span><span class="sxs-lookup"><span data-stu-id="7a420-232">Dependencies</span></span>

<span data-ttu-id="7a420-233">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="7a420-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="7a420-234">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="7a420-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="7a420-235">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="7a420-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="7a420-236">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="7a420-236">OS</span></span>                 | <span data-ttu-id="7a420-237">Elkaar</span><span class="sxs-lookup"><span data-stu-id="7a420-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="7a420-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7a420-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="7a420-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7a420-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a420-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="7a420-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="7a420-241">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="7a420-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="7a420-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7a420-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a420-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="7a420-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="7a420-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7a420-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="7a420-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7a420-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a420-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="7a420-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="7a420-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="7a420-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="7a420-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7a420-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a420-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7a420-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7a420-250">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="7a420-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="7a420-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7a420-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7a420-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="7a420-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="7a420-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7a420-253">CentOS 7</span></span> <br> <span data-ttu-id="7a420-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7a420-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="7a420-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="7a420-255">RHEL 7</span></span> | <span data-ttu-id="7a420-256">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="7a420-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="7a420-257">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="7a420-257">openSUSE 42.3</span></span> | <span data-ttu-id="7a420-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="7a420-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="7a420-259">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7a420-259">openSUSE Leap 15</span></span> | <span data-ttu-id="7a420-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="7a420-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="7a420-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="7a420-261">Fedora 27</span></span> <br> <span data-ttu-id="7a420-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7a420-262">Fedora 28</span></span> | <span data-ttu-id="7a420-263">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="7a420-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="7a420-264">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="7a420-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="7a420-265">Bijvoorbeeld, onze [Amazon Linux-dockerfile][amazon-dockerfile] installeert eerst afhankelijkheden en extraheert vervolgens het Linux `tar.gz` -archief.</span><span class="sxs-lookup"><span data-stu-id="7a420-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="7a420-266">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="7a420-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="7a420-267">Linux</span><span class="sxs-lookup"><span data-stu-id="7a420-267">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="7a420-268">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="7a420-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="7a420-269">Paden</span><span class="sxs-lookup"><span data-stu-id="7a420-269">Paths</span></span>

* <span data-ttu-id="7a420-270">`$PSHOME`ontbreekt`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="7a420-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="7a420-271">Gebruikers profielen worden gelezen van`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7a420-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="7a420-272">Standaard profielen worden gelezen uit`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7a420-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="7a420-273">Gebruikers modules worden gelezen uit`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7a420-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7a420-274">Gedeelde modules worden gelezen van`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7a420-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="7a420-275">Standaard modules worden gelezen van`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="7a420-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="7a420-276">De PSReadline-geschiedenis wordt vastgelegd in`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="7a420-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7a420-277">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="7a420-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7a420-278">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="7a420-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
