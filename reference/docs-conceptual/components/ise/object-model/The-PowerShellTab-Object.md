---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het PowerShellTab-object
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 577e2aaaddf3071801816d9ae91dbf0006dd5072
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403951"
---
# <a name="the-powershelltab-object"></a>Het PowerShellTab-object

De **PowerShellTab** object vertegenwoordigt een Windows PowerShell-runtime-omgeving.

## <a name="methods"></a>Methoden

### <a name="invoke-script-"></a>Aanroepen\( Script \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Het opgegeven script wordt uitgevoerd in de PowerShell-tabblad.

> [!NOTE]
> Deze methode werkt alleen op andere tabbladen PowerShell niet het PowerShell-tabblad waaruit deze wordt uitgevoerd. Deze retourneert geen een object of de waarde. Als de code wijzigt u een variabele, klikt u vervolgens behouden de wijzigingen op het tabblad op basis waarvan u de opdracht is aangeroepen.

**Script** -System.Management.Automation.ScriptBlock of tekenreeks het scriptblok om uit te voeren.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script \[useNewScope\], millisecondsTimeout \)

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

Het opgegeven script wordt uitgevoerd in de PowerShell-tabblad.

> [!NOTE]
> Deze methode werkt alleen op andere tabbladen PowerShell niet het PowerShell-tabblad waaruit deze wordt uitgevoerd. Het scriptblok wordt uitgevoerd en een waarde die wordt geretourneerd van het script wordt geretourneerd naar de uitvoeringsomgeving van waaruit u de opdracht aangeroepen. Als de opdracht langer duurt dan de **millesecondsTimeout** waarde wordt bepaald en vervolgens de opdracht is mislukt met een uitzondering: "De bewerking is een time-out."

**Script** -System.Management.Automation.ScriptBlock of tekenreeks het scriptblok om uit te voeren.

**\[useNewScope\]**  -optionele Booleaanse die standaard **$true** indien ingesteld op **$true**, en vervolgens een nieuwe scope wordt gemaakt waarin de opdracht uit te voeren. Wijzigt de runtime-omgeving van het PowerShell-tabblad die is opgegeven door de opdracht.

**\[millisecondsTimeout\]**  -optionele geheel getal dat standaard ingesteld op **500**.
Als de opdracht niet binnen de opgegeven tijd is voltooid, wordt de opdracht genereert een **TimeoutException** met het bericht 'de bewerking is een time-out."

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a>Eigenschappen

### <a name="addonsmenu"></a>AddOnsMenu

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die Hiermee haalt u het menu invoegtoepassingen voor de PowerShell-tabblad.

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen Booleaanse eigenschap waarmee wordt geretourneerd een **$true** waarde op als een script kan worden aangeroepen met de [Invoke (Script)](#invoke-script-) methode.

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a>Consolepane

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.  In Windows PowerShell ISE 2.0 was dit de naam **CommandPane**.

De alleen-lezen eigenschap die opgehaald van het consolevenster [editor](The-ISEEditor-Object.md) object.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De lezen / schrijven-eigenschap die de tekst die wordt weergegeven op het tabblad PowerShell opgehaald of ingesteld. Standaard tabbladen zijn met de naam ' PowerShell # ', waarbij de # een getal vertegenwoordigt.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Lezen / schrijven Booleaanse eigenschap waarmee wordt bepaald of het scriptvenster wordt uitgebreid of verborgen.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Bestanden

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die krijgt de [verzameling scriptbestanden](The-ISEFileCollection-Object.md) die zijn geopend in de PowerShell-tabblad.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Uitvoer

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  In latere versies van Windows PowerShell ISE kunt u de **ConsolePane** -object voor hetzelfde doel.

De alleen-lezen eigenschap die opgehaald van het deelvenster Uitvoer van de huidige [editor](The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Vragen

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de huidige prompttekst opgehaald. Opmerking: de **vragen** functie kan worden genegeerd door de gebruiker '™ s profiel. Als het resultaat dan een eenvoudige tekenreeks is, klikt u vervolgens deze eigenschap niets worden geretourneerd.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De lezen / schrijven-eigenschap die wordt aangegeven als het deelvenster opdrachten op dit moment wordt weergegeven.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die krijgt de **PowerShellTab** statustekst.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De alleen-lezen eigenschap die aangeeft of het horizontale invoegtoepassingen werkvenster momenteel geopend is.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Ondersteund in Windows PowerShell ISE 3.0 en hoger, en niet aanwezig zijn in eerdere versies.

De alleen-lezen eigenschap die aangeeft of het verticale invoegtoepassingen werkvenster momenteel geopend is.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Zie ook

- [Het PowerShellTabCollection-Object](The-PowerShellTabCollection-Object.md)
- [Doel van de Scriptobjectmodel van Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)