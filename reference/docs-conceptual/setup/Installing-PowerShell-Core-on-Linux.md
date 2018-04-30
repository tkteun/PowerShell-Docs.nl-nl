# <a name="installing-powershell-core-on-linux"></a>PowerShell Core installeren op Linux

Ondersteunt [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42,2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], en [boog Linux][arch].

Voor Linux-distributies die officieel niet worden ondersteund, kunt u proberen met behulp van de [PowerShell AppImage][lai].
U kunt ook proberen implementeren PowerShell binaire bestanden rechtstreeks met het Linux [ `tar.gz` archief][tar], maar u moet de vereiste afhankelijkheden op basis van het besturingssysteem in de afzonderlijke stappen instellen.

Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.
Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.

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

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installatie via pakket opslagplaats - Ubuntu 14.04

PowerShell-Core, voor Linux wordt gepubliceerd voor pakket-opslagplaatsen voor eenvoudige installatie (en -updates).
Dit is de voorkeursmethode.

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

Als beheerder, registreert u de Microsoft-bibliotheek.
Daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bijwerken van de installatie.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installatie via directe Download - Ubuntu 14.04

Download het Debian-pakket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installatie via directe Download - Ubuntu 16.04

Download het Debian-pakket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Na de registratie de Microsoft-bibliotheek eenmaal als supergebruiker daarna hoeft u alleen te gebruiken `sudo apt-get upgrade powershell` bij te werken.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Installatie via directe Download - Ubuntu 17.04

Download het Debian-pakket `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` van de [releases][] pagina naar de Ubuntu-machine.

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
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

Download het Debian-pakket `powershell_6.0.2-1.debian.8_amd64.deb` van de [releases][] pagina naar de Debian machine.

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Houd er rekening mee dat `dpkg -i` mislukt met afhankelijkheden waaraan niet is voldaan.
> De volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.

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

Download het Debian-pakket `powershell_6.0.2-1.debian.9_amd64.deb` van de [releases][] pagina naar de Debian machine.

Voer vervolgens het volgende in de terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Houd er rekening mee dat `dpkg -i` mislukt met afhankelijkheden waaraan niet is voldaan.
> De volgende opdracht `apt-get install -f` wordt deze omgezet en voltooit u vervolgens het PowerShell-pakket configureren.

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

Met behulp van [CentOS 7][], downloaden de RPM-pakket `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine CentOS.

Voer vervolgens het volgende in de terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina naar de Red Hat Enterprise Linux-machine.

Voer vervolgens het volgende in de terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Verwijdering - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42,2

> [!NOTE]
> Bij de installatie van PowerShell Core `zypper` mogelijk de volgende fout te melden:
>
> ```Output
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
> Kies vervolgens de `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` oplossing wanneer de PowerShell-pakket installeert.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Installatie via pakket opslagplaats (voorkeur) - OpenSUSE 42,2

PowerShell-kern voor Linux wordt gepubliceerd naar het officiële Microsoft-opslagplaatsen voor eenvoudige installatie (en -updates).

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

### <a name="installation-via-direct-download---opensuse-422"></a>Installatie via directe Download - OpenSUSE 42,2

Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora.

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

Voer vervolgens het volgende in de terminal:

```sh
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Download het pakket RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` van de [releases][] pagina op de machine Fedora.

Voer vervolgens het volgende in de terminal:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

U kunt ook de RPM zonder de tussenliggende stap voor het downloaden te installeren:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Gebruik van een recente Linux-distributie, downloaden de AppImage `powershell-6.0.1-x86_64.AppImage` van de [releases][] pagina naar de Linux-machine.

Voer vervolgens het volgende in de terminal:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

De [AppImage][] kunt u PowerShell uitvoeren zonder het te installeren.
Dit is een draagbare toepassing die u verzamelt van PowerShell en de afhankelijkheden ervan (inclusief .NET-Core system afhankelijkheden) in één samenhangender pakket.
Dit pakket is een enkele binaire waarde die geschikt is onafhankelijk van de Linux-distributie van de gebruiker.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

### <a name="installation"></a>Installatie

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>PowerShell uitvoeren in de meest recente Kali (Kali GNU/Linux Rolling) zonder het te installeren

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Verwijdering - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

PowerShell is momenteel alleen ondersteund op Raspbian Stretch.

Ook CoreCLR (en dus PowerShell Core) werkt alleen op apparaten Pi 2 en 3 Pi als andere apparaten, zoals [Pi nul](https://github.com/dotnet/coreclr/issues/10605), beschikken over een niet-ondersteunde processor.

Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) en volg de [installatie-instructies](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) downloaden naar uw Pi.

### <a name="installation"></a>Installatie

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

U kunt eventueel een symbolische koppeling om te kunnen PowerShell starten zonder op te geven van pad naar de binaire 'pwsh' maken

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Verwijdering - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Binaire archieven

PowerShell binair `tar.gz` archieven voor Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.

### <a name="dependencies"></a>Afhankelijkheden

PowerShell bouwt draagbare binaire bestanden voor alle Linux-distributies.
Maar .NET Core runtime verschillende afhankelijkheden op verschillende distributies vereist en daarom PowerShell hetzelfde effect heeft.

Het volgende diagram toont de afhankelijkheden voor .NET Core 2.0 die officieel ondersteund op verschillende Linux-distributies.

| Besturingssysteem                 | Afhankelijkheden |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42,2 <br> Fedora 25 | libunwind, libcurl, openssl-bibliotheken, libicu |
| Fedora 26          | libunwind, libcurl, openssl-bibliotheken, libicu, compat openssl10 |

U moet de vereiste afhankelijkheden voor het doel OS installeren in afzonderlijke stappen voor het implementeren van de binaire bestanden voor PowerShell op Linux-distributies die officieel niet worden ondersteund.
Bijvoorbeeld, onze [Amazon Linux dockerfile] [ amazon-dockerfile] afhankelijkheden als eerste geïnstalleerd en pakt vervolgens de Linux `tar.gz` archief.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installatie - binaire archieven

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Verwijderen binaire archieven

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Paden

* `$PSHOME` is `/opt/microsoft/powershell/6.0.2/`
* Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`
* Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`
* Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`
* Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`
* Standaardmodules worden gelezen uit `$PSHOME/Modules`
* Geschiedenis van PSReadline wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren van PowerShell per host-configuratie, zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.

PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Linux.

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
