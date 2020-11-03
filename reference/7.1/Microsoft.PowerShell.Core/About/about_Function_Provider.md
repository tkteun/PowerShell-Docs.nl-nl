---
description: Functie
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Functie provider
ms.openlocfilehash: 8789ceadbefed2dca47c10c26204f3e9ae82d36e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252155"
---
# <a name="function-provider"></a><span data-ttu-id="acc88-104">Functie provider</span><span class="sxs-lookup"><span data-stu-id="acc88-104">Function provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="acc88-105">Provider naam</span><span class="sxs-lookup"><span data-stu-id="acc88-105">Provider name</span></span>
<span data-ttu-id="acc88-106">Functie</span><span class="sxs-lookup"><span data-stu-id="acc88-106">Function</span></span>

## <a name="drives"></a><span data-ttu-id="acc88-107">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="acc88-107">Drives</span></span>

`Function:`

## <a name="capabilities"></a><span data-ttu-id="acc88-108">Functies</span><span class="sxs-lookup"><span data-stu-id="acc88-108">Capabilities</span></span>

<span data-ttu-id="acc88-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="acc88-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="acc88-110">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="acc88-110">Short description</span></span>

<span data-ttu-id="acc88-111">Biedt toegang tot de functies die zijn gedefinieerd in Power shell.</span><span class="sxs-lookup"><span data-stu-id="acc88-111">Provides access to the functions defined in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="acc88-112">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="acc88-112">Detailed description</span></span>

<span data-ttu-id="acc88-113">Met de **functie** provider van Power shell kunt u de functies en filters in Power shell ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="acc88-113">The PowerShell **Function** provider lets you get, add, change, clear, and delete the functions and filters in PowerShell.</span></span>

<span data-ttu-id="acc88-114">Een functie is een named code blok waarmee een actie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="acc88-114">A function is a named block of code that performs an action.</span></span> <span data-ttu-id="acc88-115">Wanneer u de naam van de functie typt, wordt de code in de functie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="acc88-115">When you type the function name, the code in the function runs.</span></span> <span data-ttu-id="acc88-116">Een filter is een benoemd code blok waarmee voor waarden voor een actie worden vastgelegd.</span><span class="sxs-lookup"><span data-stu-id="acc88-116">A filter is a named block of code that establishes conditions for an action.</span></span> <span data-ttu-id="acc88-117">U kunt de naam van het filter in plaats van de voor waarde typen, bijvoorbeeld in een `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="acc88-117">You can type the name of the filter in place of the condition, such as in a `Where-Object` command.</span></span>

<span data-ttu-id="acc88-118">Het **functie** station is een platte naam ruimte die alleen de functie-en filter objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="acc88-118">The **Function** drive is a flat namespace that contains only the function and filter objects.</span></span> <span data-ttu-id="acc88-119">Geen van de functies en filters hebben onderliggende items.</span><span class="sxs-lookup"><span data-stu-id="acc88-119">Neither functions nor filters have child items.</span></span>

<span data-ttu-id="acc88-120">De **functie** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="acc88-120">The **Function** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="acc88-121">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="acc88-121">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="acc88-122">Set-Location</span><span class="sxs-lookup"><span data-stu-id="acc88-122">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="acc88-123">Get-item</span><span class="sxs-lookup"><span data-stu-id="acc88-123">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="acc88-124">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="acc88-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="acc88-125">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="acc88-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="acc88-126">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="acc88-126">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="acc88-127">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="acc88-127">Types exposed by this provider</span></span>

<span data-ttu-id="acc88-128">Elke functie is een instantie van de klasse [System. Management. Automation. FunctionInfo](/dotnet/api/system.management.automation.functioninfo) .</span><span class="sxs-lookup"><span data-stu-id="acc88-128">Each function is an instance of the [System.Management.Automation.FunctionInfo](/dotnet/api/system.management.automation.functioninfo) class.</span></span> <span data-ttu-id="acc88-129">Elk filter is een instantie van de klasse [System. Management. Automation. FilterInfo](/dotnet/api/system.management.automation.filterinfo) .</span><span class="sxs-lookup"><span data-stu-id="acc88-129">Each filter is an instance of the [System.Management.Automation.FilterInfo](/dotnet/api/system.management.automation.filterinfo) class.</span></span>

## <a name="navigating-the-function-drive"></a><span data-ttu-id="acc88-130">Navigeren door het functie station</span><span class="sxs-lookup"><span data-stu-id="acc88-130">Navigating the Function drive</span></span>

<span data-ttu-id="acc88-131">De **functie** provider toont de gegevens opslag in het `Function:` station.</span><span class="sxs-lookup"><span data-stu-id="acc88-131">The **Function** provider exposes its data store in the `Function:` drive.</span></span> <span data-ttu-id="acc88-132">Als u wilt werken met functions, kunt u uw locatie wijzigen in het `Function:` station ( `Set-Location Function:` ).</span><span class="sxs-lookup"><span data-stu-id="acc88-132">To work with functions, you can change your location to the `Function:` drive (`Set-Location Function:`).</span></span> <span data-ttu-id="acc88-133">U kunt ook een ander Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="acc88-133">Or, you can work from another PowerShell drive.</span></span> <span data-ttu-id="acc88-134">Als u wilt verwijzen naar een functie vanaf een andere locatie, gebruikt u de naam van het station ( `Function:` ) in het pad.</span><span class="sxs-lookup"><span data-stu-id="acc88-134">To reference a function from another location, use the drive name (`Function:`) in the path.</span></span>

```powershell
Set-Location Function:
```

<span data-ttu-id="acc88-135">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="acc88-135">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="acc88-136">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="acc88-136">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="acc88-137">U kunt ook met de **functie** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="acc88-137">You can also work with the **Function** provider from any other PowerShell drive.</span></span> <span data-ttu-id="acc88-138">Als u wilt verwijzen naar een functie vanaf een andere locatie, gebruikt u de naam van het station `Function:` in het pad.</span><span class="sxs-lookup"><span data-stu-id="acc88-138">To reference an function from another location, use the drive name `Function:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="acc88-139">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="acc88-139">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="acc88-140">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="acc88-140">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="acc88-141">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="acc88-141">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-functions"></a><span data-ttu-id="acc88-142">Functies ophalen</span><span class="sxs-lookup"><span data-stu-id="acc88-142">Getting functions</span></span>

<span data-ttu-id="acc88-143">Met deze opdracht wordt de lijst met alle functies in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="acc88-143">This command gets the list of all the functions in the current session.</span></span> <span data-ttu-id="acc88-144">U kunt deze opdracht vanuit elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="acc88-144">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="acc88-145">De functie provider heeft geen containers, dus de bovenstaande opdracht heeft hetzelfde effect als het wordt gebruikt in combi natie met `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="acc88-145">The Function provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="acc88-146">U kunt de definitie van een functie ophalen door de eigenschap **definitie** te openen, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="acc88-146">You can retrieve a function's definition by accessing the **Definition** property, as shown below.</span></span>

```powershell
(Get-Item -Path function:more).Definition
```

<span data-ttu-id="acc88-147">U kunt ook de definitie van een functie ophalen met behulp van het pad naar de provider, voorafgegaan door het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="acc88-147">You can also retrieve a function's definition using its provider path prefixed by the dollar sign (`$`).</span></span>

```powershell
$function:more
```

### <a name="getting-selected-functions"></a><span data-ttu-id="acc88-148">Geselecteerde functies ophalen</span><span class="sxs-lookup"><span data-stu-id="acc88-148">Getting selected functions</span></span>

<span data-ttu-id="acc88-149">Met deze opdracht wordt de `man` functie van het `Function:` station opgehaald.</span><span class="sxs-lookup"><span data-stu-id="acc88-149">This command gets the `man` function from the `Function:` drive.</span></span> <span data-ttu-id="acc88-150">De cmdlet wordt gebruikt `Get-Item` om de functie op te halen.</span><span class="sxs-lookup"><span data-stu-id="acc88-150">It uses the `Get-Item` cmdlet to get the function.</span></span> <span data-ttu-id="acc88-151">De pijplijn operator ( `|` ) stuurt het resultaat naar `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="acc88-151">The pipeline operator (`|`) sends the result to `Format-Table`.</span></span> <span data-ttu-id="acc88-152">De `-Wrap` para meter leidt tekst die niet op de regel past, naar de volgende regel.</span><span class="sxs-lookup"><span data-stu-id="acc88-152">The `-Wrap` parameter directs text that does not fit on the line onto the next line.</span></span> <span data-ttu-id="acc88-153">De `-Autosize` para meter verg root of verkleint de tabel kolommen om de tekst aan te passen.</span><span class="sxs-lookup"><span data-stu-id="acc88-153">The `-Autosize` parameter resizes the table columns to accommodate the text.</span></span>

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a><span data-ttu-id="acc88-154">Werken met paden naar functie providers</span><span class="sxs-lookup"><span data-stu-id="acc88-154">Working with Function provider paths</span></span>

<span data-ttu-id="acc88-155">Met deze opdrachten wordt de functie met de naam opgehaald `c:` .</span><span class="sxs-lookup"><span data-stu-id="acc88-155">These commands both get the function named `c:`.</span></span> <span data-ttu-id="acc88-156">De eerste opdracht kan worden gebruikt in een wille keurige schijf.</span><span class="sxs-lookup"><span data-stu-id="acc88-156">The first command can be used in any drive.</span></span> <span data-ttu-id="acc88-157">De tweede opdracht wordt gebruikt in het `Function:` station.</span><span class="sxs-lookup"><span data-stu-id="acc88-157">The second command is used in the `Function:` drive.</span></span> <span data-ttu-id="acc88-158">Omdat de naam eindigt met een dubbele punt, wat de syntaxis voor een station is, moet u het pad kwalificeren met de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="acc88-158">Because the name ends in a colon, which is the syntax for a drive, you must qualify the path with the drive name.</span></span> <span data-ttu-id="acc88-159">Binnen het `Function:` station kunt u een van beide indelingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="acc88-159">Within the `Function:` drive, you can use either format.</span></span> <span data-ttu-id="acc88-160">In de tweede opdracht vertegenwoordigt de punt ( `.` ) de huidige locatie.</span><span class="sxs-lookup"><span data-stu-id="acc88-160">In the second command, the dot (`.`) represents the current location.</span></span>

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a><span data-ttu-id="acc88-161">Een functie maken</span><span class="sxs-lookup"><span data-stu-id="acc88-161">Creating a function</span></span>

<span data-ttu-id="acc88-162">Met deze opdracht wordt de `New-Item` cmdlet gebruikt voor het maken van een functie met de naam `Win32:` .</span><span class="sxs-lookup"><span data-stu-id="acc88-162">This command uses the `New-Item` cmdlet to create a function called `Win32:`.</span></span>
<span data-ttu-id="acc88-163">De expressie tussen accolades is het script blok dat wordt vertegenwoordigd door de functie naam.</span><span class="sxs-lookup"><span data-stu-id="acc88-163">The expression in braces is the script block that is represented by the function name.</span></span>

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

<span data-ttu-id="acc88-164">U kunt ook een functie maken door deze te typen op de Power shell-opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="acc88-164">You can also create a function by typing it at the PowerShell command line.</span></span> <span data-ttu-id="acc88-165">Bijvoorbeeld TPE `Function:Win32: {Set-Location C:\Windows\System32}` .</span><span class="sxs-lookup"><span data-stu-id="acc88-165">For example, tpe `Function:Win32: {Set-Location C:\Windows\System32}`.</span></span> <span data-ttu-id="acc88-166">Als u zich in het station bevindt `Function:` , kunt u de naam van het station weglaten.</span><span class="sxs-lookup"><span data-stu-id="acc88-166">If you are in the `Function:` drive, you can omit the drive name.</span></span>

## <a name="deleting-a-function"></a><span data-ttu-id="acc88-167">Een functie verwijderen</span><span class="sxs-lookup"><span data-stu-id="acc88-167">Deleting a function</span></span>

<span data-ttu-id="acc88-168">Met deze opdracht wordt de `more:` functie uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="acc88-168">This command deletes the `more:` function from the current session.</span></span>

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a><span data-ttu-id="acc88-169">Een functie wijzigen</span><span class="sxs-lookup"><span data-stu-id="acc88-169">Changing a function</span></span>

<span data-ttu-id="acc88-170">Met deze opdracht wordt de- `Set-Item` cmdlet `prompt` zo gewijzigd dat de tijd voor het pad wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="acc88-170">This command uses the `Set-Item` cmdlet to change the `prompt` function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a><span data-ttu-id="acc88-171">De naam van een functie wijzigen</span><span class="sxs-lookup"><span data-stu-id="acc88-171">Rename a function</span></span>

<span data-ttu-id="acc88-172">Met deze opdracht wordt de `Rename-Item` cmdlet gebruikt om de naam van de `help` functie te wijzigen in `gh` .</span><span class="sxs-lookup"><span data-stu-id="acc88-172">This command uses the `Rename-Item` cmdlet to change the name of the `help` function to `gh`.</span></span>

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a><span data-ttu-id="acc88-173">Een functie kopiëren</span><span class="sxs-lookup"><span data-stu-id="acc88-173">Copying a function</span></span>

<span data-ttu-id="acc88-174">Met deze opdracht `prompt` wordt de functie gekopieerd naar en wordt in `oldPrompt` feite een nieuwe naam gemaakt voor het script blok dat is gekoppeld aan de functie prompt.</span><span class="sxs-lookup"><span data-stu-id="acc88-174">This command copies the `prompt` function to `oldPrompt`, effectively creating a new name for the script block that is associated with the prompt function.</span></span>
<span data-ttu-id="acc88-175">U kunt dit gebruiken om de oorspronkelijke prompt functie op te slaan als u deze wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="acc88-175">You can use this to save the original prompt function if you plan to change it.</span></span>
<span data-ttu-id="acc88-176">De eigenschap **Options** van de nieuwe functie heeft de waarde `None` .</span><span class="sxs-lookup"><span data-stu-id="acc88-176">The **Options** property of the new function has a value of `None`.</span></span> <span data-ttu-id="acc88-177">Als u de waarde van de eigenschap **Options** wilt wijzigen, gebruikt u `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="acc88-177">To change the value of the **Options** property, use `Set-Item`.</span></span>

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a><span data-ttu-id="acc88-178">Dynamische parameters</span><span class="sxs-lookup"><span data-stu-id="acc88-178">Dynamic parameters</span></span>

<span data-ttu-id="acc88-179">Dynamische para meters zijn cmdlet-para meters die worden toegevoegd door een Power shell-provider en zijn alleen beschikbaar wanneer de cmdlet wordt gebruikt in het station waarvoor de provider is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="acc88-179">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="acc88-180">Opties < [System. Management. Automation. ScopedItemOptions] ></span><span class="sxs-lookup"><span data-stu-id="acc88-180">Options <[System.Management.Automation.ScopedItemOptions]></span></span>

<span data-ttu-id="acc88-181">Bepaalt de waarde van de eigenschap **Options** van een functie.</span><span class="sxs-lookup"><span data-stu-id="acc88-181">Determines the value of the **Options** property of a function.</span></span>

- <span data-ttu-id="acc88-182">`None`: Geen opties.</span><span class="sxs-lookup"><span data-stu-id="acc88-182">`None`: No options.</span></span> <span data-ttu-id="acc88-183">`None` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="acc88-183">`None` is the default.</span></span>
- <span data-ttu-id="acc88-184">`Constant`: De functie kan niet worden verwijderd en de eigenschappen kunnen niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="acc88-184">`Constant`: The function cannot be deleted, and its properties cannot be changed.</span></span> <span data-ttu-id="acc88-185">`Constant` is alleen beschikbaar wanneer u een functie maakt.</span><span class="sxs-lookup"><span data-stu-id="acc88-185">`Constant` is available only when you are creating a function.</span></span>
  <span data-ttu-id="acc88-186">U kunt de optie van een bestaande functie niet wijzigen in `Constant` .</span><span class="sxs-lookup"><span data-stu-id="acc88-186">You cannot change the option of an existing function to `Constant`.</span></span>
- <span data-ttu-id="acc88-187">`Private`: De functie is alleen zichtbaar in het huidige bereik</span><span class="sxs-lookup"><span data-stu-id="acc88-187">`Private`: The function is visible only in the current scope</span></span>
- <span data-ttu-id="acc88-188">(niet in onderliggende bereiken).</span><span class="sxs-lookup"><span data-stu-id="acc88-188">(not in child scopes).</span></span>
- <span data-ttu-id="acc88-189">`ReadOnly`: De eigenschappen van de functie kunnen niet worden gewijzigd, behalve door gebruik te maken van de `-Force` para meter.</span><span class="sxs-lookup"><span data-stu-id="acc88-189">`ReadOnly`: The properties of the function cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="acc88-190">U kunt gebruiken `Remove-Item` om de functie te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="acc88-190">You can use `Remove-Item` to delete the function.</span></span>
- <span data-ttu-id="acc88-191">`AllScope`: De functie wordt gekopieerd naar nieuwe bereiken die worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="acc88-191">`AllScope`: The function is copied to any new scopes that are created.</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="acc88-192">Ondersteunde cmdlets</span><span class="sxs-lookup"><span data-stu-id="acc88-192">Cmdlets supported</span></span>

- [<span data-ttu-id="acc88-193">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="acc88-193">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

- [<span data-ttu-id="acc88-194">Set-item</span><span class="sxs-lookup"><span data-stu-id="acc88-194">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="acc88-195">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="acc88-195">Using the pipeline</span></span>

<span data-ttu-id="acc88-196">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="acc88-196">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="acc88-197">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="acc88-197">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="acc88-198">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="acc88-198">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="acc88-199">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="acc88-199">Getting help</span></span>

<span data-ttu-id="acc88-200">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="acc88-200">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="acc88-201">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="acc88-201">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a><span data-ttu-id="acc88-202">Zie ook</span><span class="sxs-lookup"><span data-stu-id="acc88-202">See also</span></span>

[<span data-ttu-id="acc88-203">about_Functions</span><span class="sxs-lookup"><span data-stu-id="acc88-203">about_Functions</span></span>](../About/about_Functions.md)

[<span data-ttu-id="acc88-204">about_Providers</span><span class="sxs-lookup"><span data-stu-id="acc88-204">about_Providers</span></span>](../About/about_Providers.md)

