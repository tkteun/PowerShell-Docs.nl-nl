---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEEditor-object
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404538"
---
# <a name="the-iseeditor-object"></a>Het ISEEditor-object

Een **ISEEditor** object is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEEditor. Het consolevenster wordt een **ISEEditor** object. Elke [ISEFile](The-ISEFile-Object.md) object heeft een bijbehorende **ISEEditor** object. De volgende secties worden de methoden en eigenschappen van een **ISEEditor** object.

## <a name="methods"></a>Methoden

### <a name="clear"></a>Wissen\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee schakelt u de tekst in de editor.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De editor schuift, zodat de regel die overeenkomt met de opgegeven **lineNumber** parameterwaarde zichtbaar is. Dit genereert een uitzondering als het opgegeven regelnummer ligt buiten het bereik van 1, laatste regelnummer waarin de geldige regelnummers zijn gedefinieerd.

**lineNumber** het nummer van de regel die moet zichtbaar worden gemaakt.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Focus\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De focus ingesteld op de editor.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee haalt u de regellengte van de als een geheel getal voor de regel die is opgegeven door het regelnummer.

**lineNumber** het nummer van de regel voor het verzamelen van de lengte.

**Retourneert** de lengte van de lijn voor de regel op de opgegeven regelnummer.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Het caret-teken verplaatst naar de overeenkomende teken als de **CanGoToMatch** eigenschap van het editor-object is **$true**, die wordt weergegeven wanneer het caret-teken vóór een openingshaakje, haakje of accolade - \(,\[, {- of onmiddellijk nadat een haakje-sluiten, haakje of accolade - \),\],}.  Het caret-teken wordt geplaatst voor een teken openen of na een haakje-teken. Als de **CanGoToMatch** eigenschap **$false**, en vervolgens deze methode, er niets gebeurt.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( tekst \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De selectie vervangen door de tekst of tekst ingevoegd op de positie van de huidige caret-teken.

**tekst** -tekenreeks van de tekst om in te voegen.

Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Selecteer\( beginregel, beginkolom, eindregel, eindkolom \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee selecteert u de tekst van de **beginregel**, **startColumn**, **eindregel**, en **eindkolom** parameters.

**Beginregel** -geheel getal van de regel waar de selectie wordt gestart.

**startColumn** -geheel getal van de kolom in de begin-regel waarbij de selectie wordt gestart.

**eindregel** -geheel getal van de regel waar de selectie eindigt.

**eindkolom** -geheel getal van de kolom in de end-regel waar de selectie eindigt.

Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee selecteert u de volledige regel van de tekst die momenteel het caret-teken bevat.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Hiermee stelt u de invoegpositie aan het regelnummer en het nummer van de kolom. Dit genereert een uitzondering als het regelnummer caret-teken of het caret-teken kolomnummer buiten hun respectieve geldige bereiken.

**lineNumber** -geheel getal zijn het regelnummer caret-teken.

**columnNumber** -geheel getal zijn de kolomnummer caret-teken.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Zorgt ervoor dat de omtrek secties uitvouwen of samenvouwen.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Eigenschappen

### <a name="cangotomatch"></a>CanGoToMatch

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De Booleaanse eigenschap alleen-lezen om aan te geven of het caret-teken naast een haakje, haakje of accolade - \( \), \[ \], {}. Als het caret-teken direct vóór het teken openen of direct na het haakje-teken van een paar is, wordt de waarde van deze eigenschap **$true**. Anders is het **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die het nummer van de kolom opgehaald die overeenkomt met de positie van het caret-teken.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap waarmee het nummer van de regel met het caret-teken worden opgehaald.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die krijgt de volledige regel tekst op waarmee het caret-teken bevat.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die het aantal regels opgehaald van de editor.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de geselecteerde tekst in de editor wordt.

Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.

### <a name="text"></a>Tekst

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De lezen/schrijven-eigenschap die opgehaald of ingesteld van de tekst in de editor.

Zie de [Scripting voorbeeld](#scripting-example) verderop in dit onderwerp.

## <a name="scripting-example"></a>Voorbeeld van het uitvoeren van scripts

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

- [Het ISEFile-Object](The-ISEFile-Object.md)
- [Het PowerShellTab-Object](The-PowerShellTab-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)