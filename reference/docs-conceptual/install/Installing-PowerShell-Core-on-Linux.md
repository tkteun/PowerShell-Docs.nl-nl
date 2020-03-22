---
title: Power Shell installeren in Linux
description: Informatie over het installeren van Power shell op diverse Linux-distributies
ms.date: 03/09/2020
ms.openlocfilehash: 13b8583ed45f1201e61225b377112a59d2b26cb2
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082799"
---
# <a name="installing-powershell-on-linux"></a>Power Shell installeren in Linux

Ondersteunt [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE schrikkel 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora]en [Arch Linux][arch].

Voor Linux-distributies die niet officieel worden ondersteund, kunt u proberen Power shell te installeren met behulp van het [Power shell-snap package][snap]. U kunt ook proberen om Power shell-binaire bestanden rechtstreeks te implementeren met behulp van het Linux [`tar.gz` Archive][tar], maar u moet de vereiste afhankelijkheden instellen op basis van het besturings systeem in afzonderlijke stappen.

Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] . Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal. Voer `pwsh-preview` uit als u een [Preview-versie](#installing-preview-releases)hebt geïnstalleerd.

> [!NOTE]
> Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.
>
> De map `/usr/local/microsoft/powershell/6` wordt vervangen door `/usr/local/microsoft/powershell/7`.
>
> Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.

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


## <a name="installing-preview-releases"></a>Preview-versies installeren

Wanneer u een Power shell preview-versie voor Linux installeert via een pakket opslagplaats, wordt de naam van het pakket gewijzigd van `powershell` in `powershell-preview`.

Installeren via direct downloaden verandert niet, behalve de bestands naam.

De volgende tabel bevat de opdrachten om de stabiele en preview-pakketten te installeren met behulp van de verschillende pakket beheerders:

| Distributie (s) |            Stabiele opdracht            |               Opdracht preview                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| Ubuntu, Debian  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| CentOS, RedHat  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| Fedora          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installatie via pakket opslagplaats-Ubuntu 16,04

Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.

De voorkeurs methode is als volgt:

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

Als super gebruiker registreert u de micro soft-opslag plaats eenmaal. Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installatie via direct downloaden-Ubuntu 16,04

Down load het Debian-pakket `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.

Voer vervolgens de volgende opdrachten uit in de terminal:

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden. Met de volgende opdracht, `apt-get install -f` deze problemen op te lossen, wordt de configuratie van het Power shell-pakket voltooid.

### <a name="uninstallation---ubuntu-1604"></a>Installatie ongedaan maken-Ubuntu 16,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Installatie via pakket opslagplaats-Ubuntu 18,04

Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.

De voorkeurs methode is als volgt:

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

Als super gebruiker registreert u de micro soft-opslag plaats eenmaal. Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installatie via direct downloaden-Ubuntu 18,04

Down load het Debian-pakket `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` van de pagina [releases][] op de Ubuntu-computer.

Voer vervolgens de volgende opdrachten uit in de terminal:

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> De `dpkg -i` opdracht mislukt met unmet-afhankelijkheden. Met de volgende opdracht, `apt-get install -f` deze problemen op te lossen, wordt de configuratie van het Power shell-pakket voltooid.

### <a name="uninstallation---ubuntu-1804"></a>Installatie ongedaan maken-Ubuntu 18,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18,10

De installatie wordt ondersteund via `snapd`. Zie [snap package][snap]voor instructies.

> [!NOTE]
> Ubuntu 18,10 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).

## <a name="ubuntu-1904"></a>Ubuntu 19,04

De installatie wordt ondersteund via `snapd`. Zie [snap package][snap]voor instructies.

> [!NOTE]
> Ubuntu 19,04 is een [voorlopige versie](https://www.ubuntu.com/about/release-cycle) die door de [community wordt ondersteund](../powershell-support-lifecycle.md).

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installatie via pakket opslagplaats-Debian 8

Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.

De voorkeurs methode is als volgt:

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

Als super gebruiker registreert u de micro soft-opslag plaats eenmaal. Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installatie via pakket opslagplaats-Debian 9

Power shell voor Linux wordt gepubliceerd op pakket opslagplaatsen voor eenvoudige installatie en updates.

De voorkeurs methode is als volgt:

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

Als super gebruiker registreert u de micro soft-opslag plaats eenmaal. Na de registratie kunt u Power shell bijwerken met `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---debian-9"></a>Installatie via direct downloaden-Debian 9

Down load het Debian-pakket `powershell_7.0.0-1.debian.9_amd64.deb` van de pagina [releases][] op de Debian-computer.

Voer vervolgens de volgende opdrachten uit in de terminal:

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Installatie ongedaan maken-Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a>Debian 10

> [!NOTE]
> Debian 10 wordt alleen ondersteund in Power shell 7,0 en nieuwer.

### <a name="installation-via-direct-download---debian-10"></a>Installatie via direct downloaden-Debian 10

Down load het tar. gz-pakket `powershell_7.0.0-linux-x64.tar.gz` van de pagina [releases][] op de computer Debian.

Voer vervolgens de volgende opdrachten uit in de terminal:

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

## <a name="alpine-39-and-310"></a>Alpine 3,9 en 3,10

> [!NOTE]
> Alpine 3,9 en 3,10 worden alleen ondersteund in Power shell 7,0 en nieuwer.

### <a name="installation-via-direct-download---alpine-39-and-310"></a>Installatie via direct downloaden-Alpine 3,9 en 3,10

Down load het tar. gz-pakket `powershell-7.0.0-linux-alpine-x64.tar.gz` van de pagina [releases][] op de Alpine machine.

Voer vervolgens de volgende opdrachten uit in de terminal:

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

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Dit pakket werkt op Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installatie via pakket opslagplaats (voor keur)-CentOS 7

Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Als super gebruiker registreert u de micro soft-opslag plaats eenmaal. Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.

### <a name="installation-via-direct-download---centos-7"></a>Installatie via direct downloaden-CentOS 7

Gebruik [CentOS 7][]om het rpm-pakket te downloaden `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de CentOS-computer.

Voer vervolgens de volgende opdrachten uit in de terminal:

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Installatie ongedaan maken-CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installatie via pakket opslagplaats (voor keur)-Red Hat Enterprise Linux (RHEL) 7

Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Als super gebruiker registreert u de micro soft-opslag plaats eenmaal. Na de registratie kunt u Power shell bijwerken met `sudo yum update powershell`.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installatie via direct downloaden-Red Hat Enterprise Linux (RHEL) 7

Down load het RPM-pakket `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de Red Hat Enterprise Linux machine.

Voer vervolgens de volgende opdrachten uit in de terminal:

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Ongedaan maken-Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>Installatie-openSUSE 42,3

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

### <a name="installation---opensuse-leap-15"></a>Installatie-openSUSE Schrikkel 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Installatie ongedaan maken-openSUSE 42,3, openSUSE Schrikkel 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 wordt alleen ondersteund in Power shell 6,1 en nieuwer.

> [!NOTE]
> Fedora 29 en 30 worden alleen ondersteund in Power shell 7,0 en nieuwer.

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a>Installatie via pakket opslagplaats (voor keur): Fedora 28, 29 en 30

Power shell voor Linux wordt gepubliceerd op officiële micro soft-opslag plaatsen voor eenvoudige installatie en updates.

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a>Installatie via direct downloaden-Fedora 28, 29 en 30

Down load het RPM-pakket `powershell-7.0.0-1.rhel.7.x86_64.rpm` van de pagina [releases][] op de computer Fedora.

Voer vervolgens de volgende opdrachten uit in de terminal:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

U kunt de RPM installeren zonder de tussenliggende stap van het downloaden:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a>Installatie ongedaan maken-Fedora 28, 29 en 30

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Arch-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.

Power shell is beschikbaar via de [Arch Linux][] -gebruikers OPSLAGPLAATS (Aur).

* Het kan worden gecompileerd met de [nieuwste gelabelde release][arch-release]
* Het kan worden gecompileerd vanuit de [laatste door voering naar de hoofd server][arch-git]
* Het kan worden geïnstalleerd met behulp van de [meest recente versie van het binaire bestand][arch-bin]

Pakketten in de AUR worden beheerd door de Gemeenschap; Er is geen officiële ondersteuning.

Voor meer informatie over het installeren van pakketten van de AUR raadpleegt u de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snap-pakket

### <a name="getting-snapd"></a>Bezig met uitlijnen

`snapd` is vereist voor het uitvoeren van snaps. Gebruik [deze instructies](https://docs.snapcraft.io/core/install) om er zeker van te zijn dat `snapd` is geïnstalleerd.

### <a name="installation-via-snap"></a>Installatie via snap

Power shell voor Linux wordt gepubliceerd in de [snap Store](https://snapcraft.io/store) voor eenvoudige installatie en updates.

De voorkeurs methode is als volgt:

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Als u een preview-versie wilt installeren, gebruikt u de volgende methode:

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Na de installatie wordt de module automatisch bijgewerkt. U kunt een upgrade activeren met behulp van `sudo snap refresh powershell` of `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Installatie ongedaan maken

```sh
sudo snap remove powershell
```

of

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

> [!NOTE]
> Kali-ondersteuning wordt niet officieel ondersteund door micro soft en wordt beheerd door de community.

### <a name="installation---kali"></a>Installatie-Kali

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Installatie ongedaan maken-Kali

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian-ondersteuning is experimenteel.

Power shell wordt momenteel alleen ondersteund voor Raspbian stretch.

CoreCLR en Power shell werken alleen op pi 2-en Pi 3-apparaten als andere apparaten, zoals [pi nul](https://github.com/dotnet/coreclr/issues/10605), een niet-ondersteunde processor.

Down load [Raspbian stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) om de app te downloaden naar uw pi.

### <a name="installation---raspbian"></a>Installatie-Raspbian

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

U kunt desgewenst een symbolische koppeling maken om Power shell te starten zonder het pad naar de `pwsh` binaire waarde op te geven.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Installatie ongedaan maken-Raspbian

```sh
rm -rf ~/powershell
```

## <a name="install-as-a-net-global-tool"></a>Installeren als een Global .NET-hulp programma

Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Het installatie programma voor het DotNet-hulp programma voegt `~/.dotnet/tools` toe aan de omgevings variabele `PATH`. De momenteel actieve shell beschikt echter niet over de bijgewerkte `PATH`. U moet Power shell kunnen starten vanuit een nieuwe shell door `pwsh`te typen.

## <a name="binary-archives"></a>Binaire archieven

Er zijn binaire Power shell-`tar.gz` archieven beschikbaar voor Linux-platforms om geavanceerde implementatie scenario's mogelijk te maken.

### <a name="dependencies"></a>Afhankelijkheden

Power shell bouwt draag bare binaire bestanden voor alle Linux-distributies. .NET core runtime vereist echter andere afhankelijkheden voor verschillende distributies en Power Shell heeft ook.

In het volgende diagram ziet u de .NET Core 2,0-afhankelijkheden die officieel worden ondersteund op verschillende Linux-distributies.

| OS                 | Afhankelijkheden |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55 |
| Ubuntu 17,10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52 |
| Debian 9 (stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | afwikkeling, libkrul, openssl-Bibliotheken, libicu |
| openSUSE 42,3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Schrikkel 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | afwikkeling, libkrul, openssl-Bibliotheken, libicu, compat-openssl10 |

Als u binaire Power Shell-bestanden wilt implementeren op Linux-distributies die niet officieel worden ondersteund, moet u in afzonderlijke stappen de vereiste afhankelijkheden voor het doel besturingssysteem installeren. Zo installeert onze [Amazon Linux dockerfile][amazon-dockerfile] eerst afhankelijkheden en extraheert vervolgens het Linux `tar.gz`-archief.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Installatie-binaire archieven

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Binaire archieven verwijderen

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Paden

- `$PSHOME` is `/opt/microsoft/powershell/7/`
- Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`
- Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`
- Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`
- Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`
- Standaard modules worden gelezen uit `$PSHOME/Modules`
- De PSReadline-geschiedenis wordt geregistreerd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren de configuratie per host van Power shell, zodat de standaardhost-specifieke profielen op `Microsoft.PowerShell_profile.ps1` op dezelfde locatie bestaan.

Power shell respecteert de [XDG base-specificatie][xdg-bds] op Linux.

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
