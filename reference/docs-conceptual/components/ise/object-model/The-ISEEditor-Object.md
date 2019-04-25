---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEEditor-object
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086762"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="046cd-103">Het ISEEditor-object</span><span class="sxs-lookup"><span data-stu-id="046cd-103">The ISEEditor Object</span></span>

<span data-ttu-id="046cd-104">Een **ISEEditor** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="046cd-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="046cd-105">Het consolevenster wordt een **ISEEditor** object.</span><span class="sxs-lookup"><span data-stu-id="046cd-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="046cd-106">Elke [ISEFile](The-ISEFile-Object.md) object heeft een bijbehorende **ISEEditor** object.</span><span class="sxs-lookup"><span data-stu-id="046cd-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="046cd-107">De volgende secties worden de methoden en eigenschappen van een **ISEEditor** object.</span><span class="sxs-lookup"><span data-stu-id="046cd-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="046cd-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="046cd-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="046cd-109">Wissen\(\)</span><span class="sxs-lookup"><span data-stu-id="046cd-109">Clear\(\)</span></span>

<span data-ttu-id="046cd-110">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-111">Hiermee schakelt u de tekst in de editor.</span><span class="sxs-lookup"><span data-stu-id="046cd-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="046cd-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="046cd-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="046cd-113">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-114">De editor schuift, zodat de regel die overeenkomt met de opgegeven **lineNumber** parameterwaarde zichtbaar is.</span><span class="sxs-lookup"><span data-stu-id="046cd-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="046cd-115">Dit genereert een uitzondering als het opgegeven regelnummer ligt buiten het bereik van 1, laatste regelnummer waarin de geldige regelnummers zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="046cd-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="046cd-116">**lineNumber** het nummer van de regel die moet zichtbaar worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="046cd-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="046cd-117">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="046cd-117">Focus\(\)</span></span>

<span data-ttu-id="046cd-118">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-119">De focus ingesteld op de editor.</span><span class="sxs-lookup"><span data-stu-id="046cd-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="046cd-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="046cd-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="046cd-121">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-122">Hiermee haalt u de regellengte van de als een geheel getal voor de regel die is opgegeven door het regelnummer.</span><span class="sxs-lookup"><span data-stu-id="046cd-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="046cd-123">**lineNumber** het nummer van de regel voor het verzamelen van de lengte.</span><span class="sxs-lookup"><span data-stu-id="046cd-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="046cd-124">**Retourneert** de lengte van de lijn voor de regel op de opgegeven regelnummer.</span><span class="sxs-lookup"><span data-stu-id="046cd-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="046cd-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="046cd-125">GoToMatch\(\)</span></span>

<span data-ttu-id="046cd-126">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="046cd-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="046cd-127">Het caret-teken verplaatst naar de overeenkomende teken als de **CanGoToMatch** eigenschap van het editor-object is **$true**, die wordt weergegeven wanneer het caret-teken vóór een openingshaakje, haakje of accolade - \(,\[, {- of onmiddellijk nadat een haakje-sluiten, haakje of accolade - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="046cd-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="046cd-128">Het caret-teken wordt geplaatst voor een teken openen of na een haakje-teken.</span><span class="sxs-lookup"><span data-stu-id="046cd-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="046cd-129">Als de **CanGoToMatch** eigenschap **$false**, en vervolgens deze methode, er niets gebeurt.</span><span class="sxs-lookup"><span data-stu-id="046cd-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="046cd-130">InsertText\( tekst \)</span><span class="sxs-lookup"><span data-stu-id="046cd-130">InsertText\( text \)</span></span>

<span data-ttu-id="046cd-131">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-132">De selectie vervangen door de tekst of tekst ingevoegd op de positie van de huidige caret-teken.</span><span class="sxs-lookup"><span data-stu-id="046cd-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="046cd-133">**tekst** -tekenreeks van de tekst om in te voegen.</span><span class="sxs-lookup"><span data-stu-id="046cd-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="046cd-134">Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="046cd-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="046cd-135">Selecteer\( beginregel, beginkolom, eindregel, eindkolom \)</span><span class="sxs-lookup"><span data-stu-id="046cd-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="046cd-136">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-137">Hiermee selecteert u de tekst van de **beginregel**, **startColumn**, **eindregel**, en **eindkolom** parameters.</span><span class="sxs-lookup"><span data-stu-id="046cd-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="046cd-138">**Beginregel** -geheel getal van de regel waar de selectie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="046cd-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="046cd-139">**startColumn** -geheel getal van de kolom in de begin-regel waarbij de selectie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="046cd-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="046cd-140">**eindregel** -geheel getal van de regel waar de selectie eindigt.</span><span class="sxs-lookup"><span data-stu-id="046cd-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="046cd-141">**eindkolom** -geheel getal van de kolom in de end-regel waar de selectie eindigt.</span><span class="sxs-lookup"><span data-stu-id="046cd-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="046cd-142">Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="046cd-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="046cd-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="046cd-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="046cd-144">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-145">Hiermee selecteert u de volledige regel van de tekst die momenteel het caret-teken bevat.</span><span class="sxs-lookup"><span data-stu-id="046cd-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="046cd-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="046cd-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="046cd-147">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-148">Hiermee stelt u de invoegpositie aan het regelnummer en het nummer van de kolom.</span><span class="sxs-lookup"><span data-stu-id="046cd-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="046cd-149">Dit genereert een uitzondering als het regelnummer caret-teken of het caret-teken kolomnummer buiten hun respectieve geldige bereiken.</span><span class="sxs-lookup"><span data-stu-id="046cd-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="046cd-150">**lineNumber** -geheel getal zijn het regelnummer caret-teken.</span><span class="sxs-lookup"><span data-stu-id="046cd-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="046cd-151">**columnNumber** -geheel getal zijn de kolomnummer caret-teken.</span><span class="sxs-lookup"><span data-stu-id="046cd-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="046cd-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="046cd-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="046cd-153">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="046cd-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="046cd-154">Zorgt ervoor dat de omtrek secties uitvouwen of samenvouwen.</span><span class="sxs-lookup"><span data-stu-id="046cd-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="046cd-155">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="046cd-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="046cd-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="046cd-156">CanGoToMatch</span></span>

<span data-ttu-id="046cd-157">Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="046cd-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="046cd-158">De Booleaanse eigenschap alleen-lezen om aan te geven of het caret-teken naast een haakje, haakje of accolade - \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="046cd-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="046cd-159">Als het caret-teken direct vóór het teken openen of direct na het haakje-teken van een paar is, wordt de waarde van deze eigenschap **$true**.</span><span class="sxs-lookup"><span data-stu-id="046cd-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="046cd-160">Anders is het **$false**.</span><span class="sxs-lookup"><span data-stu-id="046cd-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="046cd-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="046cd-161">CaretColumn</span></span>

<span data-ttu-id="046cd-162">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-163">De alleen-lezen eigenschap die het nummer van de kolom opgehaald die overeenkomt met de positie van het caret-teken.</span><span class="sxs-lookup"><span data-stu-id="046cd-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="046cd-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="046cd-164">CaretLine</span></span>

<span data-ttu-id="046cd-165">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-166">De alleen-lezen eigenschap waarmee het nummer van de regel met het caret-teken worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="046cd-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="046cd-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="046cd-167">CaretLineText</span></span>

<span data-ttu-id="046cd-168">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-169">De alleen-lezen eigenschap die krijgt de volledige regel tekst op waarmee het caret-teken bevat.</span><span class="sxs-lookup"><span data-stu-id="046cd-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="046cd-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="046cd-170">LineCount</span></span>

<span data-ttu-id="046cd-171">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-172">De alleen-lezen eigenschap die het aantal regels opgehaald van de editor.</span><span class="sxs-lookup"><span data-stu-id="046cd-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="046cd-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="046cd-173">SelectedText</span></span>

<span data-ttu-id="046cd-174">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-175">De alleen-lezen eigenschap die de geselecteerde tekst in de editor wordt.</span><span class="sxs-lookup"><span data-stu-id="046cd-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="046cd-176">Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="046cd-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="046cd-177">Tekst</span><span class="sxs-lookup"><span data-stu-id="046cd-177">Text</span></span>

<span data-ttu-id="046cd-178">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="046cd-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="046cd-179">De lezen/schrijven-eigenschap die opgehaald of ingesteld van de tekst in de editor.</span><span class="sxs-lookup"><span data-stu-id="046cd-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="046cd-180">Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="046cd-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="046cd-181">Voorbeeld van het uitvoeren van scripts</span><span class="sxs-lookup"><span data-stu-id="046cd-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="046cd-182">Zie ook</span><span class="sxs-lookup"><span data-stu-id="046cd-182">See Also</span></span>

- [<span data-ttu-id="046cd-183">Het ISEFile-Object</span><span class="sxs-lookup"><span data-stu-id="046cd-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="046cd-184">The PowerShellTab Object</span><span class="sxs-lookup"><span data-stu-id="046cd-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="046cd-185">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="046cd-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="046cd-186">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="046cd-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)