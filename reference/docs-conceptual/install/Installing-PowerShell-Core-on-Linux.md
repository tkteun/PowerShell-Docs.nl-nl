---
title: PowerShell Core in Linux installeren
description: Informatie over het installeren van PowerShell Core in verschillende Linux-distributies
ms.date: 08/06/2018
ms.openlocfilehash: 0a7c9549c37222bf599e4bdb9e36c91288191bb3
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64530630"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="ac869-103">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="ac869-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="ac869-104">Ondersteunt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [ openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], en [Boog Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="ac869-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="ac869-105">Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell module pakket][snap].</span><span class="sxs-lookup"><span data-stu-id="ac869-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="ac869-106">U kunt ook PowerShell binaire bestanden rechtstreeks met behulp van de Linux implementeren [ `tar.gz` archief][tar], maar dan moet u voor het instellen van de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="ac869-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="ac869-107">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="ac869-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="ac869-108">Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="ac869-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
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

## <a name="installing-preview-releases"></a><span data-ttu-id="ac869-109">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="ac869-109">Installing Preview Releases</span></span>

<span data-ttu-id="ac869-110">Bij het installeren van een PowerShell Core Preview-versie voor Linux via een Pakketopslagplaats, naam van het pakket verandert van `powershell` naar `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ac869-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="ac869-111">Installeren via de directe download verandert niet, dan de naam van het bestand.</span><span class="sxs-lookup"><span data-stu-id="ac869-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="ac869-112">Hier volgt een tabel met de opdrachten om de met de verschillende pakketmanagers stabiel en preview-pakketten te installeren:</span><span class="sxs-lookup"><span data-stu-id="ac869-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="ac869-113">Verdeling van</span><span class="sxs-lookup"><span data-stu-id="ac869-113">Distribution(s)</span></span>|<span data-ttu-id="ac869-114">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="ac869-114">Stable Command</span></span> | <span data-ttu-id="ac869-115">Preview-opdracht</span><span class="sxs-lookup"><span data-stu-id="ac869-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="ac869-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="ac869-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="ac869-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="ac869-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="ac869-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="ac869-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="ac869-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ac869-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="ac869-120">Installatie via Pakketopslagplaats - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ac869-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="ac869-121">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ac869-122">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="ac869-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ac869-123">Als beheerder, de Microsoft-opslagplaats te registreren.</span><span class="sxs-lookup"><span data-stu-id="ac869-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="ac869-124">Vanaf hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` om bij te werken van de installatie.</span><span class="sxs-lookup"><span data-stu-id="ac869-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="ac869-125">Installatie via de directe Download - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ac869-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="ac869-126">Het Debian-pakket downloaden `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ac869-126">Download the Debian package `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="ac869-127">uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="ac869-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ac869-128">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="ac869-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ac869-129">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="ac869-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ac869-130">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="ac869-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="ac869-131">Verwijderen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ac869-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="ac869-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ac869-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="ac869-133">Installatie via Pakketopslagplaats - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ac869-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="ac869-134">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ac869-135">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="ac869-135">This is the preferred method.</span></span>

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

<span data-ttu-id="ac869-136">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="ac869-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="ac869-137">Installatie via de directe Download - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ac869-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="ac869-138">Het Debian-pakket downloaden `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ac869-138">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="ac869-139">uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="ac869-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ac869-140">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="ac869-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ac869-141">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="ac869-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ac869-142">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="ac869-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="ac869-143">Verwijderen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ac869-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="ac869-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ac869-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="ac869-145">Installatie via Pakketopslagplaats - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ac869-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="ac869-146">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ac869-147">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="ac869-147">This is the preferred method.</span></span>

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

<span data-ttu-id="ac869-148">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="ac869-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="ac869-149">Installatie via de directe Download - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ac869-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="ac869-150">Het Debian-pakket downloaden `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ac869-150">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="ac869-151">uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="ac869-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="ac869-152">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="ac869-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="ac869-153">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="ac869-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="ac869-154">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="ac869-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="ac869-155">Verwijderen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ac869-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="ac869-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="ac869-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="ac869-157">18.10 is een [tussentijdse release](https://www.ubuntu.com/about/release-cycle), is het alleen [community ondersteund](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="ac869-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="ac869-158">Installeren op 18.10 wordt ondersteund `snapd`.</span><span class="sxs-lookup"><span data-stu-id="ac869-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="ac869-159">Zie [module pakket] [ snap] voor volledige instructies;</span><span class="sxs-lookup"><span data-stu-id="ac869-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="ac869-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="ac869-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="ac869-161">Installatie via Pakketopslagplaats - Debian 8</span><span class="sxs-lookup"><span data-stu-id="ac869-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="ac869-162">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ac869-163">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="ac869-163">This is the preferred method.</span></span>

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

<span data-ttu-id="ac869-164">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="ac869-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="ac869-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="ac869-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="ac869-166">Installatie via Pakketopslagplaats - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ac869-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="ac869-167">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="ac869-168">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="ac869-168">This is the preferred method.</span></span>

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

<span data-ttu-id="ac869-169">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="ac869-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="ac869-170">Installatie via de directe Download - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ac869-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="ac869-171">Het Debian-pakket downloaden `powershell_6.2.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="ac869-171">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="ac869-172">uit de [releases][] pagina naar de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="ac869-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="ac869-173">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="ac869-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="ac869-174">Verwijderen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="ac869-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="ac869-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ac869-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="ac869-176">Dit pakket werkt ook op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="ac869-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="ac869-177">Installatie via (aanbevolen) - Pakketopslagplaats CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ac869-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="ac869-178">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ac869-179">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac869-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="ac869-180">Installatie via de directe Download - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ac869-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="ac869-181">Met behulp van [CentOS 7][], het RPM-pakket downloaden `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="ac869-181">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="ac869-182">uit de [releases][] pagina op de computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="ac869-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="ac869-183">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="ac869-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ac869-184">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="ac869-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="ac869-185">Verwijderen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ac869-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ac869-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ac869-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ac869-188">Installatie via (aanbevolen) - Pakketopslagplaats Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ac869-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ac869-189">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="ac869-190">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ac869-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ac869-191">Installatie via de directe Download - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ac869-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="ac869-192">Download het RPM-pakket `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="ac869-192">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="ac869-193">uit de [releases][] pagina naar de Red Hat Enterprise Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="ac869-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="ac869-194">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="ac869-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ac869-195">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="ac869-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="ac869-196">Verwijderen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="ac869-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="ac869-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="ac869-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="ac869-198">Installatie - openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="ac869-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="ac869-199">Installatie - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ac869-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="ac869-200">Verwijderen - openSUSE 42,3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ac869-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="ac869-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="ac869-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="ac869-202">Fedora 28 wordt alleen ondersteund in PowerShell Core 6.1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ac869-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="ac869-203">Installatie via Pakketopslagplaats (aanbevolen) - 27 Fedora, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ac869-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ac869-204">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="ac869-205">Installatie via de directe Download - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ac869-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="ac869-206">Download het RPM-pakket `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="ac869-206">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="ac869-207">uit de [releases][] pagina op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="ac869-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="ac869-208">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="ac869-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="ac869-209">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="ac869-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="ac869-210">Verwijderen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ac869-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="ac869-211">Linux boog</span><span class="sxs-lookup"><span data-stu-id="ac869-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="ac869-212">Er is een experimenteel boog ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="ac869-212">Arch support is experimental.</span></span>

<span data-ttu-id="ac869-213">PowerShell is beschikbaar via de [Linux boog][] gebruiker opslagplaats (AUR).</span><span class="sxs-lookup"><span data-stu-id="ac869-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="ac869-214">Het kan worden gecompileerd met de [meest recente versie gemarkeerd][arch-release]</span><span class="sxs-lookup"><span data-stu-id="ac869-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="ac869-215">Het kan worden gecompileerd uit de [laatste doorvoering naar hoofdniveau][arch-git]</span><span class="sxs-lookup"><span data-stu-id="ac869-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="ac869-216">Kan worden geïnstalleerd met behulp van de [binaire de meest recente release][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="ac869-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="ac869-217">Pakketten in de AUR zijn community onderhouden: Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="ac869-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="ac869-218">Zie voor meer informatie over het installeren van pakketten van de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="ac869-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Linux boog]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="ac869-220">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="ac869-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="ac869-221">Snapd ophalen</span><span class="sxs-lookup"><span data-stu-id="ac869-221">Getting snapd</span></span>

<span data-ttu-id="ac869-222">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="ac869-222">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="ac869-223">Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om ervoor te zorgen dat u hebt `snapd` geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ac869-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="ac869-224">Installatie via de module</span><span class="sxs-lookup"><span data-stu-id="ac869-224">Installation via Snap</span></span>

<span data-ttu-id="ac869-225">PowerShell Core voor Linux is gepubliceerd naar de [module store](https://snapcraft.io/store) voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="ac869-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="ac869-226">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="ac869-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="ac869-227">Als u installeren van de preview-versie wilt, gebruikt u de volgende methode.</span><span class="sxs-lookup"><span data-stu-id="ac869-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="ac869-228">Nadat de installatie van module, automatisch bijgewerkt, maar u kunt activeren een upgrade uitvoeren met behulp `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="ac869-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="ac869-229">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="ac869-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="ac869-230">of</span><span class="sxs-lookup"><span data-stu-id="ac869-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="ac869-231">Kali</span><span class="sxs-lookup"><span data-stu-id="ac869-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="ac869-232">Installatie - Kali</span><span class="sxs-lookup"><span data-stu-id="ac869-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="ac869-233">Verwijderen - Kali</span><span class="sxs-lookup"><span data-stu-id="ac869-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="ac869-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="ac869-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="ac869-235">Ondersteuning voor Raspbian is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="ac869-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="ac869-236">PowerShell is momenteel alleen ondersteund op Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="ac869-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="ac869-237">Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten van Pi 2 en Pi 3 als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="ac869-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="ac869-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) zodat deze naar uw Pi.</span><span class="sxs-lookup"><span data-stu-id="ac869-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="ac869-239">Installatie - Raspbian</span><span class="sxs-lookup"><span data-stu-id="ac869-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="ac869-240">U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven pad naar het binaire 'pwsh' maken</span><span class="sxs-lookup"><span data-stu-id="ac869-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="ac869-241">Verwijderen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="ac869-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="ac869-242">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="ac869-242">Binary Archives</span></span>

<span data-ttu-id="ac869-243">PowerShell binaire `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="ac869-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="ac869-244">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="ac869-244">Dependencies</span></span>

<span data-ttu-id="ac869-245">PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="ac869-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="ac869-246">Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en kan daarom PowerShell hetzelfde effect heeft.</span><span class="sxs-lookup"><span data-stu-id="ac869-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="ac869-247">Het volgende diagram toont de .NET Core 2.0-afhankelijkheden die officieel ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="ac869-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="ac869-248">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="ac869-248">OS</span></span>                 | <span data-ttu-id="ac869-249">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="ac869-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="ac869-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="ac869-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="ac869-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ac869-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ac869-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ac869-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ac869-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="ac869-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="ac869-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ac869-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ac869-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="ac869-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="ac869-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="ac869-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="ac869-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ac869-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ac869-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="ac869-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="ac869-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="ac869-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="ac869-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ac869-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ac869-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="ac869-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="ac869-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="ac869-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="ac869-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ac869-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ac869-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="ac869-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="ac869-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="ac869-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="ac869-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="ac869-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="ac869-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="ac869-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="ac869-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="ac869-268">CentOS 7</span></span> <br> <span data-ttu-id="ac869-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="ac869-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="ac869-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="ac869-270">RHEL 7</span></span> | <span data-ttu-id="ac869-271">libunwind, libcurl, openssl-bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="ac869-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="ac869-272">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="ac869-272">openSUSE 42.3</span></span> | <span data-ttu-id="ac869-273">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="ac869-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="ac869-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="ac869-274">openSUSE Leap 15</span></span> | <span data-ttu-id="ac869-275">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="ac869-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="ac869-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="ac869-276">Fedora 27</span></span> <br> <span data-ttu-id="ac869-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="ac869-277">Fedora 28</span></span> | <span data-ttu-id="ac869-278">libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="ac869-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="ac869-279">Voor het implementeren van binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund, moet u de vereiste afhankelijkheden voor het doelbesturingssysteem installeren in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="ac869-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="ac869-280">Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden eerst geïnstalleerd en pakt u vervolgens de Linux `tar.gz` archief.</span><span class="sxs-lookup"><span data-stu-id="ac869-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="ac869-281">Installatie - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="ac869-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="ac869-282">Linux</span><span class="sxs-lookup"><span data-stu-id="ac869-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="ac869-283">Verwijderen binaire archieven</span><span class="sxs-lookup"><span data-stu-id="ac869-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="ac869-284">Paden</span><span class="sxs-lookup"><span data-stu-id="ac869-284">Paths</span></span>

* <span data-ttu-id="ac869-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="ac869-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="ac869-286">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ac869-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="ac869-287">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="ac869-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="ac869-288">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ac869-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ac869-289">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="ac869-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="ac869-290">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="ac869-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="ac869-291">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="ac869-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="ac869-292">De profielen respecteren van PowerShell per host-configuratie, zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="ac869-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="ac869-293">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="ac869-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
