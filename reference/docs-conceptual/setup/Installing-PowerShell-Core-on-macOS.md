---
title: PowerShell Core in macOS installeren
description: Informatie over PowerShell Core in macOS installeren
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587462"
---
# <a name="installing-powershell-core-on-macos"></a>PowerShell Core in macOS installeren

PowerShell Core biedt ondersteuning voor macOS 10.12 en hoger.
Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.
Nadat het pakket is geïnstalleerd, voert `pwsh` vanuit een terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installatie via Homebrew in macOS 10.12 +

[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.
Typ in een terminalvenster `brew` om uit te voeren van Homebrew.  Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].

> [!NOTE]
> Als u Homebrew in het verleden hebt geïnstalleerd, is het altijd een goed idee om uit te voeren "brew bijwerken naar de fabrieksinstellingen" & & 'brew update'.
```sh
brew update-reset
brew update
```

> Oudere versies van Homebrew gebruikt de tikt u op 'caskroom/cask', die is afgeschaft, en naar homebrew/cask gemigreerd.  Meer informatie kunt vinden op [Homebrew-cask][cask]. Gebruik de opdracht 'homebrew tikt u op' om uw huidige tap's weer te geven.  Als u ' caskroom/cask' ziet u 'update brew' kunt gebruiken om de tap's migreren Homebrew.

```sh
brew tap
brew update
```

Nadat u geïnstalleerd / Homebrew bijgewerkt hebt, is het eenvoudig om PowerShell installeren.

Voor het installeren van PowerShell:

```sh
brew cask install powershell
```

Controleer ten slotte of het installeren van uw correct werkt:

```sh
pwsh
```

Als u PowerShell sluiten en keer terug naar bash-, gebruikt u de opdracht 'exit'.
```sh
exit
```

Wanneer er nieuwe versies van PowerShell worden uitgebracht, de Homebrew-formule bijwerken en PowerShell een upgrade uitvoert:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>Preview-versie via Homebrew in macOS 10.12 + installeren

[Homebrew] [ brew] is het gewenste pakketbeheerprogramma voor Mac OS.
Typ in een terminalvenster `brew` om uit te voeren van Homebrew.  Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew installeren [hun instructies][brew].

> [!NOTE]
> Als u Homebrew in het verleden hebt geïnstalleerd, is het altijd een goed idee om uit te voeren "brew bijwerken naar de fabrieksinstellingen" & & 'brew update'.
```sh
brew update-reset
brew update
```

U moet vervolgens, tik op de `versions` fusten opslagplaats om op te halen van de preview-pakket:

```sh
brew tap homebrew/cask-versions
```

Voor het installeren van PowerShell-voorbeeld:

```sh
brew cask install powershell-preview
```

Controleer ten slotte of het installeren van uw correct werkt:

```sh
pwsh-preview
```

Wanneer er nieuwe versies van PowerShell worden uitgebracht, bijwerken van Homebrew-formules en bijwerken van de PowerShell-voorbeeld:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden opgeroepen binnen een host PowerShell (pwsh), maar vervolgens de shell van PowerShell moet worden afgesloten en opnieuw gestart om de upgrade is voltooid en de waarden in $PSVersionTable vernieuwen.

### <a name="installation-via-direct-download"></a>Installatie via directe downloaden

Pak het pakket downloaden `powershell-6.0.2-osx.10.12-x64.pkg` uit de [releases][] pagina naar uw macOS-computer.

U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Binaire archieven

PowerShell binaire `tar.gz` archieven voor macOS en Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.

### <a name="installing-binary-archives-on-macos"></a>Installeren van de binaire archieven in macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
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

Als u wilt verwijderen van de extra PowerShell-paden, raadpleegt u de [paden][] sectie in dit document en verwijder de paden met behulp van de gewenste `sudo rm`.

> [!NOTE]
> Dit is niet nodig als u met Homebrew hebt geïnstalleerd.

[Paden]:#paths

## <a name="paths"></a>Paden

* `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`
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
Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Aanvullende bronnen

* [Homebrew Web][brew]
* [Homebrew Github-opslagplaats][GitHub]
* [Homebrew-Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
