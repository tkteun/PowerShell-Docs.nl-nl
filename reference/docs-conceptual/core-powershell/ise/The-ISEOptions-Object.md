---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEOptions-object
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953647"
---
# <a name="the-iseoptions-object"></a>Het ISEOptions-object

De **ISEOptions** object vertegenwoordigt diverse instellingen voor Windows PowerShell ISE. Er is een exemplaar van de **Microsoft.PowerShell.Host.ISE.ISEOptions** klasse.

De **ISEOptions** -object biedt de volgende eigenschappen en methoden.

## <a name="methods"></a>Methoden

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee herstelt u de standaardwaarden van de token kleuren in het consolevenster.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee herstelt u de standaardwaarden van alle instellingen in het consolevenster. Dit wordt ook het gedrag van verschillende waarschuwingsberichten waarmee u het selectievakje standaard om te voorkomen dat het bericht opnieuw wordt weergegeven, wordt opnieuw ingesteld.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee worden de standaardwaarden van de token kleuren in het scriptvenster hersteld.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee herstelt u de standaardwaarden van de token kleuren voor XML-elementen die worden weergegeven in de Windows PowerShell ISE. Zie ook [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Eigenschappen

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u het aantal minuten tussen automatische opslagbewerkingen van uw bestanden door de Windows PowerShell ISE. De standaardwaarde is 2 minuten. De waarde is een geheel getal.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Hiermee geeft u de achtergrondkleur voor het opdrachtvenster. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

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

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u de achtergrondkleur voor het consolevenster. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u de voorgrondkleur van de tekst in het consolevenster.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u de achtergrondkleur van de tekst in het consolevenster.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Console. Deze eigenschap is een dictionary-object met de naam/waarde-paren van tokentypen en kleuren van het consolevenster. Zie het wijzigen van de kleuren van de tokens IntelliSense in het scriptvenster [TokenColors](#tokencolors). Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, NewLine, getal, Operator, positie, StatementSeparator, String, Type, Onbekend, variabele.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de achtergrondkleur voor de foutopsporing tekst die verschijnt in het consolevenster. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de voorgrondkleur voor de foutopsporing tekst die verschijnt in het consolevenster. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Een verzameling eigenschappen die de standaardwaarden moet worden gebruikt wanneer het opnieuw instellen van methoden worden gebruikt.

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

Hiermee geeft u de achtergrondkleur voor fouttekst die wordt weergegeven in het consolevenster. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de voorgrondkleur voor fouttekst die wordt weergegeven in het consolevenster. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Geeft de lettertypenaam momenteel in gebruik is in het scriptvenster zowel het consolevenster.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de tekengrootte als een geheel getal. Het wordt gebruikt in het scriptvenster, het opdrachtvenster en het deelvenster Uitvoer. Het geldige waardenbereik is 8 tot en met 32.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u het aantal seconden dat IntelliSense gebruikt om op te lossen momenteel tekst. Na dit aantal seconden IntelliSense een time-out optreedt en kunt u verder kunt typen. De standaardwaarde is 3 seconden. De waarde is een geheel getal.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u het aantal onlangs geopende bestanden die Windows PowerShell ISE en wordt weergegeven aan de onderkant van de **bestand openen** menu. De standaardwaarde is 10. De waarde is een geheel getal.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

De eigenschap lezen/schrijven die opgehaald of ingesteld van de achtergrondkleur voor het deelvenster Uitvoer zelf. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

De eigenschap lezen/schrijven waarmee de voorgrondkleur van de tekst in het deelvenster Uitvoer in Windows PowerShell ISE 2.0 wordt gewijzigd.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  Zie voor latere versies [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

Het lezen/schrijven-eigenschap die de achtergrondkleur van de tekst in het deelvenster Uitvoer wordt.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De eigenschap lezen/schrijven die opgehaald of ingesteld van de achtergrondkleur voor bestanden. Er is een exemplaar van de **System.Windows.Media.Color** klasse.

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De eigenschap lezen/schrijven die opgehaald of ingesteld van de voorgrondkleur voor niet-scriptbestanden in de Script-veld.
U kunt de voorgrondkleur voor scriptbestanden instellen met de [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De eigenschap lezen/schrijven die opgehaald of ingesteld van de positie van het scriptvenster op de weergave. De tekenreeks kan niet 'Maximized', 'Top' of 'Rechts'.

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of de **CTRL + J** lijst met codefragmenten omvat de starter die is opgenomen in Windows PowerShell. Als de waarde **$false**, alleen door de gebruiker gedefinieerde codefragmenten worden weergegeven in de **CTRL + J** lijst. De standaardwaarde is **$true**.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of IntelliSense syntaxis, parameter en suggesties waarde in het consolevenster biedt. De standaardwaarde is **$true**.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of IntelliSense syntaxis, parameter en suggesties waarde in het scriptvenster biedt. De standaardwaarde is **$true**.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of het scriptvenster regelnummers in de linkermarge weergeeft. De standaardwaarde is **$true**.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of het scriptvenster worden uitgevouwen en samengevouwen haken naast stukjes code in de linkermarge weergegeven. Wanneer ze worden weergegeven, klikt u op de min \( - \) pictogrammen naast een blok van tekst naar deze samenvouwen of klik op het plusteken \( + \) pictogram uitbreiden van een blok van tekst. De standaardwaarde is **$true**.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u op of de ISE-werkbalk aan de bovenkant van het Windows PowerShell ISE-venster wordt weergegeven. De standaardwaarde is **$true**.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u op of een waarschuwing wordt weergegeven wanneer een script automatisch opgeslagen wordt voordat deze wordt uitgevoerd. De standaardwaarde is **$true**.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u op of een waarschuwing wordt weergegeven als hetzelfde bestand wordt geopend in andere PowerShell tabbladen. Indien ingesteld op **$true**, hetzelfde bestand openen in meerdere tabbladen geeft dit bericht: "een kopie van dit bestand is geopend in een ander tabblad van de Windows PowerShell. Wijzigingen in dit bestand heeft invloed op alle geopende exemplaren." De standaardwaarde is **$true**.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Script. Deze eigenschap is een dictionary-object met de naam/waarde-paren van tokentypen en kleuren voor het Script-veld. Zie het wijzigen van de kleuren van de tokens IntelliSense in het consolevenster [ConsoleTokenColors](#consoletokencolors). Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultTokenColors](#restoredefaulttokencolors). Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, NewLine, getal, Operator, positie, StatementSeparator, String, Type, Onbekend, variabele.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of u kunt de Enter-toets Selecteer een optie in het consolevenster opgegeven IntelliSense. De standaardwaarde is **$true**.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of u een optie IntelliSense verstrekte selecteren in het scriptvenster de Enter-toets kunt gebruiken. De standaardwaarde is **$true**.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u op of de lokaal geïnstalleerde Help of de online TechNet-bibliotheek Help wordt weergegeven wanneer u op F1 drukt de cursor in een trefwoord. Indien ingesteld op **$true**, een pop-upvenster uit de lokaal geïnstalleerde Help-inhoud bevat. U kunt de Help-bestanden installeren door het uitvoeren van de `Update-Help` opdracht. Indien ingesteld op **$false**, en vervolgens uw browser geopend met een pagina in de TechNet-bibliotheek.

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

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u een dictionary-object met de naam/waarde-paren van tokentypen en kleuren voor XML-inhoud die wordt weergegeven in de Windows PowerShell ISE. Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, NewLine, getal, Operator, positie, StatementSeparator, String, Type, Onbekend, variabele. Zie ook [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Uitzoomen

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Hiermee geeft u de relatieve grootte van tekst in de Console en het Script deelvensters. De standaardwaarde is 100. Lagere waarden kunt u de tekst in Windows PowerShell ISE kleinere geopend terwijl grotere aantallen ervoor zorgen dat de tekst die moet worden weergegeven groter veroorzaken. De waarde is een geheel getal met een bereik van 20 tot en met 400.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Zie ook

- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)