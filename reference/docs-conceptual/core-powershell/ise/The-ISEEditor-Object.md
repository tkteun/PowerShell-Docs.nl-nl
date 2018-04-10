---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEEditor-object
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="ecd85-103">Het ISEEditor-object</span><span class="sxs-lookup"><span data-stu-id="ecd85-103">The ISEEditor Object</span></span>

<span data-ttu-id="ecd85-104">Een **ISEEditor** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="ecd85-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="ecd85-105">Het consolevenster is een **ISEEditor** object.</span><span class="sxs-lookup"><span data-stu-id="ecd85-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="ecd85-106">Elke [ISEFile](The-ISEFile-Object.md) -object heeft een bijbehorende **ISEEditor** object.</span><span class="sxs-lookup"><span data-stu-id="ecd85-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="ecd85-107">De volgende secties worden de methoden en eigenschappen van een **ISEEditor** object.</span><span class="sxs-lookup"><span data-stu-id="ecd85-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="ecd85-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="ecd85-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="ecd85-109">Wissen\(\)</span><span class="sxs-lookup"><span data-stu-id="ecd85-109">Clear\(\)</span></span>

<span data-ttu-id="ecd85-110">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-111">Hiermee wist u de tekst in de editor.</span><span class="sxs-lookup"><span data-stu-id="ecd85-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="ecd85-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="ecd85-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="ecd85-113">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-114">De editor schuift zodat de regel die overeenkomt met de opgegeven **lineNumber** parameterwaarde zichtbaar is.</span><span class="sxs-lookup"><span data-stu-id="ecd85-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="ecd85-115">Het genereert een uitzondering als het opgegeven regelnummer valt buiten het bereik van 1, laatste regelnummer, waarmee de geldige regelnummers zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="ecd85-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="ecd85-116">**lineNumber** het nummer van de regel die moet zichtbaar worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ecd85-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="ecd85-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="ecd85-117">Focus\(\)</span></span>

<span data-ttu-id="ecd85-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-119">Hiermee stelt u de focus naar de editor.</span><span class="sxs-lookup"><span data-stu-id="ecd85-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="ecd85-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="ecd85-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="ecd85-121">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-122">Hiermee wordt de lengte van de als een geheel getal voor de regel die is opgegeven door het regelnummer.</span><span class="sxs-lookup"><span data-stu-id="ecd85-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="ecd85-123">**lineNumber** het nummer van de regel waarvan de lengte ophalen.</span><span class="sxs-lookup"><span data-stu-id="ecd85-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="ecd85-124">**Retourneert** de lengte van de regels voor de regel aan het opgegeven regelnummer.</span><span class="sxs-lookup"><span data-stu-id="ecd85-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="ecd85-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="ecd85-125">GoToMatch\(\)</span></span>

<span data-ttu-id="ecd85-126">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="ecd85-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="ecd85-127">De caret verplaatst naar het overeenkomende teken als de **CanGoToMatch** eigenschap van de editor-object is **$true**, die wordt weergegeven wanneer de caret direct vóór een openingshaakje, een accolade of haakje - \(,\[, {- of direct na een sluithaakje, een accolade of haakje - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="ecd85-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="ecd85-128">De caret wordt geplaatst voor een teken openen of na een teken sluiten.</span><span class="sxs-lookup"><span data-stu-id="ecd85-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="ecd85-129">Als de **CanGoToMatch** eigenschap is **$false**, en vervolgens deze methode geen effect.</span><span class="sxs-lookup"><span data-stu-id="ecd85-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="ecd85-130">InsertText\( tekst \)</span><span class="sxs-lookup"><span data-stu-id="ecd85-130">InsertText\( text \)</span></span>

<span data-ttu-id="ecd85-131">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-132">De selectie vervangen door de tekst of tekst op de huidige invoegpositie ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="ecd85-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="ecd85-133">**tekst** -tekenreeks van de tekst om in te voegen.</span><span class="sxs-lookup"><span data-stu-id="ecd85-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="ecd85-134">Zie de [voorbeeld Scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="ecd85-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="ecd85-135">Selecteer\( beginregel, beginkolom, eindregel, eindkolom \)</span><span class="sxs-lookup"><span data-stu-id="ecd85-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="ecd85-136">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-137">Hiermee selecteert u de tekst van de **beginregel**, **beginkolom**, **eindregel**, en **eindkolom** parameters.</span><span class="sxs-lookup"><span data-stu-id="ecd85-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="ecd85-138">**Beginregel** -geheel getal van de regel waarbij de selectie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="ecd85-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="ecd85-139">**Beginkolom** -geheel getal van de kolom in de begin-regel waarbij de selectie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="ecd85-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="ecd85-140">**endLine** -geheel getal van de regel waar de selectie eindigt.</span><span class="sxs-lookup"><span data-stu-id="ecd85-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="ecd85-141">**eindkolom** -geheel getal van de kolom in de end-regel waar de selectie eindigt.</span><span class="sxs-lookup"><span data-stu-id="ecd85-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="ecd85-142">Zie de [voorbeeld Scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="ecd85-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="ecd85-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="ecd85-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="ecd85-144">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-145">De volledige regel van de tekst die momenteel de caret bevat selecteert.</span><span class="sxs-lookup"><span data-stu-id="ecd85-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="ecd85-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="ecd85-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="ecd85-147">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-148">Hiermee stelt u de invoegpositie op het regelnummer en nummer van de kolom.</span><span class="sxs-lookup"><span data-stu-id="ecd85-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="ecd85-149">Het genereert een uitzondering als het regelnummer caret of het kolomnummer caret aanwezig buiten hun respectieve geldig bereiken zijn.</span><span class="sxs-lookup"><span data-stu-id="ecd85-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="ecd85-150">**lineNumber** -Integer het regelnummer caret.</span><span class="sxs-lookup"><span data-stu-id="ecd85-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="ecd85-151">**columnNumber** -het kolomnummer caret geheel getal zijn.</span><span class="sxs-lookup"><span data-stu-id="ecd85-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="ecd85-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="ecd85-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="ecd85-153">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="ecd85-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="ecd85-154">Zorgt ervoor dat alle overzichtssecties wilt uitvouwen of samenvouwen.</span><span class="sxs-lookup"><span data-stu-id="ecd85-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="ecd85-155">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ecd85-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="ecd85-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="ecd85-156">CanGoToMatch</span></span>

<span data-ttu-id="ecd85-157">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="ecd85-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="ecd85-158">De alleen-lezen Boole-eigenschap om aan te geven of de caret naast een haakje-openen, een accolade of haakje - \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="ecd85-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="ecd85-159">Als de caret direct vóór het teken dat openen of direct na het teken van het sluiten van een paar, wordt de waarde van deze eigenschap **$true**.</span><span class="sxs-lookup"><span data-stu-id="ecd85-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="ecd85-160">Anders is de **$false**.</span><span class="sxs-lookup"><span data-stu-id="ecd85-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="ecd85-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="ecd85-161">CaretColumn</span></span>

<span data-ttu-id="ecd85-162">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-163">De alleen-lezen eigenschap die het kolomnummer opgehaald die overeenkomt met de positie van de caret.</span><span class="sxs-lookup"><span data-stu-id="ecd85-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="ecd85-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="ecd85-164">CaretLine</span></span>

<span data-ttu-id="ecd85-165">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-166">De alleen-lezen eigenschap die het nummer van de regel met de caret opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ecd85-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="ecd85-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="ecd85-167">CaretLineText</span></span>

<span data-ttu-id="ecd85-168">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-169">De alleen-lezen eigenschap die de volledige regel van de tekst waarin de caret opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ecd85-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="ecd85-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="ecd85-170">LineCount</span></span>

<span data-ttu-id="ecd85-171">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-172">De alleen-lezen eigenschap die het aantal regels opgehaald van de editor.</span><span class="sxs-lookup"><span data-stu-id="ecd85-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="ecd85-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="ecd85-173">SelectedText</span></span>

<span data-ttu-id="ecd85-174">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-175">De alleen-lezen eigenschap die de geselecteerde tekst opgehaald van de editor.</span><span class="sxs-lookup"><span data-stu-id="ecd85-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="ecd85-176">Zie de [voorbeeld Scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="ecd85-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="ecd85-177">Tekst</span><span class="sxs-lookup"><span data-stu-id="ecd85-177">Text</span></span>

<span data-ttu-id="ecd85-178">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ecd85-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ecd85-179">De eigenschap lezen/schrijven die opgehaald of ingesteld van de tekst in de editor.</span><span class="sxs-lookup"><span data-stu-id="ecd85-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="ecd85-180">Zie de [voorbeeld Scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="ecd85-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="ecd85-181">Voorbeeld Scripting</span><span class="sxs-lookup"><span data-stu-id="ecd85-181">Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="ecd85-182">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ecd85-182">See Also</span></span>

- [<span data-ttu-id="ecd85-183">Het Object ISEFile</span><span class="sxs-lookup"><span data-stu-id="ecd85-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="ecd85-184">Het Object PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="ecd85-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="ecd85-185">Doel van de Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="ecd85-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ecd85-186">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="ecd85-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)