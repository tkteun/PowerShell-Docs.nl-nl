---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Help voor de PowerShell.exe-opdrachtregel
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="powershellexe-command-line-help"></a>Help voor de opdrachtregel PowerShell.exe

U kunt PowerShell.exe gebruiken een PowerShell-sessie starten vanaf de opdrachtregel van een ander hulpprogramma, zoals Cmd.exe of op de PowerShell-opdrachtregel gebruiken om een nieuwe sessie te starten. Gebruik de parameters voor het aanpassen van de sessie.

## <a name="syntax"></a>Syntaxis

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>Parameters

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

Een base 64 gecodeerde tekenreeksversie van een opdracht accepteert. Gebruik deze parameter om opdrachten naar PowerShell waarvoor complexe aanhalingstekens of accolades verzenden.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Hiermee stelt u het standaarduitvoeringsbeleid voor de huidige sessie en opgeslagen in de $env: PSExecutionPolicyPreference-omgevingsvariabele. Deze parameter wordt de PowerShell-uitvoeringsbeleid dat is ingesteld in het register niet gewijzigd. Zie voor informatie over de uitvoeringsbeleidsregels PowerShell, waaronder een lijst met geldige waarden [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Bestand <FilePath> \[ <Parameters>]

Voert het opgegeven script in het lokale bereik ('dot-afkomstig'), zodat de functies en variabelen die het script maakt beschikbaar in de huidige sessie zijn. Geef het pad naar het script en parameters. **Bestand** moet de laatste parameter in de opdracht, omdat alle tekens worden ingevoerd na de **bestand** parameternaam worden geïnterpreteerd als het script bestandspad gevolgd door de scriptparameters en hun waarden.

U kunt de parameters van een script en parameterwaarden, opnemen in de waarde van de **bestand** parameter. Bijvoorbeeld: `-File .\Get-Script.ps1 -Domain Central` opmerking die parameters doorgegeven aan het script worden doorgegeven als letterlijke tekenreeksen (na interpretatie door de huidige shell).
Bijvoorbeeld, als u in cmd.exe en wilt doorgeven van een omgevingsvariabele, gebruikt u de syntaxis van de cmd.exe: `powershell -File .\test.ps1 -Sample %windir%` als u zou gebruiken van PowerShell-syntaxis, wordt in dit voorbeeld uw script de letterlijke waarde ontvangt ' $env: windir ' en niet de waarde van die omgevingsvariabele: `powershell -File .\test.ps1 -Sample $env:windir`

Normaal gesproken worden de switch-parameters van een script opgenomen of weggelaten. Bijvoorbeeld de volgende opdracht maakt gebruik van de **alle** parameter van het scriptbestand Get-Script.ps1: `-File .\Get-Script.ps1 -All`

### <a name="-inputformat-text--xml"></a>\-InputFormat {tekst | XML}

Beschrijft de indeling van gegevens die worden verzonden naar PowerShell. Geldige waarden zijn 'Text' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).

### <a name="-mta"></a>-Mta

Start PowerShell met een apartment met meerdere threads. Deze parameter is geïntroduceerd in PowerShell 3.0. PowerShell 3.0 is single thread apartment (STA) de standaardinstelling. In PowerShell 2.0 is met meerdere threads MTA (apartment) de standaardinstelling.

### <a name="-noexit"></a>-NoExit

Bestaat niet na het starten van de opdrachten uit te voeren.

### <a name="-nologo"></a>-NoLogo

Hiermee verbergt het vaandel met copyright bij het opstarten.

### <a name="-noninteractive"></a>-NonInteractive

Biedt een interactieve prompt niet aanwezig voor de gebruiker.

### <a name="-noprofile"></a>-NoProfile

Het PowerShell-profiel niet geladen.

### <a name="-outputformat-text--xml"></a>-OutputFormat {tekst | XML}

Hiermee wordt bepaald hoe de uitvoer van PowerShell is geformatteerd. Geldige waarden zijn 'Text' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Laadt het opgegeven bestand van de PowerShell-console. Geef het pad en de naam van het consolebestand. Gebruik voor het maken van een consolebestand de [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.

### <a name="-sta"></a>-Sta

Start PowerShell met een apartment met één thread bevindt. PowerShell 3.0 is single thread apartment (STA) de standaardinstelling. In PowerShell 2.0 is met meerdere threads MTA (apartment) de standaardinstelling.

### <a name="-version-powershell-version"></a>-Versie <PowerShell Version>

Hiermee start u de opgegeven versie van PowerShell. De versie die u opgeeft moet worden geïnstalleerd op het systeem. Als PowerShell 3.0 is geïnstalleerd op de computer, wordt de geldige waarden zijn '2.0' en '3.0'. De standaardwaarde is '3.0'.

Als PowerShell 3.0 niet is geïnstalleerd, is de enige geldige waarde '2.0'. Andere waarden worden genegeerd.

Zie voor meer informatie '[Windows PowerShell installeren](../../setup/installing-windows-powershell.md)'.

### <a name="-windowstyle-window-style"></a>-Vensterstijl <Window style>

Hiermee stelt de vensterstijl voor de sessie. Geldige waarden zijn standaard, geminimaliseerd, gemaximaliseerd en verborgen.

### <a name="-command"></a>-Opdracht

Voert de opgegeven opdrachten (en eventuele parameters) alsof ze zijn getypt achter de PowerShell-opdrachtprompt en vervolgens wordt afgesloten, tenzij de parameter NoExit is opgegeven.
In wezen elke tekst na `-Command` wordt verzonden als een enkele opdrachtregel naar PowerShell (dit verschilt van het `-File` omgaat met parameters die worden verzonden naar een script).

De waarde van de opdracht kan niet '-', een tekenreeks. of een scriptblok is opgegeven. Als de waarde van de opdracht '-', de opdrachttekst is gelezen uit standaard invoer.

Scriptblokken moeten tussen accolades ({}) worden geplaatst. U kunt een scriptblok opgeven, alleen wanneer PowerShell.exe uitgevoerd in PowerShell. De resultaten van het script worden geretourneerd aan de bovenliggende shell als gedeserialiseerde XML-objecten die niet live objecten.

Als de waarde van de opdracht een tekenreeks is, **opdracht** moet de laatste parameter in de opdracht, omdat alle tekens worden ingevoerd nadat de opdracht als de opdrachtargumenten worden geïnterpreteerd.

Gebruik de notatie voor het schrijven van een tekenreeks die wordt uitgevoerd een PowerShell-opdracht:

```powershell
"& {<command>}"
```

waar de aanhalingstekens geven een tekenreeks en de operator invoke (&) zorgt ervoor dat de opdracht om te worden uitgevoerd.

### <a name="-help---"></a>-Help, -?, /?

Dit bericht bevat. Als u een opdracht PowerShell.exe in PowerShell typt, voeg de opdrachtparameters met een afbreekstreepje (-), niet een slash (/). U kunt een koppelteken of een slash in Cmd.exe.

> [!NOTE]
> Opmerking voor probleemoplossing: In PowerShell 2.0 beginnen enkele programma's in de Windows PowerShell console is mislukt met een LastExitCode van 0xc0000142.

## <a name="examples"></a>VOORBEELDEN

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