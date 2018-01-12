# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="e85b9-101">PowerShell Core installeert op Mac OS- en Linux</span><span class="sxs-lookup"><span data-stu-id="e85b9-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="e85b9-102">Ondersteunt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42,2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [boog Linux][arch], en [Mac OS 10,12][mac].</span><span class="sxs-lookup"><span data-stu-id="e85b9-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="e85b9-103">Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="e85b9-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="e85b9-104">U kunt ook proberen implementeren PowerShell binaire bestanden rechtstreeks met het Linux [ `tar.gz` archief][tar], maar u moet de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen instellen.</span><span class="sxs-lookup"><span data-stu-id="e85b9-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e85b9-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="e85b9-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e85b9-106">Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.</span><span class="sxs-lookup"><span data-stu-id="e85b9-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="e85b9-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e85b9-108">Installatie via pakket opslagplaats - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e85b9-109">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e85b9-110">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="e85b9-110">This is the preferred method.</span></span>

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

<span data-ttu-id="e85b9-111">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e85b9-112">Installatie via directe Download - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e85b9-113">Download het Debian-pakket `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-113">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e85b9-114">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e85b9-115">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e85b9-116">Verwijdering - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e85b9-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e85b9-118">Installatie via pakket opslagplaats - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e85b9-119">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e85b9-120">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="e85b9-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e85b9-121">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e85b9-122">Installatie via directe Download - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e85b9-123">Download het Debian-pakket `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-123">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e85b9-124">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e85b9-125">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e85b9-126">Verwijdering - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="e85b9-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="e85b9-128">Installatie via pakket opslagplaats - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="e85b9-129">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e85b9-130">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="e85b9-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e85b9-131">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="e85b9-132">Installatie via directe Download - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="e85b9-133">Download het Debian-pakket `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-133">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e85b9-134">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e85b9-135">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="e85b9-136">Verwijdering - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="e85b9-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e85b9-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e85b9-138">Installatie via pakket opslagplaats - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e85b9-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e85b9-139">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e85b9-140">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="e85b9-140">This is the preferred method.</span></span>

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

<span data-ttu-id="e85b9-141">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e85b9-142">Installatie via directe Download - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e85b9-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e85b9-143">Download het Debian-pakket `powershell_6.0.0-rc-1.debian.8_amd64.deb` van de [releases][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-143">Download the Debian package `powershell_6.0.0-rc-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e85b9-144">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e85b9-145">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e85b9-146">Verwijdering - Debian 8</span><span class="sxs-lookup"><span data-stu-id="e85b9-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e85b9-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e85b9-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e85b9-148">Installatie via pakket opslagplaats - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e85b9-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e85b9-149">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e85b9-150">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="e85b9-150">This is the preferred method.</span></span>

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

<span data-ttu-id="e85b9-151">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e85b9-152">Installatie via directe Download - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e85b9-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e85b9-153">Download het Debian-pakket `powershell_6.0.0-rc-1.debian.9_amd64.deb` van de [releases][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-153">Download the Debian package `powershell_6.0.0-rc-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e85b9-154">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e85b9-155">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e85b9-156">Verwijdering - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e85b9-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e85b9-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-157">CentOS 7</span></span>

> <span data-ttu-id="e85b9-158">Dit pakket werkt ook op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e85b9-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e85b9-159">Installatie via pakket opslagplaats (voorkeur) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e85b9-160">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e85b9-161">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e85b9-162">Installatie via directe Download - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e85b9-163">Met behulp van [CentOS 7][], downloaden de RPM-pakket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine CentOS.</span><span class="sxs-lookup"><span data-stu-id="e85b9-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e85b9-164">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e85b9-165">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="e85b9-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e85b9-166">Verwijdering - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e85b9-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e85b9-169">Installatie via pakket opslagplaats (voorkeur) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e85b9-170">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e85b9-171">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e85b9-172">Installatie via directe Download - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e85b9-173">Download het pakket RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` van de [releases][] pagina naar de Red Hat Enterprise Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-173">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e85b9-174">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e85b9-175">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="e85b9-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e85b9-176">Verwijdering - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="e85b9-177">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="e85b9-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="e85b9-178">**Opmerking:** bij de installatie van PowerShell Core OpenSUSE kan rapporteren dat niets biedt `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="e85b9-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="e85b9-179">`libcurl`al is geïnstalleerd op alle ondersteunde versies van OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="e85b9-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="e85b9-180">Voer `zypper search libcurl` om te bevestigen.</span><span class="sxs-lookup"><span data-stu-id="e85b9-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="e85b9-181">De fout geeft 2 oplossingen.</span><span class="sxs-lookup"><span data-stu-id="e85b9-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="e85b9-182">Kies oplossing 2 om door te gaan met PowerShell Core installeren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="e85b9-183">Installatie via pakket opslagplaats (voorkeur) - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="e85b9-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="e85b9-184">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="e85b9-185">Installatie via directe Download - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="e85b9-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="e85b9-186">Download het pakket RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="e85b9-186">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e85b9-187">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="e85b9-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="e85b9-188">Verwijdering - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="e85b9-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="e85b9-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e85b9-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="e85b9-190">Installatie via pakket opslagplaats (voorkeur) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e85b9-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="e85b9-191">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="e85b9-192">Installatie via directe Download - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e85b9-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="e85b9-193">Download het pakket RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora.</span><span class="sxs-lookup"><span data-stu-id="e85b9-193">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e85b9-194">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e85b9-195">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="e85b9-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="e85b9-196">Verwijdering - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e85b9-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="e85b9-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e85b9-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="e85b9-198">Installatie via pakket opslagplaats (voorkeur) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e85b9-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="e85b9-199">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="e85b9-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="e85b9-200">Installatie via directe Download - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e85b9-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="e85b9-201">Download het pakket RPM `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora.</span><span class="sxs-lookup"><span data-stu-id="e85b9-201">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e85b9-202">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e85b9-203">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="e85b9-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="e85b9-204">Verwijdering - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e85b9-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e85b9-205">Boog Linux</span><span class="sxs-lookup"><span data-stu-id="e85b9-205">Arch Linux</span></span>

<span data-ttu-id="e85b9-206">PowerShell is beschikbaar via de [Arch Linux][] gebruiker opslagplaats (AUR).</span><span class="sxs-lookup"><span data-stu-id="e85b9-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e85b9-207">Het kan worden gecompileerd met het [meest recente release met tags][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e85b9-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e85b9-208">Het kan worden gecompileerd uit de [nieuwste doorvoeren naar het hoofdniveau][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e85b9-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e85b9-209">Kan worden geïnstalleerd met de [binair de meest recente release][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e85b9-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e85b9-210">Pakketten in de AUR community bewaard zijn: Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="e85b9-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e85b9-211">Zie voor meer informatie over het installeren van pakketten uit de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e85b9-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="e85b9-213">Linux-AppImage</span><span class="sxs-lookup"><span data-stu-id="e85b9-213">Linux AppImage</span></span>

<span data-ttu-id="e85b9-214">Gebruik van een recente Linux-distributie, downloaden de AppImage `powershell-6.0.0-rc-x86_64.AppImage` van de [releases][] pagina naar de Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-rc-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="e85b9-215">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-rc-x86_64.AppImage
./powershell-6.0.0-rc-x86_64.AppImage
```

<span data-ttu-id="e85b9-216">De [AppImage][] kunt u PowerShell uitvoeren zonder het te installeren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-216">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="e85b9-217">Dit is een draagbare toepassing die u verzamelt van PowerShell en de afhankelijkheden ervan (inclusief .NET-Core system afhankelijkheden) in één samenhangender pakket.</span><span class="sxs-lookup"><span data-stu-id="e85b9-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="e85b9-218">Dit pakket werkt onafhankelijk van de Linux-distributie van de gebruiker en een enkele binaire waarde is.</span><span class="sxs-lookup"><span data-stu-id="e85b9-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="e85b9-220">Mac OS 10,12</span><span class="sxs-lookup"><span data-stu-id="e85b9-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="e85b9-221">Installatie via Homebrew (voorkeur) - Mac OS 10,12</span><span class="sxs-lookup"><span data-stu-id="e85b9-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="e85b9-222">[Homebrew] [ brew] is de ontbrekende package manager voor Mac OS.</span><span class="sxs-lookup"><span data-stu-id="e85b9-222">[Homebrew][brew] is the missing package manager for macOS.</span></span>
<span data-ttu-id="e85b9-223">Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew geïnstalleerd [hun instructies][brew].</span><span class="sxs-lookup"><span data-stu-id="e85b9-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="e85b9-224">Zodra u Homebrew hebt geïnstalleerd, is het eenvoudig om PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="e85b9-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="e85b9-225">Installeer eerst [Homebrew Cask][cask], zodat u kunt meer pakketten installeren:</span><span class="sxs-lookup"><span data-stu-id="e85b9-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="e85b9-226">U kunt nu PowerShell installeren:</span><span class="sxs-lookup"><span data-stu-id="e85b9-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="e85b9-227">Wanneer er nieuwe versies van PowerShell zijn uitgebracht, Homebrew van formules bijwerken en upgrade uitvoeren van PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e85b9-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="e85b9-228">Opmerking:-vanwege van [dit probleem in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), u hebt momenteel doen opnieuw moet installeren om bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e85b9-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="e85b9-229">Installatie via de directe Download - Mac OS 10,12</span><span class="sxs-lookup"><span data-stu-id="e85b9-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="e85b9-230">Pak het pakket met behulp van Mac OS 10,12 downloaden `powershell-6.0.0-rc-osx.10.12-x64.pkg` van de [releases][] pagina op de Mac OS-machine.</span><span class="sxs-lookup"><span data-stu-id="e85b9-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-rc-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="e85b9-231">Dubbelklik op het bestand en volg de aanwijzingen, noch installeren vanaf de terminal:</span><span class="sxs-lookup"><span data-stu-id="e85b9-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-rc-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="e85b9-232">Verwijdering - Mac OS 10,12</span><span class="sxs-lookup"><span data-stu-id="e85b9-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="e85b9-233">Als u met Homebrew PowerShell hebt geïnstalleerd, is het verwijderen is eenvoudig:</span><span class="sxs-lookup"><span data-stu-id="e85b9-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="e85b9-234">Als u via de directe download PowerShell hebt geïnstalleerd, moet PowerShell handmatig worden verwijderd:</span><span class="sxs-lookup"><span data-stu-id="e85b9-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="e85b9-235">Verwijder de extra PowerShell-paden (zoals het pad van het gebruikersprofiel) raadpleegt u de [paden] [ paths] onder sectie in dit document en verwijdert u de gewenste de paden met `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="e85b9-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span>
<span data-ttu-id="e85b9-236">(Opmerking: dit is niet nodig als u met Homebrew geïnstalleerd.)</span><span class="sxs-lookup"><span data-stu-id="e85b9-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="e85b9-237">Kali</span><span class="sxs-lookup"><span data-stu-id="e85b9-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="e85b9-238">Installatie</span><span class="sxs-lookup"><span data-stu-id="e85b9-238">Installation</span></span>

```sh
# Install prerequisites
apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="e85b9-239">PowerShell uitvoeren in de meest recente Kali (Kali GNU/Linux Rolling) zonder het te installeren</span><span class="sxs-lookup"><span data-stu-id="e85b9-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-rc-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-rc-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e85b9-240">Verwijdering - Kali</span><span class="sxs-lookup"><span data-stu-id="e85b9-240">Uninstallation - Kali</span></span>

```sh
dpkg -r powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="e85b9-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e85b9-241">Raspbian</span></span>

<span data-ttu-id="e85b9-242">PowerShell is momenteel alleen ondersteund op Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e85b9-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="e85b9-243">Installatie</span><span class="sxs-lookup"><span data-stu-id="e85b9-243">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-rc-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e85b9-244">Verwijdering - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e85b9-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e85b9-245">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="e85b9-245">Binary Archives</span></span>

<span data-ttu-id="e85b9-246">PowerShell binair `tar.gz` archieven voor Mac OS- en Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="e85b9-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e85b9-247">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="e85b9-247">Dependencies</span></span>

<span data-ttu-id="e85b9-248">Voor Linux bouwt PowerShell draagbare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="e85b9-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e85b9-249">Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en daarom PowerShell hetzelfde effect heeft.</span><span class="sxs-lookup"><span data-stu-id="e85b9-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e85b9-250">Het volgende diagram toont de afhankelijkheden .NET Core 2.0 op verschillende Linux-distributies die officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e85b9-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="e85b9-251">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="e85b9-251">OS</span></span>                 | <span data-ttu-id="e85b9-252">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="e85b9-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e85b9-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="e85b9-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e85b9-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e85b9-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e85b9-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e85b9-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="e85b9-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e85b9-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e85b9-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e85b9-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e85b9-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e85b9-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="e85b9-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e85b9-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e85b9-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e85b9-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e85b9-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e85b9-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e85b9-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e85b9-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e85b9-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e85b9-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e85b9-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e85b9-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e85b9-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="e85b9-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e85b9-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e85b9-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e85b9-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-268">CentOS 7</span></span> <br> <span data-ttu-id="e85b9-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="e85b9-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e85b9-270">RHEL 7</span></span> <br> <span data-ttu-id="e85b9-271">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="e85b9-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="e85b9-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e85b9-272">Fedora 25</span></span> | <span data-ttu-id="e85b9-273">libunwind, libcurl, openssl-bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="e85b9-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e85b9-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e85b9-274">Fedora 26</span></span>          | <span data-ttu-id="e85b9-275">libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="e85b9-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e85b9-276">Als u wilt implementeren PowerShell binaire bestanden op Linux-distributies die officieel niet worden ondersteund, moet u voor het installeren van de vereiste afhankelijkheden voor het doel OS in afzonderlijke stappen.</span><span class="sxs-lookup"><span data-stu-id="e85b9-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e85b9-277">Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden als eerste geïnstalleerd en pakt vervolgens de Linux `tar.gz` archief.</span><span class="sxs-lookup"><span data-stu-id="e85b9-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e85b9-278">Installatie - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="e85b9-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e85b9-279">Linux</span><span class="sxs-lookup"><span data-stu-id="e85b9-279">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0-rc/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="e85b9-280">Mac OS</span><span class="sxs-lookup"><span data-stu-id="e85b9-280">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0-rc/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="e85b9-281">Verwijdering - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="e85b9-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e85b9-282">Linux</span><span class="sxs-lookup"><span data-stu-id="e85b9-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="e85b9-283">Mac OS</span><span class="sxs-lookup"><span data-stu-id="e85b9-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e85b9-284">Paden</span><span class="sxs-lookup"><span data-stu-id="e85b9-284">Paths</span></span>

* <span data-ttu-id="e85b9-285">`$PSHOME`is`/opt/microsoft/powershell/6.0.0-rc/`</span><span class="sxs-lookup"><span data-stu-id="e85b9-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0-rc/`</span></span>
* <span data-ttu-id="e85b9-286">Gebruikersprofielen worden gelezen uit`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e85b9-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e85b9-287">Standaardprofielen worden gelezen uit`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e85b9-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e85b9-288">Gebruikersmodules worden gelezen uit`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e85b9-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e85b9-289">Gedeelde modules worden gelezen uit`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e85b9-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e85b9-290">Standaardmodules worden gelezen uit`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e85b9-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e85b9-291">Geschiedenis van PSReadline wordt vastgelegd`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e85b9-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e85b9-292">De profielen respecteren van PowerShell per host-configuratie, zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="e85b9-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e85b9-293">Op Linux- en Mac OS, de [XDG Base Directory specificatie] [ xdg-bds] is voldaan.</span><span class="sxs-lookup"><span data-stu-id="e85b9-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="e85b9-294">Omdat Mac OS is geen afwijking van BSD, in plaats van `/opt`, het voorvoegsel dat gebruikt is `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="e85b9-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span>
<span data-ttu-id="e85b9-295">Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0-rc/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="e85b9-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0-rc/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
