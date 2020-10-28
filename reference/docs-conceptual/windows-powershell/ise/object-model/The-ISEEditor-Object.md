---
ms.date: 12/31/2019
title: Het ISEEditor-object
description: Een ISEEditor-object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEEditor. Het console venster is een ISEEditor-object.
ms.openlocfilehash: ffcb6e35e1160beab6efb29cc84847fa9ffd012b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654061"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="eef6d-104">Het ISEEditor-object</span><span class="sxs-lookup"><span data-stu-id="eef6d-104">The ISEEditor Object</span></span>

<span data-ttu-id="eef6d-105">Een **ISEEditor** -object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="eef6d-105">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="eef6d-106">Het console venster is een **ISEEditor** -object.</span><span class="sxs-lookup"><span data-stu-id="eef6d-106">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="eef6d-107">Elk [ISEFile](The-ISEFile-Object.md) -object heeft een bijbehorend **ISEEditor** -object.</span><span class="sxs-lookup"><span data-stu-id="eef6d-107">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="eef6d-108">In de volgende secties worden de methoden en eigenschappen van een **ISEEditor** -object vermeld.</span><span class="sxs-lookup"><span data-stu-id="eef6d-108">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="eef6d-109">Methoden</span><span class="sxs-lookup"><span data-stu-id="eef6d-109">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="eef6d-110">Maak\(\)</span><span class="sxs-lookup"><span data-stu-id="eef6d-110">Clear\(\)</span></span>

<span data-ttu-id="eef6d-111">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-112">Hiermee wordt de tekst in de editor gewist.</span><span class="sxs-lookup"><span data-stu-id="eef6d-112">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="eef6d-113">EnsureVisible \( int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="eef6d-113">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="eef6d-114">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-115">Schuift de editor zodat de regel die overeenkomt met de opgegeven waarde voor de para meter **lineNumber** zichtbaar is.</span><span class="sxs-lookup"><span data-stu-id="eef6d-115">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="eef6d-116">Er wordt een uitzonde ring gegenereerd als het opgegeven regel nummer zich buiten het bereik van 1, laatste regel nummer bevindt dat de geldige regel nummers definieert.</span><span class="sxs-lookup"><span data-stu-id="eef6d-116">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="eef6d-117">**lineNumber** Het nummer van de regel die zichtbaar moet worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="eef6d-117">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="eef6d-118">Focus\(\)</span><span class="sxs-lookup"><span data-stu-id="eef6d-118">Focus\(\)</span></span>

<span data-ttu-id="eef6d-119">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-120">Hiermee stelt u de focus naar de editor.</span><span class="sxs-lookup"><span data-stu-id="eef6d-120">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="eef6d-121">GetLineLength \( int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="eef6d-121">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="eef6d-122">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-123">Hiermee wordt de lijn lengte opgehaald als een geheel getal voor de regel die wordt opgegeven met het regel nummer.</span><span class="sxs-lookup"><span data-stu-id="eef6d-123">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="eef6d-124">**lineNumber** Het nummer van de regel waarvan de lengte moet worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="eef6d-124">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="eef6d-125">**Retourneert** De regel lengte voor de regel op het opgegeven regel nummer.</span><span class="sxs-lookup"><span data-stu-id="eef6d-125">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="eef6d-126">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="eef6d-126">GoToMatch\(\)</span></span>

<span data-ttu-id="eef6d-127">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="eef6d-127">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="eef6d-128">Hiermee wordt het caret naar het overeenkomende teken verplaatst als de eigenschap **CanGoToMatch** van het object editor `$true` , die optreedt wanneer het caret direct vóór een haakje openen, een haakje sluiten of `(` een accolade, `[` ,, `{` of direct na een haakje, een haakje of een accolade `)` - `]` , `}` , wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="eef6d-128">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="eef6d-129">Het caret wordt geplaatst vóór een openings teken of na een afsluitend teken.</span><span class="sxs-lookup"><span data-stu-id="eef6d-129">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="eef6d-130">Als de eigenschap **CanGoToMatch** is `$false` , heeft deze methode niets.</span><span class="sxs-lookup"><span data-stu-id="eef6d-130">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="eef6d-131">InsertText- \( tekst \)</span><span class="sxs-lookup"><span data-stu-id="eef6d-131">InsertText\( text \)</span></span>

<span data-ttu-id="eef6d-132">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-133">Hiermee wordt de selectie vervangen door tekst of wordt tekst ingevoegd op de huidige invoeg positie.</span><span class="sxs-lookup"><span data-stu-id="eef6d-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="eef6d-134">**tekst** teken reeks die moet worden ingevoegd in de tekst.</span><span class="sxs-lookup"><span data-stu-id="eef6d-134">**text** - String The text to insert.</span></span>

<span data-ttu-id="eef6d-135">Zie het [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="eef6d-135">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="eef6d-136">Selecteer \( startLine, start column, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="eef6d-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="eef6d-137">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-138">Hiermee selecteert u de tekst van de para meters **startLine** , start **Column** , **endLine** en **endColumn** .</span><span class="sxs-lookup"><span data-stu-id="eef6d-138">Selects the text from the **startLine** , **startColumn** , **endLine** , and **endColumn** parameters.</span></span>

<span data-ttu-id="eef6d-139">**startLine** : de regel waar de selectie wordt gestart geheel getal.</span><span class="sxs-lookup"><span data-stu-id="eef6d-139">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="eef6d-140">Start **Column** : een geheel getal voor de kolom in de begin regel waar de selectie wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="eef6d-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="eef6d-141">**endLine** : de regel waar de selectie eindigt.</span><span class="sxs-lookup"><span data-stu-id="eef6d-141">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="eef6d-142">**endColumn** : Hiermee wordt de kolom in de eind regel waarvan de selectie eindigt, geheel getal.</span><span class="sxs-lookup"><span data-stu-id="eef6d-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="eef6d-143">Zie het  [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="eef6d-143">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="eef6d-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="eef6d-144">SelectCaretLine\(\)</span></span>

<span data-ttu-id="eef6d-145">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-146">Hiermee wordt de volledige tekst regel geselecteerd die het caret-teken bevat.</span><span class="sxs-lookup"><span data-stu-id="eef6d-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="eef6d-147">SetCaretPosition \( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="eef6d-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="eef6d-148">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-149">Hiermee wordt de positie van het invoeg teken ingesteld op het regel nummer en het kolom nummer.</span><span class="sxs-lookup"><span data-stu-id="eef6d-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="eef6d-150">Er wordt een uitzonde ring gegenereerd als het regel nummer van het caret-of het kolom nummer van de caret uit de respectieve geldige bereiken valt.</span><span class="sxs-lookup"><span data-stu-id="eef6d-150">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="eef6d-151">**lineNumber** : een geheel getal voor het regel nummer caret.</span><span class="sxs-lookup"><span data-stu-id="eef6d-151">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="eef6d-152">**columnNumber** : een geheel getal voor het kolom nummer van de caret.</span><span class="sxs-lookup"><span data-stu-id="eef6d-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="eef6d-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="eef6d-153">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="eef6d-154">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="eef6d-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="eef6d-155">Zorgt ervoor dat alle overzichts secties uit-of samen vouwen.</span><span class="sxs-lookup"><span data-stu-id="eef6d-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="eef6d-156">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="eef6d-156">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="eef6d-157">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="eef6d-157">CanGoToMatch</span></span>

<span data-ttu-id="eef6d-158">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="eef6d-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="eef6d-159">De alleen-lezen Booleaanse eigenschap om aan te geven of het caret naast een haakje, een haakje of een accolade-,-,-,-,-,-,-,-, `()` `[]` `{}` .</span><span class="sxs-lookup"><span data-stu-id="eef6d-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="eef6d-160">Als het caret direct vóór het begin teken of direct na het afsluitende teken van een paar staat, is deze eigenschaps waarde `$true` .</span><span class="sxs-lookup"><span data-stu-id="eef6d-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="eef6d-161">Anders is dit `$false` .</span><span class="sxs-lookup"><span data-stu-id="eef6d-161">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="eef6d-162">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="eef6d-162">CaretColumn</span></span>

<span data-ttu-id="eef6d-163">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-164">De alleen-lezen eigenschap waarmee het kolom nummer wordt opgehaald dat overeenkomt met de positie van het caret-teken.</span><span class="sxs-lookup"><span data-stu-id="eef6d-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="eef6d-165">CaretLine</span><span class="sxs-lookup"><span data-stu-id="eef6d-165">CaretLine</span></span>

<span data-ttu-id="eef6d-166">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-167">De alleen-lezen eigenschap waarmee het nummer wordt opgehaald van de regel die het caret-teken bevat.</span><span class="sxs-lookup"><span data-stu-id="eef6d-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="eef6d-168">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="eef6d-168">CaretLineText</span></span>

<span data-ttu-id="eef6d-169">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-170">De alleen-lezen eigenschap waarmee de volledige regel tekst wordt opgehaald die het caret bevat.</span><span class="sxs-lookup"><span data-stu-id="eef6d-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="eef6d-171">LineCount</span><span class="sxs-lookup"><span data-stu-id="eef6d-171">LineCount</span></span>

<span data-ttu-id="eef6d-172">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-173">De alleen-lezen eigenschap waarmee het aantal regels wordt opgehaald uit de editor.</span><span class="sxs-lookup"><span data-stu-id="eef6d-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="eef6d-174">SelectedText</span><span class="sxs-lookup"><span data-stu-id="eef6d-174">SelectedText</span></span>

<span data-ttu-id="eef6d-175">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-176">De alleen-lezen eigenschap waarmee de geselecteerde tekst wordt opgehaald uit de editor.</span><span class="sxs-lookup"><span data-stu-id="eef6d-176">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="eef6d-177">Zie het  [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="eef6d-177">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="eef6d-178">Tekst</span><span class="sxs-lookup"><span data-stu-id="eef6d-178">Text</span></span>

<span data-ttu-id="eef6d-179">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="eef6d-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="eef6d-180">De eigenschap lezen/schrijven waarmee de tekst in de editor wordt opgehaald of ingesteld.</span><span class="sxs-lookup"><span data-stu-id="eef6d-180">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="eef6d-181">Zie het [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="eef6d-181">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="eef6d-182">Script voorbeeld</span><span class="sxs-lookup"><span data-stu-id="eef6d-182">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eef6d-183">Zie ook</span><span class="sxs-lookup"><span data-stu-id="eef6d-183">See Also</span></span>

- [<span data-ttu-id="eef6d-184">Het ISEFile-object</span><span class="sxs-lookup"><span data-stu-id="eef6d-184">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="eef6d-185">Het PowerShellTab-object</span><span class="sxs-lookup"><span data-stu-id="eef6d-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="eef6d-186">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="eef6d-186">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="eef6d-187">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="eef6d-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
