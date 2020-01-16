---
title: PowerShell Core in Linux installeren
description: Informatie over het installeren van Power shell Core op diverse Linux-distributies
ms.date: 07/19/2019
ms.openlocfilehash: 3b0b9b1520247fa49760e631c837196fb7107b5f
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022264"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="6e66d-103">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="6e66d-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="6e66d-104">Ondersteunt [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE schrikkel 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora]en [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="6e66d-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="6e66d-105">Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap].</span><span class="sxs-lookup"><span data-stu-id="6e66d-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="6e66d-106">U kunt ook proberen om Power shell-binaire bestanden rechtstreeks te implementeren met behulp van het Linux [`tar.gz` Archive][tar], maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="6e66d-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="6e66d-107">Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .</span><span class="sxs-lookup"><span data-stu-id="6e66d-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="6e66d-108">Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.</span><span class="sxs-lookup"><span data-stu-id="6e66d-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="6e66d-109">Voer `pwsh-preview` uit als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="6e66d-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

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

> [!TIP]
> <span data-ttu-id="6e66d-110">Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="6e66d-110">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="installing-preview-releases"></a><span data-ttu-id="6e66d-111">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="6e66d-111">Installing Preview Releases</span></span>

<span data-ttu-id="6e66d-112">Wanneer u een Power shell core preview-versie voor Linux installeert via een pakket opslagplaats, wordt de naam van het pakket gewijzigd van `powershell` in `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-112">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="6e66d-113">Installeren via direct downloaden verandert niet, behalve de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="6e66d-113">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="6e66d-114">De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:</span><span class="sxs-lookup"><span data-stu-id="6e66d-114">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="6e66d-115">Distributie(s)</span><span class="sxs-lookup"><span data-stu-id="6e66d-115">Distribution(s)</span></span>|<span data-ttu-id="6e66d-116">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="6e66d-116">Stable Command</span></span> | <span data-ttu-id="6e66d-117">Opdracht preview</span><span class="sxs-lookup"><span data-stu-id="6e66d-117">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="6e66d-118">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="6e66d-118">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="6e66d-119">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="6e66d-119">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="6e66d-120">Fedora</span><span class="sxs-lookup"><span data-stu-id="6e66d-120">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="6e66d-121">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6e66d-121">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="6e66d-122">Installatie via pakket opslagplaats-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="6e66d-122">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="6e66d-123">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-123">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="6e66d-124">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6e66d-124">The preferred method is as follows:</span></span>

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

<span data-ttu-id="6e66d-125">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="6e66d-125">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="6e66d-126">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-126">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="6e66d-127">Installatie via direct downloaden-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="6e66d-127">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="6e66d-128">Down load het Debian-pakket `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="6e66d-128">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6e66d-129">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-129">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6e66d-130">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="6e66d-130">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="6e66d-131">Met de volgende opdracht, `apt-get install -f` deze problemen op te lossen, wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="6e66d-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="6e66d-132">Installatie ongedaan maken-Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="6e66d-132">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="6e66d-133">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6e66d-133">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="6e66d-134">Installatie via pakket opslagplaats-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="6e66d-134">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="6e66d-135">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-135">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="6e66d-136">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6e66d-136">The preferred method is as follows:</span></span>

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

<span data-ttu-id="6e66d-137">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="6e66d-137">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="6e66d-138">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-138">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="6e66d-139">Installatie via direct downloaden-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="6e66d-139">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="6e66d-140">Down load het Debian-pakket `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.</span><span class="sxs-lookup"><span data-stu-id="6e66d-140">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6e66d-141">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-141">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6e66d-142">De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden.</span><span class="sxs-lookup"><span data-stu-id="6e66d-142">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="6e66d-143">Met de volgende opdracht, `apt-get install -f` deze problemen op te lossen, wordt de configuratie van het Power shell-pakket voltooid.</span><span class="sxs-lookup"><span data-stu-id="6e66d-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="6e66d-144">Installatie ongedaan maken-Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="6e66d-144">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="6e66d-145">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="6e66d-145">Ubuntu 18.10</span></span>

<span data-ttu-id="6e66d-146">De installatie wordt ondersteund via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-146">Installation is supported via `snapd`.</span></span> <span data-ttu-id="6e66d-147">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="6e66d-147">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-148">Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="6e66d-148">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="6e66d-149">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="6e66d-149">Ubuntu 19.04</span></span>

<span data-ttu-id="6e66d-150">De installatie wordt ondersteund via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-150">Installation is supported via `snapd`.</span></span> <span data-ttu-id="6e66d-151">Zie [snap package][snap]voor instructies.</span><span class="sxs-lookup"><span data-stu-id="6e66d-151">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-152">Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="6e66d-152">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="6e66d-153">Debian 8</span><span class="sxs-lookup"><span data-stu-id="6e66d-153">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="6e66d-154">Installatie via pakket opslagplaats-Debian 8</span><span class="sxs-lookup"><span data-stu-id="6e66d-154">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="6e66d-155">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="6e66d-156">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6e66d-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="6e66d-157">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="6e66d-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="6e66d-158">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="6e66d-159">Debian 9</span><span class="sxs-lookup"><span data-stu-id="6e66d-159">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="6e66d-160">Installatie via pakket opslagplaats-Debian 9</span><span class="sxs-lookup"><span data-stu-id="6e66d-160">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="6e66d-161">Power shell core voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-161">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="6e66d-162">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6e66d-162">The preferred method is as follows:</span></span>

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

<span data-ttu-id="6e66d-163">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="6e66d-163">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="6e66d-164">Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-164">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="6e66d-165">Installatie via direct downloaden-Debian 9</span><span class="sxs-lookup"><span data-stu-id="6e66d-165">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="6e66d-166">Down load het Debian-pakket `powershell_7.0.0-1.debian.9_amd64.deb` van de pagina [releases][] op de Debian-computer.</span><span class="sxs-lookup"><span data-stu-id="6e66d-166">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="6e66d-167">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-167">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="6e66d-168">Installatie ongedaan maken-Debian 9</span><span class="sxs-lookup"><span data-stu-id="6e66d-168">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="6e66d-169">Debian 10</span><span class="sxs-lookup"><span data-stu-id="6e66d-169">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-170">Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="6e66d-170">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="6e66d-171">Installatie via direct downloaden-Debian 10</span><span class="sxs-lookup"><span data-stu-id="6e66d-171">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="6e66d-172">Down load het tar. gz-pakket `powershell_7.0.0-preview-7-linux-x64.tar.gz` van de pagina [releases][] op de computer Debian.</span><span class="sxs-lookup"><span data-stu-id="6e66d-172">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="6e66d-173">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-173">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="6e66d-174">Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="6e66d-174">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-175">Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="6e66d-175">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="6e66d-176">Installatie via direct downloaden-Alpine 3,9 en 3,10</span><span class="sxs-lookup"><span data-stu-id="6e66d-176">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="6e66d-177">Down load het tar. gz-pakket `powershell_7.0.0-preview-7-linux-x64.tar.gz` van de pagina [releases][] op de Alpine machine.</span><span class="sxs-lookup"><span data-stu-id="6e66d-177">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="6e66d-178">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-178">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="6e66d-179">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-179">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-180">Dit pakket werkt op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="6e66d-180">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="6e66d-181">Installatie via pakket opslagplaats (voor keur)-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-181">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="6e66d-182">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="6e66d-183">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="6e66d-183">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="6e66d-184">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-184">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="6e66d-185">Installatie via direct downloaden-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="6e66d-186">Gebruik [CentOS 7][]om het rpm-pakket te downloaden `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de CentOS-computer.</span><span class="sxs-lookup"><span data-stu-id="6e66d-186">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="6e66d-187">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-187">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6e66d-188">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="6e66d-188">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="6e66d-189">Installatie ongedaan maken-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6e66d-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6e66d-192">Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="6e66d-193">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="6e66d-194">Als super gebruiker registreert u de micro soft-opslag plaats eenmaal.</span><span class="sxs-lookup"><span data-stu-id="6e66d-194">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="6e66d-195">Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-195">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6e66d-196">Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-196">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="6e66d-197">Down load het RPM-pakket `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Red Hat Enterprise Linux machine.</span><span class="sxs-lookup"><span data-stu-id="6e66d-197">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="6e66d-198">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-198">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6e66d-199">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="6e66d-199">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6e66d-200">Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-200">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="6e66d-201">openSUSE</span><span class="sxs-lookup"><span data-stu-id="6e66d-201">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="6e66d-202">Installatie-openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="6e66d-202">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="6e66d-203">Installatie-openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="6e66d-203">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="6e66d-204">Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="6e66d-204">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="6e66d-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="6e66d-205">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-206">Fedora 28 wordt alleen ondersteund in Power shell Core 6,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="6e66d-206">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-207">Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.</span><span class="sxs-lookup"><span data-stu-id="6e66d-207">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="6e66d-208">Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="6e66d-208">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="6e66d-209">Power shell core voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-209">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="6e66d-210">Installatie via direct downloaden-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="6e66d-210">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="6e66d-211">Down load het RPM-pakket `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="6e66d-211">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="6e66d-212">Voer vervolgens de volgende opdrachten uit in de terminal:</span><span class="sxs-lookup"><span data-stu-id="6e66d-212">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6e66d-213">U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:</span><span class="sxs-lookup"><span data-stu-id="6e66d-213">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="6e66d-214">Installatie ongedaan maken-Fedora 28, 29 en 30</span><span class="sxs-lookup"><span data-stu-id="6e66d-214">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="6e66d-215">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="6e66d-215">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-216">Arch-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="6e66d-216">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="6e66d-217">Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).</span><span class="sxs-lookup"><span data-stu-id="6e66d-217">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="6e66d-218">Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]</span><span class="sxs-lookup"><span data-stu-id="6e66d-218">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="6e66d-219">Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]</span><span class="sxs-lookup"><span data-stu-id="6e66d-219">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="6e66d-220">Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="6e66d-220">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="6e66d-221">Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="6e66d-221">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="6e66d-222">Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="6e66d-222">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="6e66d-224">Snap-pakket</span><span class="sxs-lookup"><span data-stu-id="6e66d-224">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="6e66d-225">Bezig met uitlijnen</span><span class="sxs-lookup"><span data-stu-id="6e66d-225">Getting snapd</span></span>

<span data-ttu-id="6e66d-226">`snapd` is vereist voor het uitvoeren van snaps.</span><span class="sxs-lookup"><span data-stu-id="6e66d-226">`snapd` is required to run snaps.</span></span> <span data-ttu-id="6e66d-227">Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om er zeker van te zijn dat `snapd` is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="6e66d-227">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="6e66d-228">Installatie via snap</span><span class="sxs-lookup"><span data-stu-id="6e66d-228">Installation via Snap</span></span>

<span data-ttu-id="6e66d-229">Power shell core voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.</span><span class="sxs-lookup"><span data-stu-id="6e66d-229">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="6e66d-230">De voorkeurs methode is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6e66d-230">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="6e66d-231">Als u een preview-versie wilt installeren, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="6e66d-231">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="6e66d-232">Na de installatie wordt de module automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="6e66d-232">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="6e66d-233">U kunt een upgrade activeren met behulp van `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="6e66d-233">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="6e66d-234">Installatie ongedaan maken</span><span class="sxs-lookup"><span data-stu-id="6e66d-234">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="6e66d-235">of</span><span class="sxs-lookup"><span data-stu-id="6e66d-235">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="6e66d-236">Kali</span><span class="sxs-lookup"><span data-stu-id="6e66d-236">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-237">Kali-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.</span><span class="sxs-lookup"><span data-stu-id="6e66d-237">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="6e66d-238">Installatie-Kali</span><span class="sxs-lookup"><span data-stu-id="6e66d-238">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="6e66d-239">Installatie ongedaan maken-Kali</span><span class="sxs-lookup"><span data-stu-id="6e66d-239">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="6e66d-240">Raspbian</span><span class="sxs-lookup"><span data-stu-id="6e66d-240">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="6e66d-241">Raspbian-ondersteuning is experimenteel.</span><span class="sxs-lookup"><span data-stu-id="6e66d-241">Raspbian support is experimental.</span></span>

<span data-ttu-id="6e66d-242">Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.</span><span class="sxs-lookup"><span data-stu-id="6e66d-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="6e66d-243">CoreCLR en Power shell core werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="6e66d-243">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="6e66d-244">Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.</span><span class="sxs-lookup"><span data-stu-id="6e66d-244">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="6e66d-245">Installatie-Raspbian</span><span class="sxs-lookup"><span data-stu-id="6e66d-245">Installation - Raspbian</span></span>

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

<span data-ttu-id="6e66d-246">U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar de `pwsh` binaire waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="6e66d-246">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="6e66d-247">Installatie ongedaan maken-Raspbian</span><span class="sxs-lookup"><span data-stu-id="6e66d-247">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="6e66d-248">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="6e66d-248">Binary Archives</span></span>

<span data-ttu-id="6e66d-249">Er zijn binaire Power shell-`tar.gz` archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="6e66d-249">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="6e66d-250">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="6e66d-250">Dependencies</span></span>

<span data-ttu-id="6e66d-251">Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="6e66d-251">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="6e66d-252">.NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.</span><span class="sxs-lookup"><span data-stu-id="6e66d-252">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="6e66d-253">In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="6e66d-253">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="6e66d-254">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="6e66d-254">OS</span></span>                 | <span data-ttu-id="6e66d-255">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="6e66d-255">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="6e66d-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6e66d-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="6e66d-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="6e66d-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6e66d-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="6e66d-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="6e66d-259">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="6e66d-259">Ubuntu 17.10</span></span>       | <span data-ttu-id="6e66d-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="6e66d-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6e66d-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="6e66d-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="6e66d-262">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6e66d-262">Ubuntu 18.04</span></span>       | <span data-ttu-id="6e66d-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="6e66d-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6e66d-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="6e66d-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="6e66d-265">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="6e66d-265">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="6e66d-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="6e66d-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6e66d-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="6e66d-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="6e66d-268">Debian 9 (stretch)</span><span class="sxs-lookup"><span data-stu-id="6e66d-268">Debian 9 (Stretch)</span></span> | <span data-ttu-id="6e66d-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="6e66d-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6e66d-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="6e66d-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="6e66d-271">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-271">CentOS 7</span></span> <br> <span data-ttu-id="6e66d-272">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-272">Oracle Linux 7</span></span> <br> <span data-ttu-id="6e66d-273">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="6e66d-273">RHEL 7</span></span> | <span data-ttu-id="6e66d-274">afwikkeling, libkrul, openssl-Bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="6e66d-274">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="6e66d-275">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="6e66d-275">openSUSE 42.3</span></span> | <span data-ttu-id="6e66d-276">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="6e66d-276">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="6e66d-277">openSUSE Schrikkel 15</span><span class="sxs-lookup"><span data-stu-id="6e66d-277">openSUSE Leap 15</span></span> | <span data-ttu-id="6e66d-278">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="6e66d-278">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="6e66d-279">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="6e66d-279">Fedora 27</span></span> <br> <span data-ttu-id="6e66d-280">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6e66d-280">Fedora 28</span></span> | <span data-ttu-id="6e66d-281">afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="6e66d-281">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="6e66d-282">Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren.</span><span class="sxs-lookup"><span data-stu-id="6e66d-282">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="6e66d-283">Zo installeert onze [Amazon Linux dockerfile][amazon-dockerfile] eerst afhankelijkheden en extraheert vervolgens het Linux `tar.gz`-archief.</span><span class="sxs-lookup"><span data-stu-id="6e66d-283">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="6e66d-284">Installatie-binaire archieven</span><span class="sxs-lookup"><span data-stu-id="6e66d-284">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="6e66d-285">Linux</span><span class="sxs-lookup"><span data-stu-id="6e66d-285">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="6e66d-286">Binaire archieven verwijderen</span><span class="sxs-lookup"><span data-stu-id="6e66d-286">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="6e66d-287">Paden</span><span class="sxs-lookup"><span data-stu-id="6e66d-287">Paths</span></span>

* <span data-ttu-id="6e66d-288">`$PSHOME` is `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="6e66d-288">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
* <span data-ttu-id="6e66d-289">Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6e66d-289">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="6e66d-290">Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6e66d-290">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="6e66d-291">Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6e66d-291">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6e66d-292">Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6e66d-292">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6e66d-293">Standaard modules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="6e66d-293">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="6e66d-294">De PSReadline-geschiedenis wordt geregistreerd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="6e66d-294">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="6e66d-295">De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` op dezelfde locatie bestaan.</span><span class="sxs-lookup"><span data-stu-id="6e66d-295">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="6e66d-296">Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="6e66d-296">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
