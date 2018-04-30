# <a name="installing-powershell-core-on-macos"></a>PowerShell Core installeert op Mac OS

PowerShell Core biedt ondersteuning voor Mac OS 10.12 en hoger.
Alle pakketten zijn beschikbaar op onze GitHub [releases][] pagina.
Wanneer het pakket is geïnstalleerd, uitvoeren `pwsh` vanaf een terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installatie via Homebrew op Mac OS 10,12

[Homebrew] [ brew] is de voorkeur package manager voor Mac OS.
Als de `brew` opdracht is niet gevonden, moet u de volgende Homebrew geïnstalleerd [hun instructies][brew].

Zodra u Homebrew hebt geïnstalleerd, is het eenvoudig om PowerShell installeren.
Installeer eerst [Homebrew Cask][cask], zodat u kunt meer pakketten installeren:

```sh
brew tap caskroom/cask
```

U kunt nu PowerShell installeren:

```sh
brew cask install powershell
```

Controleer ten slotte of het installeren van uw correct werkt:

```sh
pwsh
```

Wanneer er nieuwe versies van PowerShell zijn uitgebracht, Homebrew van formules bijwerken en upgrade uitvoeren van PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> De bovenstaande opdrachten kunnen worden aangeroepen vanuit een host PowerShell (pwsh), maar de PowerShell-shell moet worden afgesloten en opnieuw worden opgestart om de upgrade te voltooien.
> en de waarden in $PSVersionTable vernieuwen.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a>Installatie via directe Download

Pak het pakket downloaden `powershell-6.0.2-osx.10.12-x64.pkg` van de [releases][] pagina op uw Mac OS-machine.

U kunt dubbelklikken op het bestand en volg de aanwijzingen of installeren vanaf de terminal:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Binaire archieven

PowerShell binair `tar.gz` archieven voor Mac OS- en Linux-platformen om in te schakelen geavanceerde implementatiescenario's worden geleverd.

### <a name="installing-binary-archives-on-macos"></a>Installeren van de binaire archieven op Mac OS

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

Als u met Homebrew PowerShell hebt geïnstalleerd, is het verwijderen is eenvoudig:

```sh
brew cask uninstall powershell
```

Als u via de directe download PowerShell hebt geïnstalleerd, moet PowerShell handmatig worden verwijderd:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Als u wilt de aanvullende PowerShell paden verwijderen, raadpleegt u de [paden][] sectie in dit document en verwijdert u de paden met behulp van de gewenste `sudo rm`.

> [!NOTE]
> Dit is niet nodig als u met Homebrew geïnstalleerd.

[paden]:#paths

## <a name="paths"></a>Paden

* `$PSHOME` is `/opt/microsoft/powershell/6.0.0/`
* Gebruikersprofielen worden gelezen uit `~/.config/powershell/profile.ps1`
* Standaardprofielen worden gelezen uit `$PSHOME/profile.ps1`
* Gebruikersmodules worden gelezen uit `~/.local/share/powershell/Modules`
* Gedeelde modules worden gelezen uit `/usr/local/share/powershell/Modules`
* Standaardmodules worden gelezen uit `$PSHOME/Modules`
* Geschiedenis van PSReadline wordt vastgelegd `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

De profielen respecteren van PowerShell per host-configuratie.
Zodat er op de host-specifieke standaardprofielen bestaat `Microsoft.PowerShell_profile.ps1` in dezelfde locaties.

PowerShell respecteert de [XDG Base Directory specificatie] [ xdg-bds] op Mac OS.

Omdat Mac OS geen afwijking van BSD, het voorvoegsel is `/usr/local` wordt gebruikt in plaats van `/opt`.
Dus `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, en de symlink wordt geplaatst op `/usr/local/bin/pwsh`.

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
