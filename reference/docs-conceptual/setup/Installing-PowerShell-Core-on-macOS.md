---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611484"
---
# <a name="installing-powershell-core-on-macos"></a>PowerShell Core in macOS installeren

PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.
Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.
Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installatie van de nieuwste stabiele versie via Homebrew in macOS 10.12 of hoger

[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.
Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].

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
> De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.
> en vernieuw de waarden in $PSVersionTable.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installatie van de meest recente preview release via Homebrew in macOS 10.12 of hoger

[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.
Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].

Nadat u Homebrew hebt geïnstalleerd, is het eenvoudig om PowerShell installeren.
Installeer eerst [Cask-versies] [ cask-versions] waarmee u alternatieve versies van cask pakketten installeren:

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
> en vernieuw de waarden in $PSVersionTable.

## <a name="installation-via-direct-download"></a>Installatie via directe downloaden

Pak het pakket downloaden `powershell-6.1.0-osx-x64.pkg`
uit de [releases][] pagina naar uw macOS-computer.

U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a>Binaire archieven

PowerShell binaire `tar.gz` archieven worden opgegeven voor het macOS-platform om in te schakelen geavanceerde implementatiescenario's.

### <a name="installing-binary-archives-on-macos"></a>Installeren van de binaire archieven in macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>PowerShell Core verwijderen

Als u PowerShell hebt geïnstalleerd met Homebrew, is verwijderen is eenvoudig:

```sh
brew cask uninstall powershell
```

Als u PowerShell hebt geïnstalleerd via de directe download, moet PowerShell handmatig worden verwijderd:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Als u wilt verwijderen van de extra PowerShell-paden, raadpleegt u de [paden](#paths) sectie in dit document en verwijder de paden met behulp van de gewenste `sudo rm`.

> [!NOTE]
> Dit is niet nodig als u met Homebrew hebt geïnstalleerd.

## <a name="paths"></a>Paden

* `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`
* Gebruikersprofielen worden gelezen in `~/.config/powershell/profile.ps1`
* Standaardprofielen worden gelezen in `$PSHOME/profile.ps1`
* Gebruikersmodules worden gelezen in `~/.local/share/powershell/Modules`
* Gedeelde modules worden gelezen in `/usr/local/share/powershell/Modules`
* Standaardmodules worden gelezen in `$PSHOME/Modules`
* PSReadline geschiedenis wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen met inachtneming van de PowerShell-per-host-configuratie.
Zodat de standaardprofielen voor de host-specifieke bestaat op `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.

PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] in macOS.

Omdat Mac OS een afleiding van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.
Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.

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
