---
title: PowerShell installeren in macOS
description: Informatie over het installeren van PowerShell in macOS
ms.date: 04/26/2021
ms.openlocfilehash: ea878dad1ce4d2ab2b48a34b5f89ba8ebb7c82c3
ms.sourcegitcommit: 1e1535cb22d16de06f80beafe77a37a7c77de6d3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025610"
---
# <a name="installing-powershell-on-macos"></a>PowerShell installeren in macOS

Voor PowerShell 7.0 of hoger is macOS 10.13 en hoger vereist. Alle pakketten zijn beschikbaar op onze pagina met [GitHub-releases.][] Nadat het pakket is geïnstalleerd, moet u `pwsh` uitvoeren vanuit een terminal.

> [!NOTE]
> PowerShell 7.1 is een in-place upgrade die PowerShell Core 6.x en 7.0 verwijdert.
>
> De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .
>
> Als u een oudere versie van PowerShell Core naast PowerShell 7.1 wilt uitvoeren, installeert u de versie die u wilt gebruiken met behulp van de [binaire archiefmethode.](#binary-archives)

Er zijn verschillende manieren om PowerShell in macOS te installeren. Kies één van de volgende methoden:

- Installeer met [behulp van Homebrew][brew]. Homebrew is het voorkeurspakketbeheer voor macOS.
- PowerShell installeren via [Direct downloaden](#installation-via-direct-download)
- Installeer vanuit [binaire archieven.](#binary-archives)

Nadat u PowerShell hebt geïnstalleerd, moet u [OpenSSL installeren.](#installing-dependencies) OpenSSL is nodig voor remoting- en CIM-bewerkingen in PowerShell.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a>Installatie van de nieuwste stabiele release via Homebrew in macOS 10.13 of hoger

Als de `brew` opdracht niet wordt gevonden, moet u Homebrew installeren volgens [de instructies][brew].

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

U kunt nu PowerShell installeren:

```sh
brew install --cask powershell
```

Controleer ten slotte of de installatie goed werkt:

```sh
pwsh
```

Wanneer er nieuwe versies van PowerShell worden uitgebracht, moet u de formule van Homebrew bijwerken en PowerShell upgraden:

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden aangeroepen vanuit een PowerShell-host (pwsh), maar vervolgens moet de PowerShell-shell worden afgesloten en opnieuw worden gestart om de upgrade te voltooien en de waarden in te `$PSVersionTable` vernieuwen.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a>Installatie van de nieuwste preview-versie via Homebrew in macOS 10.13 of hoger

Nadat u Homebrew hebt geïnstalleerd, kunt u PowerShell installeren. Installeer eerst het [pakket Cask-Versions][cask-versions] waarmee u alternatieve versies van cask-pakketten kunt installeren:

```sh
brew tap homebrew/cask-versions
```

Nu kunt u PowerShell installeren:

```sh
brew install --cask powershell-preview
```

Controleer ten slotte of de installatie goed werkt:

```sh
pwsh-preview
```

Wanneer er nieuwe versies van PowerShell worden uitgebracht, kunt u de formules van Homebrew bijwerken en PowerShell upgraden:

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden aangeroepen vanuit een PowerShell-host (pwsh), maar vervolgens moet de PowerShell-shell worden afgesloten en opnieuw worden gestart om de upgrade te voltooien.
> en vernieuw de waarden die worden weergegeven in `$PSVersionTable` .

Het installeren van PowerShell met behulp van de Homebrew-tikmethode wordt ook ondersteund voor stabiele en LTS-versies.

```sh
brew install powershell/tap/powershell
```

U kunt nu uw installatie controleren

```sh
pwsh
```

Wanneer er nieuwe versies van PowerShell worden uitgebracht, kunt u gewoon de volgende opdracht uitvoeren.

```sh
brew upgrade powershell
```

> [!NOTE]
> Of u nu het cask- of de tikmethode gebruikt, bij het bijwerken naar een nieuwere versie van PowerShell gebruikt u dezelfde methode die u hebt gebruikt om PowerShell in eerste instantie te installeren. Als u een andere methode gebruikt, blijft het openen van een nieuwe pwsh-sessie de oudere versie van PowerShell gebruiken.
>
> Als u besluit verschillende methoden te gebruiken, zijn er manieren om het probleem op te lossen met behulp van de [Homebrew-koppelingsmethode](https://docs.brew.sh/Manpage#link-ln-options-formula).

## <a name="installation-via-direct-download"></a>Installatie via Direct downloaden

Download het PKG-pakket `powershell-7.1.3-osx-x64.pkg` van de [releasepagina][] op uw macOS-computer.

U kunt dubbelklikken op het bestand en de aanwijzingen volgen of het installeren vanuit de terminal:

```sh
sudo installer -pkg powershell-7.1.3-osx-x64.pkg -target /
```

Installeer [OpenSSL.](#installing-dependencies) OpenSSL is nodig voor remoting- en CIM-bewerkingen van PowerShell.

## <a name="install-as-a-net-global-tool"></a>Installeren als een .NET Global-hulpprogramma

Als u de .NET Core SDK [al](/dotnet/core/sdk) hebt geïnstalleerd, kunt u PowerShell eenvoudig installeren als [een .NET Global-hulpprogramma.](/dotnet/core/tools/global-tools)

```
dotnet tool install --global PowerShell
```

Het dotnet-hulpprogramma-installatieprogramma wordt `~/.dotnet/tools` toegevoegd aan uw `PATH` omgevingsvariabele. De momenteel lopende shell heeft echter niet de bijgewerkte `PATH` . U moet PowerShell vanuit een nieuwe shell kunnen starten door te `pwsh` typen.

Installeer [OpenSSL.](#installing-dependencies) OpenSSL is nodig voor remoting- en CIM-bewerkingen in PowerShell.

## <a name="binary-archives"></a>Binaire archieven

Er zijn binaire `tar.gz` PowerShell-archieven beschikbaar voor het macOS-platform om geavanceerde implementatiescenario's mogelijk te maken. Wanneer u met deze methode installeert, moet u ook handmatig eventuele afhankelijkheden installeren.

Installeer [OpenSSL.](#installing-dependencies) OpenSSL is nodig voor remoting- en CIM-bewerkingen in PowerShell.

> [!NOTE]
> U kunt deze methode gebruiken om elke versie van PowerShell te installeren, inclusief de nieuwste versie:
> - Stabiele release: [https://aka.ms/powershell-release?tag=stable](https://aka.ms/powershell-release?tag=stable)
> - Preview-versie: [https://aka.ms/powershell-release?tag=preview](https://aka.ms/powershell-release?tag=preview)
> - LTS-release: [https://aka.ms/powershell-release?tag=lts](https://aka.ms/powershell-release?tag=lts)

### <a name="installing-binary-archives-on-macos"></a>Binaire archieven installeren in macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.3/powershell-7.1.3-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.3

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.3

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.3/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.3/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a>Afhankelijkheden installeren

OpenSSL is vereist voor remoting- en CIM-bewerkingen in PowerShell. U kunt OpenSSL indien nodig installeren via MacPorts.

> [!NOTE]
> MacPorts en Homebrew kunnen problemen hebben wanneer ze worden gebruikt in hetzelfde systeem. Homebrew heeft echter geen pakket voor OpenSSL 1.0. Zie de Veelgestelde vragen over [MacPorts voor meer informatie.](https://trac.macports.org/wiki/FAQ)

1. Installeer de Xcode-opdrachtregelprogramma's. De Xcode-hulpprogramma's zijn vereist voor MacPorts.

   ```sh
   xcode-select --install
   ```

1. Installeer MacPorts. Raadpleeg de installatiehandleiding als u [instructies nodig hebt.](https://www.macports.org/install.php)
1. Werk MacPorts bij door uit te `sudo port selfupdate` werken.
1. Upgrade MacPorts-pakketten door uit te `sudo port upgrade outdated` voeren.
1. Installeer OpenSSL door uit te `sudo port install openssl10` gaan.
1. Koppel de bibliotheken om ze beschikbaar te maken voor PowerShell:

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a>PowerShell verwijderen

Als u PowerShell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:

```sh
brew --cask uninstall powershell
```

Als u PowerShell hebt geïnstalleerd via direct downloaden, moet PowerShell handmatig worden verwijderd:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Als u de extra PowerShell-paden wilt verwijderen, raadpleegt u de [sectie paden](#paths) in dit document en verwijdert u de paden met behulp van `sudo rm` .

> [!NOTE]
> Dit is niet nodig als u hebt geïnstalleerd met Homebrew.

## <a name="paths"></a>Paden

- `$PSHOME` is `/usr/local/microsoft/powershell/7.1.3/`
- Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`
- Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`
- Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`
- Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`
- Standaardmodules worden gelezen uit `$PSHOME/Modules`
- De PSReadline-geschiedenis wordt vastgelegd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren de configuratie per host van PowerShell. Het standaard hostspecifieke profiel bevindt zich dus `Microsoft.PowerShell_profile.ps1` op dezelfde locaties.

PowerShell respecteert de [XDG-basismapspecificatie][xdg-bds] in macOS.

Omdat macOS een afleiding van BSD is, wordt het voorvoegsel `/usr/local` gebruikt in plaats van `/opt` . Is dus `$PSHOME` `/usr/local/microsoft/powershell/7.1.3/` en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh` .

## <a name="installation-support"></a>Ondersteuning voor installatie

Microsoft ondersteunt de installatiemethoden in dit document. Er zijn mogelijk andere installatiemethoden beschikbaar vanuit andere bronnen. Hoewel deze hulpprogramma's en methoden kunnen werken, biedt Microsoft geen ondersteuning voor deze methoden.

## <a name="additional-resources"></a>Aanvullende resources

- [Homebrew Web][brew]
- [Homebrew Github-opslagplaats][GitHub]
- [Homebrew-Cask][cask]

[brew]: https://docs.brew.sh/Installation
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[Releases]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
