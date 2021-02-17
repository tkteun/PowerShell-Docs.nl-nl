---
title: PowerShell installeren in macOS
description: Informatie over het installeren van Power shell in macOS
ms.date: 02/02/2021
ms.openlocfilehash: 3ae1fe0eb29b4d826221a2c11db19bc18c3efba7
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563212"
---
# <a name="installing-powershell-on-macos"></a>PowerShell installeren in macOS

Voor Power shell 7,0 of hoger is macOS 10,13 en hoger vereist. Alle pakketten zijn beschikbaar op onze pagina met GitHub- [releases][] . Nadat het pakket is geïnstalleerd, voert u `pwsh` uit vanaf een Terminal.

> [!NOTE]
> Power shell 7,1 is een in-place upgrade waarmee Power shell Core 6. x en 7,0 worden verwijderd.
>
> De `/usr/local/microsoft/powershell/6` map wordt vervangen door `/usr/local/microsoft/powershell/7` .
>
> Als u een oudere versie van Power shell core naast Power shell 7,1 wilt uitvoeren, installeert u de gewenste versie met behulp van de [binaire archief](#binary-archives) methode.

Er zijn verschillende manieren om Power shell op macOS te installeren. Kies één van de volgende methoden:

- Installeer met behulp van homebrew. Homebrew is de voorkeurs pakket beheerder voor macOS.
- Power Shell installeren via [direct downloaden](#installation-via-direct-download)
- Installeren vanuit [binaire archieven](#binary-archives).

Nadat u Power shell hebt geïnstalleerd, moet u [openssl](#installing-dependencies)installeren. OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a>Installatie van de laatste stabiele release via homebrew op macOS 10,13 of hoger

Als de `brew` opdracht niet wordt gevonden, moet u homebrew installeren volgens [de instructies][brew].

U kunt nu Power Shell installeren:

```sh
brew install --cask powershell
```

Controleer ten slotte of uw installatie goed werkt:

```sh
pwsh
```

Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien en de waarden die worden weer gegeven in te vernieuwen `$PSVersionTable` .

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a>Installatie van de nieuwste preview-versie via homebrew op macOS 10,13 of hoger

Nadat u homebrew hebt geïnstalleerd, kunt u Power Shell installeren. Installeer eerst het pakket met [Cask versies][cask-versions] waarmee u alternatieve versies van Cask-pakketten kunt installeren:

```sh
brew tap homebrew/cask-versions
```

U kunt nu Power Shell installeren:

```sh
brew install --cask powershell-preview
```

Controleer ten slotte of uw installatie goed werkt:

```sh
pwsh-preview
```

Wanneer er nieuwe versies van Power shell worden uitgebracht, werkt u de Power shell-formule voor homebrew en upgrade bij:

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden aangeroepen vanuit een Power shell-host (pwsh), maar vervolgens moet de Power shell-shell worden afgesloten en opnieuw worden gestart om de upgrade te volt ooien.
> en vernieuw de waarden die worden weer gegeven in `$PSVersionTable` .

Het installeren van Power shell met de methode homebrew tap wordt ook ondersteund voor stabiele en LTS-versies.

```sh
brew install powershell/tap/powershell
```

U kunt nu uw installatie controleren

```sh
pwsh
```

Wanneer er nieuwe versies van Power shell worden uitgebracht, voert u gewoon de volgende opdracht uit.

```sh
brew upgrade powershell
```

> [!NOTE]
> Ongeacht of u de Cask of de methode tap gebruikt wanneer u een update uitvoert naar een nieuwere versie van Power shell, gebruikt u dezelfde methode die u hebt gebruikt om Power shell voor het eerst te installeren. Als u een andere methode gebruikt, blijft het openen van een nieuwe pwsh-sessie de oudere versie van Power shell blijven gebruiken.
>
> Als u besluit verschillende methoden te gebruiken, zijn er manieren om het probleem op te lossen met behulp van de [homebrew-koppelings methode](https://docs.brew.sh/Manpage#link-ln-options-formula).

## <a name="installation-via-direct-download"></a>Installatie via direct downloaden

Down load het pakket Package `powershell-7.1.2-osx-x64.pkg` van de pagina [releases][] op uw macOS-computer.

U kunt dubbel klikken op het bestand en de prompts volgen of installeren vanaf de terminal:

```sh
sudo installer -pkg powershell-7.1.2-osx-x64.pkg -target /
```

Installeer [openssl](#installing-dependencies). OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.

## <a name="install-as-a-net-global-tool"></a>Installeren als een Global .NET-hulp programma

Als u de [.net core SDK](/dotnet/core/sdk) al hebt geïnstalleerd, kunt u Power shell eenvoudig installeren als een [wereld wijd .net-hulp programma](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Het hulp programma DotNet tool wordt toegevoegd `~/.dotnet/tools` aan de `PATH` omgevings variabele. De momenteel actieve shell beschikt echter niet over de bijgewerkte versie `PATH` . U moet Power shell kunnen starten vanuit een nieuwe shell door te typen `pwsh` .

Installeer [openssl](#installing-dependencies). OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.

## <a name="binary-archives"></a>Binaire archieven

Er zijn binaire Power shell- `tar.gz` archieven beschikbaar voor het macOS-platform om geavanceerde implementatie scenario's mogelijk te maken. Wanneer u met deze methode installeert, moet u ook hand matig afhankelijkheden installeren.

Installeer [openssl](#installing-dependencies). OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen.

### <a name="installing-binary-archives-on-macos"></a>Binaire archieven installeren op macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.2/powershell-7.1.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.2/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a>Afhankelijkheden installeren

OpenSSL is vereist voor externe communicatie met Power shell en CIM-bewerkingen. U kunt OpenSSL installeren via MacPorts, indien nodig.

> [!NOTE]
> MacPorts en homebrew kunnen problemen ondervinden wanneer ze worden gebruikt voor samen werking op hetzelfde systeem. Homebrew heeft echter geen pakket voor OpenSSL 1,0. Zie de [Veelgestelde vragen over MacPorts](https://trac.macports.org/wiki/FAQ)voor meer informatie.

1. Installeer de Xcode-opdracht regel Programma's. De Xcode-hulpprogram ma's zijn vereist door MacPorts.

   ```sh
   xcode-select --install
   ```

1. Installeer MacPorts. Raadpleeg de [installatie handleiding](https://www.macports.org/install.php)als u instructies nodig hebt.
1. Werk MacPorts bij door uit te voeren `sudo port selfupdate` .
1. Upgrade MacPorts packages door uit te voeren `sudo port upgrade outdated` .
1. Installeer OpenSSL door uit te voeren `sudo port install openssl10` .
1. Koppel de bibliotheken om ze beschikbaar te maken voor Power shell:

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a>Power shell verwijderen

Als u Power shell hebt geïnstalleerd met Homebrew, gebruikt u de volgende opdracht om te verwijderen:

```sh
brew cask uninstall powershell
```

Als u Power shell hebt geïnstalleerd via direct downloaden, moet Power shell hand matig worden verwijderd:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Als u de extra Power shell-paden wilt verwijderen, raadpleegt u de sectie [paden](#paths) in dit document en verwijdert u de paden met `sudo rm` .

> [!NOTE]
> Dit is niet nodig als u hebt geïnstalleerd met homebrew.

## <a name="paths"></a>Paden

- `$PSHOME` is `/usr/local/microsoft/powershell/7.1.2/`
- Gebruikers profielen worden gelezen van `~/.config/powershell/profile.ps1`
- Standaard profielen worden gelezen uit `$PSHOME/profile.ps1`
- Gebruikers modules worden gelezen uit `~/.local/share/powershell/Modules`
- Gedeelde modules worden gelezen van `/usr/local/share/powershell/Modules`
- Standaard modules worden gelezen van `$PSHOME/Modules`
- De PSReadline-geschiedenis wordt vastgelegd in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren de configuratie van de Power shell per host. Het standaard-host-profiel bestaat dus op `Microsoft.PowerShell_profile.ps1` dezelfde locatie.

Power shell respecteert de [XDG-basis directory specificatie][xdg-bds] op macOS.

Omdat macOS een afleiding van BSD is, wordt het voor voegsel `/usr/local` gebruikt in plaats van `/opt` . Dat `$PSHOME` wil zeggen `/usr/local/microsoft/powershell/7.1.2/` , en de symbolische koppeling wordt geplaatst op `/usr/local/bin/pwsh` .

## <a name="installation-support"></a>Ondersteuning voor installatie

Micro soft ondersteunt de installatie methoden in dit document. Er zijn mogelijk andere methoden van installatie beschikbaar van andere bronnen. Deze hulpprogram ma's en methoden kunnen werken, maar deze methoden kunnen niet door micro soft worden ondersteund.

## <a name="additional-resources"></a>Aanvullende resources

- [Homebrew-Web][brew]
- [Homebrew github-opslag plaats][GitHub]
- [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[shell]: https://aka.ms/powershell-release?tag=stable
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
