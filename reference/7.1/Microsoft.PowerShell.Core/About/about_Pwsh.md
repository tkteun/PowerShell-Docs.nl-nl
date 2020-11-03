---
description: Hierin wordt uitgelegd hoe u de `pwsh` opdracht regel interface gebruikt. Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.
keywords: powershell,cmdlet
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: c71848e327822f7cbc659310d3fa47a5a46a37a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252660"
---
# <a name="about-pwsh"></a>Over pwsh

## <a name="short-description"></a>Korte beschrijving
Hierin wordt uitgelegd hoe u de `pwsh` opdracht regel interface gebruikt. Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.

## <a name="long-description"></a>Lange beschrijving

## <a name="syntax"></a>Syntaxis

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a>Parameters

Alle para meters zijn hoofdletter gevoelig.

### <a name="-file---f"></a>-Bestand | -f

Als de waarde van `File` is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.
Als u `pwsh -File -` zonder omgeleide standaard invoer uitvoert, wordt een reguliere sessie gestart. Dit is hetzelfde als het niet opgeven `File` van de para meter.

Dit is de standaard parameter als er geen para meters aanwezig zijn, maar waarden wel aanwezig zijn in de opdracht regel. Het opgegeven script wordt uitgevoerd in het lokale bereik (' dot-sourced '), zodat de functies en variabelen die het script maakt, beschikbaar zijn in de huidige sessie. Voer het pad naar het script bestand en eventuele para meters in. Het bestand moet de laatste para meter in de opdracht zijn, omdat alle tekens die na de naam van de bestands parameter worden getypt, worden geïnterpreteerd als het pad naar het script bestand, gevolgd door de script parameters.

Normaal gesp roken worden de switch parameters van een script opgenomen of wegge laten.
Met de volgende opdracht wordt bijvoorbeeld de para meter all van het Get-Script.ps1 script bestand gebruikt: `-File .\Get-Script.ps1 -All`

In zeldzame gevallen moet u mogelijk een **Booleaanse** waarde voor een switch parameter opgeven. Als u een **Boole** -waarde voor een para meter switch wilt opgeven in de waarde van de **Bestands** parameter, gebruikt u de para meter normaal gesp roken onmiddellijk gevolgd door een dubbele punt en de Booleaanse waarde, zoals de volgende: `-File .\Get-Script.ps1 -All:$False` .

Para meters die aan het script worden door gegeven, worden als letterlijke teken reeksen door gegeven na de interpretatie van de huidige shell. Als u bijvoorbeeld in bent `cmd.exe` en een waarde voor een omgevings variabele wilt door geven, gebruikt u de volgende `cmd.exe` syntaxis: `pwsh -File .\test.ps1 -TestParam %windir%`

In daarentegen wordt `pwsh -File .\test.ps1 -TestParam $env:windir` de `cmd.exe` letterlijke teken reeks ontvangen in resultaten van het script `$env:windir` omdat het geen speciale betekenis heeft voor de huidige `cmd.exe` shell. De `$env:windir` stijl van de verwijzing naar een omgevings variabele _kan_ worden gebruikt binnen een **opdracht** parameter, omdat deze wordt geïnterpreteerd als Power shell-code.

Als u dezelfde opdracht uit een _batch script_ wilt uitvoeren, gebruikt u `%~dp0` in plaats van `.\` of `$PSScriptRoot` om de huidige uitvoerings Directory te vertegenwoordigen: `pwsh -File %~dp0test.ps1 -TestParam %windir%` . Als u in plaats daarvan gebruikt `.\test.ps1` , genereert Power shell een fout omdat het letterlijke pad niet kan worden gevonden `.\test.ps1`

Wanneer het script bestand met een `exit` opdracht wordt beëindigd, wordt de afsluit code van het proces ingesteld op het numerieke argument dat met de opdracht wordt gebruikt `exit` . Bij normale beëindiging is de afsluit code altijd `0` .

Net als bij `-Command` het beëindigen van een script wordt de afsluit code ingesteld op `1` . Maar in tegens telling tot `-Command` , wanneer de uitvoering wordt onderbroken met <kbd>CTRL</kbd> - <kbd>C</kbd> , is de afsluit code `0` .

### <a name="-command---c"></a>-Opdracht | -c

Hiermee worden de opgegeven opdrachten (en eventuele para meters) uitgevoerd alsof ze zijn getypt bij de Power shell-opdracht prompt en vervolgens afgesloten, tenzij de `NoExit` para meter is opgegeven.

De waarde van de **opdracht** kan `-` een script blok of een teken reeks zijn. Als de waarde van de **opdracht** is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.

De **opdracht** parameter accepteert alleen een script blok voor uitvoering wanneer het de **waarde die wordt door gegeven, kan** herkennen als een **script Block** -type. Dit kan _alleen_ worden uitgevoerd `pwsh` vanuit een andere Power shell-host. Het type **script Block** kan worden opgenomen in een bestaande variabele, geretourneerd vanuit een expressie, of door de Power shell-host geparseerd als een letterlijk script blok tussen accolades ( `{}` ) voordat het wordt door gegeven aan `pwsh` .

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

In `cmd.exe` is er geen script blok (of **script Block** -type), dus de waarde die is door gegeven aan de **opdracht** , is _altijd_ een teken reeks. U kunt een script blok schrijven in de teken reeks, maar in plaats van dat het wordt uitgevoerd, werkt het niet exact alsof u het hebt getypt bij een typische Power shell-prompt, waarbij de inhoud van het script blok wordt weer gegeven.

Een teken reeks die aan de **opdracht** is door gegeven, wordt nog steeds uitgevoerd als Power shell-code, dus de accolades voor het blok keren van een script zijn in de eerste plaats vaak niet vereist tijdens de uitvoering van `cmd.exe` . Voor het uitvoeren van een inline-script blok dat in een teken reeks is gedefinieerd, kan de [aanroep operator](about_operators.md#special-operators) `&` worden gebruikt:

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

Als de waarde van de **opdracht** een teken reeks is, moet de **opdracht** de laatste para meter zijn voor pwsh, omdat alle argumenten die deze bevat, worden geïnterpreteerd als onderdeel van de opdracht die moet worden uitgevoerd.

Bij het aanroepen vanuit een bestaande Power shell-sessie worden de resultaten geretourneerd naar de bovenliggende shell als gedeserialiseerd XML-objecten, niet live-objecten. Voor andere shells worden de resultaten geretourneerd als teken reeksen.

Als de waarde van de **opdracht** is `-` , wordt de opdracht tekst gelezen uit de standaard invoer. U moet de standaard invoer omleiden wanneer u de **opdracht** parameter gebruikt met standaard invoer. Bijvoorbeeld:

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

In dit voor beeld wordt de volgende uitvoer gegenereerd:

```Output
in
hi there
out
```

De afsluit code van het proces wordt bepaald door de status van de laatste (uitgevoerde) opdracht in het-script blok. De afsluit code is `0` `$?` `$true` of wanneer dat `1` `$?` zo is `$false` . Als de laatste opdracht een extern programma of een Power shell-script is waarmee expliciet een andere afsluit code dan of wordt ingesteld `0` `1` , wordt die afsluit code geconverteerd naar `1` voor de afsluit code van het proces. Als u de specifieke afsluit code wilt behouden, voegt `exit $LASTEXITCODE` u toe aan de opdracht reeks of het script blok.

Op dezelfde manier wordt de waarde 1 geretourneerd als er een fout optreedt bij het beëindigen van een script (runs, afgebroken), zoals een `throw` of `-ErrorAction Stop` , wanneer de uitvoering wordt onderbroken door <kbd>CTRL</kbd> - <kbd>C</kbd>.

### <a name="-configurationname---config"></a>-Configuratiepad | -config

Hiermee geeft u een configuratie-eind punt waarin Power shell wordt uitgevoerd. Dit kan elk eind punt zijn dat is geregistreerd op de lokale computer, met inbegrip van de standaard externe communicatie-eind punten in Power shell of een aangepast eind punt met specifieke mogelijkheden voor de gebruikersrol.

Voorbeeld: `pwsh -ConfigurationName AdminRoles`

### <a name="-custompipename"></a>-CustomPipeName

Hiermee geeft u de naam op die moet worden gebruikt voor een extra IPC-server (named pipe) die wordt gebruikt voor fout opsporing en andere communicatie tussen processen. Dit biedt een voorspelbaar mechanisme om verbinding te maken met andere Power shell-exemplaren. Wordt meestal gebruikt met de para meter **CustomPipeName** op `Enter-PSHostProcess` .

Deze para meter is geïntroduceerd in Power shell 6,2.

Bijvoorbeeld:

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a>-EncodedCommand | -e | -EG

Hiermee wordt een met base64 gecodeerde teken reeks versie van een opdracht geaccepteerd. Gebruik deze para meter voor het verzenden van opdrachten naar Power shell waarvoor complexe, geneste aanhalings tekens zijn vereist. De base64-weer gave moet een UTF-16-gecodeerde teken reeks zijn.

Bijvoorbeeld:

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a>-ExecutionPolicy | -ex | -EP

Hiermee stelt u het standaard uitvoerings beleid voor de huidige sessie en slaat u deze op in de `$env:PSExecutionPolicyPreference` omgevings variabele. Met deze para meter wordt het permanent geconfigureerde uitvoerings beleid niet gewijzigd.

Deze para meter is alleen van toepassing op Windows-computers. De `$env:PSExecutionPolicyPreference` omgevings variabele bestaat niet op niet-Windows-platforms.

### <a name="-inputformat---inp---if"></a>-InputFormat | -INP | -Als

Beschrijft de indeling van gegevens die naar Power shell worden verzonden. Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).

### <a name="-interactive---i"></a>-Interactief | -i

Presenteer een interactieve prompt aan de gebruiker. Inverse voor niet-interactieve para meter.

### <a name="-login---l"></a>-Aanmelden | -l

In Linux en macOS wordt Power shell gestart als een aanmeldings shell, met behulp van/bin/sh om aanmeldings profielen, zoals/etc/profile en ~/.profile., uit te voeren.
In Windows heeft deze switch niets.

> [!IMPORTANT]
> Deze para meter moet eerst worden gestart om Power shell als een aanmeldings shell te starten.
> Als deze para meter op een andere positie wordt door gegeven, wordt dit genegeerd.

Instellen `pwsh` als de aanmeldings shell op UNIX-achtige besturings systemen:

- Controleer of het volledige absolute pad naar `pwsh` wordt vermeld onder `/etc/shells`
  - Dit pad is doorgaans iets zoals `/usr/bin/pwsh` in Linux of `/usr/local/bin/pwsh` op macOS
  - Bij sommige installatie methoden wordt deze vermelding tijdens de installatie automatisch toegevoegd
  - Als `pwsh` niet aanwezig is in `/etc/shells` , gebruikt u een editor om het pad toe te voegen aan `pwsh` op de laatste regel. Hiervoor zijn verhoogde bevoegdheden vereist om te bewerken.
- Gebruik het hulp programma [chsh](https://linux.die.net/man/1/chsh) om de shell van uw huidige gebruiker in te stellen op `pwsh` :

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> `pwsh`Het instellen van de aanmeldings shell wordt momenteel niet ondersteund op het Windows-subsysteem voor Linux (WSL), en het instellen van `pwsh` de aanmeldings shell kan ertoe leiden dat WSL niet interactief kan worden gestart.

### <a name="-mta"></a>-MTA

Start Power shell met een Apartment met meerdere threads. Deze schakel optie is alleen beschikbaar in Windows.

### <a name="-noexit---noe"></a>-Niet afsluiten | -noe

Wordt niet afgesloten na het uitvoeren van opstart opdrachten.

Voorbeeld: `pwsh -NoExit -Command Get-Date`

### <a name="-nologo---nol"></a>-Logo | -nol

Hiermee verbergt u het copyright banner bij het opstarten van interactieve sessies.

### <a name="-noninteractive---noni"></a>-Niet-interactief | -noni

Er wordt geen interactieve prompt voor de gebruiker weer gegeven. Alle pogingen om interactieve functies, zoals `Read-Host` of bevestigings prompts, te gebruiken, resulteren in instructie-Terminate-fouten.

### <a name="-noprofile---nop"></a>-Profile | -NOP

Laadt de Power shell-profielen niet.

### <a name="-outputformat---o---of"></a>-Output Format | -o | -van

Hiermee wordt bepaald hoe de uitvoer van Power shell wordt opgemaakt. Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).

Voorbeeld: `pwsh -o XML -c Get-Date`

Wanneer u een Power shell-sessie aanroept, haalt u objecten op die zijn gedeserialiseerd als uitvoer in plaats van gewone teken reeksen. Bij het aanroepen van andere shells is de uitvoer teken reeks gegevens die zijn opgemaakt als CLIXML-tekst.

### <a name="-settingsfile---settings"></a>-SettingsFile | -instellingen

Onderdrukt het `powershell.config.json` instellingen bestand voor het hele systeem voor de sessie. Standaard worden de instellingen voor het hele systeem gelezen van de `powershell.config.json` in de `$PSHOME` map.

Houd er rekening mee dat deze instellingen niet worden gebruikt door het eind punt dat is opgegeven door het `-ConfigurationName` argument.

Voorbeeld: `pwsh -SettingsFile c:\myproject\powershell.config.json`

### <a name="-sshservermode---sshs"></a>-SSHServerMode | -sshs

Wordt gebruikt in sshd_config voor het uitvoeren van Power shell als een SSH-subsysteem. Het is niet bedoeld of wordt niet ondersteund voor andere gebruik.

### <a name="-sta"></a>-STA

Start Power shell met een Apartment met één thread. Dit is de standaardinstelling. Deze schakel optie is alleen beschikbaar in Windows.

### <a name="-version---v"></a>-Versie | -v

Hiermee wordt de versie van Power shell weer gegeven. Aanvullende para meters worden genegeerd.

### <a name="-windowstyle---w"></a>-WindowStyle | -w

Hiermee stelt u de venster stijl voor de sessie. Geldige waarden zijn normaal, geminimaliseerd, gemaximaliseerd en verborgen.

### <a name="-workingdirectory---wd"></a>-Variabele workingdirectory | -WD

Hiermee stelt u de oorspronkelijke werkmap in door tijdens het opstarten uit te voeren. Een geldig pad naar een Power shell-bestand wordt ondersteund.

Als u Power shell in uw basismap wilt starten, gebruikt u: `pwsh -WorkingDirectory ~`

### <a name="-help---"></a>-Help,-?,/?

Geeft Help weer voor `pwsh` . Als u een pwsh-opdracht in Power shell typt, laten voorafgaan door u de opdracht parameters met een koppel teken ( `-` ), niet een slash ( `/` ).
