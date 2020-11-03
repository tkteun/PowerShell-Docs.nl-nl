---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: aaee09926c93bb8c8e72efb5fd4ea34e2fc67391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250121"
---
# <span data-ttu-id="31837-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="31837-103">Where-Object</span></span>

## <span data-ttu-id="31837-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="31837-104">SYNOPSIS</span></span>
<span data-ttu-id="31837-105">Selecteert objecten uit een verzameling op basis van de bijbehorende eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="31837-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="31837-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="31837-106">SYNTAX</span></span>

### <span data-ttu-id="31837-107">Gelijkset (standaard)</span><span class="sxs-lookup"><span data-stu-id="31837-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ] [<CommonParameters>]
```

### <span data-ttu-id="31837-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="31837-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="31837-109">Overeenkomstset</span><span class="sxs-lookup"><span data-stu-id="31837-109">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Match]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="31837-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CEQ] [<CommonParameters>]
```

### <span data-ttu-id="31837-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="31837-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NE] [<CommonParameters>]
```

### <span data-ttu-id="31837-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="31837-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNE] [<CommonParameters>]
```

### <span data-ttu-id="31837-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="31837-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GT] [<CommonParameters>]
```

### <span data-ttu-id="31837-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="31837-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGT] [<CommonParameters>]
```

### <span data-ttu-id="31837-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="31837-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LT] [<CommonParameters>]
```

### <span data-ttu-id="31837-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="31837-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLT] [<CommonParameters>]
```

### <span data-ttu-id="31837-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="31837-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GE] [<CommonParameters>]
```

### <span data-ttu-id="31837-118">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="31837-118">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGE] [<CommonParameters>]
```

### <span data-ttu-id="31837-119">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="31837-119">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LE] [<CommonParameters>]
```

### <span data-ttu-id="31837-120">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="31837-120">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLE] [<CommonParameters>]
```

### <span data-ttu-id="31837-121">Like-set</span><span class="sxs-lookup"><span data-stu-id="31837-121">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Like] [<CommonParameters>]
```

### <span data-ttu-id="31837-122">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="31837-122">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLike] [<CommonParameters>]
```

### <span data-ttu-id="31837-123">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="31837-123">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotLike] [<CommonParameters>]
```

### <span data-ttu-id="31837-124">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="31837-124">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotLike]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="31837-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CMatch] [<CommonParameters>]
```

### <span data-ttu-id="31837-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="31837-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotMatch]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="31837-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotMatch]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-128">Contains bevat</span><span class="sxs-lookup"><span data-stu-id="31837-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Contains]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="31837-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CContains]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="31837-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotContains]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="31837-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotContains]
 [<CommonParameters>]
```

### <span data-ttu-id="31837-132">Pentekenen</span><span class="sxs-lookup"><span data-stu-id="31837-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-In] [<CommonParameters>]
```

### <span data-ttu-id="31837-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="31837-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CIn] [<CommonParameters>]
```

### <span data-ttu-id="31837-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="31837-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotIn] [<CommonParameters>]
```

### <span data-ttu-id="31837-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="31837-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotIn] [<CommonParameters>]
```

### <span data-ttu-id="31837-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="31837-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Is] [<CommonParameters>]
```

### <span data-ttu-id="31837-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="31837-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-IsNot] [<CommonParameters>]
```

## <span data-ttu-id="31837-138">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="31837-138">DESCRIPTION</span></span>

<span data-ttu-id="31837-139">De `Where-Object` cmdlet selecteert objecten met bepaalde eigenschaps waarden uit de verzameling van objecten die worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="31837-139">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="31837-140">U kunt bijvoorbeeld de `Where-Object` -cmdlet gebruiken om bestanden te selecteren die zijn gemaakt na een bepaalde datum, gebeurtenissen met een bepaalde id of computers die gebruikmaken van een bepaalde versie van Windows.</span><span class="sxs-lookup"><span data-stu-id="31837-140">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="31837-141">Vanaf Windows Power Shell 3,0 zijn er twee verschillende manieren om een opdracht te maken `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="31837-141">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="31837-142">**Script blok**.</span><span class="sxs-lookup"><span data-stu-id="31837-142">**Script block**.</span></span> <span data-ttu-id="31837-143">U kunt een script blok gebruiken om de naam van de eigenschap, een vergelijkings operator en een eigenschaps waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="31837-143">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="31837-144">`Where-Object` retourneert alle objecten waarvoor de instructie script blok is ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="31837-144">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="31837-145">Met de volgende opdracht worden bijvoorbeeld processen in de klasse met normale prioriteit opgehaald, dat wil zeggen, processen waarbij de waarde van de eigenschap **PriorityClass** gelijk is aan normaal.</span><span class="sxs-lookup"><span data-stu-id="31837-145">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="31837-146">Alle Power shell-vergelijkings operatoren zijn geldig in de script blok indeling.</span><span class="sxs-lookup"><span data-stu-id="31837-146">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="31837-147">Zie [about_Comparison_Operators](./About/about_Comparison_Operators.md)voor meer informatie over vergelijkings operatoren.</span><span class="sxs-lookup"><span data-stu-id="31837-147">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="31837-148">**Vergelijkings instructie**.</span><span class="sxs-lookup"><span data-stu-id="31837-148">**Comparison statement**.</span></span> <span data-ttu-id="31837-149">U kunt ook een vergelijkings instructie schrijven die veel meer lijkt op natuurlijke taal.</span><span class="sxs-lookup"><span data-stu-id="31837-149">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="31837-150">Vergelijkings instructies zijn geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-150">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="31837-151">Met de volgende opdrachten worden ook processen opgehaald die de prioriteits klasse normaal hebben.</span><span class="sxs-lookup"><span data-stu-id="31837-151">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="31837-152">Deze opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="31837-152">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="31837-153">Vanuit Windows Power Shell 3,0 worden `Where-Object` vergelijkings operatoren als para meters toegevoegd aan een `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="31837-153">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="31837-154">Tenzij opgegeven, zijn alle Opera tors niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-154">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="31837-155">Vóór Windows Power Shell 3,0 kan de vergelijkings operators in de Power shell-taal alleen worden gebruikt in script blokken.</span><span class="sxs-lookup"><span data-stu-id="31837-155">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="31837-156">Wanneer u één **eigenschap** opgeeft `Where-Object` , wordt de waarde van de eigenschap behandeld als een booleaanse expressie.</span><span class="sxs-lookup"><span data-stu-id="31837-156">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="31837-157">Als de waarde van **Length** niet gelijk is aan nul, wordt de expressie geëvalueerd als **waar**.</span><span class="sxs-lookup"><span data-stu-id="31837-157">When the value of **Length** is not zero, the expression evaluates to **True**.</span></span> <span data-ttu-id="31837-158">Bijvoorbeeld: `('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="31837-158">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="31837-159">Het vorige voor beeld is functioneel equivalent aan:</span><span class="sxs-lookup"><span data-stu-id="31837-159">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="31837-160">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="31837-160">EXAMPLES</span></span>

### <span data-ttu-id="31837-161">Voor beeld 1: gestopt services ophalen</span><span class="sxs-lookup"><span data-stu-id="31837-161">Example 1: Get stopped services</span></span>

<span data-ttu-id="31837-162">Met deze opdrachten wordt een lijst weer geven met alle services die momenteel zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="31837-162">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="31837-163">De `$_` Automatische variabele vertegenwoordigt elk object dat wordt door gegeven aan de `Where-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31837-163">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="31837-164">De eerste opdracht maakt gebruik van de script blok indeling. de tweede opdracht maakt gebruik van de indeling van de vergelijkings instructie.</span><span class="sxs-lookup"><span data-stu-id="31837-164">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="31837-165">De opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="31837-165">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="31837-166">Voor beeld 2: processen ophalen op basis van werkset</span><span class="sxs-lookup"><span data-stu-id="31837-166">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="31837-167">Met deze opdrachten worden processen weer geven die een werkset hebben die groter is dan 250 mega bytes (KB).</span><span class="sxs-lookup"><span data-stu-id="31837-167">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="31837-168">De syntaxis van de script Block en-instructie zijn gelijk en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="31837-168">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="31837-169">Voor beeld 3: processen ophalen op basis van proces naam</span><span class="sxs-lookup"><span data-stu-id="31837-169">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="31837-170">Met deze opdrachten worden de processen opgehaald die de waarde van de eigenschap **proces** naam hebben die begint met de letter `p` .</span><span class="sxs-lookup"><span data-stu-id="31837-170">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="31837-171">Met de operator **match** kunt u reguliere expressie overeenkomsten gebruiken.</span><span class="sxs-lookup"><span data-stu-id="31837-171">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="31837-172">De syntaxis van de script Block en-instructie zijn gelijk en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="31837-172">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="31837-173">Voor beeld 4: de indeling van de vergelijkings instructie gebruiken</span><span class="sxs-lookup"><span data-stu-id="31837-173">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="31837-174">In dit voor beeld ziet u hoe u de nieuwe indeling van de vergelijkings instructie van de `Where-Object` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="31837-174">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="31837-175">De eerste opdracht maakt gebruik van de indeling van de vergelijkings instructie.</span><span class="sxs-lookup"><span data-stu-id="31837-175">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="31837-176">In deze opdracht worden geen aliassen gebruikt en alle para meters bevatten de parameter naam.</span><span class="sxs-lookup"><span data-stu-id="31837-176">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="31837-177">De tweede opdracht is het natuurlijke gebruik van de opdracht notatie voor vergelijking.</span><span class="sxs-lookup"><span data-stu-id="31837-177">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="31837-178">De `where` alias wordt vervangen door de naam van de `Where-Object` cmdlet en alle optionele parameter namen worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="31837-178">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="31837-179">Voor beeld 5: opdrachten ophalen op basis van eigenschappen</span><span class="sxs-lookup"><span data-stu-id="31837-179">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="31837-180">In dit voor beeld ziet u hoe u opdrachten schrijft die items retour neren die waar of onwaar zijn of een wille keurige waarde hebben voor een opgegeven eigenschap.</span><span class="sxs-lookup"><span data-stu-id="31837-180">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="31837-181">Elk voor beeld toont zowel het script blok als de indeling van de vergelijkings instructie voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="31837-181">Each example shows both the script block and comparison statement formats for the command.</span></span>

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### <span data-ttu-id="31837-182">Voor beeld 6: meerdere voor waarden gebruiken</span><span class="sxs-lookup"><span data-stu-id="31837-182">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="31837-183">In dit voor beeld ziet u hoe u een `Where-Object` opdracht met meerdere voor waarden maakt.</span><span class="sxs-lookup"><span data-stu-id="31837-183">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="31837-184">Met deze opdracht worden niet-kern modules opgehaald die ondersteuning bieden voor de Help-functie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="31837-184">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="31837-185">De opdracht gebruikt de para meter **ListAvailable** van de `Get-Module` cmdlet om alle modules op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="31837-185">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="31837-186">Een pijplijn operator ( `|` ) verzendt de modules naar de `Where-Object` cmdlet, die modules ophaalt waarvan de namen niet beginnen met micro soft of PS, en een waarde hebben voor de eigenschap **HelpInfoURI** , die Power shell vertelt waar bijgewerkte Help-bestanden voor de module moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="31837-186">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="31837-187">De vergelijkings instructies zijn verbonden door de operator **and** .</span><span class="sxs-lookup"><span data-stu-id="31837-187">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="31837-188">In het voor beeld wordt de script blok opdracht indeling gebruikt.</span><span class="sxs-lookup"><span data-stu-id="31837-188">The example uses the script block command format.</span></span> <span data-ttu-id="31837-189">Logische Opera Tors, zoals **en** en **of** , zijn alleen geldig in script blokken.</span><span class="sxs-lookup"><span data-stu-id="31837-189">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="31837-190">U kunt ze niet gebruiken in de indeling van de vergelijkings instructie van een `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="31837-190">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="31837-191">Zie [about_Logical_Operators](./About/about_logical_operators.md)voor meer informatie over logische Power shell-Opera tors.</span><span class="sxs-lookup"><span data-stu-id="31837-191">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="31837-192">Zie [about_Updatable_Help](./About/about_Updatable_Help.md)voor meer informatie over de Help-functie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="31837-192">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="31837-193">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31837-193">PARAMETERS</span></span>

### <span data-ttu-id="31837-194">-CContains</span><span class="sxs-lookup"><span data-stu-id="31837-194">-CContains</span></span>

<span data-ttu-id="31837-195">Geeft aan dat deze cmdlet objecten van een collectie ophaalt als de eigenschaps waarde van het object een exacte overeenkomst voor de opgegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="31837-195">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="31837-196">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-196">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-197">Bijvoorbeeld: `Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="31837-197">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="31837-198">**CContains** verwijst naar een verzameling waarden en is waar als de verzameling een item bevat dat exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-198">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="31837-199">Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="31837-199">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="31837-200">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-200">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-201">-CEQ</span><span class="sxs-lookup"><span data-stu-id="31837-201">-CEQ</span></span>

<span data-ttu-id="31837-202">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-202">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="31837-203">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-203">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-204">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-205">-CGE</span><span class="sxs-lookup"><span data-stu-id="31837-205">-CGE</span></span>

<span data-ttu-id="31837-206">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-206">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="31837-207">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-207">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-208">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-209">-CGT</span><span class="sxs-lookup"><span data-stu-id="31837-209">-CGT</span></span>

<span data-ttu-id="31837-210">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-210">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="31837-211">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-211">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-212">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-213">-CIn</span><span class="sxs-lookup"><span data-stu-id="31837-213">-CIn</span></span>

<span data-ttu-id="31837-214">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap de opgegeven waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="31837-214">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="31837-215">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-215">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-216">Bijvoorbeeld: `Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="31837-216">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="31837-217">**Cin** lijkt op **CContains** , behalve dat de positie van de eigenschap en de waarde worden omgekeerd.</span><span class="sxs-lookup"><span data-stu-id="31837-217">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="31837-218">De volgende instructies zijn bijvoorbeeld beide waar.</span><span class="sxs-lookup"><span data-stu-id="31837-218">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="31837-219">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-219">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-220">-CLE</span><span class="sxs-lookup"><span data-stu-id="31837-220">-CLE</span></span>

<span data-ttu-id="31837-221">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-221">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="31837-222">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-222">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-223">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-223">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-224">-CLike</span><span class="sxs-lookup"><span data-stu-id="31837-224">-CLike</span></span>

<span data-ttu-id="31837-225">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="31837-225">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="31837-226">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-226">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-227">Bijvoorbeeld: `Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="31837-227">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="31837-228">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-229">-CLT</span><span class="sxs-lookup"><span data-stu-id="31837-229">-CLT</span></span>

<span data-ttu-id="31837-230">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-230">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="31837-231">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-231">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-232">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-233">-CMatch</span><span class="sxs-lookup"><span data-stu-id="31837-233">-CMatch</span></span>

<span data-ttu-id="31837-234">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="31837-234">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="31837-235">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-235">This operation is case-sensitive.</span></span> <span data-ttu-id="31837-236">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="31837-236">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="31837-237">Bijvoorbeeld: `Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="31837-237">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="31837-238">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-239">-CNE</span><span class="sxs-lookup"><span data-stu-id="31837-239">-CNE</span></span>

<span data-ttu-id="31837-240">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap anders is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-240">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="31837-241">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-241">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-242">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-242">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-243">-CNotContains</span><span class="sxs-lookup"><span data-stu-id="31837-243">-CNotContains</span></span>

<span data-ttu-id="31837-244">Hiermee wordt aangegeven dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde van het object niet exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-244">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="31837-245">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-245">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-246">Bijvoorbeeld: `Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="31837-246">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="31837-247">**NotContains** en **CNotContains** verwijzen naar een verzameling waarden en zijn waar wanneer de verzameling geen items bevat die exact overeenkomen voor de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-247">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="31837-248">Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="31837-248">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="31837-249">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-250">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="31837-250">-CNotIn</span></span>

<span data-ttu-id="31837-251">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap niet exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-251">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="31837-252">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-252">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-253">Bijvoorbeeld: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="31837-253">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="31837-254">**NotIn** -en **CNotIn** -Opera tors lijken op **NotContains** en **CNotContains** , behalve dat de positie van de eigenschap en de waarde worden omgekeerd.</span><span class="sxs-lookup"><span data-stu-id="31837-254">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="31837-255">De volgende instructies zijn bijvoorbeeld waar.</span><span class="sxs-lookup"><span data-stu-id="31837-255">For example, the following statements are true.</span></span>

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-256">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="31837-256">-CNotLike</span></span>

<span data-ttu-id="31837-257">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="31837-257">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="31837-258">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-258">This operation is case-sensitive.</span></span>

<span data-ttu-id="31837-259">Bijvoorbeeld: `Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="31837-259">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="31837-260">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-261">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="31837-261">-CNotMatch</span></span>

<span data-ttu-id="31837-262">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="31837-262">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="31837-263">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="31837-263">This operation is case-sensitive.</span></span> <span data-ttu-id="31837-264">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="31837-264">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="31837-265">Bijvoorbeeld: `Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="31837-265">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="31837-266">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-267">-Bevat</span><span class="sxs-lookup"><span data-stu-id="31837-267">-Contains</span></span>

<span data-ttu-id="31837-268">Geeft aan dat met deze cmdlet objecten worden opgehaald als een item in de waarde van de eigenschap van het object een exacte overeenkomst voor de opgegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="31837-268">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="31837-269">Bijvoorbeeld: `Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="31837-269">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="31837-270">Als de waarde van de eigenschap één object bevat, wordt deze door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="31837-270">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="31837-271">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-272">-EQ</span><span class="sxs-lookup"><span data-stu-id="31837-272">-EQ</span></span>

<span data-ttu-id="31837-273">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-273">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="31837-274">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-274">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-275">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="31837-275">-FilterScript</span></span>

<span data-ttu-id="31837-276">Hiermee geeft u het script blok op dat wordt gebruikt voor het filteren van de objecten.</span><span class="sxs-lookup"><span data-stu-id="31837-276">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="31837-277">Plaats het script blok tussen accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="31837-277">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="31837-278">De parameter naam **FilterScript** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="31837-278">The parameter name, **FilterScript** , is optional.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-279">-GE</span><span class="sxs-lookup"><span data-stu-id="31837-279">-GE</span></span>

<span data-ttu-id="31837-280">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-280">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="31837-281">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-282">-GT</span><span class="sxs-lookup"><span data-stu-id="31837-282">-GT</span></span>

<span data-ttu-id="31837-283">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-283">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="31837-284">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-284">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-285">-In</span><span class="sxs-lookup"><span data-stu-id="31837-285">-In</span></span>

<span data-ttu-id="31837-286">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met een van de opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="31837-286">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="31837-287">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="31837-287">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="31837-288">Als de waarde van de para meter **Value** één object is, converteert Power shell deze naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="31837-288">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="31837-289">Als de eigenschaps waarde van een object een matrix is, gebruikt Power shell referentie gelijkheid om een overeenkomst te bepalen.</span><span class="sxs-lookup"><span data-stu-id="31837-289">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="31837-290">`Where-Object` retourneert het object alleen als de waarde van de **eigenschaps** parameter en een waarde van **waarde** hetzelfde exemplaar van een object zijn.</span><span class="sxs-lookup"><span data-stu-id="31837-290">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="31837-291">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-291">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-292">-Input object</span><span class="sxs-lookup"><span data-stu-id="31837-292">-InputObject</span></span>

<span data-ttu-id="31837-293">Geeft aan welke objecten moeten worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="31837-293">Specifies the objects to be filtered.</span></span> <span data-ttu-id="31837-294">U kunt de objecten ook door sluizen naar `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="31837-294">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="31837-295">Wanneer u de para meter **input object** gebruikt in `Where-Object` plaats van de resultaten van de pijpleiding opdracht, `Where-Object` wordt de waarde van **input object** behandeld als een enkel object.</span><span class="sxs-lookup"><span data-stu-id="31837-295">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="31837-296">Dit geldt ook als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="31837-296">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="31837-297">Omdat **input object** geen afzonderlijke eigenschappen van een matrix of verzameling van objecten kan retour neren, raden we u aan dat, als u gebruikt `Where-Object` om een verzameling objecten te filteren voor objecten die specifieke waarden in gedefinieerde eigenschappen hebben, u `Where-Object` in de pijp lijn gebruikt, zoals wordt weer gegeven in de voor beelden in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="31837-297">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="31837-298">-Is</span><span class="sxs-lookup"><span data-stu-id="31837-298">-Is</span></span>

<span data-ttu-id="31837-299">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap een exemplaar van het opgegeven .NET-type is.</span><span class="sxs-lookup"><span data-stu-id="31837-299">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="31837-300">Plaats de type naam tussen vier Kante haken.</span><span class="sxs-lookup"><span data-stu-id="31837-300">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="31837-301">bijvoorbeeld `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="31837-301">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="31837-302">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-302">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-303">-IsNot</span><span class="sxs-lookup"><span data-stu-id="31837-303">-IsNot</span></span>

<span data-ttu-id="31837-304">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde geen exemplaar van het opgegeven .NET-type is.</span><span class="sxs-lookup"><span data-stu-id="31837-304">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="31837-305">bijvoorbeeld `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="31837-305">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="31837-306">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-306">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-307">-LE</span><span class="sxs-lookup"><span data-stu-id="31837-307">-LE</span></span>

<span data-ttu-id="31837-308">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-308">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="31837-309">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-309">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-310">-Like</span><span class="sxs-lookup"><span data-stu-id="31837-310">-Like</span></span>

<span data-ttu-id="31837-311">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="31837-311">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="31837-312">Bijvoorbeeld: `Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="31837-312">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="31837-313">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-313">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-314">-LT</span><span class="sxs-lookup"><span data-stu-id="31837-314">-LT</span></span>

<span data-ttu-id="31837-315">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-315">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="31837-316">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-317">-Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="31837-317">-Match</span></span>

<span data-ttu-id="31837-318">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="31837-318">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="31837-319">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="31837-319">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="31837-320">Bijvoorbeeld: `Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="31837-320">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="31837-321">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-321">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-322">-NE</span><span class="sxs-lookup"><span data-stu-id="31837-322">-NE</span></span>

<span data-ttu-id="31837-323">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap anders is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-323">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="31837-324">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-324">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-325">-NotContains</span><span class="sxs-lookup"><span data-stu-id="31837-325">-NotContains</span></span>

<span data-ttu-id="31837-326">Hiermee wordt aangegeven dat met deze cmdlet objecten worden opgehaald als geen van de items in de waarde van de eigenschap een exacte overeenkomst voor de opgegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="31837-326">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="31837-327">Bijvoorbeeld: `Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="31837-327">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="31837-328">**NotContains** verwijst naar een verzameling waarden en is waar als de verzameling geen items bevat die exact overeenkomen voor de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="31837-328">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="31837-329">Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="31837-329">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="31837-330">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-330">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-331">-NotIn</span><span class="sxs-lookup"><span data-stu-id="31837-331">-NotIn</span></span>

<span data-ttu-id="31837-332">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap niet exact overeenkomt met een van de opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="31837-332">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="31837-333">Bijvoorbeeld: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="31837-333">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="31837-334">Als de waarde van de **waarde** één object is, converteert Power shell deze naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="31837-334">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="31837-335">Als de eigenschaps waarde van een object een matrix is, gebruikt Power shell referentie gelijkheid om een overeenkomst te bepalen.</span><span class="sxs-lookup"><span data-stu-id="31837-335">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="31837-336">`Where-Object` retourneert het object alleen als de waarde van de **eigenschap** en een waarde van de **waarde** niet hetzelfde exemplaar van een object zijn.</span><span class="sxs-lookup"><span data-stu-id="31837-336">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="31837-337">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-337">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-338">-NotLike</span><span class="sxs-lookup"><span data-stu-id="31837-338">-NotLike</span></span>

<span data-ttu-id="31837-339">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="31837-339">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="31837-340">Bijvoorbeeld: `Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="31837-340">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="31837-341">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-341">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-342">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="31837-342">-NotMatch</span></span>

<span data-ttu-id="31837-343">Geeft aan dat met deze cmdlet objecten worden opgehaald wanneer de eigenschaps waarde niet overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="31837-343">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="31837-344">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="31837-344">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="31837-345">Bijvoorbeeld: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="31837-345">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="31837-346">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-347">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="31837-347">-Property</span></span>

<span data-ttu-id="31837-348">Hiermee geeft u de naam van een object eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="31837-348">Specifies the name of an object property.</span></span> <span data-ttu-id="31837-349">De parameter naam, **eigenschap** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="31837-349">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="31837-350">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-350">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="31837-351">-Waarde</span><span class="sxs-lookup"><span data-stu-id="31837-351">-Value</span></span>

<span data-ttu-id="31837-352">Geeft een eigenschaps waarde aan.</span><span class="sxs-lookup"><span data-stu-id="31837-352">Specifies a property value.</span></span> <span data-ttu-id="31837-353">De parameter naam, **waarde** , is optioneel.</span><span class="sxs-lookup"><span data-stu-id="31837-353">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="31837-354">Deze para meter accepteert joker tekens wanneer ze worden gebruikt met de volgende vergelijkings parameters:</span><span class="sxs-lookup"><span data-stu-id="31837-354">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="31837-355">**CLike**</span><span class="sxs-lookup"><span data-stu-id="31837-355">**CLike**</span></span>
- <span data-ttu-id="31837-356">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="31837-356">**CNotLike**</span></span>
- <span data-ttu-id="31837-357">**Zo**</span><span class="sxs-lookup"><span data-stu-id="31837-357">**Like**</span></span>
- <span data-ttu-id="31837-358">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="31837-358">**NotLike**</span></span>

<span data-ttu-id="31837-359">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="31837-359">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="31837-360">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31837-360">CommonParameters</span></span>

<span data-ttu-id="31837-361">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="31837-361">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31837-362">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="31837-362">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31837-363">INVOER</span><span class="sxs-lookup"><span data-stu-id="31837-363">INPUTS</span></span>

### <span data-ttu-id="31837-364">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="31837-364">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="31837-365">U kunt de objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="31837-365">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="31837-366">UITVOER</span><span class="sxs-lookup"><span data-stu-id="31837-366">OUTPUTS</span></span>

### <span data-ttu-id="31837-367">Object</span><span class="sxs-lookup"><span data-stu-id="31837-367">Object</span></span>

<span data-ttu-id="31837-368">Met deze cmdlet worden geselecteerde items uit de invoer objectset geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="31837-368">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="31837-369">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="31837-369">NOTES</span></span>

<span data-ttu-id="31837-370">Starten in Windows Power Shell 4,0 `Where` en `ForEach` methoden zijn toegevoegd voor gebruik met verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="31837-370">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="31837-371">U kunt hier meer lezen over deze nieuwe methoden [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="31837-371">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="31837-372">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="31837-372">RELATED LINKS</span></span>

[<span data-ttu-id="31837-373">Compare-object</span><span class="sxs-lookup"><span data-stu-id="31837-373">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="31837-374">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="31837-374">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="31837-375">Groep-object</span><span class="sxs-lookup"><span data-stu-id="31837-375">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="31837-376">Meting object</span><span class="sxs-lookup"><span data-stu-id="31837-376">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="31837-377">New-Object</span><span class="sxs-lookup"><span data-stu-id="31837-377">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="31837-378">Select-Object</span><span class="sxs-lookup"><span data-stu-id="31837-378">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="31837-379">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="31837-379">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="31837-380">T-object</span><span class="sxs-lookup"><span data-stu-id="31837-380">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
