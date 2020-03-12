---
title: Power Shell installeren in Linux
description: Informatie over het installeren van Power shell op diverse Linux-distributies
ms.date: 03/09/2020
ms.openlocfilehash: 0c7b2bd804d07b2fcb61a61240b139f84fabd6db
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/11/2020
ms.locfileid: "79128422"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="7ca49-103">Power Shell installeren in Linux</span><span class="sxs-lookup"><span data-stu-id="7ca49-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="7ca49-104">Ondersteunt [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE schrikkel 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora]en [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="7ca49-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="7ca49-105">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="7ca49-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="7ca49-106">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks te implementeren met behulp van het Linux [`tar.gz` Archive][tar], maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="7ca49-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="7ca49-107">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="7ca49-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="7ca49-108">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="7ca49-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="7ca49-109">Voer `pwsh-preview` uit als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7ca49-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-110">Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7ca49-110">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="7ca49-111">De map `/usr/local/microsoft/powershell/6` wordt vervangen door `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-111">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="7ca49-112">Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.</span><span class="sxs-lookup"><span data-stu-id="7ca49-112">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives


## <a name="installing-preview-releases"></a><span data-ttu-id="7ca49-113">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="7ca49-113">Installing Preview Releases</span></span>

<span data-ttu-id="7ca49-114">Wanneer u een Power shell preview-versie voor Linux installeert via een pakket opslagplaats, wordt de naam van het pakket gewijzigd van `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-114">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="7ca49-115">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="7ca49-115">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="7ca49-116">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="7ca49-116">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="7ca49-117">Distributie (s)</span><span class="sxs-lookup"><span data-stu-id="7ca49-117">Distribution(s)</span></span> |            <span data-ttu-id="7ca49-118">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="7ca49-118">Stable Command</span></span>            |               <span data-ttu-id="7ca49-119">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="7ca49-119">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="7ca49-120">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="7ca49-120">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="7ca49-121">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="7ca49-121">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="7ca49-122">Fedora</span><span class="sxs-lookup"><span data-stu-id="7ca49-122">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a><span data-ttu-id="7ca49-123">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7ca49-123">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="7ca49-124">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7ca49-124">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="7ca49-125">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-125">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7ca49-126">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7ca49-126">The preferred method is as follows:</span></span>

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

<span data-ttu-id="7ca49-127">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7ca49-127">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7ca49-128">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-128">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="7ca49-129">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7ca49-129">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="7ca49-130">Down load het Debian-pakket `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-130">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7ca49-131">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-131">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7ca49-132">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7ca49-132">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="7ca49-133">Met de volgende opdracht, `apt-get install -f` deze problemen op te lossen, wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="7ca49-133">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="7ca49-134">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="7ca49-134">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="7ca49-135">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7ca49-135">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="7ca49-136">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7ca49-136">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="7ca49-137">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-137">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7ca49-138">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7ca49-138">The preferred method is as follows:</span></span>

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

<span data-ttu-id="7ca49-139">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7ca49-139">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7ca49-140">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-140">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="7ca49-141">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7ca49-141">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="7ca49-142">Down load het Debian-pakket `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-142">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="7ca49-143">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-143">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="7ca49-144">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="7ca49-144">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="7ca49-145">Met de volgende opdracht, `apt-get install -f` deze problemen op te lossen, wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="7ca49-145">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="7ca49-146">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="7ca49-146">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="7ca49-147">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="7ca49-147">Ubuntu 18.10</span></span>

<span data-ttu-id="7ca49-148">De installatie wordt ondersteund via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="7ca49-149">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="7ca49-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-150">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="7ca49-150">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="7ca49-151">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="7ca49-151">Ubuntu 19.04</span></span>

<span data-ttu-id="7ca49-152">De installatie wordt ondersteund via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-152">Installation is supported via `snapd`.</span></span> <span data-ttu-id="7ca49-153">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="7ca49-153">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-154">Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="7ca49-154">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="7ca49-155">Debian 8</span><span class="sxs-lookup"><span data-stu-id="7ca49-155">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="7ca49-156">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="7ca49-156">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="7ca49-157">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7ca49-158">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7ca49-158">The preferred method is as follows:</span></span>

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

<span data-ttu-id="7ca49-159">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7ca49-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7ca49-160">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-160">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="7ca49-161">Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ca49-161">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="7ca49-162">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ca49-162">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="7ca49-163">Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-163">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="7ca49-164">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7ca49-164">The preferred method is as follows:</span></span>

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

<span data-ttu-id="7ca49-165">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7ca49-165">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7ca49-166">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-166">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="7ca49-167">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ca49-167">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="7ca49-168">Down load het Debian-pakket `powershell_7.0.0-1.debian.9_amd64.deb` van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-168">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7ca49-169">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-169">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="7ca49-170">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="7ca49-170">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="7ca49-171">Debian 10</span><span class="sxs-lookup"><span data-stu-id="7ca49-171">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-172">Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-172">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="7ca49-173">Installatie via direct downloaden-Debian 10</span><span class="sxs-lookup"><span data-stu-id="7ca49-173">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="7ca49-174">Down load het tar. gz-pakket `powershell_7.0.0-linux-x64.tar.gz` van de pagina [releases][] op de computer Debian.</span><span class="sxs-lookup"><span data-stu-id="7ca49-174">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="7ca49-175">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-175">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="7ca49-176">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="7ca49-176">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-177">Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-177">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="7ca49-178">Installatie via direct downloaden-Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="7ca49-178">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="7ca49-179">Down load het tar. gz-pakket `powershell_7.0.0-linux-x64.tar.gz` van de pagina [releases][] op de Alpine machine.</span><span class="sxs-lookup"><span data-stu-id="7ca49-179">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="7ca49-180">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-180">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="7ca49-181">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-181">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-182">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="7ca49-182">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="7ca49-183">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-183">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="7ca49-184">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-184">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7ca49-185">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7ca49-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7ca49-186">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-186">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="7ca49-187">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="7ca49-188">Gebruik [CentOS 7][]om het rpm-pakket te downloaden `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-188">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="7ca49-189">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ca49-190">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7ca49-190">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="7ca49-191">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-191">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ca49-193">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-193">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ca49-194">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-194">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7ca49-195">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-195">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="7ca49-196">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="7ca49-196">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="7ca49-197">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-197">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ca49-198">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="7ca49-199">Down load het RPM-pakket `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="7ca49-199">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="7ca49-200">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-200">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ca49-201">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7ca49-201">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="7ca49-202">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-202">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="7ca49-203">openSUSE</span><span class="sxs-lookup"><span data-stu-id="7ca49-203">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="7ca49-204">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="7ca49-204">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="7ca49-205">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7ca49-205">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="7ca49-206">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7ca49-206">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="7ca49-207">Fedora</span><span class="sxs-lookup"><span data-stu-id="7ca49-207">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-208">Fedora 28 wordt alleen ondersteund in Power shell 6,1 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-208">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-209">Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="7ca49-209">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="7ca49-210">Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="7ca49-210">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="7ca49-211">Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="7ca49-212">Installatie via direct downloaden-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="7ca49-212">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="7ca49-213">Down load het RPM-pakket `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="7ca49-213">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="7ca49-214">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="7ca49-214">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="7ca49-215">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="7ca49-215">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="7ca49-216">Installatie ongedaan maken-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="7ca49-216">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="7ca49-217">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="7ca49-217">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-218">Arch-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="7ca49-218">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="7ca49-219">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="7ca49-219">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="7ca49-220">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="7ca49-220">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="7ca49-221">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="7ca49-221">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="7ca49-222">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="7ca49-222">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="7ca49-223">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="7ca49-223">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="7ca49-224">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="7ca49-224">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="7ca49-226">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="7ca49-226">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="7ca49-227">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="7ca49-227">Getting snapd</span></span>

<span data-ttu-id="7ca49-228">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="7ca49-228">`snapd` is required to run snaps.</span></span> <span data-ttu-id="7ca49-229">Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om er zeker van te zijn dat `snapd` is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="7ca49-229">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="7ca49-230">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="7ca49-230">Installation via Snap</span></span>

<span data-ttu-id="7ca49-231">Power shell voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="7ca49-231">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="7ca49-232">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="7ca49-232">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="7ca49-233">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="7ca49-233">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="7ca49-234">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="7ca49-234">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="7ca49-235">U kunt een upgrade activeren met behulp van `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="7ca49-235">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="7ca49-236">Installatie ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="7ca49-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="7ca49-237">of</span><span class="sxs-lookup"><span data-stu-id="7ca49-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="7ca49-238">Kali</span><span class="sxs-lookup"><span data-stu-id="7ca49-238">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-239">Kali-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="7ca49-239">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="7ca49-240">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="7ca49-240">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="7ca49-241">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="7ca49-241">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="7ca49-242">Raspbian</span><span class="sxs-lookup"><span data-stu-id="7ca49-242">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="7ca49-243">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="7ca49-243">Raspbian support is experimental.</span></span>

<span data-ttu-id="7ca49-244">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="7ca49-244">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="7ca49-245">CoreCLR en Power shell werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="7ca49-245">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="7ca49-246">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="7ca49-246">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="7ca49-247">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="7ca49-247">Installation - Raspbian</span></span>

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

<span data-ttu-id="7ca49-248">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar de `pwsh` binaire waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="7ca49-248">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="7ca49-249">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="7ca49-249">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="7ca49-250">Installeren als een Global .NET-hulp programma</span><span class="sxs-lookup"><span data-stu-id="7ca49-250">Install as a .NET Global tool</span></span>

<span data-ttu-id="7ca49-251">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="7ca49-251">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="binary-archives"></a><span data-ttu-id="7ca49-252">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="7ca49-252">Binary Archives</span></span>

<span data-ttu-id="7ca49-253">Er zijn binaire Power shell-`tar.gz` archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="7ca49-253">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="7ca49-254">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="7ca49-254">Dependencies</span></span>

<span data-ttu-id="7ca49-255">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="7ca49-255">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="7ca49-256">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="7ca49-256">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="7ca49-257">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="7ca49-257">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="7ca49-258">OS</span><span class="sxs-lookup"><span data-stu-id="7ca49-258">OS</span></span>                 | <span data-ttu-id="7ca49-259">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="7ca49-259">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="7ca49-260">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="7ca49-260">Ubuntu 16.04</span></span>       | <span data-ttu-id="7ca49-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7ca49-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ca49-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="7ca49-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="7ca49-263">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="7ca49-263">Ubuntu 17.10</span></span>       | <span data-ttu-id="7ca49-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7ca49-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ca49-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="7ca49-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="7ca49-266">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="7ca49-266">Ubuntu 18.04</span></span>       | <span data-ttu-id="7ca49-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7ca49-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ca49-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="7ca49-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="7ca49-269">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="7ca49-269">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="7ca49-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7ca49-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ca49-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="7ca49-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="7ca49-272">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="7ca49-272">Debian 9 (Stretch)</span></span> | <span data-ttu-id="7ca49-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="7ca49-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="7ca49-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="7ca49-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="7ca49-275">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-275">CentOS 7</span></span> <br> <span data-ttu-id="7ca49-276">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-276">Oracle Linux 7</span></span> <br> <span data-ttu-id="7ca49-277">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="7ca49-277">RHEL 7</span></span> | <span data-ttu-id="7ca49-278">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="7ca49-278">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="7ca49-279">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="7ca49-279">openSUSE 42.3</span></span> | <span data-ttu-id="7ca49-280">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="7ca49-280">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="7ca49-281">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="7ca49-281">openSUSE Leap 15</span></span> | <span data-ttu-id="7ca49-282">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="7ca49-282">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="7ca49-283">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="7ca49-283">Fedora 27</span></span> <br> <span data-ttu-id="7ca49-284">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="7ca49-284">Fedora 28</span></span> | <span data-ttu-id="7ca49-285">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="7ca49-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="7ca49-286">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="7ca49-286">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="7ca49-287">Zo installeert onze [Amazon Linux dockerfile][amazon-dockerfile] eerst afhankelijkheden en extraheert vervolgens het Linux `tar.gz`-archief.</span><span class="sxs-lookup"><span data-stu-id="7ca49-287">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="7ca49-288">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="7ca49-288">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="7ca49-289">Linux</span><span class="sxs-lookup"><span data-stu-id="7ca49-289">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="7ca49-290">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="7ca49-290">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="7ca49-291">Paden</span><span class="sxs-lookup"><span data-stu-id="7ca49-291">Paths</span></span>

- <span data-ttu-id="7ca49-292">`$PSHOME` is `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="7ca49-292">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="7ca49-293">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7ca49-293">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="7ca49-294">Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="7ca49-294">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="7ca49-295">Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7ca49-295">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="7ca49-296">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="7ca49-296">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="7ca49-297">Standaard modules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="7ca49-297">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="7ca49-298">De PSReadline-geschiedenis wordt geregistreerd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="7ca49-298">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="7ca49-299">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` op dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="7ca49-299">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="7ca49-300">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="7ca49-300">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
