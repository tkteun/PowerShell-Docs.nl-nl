---
description: Variabele
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variabele provider
ms.openlocfilehash: cae9a100b9e0a8fd044ec87d1541e1fe2bf440c8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252528"
---
# <a name="variable-provider"></a><span data-ttu-id="074fb-104">Variabele provider</span><span class="sxs-lookup"><span data-stu-id="074fb-104">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="074fb-105">Provider naam</span><span class="sxs-lookup"><span data-stu-id="074fb-105">Provider name</span></span>
<span data-ttu-id="074fb-106">Variabele</span><span class="sxs-lookup"><span data-stu-id="074fb-106">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="074fb-107">Aandrijfeenheden</span><span class="sxs-lookup"><span data-stu-id="074fb-107">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="074fb-108">Functies</span><span class="sxs-lookup"><span data-stu-id="074fb-108">Capabilities</span></span>

<span data-ttu-id="074fb-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="074fb-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="074fb-110">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="074fb-110">Short description</span></span>

<span data-ttu-id="074fb-111">Biedt toegang tot de Power shell-variabelen en de waarden ervan.</span><span class="sxs-lookup"><span data-stu-id="074fb-111">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="074fb-112">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="074fb-112">Detailed description</span></span>

<span data-ttu-id="074fb-113">Met de provider van de Power shell- **variabele** kunt u Power shell-variabelen in de huidige console ophalen, toevoegen, wijzigen, wissen en verwijderen.</span><span class="sxs-lookup"><span data-stu-id="074fb-113">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="074fb-114">De provider van de Power shell- **variabele** ondersteunt de variabelen die Power Shell maakt, met inbegrip van de automatische variabelen, de voorkeurs variabelen en de variabelen die u maakt.</span><span class="sxs-lookup"><span data-stu-id="074fb-114">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="074fb-115">Het **variabele** station is een platte naam ruimte die alleen de variabele-objecten bevat.</span><span class="sxs-lookup"><span data-stu-id="074fb-115">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="074fb-116">De variabelen hebben geen onderliggende items.</span><span class="sxs-lookup"><span data-stu-id="074fb-116">The variables have no child items.</span></span>

<span data-ttu-id="074fb-117">De **variabelen** provider ondersteunt de volgende cmdlets, die in dit artikel worden besproken.</span><span class="sxs-lookup"><span data-stu-id="074fb-117">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="074fb-118">Get-locatie</span><span class="sxs-lookup"><span data-stu-id="074fb-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="074fb-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="074fb-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="074fb-120">Get-item</span><span class="sxs-lookup"><span data-stu-id="074fb-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="074fb-121">Nieuw-item</span><span class="sxs-lookup"><span data-stu-id="074fb-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="074fb-122">Verwijderen-item</span><span class="sxs-lookup"><span data-stu-id="074fb-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="074fb-123">Wissen-item</span><span class="sxs-lookup"><span data-stu-id="074fb-123">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="074fb-124">Power shell bevat ook een set cmdlets die speciaal zijn ontworpen voor het weer geven en wijzigen van variabelen.</span><span class="sxs-lookup"><span data-stu-id="074fb-124">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="074fb-125">Wanneer u **variabelen** -cmdlets gebruikt, hoeft u het station niet op te geven `Variable:` in de naam.</span><span class="sxs-lookup"><span data-stu-id="074fb-125">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="074fb-126">Dit artikel is niet van belang voor het werken met **variabele** cmdlets.</span><span class="sxs-lookup"><span data-stu-id="074fb-126">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="074fb-127">Get-variabele</span><span class="sxs-lookup"><span data-stu-id="074fb-127">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="074fb-128">Nieuwe variabele</span><span class="sxs-lookup"><span data-stu-id="074fb-128">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="074fb-129">Set-variabele</span><span class="sxs-lookup"><span data-stu-id="074fb-129">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="074fb-130">Remove-variabele</span><span class="sxs-lookup"><span data-stu-id="074fb-130">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="074fb-131">Clear-variabele</span><span class="sxs-lookup"><span data-stu-id="074fb-131">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="074fb-132">U kunt ook de Power shell-expressie-parser gebruiken om de waarden van variabelen te maken, weer te geven en te wijzigen zonder de-cmdlets te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="074fb-132">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="074fb-133">Wanneer u rechtstreeks met variabelen werkt, gebruikt u een dollar teken ( `$` ) om de naam te identificeren als een variabele en de toewijzings operator ( `=` ) om de waarde te bepalen en te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="074fb-133">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="074fb-134">`$p = Get-Process`De variabele wordt bijvoorbeeld gemaakt `p` en de resultaten van een opdracht worden opgeslagen `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="074fb-134">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="074fb-135">Typen die door deze provider worden weer gegeven</span><span class="sxs-lookup"><span data-stu-id="074fb-135">Types exposed by this provider</span></span>

<span data-ttu-id="074fb-136">Variabelen kunnen een van de verschillende typen zijn.</span><span class="sxs-lookup"><span data-stu-id="074fb-136">Variables can be one of several different types.</span></span> <span data-ttu-id="074fb-137">De meeste variabelen zijn exemplaren van de `PSVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="074fb-137">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="074fb-138">Andere variabelen en hun typen worden hieronder weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="074fb-138">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="074fb-139">De `?` variabele is een exemplaar van de `QuestionMarkVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="074fb-139">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="074fb-140">De `null` variabele is een exemplaar van de `NullVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="074fb-140">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="074fb-141">De variabelen voor het maximum aantal zijn exemplaren van de `SessionStateCapacityVariable` klasse.</span><span class="sxs-lookup"><span data-stu-id="074fb-141">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="074fb-142">`LocalVariable` instanties bevatten informatie over de huidige uitvoering, zoals:</span><span class="sxs-lookup"><span data-stu-id="074fb-142">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="074fb-143">Navigeren door de variabele stations</span><span class="sxs-lookup"><span data-stu-id="074fb-143">Navigating the Variable drives</span></span>

<span data-ttu-id="074fb-144">De provider van de **variabele** geeft het gegevens archief van het `Variable:` station beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="074fb-144">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="074fb-145">Als u met variabelen wilt werken, kunt u uw locatie wijzigen in het `Variable:` station ( `Set-Location Variable:` ) of u kunt werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="074fb-145">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="074fb-146">Als u wilt verwijzen naar een variabele van een andere locatie, gebruikt u de station naam ( `Variable:` ) in het pad.</span><span class="sxs-lookup"><span data-stu-id="074fb-146">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="074fb-147">Als u wilt terugkeren naar een bestandssysteem station, typt u de naam van het station.</span><span class="sxs-lookup"><span data-stu-id="074fb-147">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="074fb-148">Typ bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="074fb-148">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="074fb-149">U kunt ook met de **variabelen** provider werken vanuit elk ander Power Shell-station.</span><span class="sxs-lookup"><span data-stu-id="074fb-149">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="074fb-150">Als u wilt verwijzen naar een variabele van een andere locatie, gebruikt u de naam van het station `Variable:` in het pad.</span><span class="sxs-lookup"><span data-stu-id="074fb-150">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="074fb-151">In Power shell worden aliassen gebruikt om u een vertrouwde manier te bieden om met provider paden te werken.</span><span class="sxs-lookup"><span data-stu-id="074fb-151">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="074fb-152">Opdrachten zoals `dir` en `ls` zijn nu aliassen voor [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is een alias voor [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="074fb-152">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="074fb-153">en `pwd` is een alias voor [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="074fb-153">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="074fb-154">De waarde van variabelen weer geven</span><span class="sxs-lookup"><span data-stu-id="074fb-154">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="074fb-155">Alle variabelen ophalen in de huidige sessie</span><span class="sxs-lookup"><span data-stu-id="074fb-155">Get all variables in the current session</span></span>

<span data-ttu-id="074fb-156">Met deze opdracht wordt de lijst met alle variabelen en hun waarden in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="074fb-156">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="074fb-157">U kunt deze opdracht vanuit elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="074fb-157">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="074fb-158">Een variabele ophalen met behulp van het pad van de provider</span><span class="sxs-lookup"><span data-stu-id="074fb-158">Get a variable using its provider path</span></span>

<span data-ttu-id="074fb-159">Met deze opdracht wordt een variabelen waarde opgehaald met behulp van het pad van de provider, voorafgegaan door het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="074fb-159">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="074fb-160">Dit heeft hetzelfde effect als het voor voegsel van de variabelen naam met het dollar teken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="074fb-160">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="074fb-161">Variabelen ophalen met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="074fb-161">Get variables using wildcards</span></span>

<span data-ttu-id="074fb-162">Met deze opdracht worden de variabelen opgehaald met een naam die begint met "Max".</span><span class="sxs-lookup"><span data-stu-id="074fb-162">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="074fb-163">U kunt deze opdracht vanuit elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="074fb-163">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="074fb-164">Haal de waarde van de?</span><span class="sxs-lookup"><span data-stu-id="074fb-164">Get the value of the ?</span></span> <span data-ttu-id="074fb-165">variabeletype</span><span class="sxs-lookup"><span data-stu-id="074fb-165">variable</span></span>

<span data-ttu-id="074fb-166">Met deze opdracht wordt de `-LiteralPath` para meter [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) gebruikt om de waarde van de `?` variabele in het station op te halen `Variable:` .</span><span class="sxs-lookup"><span data-stu-id="074fb-166">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="074fb-167">Het `?` is een Joker teken in paden, maar `Get-ChildItem` probeert geen joker tekens op te lossen in de waarden van `-LiteralPath` de para meter.</span><span class="sxs-lookup"><span data-stu-id="074fb-167">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="074fb-168">Alleen-lezen en constante variabelen ophalen</span><span class="sxs-lookup"><span data-stu-id="074fb-168">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="074fb-169">Met deze opdracht worden de variabelen opgehaald die de waarden van `ReadOnly` of `Constant` voor de eigenschap **Options** hebben.</span><span class="sxs-lookup"><span data-stu-id="074fb-169">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="074fb-170">Variabelen maken</span><span class="sxs-lookup"><span data-stu-id="074fb-170">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="074fb-171">Een nieuwe variabele maken</span><span class="sxs-lookup"><span data-stu-id="074fb-171">Create a new variable</span></span>

<span data-ttu-id="074fb-172">Met deze opdracht wordt de `services` variabele gemaakt en worden de resultaten van een `Get-Service` opdracht erin opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="074fb-172">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="074fb-173">Omdat de huidige locatie zich in het station bevindt `Variable:` , is de waarde van de `-Path` para meter een punt ( `.` ), die de huidige locatie vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="074fb-173">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="074fb-174">De haakjes rond de `Get-Service` opdracht zorgen ervoor dat de opdracht wordt uitgevoerd voordat de variabele wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="074fb-174">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="074fb-175">Zonder haakjes is de waarde van de nieuwe variabele een ' Get-service ' teken reeks.</span><span class="sxs-lookup"><span data-stu-id="074fb-175">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="074fb-176">Een variabele maken met een absoluut pad</span><span class="sxs-lookup"><span data-stu-id="074fb-176">Create a variable using an absolute path</span></span>

<span data-ttu-id="074fb-177">Met deze opdracht wordt een `services` variabele gemaakt en wordt het resultaat van een `Get-Service` opdracht erin opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="074fb-177">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="074fb-178">Als u een variabele zonder waarde wilt maken, laat u de toewijzings operator weg.</span><span class="sxs-lookup"><span data-stu-id="074fb-178">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="074fb-179">Variabelen wijzigen</span><span class="sxs-lookup"><span data-stu-id="074fb-179">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="074fb-180">De naam van een variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="074fb-180">Rename a variable</span></span>

<span data-ttu-id="074fb-181">Met deze opdracht wordt de `Rename-Item` cmdlet gebruikt om de naam van de `a` variabele te wijzigen in `processes` .</span><span class="sxs-lookup"><span data-stu-id="074fb-181">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="074fb-182">De waarde van een variabele wijzigen</span><span class="sxs-lookup"><span data-stu-id="074fb-182">Change the value of a variable</span></span>

<span data-ttu-id="074fb-183">Met deze opdracht wordt de `Set-Item` cmdlet gebruikt om de waarde van de `ErrorActionPreference` variabele te wijzigen in ' Stop '.</span><span class="sxs-lookup"><span data-stu-id="074fb-183">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="074fb-184">Een variabele kopiëren</span><span class="sxs-lookup"><span data-stu-id="074fb-184">Copy a variable</span></span>

<span data-ttu-id="074fb-185">Met deze opdracht wordt de- `Copy-Item` cmdlet gebruikt om de `processes` variabele naar te kopiëren `old_processes` .</span><span class="sxs-lookup"><span data-stu-id="074fb-185">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="074fb-186">Hiermee maakt u een nieuwe variabele `old_processes` met de naam die dezelfde waarde heeft als de `processes` variabele.</span><span class="sxs-lookup"><span data-stu-id="074fb-186">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="074fb-187">Een variabele verwijderen</span><span class="sxs-lookup"><span data-stu-id="074fb-187">Delete a variable</span></span>

<span data-ttu-id="074fb-188">Met deze opdracht wordt de `serv` variabele uit de huidige sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="074fb-188">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="074fb-189">U kunt deze opdracht in elk Power Shell-station gebruiken.</span><span class="sxs-lookup"><span data-stu-id="074fb-189">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="074fb-190">Variabelen verwijderen met de para meter-Force</span><span class="sxs-lookup"><span data-stu-id="074fb-190">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="074fb-191">Met deze opdracht worden alle variabelen uit de huidige sessie verwijderd, met uitzonde ring van de variabelen waarvan de eigenschap **Options** de waarde `Constant` .</span><span class="sxs-lookup"><span data-stu-id="074fb-191">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="074fb-192">Zonder de `-Force` para meter verwijdert de opdracht geen variabelen waarvan de eigenschap **Options** de waarde `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="074fb-192">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="074fb-193">De waarde van een variabele instellen op NULL</span><span class="sxs-lookup"><span data-stu-id="074fb-193">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="074fb-194">Met deze opdracht wordt de `Clear-Item` cmdlet gebruikt om de waarde van de `processes` variabele te wijzigen in null.</span><span class="sxs-lookup"><span data-stu-id="074fb-194">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="074fb-195">De pijp lijn gebruiken</span><span class="sxs-lookup"><span data-stu-id="074fb-195">Using the pipeline</span></span>

<span data-ttu-id="074fb-196">Provider-cmdlets accepteren de invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="074fb-196">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="074fb-197">U kunt de pijp lijn gebruiken om de taak te vereenvoudigen door provider gegevens van de ene cmdlet naar een andere provider-cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="074fb-197">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="074fb-198">Zie de cmdlet-verwijzingen die in dit artikel worden vermeld voor meer informatie over het gebruik van de pijp lijn met provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="074fb-198">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="074fb-199">Ondersteuning vragen</span><span class="sxs-lookup"><span data-stu-id="074fb-199">Getting help</span></span>

<span data-ttu-id="074fb-200">Vanaf Windows Power Shell 3,0 kunt u aangepaste Help-onderwerpen voor provider-cmdlets krijgen waarin wordt uitgelegd hoe deze cmdlets zich gedragen in een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="074fb-200">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="074fb-201">Als u de Help-onderwerpen wilt ophalen die zijn aangepast voor het bestandssysteem station, voert u de opdracht [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) uit in een bestandssysteem station of gebruikt `-Path` u de para meter [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) om een bestandssysteem station op te geven.</span><span class="sxs-lookup"><span data-stu-id="074fb-201">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="074fb-202">Zie ook</span><span class="sxs-lookup"><span data-stu-id="074fb-202">See also</span></span>

[<span data-ttu-id="074fb-203">about_Variables</span><span class="sxs-lookup"><span data-stu-id="074fb-203">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="074fb-204">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="074fb-204">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="074fb-205">about_Providers</span><span class="sxs-lookup"><span data-stu-id="074fb-205">about_Providers</span></span>](../About/about_Providers.md)
