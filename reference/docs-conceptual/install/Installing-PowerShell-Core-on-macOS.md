---
title: PowerShell Core in macOS installeren
description: Informatie over het installeren van Power shell core in macOS
ms.date: 12/12/2018
ms.openlocfilehash: b7ea1d494b12d31ffec330a0a68e282a05b011fc
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78280286"
---
# <a name="installing-powershell-core-on-macos"></a>PowerShell Core in macOS installeren

Power shell core ondersteunt macOS 10,12 en hoger.
Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] .
Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.

> [!NOTE]
> Power shell 7 is een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.
>
> De map `/usr/local/microsoft/powershell/6` wordt vervangen door `/usr/local/microsoft/powershell/7`.
>
> Als u Power shell 6 side-by-side wilt uitvoeren met Power shell 7, installeert u Power shell 6 opnieuw met behulp van de [binaire archief](#binary-archives) methode.

## <a name="about-brew"></a>Over Brew

[Homebrew][brew] is de voorkeurs pakket beheerder voor macOS. Als de `brew` opdracht niet wordt gevonden, moet u homebrew installeren volgens [de instructies][brew]. Anders kunt u Power Shell installeren via [direct downloaden](#installation-via-direct-download) of vanuit [binaire archieven](#binary-archives).

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installatie van de laatste stabiele release via homebrew op macOS 10,12 of hoger

Zie [about Brew](#about-brew) voor informatie over Brew.

U kunt nu Power Shell installeren:

```sh
brew cask install powershell
```

Controleer ten slotte of uw installatie goed werkt:

```sh
pwsh
```

Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien en de waarden te vernieuwen die worden weer gegeven in `$PSVersionTable`.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installatie van de nieuwste preview-versie via homebrew op macOS 10,12 of hoger

Zie [about Brew](#about-brew) voor informatie over Brew.

Nadat u homebrew hebt geïnstalleerd, kunt u Power Shell installeren.
Installeer eerst het pakket met [Cask versies][cask-versions] waarmee u alternatieve versies van Cask-pakketten kunt installeren:

```sh
brew tap homebrew/cask-versions
```

U kunt nu Power Shell installeren:

```sh
brew cask install powershell-preview
```

Controleer ten slotte of uw installatie goed werkt:

```sh
pwsh-preview
```

Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien.
> en de waarden vernieuwen die worden weer gegeven in `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installatie via direct downloaden

Down load het pakket package `powershell-6.2.0-osx-x64.pkg`
van de pagina [releases][] op uw macOS-computer.

U kunt dubbel klikken op het bestand en de prompts volgen of installeren vanaf de terminal:

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

Installeer [openssl](#install-openssl). OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.

## <a name="install-as-a-net-global-tool"></a>Installeren als een Global .NET-hulp programma

Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

## <a name="binary-archives"></a>Binaire archieven

Er zijn binaire Power shell-`tar.gz` archieven beschikbaar voor het macOS-platform om geavanceerde implementatie scenario's mogelijk te maken.

### <a name="installing-binary-archives-on-macos"></a>Binaire archieven installeren op macOS

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

Installeer [openssl](#install-openssl). OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.

## <a name="installing-dependencies"></a>Afhankelijkheden installeren

### <a name="install-xcode-command-line-tools"></a>Opdracht regel Programma's voor XCode installeren

```sh
xcode-select --install
```

### <a name="install-openssl"></a>OpenSSL installeren

OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen. U kunt installeren via MacPorts of Brew.

#### <a name="install-openssl-via-brew"></a>OpenSSL installeren via Brew

Zie [about Brew](#about-brew) voor informatie over Brew.

Voer `brew install openssl`uit om OpenSSL te installeren.

#### <a name="install-openssl-via-macports"></a>OpenSSL installeren via MacPorts

1. Installeer de [Xcode-opdracht regel Programma's](#install-xcode-command-line-tools).
1. Installeer MacPorts.
   Raadpleeg de [installatie handleiding](https://guide.macports.org/chunked/installing.macports.html)als u instructies nodig hebt.
1. Werk MacPorts bij door `sudo port selfupdate`uit te voeren.
1. Upgrade MacPorts-pakketten door `sudo port upgrade outdated`uit te voeren.
1. Installeer OpenSSL door `sudo port install openssl`uit te voeren.
1. Koppel de bibliotheken om ze beschikbaar te maken voor Power shell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Power shell core verwijderen

Als u Power shell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:

```sh
brew cask uninstall powershell
```

Als u Power shell hebt geïnstalleerd via direct downloaden, moet Power shell hand matig worden verwijderd:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Als u de extra Power shell-paden wilt verwijderen, raadpleegt u de sectie [paden](#paths) in dit document en verwijdert u de paden met behulp van `sudo rm`.

> [!NOTE]
> Dit is niet nodig als u hebt geïnstalleerd met homebrew.

## <a name="paths"></a>Paden

* `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`
* Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`
* Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`
* Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`
* Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`
* Standaard modules worden gelezen uit `$PSHOME/Modules`
* De PSReadline-geschiedenis wordt geregistreerd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren de configuratie van de Power shell per host.
Het standaard-host-profiel bestaat dus op `Microsoft.PowerShell_profile.ps1` op dezelfde locatie.

Power shell respecteert de [XDG-basis directory specificatie][xdg-bds] op macOS.

Omdat macOS een afleiding van BSD is, wordt het voor voegsel `/usr/local` gebruikt in plaats van `/opt`.
`$PSHOME` is dus `/usr/local/microsoft/powershell/6.2.0/`en de symbolische koppeling wordt in `/usr/local/bin/pwsh`geplaatst.

## <a name="additional-resources"></a>Extra bronnen

* [Homebrew-Web][brew]
* [Homebrew github-opslag plaats][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
