---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEOptions-object
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686262"
---
# <a name="the-iseoptions-object"></a>Het ISEOptions-object

De **ISEOptions** object vertegenwoordigt diverse instellingen voor Windows PowerShell ISE. Het is een exemplaar van de **Microsoft.PowerShell.Host.ISE.ISEOptions** klasse.

De **ISEOptions** object biedt de volgende eigenschappen en methoden.

## <a name="methods"></a>Methoden

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee herstelt u de standaardwaarden van de token kleuren in het consolevenster.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee herstelt u de standaardwaarden van alle instellingen in het consolevenster. Het stelt ook het gedrag van verschillende waarschuwingsberichten waarmee u het selectievakje standaard om te voorkomen dat het bericht opnieuw wordt weergegeven.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee herstelt u de standaardwaarden van de token kleuren in het scriptvenster.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee herstelt u de standaardwaarden van de token kleuren voor XML-elementen die worden weergegeven in Windows PowerShell ISE. Zie ook [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Eigenschappen

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u het aantal minuten tussen bewerkingen automatisch opslaan van uw bestanden in Windows PowerShell ISE. De standaardwaarde is 2 minuten. De waarde is een geheel getal zijn.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Hiermee geeft u de achtergrondkleur voor het opdrachtvenster. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.

Hiermee geeft u op of het deelvenster van de opdracht bevindt zich boven het deelvenster Uitvoer.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u de achtergrondkleur van het consolevenster. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u de voorgrondkleur van de tekst in het consolevenster.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u de achtergrondkleur van de tekst in het consolevenster.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Console. Deze eigenschap is een dictionary-object met de naam/waarde-paren van de typen tokens en kleuren voor het consolevenster. Zie het wijzigen van de kleuren van de tokens IntelliSense in het scriptvenster [TokenColors](#tokencolors). Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Token kleuren kunnen worden ingesteld voor het volgende: Kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, nieuwe regel, getal, Operator, positie, StatementSeparator, String, Type, onbekend, variabele.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de achtergrondkleur voor de foutopsporing tekst die wordt weergegeven in het consolevenster. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de voorgrondkleur aan voor de foutopsporing tekst die wordt weergegeven in het consolevenster. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Een verzameling eigenschappen die de standaardwaarden worden gebruikt wanneer het opnieuw instellen-methoden worden gebruikt.

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de achtergrondkleur voor de tekst van de fout die wordt weergegeven in het consolevenster. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de voorgrondkleur aan voor de tekst van de fout die wordt weergegeven in het consolevenster. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de naam van het lettertype in momenteel wordt gebruikt in het scriptvenster en het consolevenster.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de tekengrootte als een geheel getal zijn. Het wordt gebruikt in het scriptvenster, het opdrachtvenster en het deelvenster Uitvoer. Het geldige waardenbereik is 8 tot en met 32.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u het aantal seconden dat IntelliSense wordt gebruikt om op te lossen van de momenteel getypte tekst. Na dit aantal seconden, IntelliSense een time-out optreedt en kunt u verder kunt typen. De standaardwaarde is 3 seconden. De waarde is een geheel getal zijn.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u het aantal onlangs geopende bestanden met Windows PowerShell ISE worden bijgehouden en worden weergegeven aan de onderkant van de **bestand openen** menu. De standaardwaarde is 10. De waarde is een geheel getal zijn.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

De lezen/schrijven-eigenschap die opgehaald of ingesteld van de achtergrondkleur van het deelvenster Uitvoer zelf. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

De lezen/schrijven-eigenschap die de voorgrondkleur van de tekst in het deelvenster Uitvoer in Windows PowerShell ISE 2.0 wordt gewijzigd.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

De lezen/schrijven-eigenschap die de achtergrondkleur van de tekst in het deelvenster Uitvoer wordt gewijzigd.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De lezen/schrijven-eigenschap die opgehaald of ingesteld van de achtergrondkleur voor bestanden. Het is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De lezen/schrijven-eigenschap die opgehaald of ingesteld van de voorgrondkleur voor niet-scriptbestanden in het scriptvenster.
Als u wilt de voorgrondkleur voor scriptbestanden, gebruikt de [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De lezen/schrijven-eigenschap die opgehaald of ingesteld van de positie van het scriptvenster op het scherm. De tekenreeks mag 'Gemaximaliseerd', 'Top' of 'Chterkant'.

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of de **CTRL + J** lijst met fragmenten bevat de set met starter die is opgenomen in Windows PowerShell. Als de waarde **$false**, alleen door de gebruiker gedefinieerde fragmenten worden weergegeven in de **CTRL + J** lijst. De standaardwaarde is **$true**.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of IntelliSense syntaxis van de parameter en waarde suggesties in het consolevenster biedt. De standaardwaarde is **$true**.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of IntelliSense syntaxis van de parameter en waarde suggesties in het scriptvenster biedt. De standaardwaarde is **$true**.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of het scriptvenster regelnummers in de linkermarge weergeeft. De standaardwaarde is **$true**.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of het scriptvenster worden uitgevouwen en samengevouwen tussen haakjes naast de gedeelten van de code in de linkermarge weergegeven. Wanneer ze worden weergegeven, kunt u het minteken \( - \) pictogrammen naast een blok tekst wilt samenvouwen of klik op het plusteken \( + \) pictogram om uit te breiden van een blok tekst. De standaardwaarde is **$true**.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u op of de ISE-werkbalk aan de bovenkant van de Windows PowerShell ISE-venster wordt weergegeven. De standaardwaarde is **$true**.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u op of er een waarschuwingsbericht wordt weergegeven wanneer een script automatisch opgeslagen wordt voordat deze wordt uitgevoerd. De standaardwaarde is **$true**.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u op of een waarschuwing wordt weergegeven als hetzelfde bestand wordt geopend in de verschillende tabbladen van PowerShell. Indien ingesteld op **$true**, hetzelfde bestand openen in meerdere tabbladen toont dit bericht: "Een kopie van dit bestand is geopend in een andere Windows PowerShell-tabblad. Wijzigingen in dit bestand heeft invloed op alle geopende exemplaren." De standaardwaarde is **$true**.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Script. Deze eigenschap is een dictionary-object met de naam/waarde-paren van de typen tokens en kleuren voor het scriptvenster. Zie het wijzigen van de kleuren van de tokens IntelliSense in het consolevenster [ConsoleTokenColors](#consoletokencolors). Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultTokenColors](#restoredefaulttokencolors). Token kleuren kunnen worden ingesteld voor het volgende: Kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, nieuwe regel, getal, Operator, positie, StatementSeparator, String, Type, onbekend, variabele.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of u de Enter-toets gebruiken kunt om te selecteren van een opgegeven optie in het consolevenster IntelliSense. De standaardwaarde is **$true**.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of u de Enter-toets gebruiken kunt om een IntelliSense-opgegeven optie in het scriptvenster. De standaardwaarde is **$true**.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u op of de lokaal geïnstalleerde Help of de online Help van TechNet-bibliotheek wordt weergegeven wanneer u de cursor in een trefwoord op F1 drukt. Indien ingesteld op **$true**, en vervolgens een pop-upvenster uit de lokaal geïnstalleerde Help-inhoud bevat. U kunt de Help-bestanden installeren door het uitvoeren van de `Update-Help` opdracht. Indien ingesteld op **$false**, en vervolgens uw browser wordt geopend op een pagina in de TechNet-bibliotheek.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de achtergrondkleur voor uitgebreide tekst die wordt weergegeven in het consolevenster. Het is een **System.Windows.Media.Color** object.

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de voorgrondkleur voor uitgebreide tekst die wordt weergegeven in het consolevenster. Het is een **System.Windows.Media.Color** object.

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de achtergrondkleur voor waarschuwingstekst die wordt weergegeven in het consolevenster. Het is een **System.Windows.Media.Color** object.

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de voorgrondkleur voor waarschuwingstekst die wordt weergegeven in het deelvenster Uitvoer. Het is een **System.Windows.Media.Color** object.

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u een dictionary-object met de naam/waarde-paren van de typen tokens en kleuren voor XML-inhoud die wordt weergegeven in Windows PowerShell ISE. Token kleuren kunnen worden ingesteld voor het volgende: Kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, nieuwe regel, getal, Operator, positie, StatementSeparator, String, Type, onbekend, variabele. Zie ook [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Uitzoomen

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Hiermee geeft u de relatieve grootte van de tekst in de Console en het Script deelvensters. De standaardwaarde is 100. Lagere waarden ertoe leiden dat de tekst in Windows PowerShell ISE kleinere weergegeven terwijl groot ertoe leiden dat de tekst groter worden weergegeven. De waarde is een geheel getal met een bereik van 20 tot 400.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Zie ook

- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)