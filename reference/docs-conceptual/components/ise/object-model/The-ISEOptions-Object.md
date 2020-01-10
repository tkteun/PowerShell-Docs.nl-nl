---
ms.date: 12/31/2019
keywords: Power shell, cmdlet
title: Het ISEOptions-object
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736944"
---
# <a name="the-iseoptions-object"></a>Het ISEOptions-object

Het **ISEOptions** -object vertegenwoordigt verschillende instellingen voor Windows PowerShell ISE. Het is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEOptions** .

Het **ISEOptions** -object biedt de volgende methoden en eigenschappen.

## <a name="methods"></a>Methoden

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee herstelt u de standaard waarden van de token kleuren in het console venster.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee herstelt u de standaard waarden van alle opties instellingen in het console venster. Ook wordt het gedrag van verschillende waarschuwings berichten die het standaard selectie vakje bieden, opnieuw ingesteld om te voor komen dat het bericht opnieuw wordt weer gegeven.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee worden de standaard waarden van de token kleuren in het Script-venster hersteld.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee herstelt u de standaard waarden van de token kleuren voor XML-elementen die worden weer gegeven in Windows PowerShell ISE. Zie ook [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Eigenschappen

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u het aantal minuten op tussen de automatische opslag bewerkingen van uw bestanden door Windows PowerShell ISE. De standaard waarde is 2 minuten. De waarde is een geheel getal.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd. Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Hiermee geeft u de achtergrond kleur voor het opdracht venster op. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.

Hiermee wordt aangegeven of het opdracht venster zich boven het deel venster uitvoer bevindt.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u de achtergrond kleur voor het console venster. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u de voorgrond kleur van de tekst in het console venster.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u de achtergrond kleur van de tekst in het console venster.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u de kleuren van de IntelliSense-tokens in het deel venster Windows PowerShell ISE console. Deze eigenschap is een woordenlijst object dat naam/waarde-paren van token typen en kleuren voor het console venster bevat. Zie [TokenColors](#tokencolors)voor informatie over het wijzigen van de kleuren van de IntelliSense-tokens in het Script-venster.
Zie [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors)als u de kleuren opnieuw wilt instellen op de standaard waarden.
Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, sleutel woord, LineContinuation, LoopLabel, lid, nieuwe regel, nummer, operator, positie, StatementSeparator, teken reeks, type, Onbekende, variabele.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de achtergrond kleur voor de tekst van de fout opsporing die wordt weer gegeven in het console venster. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de voorgrond kleur voor de tekst van de fout opsporing die wordt weer gegeven in het console venster. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Een verzameling eigenschappen waarmee de standaard waarden worden opgegeven die moeten worden gebruikt wanneer de methoden voor opnieuw instellen worden gebruikt.

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
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

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de achtergrond kleur voor de fout tekst op die wordt weer gegeven in het console venster. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de voorgrond kleur voor de fout tekst op die wordt weer gegeven in het console venster. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de naam van het letter type op dat momenteel wordt gebruikt in het Script venster en het console venster.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Geeft de teken grootte als een geheel getal aan. Het wordt gebruikt in het Script venster, in het opdracht venster en in het deel venster uitvoer. Het geldige waarden bereik is 8 tot en met 32.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u het aantal seconden op dat door IntelliSense wordt gebruikt om de momenteel getypte tekst op te lossen.
Na dit aantal seconden loopt IntelliSense een time-out en kunt u door gaan met typen. De standaard waarde is 3 seconden. De waarde is een geheel getal.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u het aantal onlangs geopende bestanden op dat Windows PowerShell ISE gevolgd en onder aan het menu **bestand openen** wordt weer gegeven. De standaard waarde is 10. De waarde is een geheel getal.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd. Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

De eigenschap lezen/schrijven waarmee de achtergrond kleur voor het deel venster uitvoer wordt opgehaald of ingesteld. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd. Zie voor latere versies [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

De eigenschap lezen/schrijven waarmee de voorgrond kleur van de tekst in het deel venster uitvoer van Windows PowerShell ISE 2,0 wordt gewijzigd.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd. Zie voor latere versies [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

De eigenschap lezen/schrijven waarmee de achtergrond kleur van de tekst in het deel venster uitvoer wordt gewijzigd.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De eigenschap lezen/schrijven waarmee de achtergrond kleur voor bestanden wordt opgehaald of ingesteld. Het is een instantie van de klasse **System. Windows. media. Color** .

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De eigenschap lezen/schrijven waarmee de voorgrond kleur voor niet-script bestanden in het Script-venster wordt opgehaald of ingesteld.
Als u de voorgrond kleur voor script bestanden wilt instellen, gebruikt u de [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De eigenschap lezen/schrijven waarmee de positie van het Script venster op de weer gave wordt opgehaald of ingesteld. De teken reeks kan ' Maximized ', ' top ' of ' right ' zijn.

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt aangegeven of de <kbd>CTRL</kbd>+<kbd>J</kbd> -lijst met fragmenten de starter set bevat die is opgenomen in Windows Power shell. Als deze functie is ingesteld op `$false`, worden alleen door de gebruiker gedefinieerde fragmenten weer gegeven in de lijst met <kbd>CTRL</kbd>+<kbd>J</kbd> .
De standaardwaarde is `$true`.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u op of IntelliSense syntaxis, para meters en waarde Suggestions biedt in het console venster.
De standaardwaarde is `$true`.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u op of IntelliSense syntaxis, para meters en waarde Suggestions biedt in het Script-venster.
De standaardwaarde is `$true`.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt aangegeven of in het deel venster script regel nummers in de linkermarge worden weer gegeven. De standaardwaarde is `$true`.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt aangegeven of het deel venster script uitbreid bare en samengevouwen haakjes naast de secties met de code in de linkermarge worden weer gegeven. Wanneer deze worden weer gegeven, kunt u op de minknop `-` naast een tekst blok klikken om deze samen te vouwen of op het plus `+` pictogram klikken om een tekst blok te verg Roten. De standaardwaarde is `$true`.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>Weer

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt aangegeven of de ISE-werk balk boven aan het Windows PowerShell ISE-venster wordt weer gegeven. De standaardwaarde is `$true`.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt aangegeven of een waarschuwings bericht wordt weer gegeven wanneer een script automatisch wordt opgeslagen voordat het wordt uitgevoerd.
De standaardwaarde is `$true`.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt aangegeven of een waarschuwing wordt weer gegeven wanneer hetzelfde bestand wordt geopend in verschillende Power shell-tabbladen. Als de instelling is ingesteld op `$true`, wordt in het volgende bericht weer gegeven: ' een kopie van dit bestand is geopend op een ander Windows Power shell-tabblad. wijzigingen in dit bestand zijn van invloed op alle geopende exemplaren. ' De standaardwaarde is `$true`.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de kleuren van de IntelliSense-tokens in het deel venster Windows PowerShell ISE script. Deze eigenschap is een woordenlijst object dat naam/waarde-paren van token typen en kleuren voor het Script-venster bevat. Zie [ConsoleTokenColors](#consoletokencolors)voor informatie over het wijzigen van de kleuren van de IntelliSense-tokens in het console venster.
Zie [RestoreDefaultTokenColors](#restoredefaulttokencolors)als u de kleuren opnieuw wilt instellen op de standaard waarden.
Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, sleutel woord, LineContinuation, LoopLabel, lid, nieuwe regel, nummer, operator, positie, StatementSeparator, teken reeks, type, Onbekende, variabele.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee wordt aangegeven of u de Enter-toets kunt gebruiken om een optie te selecteren die IntelliSense in het console venster is opgegeven. De standaardwaarde is `$true`.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u op of u de Enter-toets kunt gebruiken om een door IntelliSense opgegeven optie te selecteren in het Script-venster. De standaardwaarde is `$true`.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u op of de lokaal geïnstalleerde Help of de Help van de online TechNet-bibliotheek wordt weer gegeven wanneer u op <kbd>F1</kbd> drukt met de cursor in een tref woord. Als deze is ingesteld op `$true`, wordt in een pop-upvenster inhoud weer gegeven van de lokaal geïnstalleerde Help. U kunt de Help-bestanden installeren door de `Update-Help` opdracht uit te voeren. Als deze is ingesteld op `$false`, wordt uw browser geopend met een pagina in de TechNet-bibliotheek.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de achtergrond kleur voor uitgebreide tekst op die wordt weer gegeven in het console venster. Het is een object **System. Windows. media. Color** .

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de voorgrond kleur voor uitgebreide tekst op die wordt weer gegeven in het console venster. Het is een object **System. Windows. media. Color** .

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de achtergrond kleur voor waarschuwings tekst op die wordt weer gegeven in het console venster. Het is een object **System. Windows. media. Color** .

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee geeft u de voorgrond kleur op voor waarschuwings tekst die wordt weer gegeven in het deel venster uitvoer. Het is een object **System. Windows. media. Color** .

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u een woordenlijst object op dat naam/waarde-paren van token typen en kleuren bevat voor XML-inhoud die wordt weer gegeven in Windows PowerShell ISE. Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, sleutel woord, LineContinuation, LoopLabel, lid, nieuwe regel, nummer, operator, positie, StatementSeparator, teken reeks, type, Onbekende, variabele. Zie ook [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Zoom

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee geeft u de relatieve grootte van de tekst in de console-en script deel Vensters. De standaardwaarde is 100.
Bij kleinere waarden wordt de tekst in Windows PowerShell ISE kleiner weer gegeven, terwijl grotere getallen de tekst groter worden weer gegeven. De waarde is een geheel getal tussen 20 en 400.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Zie ook

- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
