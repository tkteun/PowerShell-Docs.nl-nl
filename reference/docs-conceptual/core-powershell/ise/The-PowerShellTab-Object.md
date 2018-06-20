---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het PowerShellTab-object
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: c10f9106e31bb05828f1e76554ebe40ddb778340
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952508"
---
# <a name="the-powershelltab-object"></a>Het PowerShellTab-object

De **PowerShellTab** object vertegenwoordigt een Windows PowerShell-runtime-omgeving.

## <a name="methods"></a>Methoden

### <a name="invoke-script-"></a>Aanroepen\( Script \)

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Het opgegeven script wordt uitgevoerd op het tabblad PowerShell.

> [!NOTE]
> Deze methode werkt alleen op andere tabbladen PowerShell niet het PowerShell-tabblad waaruit deze wordt uitgevoerd. Deze retourneert een object of de waarde. Als de code in eventuele variabele wijzigt, klikt u vervolgens de wijzigingen behouden blijven op het tabblad op basis waarvan de opdracht werd aangeroepen.

**Script** -System.Management.Automation.ScriptBlock of tekenreeks het scriptblok worden uitgevoerd.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( Script \[useNewScope\], millisecondsTimeout \)

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

Het opgegeven script wordt uitgevoerd op het tabblad PowerShell.

> [!NOTE]
> Deze methode werkt alleen op andere tabbladen PowerShell niet het PowerShell-tabblad waaruit deze wordt uitgevoerd. Het scriptblok wordt uitgevoerd en een waarde die wordt geretourneerd uit het script wordt geretourneerd naar de uitvoeren-omgeving van waaruit u de opdracht aangeroepen. Als de opdracht langer duurt dan de **millesecondsTimeout** waarde geeft aan en vervolgens de opdracht is mislukt met een uitzondering: "de bewerking is een time-out."

**Script** -System.Management.Automation.ScriptBlock of tekenreeks het scriptblok worden uitgevoerd.

**\[useNewScope\]**  -optionele Booleaanse die standaard **$true** als ingesteld op **$true**, wordt een nieuwe scope gemaakt waarin de opdracht uit te voeren. De runtime-omgeving van het PowerShell-tabblad die is opgegeven door de opdracht wijzigt niet.

**\[millisecondsTimeout\]**  -optioneel geheel getal dat wordt standaard ingesteld op **500**.
Als de opdracht niet is voltooid binnen de opgegeven tijd, wordt de opdracht genereert een **TimeoutException** met het bericht 'de bewerking is een time-out."

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

De alleen-lezen eigenschap die in het menu invoegtoepassingen voor het PowerShell-tabblad opgehaald.

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

De alleen-lezen Boole-eigenschap die als resultaat geeft een **$true** waarde als een script kan worden aangeroepen met de [Invoke (Script)](#invoke-script-) methode.

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

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.  In Windows PowerShell ISE 2.0 Dit heette **CommandPane**.

De alleen-lezen eigenschap die opgehaald van het consolevenster [editor](../ise/The-ISEEditor-Object.md) object.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de tekst die wordt weergegeven op het tabblad PowerShell opgehaald of ingesteld. Standaard tabbladen zijn met de naam ' PowerShell #", waarbij het # een getal vertegenwoordigt.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

In Windows PowerShell ISE 2.0 en hoger ondersteund.

Lezen / schrijven Boole-eigenschap die bepaalt of het scriptvenster is uitgevouwen of verborgen.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Bestanden

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die krijgt de [verzameling van scriptbestanden](../ise/The-ISEFileCollection-Object.md) die zijn geopend in het tabblad PowerShell.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Uitvoer

Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.  In latere versies van Windows PowerShell ISE kunt u de **ConsolePane** -object voor dezelfde doelen.

De alleen-lezen eigenschap die opgehaald van het deelvenster Uitvoer van de huidige [editor](../ise/The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Vragen

In Windows PowerShell ISE 2.0 en hoger ondersteund.

De alleen-lezen eigenschap die de huidige prompttekst opgehaald. Opmerking: de **vragen** functie kan worden genegeerd door de gebruiker '™ profiel s. Als het resultaat dan een eenvoudige tekenreeks is, geeft deze eigenschap niets als resultaat.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap die aangeeft of het opdrachtenvenster weergegeven die momenteel wordt weergegeven.

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

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap die aangeeft of het horizontale werkvenster van invoegtoepassingen momenteel geopend is.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.

De alleen-lezen eigenschap die aangeeft of de verticale werkvenster van invoegtoepassingen momenteel geopend is.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Zie ook

- [Het Object PowerShellTabCollection](The-PowerShellTabCollection-Object.md)
- [Doel van de Windows PowerShell ISE-objectmodel Scripting](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [De objectmodelhiërarchie van ISE](The-ISE-Object-Model-Hierarchy.md)