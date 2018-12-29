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
# <a name="installing-powershell-core-on-linux"></a>PowerShell Core in Linux installeren

Ondersteunt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9] [ deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [ Fedora 28][fedora], en [boog Linux][arch].

Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell module pakket][snap].
U kunt ook PowerShell binaire bestanden rechtstreeks met behulp van de Linux implementeren [ `tar.gz` archief][tar], maar dan moet u voor het instellen van de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen.

Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.
Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.

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

## <a name="installing-preview-releases"></a>Preview-versies installeren

Bij het installeren van een PowerShell Core Preview-versie voor Linux via een Pakketopslagplaats, naam van het pakket verandert van `powershell` naar `powershell-preview`.

Installeren via de directe download verandert niet, dan de naam van het bestand.

Hier volgt een tabel met de opdrachten om de met de verschillende pakketmanagers stabiel en preview-pakketten te installeren:

|Verdeling van|Stabiele opdracht | Preview-opdracht |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, Red Hat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installatie via Pakketopslagplaats - Ubuntu 14.04

PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Als beheerder, de Microsoft-opslagplaats te registreren.
Vanaf hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` om bij te werken van de installatie.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installatie via de directe Download - Ubuntu 14.04

Het Debian-pakket downloaden `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
uit de [releases][] pagina naar de Ubuntu-machine.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.
> De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.

### <a name="uninstallation---ubuntu-1404"></a>Verwijderen - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installatie via Pakketopslagplaats - Ubuntu 16.04

PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installatie via de directe Download - Ubuntu 16.04

Het Debian-pakket downloaden `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
uit de [releases][] pagina naar de Ubuntu-machine.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.
> De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.

### <a name="uninstallation---ubuntu-1604"></a>Verwijderen - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Er is ondersteuning voor Ubuntu 18.04 toegevoegd na `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Installatie via Pakketopslagplaats - Ubuntu 18.04

PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installatie via de directe Download - Ubuntu 18.04

Het Debian-pakket downloaden `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
uit de [releases][] pagina naar de Ubuntu-machine.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.
> De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.

### <a name="uninstallation---ubuntu-1804"></a>Verwijderen - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> Er is ondersteuning voor Ubuntu 18.10 toegevoegd na `6.1.0-preview.3`.
> Zoals 18.10 een dagelijkse build is, is het alleen community ondersteund.

Installeren op 18.10 wordt ondersteund `snapd`. Zie [module pakket] [ snap] voor volledige instructies;

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installatie via Pakketopslagplaats - Debian 8

PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---debian-8"></a>Installatie via de directe Download - Debian 8

Het Debian-pakket downloaden `powershell_6.1.0-1.debian.8_amd64.deb`
uit de [releases][] pagina naar de Debian-machine.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> De `dpkg -i` opdracht is mislukt met nog niet vervulde afhankelijkheden.
> De volgende opdracht, `apt-get install -f` deze problemen worden opgelost en vervolgens klaar is met het PowerShell-pakket configureren.

### <a name="uninstallation---debian-8"></a>Verwijderen - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installatie via Pakketopslagplaats - Debian 9

PowerShell Core voor Linux is gepubliceerd op pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---debian-9"></a>Installatie via de directe Download - Debian 9

Het Debian-pakket downloaden `powershell_6.1.0-1.debian.9_amd64.deb`
uit de [releases][] pagina naar de Debian-machine.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Verwijderen - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Dit pakket werkt ook op Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installatie via (aanbevolen) - Pakketopslagplaats CentOS 7

PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Installatie via de directe Download - CentOS 7

Met behulp van [CentOS 7][], het RPM-pakket downloaden `powershell-6.1.0-1.rhel.7.x86_64.rpm`
uit de [releases][] pagina op de computer CentOS.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Verwijderen - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installatie via (aanbevolen) - Pakketopslagplaats Red Hat Enterprise Linux (RHEL) 7

PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Na het registreren van de Microsoft-bibliotheek eenmaal als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` om bij te werken van PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installatie via de directe Download - Red Hat Enterprise Linux (RHEL) 7

Download het RPM-pakket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
uit de [releases][] pagina naar de Red Hat Enterprise Linux-machine.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Verwijderen - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>OpenSUSE

### <a name="installation---opensuse-423"></a>Installatie - openSUSE 42,3

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

### <a name="installation---opensuse-leap-15"></a>Installatie - openSUSE Leap 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Verwijderen - openSUSE 42,3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 wordt alleen ondersteund in PowerShell Core 6.1 en hoger.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Installatie via Pakketopslagplaats (aanbevolen) - 27 Fedora, Fedora 28

PowerShell Core voor Linux is gepubliceerd naar de officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Installatie via de directe Download - Fedora 27, Fedora 28

Download het RPM-pakket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
uit de [releases][] pagina op de computer Fedora.

Voer vervolgens het volgende uit in de terminal:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap van het downloaden van het te installeren:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Verwijderen - Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Linux boog

> [!NOTE]
> Er is een experimenteel boog ondersteuning.

PowerShell is beschikbaar via de [Linux boog][] gebruiker opslagplaats (AUR).

* Het kan worden gecompileerd met de [meest recente versie gemarkeerd][arch-release]
* Het kan worden gecompileerd uit de [laatste doorvoering naar hoofdniveau][arch-git]
* Kan worden geïnstalleerd met behulp van de [binaire de meest recente release][arch-bin]

Pakketten in de AUR zijn community onderhouden: Er is geen officiële ondersteuning.

Zie voor meer informatie over het installeren van pakketten van de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Linux boog]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snap-pakket

### <a name="getting-snapd"></a>Snapd ophalen

`snapd` is vereist voor het uitvoeren van snaps.
Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om ervoor te zorgen dat u hebt `snapd` geïnstalleerd.

### <a name="installation-via-snap"></a>Installatie via de module

PowerShell Core voor Linux is gepubliceerd naar de [module store](https://snapcraft.io/store) voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Als u installeren van de preview-versie wilt, gebruikt u de volgende methode.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Nadat de installatie van module, automatisch bijgewerkt, maar u kunt activeren een upgrade uitvoeren met behulp `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Verwijderen

```sh
sudo snap remove powershell
```

of

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Installatie - Kali

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

### <a name="uninstallation---kali"></a>Verwijderen - Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Ondersteuning voor Raspbian is experimenteel.

PowerShell is momenteel alleen ondersteund op Raspbian Stretch.

Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten van Pi 2 en Pi 3 als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.

Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) zodat deze naar uw Pi.

### <a name="installation---raspbian"></a>Installatie - Raspbian

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

U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven pad naar het binaire 'pwsh' maken

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Verwijderen - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Binaire archieven

PowerShell binaire `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.

### <a name="dependencies"></a>Afhankelijkheden

PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.
Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en kan daarom PowerShell hetzelfde effect heeft.

Het volgende diagram toont de .NET Core 2.0-afhankelijkheden die officieel ondersteund op verschillende Linux-distributies.

| Besturingssysteem                 | Afhankelijkheden |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-bibliotheken, libicu |
| OpenSUSE 42,3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10 |

Voor het implementeren van binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund, moet u de vereiste afhankelijkheden voor het doelbesturingssysteem installeren in afzonderlijke stappen.
Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden eerst geïnstalleerd en pakt u vervolgens de Linux `tar.gz` archief.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installatie - binaire archieven

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Verwijderen binaire archieven

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Paden

* `$PSHOME` is `/opt/microsoft/powershell/6.1.0/`
* Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`
* Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`
* Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`
* Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`
* Standaardmodules worden gelezen in `$PSHOME/Modules`
* PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren van PowerShell per host-configuratie, zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.

PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
