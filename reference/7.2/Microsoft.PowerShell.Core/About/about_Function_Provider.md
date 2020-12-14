---
description: Functie
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Functie provider
ms.openlocfilehash: f72ad1e93e65848238afd9feacb38982b4986177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706103"
---
# <a name="function-provider"></a><span data-ttu-id="37139-103">Functie provider</span><span class="sxs-lookup"><span data-stu-id="37139-103">Function provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="37139-104">Provider naam</span><span class="sxs-lookup"><span data-stu-id="37139-104">Provider name</span></span>
<span data-ttu-id="37139-105">Functie</span><span class="sxs-lookup"><span data-stu-id="37139-105">Function</span></span>

## <a name="drives"></a><span data-ttu-id="37139-106">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="37139-106">Drives</span></span>

`Function:`

## <a name="capabilities"></a><span data-ttu-id="37139-107">Functies</span><span class="sxs-lookup"><span data-stu-id="37139-107">Capabilities</span></span>

<span data-ttu-id="37139-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="37139-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="37139-109">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="37139-109">Short description</span></span>

<span data-ttu-id="37139-110">Biedt toegang tot de functies die zijn gedefinieerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="37139-110">Provides access to the functions defined in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="37139-111">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="37139-111">Detailed description</span></span>

<span data-ttu-id="37139-112">Met de **functie** provider van Power shell kunt u de functies en filters in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="37139-112">The PowerShell **Function** provider lets you get, add, change, clear, and delete the functions and filters in PowerShell.</span></span>

<span data-ttu-id="37139-113">Een functie is een named code blok waarmee een actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="37139-113">A function is a named block of code that performs an action.</span></span> <span data-ttu-id="37139-114">Wanneer u de naam van de functie typt, wordt de code in de functie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="37139-114">When you type the function name, the code in the function runs.</span></span> <span data-ttu-id="37139-115">Een filter is een benoemd code blok waarmee voor waarden voor een actie worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="37139-115">A filter is a named block of code that establishes conditions for an action.</span></span> <span data-ttu-id="37139-116">U kunt de naam van het filter in plaats van de voor waarde typen, bijvoorbeeld in een `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="37139-116">You can type the name of the filter in place of the condition, such as in a `Where-Object` command.</span></span>

<span data-ttu-id="37139-117">Het **functie** station is een platte naam ruimte die alleen de functie-en filter objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="37139-117">The **Function** drive is a flat namespace that contains only the function and filter objects.</span></span> <span data-ttu-id="37139-118">Geen van de functies en filters hebben onderliggende items.</span><span class="sxs-lookup"><span data-stu-id="37139-118">Neither functions nor filters have child items.</span></span>

<span data-ttu-id="37139-119">De **functie** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="37139-119">The **Function** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="37139-120">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="37139-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="37139-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="37139-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="37139-122">Get-item</span><span class="sxs-lookup"><span data-stu-id="37139-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="37139-123">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="37139-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="37139-124">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="37139-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="37139-125">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="37139-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="37139-126">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="37139-126">Types exposed by this provider</span></span>

<span data-ttu-id="37139-127">Elke functie is een instantie van de klasse [System. Management. Automation. FunctionInfo](/dotnet/api/system.management.automation.functioninfo) .</span><span class="sxs-lookup"><span data-stu-id="37139-127">Each function is an instance of the [System.Management.Automation.FunctionInfo](/dotnet/api/system.management.automation.functioninfo) class.</span></span> <span data-ttu-id="37139-128">Elk filter is een instantie van de klasse [System. Management. Automation. FilterInfo](/dotnet/api/system.management.automation.filterinfo) .</span><span class="sxs-lookup"><span data-stu-id="37139-128">Each filter is an instance of the [System.Management.Automation.FilterInfo](/dotnet/api/system.management.automation.filterinfo) class.</span></span>

## <a name="navigating-the-function-drive"></a><span data-ttu-id="37139-129">Navigeren door het functie station</span><span class="sxs-lookup"><span data-stu-id="37139-129">Navigating the Function drive</span></span>

<span data-ttu-id="37139-130">De **functie** provider toont de gegevens opslag in het `Function:` station.</span><span class="sxs-lookup"><span data-stu-id="37139-130">The **Function** provider exposes its data store in the `Function:` drive.</span></span> <span data-ttu-id="37139-131">Als u wilt werken met functions, kunt u uw locatie wijzigen in het `Function:` station ( `Set-Location Function:` ).</span><span class="sxs-lookup"><span data-stu-id="37139-131">To work with functions, you can change your location to the `Function:` drive (`Set-Location Function:`).</span></span> <span data-ttu-id="37139-132">U kunt ook een ander Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="37139-132">Or, you can work from another PowerShell drive.</span></span> <span data-ttu-id="37139-133">Als u wilt verwijzen naar een functie vanaf een andere locatie, gebruikt u de naam van het station ( `Function:` ) in het pad.</span><span class="sxs-lookup"><span data-stu-id="37139-133">To reference a function from another location, use the drive name (`Function:`) in the path.</span></span>

```powershell
Set-Location Function:
```

<span data-ttu-id="37139-134">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="37139-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="37139-135">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="37139-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="37139-136">U kunt ook met de **functie** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="37139-136">You can also work with the **Function** provider from any other PowerShell drive.</span></span> <span data-ttu-id="37139-137">Als u wilt verwijzen naar een functie vanaf een andere locatie, gebruikt u de naam van het station `Function:` in het pad.</span><span class="sxs-lookup"><span data-stu-id="37139-137">To reference an function from another location, use the drive name `Function:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="37139-138">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="37139-138">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="37139-139">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="37139-139">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="37139-140">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="37139-140">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-functions"></a><span data-ttu-id="37139-141">Functies ophalen</span><span class="sxs-lookup"><span data-stu-id="37139-141">Getting functions</span></span>

<span data-ttu-id="37139-142">Met deze opdracht wordt de lijst met alle functies in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="37139-142">This command gets the list of all the functions in the current session.</span></span> <span data-ttu-id="37139-143">U kunt deze opdracht vanuit elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="37139-143">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="37139-144">De functie provider heeft geen containers, dus de bovenstaande opdracht heeft hetzelfde effect als het wordt gebruikt in combi natie met `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="37139-144">The Function provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="37139-145">U kunt de definitie van een functie ophalen door de eigenschap **definitie** te openen, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="37139-145">You can retrieve a function's definition by accessing the **Definition** property, as shown below.</span></span>

```powershell
(Get-Item -Path function:more).Definition
```

<span data-ttu-id="37139-146">U kunt ook de definitie van een functie ophalen met behulp van het pad naar de provider, voorafgegaan door het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="37139-146">You can also retrieve a function's definition using its provider path prefixed by the dollar sign (`$`).</span></span>

```powershell
$function:more
```

### <a name="getting-selected-functions"></a><span data-ttu-id="37139-147">Geselecteerde functies ophalen</span><span class="sxs-lookup"><span data-stu-id="37139-147">Getting selected functions</span></span>

<span data-ttu-id="37139-148">Met deze opdracht wordt de `man` functie van het `Function:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="37139-148">This command gets the `man` function from the `Function:` drive.</span></span> <span data-ttu-id="37139-149">De cmdlet wordt gebruikt `Get-Item` om de functie op te halen.</span><span class="sxs-lookup"><span data-stu-id="37139-149">It uses the `Get-Item` cmdlet to get the function.</span></span> <span data-ttu-id="37139-150">De pijplijn operator ( `|` ) stuurt het resultaat naar `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="37139-150">The pipeline operator (`|`) sends the result to `Format-Table`.</span></span> <span data-ttu-id="37139-151">De `-Wrap` para meter leidt tekst die niet op de regel past, naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="37139-151">The `-Wrap` parameter directs text that does not fit on the line onto the next line.</span></span> <span data-ttu-id="37139-152">De `-Autosize` para meter verg root of verkleint de tabel kolommen om de tekst aan te passen.</span><span class="sxs-lookup"><span data-stu-id="37139-152">The `-Autosize` parameter resizes the table columns to accommodate the text.</span></span>

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a><span data-ttu-id="37139-153">Werken met paden naar functie providers</span><span class="sxs-lookup"><span data-stu-id="37139-153">Working with Function provider paths</span></span>

<span data-ttu-id="37139-154">Met deze opdrachten wordt de functie met de naam opgehaald `c:` .</span><span class="sxs-lookup"><span data-stu-id="37139-154">These commands both get the function named `c:`.</span></span> <span data-ttu-id="37139-155">De eerste opdracht kan worden gebruikt in een wille keurige schijf.</span><span class="sxs-lookup"><span data-stu-id="37139-155">The first command can be used in any drive.</span></span> <span data-ttu-id="37139-156">De tweede opdracht wordt gebruikt in het `Function:` station.</span><span class="sxs-lookup"><span data-stu-id="37139-156">The second command is used in the `Function:` drive.</span></span> <span data-ttu-id="37139-157">Omdat de naam eindigt met een dubbele punt, wat de syntaxis voor een station is, moet u het pad kwalificeren met de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="37139-157">Because the name ends in a colon, which is the syntax for a drive, you must qualify the path with the drive name.</span></span> <span data-ttu-id="37139-158">Binnen het `Function:` station kunt u een van beide indelingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="37139-158">Within the `Function:` drive, you can use either format.</span></span> <span data-ttu-id="37139-159">In de tweede opdracht vertegenwoordigt de punt ( `.` ) de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="37139-159">In the second command, the dot (`.`) represents the current location.</span></span>

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a><span data-ttu-id="37139-160">Een functie maken</span><span class="sxs-lookup"><span data-stu-id="37139-160">Creating a function</span></span>

<span data-ttu-id="37139-161">Met deze opdracht wordt de `New-Item` cmdlet gebruikt voor het maken van een functie met de naam `Win32:` .</span><span class="sxs-lookup"><span data-stu-id="37139-161">This command uses the `New-Item` cmdlet to create a function called `Win32:`.</span></span>
<span data-ttu-id="37139-162">De expressie tussen accolades is het script blok dat wordt vertegenwoordigd door de functie naam.</span><span class="sxs-lookup"><span data-stu-id="37139-162">The expression in braces is the script block that is represented by the function name.</span></span>

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

<span data-ttu-id="37139-163">U kunt ook een functie maken door deze te typen op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="37139-163">You can also create a function by typing it at the PowerShell command line.</span></span> <span data-ttu-id="37139-164">Bijvoorbeeld TPE `Function:Win32: {Set-Location C:\Windows\System32}` .</span><span class="sxs-lookup"><span data-stu-id="37139-164">For example, tpe `Function:Win32: {Set-Location C:\Windows\System32}`.</span></span> <span data-ttu-id="37139-165">Als u zich in het station bevindt `Function:` , kunt u de naam van het station weglaten.</span><span class="sxs-lookup"><span data-stu-id="37139-165">If you are in the `Function:` drive, you can omit the drive name.</span></span>

## <a name="deleting-a-function"></a><span data-ttu-id="37139-166">Een functie verwijderen</span><span class="sxs-lookup"><span data-stu-id="37139-166">Deleting a function</span></span>

<span data-ttu-id="37139-167">Met deze opdracht wordt de `more:` functie uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="37139-167">This command deletes the `more:` function from the current session.</span></span>

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a><span data-ttu-id="37139-168">Een functie wijzigen</span><span class="sxs-lookup"><span data-stu-id="37139-168">Changing a function</span></span>

<span data-ttu-id="37139-169">Met deze opdracht wordt de- `Set-Item` cmdlet `prompt` zo gewijzigd dat de tijd voor het pad wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="37139-169">This command uses the `Set-Item` cmdlet to change the `prompt` function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a><span data-ttu-id="37139-170">De naam van een functie wijzigen</span><span class="sxs-lookup"><span data-stu-id="37139-170">Rename a function</span></span>

<span data-ttu-id="37139-171">Met deze opdracht wordt de `Rename-Item` cmdlet gebruikt om de naam van de `help` functie te wijzigen in `gh` .</span><span class="sxs-lookup"><span data-stu-id="37139-171">This command uses the `Rename-Item` cmdlet to change the name of the `help` function to `gh`.</span></span>

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a><span data-ttu-id="37139-172">Een functie kopiëren</span><span class="sxs-lookup"><span data-stu-id="37139-172">Copying a function</span></span>

<span data-ttu-id="37139-173">Met deze opdracht `prompt` wordt de functie gekopieerd naar en wordt in `oldPrompt` feite een nieuwe naam gemaakt voor het script blok dat is gekoppeld aan de functie prompt.</span><span class="sxs-lookup"><span data-stu-id="37139-173">This command copies the `prompt` function to `oldPrompt`, effectively creating a new name for the script block that is associated with the prompt function.</span></span>
<span data-ttu-id="37139-174">U kunt dit gebruiken om de oorspronkelijke prompt functie op te slaan als u deze wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="37139-174">You can use this to save the original prompt function if you plan to change it.</span></span>
<span data-ttu-id="37139-175">De eigenschap **Options** van de nieuwe functie heeft de waarde `None` .</span><span class="sxs-lookup"><span data-stu-id="37139-175">The **Options** property of the new function has a value of `None`.</span></span> <span data-ttu-id="37139-176">Als u de waarde van de eigenschap **Options** wilt wijzigen, gebruikt u `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="37139-176">To change the value of the **Options** property, use `Set-Item`.</span></span>

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a><span data-ttu-id="37139-177">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="37139-177">Dynamic parameters</span></span>

<span data-ttu-id="37139-178">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="37139-178">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="37139-179">Opties < [System. Management. Automation. ScopedItemOptions] ></span><span class="sxs-lookup"><span data-stu-id="37139-179">Options <[System.Management.Automation.ScopedItemOptions]></span></span>

<span data-ttu-id="37139-180">Bepaalt de waarde van de eigenschap **Options** van een functie.</span><span class="sxs-lookup"><span data-stu-id="37139-180">Determines the value of the **Options** property of a function.</span></span>

- <span data-ttu-id="37139-181">`None`: Geen opties.</span><span class="sxs-lookup"><span data-stu-id="37139-181">`None`: No options.</span></span> <span data-ttu-id="37139-182">`None` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="37139-182">`None` is the default.</span></span>
- <span data-ttu-id="37139-183">`Constant`: De functie kan niet worden verwijderd en de eigenschappen kunnen niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="37139-183">`Constant`: The function cannot be deleted, and its properties cannot be changed.</span></span> <span data-ttu-id="37139-184">`Constant` is alleen beschikbaar wanneer u een functie maakt.</span><span class="sxs-lookup"><span data-stu-id="37139-184">`Constant` is available only when you are creating a function.</span></span>
  <span data-ttu-id="37139-185">U kunt de optie van een bestaande functie niet wijzigen in `Constant` .</span><span class="sxs-lookup"><span data-stu-id="37139-185">You cannot change the option of an existing function to `Constant`.</span></span>
- <span data-ttu-id="37139-186">`Private`: De functie is alleen zichtbaar in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="37139-186">`Private`: The function is visible only in the current scope</span></span>
- <span data-ttu-id="37139-187">(niet in onderliggende bereiken).</span><span class="sxs-lookup"><span data-stu-id="37139-187">(not in child scopes).</span></span>
- <span data-ttu-id="37139-188">`ReadOnly`: De eigenschappen van de functie kunnen niet worden gewijzigd, behalve door gebruik te maken van de `-Force` para meter.</span><span class="sxs-lookup"><span data-stu-id="37139-188">`ReadOnly`: The properties of the function cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="37139-189">U kunt gebruiken `Remove-Item` om de functie te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="37139-189">You can use `Remove-Item` to delete the function.</span></span>
- <span data-ttu-id="37139-190">`AllScope`: De functie wordt gekopieerd naar nieuwe bereiken die worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="37139-190">`AllScope`: The function is copied to any new scopes that are created.</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="37139-191">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="37139-191">Cmdlets supported</span></span>

- [<span data-ttu-id="37139-192">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="37139-192">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

- [<span data-ttu-id="37139-193">Set-item</span><span class="sxs-lookup"><span data-stu-id="37139-193">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="37139-194">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="37139-194">Using the pipeline</span></span>

<span data-ttu-id="37139-195">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="37139-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="37139-196">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="37139-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="37139-197">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="37139-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="37139-198">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="37139-198">Getting help</span></span>

<span data-ttu-id="37139-199">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="37139-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="37139-200">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="37139-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a><span data-ttu-id="37139-201">Zie ook</span><span class="sxs-lookup"><span data-stu-id="37139-201">See also</span></span>

[<span data-ttu-id="37139-202">about_Functions</span><span class="sxs-lookup"><span data-stu-id="37139-202">about_Functions</span></span>](../About/about_Functions.md)

[<span data-ttu-id="37139-203">about_Providers</span><span class="sxs-lookup"><span data-stu-id="37139-203">about_Providers</span></span>](../About/about_Providers.md)

