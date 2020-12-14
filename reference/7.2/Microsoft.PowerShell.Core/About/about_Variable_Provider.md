---
description: Variabele
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variabele provider
ms.openlocfilehash: f93e58c24fdfc085983459d214db931274e164e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705510"
---
# <a name="variable-provider"></a><span data-ttu-id="ff788-103">Variabele provider</span><span class="sxs-lookup"><span data-stu-id="ff788-103">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="ff788-104">Provider naam</span><span class="sxs-lookup"><span data-stu-id="ff788-104">Provider name</span></span>
<span data-ttu-id="ff788-105">Variabele</span><span class="sxs-lookup"><span data-stu-id="ff788-105">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="ff788-106">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="ff788-106">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="ff788-107">Functies</span><span class="sxs-lookup"><span data-stu-id="ff788-107">Capabilities</span></span>

<span data-ttu-id="ff788-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="ff788-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="ff788-109">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="ff788-109">Short description</span></span>

<span data-ttu-id="ff788-110">Biedt toegang tot de Power shell-variabelen en de waarden ervan.</span><span class="sxs-lookup"><span data-stu-id="ff788-110">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="ff788-111">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="ff788-111">Detailed description</span></span>

<span data-ttu-id="ff788-112">Met de provider van de Power shell- **variabele** kunt u Power shell-variabelen in de huidige console ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="ff788-112">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="ff788-113">De provider van de Power shell- **variabele** ondersteunt de variabelen die Power Shell maakt, met inbegrip van de automatische variabelen, de voorkeurs variabelen en de variabelen die u maakt.</span><span class="sxs-lookup"><span data-stu-id="ff788-113">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="ff788-114">Het **variabele** station is een platte naam ruimte die alleen de variabele-objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="ff788-114">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="ff788-115">De variabelen hebben geen onderliggende items.</span><span class="sxs-lookup"><span data-stu-id="ff788-115">The variables have no child items.</span></span>

<span data-ttu-id="ff788-116">De **variabelen** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="ff788-116">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="ff788-117">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="ff788-117">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="ff788-118">Set-Location</span><span class="sxs-lookup"><span data-stu-id="ff788-118">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="ff788-119">Get-item</span><span class="sxs-lookup"><span data-stu-id="ff788-119">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="ff788-120">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="ff788-120">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="ff788-121">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="ff788-121">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="ff788-122">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="ff788-122">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="ff788-123">Power shell bevat ook een set cmdlets die speciaal zijn ontworpen voor het weer geven en wijzigen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="ff788-123">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="ff788-124">Wanneer u **variabelen** -cmdlets gebruikt, hoeft u het station niet op te geven `Variable:` in de naam.</span><span class="sxs-lookup"><span data-stu-id="ff788-124">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="ff788-125">Dit artikel is niet van belang voor het werken met **variabele** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ff788-125">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="ff788-126">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="ff788-126">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="ff788-127">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="ff788-127">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="ff788-128">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="ff788-128">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="ff788-129">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="ff788-129">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="ff788-130">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="ff788-130">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="ff788-131">U kunt ook de Power shell-expressie-parser gebruiken om de waarden van variabelen te maken, weer te geven en te wijzigen zonder de-cmdlets te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ff788-131">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="ff788-132">Wanneer u rechtstreeks met variabelen werkt, gebruikt u een dollar teken ( `$` ) om de naam te identificeren als een variabele en de toewijzings operator ( `=` ) om de waarde te bepalen en te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="ff788-132">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="ff788-133">`$p = Get-Process`De variabele wordt bijvoorbeeld gemaakt `p` en de resultaten van een opdracht worden opgeslagen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="ff788-133">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="ff788-134">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="ff788-134">Types exposed by this provider</span></span>

<span data-ttu-id="ff788-135">Variabelen kunnen een van de verschillende typen zijn.</span><span class="sxs-lookup"><span data-stu-id="ff788-135">Variables can be one of several different types.</span></span> <span data-ttu-id="ff788-136">De meeste variabelen zijn exemplaren van de `PSVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="ff788-136">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="ff788-137">Andere variabelen en hun typen worden hieronder weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ff788-137">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="ff788-138">De `?` variabele is een exemplaar van de `QuestionMarkVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="ff788-138">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="ff788-139">De `null` variabele is een exemplaar van de `NullVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="ff788-139">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="ff788-140">De variabelen voor het maximum aantal zijn exemplaren van de `SessionStateCapacityVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="ff788-140">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="ff788-141">`LocalVariable` instanties bevatten informatie over de huidige uitvoering, zoals:</span><span class="sxs-lookup"><span data-stu-id="ff788-141">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="ff788-142">Navigeren door de variabele stations</span><span class="sxs-lookup"><span data-stu-id="ff788-142">Navigating the Variable drives</span></span>

<span data-ttu-id="ff788-143">De provider van de **variabele** geeft het gegevens archief van het `Variable:` station beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="ff788-143">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="ff788-144">Als u met variabelen wilt werken, kunt u uw locatie wijzigen in het `Variable:` station ( `Set-Location Variable:` ) of u kunt werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="ff788-144">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="ff788-145">Als u wilt verwijzen naar een variabele van een andere locatie, gebruikt u de station naam ( `Variable:` ) in het pad.</span><span class="sxs-lookup"><span data-stu-id="ff788-145">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="ff788-146">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="ff788-146">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="ff788-147">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ff788-147">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="ff788-148">U kunt ook met de **variabelen** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="ff788-148">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="ff788-149">Als u wilt verwijzen naar een variabele van een andere locatie, gebruikt u de naam van het station `Variable:` in het pad.</span><span class="sxs-lookup"><span data-stu-id="ff788-149">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="ff788-150">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="ff788-150">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="ff788-151">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="ff788-151">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="ff788-152">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="ff788-152">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="ff788-153">De waarde van variabelen weer geven</span><span class="sxs-lookup"><span data-stu-id="ff788-153">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="ff788-154">Alle variabelen ophalen in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="ff788-154">Get all variables in the current session</span></span>

<span data-ttu-id="ff788-155">Met deze opdracht wordt de lijst met alle variabelen en hun waarden in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ff788-155">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="ff788-156">U kunt deze opdracht vanuit elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ff788-156">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="ff788-157">Een variabele ophalen met behulp van het pad van de provider</span><span class="sxs-lookup"><span data-stu-id="ff788-157">Get a variable using its provider path</span></span>

<span data-ttu-id="ff788-158">Met deze opdracht wordt een variabelen waarde opgehaald met behulp van het pad van de provider, voorafgegaan door het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="ff788-158">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="ff788-159">Dit heeft hetzelfde effect als het voor voegsel van de variabelen naam met het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="ff788-159">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="ff788-160">Variabelen ophalen met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="ff788-160">Get variables using wildcards</span></span>

<span data-ttu-id="ff788-161">Met deze opdracht worden de variabelen opgehaald met een naam die begint met "Max".</span><span class="sxs-lookup"><span data-stu-id="ff788-161">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="ff788-162">U kunt deze opdracht vanuit elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ff788-162">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="ff788-163">Haal de waarde van de?</span><span class="sxs-lookup"><span data-stu-id="ff788-163">Get the value of the ?</span></span> <span data-ttu-id="ff788-164">variabeletype</span><span class="sxs-lookup"><span data-stu-id="ff788-164">variable</span></span>

<span data-ttu-id="ff788-165">Met deze opdracht wordt de `-LiteralPath` para meter [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) gebruikt om de waarde van de `?` variabele in het station op te halen `Variable:` .</span><span class="sxs-lookup"><span data-stu-id="ff788-165">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="ff788-166">Het `?` is een Joker teken in paden, maar `Get-ChildItem` probeert geen joker tekens op te lossen in de waarden van `-LiteralPath` de para meter.</span><span class="sxs-lookup"><span data-stu-id="ff788-166">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="ff788-167">Alleen-lezen en constante variabelen ophalen</span><span class="sxs-lookup"><span data-stu-id="ff788-167">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="ff788-168">Met deze opdracht worden de variabelen opgehaald die de waarden van `ReadOnly` of `Constant` voor de eigenschap **Options** hebben.</span><span class="sxs-lookup"><span data-stu-id="ff788-168">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="ff788-169">Variabelen maken</span><span class="sxs-lookup"><span data-stu-id="ff788-169">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="ff788-170">Een nieuwe variabele maken</span><span class="sxs-lookup"><span data-stu-id="ff788-170">Create a new variable</span></span>

<span data-ttu-id="ff788-171">Met deze opdracht wordt de `services` variabele gemaakt en worden de resultaten van een `Get-Service` opdracht erin opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ff788-171">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="ff788-172">Omdat de huidige locatie zich in het station bevindt `Variable:` , is de waarde van de `-Path` para meter een punt ( `.` ), die de huidige locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="ff788-172">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="ff788-173">De haakjes rond de `Get-Service` opdracht zorgen ervoor dat de opdracht wordt uitgevoerd voordat de variabele wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ff788-173">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="ff788-174">Zonder haakjes is de waarde van de nieuwe variabele een ' Get-service ' teken reeks.</span><span class="sxs-lookup"><span data-stu-id="ff788-174">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="ff788-175">Een variabele maken met een absoluut pad</span><span class="sxs-lookup"><span data-stu-id="ff788-175">Create a variable using an absolute path</span></span>

<span data-ttu-id="ff788-176">Met deze opdracht wordt een `services` variabele gemaakt en wordt het resultaat van een `Get-Service` opdracht erin opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="ff788-176">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="ff788-177">Als u een variabele zonder waarde wilt maken, laat u de toewijzings operator weg.</span><span class="sxs-lookup"><span data-stu-id="ff788-177">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="ff788-178">Variabelen wijzigen</span><span class="sxs-lookup"><span data-stu-id="ff788-178">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="ff788-179">De naam van een variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="ff788-179">Rename a variable</span></span>

<span data-ttu-id="ff788-180">Met deze opdracht wordt de `Rename-Item` cmdlet gebruikt om de naam van de `a` variabele te wijzigen in `processes` .</span><span class="sxs-lookup"><span data-stu-id="ff788-180">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="ff788-181">De waarde van een variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="ff788-181">Change the value of a variable</span></span>

<span data-ttu-id="ff788-182">Met deze opdracht wordt de `Set-Item` cmdlet gebruikt om de waarde van de `ErrorActionPreference` variabele te wijzigen in ' Stop '.</span><span class="sxs-lookup"><span data-stu-id="ff788-182">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="ff788-183">Een variabele kopiëren</span><span class="sxs-lookup"><span data-stu-id="ff788-183">Copy a variable</span></span>

<span data-ttu-id="ff788-184">Met deze opdracht wordt de- `Copy-Item` cmdlet gebruikt om de `processes` variabele naar te kopiëren `old_processes` .</span><span class="sxs-lookup"><span data-stu-id="ff788-184">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="ff788-185">Hiermee maakt u een nieuwe variabele `old_processes` met de naam die dezelfde waarde heeft als de `processes` variabele.</span><span class="sxs-lookup"><span data-stu-id="ff788-185">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="ff788-186">Een variabele verwijderen</span><span class="sxs-lookup"><span data-stu-id="ff788-186">Delete a variable</span></span>

<span data-ttu-id="ff788-187">Met deze opdracht wordt de `serv` variabele uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="ff788-187">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="ff788-188">U kunt deze opdracht in elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ff788-188">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="ff788-189">Variabelen verwijderen met de para meter-Force</span><span class="sxs-lookup"><span data-stu-id="ff788-189">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="ff788-190">Met deze opdracht worden alle variabelen uit de huidige sessie verwijderd, met uitzonde ring van de variabelen waarvan de eigenschap **Options** de waarde `Constant` .</span><span class="sxs-lookup"><span data-stu-id="ff788-190">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="ff788-191">Zonder de `-Force` para meter verwijdert de opdracht geen variabelen waarvan de eigenschap **Options** de waarde `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="ff788-191">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="ff788-192">De waarde van een variabele instellen op NULL</span><span class="sxs-lookup"><span data-stu-id="ff788-192">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="ff788-193">Met deze opdracht wordt de `Clear-Item` cmdlet gebruikt om de waarde van de `processes` variabele te wijzigen in null.</span><span class="sxs-lookup"><span data-stu-id="ff788-193">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="ff788-194">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="ff788-194">Using the pipeline</span></span>

<span data-ttu-id="ff788-195">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="ff788-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="ff788-196">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="ff788-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="ff788-197">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ff788-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="ff788-198">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="ff788-198">Getting help</span></span>

<span data-ttu-id="ff788-199">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="ff788-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="ff788-200">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="ff788-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="ff788-201">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ff788-201">See also</span></span>

[<span data-ttu-id="ff788-202">about_Variables</span><span class="sxs-lookup"><span data-stu-id="ff788-202">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="ff788-203">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="ff788-203">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="ff788-204">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ff788-204">about_Providers</span></span>](../About/about_Providers.md)

