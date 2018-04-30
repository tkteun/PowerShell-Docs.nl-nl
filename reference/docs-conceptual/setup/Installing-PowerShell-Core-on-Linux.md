# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="b7cb9-101">PowerShell Core installeren op Linux</span><span class="sxs-lookup"><span data-stu-id="b7cb9-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="b7cb9-102">Ondersteunt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42,2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], en [boog Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="b7cb9-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], and [Arch Linux][arch].</span></span>

<span data-ttu-id="b7cb9-103">Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="b7cb9-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="b7cb9-104">U kunt ook proberen implementeren PowerShell binaire bestanden rechtstreeks met het Linux [ `tar.gz` archief][tar], maar u moet de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen instellen.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="b7cb9-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b7cb9-106">Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="b7cb9-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="b7cb9-108">Installatie via pakket opslagplaats - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="b7cb9-109">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b7cb9-110">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-110">This is the preferred method.</span></span>

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

<span data-ttu-id="b7cb9-111">Als beheerder, registreert u de Microsoft-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="b7cb9-112">Daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bijwerken van de installatie.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="b7cb9-113">Installatie via directe Download - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="b7cb9-114">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b7cb9-115">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b7cb9-116">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="b7cb9-117">Verwijdering - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="b7cb9-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="b7cb9-119">Installatie via pakket opslagplaats - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="b7cb9-120">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b7cb9-121">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-121">This is the preferred method.</span></span>

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

<span data-ttu-id="b7cb9-122">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="b7cb9-123">Installatie via directe Download - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="b7cb9-124">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b7cb9-125">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b7cb9-126">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="b7cb9-127">Verwijdering - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="b7cb9-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="b7cb9-129">Installatie via pakket opslagplaats - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="b7cb9-130">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b7cb9-131">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b7cb9-132">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="b7cb9-133">Installatie via directe Download - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="b7cb9-134">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b7cb9-135">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b7cb9-136">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="b7cb9-137">Verwijdering - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="b7cb9-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="b7cb9-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="b7cb9-139">Installatie via pakket opslagplaats - Debian 8</span><span class="sxs-lookup"><span data-stu-id="b7cb9-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="b7cb9-140">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b7cb9-141">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-141">This is the preferred method.</span></span>

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

<span data-ttu-id="b7cb9-142">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="b7cb9-143">Installatie via directe Download - Debian 8</span><span class="sxs-lookup"><span data-stu-id="b7cb9-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="b7cb9-144">Download het Debian-pakket `powershell_6.0.2-1.debian.8_amd64.deb` van de [releases][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b7cb9-145">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b7cb9-146">Houd er rekening mee dat `dpkg -i` mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="b7cb9-147">De volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="b7cb9-148">Verwijdering - Debian 8</span><span class="sxs-lookup"><span data-stu-id="b7cb9-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="b7cb9-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="b7cb9-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="b7cb9-150">Installatie via pakket opslagplaats - Debian 9</span><span class="sxs-lookup"><span data-stu-id="b7cb9-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="b7cb9-151">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b7cb9-152">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-152">This is the preferred method.</span></span>

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

<span data-ttu-id="b7cb9-153">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="b7cb9-154">Installatie via directe Download - Debian 9</span><span class="sxs-lookup"><span data-stu-id="b7cb9-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="b7cb9-155">Download het Debian-pakket `powershell_6.0.2-1.debian.9_amd64.deb` van de [releases][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b7cb9-156">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b7cb9-157">Houd er rekening mee dat `dpkg -i` mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="b7cb9-158">De volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="b7cb9-159">Verwijdering - Debian 9</span><span class="sxs-lookup"><span data-stu-id="b7cb9-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="b7cb9-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-160">CentOS 7</span></span>

> <span data-ttu-id="b7cb9-161">Dit pakket werkt ook op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="b7cb9-162">Installatie via pakket opslagplaats (voorkeur) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="b7cb9-163">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b7cb9-164">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="b7cb9-165">Installatie via directe Download - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="b7cb9-166">Met behulp van [CentOS 7][], downloaden de RPM-pakket `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine CentOS.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="b7cb9-167">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b7cb9-168">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="b7cb9-169">Verwijdering - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b7cb9-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b7cb9-172">Installatie via pakket opslagplaats (voorkeur) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b7cb9-173">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b7cb9-174">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b7cb9-175">Installatie via directe Download - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b7cb9-176">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina naar de Red Hat Enterprise Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="b7cb9-177">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b7cb9-178">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b7cb9-179">Verwijdering - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="b7cb9-180">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="b7cb9-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="b7cb9-181">Bij de installatie van PowerShell Core `zypper` mogelijk de volgende fout te melden:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="b7cb9-182">In dit geval controleren of een compatibel `libcurl` bibliotheek aanwezig is, door te controleren dat de volgende geeft opdracht de `libcurl4` pakket geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="b7cb9-183">Kies vervolgens de `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` oplossing wanneer de PowerShell-pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="b7cb9-184">Installatie via pakket opslagplaats (voorkeur) - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="b7cb9-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="b7cb9-185">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="b7cb9-186">Installatie via directe Download - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="b7cb9-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="b7cb9-187">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b7cb9-188">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="b7cb9-189">Verwijdering - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="b7cb9-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="b7cb9-190">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b7cb9-190">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="b7cb9-191">Installatie via pakket opslagplaats (voorkeur) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b7cb9-191">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="b7cb9-192">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="b7cb9-193">Installatie via directe Download - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b7cb9-193">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="b7cb9-194">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b7cb9-195">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b7cb9-196">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="b7cb9-197">Verwijdering - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b7cb9-197">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="b7cb9-198">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b7cb9-198">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="b7cb9-199">Installatie via pakket opslagplaats (voorkeur) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b7cb9-199">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="b7cb9-200">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-200">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="b7cb9-201">Installatie via directe Download - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b7cb9-201">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="b7cb9-202">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-202">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="b7cb9-203">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-203">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b7cb9-204">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="b7cb9-205">Verwijdering - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b7cb9-205">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="b7cb9-206">Boog Linux</span><span class="sxs-lookup"><span data-stu-id="b7cb9-206">Arch Linux</span></span>

<span data-ttu-id="b7cb9-207">PowerShell is beschikbaar via de [Arch Linux][] gebruiker opslagplaats (AUR).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-207">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="b7cb9-208">Het kan worden gecompileerd met het [meest recente release met tags][arch-release]</span><span class="sxs-lookup"><span data-stu-id="b7cb9-208">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="b7cb9-209">Het kan worden gecompileerd uit de [nieuwste doorvoeren naar het hoofdniveau][arch-git]</span><span class="sxs-lookup"><span data-stu-id="b7cb9-209">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="b7cb9-210">Kan worden geïnstalleerd met de [binair de meest recente release][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="b7cb9-210">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="b7cb9-211">Pakketten in de AUR community bewaard zijn: Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-211">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="b7cb9-212">Zie voor meer informatie over het installeren van pakketten uit de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="b7cb9-212">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="b7cb9-214">Linux-AppImage</span><span class="sxs-lookup"><span data-stu-id="b7cb9-214">Linux AppImage</span></span>

<span data-ttu-id="b7cb9-215">Gebruik van een recente Linux-distributie, downloaden de AppImage `powershell-6.0.1-x86_64.AppImage` van de [releases][] pagina naar de Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-215">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="b7cb9-216">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="b7cb9-216">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="b7cb9-217">De [AppImage][] kunt u PowerShell uitvoeren zonder het te installeren.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-217">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="b7cb9-218">Dit is een draagbare toepassing die u verzamelt van PowerShell en de afhankelijkheden ervan (inclusief .NET-Core system afhankelijkheden) in één samenhangender pakket.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-218">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="b7cb9-219">Dit pakket is een enkele binaire waarde die geschikt is onafhankelijk van de Linux-distributie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-219">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="b7cb9-221">Kali</span><span class="sxs-lookup"><span data-stu-id="b7cb9-221">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="b7cb9-222">Installatie</span><span class="sxs-lookup"><span data-stu-id="b7cb9-222">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="b7cb9-223">PowerShell uitvoeren in de meest recente Kali (Kali GNU/Linux Rolling) zonder het te installeren</span><span class="sxs-lookup"><span data-stu-id="b7cb9-223">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="b7cb9-224">Verwijdering - Kali</span><span class="sxs-lookup"><span data-stu-id="b7cb9-224">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="b7cb9-225">Raspbian</span><span class="sxs-lookup"><span data-stu-id="b7cb9-225">Raspbian</span></span>

<span data-ttu-id="b7cb9-226">PowerShell is momenteel alleen ondersteund op Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-226">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="b7cb9-227">Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten Pi 2 en 3 Pi als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-227">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="b7cb9-228">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) downloaden naar uw Pi.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-228">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="b7cb9-229">Installatie</span><span class="sxs-lookup"><span data-stu-id="b7cb9-229">Installation</span></span>

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

<span data-ttu-id="b7cb9-230">U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven van pad naar de binaire 'pwsh' maken</span><span class="sxs-lookup"><span data-stu-id="b7cb9-230">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="b7cb9-231">Verwijdering - Raspbian</span><span class="sxs-lookup"><span data-stu-id="b7cb9-231">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="b7cb9-232">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="b7cb9-232">Binary Archives</span></span>

<span data-ttu-id="b7cb9-233">PowerShell binair `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-233">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="b7cb9-234">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="b7cb9-234">Dependencies</span></span>

<span data-ttu-id="b7cb9-235">PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-235">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="b7cb9-236">Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en daarom PowerShell hetzelfde effect heeft.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-236">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="b7cb9-237">Het volgende diagram toont de afhankelijkheden voor .NET Core 2.0 die officieel ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-237">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="b7cb9-238">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="b7cb9-238">OS</span></span>                 | <span data-ttu-id="b7cb9-239">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="b7cb9-239">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="b7cb9-240">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-240">Ubuntu 14.04</span></span>       | <span data-ttu-id="b7cb9-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b7cb9-241">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b7cb9-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b7cb9-242">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b7cb9-243">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-243">Ubuntu 16.04</span></span>       | <span data-ttu-id="b7cb9-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b7cb9-244">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b7cb9-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="b7cb9-245">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="b7cb9-246">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b7cb9-246">Ubuntu 17.04</span></span>       | <span data-ttu-id="b7cb9-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b7cb9-247">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b7cb9-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="b7cb9-248">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="b7cb9-249">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="b7cb9-249">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="b7cb9-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b7cb9-250">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b7cb9-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b7cb9-251">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b7cb9-252">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="b7cb9-252">Debian 9 (Stretch)</span></span> | <span data-ttu-id="b7cb9-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="b7cb9-253">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b7cb9-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="b7cb9-254">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="b7cb9-255">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-255">CentOS 7</span></span> <br> <span data-ttu-id="b7cb9-256">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-256">Oracle Linux 7</span></span> <br> <span data-ttu-id="b7cb9-257">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="b7cb9-257">RHEL 7</span></span> <br> <span data-ttu-id="b7cb9-258">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="b7cb9-258">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="b7cb9-259">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b7cb9-259">Fedora 25</span></span> | <span data-ttu-id="b7cb9-260">libunwind, libcurl, openssl-bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="b7cb9-260">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="b7cb9-261">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b7cb9-261">Fedora 26</span></span>          | <span data-ttu-id="b7cb9-262">libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="b7cb9-262">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="b7cb9-263">U moet de vereiste afhankelijkheden voor het doel OS installeren in afzonderlijke stappen voor het implementeren van de binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-263">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="b7cb9-264">Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden als eerste geïnstalleerd en pakt vervolgens de Linux `tar.gz` archief.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-264">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="b7cb9-265">Installatie - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="b7cb9-265">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b7cb9-266">Linux</span><span class="sxs-lookup"><span data-stu-id="b7cb9-266">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="b7cb9-267">Verwijderen binaire archieven</span><span class="sxs-lookup"><span data-stu-id="b7cb9-267">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="b7cb9-268">Paden</span><span class="sxs-lookup"><span data-stu-id="b7cb9-268">Paths</span></span>

* <span data-ttu-id="b7cb9-269">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="b7cb9-269">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="b7cb9-270">Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b7cb9-270">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b7cb9-271">Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b7cb9-271">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b7cb9-272">Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b7cb9-272">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b7cb9-273">Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b7cb9-273">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b7cb9-274">Standaardmodules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="b7cb9-274">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b7cb9-275">Geschiedenis van PSReadline wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b7cb9-275">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b7cb9-276">De profielen respecteren van PowerShell per host-configuratie, zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-276">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b7cb9-277">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="b7cb9-277">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
