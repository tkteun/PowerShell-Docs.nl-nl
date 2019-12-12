---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Het PowerShellTab-object
ms.openlocfilehash: bfa11b553f97b7b27b974855ff4e8f1a48c33fea
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67028901"
---
# <a name="the-powershelltab-object"></a>Het PowerShellTab-object

Het **PowerShellTab** -object vertegenwoordigt een Windows Power shell runtime-omgeving.

## <a name="methods"></a>Methoden

### <a name="invoke-script-"></a>\( script aanroepen \)

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

Voert het opgegeven script uit op het Power shell-tabblad.

> [!NOTE]
> Deze methode werkt alleen op andere Power shell-tabbladen en niet op het Power shell-tabblad van waaruit het wordt uitgevoerd. Er wordt geen object of waarde geretourneerd. Als de code een wille keurige variabele wijzigt, blijven deze wijzigingen behouden op het tabblad waarop de opdracht is aangeroepen.

**Script** -System. Management. Automation. script block of teken reeks het uit te voeren script blok.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( script, \[useNewScope\], millisecondsTimeout \)

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

Voert het opgegeven script uit op het Power shell-tabblad.

> [!NOTE]
> Deze methode werkt alleen op andere Power shell-tabbladen en niet op het Power shell-tabblad van waaruit het wordt uitgevoerd. Het script blok wordt uitgevoerd en elke waarde die wordt geretourneerd door het script wordt geretourneerd naar de uitvoerings omgeving van waaruit u de opdracht hebt aangeroepen. Als het uitvoeren van de opdracht langer duurt dan de **millesecondsTimeout** -waarde is opgegeven, mislukt de opdracht met een uitzonde ring: ' de bewerking heeft een time-out. '

**Script** -System. Management. Automation. script block of teken reeks het uit te voeren script blok.

**\[useNewScope\]** : een optionele Booleaanse waarde die standaard wordt **$True** als deze is ingesteld op **$True**, wordt een nieuwe scope gemaakt waarin de opdracht wordt uitgevoerd. De runtime-omgeving van het Power shell-tabblad dat is opgegeven door de opdracht wordt niet gewijzigd.

**\[millisecondsTimeout\]** -optioneel geheel getal dat standaard wordt ingesteld op **500**.
Als de opdracht niet binnen de opgegeven tijd wordt voltooid, wordt door de opdracht een **TimeoutException** gegenereerd met het bericht ' er is een time-out van de bewerking opgetreden. '

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

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee het menu met invoeg toepassingen voor het Power shell-tabblad wordt opgehaald.

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

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen Booleaanse eigenschap die een **$True** waarde retourneert als een script kan worden aangeroepen met de methode [Invoke (script)](#invoke-script-) .

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

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.  In Windows PowerShell ISE 2,0 heeft dit de naam **CommandPane**.

De alleen-lezen eigenschap waarmee het console venster [Editor](The-ISEEditor-Object.md) -object wordt opgehaald.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De eigenschap lezen/schrijven waarmee de tekst wordt opgehaald of ingesteld die op het Power shell-tabblad wordt weer gegeven. Standaard hebben tabbladen de naam ' Power shell # ', waarbij het # staat voor een getal.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De eigenschap Booleaanse waarde voor lezen/schrijven die bepaalt of het script deel venster is uitgevouwen of verborgen.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Bestanden

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de [verzameling script bestanden](The-ISEFileCollection-Object.md) wordt opgehaald die in het Power shell-tabblad zijn geopend.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Uitvoer

Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.  In latere versies van Windows PowerShell ISE kunt u het **ConsolePane** -object voor dezelfde doel einden gebruiken.

De alleen-lezen eigenschap waarmee het uitvoer deel venster van de huidige [Editor](The-ISEEditor-Object.md)wordt opgehaald.

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Vragen

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de huidige prompt tekst wordt opgehaald. Opmerking: de functie **prompt** kan worden overschreven door het profiel van de gebruiker™ s. Als het resultaat geen eenvoudige teken reeks is, retourneert deze eigenschap niets.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De eigenschap lezen/schrijven die aangeeft of het deel venster opdrachten op dat moment wordt weer gegeven.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Ondersteund in Windows PowerShell ISE 2,0 en hoger.

De alleen-lezen eigenschap waarmee de status tekst van de **PowerShellTab** wordt opgehaald.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap waarmee wordt aangegeven of het deel venster met horizontale invoeg toepassingen momenteel is geopend.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap waarmee wordt aangegeven of het deel venster met verticale invoeg toepassingen momenteel is geopend.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Zie ook

- [Het PowerShellTabCollection-object](The-PowerShellTabCollection-Object.md)
- [Doel van het Windows PowerShell ISE scripting object model](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)
