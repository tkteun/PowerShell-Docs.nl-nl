---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het ISEEditor-object
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "62086762"
---
# <a name="the-iseeditor-object"></a>Het ISEEditor-object

Een **ISEEditor** -object is een exemplaar van de klasse micro soft. Power shell. host. ISE. ISEEditor. Het console venster is een **ISEEditor** -object. Elk [ISEFile](The-ISEFile-Object.md) -object heeft een bijbehorend **ISEEditor** -object. In de volgende secties worden de methoden en eigenschappen van een **ISEEditor** -object vermeld.

## <a name="methods"></a>Methoden

### <a name="clear"></a>\(\) wissen

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt de tekst in de editor gewist.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Schuift de editor zodat de regel die overeenkomt met de opgegeven waarde voor de para meter **lineNumber** zichtbaar is. Er wordt een uitzonde ring gegenereerd als het opgegeven regel nummer zich buiten het bereik van 1, laatste regel nummer bevindt dat de geldige regel nummers definieert.

**lineNumber** Het nummer van de regel die zichtbaar moet worden gemaakt.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee stelt u de focus naar de editor.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt de lijn lengte opgehaald als een geheel getal voor de regel die wordt opgegeven met het regel nummer.

**lineNumber** Het nummer van de regel waarvan de lengte moet worden opgehaald.

**Retourneert** De regel lengte voor de regel op het opgegeven regel nummer.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Hiermee verplaatst u het caret naar het overeenkomende teken als de eigenschap **CanGoToMatch** van het object editor is **$True**. dit gebeurt wanneer het caret direct vóór een haakje openen, een haakje of een accolade \(,\[, {-of direct na een haakje sluiten, een haakje of een accolade \),\]}.  Het caret wordt geplaatst vóór een openings teken of na een afsluitend teken. Als de eigenschap **CanGoToMatch** is **$False**, heeft deze methode niets.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( tekst \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt de selectie vervangen door tekst of wordt tekst ingevoegd op de huidige invoeg positie.

**tekst** teken reeks die moet worden ingevoegd in de tekst.

Zie het [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Selecteer\( startLine, start column, endLine, endColumn \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee selecteert u de tekst van de para meters **startLine**, start **Column**, **endLine**en **endColumn** .

**startLine** : de regel waar de selectie wordt gestart geheel getal.

Start **Column** : een geheel getal voor de kolom in de begin regel waar de selectie wordt gestart.

**endLine** : de regel waar de selectie eindigt.

**endColumn** : Hiermee wordt de kolom in de eind regel waarvan de selectie eindigt, geheel getal.

Zie het [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt de volledige tekst regel geselecteerd die het caret-teken bevat.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Hiermee wordt de positie van het invoeg teken ingesteld op het regel nummer en het kolom nummer. Er wordt een uitzonde ring gegenereerd als het regel nummer van het caret-of het kolom nummer van de caret uit de respectieve geldige bereiken valt.

**lineNumber** : een geheel getal voor het regel nummer caret.

**columnNumber** : een geheel getal voor het kolom nummer van de caret.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Zorgt ervoor dat alle overzichts secties uit-of samen vouwen.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Eigenschappen

### <a name="cangotomatch"></a>CanGoToMatch

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De alleen-lezen Booleaanse eigenschap om aan te geven of het caret naast een haakje, een haakje of een accolade \(\)\[\]{}. Als het caret direct vóór het begin teken of direct na het afsluitende teken van een paar staat, wordt deze eigenschaps waarde **$True**. Zo niet, dan is het **$False**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee het kolom nummer wordt opgehaald dat overeenkomt met de positie van het caret-teken.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee het nummer wordt opgehaald van de regel die het caret-teken bevat.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de volledige regel tekst wordt opgehaald die het caret bevat.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee het aantal regels wordt opgehaald uit de editor.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de geselecteerde tekst wordt opgehaald uit de editor.

Zie het [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.

### <a name="text"></a>Tekst

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De eigenschap lezen/schrijven waarmee de tekst in de editor wordt opgehaald of ingesteld.

Zie het [voor beeld van scripting](#scripting-example) verderop in dit onderwerp.

## <a name="scripting-example"></a>Script voorbeeld

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

## <a name="see-also"></a>Zie ook

- [Het ISEFile-object](The-ISEFile-Object.md)
- [Het PowerShellTab-object](The-PowerShellTab-Object.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)