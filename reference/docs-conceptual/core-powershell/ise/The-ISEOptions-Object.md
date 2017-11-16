---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 5e04adeebacfb9214bf39d9ec9c5f0e01f5729ee
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/08/2017
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="bf3ce-103">Het Object ISEOptions</span><span class="sxs-lookup"><span data-stu-id="bf3ce-103">The ISEOptions Object</span></span>
  <span data-ttu-id="bf3ce-104">De **ISEOptions** object vertegenwoordigt diverse instellingen voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="bf3ce-105">Er is een exemplaar van de **Microsoft.PowerShell.Host.ISE.ISEOptions** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="bf3ce-106">De **ISEOptions** -object biedt de volgende eigenschappen en methoden.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="bf3ce-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="bf3ce-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="bf3ce-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="bf3ce-108">RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="bf3ce-109">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-110">Hiermee herstelt u de standaardwaarden van de token kleuren in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-110">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="bf3ce-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="bf3ce-111">RestoreDefaults\(\)</span></span>
  <span data-ttu-id="bf3ce-112">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-113">Hiermee herstelt u de standaardwaarden van alle instellingen in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="bf3ce-114">Dit wordt ook het gedrag van verschillende waarschuwingsberichten waarmee u het selectievakje standaard om te voorkomen dat het bericht opnieuw wordt weergegeven, wordt opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="bf3ce-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="bf3ce-115">RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="bf3ce-116">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-117">Hiermee worden de standaardwaarden van de token kleuren in het scriptvenster hersteld.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-117">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="bf3ce-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="bf3ce-118">RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="bf3ce-119">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-120">Hiermee herstelt u de standaardwaarden van de token kleuren voor XML-elementen die worden weergegeven in de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="bf3ce-121">Zie ook [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="bf3ce-122">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="bf3ce-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="bf3ce-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="bf3ce-123">AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="bf3ce-124">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-125">Hiermee geeft u het aantal minuten tussen automatische opslagbewerkingen van uw bestanden door de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="bf3ce-126">De standaardwaarde is 2 minuten.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-126">The default value is 2 minutes.</span></span> <span data-ttu-id="bf3ce-127">De waarde is een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-127">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="bf3ce-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-128">CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-129">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="bf3ce-130">Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="bf3ce-131">Hiermee geeft u de achtergrondkleur voor het opdrachtvenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="bf3ce-132">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

### <a name="commandpaneup"></a><span data-ttu-id="bf3ce-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="bf3ce-133">CommandPaneUp</span></span>
  <span data-ttu-id="bf3ce-134">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="bf3ce-135">Hiermee geeft u op of het deelvenster van de opdracht bevindt zich boven het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="bf3ce-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-136">ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-137">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-138">Hiermee geeft u de achtergrondkleur voor het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="bf3ce-139">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="bf3ce-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-140">ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="bf3ce-141">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-142">Hiermee geeft u de voorgrondkleur van de tekst in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-142">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="bf3ce-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-143">ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-144">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-145">Hiermee geeft u de achtergrondkleur van de tekst in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-145">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

### <a name="consoletokencolors"></a><span data-ttu-id="bf3ce-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="bf3ce-146">ConsoleTokenColors</span></span>
  <span data-ttu-id="bf3ce-147">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-148">Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Console.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="bf3ce-149">Deze eigenschap is een dictionary-object met de naam/waarde-paren van tokentypen en kleuren van het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="bf3ce-150">Zie het wijzigen van de kleuren van de tokens IntelliSense in het scriptvenster [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="bf3ce-151">Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="bf3ce-152">Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, NewLine, getal, Operator, positie, StatementSeparator, String, Type, Onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="bf3ce-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-153">DebugBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-154">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-155">Hiermee geeft u de achtergrondkleur voor de foutopsporing tekst die verschijnt in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="bf3ce-156">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="bf3ce-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-157">DebugForegroundColor</span></span>
  <span data-ttu-id="bf3ce-158">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-159">Hiermee geeft u de voorgrondkleur voor de foutopsporing tekst die verschijnt in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="bf3ce-160">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

### <a name="defaultoptions"></a><span data-ttu-id="bf3ce-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="bf3ce-161">DefaultOptions</span></span>
  <span data-ttu-id="bf3ce-162">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-163">Een verzameling eigenschappen die de standaardwaarden moet worden gebruikt wanneer het opnieuw instellen van methoden worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

```
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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="bf3ce-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-164">ErrorBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-165">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-166">Hiermee geeft u de achtergrondkleur voor fouttekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="bf3ce-167">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="bf3ce-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-168">ErrorForegroundColor</span></span>
  <span data-ttu-id="bf3ce-169">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-170">Hiermee geeft u de voorgrondkleur voor fouttekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="bf3ce-171">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

### <a name="fontname"></a><span data-ttu-id="bf3ce-172">Lettertype</span><span class="sxs-lookup"><span data-stu-id="bf3ce-172">FontName</span></span>
  <span data-ttu-id="bf3ce-173">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-174">Geeft de lettertypenaam momenteel in gebruik is in het scriptvenster zowel het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

### <a name="fontsize"></a><span data-ttu-id="bf3ce-175">Tekengrootte</span><span class="sxs-lookup"><span data-stu-id="bf3ce-175">FontSize</span></span>
  <span data-ttu-id="bf3ce-176">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-177">Hiermee geeft u de tekengrootte als een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="bf3ce-178">Het wordt gebruikt in het scriptvenster, het opdrachtvenster en het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="bf3ce-179">Het geldige waardenbereik is 8 tot en met 32.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-179">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="bf3ce-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="bf3ce-180">IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="bf3ce-181">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-182">Hiermee geeft u het aantal seconden dat IntelliSense gebruikt om op te lossen momenteel tekst.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="bf3ce-183">Na dit aantal seconden IntelliSense een time-out optreedt en kunt u verder kunt typen.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="bf3ce-184">De standaardwaarde is 3 seconden.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-184">The default value is 3 seconds.</span></span> <span data-ttu-id="bf3ce-185">De waarde is een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-185">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="bf3ce-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="bf3ce-186">MruCount</span></span>
  <span data-ttu-id="bf3ce-187">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-188">Hiermee geeft u het aantal onlangs geopende bestanden die Windows PowerShell ISE en wordt weergegeven aan de onderkant van de **bestand openen** menu.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="bf3ce-189">De standaardwaarde is 10.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-189">The default value is 10.</span></span> <span data-ttu-id="bf3ce-190">De waarde is een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-190">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="bf3ce-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-191">OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-192">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="bf3ce-193">Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="bf3ce-194">De eigenschap lezen/schrijven die opgehaald of ingesteld van de achtergrondkleur voor het deelvenster Uitvoer zelf.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="bf3ce-195">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="bf3ce-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-196">OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="bf3ce-197">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="bf3ce-198">Zie voor latere versies [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

 <span data-ttu-id="bf3ce-199">De eigenschap lezen/schrijven waarmee de voorgrondkleur van de tekst in het deelvenster Uitvoer in Windows PowerShell ISE 2.0 wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="bf3ce-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-200">OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-201">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="bf3ce-202">Zie voor latere versies [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

 <span data-ttu-id="bf3ce-203">Het lezen/schrijven-eigenschap die de achtergrondkleur van de tekst in het deelvenster Uitvoer wordt.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="bf3ce-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-204">ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-205">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-206">De eigenschap lezen/schrijven die opgehaald of ingesteld van de achtergrondkleur voor bestanden.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="bf3ce-207">Er is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'

```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="bf3ce-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-208">ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="bf3ce-209">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-210">De eigenschap lezen/schrijven die opgehaald of ingesteld van de voorgrondkleur voor niet-scriptbestanden in de Script-veld.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="bf3ce-211">U kunt de voorgrondkleur voor scriptbestanden instellen met de [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="bf3ce-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="bf3ce-212">SelectedScriptPaneState</span></span>
  <span data-ttu-id="bf3ce-213">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-214">De eigenschap lezen/schrijven die opgehaald of ingesteld van de positie van het scriptvenster op de weergave.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="bf3ce-215">De tekenreeks kan niet 'Maximized', 'Top' of 'Rechts'.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-215">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

### <a name="showdefaultsnippets"></a><span data-ttu-id="bf3ce-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="bf3ce-216">ShowDefaultSnippets</span></span>
  <span data-ttu-id="bf3ce-217">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-218">Hiermee geeft u op of de **CTRL + J** lijst met codefragmenten omvat de starter die is opgenomen in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="bf3ce-219">Als de waarde **$false**, alleen door de gebruiker gedefinieerde codefragmenten worden weergegeven in de **CTRL + J** lijst.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="bf3ce-220">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-220">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="bf3ce-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="bf3ce-221">ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="bf3ce-222">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-223">Hiermee geeft u op of IntelliSense syntaxis, parameter en suggesties waarde in het consolevenster biedt.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="bf3ce-224">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-224">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="bf3ce-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="bf3ce-225">ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="bf3ce-226">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-227">Hiermee geeft u op of IntelliSense syntaxis, parameter en suggesties waarde in het scriptvenster biedt.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="bf3ce-228">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-228">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="bf3ce-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="bf3ce-229">ShowLineNumbers</span></span>
  <span data-ttu-id="bf3ce-230">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-231">Hiermee geeft u op of het scriptvenster regelnummers in de linkermarge weergeeft.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="bf3ce-232">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-232">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="bf3ce-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="bf3ce-233">ShowOutlining</span></span>
  <span data-ttu-id="bf3ce-234">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-235">Hiermee geeft u op of het scriptvenster worden uitgevouwen en samengevouwen haken naast stukjes code in de linkermarge weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="bf3ce-236">Wanneer ze worden weergegeven, klikt u op de min \( - \) pictogrammen naast een blok van tekst naar deze samenvouwen of klik op het plusteken \( + \) pictogram uitbreiden van een blok van tekst.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="bf3ce-237">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-237">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="bf3ce-238">WerkbalkWeergeven</span><span class="sxs-lookup"><span data-stu-id="bf3ce-238">ShowToolBar</span></span>
  <span data-ttu-id="bf3ce-239">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-240">Hiermee geeft u op of de ISE-werkbalk aan de bovenkant van het Windows PowerShell ISE-venster wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="bf3ce-241">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-241">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="bf3ce-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="bf3ce-242">ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="bf3ce-243">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-244">Hiermee geeft u op of een waarschuwing wordt weergegeven wanneer een script automatisch opgeslagen wordt voordat deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="bf3ce-245">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-245">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="bf3ce-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="bf3ce-246">ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="bf3ce-247">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-248">Hiermee geeft u op of een waarschuwing wordt weergegeven als hetzelfde bestand wordt geopend in andere PowerShell tabbladen.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="bf3ce-249">Indien ingesteld op **$true**, hetzelfde bestand openen in meerdere tabbladen geeft dit bericht: "een kopie van dit bestand is geopend in een ander tabblad van de Windows PowerShell. Wijzigingen in dit bestand heeft invloed op alle geopende exemplaren."</span><span class="sxs-lookup"><span data-stu-id="bf3ce-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="bf3ce-250">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-250">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

### <a name="tokencolors"></a><span data-ttu-id="bf3ce-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="bf3ce-251">TokenColors</span></span>
  <span data-ttu-id="bf3ce-252">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-253">Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Script.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="bf3ce-254">Deze eigenschap is een dictionary-object met de naam/waarde-paren van tokentypen en kleuren voor het Script-veld.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="bf3ce-255">Zie het wijzigen van de kleuren van de tokens IntelliSense in het consolevenster [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="bf3ce-256">Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="bf3ce-257">Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, NewLine, getal, Operator, positie, StatementSeparator, String, Type, Onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="bf3ce-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="bf3ce-258">UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="bf3ce-259">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-260">Hiermee geeft u op of u kunt de Enter-toets Selecteer een optie in het consolevenster opgegeven IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="bf3ce-261">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-261">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="bf3ce-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="bf3ce-262">UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="bf3ce-263">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-264">Hiermee geeft u op of u een optie IntelliSense verstrekte selecteren in het scriptvenster de Enter-toets kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="bf3ce-265">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-265">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

### <a name="uselocalhelp"></a><span data-ttu-id="bf3ce-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="bf3ce-266">UseLocalHelp</span></span>
  <span data-ttu-id="bf3ce-267">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-268">Hiermee geeft u op of de lokaal geïnstalleerde Help of de online TechNet-bibliotheek Help wordt weergegeven wanneer u op F1 drukt de cursor in een trefwoord.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="bf3ce-269">Indien ingesteld op **$true**, een pop-upvenster uit de lokaal geïnstalleerde Help-inhoud bevat.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="bf3ce-270">U kunt de Help-bestanden installeren door het uitvoeren van de `Update-Help` opdracht.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="bf3ce-271">Indien ingesteld op **$false**, en vervolgens uw browser geopend met een pagina in de TechNet-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="bf3ce-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-272">VerboseBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-273">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-274">Hiermee geeft u de achtergrondkleur voor uitgebreide tekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="bf3ce-275">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-275">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="bf3ce-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-276">VerboseForegroundColor</span></span>
  <span data-ttu-id="bf3ce-277">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-278">Hiermee geeft u de voorgrondkleur voor uitgebreide tekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="bf3ce-279">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-279">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor ='yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="bf3ce-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-280">WarningBackgroundColor</span></span>
  <span data-ttu-id="bf3ce-281">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-282">Hiermee geeft u de achtergrondkleur voor waarschuwingstekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="bf3ce-283">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-283">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="bf3ce-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="bf3ce-284">WarningForegroundColor</span></span>
  <span data-ttu-id="bf3ce-285">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="bf3ce-286">Hiermee geeft u de voorgrondkleur voor waarschuwingstekst die wordt weergegeven in het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="bf3ce-287">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-287">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor ='yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="bf3ce-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="bf3ce-288">XmlTokenColors</span></span>
  <span data-ttu-id="bf3ce-289">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-290">Hiermee geeft u een dictionary-object met de naam/waarde-paren van tokentypen en kleuren voor XML-inhoud die wordt weergegeven in de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="bf3ce-291">Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, NewLine, getal, Operator, positie, StatementSeparator, String, Type, Onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="bf3ce-292">Zie ook [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="bf3ce-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

### <a name="zoom"></a><span data-ttu-id="bf3ce-293">Uitzoomen</span><span class="sxs-lookup"><span data-stu-id="bf3ce-293">Zoom</span></span>
  <span data-ttu-id="bf3ce-294">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="bf3ce-295">Hiermee geeft u de relatieve grootte van tekst in de Console en het Script deelvensters.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="bf3ce-296">De standaardwaarde is 100.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-296">The default value is 100.</span></span> <span data-ttu-id="bf3ce-297">Lagere waarden kunt u de tekst in Windows PowerShell ISE kleinere geopend terwijl grotere aantallen ervoor zorgen dat de tekst die moet worden weergegeven groter veroorzaken.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="bf3ce-298">De waarde is een geheel getal met een bereik van 20 tot en met 400.</span><span class="sxs-lookup"><span data-stu-id="bf3ce-298">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="bf3ce-299">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bf3ce-299">See Also</span></span>
- [<span data-ttu-id="bf3ce-300">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="bf3ce-300">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="bf3ce-301">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="bf3ce-301">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

