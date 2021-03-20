---
description: Hierin wordt uitgelegd hoe u de `powershell.exe` opdracht regel interface gebruikt. Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: 4025630ebb3abe4c0598c85940cfce383e9c7890
ms.sourcegitcommit: 16a02ae47d1a85b01692101aa0aa6e91e1ba398e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104726652"
---
# <a name="about-powershellexe"></a>Over PowerShell.exe

## <a name="short-description"></a>Korte beschrijving
Hierin wordt uitgelegd hoe u de `powershell.exe` opdracht regel interface gebruikt. Hiermee worden de opdracht regel parameters weer gegeven en wordt de syntaxis beschreven.

## <a name="long-description"></a>Lange beschrijving

### <a name="syntax"></a>SYNTAXIS

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a>Parameters

#### <a name="-psconsolefile-filepath"></a>-PSConsoleFile \<FilePath\>

Hiermee wordt het opgegeven Power shell-console bestand geladen. Voer het pad en de naam van het console bestand in. Gebruik de cmdlet Export-Console in Power shell om een console bestand te maken.

#### <a name="-version-powershell-version"></a>-Versie \<PowerShell Version\>

Hiermee wordt de opgegeven versie van Power shell gestart. Geldige waarden zijn 2,0 en 3,0. De versie die u opgeeft, moet op het systeem zijn geïnstalleerd. Als Windows Power Shell 3,0 is geïnstalleerd op de computer, is "3,0" de standaard versie.
Anders is ' 2,0 ' de standaard versie. Zie [Power Shell installeren](/powershell/scripting/install/installing-windows-powershell)voor meer informatie.

#### <a name="-nologo"></a>-Logo

Hiermee verbergt u het copyright banner bij het opstarten.

#### <a name="-noexit"></a>-Outexit

Wordt niet afgesloten na het uitvoeren van opstart opdrachten.

#### <a name="-sta"></a>-Sta

Power shell wordt gestart met een Apartment met één thread. In Windows Power Shell 2,0 is multi-threaded apartment (MTA) de standaard waarde. In Windows Power Shell 3,0 is single-threaded apartment (STA) de standaard waarde.

#### <a name="-mta"></a>-MTA

Power shell wordt gestart met een Apartment met meerdere threads. Deze para meter wordt geïntroduceerd in Power Shell 3,0. In Power Shell 2,0 is multi-threaded apartment (MTA) de standaard waarde. In Power Shell 3,0 is single-threaded apartment (STA) de standaard waarde.

#### <a name="-noprofile"></a>-Geen profiel

Laadt het Power shell-profiel niet.

#### <a name="-noninteractive"></a>-Niet-interactief

Er wordt geen interactieve prompt voor de gebruiker weer gegeven.

#### <a name="-inputformat-text--xml"></a>-InputFormat {text | INDELING

Beschrijft de indeling van gegevens die naar Power shell worden verzonden. Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).

#### <a name="-outputformat-text--xml"></a>-Output Format {Text | INDELING

Hiermee wordt bepaald hoe de uitvoer van Power shell wordt opgemaakt. Geldige waarden zijn ' text ' (tekst reeksen) of ' XML ' (geserialiseerde CLIXML-indeling).

#### <a name="-windowstyle-window-style"></a>-WindowStyle \<Window style\>

Hiermee stelt u de venster stijl voor de sessie. Geldige waarden zijn normaal, geminimaliseerd, gemaximaliseerd en verborgen.

#### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand \<Base64EncodedCommand\>

Hiermee wordt een teken reeks versie met basis-64-code ring geaccepteerd van een opdracht. Gebruik deze para meter om opdrachten naar Power shell te verzenden waarvoor complexe aanhalings tekens of accolades zijn vereist. De teken reeks moet worden opgemaakt met de UTF-16LE-teken codering.

#### <a name="-configurationname-string"></a>-Configuratiepad \<string\>

Hiermee geeft u een configuratie-eind punt waarin Power shell wordt uitgevoerd. Dit kan elk eind punt zijn dat is geregistreerd op de lokale computer, met inbegrip van de standaard externe communicatie-eind punten in Power shell of een aangepast eind punt met specifieke mogelijkheden voor de gebruikersrol.

#### <a name="-file----filepath-args"></a>-Bestand-| \<filePath\>\<args\>

Als de waarde van het **bestand** is, wordt de opdracht tekst gelezen uit de standaard invoer.
Als u `powershell -File -` zonder omgeleide standaard invoer uitvoert, wordt een reguliere sessie gestart. Dit is hetzelfde als de **Bestands** parameter helemaal niet opgeven.

Als de waarde van het **bestand** een bestandspad is, wordt het script uitgevoerd in het lokale bereik (' dot-brond '), zodat de functies en variabelen die het script maakt, beschikbaar zijn in de huidige sessie. Voer het pad naar het script bestand en eventuele para meters in. Het **bestand** moet de laatste para meter in de opdracht zijn. Alle waarden die na de **Bestands** parameter worden getypt, worden geïnterpreteerd als het pad naar het script bestand en de para meters die aan het script worden door gegeven.

Para meters die aan het script worden door gegeven, worden als letterlijke teken reeksen door gegeven na de interpretatie van de huidige shell. Als u bijvoorbeeld in **cmd.exe** bent en u een omgevings variabele waarde wilt door geven, gebruikt u de **cmd.exe** syntaxis: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Als u daarentegen `powershell.exe -File .\test.ps1 -TestParam $env:windir` in **cmd.exe** resulteert, wordt de letterlijke teken reeks door het script ontvangen `$env:windir` omdat het geen speciale betekenis heeft voor de huidige **cmd.exe** shell. De `$env:windir` stijl van de verwijzing naar een omgevings variabele _kan_ worden gebruikt binnen een **opdracht** parameter, omdat deze wordt geïnterpreteerd als Power shell-code.

Als u dezelfde opdracht uit een **batch script** wilt uitvoeren, gebruikt u `%~dp0` in plaats van `.\` of `$PSScriptRoot` om de huidige uitvoerings Directory te vertegenwoordigen: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .
Als u in plaats daarvan gebruikt `.\test.ps1` , genereert Power shell een fout omdat het letterlijke pad niet kan worden gevonden `.\test.ps1`

Wanneer de **waarde van het bestand een** bestandspad is,  _moet_ het bestand de laatste para meter zijn in de opdracht omdat de tekens die na de naam van de **Bestands** parameter worden getypt, worden geïnterpreteerd als het pad naar het script bestand gevolgd door de script parameters.

U kunt de script parameters en waarden in de waarde van de **Bestands** parameter toevoegen. Bijvoorbeeld: `-File .\Get-Script.ps1 -Domain Central`

Normaal gesp roken worden de switch parameters van een script opgenomen of wegge laten.
Met de volgende opdracht wordt bijvoorbeeld de para meter **all** van het `Get-Script.ps1` script bestand gebruikt: `-File .\Get-Script.ps1 -All`

In zeldzame gevallen moet u mogelijk een **Booleaanse** waarde voor een para meter opgeven.
Het is niet mogelijk om een expliciete Booleaanse waarde door te geven voor een switch parameter wanneer u een script op deze manier uitvoert. Deze beperking is verwijderd in Power shell 6 ( `pwsh.exe` ).

#### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy \<ExecutionPolicy\>

Hiermee stelt u het standaard uitvoerings beleid voor de huidige sessie en slaat u deze op in de `$env:PSExecutionPolicyPreference` omgevings variabele. Met deze para meter wordt het Power shell-uitvoerings beleid dat in het REGI ster is ingesteld, niet gewijzigd. Zie [about_Execution_Policies](about_Execution_Policies.md)voor meer informatie over het uitvoeren van Power shell-uitvoerings beleid, met inbegrip van een lijst met geldige waarden.

#### <a name="-command"></a>-Opdracht

Hiermee worden de opgegeven opdrachten (en eventuele para meters) uitgevoerd alsof ze zijn getypt bij de Power shell-opdracht prompt en vervolgens afgesloten, tenzij de `NoExit` para meter is opgegeven.

De waarde van de **opdracht** kan `-` een script blok of een teken reeks zijn. Als de waarde van de **opdracht** is `-` , wordt de opdracht tekst gelezen uit de standaard invoer.

De **opdracht** parameter accepteert alleen een script blok voor uitvoering wanneer het de **waarde die wordt door gegeven, kan** herkennen als een **script Block** -type. Dit kan _alleen_ worden uitgevoerd `powershell.exe` vanuit een andere Power shell-host. Het type **script Block** kan worden opgenomen in een bestaande variabele, geretourneerd vanuit een expressie, of door de Power shell-host geparseerd als een letterlijk script blok tussen accolades ( `{}` ) voordat het wordt door gegeven aan `powershell.exe` .

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

In `cmd.exe` is er geen script blok (of **script Block** -type), dus de waarde die is door gegeven aan de **opdracht** , is _altijd_ een teken reeks. U kunt een script blok schrijven in de teken reeks, maar in plaats van dat het wordt uitgevoerd, werkt het niet exact alsof u het hebt getypt bij een typische Power shell-prompt, waarbij de inhoud van het script blok wordt weer gegeven.

Een teken reeks die aan de **opdracht** is door gegeven, wordt nog steeds uitgevoerd als Power shell-code, dus de accolades voor het blok keren van een script zijn in de eerste plaats vaak niet vereist tijdens de uitvoering van `cmd.exe` . Voor het uitvoeren van een inline-script blok dat in een teken reeks is gedefinieerd, kan de [aanroep operator](about_operators.md#special-operators) `&` worden gebruikt:

```cmd
powershell.exe -Command "& {Get-WinEvent -LogName security}"
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

#### <a name="-help---"></a>-Help,-?,/?

Geeft Help weer voor **PowerShell.exe**. Als u een **PowerShell.exe** -opdracht in een Power shell-sessie typt, laten voorafgaan door u de opdracht parameters met een koppel teken (-), niet een slash (/). U kunt een koppel teken of slash gebruiken in **cmd.exe**.

### <a name="remarks"></a>OPMERKINGEN

Problemen met de probleem oplossing: in Power Shell 2,0 kunnen sommige Program ma's van de Power shell-console niet worden gestart met een **LastExitCode** van 0xc0000142.

### <a name="examples"></a>VOORBEELDEN

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
