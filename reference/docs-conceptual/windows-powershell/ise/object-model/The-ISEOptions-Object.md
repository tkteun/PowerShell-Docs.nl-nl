---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Het ISEOptions-object
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810097"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="c9f21-103">Het ISEOptions-object</span><span class="sxs-lookup"><span data-stu-id="c9f21-103">The ISEOptions Object</span></span>

<span data-ttu-id="c9f21-104">Het **ISEOptions** -object vertegenwoordigt verschillende instellingen voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c9f21-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="c9f21-105">Het is een exemplaar van de klasse **micro soft. Power shell. host. ISE. ISEOptions** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="c9f21-106">Het **ISEOptions** -object biedt de volgende methoden en eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="c9f21-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="c9f21-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="c9f21-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="c9f21-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="c9f21-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="c9f21-109">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-110">Hiermee herstelt u de standaard waarden van de token kleuren in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="c9f21-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="c9f21-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="c9f21-112">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-113">Hiermee herstelt u de standaard waarden van alle opties instellingen in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="c9f21-114">Ook wordt het gedrag van verschillende waarschuwings berichten die het standaard selectie vakje bieden, opnieuw ingesteld om te voor komen dat het bericht opnieuw wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f21-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="c9f21-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="c9f21-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="c9f21-116">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-117">Hiermee worden de standaard waarden van de token kleuren in het Script-venster hersteld.</span><span class="sxs-lookup"><span data-stu-id="c9f21-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="c9f21-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="c9f21-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="c9f21-119">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-120">Hiermee herstelt u de standaard waarden van de token kleuren voor XML-elementen die worden weer gegeven in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c9f21-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="c9f21-121">Zie ook [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="c9f21-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="c9f21-122">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c9f21-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="c9f21-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="c9f21-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="c9f21-124">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-125">Hiermee geeft u het aantal minuten op tussen de automatische opslag bewerkingen van uw bestanden door Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c9f21-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="c9f21-126">De standaard waarde is 2 minuten.</span><span class="sxs-lookup"><span data-stu-id="c9f21-126">The default value is 2 minutes.</span></span> <span data-ttu-id="c9f21-127">De waarde is een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="c9f21-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="c9f21-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="c9f21-129">Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="c9f21-130">Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="c9f21-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="c9f21-131">Hiermee geeft u de achtergrond kleur voor het opdracht venster op.</span><span class="sxs-lookup"><span data-stu-id="c9f21-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="c9f21-132">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="c9f21-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="c9f21-133">CommandPaneUp</span></span>

<span data-ttu-id="c9f21-134">Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="c9f21-135">Hiermee wordt aangegeven of het opdracht venster zich boven het deel venster uitvoer bevindt.</span><span class="sxs-lookup"><span data-stu-id="c9f21-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="c9f21-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="c9f21-137">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-138">Hiermee geeft u de achtergrond kleur voor het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="c9f21-139">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="c9f21-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="c9f21-141">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-142">Hiermee geeft u de voorgrond kleur van de tekst in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="c9f21-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="c9f21-144">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-145">Hiermee geeft u de achtergrond kleur van de tekst in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="c9f21-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="c9f21-146">ConsoleTokenColors</span></span>

<span data-ttu-id="c9f21-147">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-148">Hiermee geeft u de kleuren van de IntelliSense-tokens in het deel venster Windows PowerShell ISE console.</span><span class="sxs-lookup"><span data-stu-id="c9f21-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="c9f21-149">Deze eigenschap is een woordenlijst object dat naam/waarde-paren van token typen en kleuren voor het console venster bevat.</span><span class="sxs-lookup"><span data-stu-id="c9f21-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="c9f21-150">Zie [TokenColors](#tokencolors)voor informatie over het wijzigen van de kleuren van de IntelliSense-tokens in het Script-venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span>
<span data-ttu-id="c9f21-151">Zie [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors)als u de kleuren opnieuw wilt instellen op de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="c9f21-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span>
<span data-ttu-id="c9f21-152">Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, sleutel woord, LineContinuation, LoopLabel, lid, nieuwe regel, nummer, operator, positie, StatementSeparator, teken reeks, type, onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="c9f21-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="c9f21-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-153">DebugBackgroundColor</span></span>

<span data-ttu-id="c9f21-154">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-155">Hiermee geeft u de achtergrond kleur voor de tekst van de fout opsporing die wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="c9f21-156">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="c9f21-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-157">DebugForegroundColor</span></span>

<span data-ttu-id="c9f21-158">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-159">Hiermee geeft u de voorgrond kleur voor de tekst van de fout opsporing die wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="c9f21-160">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="c9f21-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="c9f21-161">DefaultOptions</span></span>

<span data-ttu-id="c9f21-162">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-163">Een verzameling eigenschappen waarmee de standaard waarden worden opgegeven die moeten worden gebruikt wanneer de methoden voor opnieuw instellen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c9f21-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="c9f21-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="c9f21-165">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-166">Hiermee geeft u de achtergrond kleur voor de fout tekst op die wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="c9f21-167">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="c9f21-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-168">ErrorForegroundColor</span></span>

<span data-ttu-id="c9f21-169">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-170">Hiermee geeft u de voorgrond kleur voor de fout tekst op die wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="c9f21-171">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="c9f21-172">FontName</span><span class="sxs-lookup"><span data-stu-id="c9f21-172">FontName</span></span>

<span data-ttu-id="c9f21-173">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-174">Hiermee geeft u de naam van het letter type op dat momenteel wordt gebruikt in het Script venster en het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="c9f21-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="c9f21-175">FontSize</span></span>

<span data-ttu-id="c9f21-176">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-177">Geeft de teken grootte als een geheel getal aan.</span><span class="sxs-lookup"><span data-stu-id="c9f21-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="c9f21-178">Het wordt gebruikt in het Script venster, in het opdracht venster en in het deel venster uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9f21-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="c9f21-179">Het geldige waarden bereik is 8 tot en met 32.</span><span class="sxs-lookup"><span data-stu-id="c9f21-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="c9f21-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="c9f21-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="c9f21-181">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-182">Hiermee geeft u het aantal seconden op dat door IntelliSense wordt gebruikt om de momenteel getypte tekst op te lossen.</span><span class="sxs-lookup"><span data-stu-id="c9f21-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span>
<span data-ttu-id="c9f21-183">Na dit aantal seconden loopt IntelliSense een time-out en kunt u door gaan met typen.</span><span class="sxs-lookup"><span data-stu-id="c9f21-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="c9f21-184">De standaard waarde is 3 seconden.</span><span class="sxs-lookup"><span data-stu-id="c9f21-184">The default value is 3 seconds.</span></span> <span data-ttu-id="c9f21-185">De waarde is een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="c9f21-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="c9f21-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="c9f21-186">MruCount</span></span>

<span data-ttu-id="c9f21-187">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-188">Hiermee geeft u het aantal onlangs geopende bestanden op dat Windows PowerShell ISE gevolgd en onder aan het menu **bestand openen** wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f21-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="c9f21-189">De standaardwaarde is 10.</span><span class="sxs-lookup"><span data-stu-id="c9f21-189">The default value is 10.</span></span> <span data-ttu-id="c9f21-190">De waarde is een geheel getal.</span><span class="sxs-lookup"><span data-stu-id="c9f21-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="c9f21-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="c9f21-192">Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="c9f21-193">Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="c9f21-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="c9f21-194">De eigenschap lezen/schrijven waarmee de achtergrond kleur voor het deel venster uitvoer wordt opgehaald of ingesteld.</span><span class="sxs-lookup"><span data-stu-id="c9f21-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="c9f21-195">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="c9f21-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="c9f21-197">Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="c9f21-198">Zie voor latere versies [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="c9f21-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="c9f21-199">De eigenschap lezen/schrijven waarmee de voorgrond kleur van de tekst in het deel venster uitvoer van Windows PowerShell ISE 2,0 wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="c9f21-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="c9f21-201">Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="c9f21-202">Zie voor latere versies [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="c9f21-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="c9f21-203">De eigenschap lezen/schrijven waarmee de achtergrond kleur van de tekst in het deel venster uitvoer wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="c9f21-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="c9f21-205">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-206">De eigenschap lezen/schrijven waarmee de achtergrond kleur voor bestanden wordt opgehaald of ingesteld.</span><span class="sxs-lookup"><span data-stu-id="c9f21-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="c9f21-207">Het is een instantie van de klasse **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="c9f21-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="c9f21-209">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-210">De eigenschap lezen/schrijven waarmee de voorgrond kleur voor niet-script bestanden in het Script-venster wordt opgehaald of ingesteld.</span><span class="sxs-lookup"><span data-stu-id="c9f21-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="c9f21-211">Als u de voorgrond kleur voor script bestanden wilt instellen, gebruikt u de [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="c9f21-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="c9f21-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="c9f21-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="c9f21-213">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-214">De eigenschap lezen/schrijven waarmee de positie van het Script venster op de weer gave wordt opgehaald of ingesteld.</span><span class="sxs-lookup"><span data-stu-id="c9f21-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="c9f21-215">De teken reeks kan ' Maximized ', ' top ' of ' right ' zijn.</span><span class="sxs-lookup"><span data-stu-id="c9f21-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="c9f21-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="c9f21-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="c9f21-217">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-218">Hiermee wordt aangegeven of de <kbd>CTRL</kbd> + <kbd>J</kbd> -lijst met code fragmenten de starter set bevat die is opgenomen in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="c9f21-218">Specifies whether the <kbd>CTRL</kbd>+<kbd>J</kbd> list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="c9f21-219">Als deze instelling `$false` is ingesteld op, worden alleen door de gebruiker gedefinieerde fragmenten weer gegeven in de lijst met <kbd>CTRL</kbd> + <kbd>J</kbd> .</span><span class="sxs-lookup"><span data-stu-id="c9f21-219">When set to `$false`, only user-defined snippets appear in the <kbd>CTRL</kbd>+<kbd>J</kbd> list.</span></span>
<span data-ttu-id="c9f21-220">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-220">The default value is `$true`.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="c9f21-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="c9f21-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="c9f21-222">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-223">Hiermee geeft u op of IntelliSense syntaxis, para meters en waarde Suggestions biedt in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span>
<span data-ttu-id="c9f21-224">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-224">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="c9f21-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="c9f21-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="c9f21-226">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-227">Hiermee geeft u op of IntelliSense syntaxis, para meters en waarde Suggestions biedt in het Script-venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span>
<span data-ttu-id="c9f21-228">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-228">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="c9f21-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="c9f21-229">ShowLineNumbers</span></span>

<span data-ttu-id="c9f21-230">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-231">Hiermee wordt aangegeven of in het deel venster script regel nummers in de linkermarge worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f21-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="c9f21-232">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-232">The default value is `$true`.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="c9f21-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="c9f21-233">ShowOutlining</span></span>

<span data-ttu-id="c9f21-234">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-235">Hiermee wordt aangegeven of het deel venster script uitbreid bare en samengevouwen haakjes naast de secties met de code in de linkermarge worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f21-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="c9f21-236">Wanneer deze worden weer gegeven, kunt u op de min- `-` pictogrammen naast een tekst blok klikken om deze samen te vouwen of op het plus `+` pictogram klikken om een tekst blok te verg Roten.</span><span class="sxs-lookup"><span data-stu-id="c9f21-236">When they are displayed, you can click the minus `-` icons next to a block of text to collapse it or click the plus `+` icon to expand a block of text.</span></span> <span data-ttu-id="c9f21-237">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-237">The default value is `$true`.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="c9f21-238">Weer</span><span class="sxs-lookup"><span data-stu-id="c9f21-238">ShowToolBar</span></span>

<span data-ttu-id="c9f21-239">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-240">Hiermee wordt aangegeven of de ISE-werk balk boven aan het Windows PowerShell ISE-venster wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f21-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="c9f21-241">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-241">The default value is `$true`.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="c9f21-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="c9f21-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="c9f21-243">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-244">Hiermee wordt aangegeven of een waarschuwings bericht wordt weer gegeven wanneer een script automatisch wordt opgeslagen voordat het wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c9f21-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span>
<span data-ttu-id="c9f21-245">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-245">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="c9f21-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="c9f21-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="c9f21-247">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-248">Hiermee wordt aangegeven of een waarschuwing wordt weer gegeven wanneer hetzelfde bestand wordt geopend in verschillende Power shell-tabbladen.</span><span class="sxs-lookup"><span data-stu-id="c9f21-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="c9f21-249">Als deze instelling `$true` is ingesteld op, wordt het volgende bericht weer gegeven: ' een kopie van dit bestand is geopend in een ander Windows Power shell-tabblad. wijzigingen in dit bestand zijn van invloed op alle geopende exemplaren. '</span><span class="sxs-lookup"><span data-stu-id="c9f21-249">If set to `$true`, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="c9f21-250">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-250">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="c9f21-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="c9f21-251">TokenColors</span></span>

<span data-ttu-id="c9f21-252">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-253">Hiermee geeft u de kleuren van de IntelliSense-tokens in het deel venster Windows PowerShell ISE script.</span><span class="sxs-lookup"><span data-stu-id="c9f21-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="c9f21-254">Deze eigenschap is een woordenlijst object dat naam/waarde-paren van token typen en kleuren voor het Script-venster bevat.</span><span class="sxs-lookup"><span data-stu-id="c9f21-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="c9f21-255">Zie [ConsoleTokenColors](#consoletokencolors)voor informatie over het wijzigen van de kleuren van de IntelliSense-tokens in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span>
<span data-ttu-id="c9f21-256">Zie [RestoreDefaultTokenColors](#restoredefaulttokencolors)als u de kleuren opnieuw wilt instellen op de standaard waarden.</span><span class="sxs-lookup"><span data-stu-id="c9f21-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span>
<span data-ttu-id="c9f21-257">Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, sleutel woord, LineContinuation, LoopLabel, lid, nieuwe regel, nummer, operator, positie, StatementSeparator, teken reeks, type, onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="c9f21-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="c9f21-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="c9f21-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="c9f21-259">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-260">Hiermee wordt aangegeven of u de Enter-toets kunt gebruiken om een optie te selecteren die IntelliSense in het console venster is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f21-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="c9f21-261">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-261">The default value is `$true`.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="c9f21-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="c9f21-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="c9f21-263">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-264">Hiermee geeft u op of u de Enter-toets kunt gebruiken om een door IntelliSense opgegeven optie te selecteren in het Script-venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="c9f21-265">De standaardwaarde is `$true`.</span><span class="sxs-lookup"><span data-stu-id="c9f21-265">The default value is `$true`.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="c9f21-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="c9f21-266">UseLocalHelp</span></span>

<span data-ttu-id="c9f21-267">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-268">Hiermee geeft u op of de lokaal geïnstalleerde Help of de Help van de online TechNet-bibliotheek wordt weer gegeven wanneer u op <kbd>F1</kbd> drukt met de cursor in een tref woord.</span><span class="sxs-lookup"><span data-stu-id="c9f21-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press <kbd>F1</kbd> with the cursor positioned in a keyword.</span></span> <span data-ttu-id="c9f21-269">Als `$true` deze is ingesteld op, wordt in een pop-upvenster inhoud weer gegeven van de lokaal geïnstalleerde Help.</span><span class="sxs-lookup"><span data-stu-id="c9f21-269">If set to `$true`, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="c9f21-270">U kunt de Help-bestanden installeren door de opdracht uit te voeren `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="c9f21-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="c9f21-271">Als `$false` deze is ingesteld op, wordt uw browser geopend op een pagina in de TechNet-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="c9f21-271">If set to `$false`, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="c9f21-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="c9f21-273">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-274">Hiermee geeft u de achtergrond kleur voor uitgebreide tekst op die wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="c9f21-275">Het is een object **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="c9f21-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-276">VerboseForegroundColor</span></span>

<span data-ttu-id="c9f21-277">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-278">Hiermee geeft u de voorgrond kleur voor uitgebreide tekst op die wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="c9f21-279">Het is een object **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="c9f21-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-280">WarningBackgroundColor</span></span>

<span data-ttu-id="c9f21-281">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-282">Hiermee geeft u de achtergrond kleur voor waarschuwings tekst op die wordt weer gegeven in het console venster.</span><span class="sxs-lookup"><span data-stu-id="c9f21-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="c9f21-283">Het is een object **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="c9f21-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="c9f21-284">WarningForegroundColor</span></span>

<span data-ttu-id="c9f21-285">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c9f21-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c9f21-286">Hiermee geeft u de voorgrond kleur op voor waarschuwings tekst die wordt weer gegeven in het deel venster uitvoer.</span><span class="sxs-lookup"><span data-stu-id="c9f21-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="c9f21-287">Het is een object **System. Windows. media. Color** .</span><span class="sxs-lookup"><span data-stu-id="c9f21-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="c9f21-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="c9f21-288">XmlTokenColors</span></span>

<span data-ttu-id="c9f21-289">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-290">Hiermee geeft u een woordenlijst object op dat naam/waarde-paren van token typen en kleuren bevat voor XML-inhoud die wordt weer gegeven in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c9f21-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="c9f21-291">Token kleuren kunnen worden ingesteld voor het volgende: kenmerk, opdracht, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, sleutel woord, LineContinuation, LoopLabel, lid, nieuwe regel, nummer, operator, positie, StatementSeparator, teken reeks, type, onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="c9f21-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="c9f21-292">Zie ook [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="c9f21-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="c9f21-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="c9f21-293">Zoom</span></span>

<span data-ttu-id="c9f21-294">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c9f21-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c9f21-295">Hiermee geeft u de relatieve grootte van de tekst in de console-en script deel Vensters.</span><span class="sxs-lookup"><span data-stu-id="c9f21-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="c9f21-296">De standaardwaarde is 100.</span><span class="sxs-lookup"><span data-stu-id="c9f21-296">The default value is 100.</span></span>
<span data-ttu-id="c9f21-297">Bij kleinere waarden wordt de tekst in Windows PowerShell ISE kleiner weer gegeven, terwijl grotere getallen de tekst groter worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c9f21-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="c9f21-298">De waarde is een geheel getal tussen 20 en 400.</span><span class="sxs-lookup"><span data-stu-id="c9f21-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="c9f21-299">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c9f21-299">See Also</span></span>

- [<span data-ttu-id="c9f21-300">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c9f21-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c9f21-301">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="c9f21-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
