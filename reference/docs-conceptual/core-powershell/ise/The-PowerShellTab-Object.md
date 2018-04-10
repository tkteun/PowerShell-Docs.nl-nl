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
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="c357a-103">Het PowerShellTab-object</span><span class="sxs-lookup"><span data-stu-id="c357a-103">The PowerShellTab Object</span></span>

<span data-ttu-id="c357a-104">De **PowerShellTab** object vertegenwoordigt een Windows PowerShell-runtime-omgeving.</span><span class="sxs-lookup"><span data-stu-id="c357a-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="c357a-105">Methoden</span><span class="sxs-lookup"><span data-stu-id="c357a-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="c357a-106">Aanroepen\( Script \)</span><span class="sxs-lookup"><span data-stu-id="c357a-106">Invoke\( Script \)</span></span>

<span data-ttu-id="c357a-107">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-108">Het opgegeven script wordt uitgevoerd op het tabblad PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c357a-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="c357a-109">Deze methode werkt alleen op andere tabbladen PowerShell niet het PowerShell-tabblad waaruit deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c357a-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="c357a-110">Deze retourneert een object of de waarde.</span><span class="sxs-lookup"><span data-stu-id="c357a-110">It does not return any object or value.</span></span> <span data-ttu-id="c357a-111">Als de code in eventuele variabele wijzigt, klikt u vervolgens de wijzigingen behouden blijven op het tabblad op basis waarvan de opdracht werd aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="c357a-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="c357a-112">**Script** -System.Management.Automation.ScriptBlock of tekenreeks het scriptblok worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c357a-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="c357a-113">InvokeSynchronous\( Script \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="c357a-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="c357a-114">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c357a-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c357a-115">Het opgegeven script wordt uitgevoerd op het tabblad PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c357a-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="c357a-116">Deze methode werkt alleen op andere tabbladen PowerShell niet het PowerShell-tabblad waaruit deze wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c357a-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="c357a-117">Het scriptblok wordt uitgevoerd en een waarde die wordt geretourneerd uit het script wordt geretourneerd naar de uitvoeren-omgeving van waaruit u de opdracht aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="c357a-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="c357a-118">Als de opdracht langer duurt dan de **millesecondsTimeout** waarde geeft aan en vervolgens de opdracht is mislukt met een uitzondering: "de bewerking is een time-out."</span><span class="sxs-lookup"><span data-stu-id="c357a-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="c357a-119">**Script** -System.Management.Automation.ScriptBlock of tekenreeks het scriptblok worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c357a-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="c357a-120">**\[useNewScope\]**  -optionele Booleaanse die standaard **$true** als ingesteld op **$true**, wordt een nieuwe scope gemaakt waarin de opdracht uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c357a-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="c357a-121">De runtime-omgeving van het PowerShell-tabblad die is opgegeven door de opdracht wijzigt niet.</span><span class="sxs-lookup"><span data-stu-id="c357a-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="c357a-122">**\[millisecondsTimeout\]**  -optioneel geheel getal dat wordt standaard ingesteld op **500**.</span><span class="sxs-lookup"><span data-stu-id="c357a-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="c357a-123">Als de opdracht niet is voltooid binnen de opgegeven tijd, wordt de opdracht genereert een **TimeoutException** met het bericht 'de bewerking is een time-out."</span><span class="sxs-lookup"><span data-stu-id="c357a-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="c357a-124">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="c357a-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="c357a-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="c357a-125">AddOnsMenu</span></span>

<span data-ttu-id="c357a-126">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-127">De alleen-lezen eigenschap die in het menu invoegtoepassingen voor het PowerShell-tabblad opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c357a-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="c357a-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="c357a-128">CanInvoke</span></span>

<span data-ttu-id="c357a-129">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-130">De alleen-lezen Boole-eigenschap die als resultaat geeft een **$true** waarde als een script kan worden aangeroepen met de [Invoke (Script)](#invoke-script-) methode.</span><span class="sxs-lookup"><span data-stu-id="c357a-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="c357a-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="c357a-131">Consolepane</span></span>

<span data-ttu-id="c357a-132">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c357a-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="c357a-133">In Windows PowerShell ISE 2.0 Dit heette **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="c357a-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="c357a-134">De alleen-lezen eigenschap die opgehaald van het consolevenster [editor](../ise/The-ISEEditor-Object.md) object.</span><span class="sxs-lookup"><span data-stu-id="c357a-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="c357a-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c357a-135">DisplayName</span></span>

<span data-ttu-id="c357a-136">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-137">De alleen-lezen eigenschap die de tekst die wordt weergegeven op het tabblad PowerShell opgehaald of ingesteld. Standaard tabbladen zijn met de naam ' PowerShell #", waarbij het # een getal vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c357a-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="c357a-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="c357a-138">ExpandedScript</span></span>

<span data-ttu-id="c357a-139">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-140">Lezen / schrijven Boole-eigenschap die bepaalt of het scriptvenster is uitgevouwen of verborgen.</span><span class="sxs-lookup"><span data-stu-id="c357a-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="c357a-141">Bestanden</span><span class="sxs-lookup"><span data-stu-id="c357a-141">Files</span></span>

<span data-ttu-id="c357a-142">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-143">De alleen-lezen eigenschap die krijgt de [verzameling van scriptbestanden](../ise/The-ISEFileCollection-Object.md) die zijn geopend in het tabblad PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c357a-143">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="c357a-144">Uitvoer</span><span class="sxs-lookup"><span data-stu-id="c357a-144">Output</span></span>

<span data-ttu-id="c357a-145">Deze functie is is aanwezig in Windows PowerShell ISE 2.0, maar verwijderd of hernoemd in latere versies van de ISE.</span><span class="sxs-lookup"><span data-stu-id="c357a-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="c357a-146">In latere versies van Windows PowerShell ISE kunt u de **ConsolePane** -object voor dezelfde doelen.</span><span class="sxs-lookup"><span data-stu-id="c357a-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="c357a-147">De alleen-lezen eigenschap die opgehaald van het deelvenster Uitvoer van de huidige [editor](../ise/The-ISEEditor-Object.md).</span><span class="sxs-lookup"><span data-stu-id="c357a-147">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="c357a-148">Vragen</span><span class="sxs-lookup"><span data-stu-id="c357a-148">Prompt</span></span>

<span data-ttu-id="c357a-149">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-150">De alleen-lezen eigenschap die de huidige prompttekst opgehaald.</span><span class="sxs-lookup"><span data-stu-id="c357a-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="c357a-151">Opmerking: de **vragen** functie kan worden genegeerd door de gebruiker '™ profiel s.</span><span class="sxs-lookup"><span data-stu-id="c357a-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="c357a-152">Als het resultaat dan een eenvoudige tekenreeks is, geeft deze eigenschap niets als resultaat.</span><span class="sxs-lookup"><span data-stu-id="c357a-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="c357a-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="c357a-153">ShowCommands</span></span>

<span data-ttu-id="c357a-154">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c357a-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c357a-155">De alleen-lezen eigenschap die aangeeft of het opdrachtenvenster weergegeven die momenteel wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="c357a-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="c357a-156">StatusText</span><span class="sxs-lookup"><span data-stu-id="c357a-156">StatusText</span></span>

<span data-ttu-id="c357a-157">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c357a-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c357a-158">De alleen-lezen eigenschap die krijgt de **PowerShellTab** statustekst.</span><span class="sxs-lookup"><span data-stu-id="c357a-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="c357a-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="c357a-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="c357a-160">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c357a-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c357a-161">De alleen-lezen eigenschap die aangeeft of het horizontale werkvenster van invoegtoepassingen momenteel geopend is.</span><span class="sxs-lookup"><span data-stu-id="c357a-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="c357a-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="c357a-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="c357a-163">Ondersteunde Windows PowerShell ISE 3.0 en hoger, en niet aanwezig in eerdere versies.</span><span class="sxs-lookup"><span data-stu-id="c357a-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="c357a-164">De alleen-lezen eigenschap die aangeeft of de verticale werkvenster van invoegtoepassingen momenteel geopend is.</span><span class="sxs-lookup"><span data-stu-id="c357a-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="c357a-165">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c357a-165">See Also</span></span>

- [<span data-ttu-id="c357a-166">Het Object PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="c357a-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="c357a-167">Doel van de Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="c357a-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c357a-168">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="c357a-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)