# <a name="installing-powershell-core-on-macos-and-linux"></a>PowerShell Core in macOS en Linux installeren

Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].

Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell AppImage][lai]. U kunt ook proberen implementeren PowerShell binaire bestanden rechtstreeks met het Linux [ `tar.gz` archief][tar], maar u moet de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen instellen.

Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina. Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.

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

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installatie via pakket opslagplaats - Ubuntu 14.04

PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates). Dit is de voorkeursmethode.

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

Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installatie via directe Download - Ubuntu 14.04

Download het Debian-pakket `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.

### <a name="uninstallation---ubuntu-1404"></a>Verwijdering - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installatie via pakket opslagplaats - Ubuntu 16.04

PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installatie via directe Download - Ubuntu 16.04

Download het Debian-pakket `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.

### <a name="uninstallation---ubuntu-1604"></a>Verwijdering - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu 17.04

### <a name="installation-via-package-repository---ubuntu-1704"></a>Installatie via pakket opslagplaats - Ubuntu 17.04

PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Installatie via directe Download - Ubuntu 17.04

Download het Debian-pakket `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.

### <a name="uninstallation---ubuntu-1704"></a>Verwijdering - Ubuntu 17.04

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installatie via pakket opslagplaats - Debian 8

PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
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

Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---debian-8"></a>Installatie via directe Download - Debian 8

Download het Debian-pakket `powershell_6.0.0-1.debian.8_amd64.deb` van de [releases][] pagina naar de Debian machine:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.

### <a name="uninstallation---debian-8"></a>Verwijdering - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installatie via pakket opslagplaats - Debian 9

PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
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

Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---debian-9"></a>Installatie via directe Download - Debian 9

Download het Debian-pakket `powershell_6.0.0-1.debian.9_amd64.deb` van de [releases][] pagina naar de Debian machine:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> Houd er rekening mee dat `dpkg -i` mislukt met hangt afhankelijkheden; de volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.

### <a name="uninstallation---debian-9"></a>Verwijdering - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> Dit pakket werkt ook op Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installatie via pakket opslagplaats (voorkeur) - CentOS 7

PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.

### <a name="installation-via-direct-download---centos-7"></a>Installatie via directe Download - CentOS 7

Met behulp van [CentOS 7][], downloaden de RPM-pakket `powershell-6.0.0-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine CentOS:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Voer vervolgens het volgende in de terminal:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Verwijdering - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installatie via pakket opslagplaats (voorkeur) - Red Hat Enterprise Linux (RHEL) 7

PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Na de Microsoft-bibliotheek eens registreert als supergebruiker, hoeft u alleen te gebruiken `sudo yum update powershell` PowerShell bijwerken.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installatie via directe Download - Red Hat Enterprise Linux (RHEL) 7

Download het pakket RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` van de [releases][] pagina naar de Red Hat Enterprise Linux-machine:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

Voer vervolgens het volgende in de terminal:

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Verwijdering - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42,2

> **Opmerking:** bij de installatie van PowerShell Core `zypper` mogelijk de volgende fout te melden:
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> In dit geval controleren of een compatibel `libcurl` bibliotheek aanwezig is, door te controleren dat de volgende geeft opdracht de `libcurl4` pakket geïnstalleerd:
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> Kies vervolgens de `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` oplossing bij het installeren van de `powershell` pakket.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Installatie via pakket opslagplaats (voorkeur) - OpenSUSE 42,2

PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Installatie via directe Download - OpenSUSE 42,2

Download het pakket RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine OpenSUSE:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Verwijdering - OpenSUSE 42,2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>Installatie via pakket opslagplaats (voorkeur) - Fedora 25

PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

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

### <a name="installation-via-direct-download---fedora-25"></a>Installatie via directe Download - Fedora 25

Download het pakket RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>Verwijdering - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>Installatie via pakket opslagplaats (voorkeur) - Fedora 26

PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

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

### <a name="installation-via-direct-download---fedora-26"></a>Installatie via directe Download - Fedora 26

Download het pakket RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora:

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>Verwijdering - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Boog Linux

PowerShell is beschikbaar via de [Arch Linux][] gebruiker opslagplaats (AUR).

* Het kan worden gecompileerd met het [meest recente release met tags][arch-release]
* Het kan worden gecompileerd uit de [nieuwste doorvoeren naar het hoofdniveau][arch-git]
* Kan worden geïnstalleerd met de [binair de meest recente release][arch-bin]

Pakketten in de AUR community bewaard zijn: Er is geen officiële ondersteuning.

Zie voor meer informatie over het installeren van pakketten uit de AUR de [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) of de community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux-AppImage

Gebruik van een recente Linux-distributie, downloaden de AppImage `powershell-6.0.0-x86_64.AppImage` van de [releases][] pagina naar de Linux-machine.

Voer vervolgens het volgende in de terminal:

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

De [AppImage][] kunt u PowerShell uitvoeren zonder het te installeren. Dit is een draagbare toepassing die u verzamelt van PowerShell en de afhankelijkheden ervan (inclusief .NET-Core system afhankelijkheden) in één samenhangender pakket. Dit pakket werkt onafhankelijk van de Linux-distributie van de gebruiker en een enkele binaire waarde is.

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>Installatie via Homebrew (voorkeur) - Mac OS 10,12

[Homebrew] [ brew] is de ontbrekende package manager voor Mac OS. Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew geïnstalleerd [hun instructies][brew].

Zodra u Homebrew hebt geïnstalleerd, is het eenvoudig om PowerShell installeren. Installeer eerst [Homebrew Cask][cask], zodat u kunt meer pakketten installeren:

```sh
brew tap caskroom/cask
```

U kunt nu PowerShell installeren:

```sh
brew cask install powershell
```

Wanneer er nieuwe versies van PowerShell zijn uitgebracht, Homebrew van formules bijwerken en upgrade uitvoeren van PowerShell:

```sh
brew update
brew cask reinstall powershell
```

> Opmerking:-vanwege van [dit probleem in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), u hebt momenteel doen opnieuw moet installeren om bij te werken.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>Installatie via de directe Download - Mac OS 10,12

Pak het pakket met behulp van Mac OS 10,12 downloaden `powershell-6.0.0-osx.10.12-x64.pkg` van de [releases][] pagina op de Mac OS-machine.

Dubbelklik op het bestand en volg de aanwijzingen, noch installeren vanaf de terminal:

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>Verwijdering - Mac OS 10,12

Als u met Homebrew PowerShell hebt geïnstalleerd, is het verwijderen is eenvoudig:

```sh
brew cask uninstall powershell
```

Als u via de directe download PowerShell hebt geïnstalleerd, moet PowerShell handmatig worden verwijderd:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Verwijder de extra PowerShell-paden (zoals het pad van het gebruikersprofiel) raadpleegt u de [paden] [ paths] onder sectie in dit document en verwijdert u de gewenste de paden met `sudo rm`. (Opmerking: dit is niet nodig als u met Homebrew geïnstalleerd.)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>Installatie

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>PowerShell uitvoeren in de meest recente Kali (Kali GNU/Linux Rolling) zonder het te installeren

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Verwijdering - Kali

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a>Raspbian

PowerShell is momenteel alleen ondersteund op Raspbian Stretch.

### <a name="installation"></a>Installatie

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>Verwijdering - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Binaire archieven

PowerShell binair `tar.gz` archieven voor Mac OS- en Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.

### <a name="dependencies"></a>Afhankelijkheden

Voor Linux bouwt PowerShell draagbare binaire bestanden voor alle Linux-distributies.
Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en daarom PowerShell hetzelfde effect heeft.

Het volgende diagram toont de afhankelijkheden .NET Core 2.0 op verschillende Linux-distributies die officieel ondersteund.

| Besturingssysteem                 | Afhankelijkheden |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42,2 <br> Fedora 25 | libunwind, libcurl, openssl-bibliotheken, libicu |
| Fedora 26          | libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10 |

Als u wilt implementeren PowerShell binaire bestanden op Linux-distributies die officieel niet worden ondersteund, moet u voor het installeren van de vereiste afhankelijkheden voor het doel OS in afzonderlijke stappen. Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden als eerste geïnstalleerd en pakt vervolgens de Linux `tar.gz` archief.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installatie - binaire archieven

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>Verwijdering - binaire archieven

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>Paden

* `$PSHOME` is `/opt/microsoft/powershell/6.0.0/`
* Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`
* Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`
* Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`
* Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`
* Standaardmodules worden gelezen uit `$PSHOME/Modules`
* Geschiedenis van PSReadline wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren van PowerShell per host-configuratie, zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.

Op Linux- en Mac OS, de [XDG Base Directory specificatie] [ xdg-bds] is voldaan.

Omdat Mac OS is geen afwijking van BSD, in plaats van `/opt`, het voorvoegsel dat gebruikt is `/usr/local`. Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
