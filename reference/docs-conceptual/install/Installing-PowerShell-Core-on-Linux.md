---
title: PowerShell Core in Linux installeren
description: Informatie over het installeren van PowerShell Core in verschillende Linux-distributies
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404007"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="a7d7d-103">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="a7d7d-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="a7d7d-104">Ondersteunt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9] [ deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [ Fedora 28][fedora], en [boog Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="a7d7d-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="a7d7d-105">Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell module pakket][snap].</span><span class="sxs-lookup"><span data-stu-id="a7d7d-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="a7d7d-106">U kunt ook PowerShell binaire bestanden rechtstreeks met behulp van de Linux implementeren [ `tar.gz` archief][tar], maar dan moet u voor het instellen van de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="a7d7d-107">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="a7d7d-108">Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="a7d7d-109">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="a7d7d-109">Installing Preview Releases</span></span>

<span data-ttu-id="a7d7d-110">Bij het installeren van een PowerShell Core Preview-versie voor Linux via een Pakketopslagplaats, naam van het pakket verandert van `powershell` naar `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="a7d7d-111">Installeren via de directe download verandert niet, dan de naam van het bestand.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="a7d7d-112">Hier volgt een tabel met de opdrachten om de met de verschillende pakketmanagers stabiel en preview-pakketten te installeren:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="a7d7d-113">Verdeling van</span><span class="sxs-lookup"><span data-stu-id="a7d7d-113">Distribution(s)</span></span>|<span data-ttu-id="a7d7d-114">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="a7d7d-114">Stable Command</span></span> | <span data-ttu-id="a7d7d-115">Preview-opdracht</span><span class="sxs-lookup"><span data-stu-id="a7d7d-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="a7d7d-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="a7d7d-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="a7d7d-117">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="a7d7d-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="a7d7d-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="a7d7d-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="a7d7d-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="a7d7d-120">Installatie via Pakketopslagplaats - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="a7d7d-121">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d7d-122">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-122">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d7d-123">Als beheerder, de Microsoft-opslagplaats te registreren.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="a7d7d-124">Vanaf hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` om bij te werken van de installatie.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="a7d7d-125">Installatie via de directe Download - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="a7d7d-126">Het Debian-pakket downloaden `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="a7d7d-127">uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a7d7d-128">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a7d7d-129">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a7d7d-130">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="a7d7d-131">Verwijderen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="a7d7d-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="a7d7d-133">Installatie via Pakketopslagplaats - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="a7d7d-134">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d7d-135">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-135">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d7d-136">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="a7d7d-137">Installatie via de directe Download - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="a7d7d-138">Het Debian-pakket downloaden `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="a7d7d-139">uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a7d7d-140">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a7d7d-141">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a7d7d-142">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="a7d7d-143">Verwijderen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="a7d7d-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-144">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="a7d7d-145">Er is ondersteuning voor Ubuntu 18.04 toegevoegd na `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-145">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="a7d7d-146">Installatie via Pakketopslagplaats - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-146">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="a7d7d-147">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-147">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d7d-148">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-148">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a7d7d-149">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-149">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="a7d7d-150">Installatie via de directe Download - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-150">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="a7d7d-151">Het Debian-pakket downloaden `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-151">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="a7d7d-152">uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-152">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="a7d7d-153">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-153">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a7d7d-154">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-154">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a7d7d-155">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-155">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="a7d7d-156">Verwijderen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-156">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="a7d7d-157">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="a7d7d-157">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="a7d7d-158">Er is ondersteuning voor Ubuntu 18.10 toegevoegd na `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-158">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="a7d7d-159">Zoals 18.10 een dagelijkse build is, is het alleen community ondersteund.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-159">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="a7d7d-160">Installeren op 18.10 wordt ondersteund `snapd`.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-160">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="a7d7d-161">Zie [module pakket] [ snap] voor volledige instructies;</span><span class="sxs-lookup"><span data-stu-id="a7d7d-161">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="a7d7d-162">Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d7d-162">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="a7d7d-163">Installatie via Pakketopslagplaats - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d7d-163">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="a7d7d-164">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-164">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d7d-165">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-165">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d7d-166">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-166">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="a7d7d-167">Installatie via de directe Download - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d7d-167">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="a7d7d-168">Het Debian-pakket downloaden `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-168">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="a7d7d-169">uit de [releases][] pagina naar de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-169">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="a7d7d-170">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-170">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="a7d7d-171">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-171">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="a7d7d-172">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-172">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="a7d7d-173">Verwijderen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d7d-173">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="a7d7d-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d7d-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="a7d7d-175">Installatie via Pakketopslagplaats - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d7d-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="a7d7d-176">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-176">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d7d-177">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-177">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d7d-178">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-178">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="a7d7d-179">Installatie via de directe Download - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d7d-179">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="a7d7d-180">Het Debian-pakket downloaden `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-180">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="a7d7d-181">uit de [releases][] pagina naar de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-181">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="a7d7d-182">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-182">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="a7d7d-183">Verwijderen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d7d-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="a7d7d-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="a7d7d-185">Dit pakket werkt ook op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-185">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="a7d7d-186">Installatie via (aanbevolen) - Pakketopslagplaats CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="a7d7d-187">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-187">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a7d7d-188">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-188">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="a7d7d-189">Installatie via de directe Download - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-189">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="a7d7d-190">Met behulp van [CentOS 7][], het RPM-pakket downloaden `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-190">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="a7d7d-191">uit de [releases][] pagina op de computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-191">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="a7d7d-192">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d7d-193">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="a7d7d-194">Verwijderen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d7d-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d7d-197">Installatie via (aanbevolen) - Pakketopslagplaats Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a7d7d-198">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a7d7d-199">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d7d-200">Installatie via de directe Download - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a7d7d-201">Download het RPM-pakket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-201">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="a7d7d-202">uit de [releases][] pagina naar de Red Hat Enterprise Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-202">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="a7d7d-203">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-203">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d7d-204">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d7d-205">Verwijderen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="a7d7d-206">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="a7d7d-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="a7d7d-207">Installatie - openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="a7d7d-207">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="a7d7d-208">Installatie - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="a7d7d-208">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="a7d7d-209">Verwijderen - openSUSE 42,3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="a7d7d-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="a7d7d-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="a7d7d-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="a7d7d-211">Fedora 28 wordt alleen ondersteund in PowerShell Core 6.1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="a7d7d-212">Installatie via Pakketopslagplaats (aanbevolen) - 27 Fedora, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a7d7d-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="a7d7d-213">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="a7d7d-214">Installatie via de directe Download - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a7d7d-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="a7d7d-215">Download het RPM-pakket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-215">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="a7d7d-216">uit de [releases][] pagina op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-216">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="a7d7d-217">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-217">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d7d-218">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="a7d7d-218">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="a7d7d-219">Verwijderen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a7d7d-219">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="a7d7d-220">Linux boog</span><span class="sxs-lookup"><span data-stu-id="a7d7d-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="a7d7d-221">Er is een experimenteel boog ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-221">Arch support is experimental.</span></span>

<span data-ttu-id="a7d7d-222">PowerShell is beschikbaar via de [Linux boog][] gebruiker opslagplaats (AUR).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="a7d7d-223">Het kan worden gecompileerd met de [meest recente versie gemarkeerd][arch-release]</span><span class="sxs-lookup"><span data-stu-id="a7d7d-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="a7d7d-224">Het kan worden gecompileerd uit de [laatste doorvoering naar hoofdniveau][arch-git]</span><span class="sxs-lookup"><span data-stu-id="a7d7d-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="a7d7d-225">Kan worden geïnstalleerd met behulp van de [binaire de meest recente release][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="a7d7d-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="a7d7d-226">Pakketten in de AUR zijn community onderhouden: Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-226">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="a7d7d-227">Zie voor meer informatie over het installeren van pakketten van de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Linux boog]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="a7d7d-229">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="a7d7d-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="a7d7d-230">Snapd ophalen</span><span class="sxs-lookup"><span data-stu-id="a7d7d-230">Getting snapd</span></span>

<span data-ttu-id="a7d7d-231">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-231">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="a7d7d-232">Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om ervoor te zorgen dat u hebt `snapd` geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="a7d7d-233">Installatie via de module</span><span class="sxs-lookup"><span data-stu-id="a7d7d-233">Installation via Snap</span></span>

<span data-ttu-id="a7d7d-234">PowerShell Core voor Linux is gepubliceerd naar de [module store](https://snapcraft.io/store) voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="a7d7d-234">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="a7d7d-235">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-235">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="a7d7d-236">Als u installeren van de preview-versie wilt, gebruikt u de volgende methode.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-236">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="a7d7d-237">Nadat de installatie van module, automatisch bijgewerkt, maar u kunt activeren een upgrade uitvoeren met behulp `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-237">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="a7d7d-238">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="a7d7d-238">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="a7d7d-239">of</span><span class="sxs-lookup"><span data-stu-id="a7d7d-239">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="a7d7d-240">Kali</span><span class="sxs-lookup"><span data-stu-id="a7d7d-240">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="a7d7d-241">Installatie - Kali</span><span class="sxs-lookup"><span data-stu-id="a7d7d-241">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="a7d7d-242">Verwijderen - Kali</span><span class="sxs-lookup"><span data-stu-id="a7d7d-242">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="a7d7d-243">Raspbian</span><span class="sxs-lookup"><span data-stu-id="a7d7d-243">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="a7d7d-244">Ondersteuning voor Raspbian is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-244">Raspbian support is experimental.</span></span>

<span data-ttu-id="a7d7d-245">PowerShell is momenteel alleen ondersteund op Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-245">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="a7d7d-246">Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten van Pi 2 en Pi 3 als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-246">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="a7d7d-247">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) zodat deze naar uw Pi.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-247">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="a7d7d-248">Installatie - Raspbian</span><span class="sxs-lookup"><span data-stu-id="a7d7d-248">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="a7d7d-249">U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven pad naar het binaire 'pwsh' maken</span><span class="sxs-lookup"><span data-stu-id="a7d7d-249">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="a7d7d-250">Verwijderen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="a7d7d-250">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="a7d7d-251">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="a7d7d-251">Binary Archives</span></span>

<span data-ttu-id="a7d7d-252">PowerShell binaire `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-252">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="a7d7d-253">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="a7d7d-253">Dependencies</span></span>

<span data-ttu-id="a7d7d-254">PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-254">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="a7d7d-255">Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en kan daarom PowerShell hetzelfde effect heeft.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-255">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="a7d7d-256">Het volgende diagram toont de .NET Core 2.0-afhankelijkheden die officieel ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-256">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="a7d7d-257">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="a7d7d-257">OS</span></span>                 | <span data-ttu-id="a7d7d-258">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="a7d7d-258">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="a7d7d-259">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-259">Ubuntu 14.04</span></span>       | <span data-ttu-id="a7d7d-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d7d-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d7d-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="a7d7d-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="a7d7d-262">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-262">Ubuntu 16.04</span></span>       | <span data-ttu-id="a7d7d-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d7d-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d7d-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="a7d7d-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="a7d7d-265">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="a7d7d-265">Ubuntu 17.10</span></span>       | <span data-ttu-id="a7d7d-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d7d-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d7d-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="a7d7d-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="a7d7d-268">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="a7d7d-268">Ubuntu 18.04</span></span>       | <span data-ttu-id="a7d7d-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d7d-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d7d-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="a7d7d-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="a7d7d-271">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="a7d7d-271">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="a7d7d-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d7d-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d7d-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="a7d7d-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="a7d7d-274">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="a7d7d-274">Debian 9 (Stretch)</span></span> | <span data-ttu-id="a7d7d-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d7d-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d7d-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="a7d7d-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="a7d7d-277">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-277">CentOS 7</span></span> <br> <span data-ttu-id="a7d7d-278">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-278">Oracle Linux 7</span></span> <br> <span data-ttu-id="a7d7d-279">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="a7d7d-279">RHEL 7</span></span> | <span data-ttu-id="a7d7d-280">libunwind, libcurl, openssl-bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="a7d7d-280">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="a7d7d-281">OpenSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="a7d7d-281">openSUSE 42.3</span></span> | <span data-ttu-id="a7d7d-282">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="a7d7d-282">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="a7d7d-283">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="a7d7d-283">openSUSE Leap 15</span></span> | <span data-ttu-id="a7d7d-284">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="a7d7d-284">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="a7d7d-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="a7d7d-285">Fedora 27</span></span> <br> <span data-ttu-id="a7d7d-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="a7d7d-286">Fedora 28</span></span> | <span data-ttu-id="a7d7d-287">libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="a7d7d-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="a7d7d-288">Voor het implementeren van binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund, moet u de vereiste afhankelijkheden voor het doelbesturingssysteem installeren in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="a7d7d-289">Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden eerst geïnstalleerd en pakt u vervolgens de Linux `tar.gz` archief.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="a7d7d-290">Installatie - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="a7d7d-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="a7d7d-291">Linux</span><span class="sxs-lookup"><span data-stu-id="a7d7d-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="a7d7d-292">Verwijderen binaire archieven</span><span class="sxs-lookup"><span data-stu-id="a7d7d-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="a7d7d-293">Paden</span><span class="sxs-lookup"><span data-stu-id="a7d7d-293">Paths</span></span>

* <span data-ttu-id="a7d7d-294">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-294">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="a7d7d-295">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="a7d7d-296">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="a7d7d-297">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a7d7d-298">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a7d7d-299">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="a7d7d-300">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a7d7d-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="a7d7d-301">De profielen respecteren van PowerShell per host-configuratie, zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="a7d7d-302">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="a7d7d-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
