# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="59275-101">PowerShell Core in Linux installeren</span><span class="sxs-lookup"><span data-stu-id="59275-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="59275-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="59275-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="59275-103">Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="59275-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="59275-104">U kunt ook proberen implementeren PowerShell binaire bestanden rechtstreeks met het Linux [ `tar.gz` archief][tar], maar u moet de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen instellen.</span><span class="sxs-lookup"><span data-stu-id="59275-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="59275-105">Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.</span><span class="sxs-lookup"><span data-stu-id="59275-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="59275-106">Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.</span><span class="sxs-lookup"><span data-stu-id="59275-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="59275-107">Preview-versies installeren</span><span class="sxs-lookup"><span data-stu-id="59275-107">Installing Preview Releases</span></span>

<span data-ttu-id="59275-108">Wanneer u een evaluatieversie van PowerShell Core installeert voor Linux via een opslagplaats pakket, de naam van het pakket verandert van `powershell` naar `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="59275-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="59275-109">Installeren via de directe download verandert niet, dan de bestandsnaam.</span><span class="sxs-lookup"><span data-stu-id="59275-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="59275-110">Hier volgt een tabel met de opdrachten voor het installeren van de stabiel en preview pakketten met behulp van de verschillende pakket managers:</span><span class="sxs-lookup"><span data-stu-id="59275-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="59275-111">Distrobution(s)</span><span class="sxs-lookup"><span data-stu-id="59275-111">Distrobution(s)</span></span>|<span data-ttu-id="59275-112">Stabiele opdracht</span><span class="sxs-lookup"><span data-stu-id="59275-112">Stable Command</span></span> | <span data-ttu-id="59275-113">Preview-opdracht</span><span class="sxs-lookup"><span data-stu-id="59275-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="59275-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="59275-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="59275-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="59275-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="59275-116">openSUSE</span><span class="sxs-lookup"><span data-stu-id="59275-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="59275-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="59275-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="59275-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="59275-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="59275-119">Installatie via pakket opslagplaats - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="59275-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="59275-120">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="59275-121">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="59275-121">This is the preferred method.</span></span>

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

<span data-ttu-id="59275-122">Als beheerder, registreert u de Microsoft-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="59275-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="59275-123">Daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bijwerken van de installatie.</span><span class="sxs-lookup"><span data-stu-id="59275-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="59275-124">Installatie via directe Download - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="59275-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="59275-125">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="59275-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="59275-126">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="59275-127">De `dpkg -i` opdracht is mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="59275-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="59275-128">De volgende opdracht `apt-get install -f` deze problemen worden opgelost en klaar is met het configureren van het PowerShell-pakket.</span><span class="sxs-lookup"><span data-stu-id="59275-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="59275-129">Verwijdering - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="59275-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="59275-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="59275-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="59275-131">Installatie via pakket opslagplaats - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="59275-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="59275-132">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="59275-133">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="59275-133">This is the preferred method.</span></span>

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

<span data-ttu-id="59275-134">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="59275-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="59275-135">Installatie via directe Download - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="59275-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="59275-136">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="59275-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="59275-137">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="59275-138">De `dpkg -i` opdracht is mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="59275-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="59275-139">De volgende opdracht `apt-get install -f` deze problemen worden opgelost en klaar is met het configureren van het PowerShell-pakket.</span><span class="sxs-lookup"><span data-stu-id="59275-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="59275-140">Verwijdering - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="59275-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="59275-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="59275-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="59275-142">Er is ondersteuning voor Ubuntu 17.04 toegevoegd na `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="59275-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="59275-143">Installatie via pakket opslagplaats - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="59275-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="59275-144">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="59275-145">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="59275-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="59275-146">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="59275-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="59275-147">Installatie via directe Download - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="59275-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="59275-148">Download het Debian-pakket `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="59275-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="59275-149">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="59275-150">De `dpkg -i` opdracht is mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="59275-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="59275-151">De volgende opdracht `apt-get install -f` deze problemen worden opgelost en klaar is met het configureren van het PowerShell-pakket.</span><span class="sxs-lookup"><span data-stu-id="59275-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="59275-152">Verwijdering - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="59275-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="59275-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="59275-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="59275-154">Er is ondersteuning voor Ubuntu 18.04 toegevoegd na `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="59275-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="59275-155">Installatie via pakket opslagplaats - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="59275-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="59275-156">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="59275-157">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="59275-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="59275-158">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="59275-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="59275-159">Installatie via directe Download - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="59275-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="59275-160">Download het Debian-pakket `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.</span><span class="sxs-lookup"><span data-stu-id="59275-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="59275-161">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="59275-162">De `dpkg -i` opdracht is mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="59275-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="59275-163">De volgende opdracht `apt-get install -f` deze problemen worden opgelost en klaar is met het configureren van het PowerShell-pakket.</span><span class="sxs-lookup"><span data-stu-id="59275-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="59275-164">Verwijdering - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="59275-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="59275-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="59275-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="59275-166">Installatie via pakket opslagplaats - Debian 8</span><span class="sxs-lookup"><span data-stu-id="59275-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="59275-167">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="59275-168">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="59275-168">This is the preferred method.</span></span>

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

<span data-ttu-id="59275-169">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="59275-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="59275-170">Installatie via directe Download - Debian 8</span><span class="sxs-lookup"><span data-stu-id="59275-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="59275-171">Download het Debian-pakket `powershell_6.0.2-1.debian.8_amd64.deb` van de [releases][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="59275-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="59275-172">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="59275-173">De `dpkg -i` opdracht is mislukt met afhankelijkheden waaraan niet is voldaan.</span><span class="sxs-lookup"><span data-stu-id="59275-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="59275-174">De volgende opdracht `apt-get install -f` deze problemen worden opgelost en klaar is met het configureren van het PowerShell-pakket.</span><span class="sxs-lookup"><span data-stu-id="59275-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="59275-175">Verwijdering - Debian 8</span><span class="sxs-lookup"><span data-stu-id="59275-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="59275-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="59275-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="59275-177">Installatie via pakket opslagplaats - Debian 9</span><span class="sxs-lookup"><span data-stu-id="59275-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="59275-178">PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="59275-179">Dit is de voorkeursmethode.</span><span class="sxs-lookup"><span data-stu-id="59275-179">This is the preferred method.</span></span>

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

<span data-ttu-id="59275-180">Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.</span><span class="sxs-lookup"><span data-stu-id="59275-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="59275-181">Installatie via directe Download - Debian 9</span><span class="sxs-lookup"><span data-stu-id="59275-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="59275-182">Download het Debian-pakket `powershell_6.0.2-1.debian.9_amd64.deb` van de [releases][] pagina naar de Debian machine.</span><span class="sxs-lookup"><span data-stu-id="59275-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="59275-183">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="59275-184">Verwijdering - Debian 9</span><span class="sxs-lookup"><span data-stu-id="59275-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="59275-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="59275-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="59275-186">Dit pakket werkt ook op Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="59275-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="59275-187">Installatie via pakket opslagplaats (voorkeur) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="59275-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="59275-188">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="59275-189">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="59275-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="59275-190">Installatie via directe Download - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="59275-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="59275-191">Met behulp van [CentOS 7][], downloaden de RPM-pakket `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine CentOS.</span><span class="sxs-lookup"><span data-stu-id="59275-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="59275-192">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="59275-193">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="59275-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="59275-194">Verwijdering - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="59275-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="59275-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="59275-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="59275-197">Installatie via pakket opslagplaats (voorkeur) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="59275-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="59275-198">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="59275-199">Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.</span><span class="sxs-lookup"><span data-stu-id="59275-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="59275-200">Installatie via directe Download - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="59275-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="59275-201">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina naar de Red Hat Enterprise Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="59275-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="59275-202">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="59275-203">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="59275-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="59275-204">Verwijdering - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="59275-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="59275-205">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="59275-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="59275-206">Bij de installatie van PowerShell Core `zypper` mogelijk de volgende fout te melden:</span><span class="sxs-lookup"><span data-stu-id="59275-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="59275-207">In dit geval controleren of een compatibel `libcurl` bibliotheek aanwezig is, door te controleren dat de volgende geeft opdracht de `libcurl4` pakket geïnstalleerd:</span><span class="sxs-lookup"><span data-stu-id="59275-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="59275-208">Kies vervolgens de `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` oplossing wanneer de PowerShell-pakket installeert.</span><span class="sxs-lookup"><span data-stu-id="59275-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="59275-209">Installatie via pakket opslagplaats (voorkeur) - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="59275-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="59275-210">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="59275-211">Installatie via directe Download - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="59275-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="59275-212">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="59275-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="59275-213">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="59275-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="59275-214">Verwijdering - OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="59275-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="59275-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="59275-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="59275-216">Fedora 28 wordt alleen ondersteund in PowerShell Core 6.1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="59275-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="59275-217">Installatie via pakket opslagplaats (voorkeur) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="59275-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="59275-218">PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).</span><span class="sxs-lookup"><span data-stu-id="59275-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="59275-219">Installatie via directe Download - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="59275-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="59275-220">Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora.</span><span class="sxs-lookup"><span data-stu-id="59275-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="59275-221">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="59275-222">U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:</span><span class="sxs-lookup"><span data-stu-id="59275-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="59275-223">Verwijdering - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="59275-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="59275-224">Boog Linux</span><span class="sxs-lookup"><span data-stu-id="59275-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="59275-225">Boog ondersteuning is experimentele.</span><span class="sxs-lookup"><span data-stu-id="59275-225">Arch support is experimental.</span></span>

<span data-ttu-id="59275-226">PowerShell is beschikbaar via de [Arch Linux][] gebruiker opslagplaats (AUR).</span><span class="sxs-lookup"><span data-stu-id="59275-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="59275-227">Het kan worden gecompileerd met het [meest recente release met tags][arch-release]</span><span class="sxs-lookup"><span data-stu-id="59275-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="59275-228">Het kan worden gecompileerd uit de [nieuwste doorvoeren naar het hoofdniveau][arch-git]</span><span class="sxs-lookup"><span data-stu-id="59275-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="59275-229">Kan worden geïnstalleerd met de [binair de meest recente release][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="59275-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="59275-230">Pakketten in de AUR community bewaard zijn: Er is geen officiële ondersteuning.</span><span class="sxs-lookup"><span data-stu-id="59275-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="59275-231">Zie voor meer informatie over het installeren van pakketten uit de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="59275-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="59275-233">Linux-AppImage</span><span class="sxs-lookup"><span data-stu-id="59275-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="59275-234">Ondersteuning voor AppImage is experimentele</span><span class="sxs-lookup"><span data-stu-id="59275-234">AppImage support is experimental</span></span>

<span data-ttu-id="59275-235">Gebruik van een recente Linux-distributie, downloaden de AppImage `powershell-6.0.1-x86_64.AppImage` van de [releases][] pagina naar de Linux-machine.</span><span class="sxs-lookup"><span data-stu-id="59275-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="59275-236">Voer vervolgens het volgende in de terminal:</span><span class="sxs-lookup"><span data-stu-id="59275-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="59275-237">De [AppImage][] kunt u PowerShell uitvoeren zonder het te installeren.</span><span class="sxs-lookup"><span data-stu-id="59275-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="59275-238">Dit is een draagbare toepassing die u verzamelt van PowerShell en de afhankelijkheden ervan (inclusief .NET-Core system afhankelijkheden) in één samenhangender pakket.</span><span class="sxs-lookup"><span data-stu-id="59275-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="59275-239">Dit pakket is een enkele binaire waarde die geschikt is onafhankelijk van de Linux-distributie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="59275-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="59275-241">Kali</span><span class="sxs-lookup"><span data-stu-id="59275-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="59275-242">Ondersteuning voor Kali is experimentele.</span><span class="sxs-lookup"><span data-stu-id="59275-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="59275-243">Installatie</span><span class="sxs-lookup"><span data-stu-id="59275-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="59275-244">PowerShell uitvoeren in de meest recente Kali (Kali GNU/Linux Rolling) zonder het te installeren</span><span class="sxs-lookup"><span data-stu-id="59275-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="59275-245">Verwijdering - Kali</span><span class="sxs-lookup"><span data-stu-id="59275-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="59275-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="59275-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="59275-247">Ondersteuning voor Raspbian is experimentele.</span><span class="sxs-lookup"><span data-stu-id="59275-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="59275-248">PowerShell is momenteel alleen ondersteund op Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="59275-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="59275-249">Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten Pi 2 en 3 Pi als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.</span><span class="sxs-lookup"><span data-stu-id="59275-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="59275-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) downloaden naar uw Pi.</span><span class="sxs-lookup"><span data-stu-id="59275-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="59275-251">Installatie</span><span class="sxs-lookup"><span data-stu-id="59275-251">Installation</span></span>

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

<span data-ttu-id="59275-252">U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven van pad naar de binaire 'pwsh' maken</span><span class="sxs-lookup"><span data-stu-id="59275-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="59275-253">Verwijdering - Raspbian</span><span class="sxs-lookup"><span data-stu-id="59275-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="59275-254">Binaire archieven</span><span class="sxs-lookup"><span data-stu-id="59275-254">Binary Archives</span></span>

<span data-ttu-id="59275-255">PowerShell binair `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.</span><span class="sxs-lookup"><span data-stu-id="59275-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="59275-256">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="59275-256">Dependencies</span></span>

<span data-ttu-id="59275-257">PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="59275-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="59275-258">Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en daarom PowerShell hetzelfde effect heeft.</span><span class="sxs-lookup"><span data-stu-id="59275-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="59275-259">Het volgende diagram toont de afhankelijkheden voor .NET Core 2.0 die officieel ondersteund op verschillende Linux-distributies.</span><span class="sxs-lookup"><span data-stu-id="59275-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="59275-260">Besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="59275-260">OS</span></span>                 | <span data-ttu-id="59275-261">Afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="59275-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="59275-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="59275-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="59275-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="59275-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="59275-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="59275-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="59275-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="59275-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="59275-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="59275-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="59275-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="59275-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="59275-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="59275-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="59275-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="59275-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="59275-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="59275-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="59275-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="59275-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="59275-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="59275-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="59275-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="59275-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="59275-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="59275-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="59275-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="59275-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="59275-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="59275-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="59275-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="59275-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="59275-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="59275-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="59275-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="59275-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="59275-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="59275-280">CentOS 7</span></span> <br> <span data-ttu-id="59275-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="59275-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="59275-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="59275-282">RHEL 7</span></span> <br> <span data-ttu-id="59275-283">OpenSUSE 42,2</span><span class="sxs-lookup"><span data-stu-id="59275-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="59275-284">libunwind, libcurl, openssl-bibliotheken, libicu</span><span class="sxs-lookup"><span data-stu-id="59275-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="59275-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="59275-285">Fedora 27</span></span> <br> <span data-ttu-id="59275-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="59275-286">Fedora 28</span></span> | <span data-ttu-id="59275-287">libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10</span><span class="sxs-lookup"><span data-stu-id="59275-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="59275-288">U moet de vereiste afhankelijkheden voor het doel OS installeren in afzonderlijke stappen voor het implementeren van de binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="59275-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="59275-289">Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden als eerste geïnstalleerd en pakt vervolgens de Linux `tar.gz` archief.</span><span class="sxs-lookup"><span data-stu-id="59275-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="59275-290">Installatie - binaire archieven</span><span class="sxs-lookup"><span data-stu-id="59275-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="59275-291">Linux</span><span class="sxs-lookup"><span data-stu-id="59275-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="59275-292">Verwijderen binaire archieven</span><span class="sxs-lookup"><span data-stu-id="59275-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="59275-293">Paden</span><span class="sxs-lookup"><span data-stu-id="59275-293">Paths</span></span>

* <span data-ttu-id="59275-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="59275-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="59275-295">Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="59275-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="59275-296">Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="59275-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="59275-297">Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="59275-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="59275-298">Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="59275-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="59275-299">Standaardmodules worden gelezen uit `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="59275-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="59275-300">Geschiedenis van PSReadline wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="59275-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="59275-301">De profielen respecteren van PowerShell per host-configuratie, zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.</span><span class="sxs-lookup"><span data-stu-id="59275-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="59275-302">PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.</span><span class="sxs-lookup"><span data-stu-id="59275-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
