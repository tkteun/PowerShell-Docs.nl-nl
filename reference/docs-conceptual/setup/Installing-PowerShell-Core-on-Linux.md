# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="727e6-101">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="727e6-101">Installing PowerShell Core on Linux</span></span>

Supports <bpt id="p1">[</bpt>Ubuntu 14.04<ept id="p1">]</ept><bpt id="p2">[</bpt><ept id="p2">u14]</ept>, <bpt id="p3">[</bpt>Ubuntu 16.04<ept id="p3">]</ept><bpt id="p4">[</bpt><ept id="p4">u16]</ept>, <bpt id="p5">[</bpt>Ubuntu 17.04<ept id="p5">]</ept><bpt id="p6">[</bpt><ept id="p6">u17]</ept>, <bpt id="p7">[</bpt>Debian 8<ept id="p7">]</ept><bpt id="p8">[</bpt><ept id="p8">deb8]</ept>, <bpt id="p9">[</bpt>Debian 9<ept id="p9">]</ept><bpt id="p10">[</bpt><ept id="p10">deb9]</ept>, <bpt id="p11">[</bpt>CentOS 7<ept id="p11">]</ept><bpt id="p12">[</bpt><ept id="p12">cos]</ept>, <bpt id="p13">[</bpt>Red Hat Enterprise Linux (RHEL) 7<ept id="p13">]</ept><bpt id="p14">[</bpt><ept id="p14">rhel7]</ept>, <bpt id="p15">[</bpt>OpenSUSE 42.2<ept id="p15">]</ept><bpt id="p16">[</bpt><ept id="p16">opensuse]</ept>, <bpt id="p17">[</bpt>Fedora 27<ept id="p17">]</ept><bpt id="p18">[</bpt><ept id="p18">fedora]</ept>, <bpt id="p19">[</bpt>Fedora 28<ept id="p19">]</ept><bpt id="p20">[</bpt><ept id="p20">fedora]</ept>, and <bpt id="p21">[</bpt>Arch Linux<ept id="p21">]</ept><bpt id="p22">[</bpt><ept id="p22">arch]</ept>.

<span data-ttu-id="727e6-103">Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="727e6-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="727e6-104">U kunt ook proberen implementeren PowerShell binaire bestanden rechtstreeks met het Linux [ `tar.gz` archief][tar], maar u moet de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen instellen.</span><span class="sxs-lookup"><span data-stu-id="727e6-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="727e6-105">Alle pakketten zijn beschikbaar op onze GitHub [Versies][] pagina.</span><span class="sxs-lookup"><span data-stu-id="727e6-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="727e6-106">Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.</span><span class="sxs-lookup"><span data-stu-id="727e6-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="727e6-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="727e6-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="727e6-108">Installatie via pakket opslagplaats - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="727e6-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="727e6-109">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="727e6-110">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="727e6-110">This is the preferred method.</span></span>

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

<span data-ttu-id="727e6-111">Als beheerder, registreert u de Microsoft-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="727e6-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="727e6-112">Daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bijwerken van de installatie.</span><span class="sxs-lookup"><span data-stu-id="727e6-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="727e6-113">Installatie via directe Download - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="727e6-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="727e6-114">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` van de [Versies][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="727e6-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="727e6-115">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="727e6-116">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="727e6-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="727e6-117">Verwijdering - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="727e6-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="727e6-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="727e6-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="727e6-119">Installatie via pakket opslagplaats - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="727e6-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="727e6-120">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="727e6-121">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="727e6-121">This is the preferred method.</span></span>

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

<span data-ttu-id="727e6-122">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="727e6-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="727e6-123">Installatie via directe Download - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="727e6-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="727e6-124">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` van de [Versies][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="727e6-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="727e6-125">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="727e6-126">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="727e6-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="727e6-127">Verwijdering - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="727e6-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="727e6-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="727e6-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="727e6-129">Installatie via pakket opslagplaats - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="727e6-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="727e6-130">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="727e6-131">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="727e6-131">This is the preferred method.</span></span>

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

<span data-ttu-id="727e6-132">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="727e6-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="727e6-133">Installatie via directe Download - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="727e6-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="727e6-134">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` van de [Versies][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="727e6-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="727e6-135">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="727e6-136">Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="727e6-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="727e6-137">Verwijdering - Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="727e6-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="727e6-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="727e6-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="727e6-139">Installatie via pakket opslagplaats - Debian 8</span><span class="sxs-lookup"><span data-stu-id="727e6-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="727e6-140">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="727e6-141">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="727e6-141">This is the preferred method.</span></span>

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

<span data-ttu-id="727e6-142">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="727e6-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="727e6-143">Installatie via directe Download - Debian 8</span><span class="sxs-lookup"><span data-stu-id="727e6-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="727e6-144">Download het Debian-pakket `powershell_6.0.2-1.debian.8_amd64.deb` van de [Versies][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="727e6-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="727e6-145">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="727e6-146">Houd er rekening mee dat `dpkg -i` mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="727e6-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="727e6-147">De volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="727e6-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="727e6-148">Verwijdering - Debian 8</span><span class="sxs-lookup"><span data-stu-id="727e6-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="727e6-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="727e6-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="727e6-150">Installatie via pakket opslagplaats - Debian 9</span><span class="sxs-lookup"><span data-stu-id="727e6-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="727e6-151">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="727e6-152">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="727e6-152">This is the preferred method.</span></span>

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

<span data-ttu-id="727e6-153">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="727e6-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="727e6-154">Installatie via directe Download - Debian 9</span><span class="sxs-lookup"><span data-stu-id="727e6-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="727e6-155">Download het Debian-pakket `powershell_6.0.2-1.debian.9_amd64.deb` van de [Versies][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="727e6-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="727e6-156">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="727e6-157">Houd er rekening mee dat `dpkg -i` mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="727e6-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="727e6-158">De volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.</span><span class="sxs-lookup"><span data-stu-id="727e6-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="727e6-159">Verwijdering - Debian 9</span><span class="sxs-lookup"><span data-stu-id="727e6-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="727e6-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="727e6-160">CentOS 7</span></span>

> <span data-ttu-id="727e6-161">Dit pakket werkt ook op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="727e6-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="727e6-162">Installatie via pakket opslagplaats (voorkeur) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="727e6-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="727e6-163">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="727e6-164">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="727e6-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="727e6-165">Installatie via directe Download - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="727e6-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="727e6-166">Met behulp van [CentOS 7][], downloaden de RPM-pakket `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [Versies][] pagina op de machine CentOS.</span><span class="sxs-lookup"><span data-stu-id="727e6-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="727e6-167">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="727e6-168">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="727e6-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="727e6-169">Verwijdering - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="727e6-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="727e6-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="727e6-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="727e6-172">Installatie via pakket opslagplaats (voorkeur) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="727e6-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="727e6-173">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="727e6-174">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="727e6-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="727e6-175">Installatie via directe Download - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="727e6-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="727e6-176">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [Versies][] pagina naar de Red Hat Enterprise Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="727e6-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="727e6-177">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="727e6-178">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="727e6-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="727e6-179">Verwijdering - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="727e6-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="727e6-180">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="727e6-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="727e6-181">Bij de installatie van PowerShell Core `zypper` mogelijk de volgende fout te melden:</span><span class="sxs-lookup"><span data-stu-id="727e6-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="727e6-182">In dit geval controleren of een compatibel `libcurl` bibliotheek aanwezig is, door te controleren dat de volgende geeft opdracht de `libcurl4` pakket geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="727e6-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="727e6-183">Kies vervolgens de `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` oplossing wanneer de PowerShell-pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="727e6-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="727e6-184">Installatie via pakket opslagplaats (voorkeur) - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="727e6-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="727e6-185">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="727e6-186">Installatie via directe Download - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="727e6-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="727e6-187">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [Versies][] pagina op de machine OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="727e6-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="727e6-188">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="727e6-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="727e6-189">Verwijdering - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="727e6-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="727e6-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="727e6-190">Fedora</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="727e6-191">Installatie via pakket opslagplaats (voorkeur) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="727e6-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="727e6-192">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="727e6-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="727e6-193">Installatie via directe Download - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="727e6-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="727e6-194">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [Versies][] pagina op de machine Fedora.</span><span class="sxs-lookup"><span data-stu-id="727e6-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="727e6-195">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="727e6-196">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="727e6-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="727e6-197">Verwijdering - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="727e6-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="727e6-198">Boog Linux</span><span class="sxs-lookup"><span data-stu-id="727e6-198">Arch Linux</span></span>

<span data-ttu-id="727e6-199">PowerShell is beschikbaar via de [Boog Linux][] gebruiker opslagplaats (AUR).</span><span class="sxs-lookup"><span data-stu-id="727e6-199">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="727e6-200">Het kan worden gecompileerd met het [meest recente release met tags][arch-release]</span><span class="sxs-lookup"><span data-stu-id="727e6-200">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="727e6-201">Het kan worden gecompileerd uit de [nieuwste doorvoeren naar het hoofdniveau][arch-git]</span><span class="sxs-lookup"><span data-stu-id="727e6-201">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="727e6-202">Kan worden geïnstalleerd met de [binair de meest recente release][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="727e6-202">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="727e6-203">Pakketten in de AUR community bewaard zijn: Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="727e6-203">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="727e6-204">Zie voor meer informatie over het installeren van pakketten uit de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="727e6-204">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Boog Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="727e6-206">Linux-AppImage</span><span class="sxs-lookup"><span data-stu-id="727e6-206">Linux AppImage</span></span>

<span data-ttu-id="727e6-207">Gebruik van een recente Linux-distributie, downloaden de AppImage `powershell-6.0.1-x86_64.AppImage` van de [Versies][] pagina naar de Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="727e6-207">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="727e6-208">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="727e6-208">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="727e6-209">De [AppImage][] kunt u PowerShell uitvoeren zonder het te installeren.</span><span class="sxs-lookup"><span data-stu-id="727e6-209">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="727e6-210">Dit is een draagbare toepassing die u verzamelt van PowerShell en de afhankelijkheden ervan (inclusief .NET-Core system afhankelijkheden) in één samenhangender pakket.</span><span class="sxs-lookup"><span data-stu-id="727e6-210">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="727e6-211">Dit pakket is een enkele binaire waarde die geschikt is onafhankelijk van de Linux-distributie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="727e6-211">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="727e6-213">Kali</span><span class="sxs-lookup"><span data-stu-id="727e6-213">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="727e6-214">Installatie</span><span class="sxs-lookup"><span data-stu-id="727e6-214">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="727e6-215">PowerShell uitvoeren in de meest recente Kali (Kali GNU/Linux Rolling) zonder het te installeren</span><span class="sxs-lookup"><span data-stu-id="727e6-215">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="727e6-216">Verwijdering - Kali</span><span class="sxs-lookup"><span data-stu-id="727e6-216">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="727e6-217">Raspbian</span><span class="sxs-lookup"><span data-stu-id="727e6-217">Raspbian</span></span>

<span data-ttu-id="727e6-218">PowerShell is momenteel alleen ondersteund op Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="727e6-218">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="727e6-219">Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten Pi 2 en 3 Pi als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="727e6-219">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="727e6-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) downloaden naar uw Pi.</span><span class="sxs-lookup"><span data-stu-id="727e6-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="727e6-221">Installatie</span><span class="sxs-lookup"><span data-stu-id="727e6-221">Installation</span></span>

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

<span data-ttu-id="727e6-222">U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven van pad naar de binaire 'pwsh' maken</span><span class="sxs-lookup"><span data-stu-id="727e6-222">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="727e6-223">Verwijdering - Raspbian</span><span class="sxs-lookup"><span data-stu-id="727e6-223">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="727e6-224">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="727e6-224">Binary Archives</span></span>

<span data-ttu-id="727e6-225">PowerShell binair `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="727e6-225">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="727e6-226">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="727e6-226">Dependencies</span></span>

<span data-ttu-id="727e6-227">PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="727e6-227">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="727e6-228">Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en daarom PowerShell hetzelfde effect heeft.</span><span class="sxs-lookup"><span data-stu-id="727e6-228">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="727e6-229">Het volgende diagram toont de afhankelijkheden voor .NET Core 2.0 die officieel ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="727e6-229">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="727e6-230">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="727e6-230">OS</span></span>                 | <span data-ttu-id="727e6-231">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="727e6-231">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="727e6-232">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="727e6-232">Ubuntu 14.04</span></span>       | <span data-ttu-id="727e6-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="727e6-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="727e6-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="727e6-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="727e6-235">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="727e6-235">Ubuntu 16.04</span></span>       | <span data-ttu-id="727e6-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="727e6-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="727e6-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="727e6-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="727e6-238">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="727e6-238">Ubuntu 17.04</span></span>       | <span data-ttu-id="727e6-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="727e6-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="727e6-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="727e6-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="727e6-241">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="727e6-241">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="727e6-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="727e6-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="727e6-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="727e6-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="727e6-244">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="727e6-244">Debian 9 (Stretch)</span></span> | <span data-ttu-id="727e6-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="727e6-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="727e6-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="727e6-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="727e6-247">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="727e6-247">CentOS 7</span></span> <br> <span data-ttu-id="727e6-248">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="727e6-248">Oracle Linux 7</span></span> <br> <span data-ttu-id="727e6-249">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="727e6-249">RHEL 7</span></span> <br> <span data-ttu-id="727e6-250">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="727e6-250">OpenSUSE 42.2</span></span> | <span data-ttu-id="727e6-251">libunwind, libcurl, openssl-bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="727e6-251">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="727e6-252">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="727e6-252">Fedora 27</span></span> <br> <span data-ttu-id="727e6-253">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="727e6-253">Fedora 28</span></span> | <span data-ttu-id="727e6-254">libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="727e6-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="727e6-255">U moet de vereiste afhankelijkheden voor het doel OS installeren in afzonderlijke stappen voor het implementeren van de binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="727e6-255">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="727e6-256">Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden als eerste geïnstalleerd en pakt vervolgens de Linux `tar.gz` archief.</span><span class="sxs-lookup"><span data-stu-id="727e6-256">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="727e6-257">Installatie - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="727e6-257">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="727e6-258">Linux</span><span class="sxs-lookup"><span data-stu-id="727e6-258">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="727e6-259">Verwijderen binaire archieven</span><span class="sxs-lookup"><span data-stu-id="727e6-259">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="727e6-260">Paden</span><span class="sxs-lookup"><span data-stu-id="727e6-260">Paths</span></span>

* <span data-ttu-id="727e6-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="727e6-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="727e6-262">Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="727e6-262">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="727e6-263">Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="727e6-263">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="727e6-264">Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="727e6-264">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="727e6-265">Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="727e6-265">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="727e6-266">Standaardmodules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="727e6-266">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="727e6-267">Geschiedenis van PSReadline wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="727e6-267">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="727e6-268">De profielen respecteren van PowerShell per host-configuratie, zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="727e6-268">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="727e6-269">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="727e6-269">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versies]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
