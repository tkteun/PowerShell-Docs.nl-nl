---
title: PowerShell Core in Linux installeren
description: Informatie over het installeren van PowerShell Core in verschillende Linux-distributies
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587445"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="80027-103">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="80027-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="80027-104">Ondersteunt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42,3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], en [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="80027-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="80027-105">Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell module pakket][snap].</span><span class="sxs-lookup"><span data-stu-id="80027-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="80027-106">U kunt ook PowerShell binaire bestanden rechtstreeks met behulp van de Linux implementeren [ `tar.gz` archief][tar], maar dan moet u voor het instellen van de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="80027-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="80027-107">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="80027-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="80027-108">Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.</span><span class="sxs-lookup"><span data-stu-id="80027-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="80027-109">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="80027-109">Installing Preview Releases</span></span>

<span data-ttu-id="80027-110">Bij het installeren van een PowerShell Core Preview-versie voor Linux via een Pakketopslagplaats, naam van het pakket verandert van `powershell` naar `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="80027-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="80027-111">Installeren via de directe download verandert niet, dan de naam van het bestand.</span><span class="sxs-lookup"><span data-stu-id="80027-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="80027-112">Hier volgt een tabel met de opdrachten om de met de verschillende pakketmanagers stabiel en preview-pakketten te installeren:</span><span class="sxs-lookup"><span data-stu-id="80027-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="80027-113">Verdeling van</span><span class="sxs-lookup"><span data-stu-id="80027-113">Distribution(s)</span></span>|<span data-ttu-id="80027-114">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="80027-114">Stable Command</span></span> | <span data-ttu-id="80027-115">Preview-opdracht</span><span class="sxs-lookup"><span data-stu-id="80027-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="80027-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="80027-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="80027-117">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="80027-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="80027-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="80027-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="80027-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="80027-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="80027-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="80027-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="80027-121">Installatie via Pakketopslagplaats - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="80027-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="80027-122">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="80027-123">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="80027-123">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80027-124">Als beheerder, de Microsoft-opslagplaats te registreren.</span><span class="sxs-lookup"><span data-stu-id="80027-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="80027-125">Vanaf hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` om bij te werken van de installatie.</span><span class="sxs-lookup"><span data-stu-id="80027-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="80027-126">Installatie via de directe Download - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="80027-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="80027-127">Het Debian-pakket downloaden `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="80027-127">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="80027-128">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="80027-129">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="80027-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="80027-130">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="80027-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="80027-131">Verwijderen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="80027-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="80027-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80027-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="80027-133">Installatie via Pakketopslagplaats - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80027-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="80027-134">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="80027-135">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="80027-135">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80027-136">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="80027-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="80027-137">Installatie via de directe Download - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80027-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="80027-138">Het Debian-pakket downloaden `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="80027-138">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="80027-139">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-139">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="80027-140">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="80027-140">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="80027-141">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="80027-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="80027-142">Verwijderen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80027-142">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="80027-143">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="80027-143">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="80027-144">Er is ondersteuning voor Ubuntu 18.04 toegevoegd na `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="80027-144">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="80027-145">Installatie via Pakketopslagplaats - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="80027-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="80027-146">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="80027-147">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="80027-147">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="80027-148">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="80027-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="80027-149">Installatie via de directe Download - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="80027-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="80027-150">Het Debian-pakket downloaden `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` uit de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="80027-150">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="80027-151">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-151">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="80027-152">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="80027-152">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="80027-153">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="80027-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="80027-154">Verwijderen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="80027-154">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="80027-155">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="80027-155">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="80027-156">Er is ondersteuning voor Ubuntu 18.10 toegevoegd na `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="80027-156">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="80027-157">Zoals 18.10 een dagelijkse build is, is het alleen community ondersteund.</span><span class="sxs-lookup"><span data-stu-id="80027-157">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="80027-158">Installeren op 18.10 wordt ondersteund `snapd`.</span><span class="sxs-lookup"><span data-stu-id="80027-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="80027-159">Zie [module pakket] [ snap] voor volledige instructies;</span><span class="sxs-lookup"><span data-stu-id="80027-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="80027-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="80027-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="80027-161">Installatie via Pakketopslagplaats - Debian 8</span><span class="sxs-lookup"><span data-stu-id="80027-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="80027-162">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="80027-163">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="80027-163">This is the preferred method.</span></span>

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

<span data-ttu-id="80027-164">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="80027-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="80027-165">Installatie via de directe Download - Debian 8</span><span class="sxs-lookup"><span data-stu-id="80027-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="80027-166">Het Debian-pakket downloaden `powershell_6.0.2-1.debian.8_amd64.deb` uit de [releases][] pagina naar de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="80027-166">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="80027-167">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-167">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="80027-168">De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="80027-168">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="80027-169">De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="80027-169">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="80027-170">Verwijderen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="80027-170">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="80027-171">Debian 9</span><span class="sxs-lookup"><span data-stu-id="80027-171">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="80027-172">Installatie via Pakketopslagplaats - Debian 9</span><span class="sxs-lookup"><span data-stu-id="80027-172">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="80027-173">PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-173">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="80027-174">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="80027-174">This is the preferred method.</span></span>

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

<span data-ttu-id="80027-175">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="80027-175">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="80027-176">Installatie via de directe Download - Debian 9</span><span class="sxs-lookup"><span data-stu-id="80027-176">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="80027-177">Het Debian-pakket downloaden `powershell_6.0.2-1.debian.9_amd64.deb` uit de [releases][] pagina naar de Debian-machine.</span><span class="sxs-lookup"><span data-stu-id="80027-177">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="80027-178">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-178">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="80027-179">Verwijderen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="80027-179">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="80027-180">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="80027-180">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="80027-181">Dit pakket werkt ook op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="80027-181">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="80027-182">Installatie via (aanbevolen) - Pakketopslagplaats CentOS 7</span><span class="sxs-lookup"><span data-stu-id="80027-182">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="80027-183">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-183">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80027-184">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80027-184">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="80027-185">Installatie via de directe Download - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="80027-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="80027-186">Met behulp van [CentOS 7][], het RPM-pakket downloaden `powershell-6.0.2-1.rhel.7.x86_64.rpm` uit de [releases][] pagina op de computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="80027-186">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="80027-187">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-187">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="80027-188">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="80027-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="80027-189">Verwijderen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="80027-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80027-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="80027-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80027-192">Installatie via (aanbevolen) - Pakketopslagplaats Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="80027-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="80027-193">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80027-194">Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80027-194">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80027-195">Installatie via de directe Download - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="80027-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="80027-196">Download het RPM-pakket `powershell-6.0.2-1.rhel.7.x86_64.rpm` uit de [releases][] pagina naar de Red Hat Enterprise Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="80027-196">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="80027-197">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-197">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="80027-198">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="80027-198">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80027-199">Verwijderen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="80027-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="80027-200">OpenSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="80027-200">OpenSUSE 42.3</span></span>

<span data-ttu-id="80027-201">Bij het installeren van PowerShell Core, `zypper` mogelijk meldt u de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="80027-201">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="80027-202">Controleer in dit geval een compatibel `libcurl` bibliotheek aanwezig is door te controleren dat de volgende toont opdracht de `libcurl4` verpakken als geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="80027-202">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="80027-203">Kies vervolgens de `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` oplossing wanneer u het PowerShell-pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="80027-203">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="80027-204">Installatie via (aanbevolen) - Pakketopslagplaats OpenSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="80027-204">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="80027-205">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="80027-206">Installatie via de directe Download - OpenSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="80027-206">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="80027-207">Download het RPM-pakket `powershell-6.0.2-1.rhel.7.x86_64.rpm` uit de [releases][] pagina op de computer OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="80027-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="80027-208">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="80027-208">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="80027-209">Verwijderen - OpenSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="80027-209">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="80027-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="80027-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="80027-211">Fedora 28 wordt alleen ondersteund in PowerShell Core 6.1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="80027-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="80027-212">Installatie via Pakketopslagplaats (aanbevolen) - 27 Fedora, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="80027-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="80027-213">PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="80027-214">Installatie via de directe Download - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="80027-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="80027-215">Download het RPM-pakket `powershell-6.0.2-1.rhel.7.x86_64.rpm` uit de [releases][] pagina op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="80027-215">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="80027-216">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-216">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="80027-217">U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:</span><span class="sxs-lookup"><span data-stu-id="80027-217">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="80027-218">Verwijderen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="80027-218">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="80027-219">Linux boog</span><span class="sxs-lookup"><span data-stu-id="80027-219">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="80027-220">Er is een experimenteel boog ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="80027-220">Arch support is experimental.</span></span>

<span data-ttu-id="80027-221">PowerShell is beschikbaar via de [Arch Linux][] gebruiker opslagplaats (AUR).</span><span class="sxs-lookup"><span data-stu-id="80027-221">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="80027-222">Het kan worden gecompileerd met de [meest recente versie gemarkeerd][arch-release]</span><span class="sxs-lookup"><span data-stu-id="80027-222">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="80027-223">Het kan worden gecompileerd uit de [laatste doorvoering naar hoofdniveau][arch-git]</span><span class="sxs-lookup"><span data-stu-id="80027-223">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="80027-224">Kan worden geïnstalleerd met behulp van de [binaire de meest recente release][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="80027-224">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="80027-225">Pakketten in de AUR zijn community onderhouden: Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="80027-225">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="80027-226">Zie voor meer informatie over het installeren van pakketten van de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="80027-226">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="80027-228">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="80027-228">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="80027-229">Snapd ophalen</span><span class="sxs-lookup"><span data-stu-id="80027-229">Getting snapd</span></span>

<span data-ttu-id="80027-230">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="80027-230">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="80027-231">Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om ervoor te zorgen dat u hebt `snapd` geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="80027-231">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="80027-232">Installatie via de module</span><span class="sxs-lookup"><span data-stu-id="80027-232">Installation via Snap</span></span>

<span data-ttu-id="80027-233">PowerShell Core voor Linux is gepubliceerd naar de [module store](https://snapcraft.io/store) voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="80027-233">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="80027-234">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="80027-234">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="80027-235">Nadat de installatie van module, automatisch bijgewerkt, maar u kunt activeren een upgrade uitvoeren met behulp `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="80027-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="80027-236">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="80027-236">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="80027-237">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="80027-237">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="80027-238">Ondersteuning voor AppImage is experimenteel</span><span class="sxs-lookup"><span data-stu-id="80027-238">AppImage support is experimental</span></span>

<span data-ttu-id="80027-239">Met behulp van een recente Linux-distributie, downloaden de AppImage `powershell-6.0.1-x86_64.AppImage` uit de [releases][] pagina naar de Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="80027-239">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="80027-240">Voer vervolgens het volgende uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="80027-240">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="80027-241">De [AppImage][] kunt u PowerShell uitvoeren zonder dat deze wordt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="80027-241">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="80027-242">Het is een draagbare toepassing dat PowerShell en de bijbehorende afhankelijkheden (met inbegrip van afhankelijkheden van .NET-Core system) worden in een samenhangend pakket.</span><span class="sxs-lookup"><span data-stu-id="80027-242">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="80027-243">Dit pakket is een enkele binaire waarde dat onafhankelijk van de Linux-distributie van de gebruiker werkt.</span><span class="sxs-lookup"><span data-stu-id="80027-243">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="80027-245">Kali</span><span class="sxs-lookup"><span data-stu-id="80027-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="80027-246">Ondersteuning voor Kali is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="80027-246">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="80027-247">Installatie</span><span class="sxs-lookup"><span data-stu-id="80027-247">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="80027-248">Voer PowerShell uit in de meest recente Kali (Rolling Kali GNU/Linux) zonder dat deze wordt geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="80027-248">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="80027-249">Verwijderen - Kali</span><span class="sxs-lookup"><span data-stu-id="80027-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="80027-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="80027-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="80027-251">Ondersteuning voor Raspbian is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="80027-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="80027-252">PowerShell is momenteel alleen ondersteund op Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="80027-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="80027-253">Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten van Pi 2 en Pi 3 als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="80027-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="80027-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) zodat deze naar uw Pi.</span><span class="sxs-lookup"><span data-stu-id="80027-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="80027-255">Installatie</span><span class="sxs-lookup"><span data-stu-id="80027-255">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="80027-256">U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven pad naar het binaire 'pwsh' maken</span><span class="sxs-lookup"><span data-stu-id="80027-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="80027-257">Verwijderen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="80027-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="80027-258">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="80027-258">Binary Archives</span></span>

<span data-ttu-id="80027-259">PowerShell binaire `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="80027-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="80027-260">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="80027-260">Dependencies</span></span>

<span data-ttu-id="80027-261">PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="80027-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="80027-262">Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en kan daarom PowerShell hetzelfde effect heeft.</span><span class="sxs-lookup"><span data-stu-id="80027-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="80027-263">Het volgende diagram toont de .NET Core 2.0-afhankelijkheden die officieel ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="80027-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="80027-264">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="80027-264">OS</span></span>                 | <span data-ttu-id="80027-265">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="80027-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="80027-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="80027-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="80027-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="80027-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80027-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="80027-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="80027-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80027-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="80027-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="80027-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80027-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="80027-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="80027-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="80027-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="80027-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="80027-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80027-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="80027-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="80027-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="80027-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="80027-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="80027-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80027-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="80027-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="80027-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="80027-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="80027-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="80027-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80027-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="80027-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="80027-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="80027-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="80027-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="80027-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80027-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="80027-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="80027-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="80027-284">CentOS 7</span></span> <br> <span data-ttu-id="80027-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="80027-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="80027-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="80027-286">RHEL 7</span></span> <br> <span data-ttu-id="80027-287">OpenSUSE OpenSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="80027-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="80027-288">libunwind, libcurl, openssl-bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="80027-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="80027-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="80027-289">Fedora 27</span></span> <br> <span data-ttu-id="80027-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="80027-290">Fedora 28</span></span> | <span data-ttu-id="80027-291">libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="80027-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="80027-292">Voor het implementeren van binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund, moet u de vereiste afhankelijkheden voor het doelbesturingssysteem installeren in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="80027-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="80027-293">Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden eerst geïnstalleerd en pakt u vervolgens de Linux `tar.gz` archief.</span><span class="sxs-lookup"><span data-stu-id="80027-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="80027-294">Installatie - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="80027-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="80027-295">Linux</span><span class="sxs-lookup"><span data-stu-id="80027-295">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="80027-296">Verwijderen binaire archieven</span><span class="sxs-lookup"><span data-stu-id="80027-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="80027-297">Paden</span><span class="sxs-lookup"><span data-stu-id="80027-297">Paths</span></span>

* <span data-ttu-id="80027-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="80027-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="80027-299">Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="80027-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="80027-300">Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="80027-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="80027-301">Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="80027-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="80027-302">Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="80027-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="80027-303">Standaardmodules worden gelezen in `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="80027-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="80027-304">PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="80027-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="80027-305">De profielen respecteren van PowerShell per host-configuratie, zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="80027-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="80027-306">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="80027-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
