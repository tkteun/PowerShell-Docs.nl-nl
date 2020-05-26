---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Het PowerShellTab-object
ms.openlocfilehash: 55e3678a8285f0ec7e8131d98c87478216c26f37
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810909"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="8cb05-103">Het PowerShellTab-object</span><span class="sxs-lookup"><span data-stu-id="8cb05-103">The PowerShellTab Object</span></span>

<span data-ttu-id="8cb05-104">Het **PowerShellTab** -object vertegenwoordigt een Windows Power shell runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="8cb05-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="8cb05-105">Methoden</span><span class="sxs-lookup"><span data-stu-id="8cb05-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="8cb05-106">Script aanroepen \(\)</span><span class="sxs-lookup"><span data-stu-id="8cb05-106">Invoke\( Script \)</span></span>

<span data-ttu-id="8cb05-107">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-108">Voert het opgegeven script uit op het Power shell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="8cb05-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="8cb05-109">Deze methode werkt alleen op andere Power shell-tabbladen en niet op het Power shell-tabblad van waaruit het wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8cb05-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="8cb05-110">Er wordt geen object of waarde geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8cb05-110">It does not return any object or value.</span></span> <span data-ttu-id="8cb05-111">Als de code een wille keurige variabele wijzigt, blijven deze wijzigingen behouden op het tabblad waarop de opdracht is aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="8cb05-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="8cb05-112">**Script** -System. Management. Automation. script block of teken reeks het uit te voeren script blok.</span><span class="sxs-lookup"><span data-stu-id="8cb05-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="8cb05-113">InvokeSynchronous \( script, \[ useNewScope \] , millisecondsTimeout\)</span><span class="sxs-lookup"><span data-stu-id="8cb05-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="8cb05-114">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="8cb05-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8cb05-115">Voert het opgegeven script uit op het Power shell-tabblad.</span><span class="sxs-lookup"><span data-stu-id="8cb05-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="8cb05-116">Deze methode werkt alleen op andere Power shell-tabbladen en niet op het Power shell-tabblad van waaruit het wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8cb05-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="8cb05-117">Het script blok wordt uitgevoerd en elke waarde die wordt geretourneerd door het script wordt geretourneerd naar de uitvoerings omgeving van waaruit u de opdracht hebt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="8cb05-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="8cb05-118">Als het uitvoeren van de opdracht langer duurt dan de **millesecondsTimeout** -waarde is opgegeven, mislukt de opdracht met een uitzonde ring: ' de bewerking heeft een time-out. '</span><span class="sxs-lookup"><span data-stu-id="8cb05-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="8cb05-119">**Script** -System. Management. Automation. script block of teken reeks het uit te voeren script blok.</span><span class="sxs-lookup"><span data-stu-id="8cb05-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="8cb05-120">\*\* \[ useNewScope \] \*\* : een optionele Booleaanse waarde die standaard `$true` wordt ingesteld op `$true` , wordt een nieuwe scope gemaakt waarin de opdracht wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="8cb05-120">**\[useNewScope\]** -  Optional Boolean that defaults to `$true` If set to `$true`, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="8cb05-121">De runtime-omgeving van het Power shell-tabblad dat is opgegeven door de opdracht wordt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8cb05-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="8cb05-122">\*\* \[ millisecondsTimeout \] \*\* : een optioneel geheel getal dat standaard wordt ingesteld op **500**.</span><span class="sxs-lookup"><span data-stu-id="8cb05-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="8cb05-123">Als de opdracht niet binnen de opgegeven tijd wordt voltooid, wordt door de opdracht een **TimeoutException** gegenereerd met het bericht ' er is een time-out van de bewerking opgetreden. '</span><span class="sxs-lookup"><span data-stu-id="8cb05-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="8cb05-124">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="8cb05-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="8cb05-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="8cb05-125">AddOnsMenu</span></span>

<span data-ttu-id="8cb05-126">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-127">De alleen-lezen eigenschap waarmee het menu met invoeg toepassingen voor het Power shell-tabblad wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8cb05-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="8cb05-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="8cb05-128">CanInvoke</span></span>

<span data-ttu-id="8cb05-129">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-130">De alleen-lezen Booleaanse eigenschap die een `$true` waarde retourneert als een script kan worden aangeroepen met de methode [Invoke (script)](#invoke-script-) .</span><span class="sxs-lookup"><span data-stu-id="8cb05-130">The read-only Boolean property that returns a `$true` value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="8cb05-131">ConsolePane</span><span class="sxs-lookup"><span data-stu-id="8cb05-131">ConsolePane</span></span>

<span data-ttu-id="8cb05-132">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="8cb05-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> <span data-ttu-id="8cb05-133">In Windows PowerShell ISE 2,0 heeft dit de naam **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="8cb05-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="8cb05-134">De alleen-lezen eigenschap waarmee het console venster [Editor](The-ISEEditor-Object.md) -object wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8cb05-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="8cb05-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8cb05-135">DisplayName</span></span>

<span data-ttu-id="8cb05-136">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-137">De eigenschap lezen/schrijven waarmee de tekst wordt opgehaald of ingesteld die op het Power shell-tabblad wordt weer gegeven. Standaard hebben tabbladen de naam ' Power shell # ', waarbij het # staat voor een getal.</span><span class="sxs-lookup"><span data-stu-id="8cb05-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="8cb05-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="8cb05-138">ExpandedScript</span></span>

<span data-ttu-id="8cb05-139">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-140">De eigenschap Booleaanse waarde voor lezen/schrijven die bepaalt of het script deel venster is uitgevouwen of verborgen.</span><span class="sxs-lookup"><span data-stu-id="8cb05-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="8cb05-141">Bestanden</span><span class="sxs-lookup"><span data-stu-id="8cb05-141">Files</span></span>

<span data-ttu-id="8cb05-142">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-143">De alleen-lezen eigenschap waarmee de [verzameling script bestanden](The-ISEFileCollection-Object.md) wordt opgehaald die in het Power shell-tabblad zijn geopend.</span><span class="sxs-lookup"><span data-stu-id="8cb05-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="8cb05-144">Uitvoer</span><span class="sxs-lookup"><span data-stu-id="8cb05-144">Output</span></span>

<span data-ttu-id="8cb05-145">Deze functie is aanwezig in Windows PowerShell ISE 2,0, maar is in latere versies van de ISE verwijderd of de naam ervan is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="8cb05-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="8cb05-146">In latere versies van Windows PowerShell ISE kunt u het **ConsolePane** -object voor dezelfde doel einden gebruiken.</span><span class="sxs-lookup"><span data-stu-id="8cb05-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="8cb05-147">De alleen-lezen eigenschap waarmee het uitvoer deel venster van de huidige [Editor](The-ISEEditor-Object.md)wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8cb05-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="8cb05-148">Vraag</span><span class="sxs-lookup"><span data-stu-id="8cb05-148">Prompt</span></span>

<span data-ttu-id="8cb05-149">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-150">De alleen-lezen eigenschap waarmee de huidige prompt tekst wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8cb05-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="8cb05-151">Opmerking: de functie **prompt** kan worden overschreven door het profiel van de gebruiker™ s.</span><span class="sxs-lookup"><span data-stu-id="8cb05-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="8cb05-152">Als het resultaat geen eenvoudige teken reeks is, retourneert deze eigenschap niets.</span><span class="sxs-lookup"><span data-stu-id="8cb05-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="8cb05-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="8cb05-153">ShowCommands</span></span>

<span data-ttu-id="8cb05-154">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="8cb05-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8cb05-155">De eigenschap lezen/schrijven die aangeeft of het deel venster opdrachten op dat moment wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="8cb05-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="8cb05-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="8cb05-156">StatusText</span></span>

<span data-ttu-id="8cb05-157">Ondersteund in Windows PowerShell ISE 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="8cb05-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="8cb05-158">De alleen-lezen eigenschap waarmee de status tekst van de **PowerShellTab** wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="8cb05-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="8cb05-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="8cb05-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="8cb05-160">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="8cb05-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8cb05-161">De alleen-lezen eigenschap waarmee wordt aangegeven of het deel venster met horizontale invoeg toepassingen momenteel is geopend.</span><span class="sxs-lookup"><span data-stu-id="8cb05-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="8cb05-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="8cb05-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="8cb05-163">Ondersteund in Windows PowerShell ISE 3,0 en hoger en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="8cb05-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="8cb05-164">De alleen-lezen eigenschap waarmee wordt aangegeven of het deel venster met verticale invoeg toepassingen momenteel is geopend.</span><span class="sxs-lookup"><span data-stu-id="8cb05-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="8cb05-165">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8cb05-165">See Also</span></span>

- [<span data-ttu-id="8cb05-166">Het PowerShellTabCollection-object</span><span class="sxs-lookup"><span data-stu-id="8cb05-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="8cb05-167">Doel van het scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8cb05-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="8cb05-168">De ISE-object model hiërarchie</span><span class="sxs-lookup"><span data-stu-id="8cb05-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
