---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 12/12/2018
ms.openlocfilehash: 70f5d64aa8a697a9011d07fbcb2bb821463827e1
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229732"
---
# <a name="installing-powershell-core-on-macos"></a>PowerShell Core in macOS installeren

PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.
Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.
Nadat het pakket is geïnstalleerd, voert u `pwsh` vanuit een terminal.

## <a name="about-brew"></a>Over Homebrew

[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.
Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].
Anders kunt u PowerShell via hebt geïnstalleerd [rechtstreeks downloaden](#installation-via-direct-download) of [binaire archieven](#binary-archives).

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installatie van de nieuwste stabiele versie via Homebrew in macOS 10.12 of hoger

Zie [over Brew](#about-brew) voor informatie over Homebrew.

Nu kunt u PowerShell hebt geïnstalleerd:

```sh
brew cask install powershell
```

Controleer ten slotte of het installeren van uw correct werkt:

```sh
pwsh
```

Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en vernieuwen van de waarden in `$PSVersionTable`.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installatie van de meest recente preview release via Homebrew in macOS 10.12 of hoger

Zie [over Brew](#about-brew) voor informatie over Homebrew.

Nadat u Homebrew hebt geïnstalleerd, kunt u PowerShell installeren.
Installeer eerst de [Cask-versies] [ cask-versions] pakket waarmee u alternatieve versies van cask pakketten installeren:

```sh
brew tap homebrew/cask-versions
```

Nu kunt u PowerShell hebt geïnstalleerd:

```sh
brew cask install powershell-preview
```

Controleer ten slotte of het installeren van uw correct werkt:

```sh
pwsh-preview
```

Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.
> en vernieuw de waarden in `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installatie via directe downloaden

Pak het pakket downloaden `powershell-6.2.0-osx-x64.pkg`
uit de [releases][] pagina naar uw macOS-computer.

U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

Installeer [OpenSSL](#install-openssl). OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.

## <a name="binary-archives"></a>Binaire archieven

PowerShell binaire `tar.gz` archieven worden opgegeven voor het macOS-platform om in te schakelen geavanceerde implementatiescenario's.

### <a name="installing-binary-archives-on-macos"></a>Installeren van de binaire archieven in macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

Installeer [OpenSSL](#install-openssl). OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen.

## <a name="installing-dependencies"></a>Installatie van afhankelijkheden

### <a name="install-xcode-command-line-tools"></a>Opdrachtregelprogramma's van XCode installeren

```sh
xcode-select --install
```

### <a name="install-openssl"></a>OpenSSL installeren

OpenSSL is nodig voor externe communicatie van PowerShell en CIM-bewerkingen. U kunt installeren via MacPorts of Homebrew.

#### <a name="install-openssl-via-brew"></a>OpenSSL via Homebrew installeren

Zie [over Brew](#about-brew) voor informatie over Homebrew.

Voer voor het installeren van OpenSSL `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>OpenSSL via MacPorts installeren

1. Installeer de [XCode vanaf de opdrachtregel-hulpprogramma's](#install-xcode-command-line-tools).
1. MacPorts installeren.
   Als u instructies nodig hebt, raadpleegt u de [installatiehandleiding](https://guide.macports.org/chunked/installing.macports.html).
1. MacPorts bijwerken door te voeren `sudo port selfupdate`.
1. Upgradepakketten voor besturings MacPorts door uit te voeren `sudo port upgrade outdated`.
1. OpenSSL installeren door te voeren `sudo port install openssl`.
1. Koppel de bibliotheken om deze beschikbaar maken voor PowerShell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>PowerShell Core verwijderen

Als u PowerShell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht uit om te verwijderen:

```sh
brew cask uninstall powershell
```

Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Als u wilt verwijderen van de extra PowerShell-paden, verwijzen naar de [paden](#paths) sectie in dit document en verwijder de paden met behulp van `sudo rm`.

> [!NOTE]
> Dit is niet nodig als u met Homebrew hebt geïnstalleerd.

## <a name="paths"></a>Paden

* `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`
* Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`
* Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`
* Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`
* Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`
* Standaardmodules worden gelezen in `$PSHOME/Modules`
* PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen met inachtneming van de PowerShell-per-host-configuratie.
Zodat het standaardprofiel voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.

PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.

Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.
Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Aanvullende bronnen

* [Homebrew Web][brew]
* [Homebrew Github-opslagplaats][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
