---
ms.date: 08/14/2018
keywords: PowerShell-cmdlet
title: Help voor de PowerShell.exe-opdrachtregel
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688824"
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe Help voor de opdrachtregel

U kunt het gebruiken van PowerShell.exe een PowerShell-sessie starten vanaf de opdrachtregel van een ander hulpprogramma, zoals Cmd.exe of op de PowerShell-opdrachtregel gebruiken om een nieuwe sessie te starten. Gebruik de parameters voor het aanpassen van de sessie.

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

Accepteert een base 64 gecodeerde tekenreeks-versie van een opdracht. Gebruik deze parameter om te verzenden naar PowerShell-opdrachten die complexe tussen aanhalingstekens worden gezet of accolades vereist.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

Hiermee stelt u het standaardbeleid voor uitvoering voor de huidige sessie en opgeslagen in de $env: PSExecutionPolicyPreference-omgevingsvariabele. Deze parameter wijzigen niet van de PowerShell-uitvoeringsbeleid is ingesteld in het register. Zie voor meer informatie over de uitvoeringsbeleidsregels PowerShell, waaronder een lijst met geldige waarden [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

### <a name="-file-filepath-parameters"></a>-Bestand <FilePath> \[ <Parameters>]

Voert het opgegeven script in het lokale bereik ('dot-Source'), zodat de functies en variabelen die het script wordt gemaakt, beschikbaar in de huidige sessie zijn. Geef het pad naar het script en eventueel parameters. **Bestand** moet de laatste parameter in de opdracht. Alle waarden zijn ingevoerd na de **-bestand** parameter wordt geïnterpreteerd als het script logbestandspad en -parameters doorgegeven aan het script.

Parameters doorgegeven aan het script worden doorgegeven als letterlijke tekenreeksen, na de interpretatie van de huidige shell. Bijvoorbeeld, als u zich in cmd.exe en wilt een omgevingsvariabele doorgeven, zou u de syntaxis cmd.exe gebruiken: `powershell.exe -File .\test.ps1 -TestParam %windir%`

Daarentegen uitgevoerd `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe resultaten in het script ontvangen van de letterlijke tekenreeks `$env:windir` omdat er geen speciale betekenis voor de huidige cmd.exe-shell.
De `$env:windir` stijl van de variabele omgevingsverwijzing _kunt_ worden gebruikt binnen een `-Command` parameter, omdat er deze wordt geïnterpreteerd als PowerShell-code.

### <a name="-inputformat-text--xml"></a>\-InputFormat {tekst | XML}

Hierin wordt beschreven in de indeling van gegevens die worden verzonden naar PowerShell. Geldige waarden zijn 'Tekst' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).

### <a name="-mta"></a>-Mta

Start PowerShell met behulp van een apartment meerdere threads. Deze parameter is opgenomen in PowerShell 3.0. Single-threaded apartment (STA) is PowerShell 3.0, de standaardinstelling. In PowerShell 2.0 is dankzij de multi-threaded apartment (MTA) de standaardinstelling.

### <a name="-noexit"></a>-NoExit

Na het uitvoeren van opstartopdrachten afsluiten niet.

### <a name="-nologo"></a>-NoLogo

Hiermee verbergt u de copyright banner bij het opstarten.

### <a name="-noninteractive"></a>-NonInteractive

Niet aanwezig zijn van een interactieve prompt voor de gebruiker.

### <a name="-noprofile"></a>-NoProfile

Het PowerShell-profiel niet worden geladen.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

Bepaalt hoe de uitvoer van PowerShell wordt opgemaakt. Geldige waarden zijn 'Tekst' (tekenreeksen) of 'XML' (geserialiseerde CLIXML-indeling).

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

Laadt het opgegeven bestand van de PowerShell-console. Geef het pad en de naam van de consolebestand. Gebruik voor het maken van een consolebestand de [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.

### <a name="-sta"></a>-Sta

Start PowerShell met behulp van een single-threaded apartment. Single-threaded apartment (STA) is PowerShell 3.0, de standaardinstelling. In PowerShell 2.0 is dankzij de multi-threaded apartment (MTA) de standaardinstelling.

### <a name="-version-powershell-version"></a>-Versie <PowerShell Version>

Hiermee start u de opgegeven versie van PowerShell. De versie die u opgeeft moet worden geïnstalleerd op het systeem. Als u PowerShell 3.0 op de computer is geïnstalleerd, wordt de geldige waarden zijn "2.0" en '3.0'. De standaardwaarde is '3.0'.

Als PowerShell 3.0 niet is geïnstalleerd, is de enige geldige waarde '2.0'. Andere waarden worden genegeerd.

Zie voor meer informatie, [Windows PowerShell installeren](../../setup/installing-windows-powershell.md).

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

Hiermee stelt u de vensterstijl voor de sessie. Geldige waarden zijn normaal, geminimaliseerd, gemaximaliseerd en verborgen.

### <a name="-command"></a>-Opdracht

Hiermee voert u de opgegeven opdrachten (met parameters) alsof ze zijn getypt achter de PowerShell-opdrachtprompt.
Na de uitvoering, PowerShell wordt afgesloten, tenzij de **NoExit** parameter is opgegeven.
Alle tekst na `-Command` als een enkele opdrachtregel wordt verzonden naar PowerShell.
Dit wijkt af van hoe u `-File` parameters die worden verzonden naar een script worden verwerkt.

De waarde van `-Command` kan '-', een tekenreeks of een scriptblok.
De resultaten van de opdracht keert terug naar de bovenliggende shell als gedeserialiseerde XML-objecten die niet live objecten.

Als de waarde van `-Command` is '-', de opdrachttekst worden gelezen uit de standaard invoer.

Wanneer de waarde van `-Command` is een tekenreeks, **opdracht** _moet_ worden de laatste parameter zijn opgegeven, omdat alle tekens hebt getypt nadat de opdracht als de opdrachtargumenten worden geïnterpreteerd.

De **opdracht** parameter accepteert alleen een scriptblok voor uitvoering op wanneer de waarde die is doorgegeven aan kan worden herkend `-Command` als ScriptBlock-type.
Dit is _alleen_ mogelijk bij het uitvoeren van PowerShell.exe uit een andere PowerShell-host.
Het type kan zich bevinden in een bestaande variabele, geretourneerd door een expressie of geparseerd door de PowerShell ScriptBlock hosten als een letterlijke scriptblok tussen accolades `{}`voordat wordt doorgegeven aan PowerShell.exe.

In cmd.exe, er is niet goed als een scriptblok (of ScriptBlock type), zodat de waarde die is doorgegeven aan **opdracht** wordt _altijd_ een tekenreeks zijn.
U kunt een scriptblok binnen de tekenreeks schrijven, maar in plaats van wordt uitgevoerd het gedragen precies alsof u de gegevens hebt ingevoerd bij een typische PowerShell-prompt, de inhoud van het script afdrukken blokkeren weer uit voor u.

Een tekenreeks doorgegeven aan `-Command` nog steeds worden uitgevoerd als PowerShell, zodat het script blok tussen accolades vaak niet vereist in de eerste plaats zijn bij het uitvoeren van cmd.exe.
Voor het uitvoeren van een inline-scriptblok zoals gedefinieerd in een tekenreeks, de [aanroep-operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` kan worden gebruikt:

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help-,?, /?

Ziet u de syntaxis van de powershell.exe. Als u een opdracht PowerShell.exe in PowerShell, voegt u vóór de opdrachtparameters met een afbreekstreepje (-), niet een slash (/). U kunt een afbreekstreepje of een schuine streep in Cmd.exe.

> [!NOTE]
> Opmerking voor probleemoplossing: In PowerShell 2.0, door sommige programma's in de Windows PowerShell console niet te beginnen met een LastExitCode van 0xc0000142.

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
