---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEOptions-object
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057771"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="29ee0-103">Het ISEOptions-object</span><span class="sxs-lookup"><span data-stu-id="29ee0-103">The ISEOptions Object</span></span>

<span data-ttu-id="29ee0-104">De **ISEOptions** object vertegenwoordigt diverse instellingen voor Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="29ee0-105">Het is een exemplaar van de **Microsoft.PowerShell.Host.ISE.ISEOptions** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="29ee0-106">De **ISEOptions** object biedt de volgende eigenschappen en methoden.</span><span class="sxs-lookup"><span data-stu-id="29ee0-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="29ee0-107">Methoden</span><span class="sxs-lookup"><span data-stu-id="29ee0-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="29ee0-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="29ee0-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="29ee0-109">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-110">Hiermee herstelt u de standaardwaarden van de token kleuren in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="29ee0-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="29ee0-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="29ee0-112">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-113">Hiermee herstelt u de standaardwaarden van alle instellingen in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="29ee0-114">Het stelt ook het gedrag van verschillende waarschuwingsberichten waarmee u het selectievakje standaard om te voorkomen dat het bericht opnieuw wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="29ee0-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="29ee0-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="29ee0-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="29ee0-116">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-117">Hiermee herstelt u de standaardwaarden van de token kleuren in het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="29ee0-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="29ee0-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="29ee0-119">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-120">Hiermee herstelt u de standaardwaarden van de token kleuren voor XML-elementen die worden weergegeven in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="29ee0-121">Zie ook [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="29ee0-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="29ee0-122">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="29ee0-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="29ee0-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="29ee0-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="29ee0-124">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-125">Hiermee geeft u het aantal minuten tussen bewerkingen automatisch opslaan van uw bestanden in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="29ee0-126">De standaardwaarde is 2 minuten.</span><span class="sxs-lookup"><span data-stu-id="29ee0-126">The default value is 2 minutes.</span></span> <span data-ttu-id="29ee0-127">De waarde is een geheel getal zijn.</span><span class="sxs-lookup"><span data-stu-id="29ee0-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="29ee0-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="29ee0-129">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29ee0-130">Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29ee0-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="29ee0-131">Hiermee geeft u de achtergrondkleur voor het opdrachtvenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="29ee0-132">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="29ee0-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="29ee0-133">CommandPaneUp</span></span>

<span data-ttu-id="29ee0-134">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="29ee0-135">Hiermee geeft u op of het deelvenster van de opdracht bevindt zich boven het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="29ee0-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="29ee0-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="29ee0-137">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-138">Hiermee geeft u de achtergrondkleur van het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="29ee0-139">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="29ee0-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="29ee0-141">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-142">Hiermee geeft u de voorgrondkleur van de tekst in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="29ee0-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="29ee0-144">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-145">Hiermee geeft u de achtergrondkleur van de tekst in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="29ee0-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="29ee0-146">ConsoleTokenColors</span></span>

<span data-ttu-id="29ee0-147">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-148">Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Console.</span><span class="sxs-lookup"><span data-stu-id="29ee0-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="29ee0-149">Deze eigenschap is een dictionary-object met de naam/waarde-paren van de typen tokens en kleuren voor het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="29ee0-150">Zie het wijzigen van de kleuren van de tokens IntelliSense in het scriptvenster [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="29ee0-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="29ee0-151">Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="29ee0-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="29ee0-152">Token kleuren kunnen worden ingesteld voor het volgende: Kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, nieuwe regel, getal, Operator, positie, StatementSeparator, String, Type, onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="29ee0-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="29ee0-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-153">DebugBackgroundColor</span></span>

<span data-ttu-id="29ee0-154">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-155">Hiermee geeft u de achtergrondkleur voor de foutopsporing tekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="29ee0-156">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="29ee0-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-157">DebugForegroundColor</span></span>

<span data-ttu-id="29ee0-158">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-159">Hiermee geeft u de voorgrondkleur aan voor de foutopsporing tekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="29ee0-160">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="29ee0-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="29ee0-161">DefaultOptions</span></span>

<span data-ttu-id="29ee0-162">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-163">Een verzameling eigenschappen die de standaardwaarden worden gebruikt wanneer het opnieuw instellen-methoden worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="29ee0-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="29ee0-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="29ee0-165">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-166">Hiermee geeft u de achtergrondkleur voor de tekst van de fout die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="29ee0-167">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="29ee0-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-168">ErrorForegroundColor</span></span>

<span data-ttu-id="29ee0-169">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-170">Hiermee geeft u de voorgrondkleur aan voor de tekst van de fout die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="29ee0-171">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="29ee0-172">FontName</span><span class="sxs-lookup"><span data-stu-id="29ee0-172">FontName</span></span>

<span data-ttu-id="29ee0-173">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-174">Hiermee geeft u de naam van het lettertype in momenteel wordt gebruikt in het scriptvenster en het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="29ee0-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="29ee0-175">FontSize</span></span>

<span data-ttu-id="29ee0-176">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-177">Hiermee geeft u de tekengrootte als een geheel getal zijn.</span><span class="sxs-lookup"><span data-stu-id="29ee0-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="29ee0-178">Het wordt gebruikt in het scriptvenster, het opdrachtvenster en het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="29ee0-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="29ee0-179">Het geldige waardenbereik is 8 tot en met 32.</span><span class="sxs-lookup"><span data-stu-id="29ee0-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="29ee0-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="29ee0-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="29ee0-181">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-182">Hiermee geeft u het aantal seconden dat IntelliSense wordt gebruikt om op te lossen van de momenteel getypte tekst.</span><span class="sxs-lookup"><span data-stu-id="29ee0-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="29ee0-183">Na dit aantal seconden, IntelliSense een time-out optreedt en kunt u verder kunt typen.</span><span class="sxs-lookup"><span data-stu-id="29ee0-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="29ee0-184">De standaardwaarde is 3 seconden.</span><span class="sxs-lookup"><span data-stu-id="29ee0-184">The default value is 3 seconds.</span></span> <span data-ttu-id="29ee0-185">De waarde is een geheel getal zijn.</span><span class="sxs-lookup"><span data-stu-id="29ee0-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="29ee0-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="29ee0-186">MruCount</span></span>

<span data-ttu-id="29ee0-187">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-188">Hiermee geeft u het aantal onlangs geopende bestanden met Windows PowerShell ISE worden bijgehouden en worden weergegeven aan de onderkant van de **bestand openen** menu.</span><span class="sxs-lookup"><span data-stu-id="29ee0-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="29ee0-189">De standaardwaarde is 10.</span><span class="sxs-lookup"><span data-stu-id="29ee0-189">The default value is 10.</span></span> <span data-ttu-id="29ee0-190">De waarde is een geheel getal zijn.</span><span class="sxs-lookup"><span data-stu-id="29ee0-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="29ee0-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="29ee0-192">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29ee0-193">Zie voor latere versies [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29ee0-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="29ee0-194">De lezen/schrijven-eigenschap die opgehaald of ingesteld van de achtergrondkleur van het deelvenster Uitvoer zelf.</span><span class="sxs-lookup"><span data-stu-id="29ee0-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="29ee0-195">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="29ee0-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="29ee0-197">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29ee0-198">Zie voor latere versies [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29ee0-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="29ee0-199">De lezen/schrijven-eigenschap die de voorgrondkleur van de tekst in het deelvenster Uitvoer in Windows PowerShell ISE 2.0 wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="29ee0-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="29ee0-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="29ee0-201">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="29ee0-202">Zie voor latere versies [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="29ee0-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="29ee0-203">De lezen/schrijven-eigenschap die de achtergrondkleur van de tekst in het deelvenster Uitvoer wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="29ee0-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="29ee0-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="29ee0-205">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-206">De lezen/schrijven-eigenschap die opgehaald of ingesteld van de achtergrondkleur voor bestanden.</span><span class="sxs-lookup"><span data-stu-id="29ee0-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="29ee0-207">Het is een exemplaar van de **System.Windows.Media.Color** klasse.</span><span class="sxs-lookup"><span data-stu-id="29ee0-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="29ee0-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="29ee0-209">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-210">De lezen/schrijven-eigenschap die opgehaald of ingesteld van de voorgrondkleur voor niet-scriptbestanden in het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="29ee0-211">Als u wilt de voorgrondkleur voor scriptbestanden, gebruikt de [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="29ee0-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="29ee0-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="29ee0-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="29ee0-213">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-214">De lezen/schrijven-eigenschap die opgehaald of ingesteld van de positie van het scriptvenster op het scherm.</span><span class="sxs-lookup"><span data-stu-id="29ee0-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="29ee0-215">De tekenreeks mag 'Gemaximaliseerd', 'Top' of 'Chterkant'.</span><span class="sxs-lookup"><span data-stu-id="29ee0-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="29ee0-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="29ee0-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="29ee0-217">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-218">Hiermee geeft u op of de **CTRL + J** lijst met fragmenten bevat de set met starter die is opgenomen in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29ee0-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="29ee0-219">Als de waarde **$false**, alleen door de gebruiker gedefinieerde fragmenten worden weergegeven in de **CTRL + J** lijst.</span><span class="sxs-lookup"><span data-stu-id="29ee0-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="29ee0-220">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-220">The default value is **$true**.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="29ee0-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="29ee0-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="29ee0-222">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-223">Hiermee geeft u op of IntelliSense syntaxis van de parameter en waarde suggesties in het consolevenster biedt.</span><span class="sxs-lookup"><span data-stu-id="29ee0-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="29ee0-224">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-224">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="29ee0-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="29ee0-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="29ee0-226">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-227">Hiermee geeft u op of IntelliSense syntaxis van de parameter en waarde suggesties in het scriptvenster biedt.</span><span class="sxs-lookup"><span data-stu-id="29ee0-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="29ee0-228">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-228">The default value is **$true**.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="29ee0-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="29ee0-229">ShowLineNumbers</span></span>

<span data-ttu-id="29ee0-230">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-231">Hiermee geeft u op of het scriptvenster regelnummers in de linkermarge weergeeft.</span><span class="sxs-lookup"><span data-stu-id="29ee0-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="29ee0-232">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-232">The default value is **$true**.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="29ee0-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="29ee0-233">ShowOutlining</span></span>

<span data-ttu-id="29ee0-234">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-235">Hiermee geeft u op of het scriptvenster worden uitgevouwen en samengevouwen tussen haakjes naast de gedeelten van de code in de linkermarge weergegeven.</span><span class="sxs-lookup"><span data-stu-id="29ee0-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="29ee0-236">Wanneer ze worden weergegeven, kunt u het minteken \( - \) pictogrammen naast een blok tekst wilt samenvouwen of klik op het plusteken \( + \) pictogram om uit te breiden van een blok tekst.</span><span class="sxs-lookup"><span data-stu-id="29ee0-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="29ee0-237">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-237">The default value is **$true**.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="29ee0-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="29ee0-238">ShowToolBar</span></span>

<span data-ttu-id="29ee0-239">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-240">Hiermee geeft u op of de ISE-werkbalk aan de bovenkant van de Windows PowerShell ISE-venster wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="29ee0-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="29ee0-241">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-241">The default value is **$true**.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="29ee0-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="29ee0-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="29ee0-243">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-244">Hiermee geeft u op of er een waarschuwingsbericht wordt weergegeven wanneer een script automatisch opgeslagen wordt voordat deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="29ee0-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="29ee0-245">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-245">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="29ee0-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="29ee0-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="29ee0-247">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-248">Hiermee geeft u op of een waarschuwing wordt weergegeven als hetzelfde bestand wordt geopend in de verschillende tabbladen van PowerShell.</span><span class="sxs-lookup"><span data-stu-id="29ee0-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="29ee0-249">Indien ingesteld op **$true**, hetzelfde bestand openen in meerdere tabbladen toont dit bericht: "Een kopie van dit bestand is geopend in een andere Windows PowerShell-tabblad. Wijzigingen in dit bestand heeft invloed op alle geopende exemplaren."</span><span class="sxs-lookup"><span data-stu-id="29ee0-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="29ee0-250">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-250">The default value is **$true**.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="29ee0-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="29ee0-251">TokenColors</span></span>

<span data-ttu-id="29ee0-252">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-253">Hiermee geeft u de kleuren van de tokens IntelliSense in het deelvenster met Windows PowerShell ISE-Script.</span><span class="sxs-lookup"><span data-stu-id="29ee0-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="29ee0-254">Deze eigenschap is een dictionary-object met de naam/waarde-paren van de typen tokens en kleuren voor het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="29ee0-255">Zie het wijzigen van de kleuren van de tokens IntelliSense in het consolevenster [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="29ee0-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="29ee0-256">Als u de kleuren op de standaardwaarden herstellen, Zie [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="29ee0-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="29ee0-257">Token kleuren kunnen worden ingesteld voor het volgende: Kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, nieuwe regel, getal, Operator, positie, StatementSeparator, String, Type, onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="29ee0-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="29ee0-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="29ee0-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="29ee0-259">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-260">Hiermee geeft u op of u de Enter-toets gebruiken kunt om te selecteren van een opgegeven optie in het consolevenster IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="29ee0-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="29ee0-261">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-261">The default value is **$true**.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="29ee0-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="29ee0-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="29ee0-263">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-264">Hiermee geeft u op of u de Enter-toets gebruiken kunt om een IntelliSense-opgegeven optie in het scriptvenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="29ee0-265">De standaardwaarde is **$true**.</span><span class="sxs-lookup"><span data-stu-id="29ee0-265">The default value is **$true**.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="29ee0-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="29ee0-266">UseLocalHelp</span></span>

<span data-ttu-id="29ee0-267">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-268">Hiermee geeft u op of de lokaal geïnstalleerde Help of de online Help van TechNet-bibliotheek wordt weergegeven wanneer u de cursor in een trefwoord op F1 drukt.</span><span class="sxs-lookup"><span data-stu-id="29ee0-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="29ee0-269">Indien ingesteld op **$true**, en vervolgens een pop-upvenster uit de lokaal geïnstalleerde Help-inhoud bevat.</span><span class="sxs-lookup"><span data-stu-id="29ee0-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="29ee0-270">U kunt de Help-bestanden installeren door het uitvoeren van de `Update-Help` opdracht.</span><span class="sxs-lookup"><span data-stu-id="29ee0-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="29ee0-271">Indien ingesteld op **$false**, en vervolgens uw browser wordt geopend op een pagina in de TechNet-bibliotheek.</span><span class="sxs-lookup"><span data-stu-id="29ee0-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="29ee0-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="29ee0-273">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-274">Hiermee geeft u de achtergrondkleur voor uitgebreide tekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="29ee0-275">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="29ee0-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="29ee0-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-276">VerboseForegroundColor</span></span>

<span data-ttu-id="29ee0-277">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-278">Hiermee geeft u de voorgrondkleur voor uitgebreide tekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="29ee0-279">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="29ee0-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="29ee0-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-280">WarningBackgroundColor</span></span>

<span data-ttu-id="29ee0-281">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-282">Hiermee geeft u de achtergrondkleur voor waarschuwingstekst die wordt weergegeven in het consolevenster.</span><span class="sxs-lookup"><span data-stu-id="29ee0-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="29ee0-283">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="29ee0-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="29ee0-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="29ee0-284">WarningForegroundColor</span></span>

<span data-ttu-id="29ee0-285">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29ee0-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="29ee0-286">Hiermee geeft u de voorgrondkleur voor waarschuwingstekst die wordt weergegeven in het deelvenster Uitvoer.</span><span class="sxs-lookup"><span data-stu-id="29ee0-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="29ee0-287">Het is een **System.Windows.Media.Color** object.</span><span class="sxs-lookup"><span data-stu-id="29ee0-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="29ee0-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="29ee0-288">XmlTokenColors</span></span>

<span data-ttu-id="29ee0-289">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-290">Hiermee geeft u een dictionary-object met de naam/waarde-paren van de typen tokens en kleuren voor XML-inhoud die wordt weergegeven in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="29ee0-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="29ee0-291">Token kleuren kunnen worden ingesteld voor het volgende: Kenmerk, opdracht, CommandArgument, CommandParameter, opmerking, GroupEnd, GroupStart, sleutelwoord, LineContinuation, LoopLabel, lid, nieuwe regel, getal, Operator, positie, StatementSeparator, String, Type, onbekend, variabele.</span><span class="sxs-lookup"><span data-stu-id="29ee0-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="29ee0-292">Zie ook [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="29ee0-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="29ee0-293">Uitzoomen</span><span class="sxs-lookup"><span data-stu-id="29ee0-293">Zoom</span></span>

<span data-ttu-id="29ee0-294">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="29ee0-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="29ee0-295">Hiermee geeft u de relatieve grootte van de tekst in de Console en het Script deelvensters.</span><span class="sxs-lookup"><span data-stu-id="29ee0-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="29ee0-296">De standaardwaarde is 100.</span><span class="sxs-lookup"><span data-stu-id="29ee0-296">The default value is 100.</span></span> <span data-ttu-id="29ee0-297">Lagere waarden ertoe leiden dat de tekst in Windows PowerShell ISE kleinere weergegeven terwijl groot ertoe leiden dat de tekst groter worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="29ee0-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="29ee0-298">De waarde is een geheel getal met een bereik van 20 tot 400.</span><span class="sxs-lookup"><span data-stu-id="29ee0-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="29ee0-299">Zie ook</span><span class="sxs-lookup"><span data-stu-id="29ee0-299">See Also</span></span>

- [<span data-ttu-id="29ee0-300">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="29ee0-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="29ee0-301">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="29ee0-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)