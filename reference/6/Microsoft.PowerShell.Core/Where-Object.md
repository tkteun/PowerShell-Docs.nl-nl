---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: 4f80fb0a980da81cf3da0e0ea4ae7ca8e4ad2a39
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251216"
---
# <span data-ttu-id="62d77-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="62d77-103">Where-Object</span></span>

## <span data-ttu-id="62d77-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="62d77-104">SYNOPSIS</span></span>
<span data-ttu-id="62d77-105">Selecteert objecten uit een verzameling op basis van de bijbehorende eigenschaps waarden.</span><span class="sxs-lookup"><span data-stu-id="62d77-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="62d77-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="62d77-106">SYNTAX</span></span>

### <span data-ttu-id="62d77-107">Gelijkset (standaard)</span><span class="sxs-lookup"><span data-stu-id="62d77-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="62d77-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="62d77-109">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="62d77-109">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="62d77-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="62d77-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="62d77-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="62d77-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="62d77-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="62d77-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="62d77-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="62d77-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-118">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="62d77-118">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-119">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="62d77-119">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-120">Like-set</span><span class="sxs-lookup"><span data-stu-id="62d77-120">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-121">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="62d77-121">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-122">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="62d77-122">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-123">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="62d77-123">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-124">Overeenkomstset</span><span class="sxs-lookup"><span data-stu-id="62d77-124">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="62d77-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="62d77-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="62d77-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-128">Contains bevat</span><span class="sxs-lookup"><span data-stu-id="62d77-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="62d77-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="62d77-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="62d77-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-132">Pentekenen</span><span class="sxs-lookup"><span data-stu-id="62d77-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="62d77-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="62d77-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="62d77-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="62d77-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="62d77-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### <span data-ttu-id="62d77-138">Not</span><span class="sxs-lookup"><span data-stu-id="62d77-138">Not</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## <span data-ttu-id="62d77-139">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="62d77-139">DESCRIPTION</span></span>

<span data-ttu-id="62d77-140">De `Where-Object` cmdlet selecteert objecten met bepaalde eigenschaps waarden uit de verzameling van objecten die worden door gegeven.</span><span class="sxs-lookup"><span data-stu-id="62d77-140">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="62d77-141">U kunt bijvoorbeeld de `Where-Object` -cmdlet gebruiken om bestanden te selecteren die zijn gemaakt na een bepaalde datum, gebeurtenissen met een bepaalde id of computers die gebruikmaken van een bepaalde versie van Windows.</span><span class="sxs-lookup"><span data-stu-id="62d77-141">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="62d77-142">Vanaf Windows Power Shell 3,0 zijn er twee verschillende manieren om een opdracht te maken `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="62d77-142">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="62d77-143">**Script blok**.</span><span class="sxs-lookup"><span data-stu-id="62d77-143">**Script block**.</span></span> <span data-ttu-id="62d77-144">U kunt een script blok gebruiken om de naam van de eigenschap, een vergelijkings operator en een eigenschaps waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="62d77-144">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="62d77-145">`Where-Object` retourneert alle objecten waarvoor de instructie script blok is ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="62d77-145">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="62d77-146">Met de volgende opdracht worden bijvoorbeeld processen in de klasse met normale prioriteit opgehaald, dat wil zeggen, processen waarbij de waarde van de eigenschap **PriorityClass** gelijk is aan normaal.</span><span class="sxs-lookup"><span data-stu-id="62d77-146">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="62d77-147">Alle Power shell-vergelijkings operatoren zijn geldig in de script blok indeling.</span><span class="sxs-lookup"><span data-stu-id="62d77-147">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="62d77-148">Zie [about_Comparison_Operators](./About/about_Comparison_Operators.md)voor meer informatie over vergelijkings operatoren.</span><span class="sxs-lookup"><span data-stu-id="62d77-148">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="62d77-149">**Vergelijkings instructie**.</span><span class="sxs-lookup"><span data-stu-id="62d77-149">**Comparison statement**.</span></span> <span data-ttu-id="62d77-150">U kunt ook een vergelijkings instructie schrijven die veel meer lijkt op natuurlijke taal.</span><span class="sxs-lookup"><span data-stu-id="62d77-150">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="62d77-151">Vergelijkings instructies zijn geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-151">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="62d77-152">Met de volgende opdrachten worden ook processen opgehaald die de prioriteits klasse normaal hebben.</span><span class="sxs-lookup"><span data-stu-id="62d77-152">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="62d77-153">Deze opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62d77-153">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="62d77-154">Vanuit Windows Power Shell 3,0 worden `Where-Object` vergelijkings operatoren als para meters toegevoegd aan een `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="62d77-154">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="62d77-155">Tenzij opgegeven, zijn alle Opera tors niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-155">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="62d77-156">Vóór Windows Power Shell 3,0 kan de vergelijkings operators in de Power shell-taal alleen worden gebruikt in script blokken.</span><span class="sxs-lookup"><span data-stu-id="62d77-156">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="62d77-157">Wanneer u één **eigenschap** opgeeft `Where-Object` , wordt de waarde van de eigenschap behandeld als een booleaanse expressie.</span><span class="sxs-lookup"><span data-stu-id="62d77-157">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="62d77-158">Als de waarde van **Length** niet gelijk is aan nul, wordt de expressie geëvalueerd als **waar**.</span><span class="sxs-lookup"><span data-stu-id="62d77-158">When the value of **Length** is not zero, the expression evaluates to **True**.</span></span> <span data-ttu-id="62d77-159">Bijvoorbeeld: `('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="62d77-159">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="62d77-160">Het vorige voor beeld is functioneel equivalent aan:</span><span class="sxs-lookup"><span data-stu-id="62d77-160">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="62d77-161">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="62d77-161">EXAMPLES</span></span>

### <span data-ttu-id="62d77-162">Voor beeld 1: gestopt services ophalen</span><span class="sxs-lookup"><span data-stu-id="62d77-162">Example 1: Get stopped services</span></span>

<span data-ttu-id="62d77-163">Met deze opdrachten wordt een lijst weer geven met alle services die momenteel zijn gestopt.</span><span class="sxs-lookup"><span data-stu-id="62d77-163">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="62d77-164">De `$_` Automatische variabele vertegenwoordigt elk object dat wordt door gegeven aan de `Where-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62d77-164">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="62d77-165">De eerste opdracht maakt gebruik van de script blok indeling. de tweede opdracht maakt gebruik van de indeling van de vergelijkings instructie.</span><span class="sxs-lookup"><span data-stu-id="62d77-165">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="62d77-166">De opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62d77-166">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="62d77-167">Voor beeld 2: processen ophalen op basis van werkset</span><span class="sxs-lookup"><span data-stu-id="62d77-167">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="62d77-168">Met deze opdrachten worden processen weer geven die een werkset hebben die groter is dan 250 mega bytes (KB).</span><span class="sxs-lookup"><span data-stu-id="62d77-168">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="62d77-169">De syntaxis van de script Block en-instructie zijn gelijk en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62d77-169">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="62d77-170">Voor beeld 3: processen ophalen op basis van proces naam</span><span class="sxs-lookup"><span data-stu-id="62d77-170">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="62d77-171">Met deze opdrachten worden de processen opgehaald die de waarde van de eigenschap **proces** naam hebben die begint met de letter `p` .</span><span class="sxs-lookup"><span data-stu-id="62d77-171">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="62d77-172">Met de operator **match** kunt u reguliere expressie overeenkomsten gebruiken.</span><span class="sxs-lookup"><span data-stu-id="62d77-172">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="62d77-173">De syntaxis van de script Block en-instructie zijn gelijk en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62d77-173">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="62d77-174">Voor beeld 4: de indeling van de vergelijkings instructie gebruiken</span><span class="sxs-lookup"><span data-stu-id="62d77-174">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="62d77-175">In dit voor beeld ziet u hoe u de nieuwe indeling van de vergelijkings instructie van de `Where-Object` cmdlet gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62d77-175">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="62d77-176">De eerste opdracht maakt gebruik van de indeling van de vergelijkings instructie.</span><span class="sxs-lookup"><span data-stu-id="62d77-176">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="62d77-177">In deze opdracht worden geen aliassen gebruikt en alle para meters bevatten de parameter naam.</span><span class="sxs-lookup"><span data-stu-id="62d77-177">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="62d77-178">De tweede opdracht is het natuurlijke gebruik van de opdracht notatie voor vergelijking.</span><span class="sxs-lookup"><span data-stu-id="62d77-178">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="62d77-179">De `where` alias wordt vervangen door de naam van de `Where-Object` cmdlet en alle optionele parameter namen worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="62d77-179">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="62d77-180">Voor beeld 5: opdrachten ophalen op basis van eigenschappen</span><span class="sxs-lookup"><span data-stu-id="62d77-180">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="62d77-181">In dit voor beeld ziet u hoe u opdrachten schrijft die items retour neren die waar of onwaar zijn of een wille keurige waarde hebben voor een opgegeven eigenschap.</span><span class="sxs-lookup"><span data-stu-id="62d77-181">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="62d77-182">Elk voor beeld toont zowel het script blok als de indeling van de vergelijkings instructie voor de opdracht.</span><span class="sxs-lookup"><span data-stu-id="62d77-182">Each example shows both the script block and comparison statement formats for the command.</span></span>

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

### <span data-ttu-id="62d77-183">Voor beeld 6: meerdere voor waarden gebruiken</span><span class="sxs-lookup"><span data-stu-id="62d77-183">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="62d77-184">In dit voor beeld ziet u hoe u een `Where-Object` opdracht met meerdere voor waarden maakt.</span><span class="sxs-lookup"><span data-stu-id="62d77-184">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="62d77-185">Met deze opdracht worden niet-kern modules opgehaald die ondersteuning bieden voor de Help-functie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="62d77-185">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="62d77-186">De opdracht gebruikt de para meter **ListAvailable** van de `Get-Module` cmdlet om alle modules op de computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="62d77-186">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="62d77-187">Een pijplijn operator ( `|` ) verzendt de modules naar de `Where-Object` cmdlet, die modules ophaalt waarvan de namen niet beginnen met micro soft of PS, en een waarde hebben voor de eigenschap **HelpInfoURI** , die Power shell vertelt waar bijgewerkte Help-bestanden voor de module moeten worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="62d77-187">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="62d77-188">De vergelijkings instructies zijn verbonden door de operator **and** .</span><span class="sxs-lookup"><span data-stu-id="62d77-188">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="62d77-189">In het voor beeld wordt de script blok opdracht indeling gebruikt.</span><span class="sxs-lookup"><span data-stu-id="62d77-189">The example uses the script block command format.</span></span> <span data-ttu-id="62d77-190">Logische Opera Tors, zoals **en** en **of** , zijn alleen geldig in script blokken.</span><span class="sxs-lookup"><span data-stu-id="62d77-190">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="62d77-191">U kunt ze niet gebruiken in de indeling van de vergelijkings instructie van een `Where-Object` opdracht.</span><span class="sxs-lookup"><span data-stu-id="62d77-191">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="62d77-192">Zie [about_Logical_Operators](./About/about_logical_operators.md)voor meer informatie over logische Power shell-Opera tors.</span><span class="sxs-lookup"><span data-stu-id="62d77-192">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="62d77-193">Zie [about_Updatable_Help](./About/about_Updatable_Help.md)voor meer informatie over de Help-functie die kan worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="62d77-193">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="62d77-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="62d77-194">PARAMETERS</span></span>

### <span data-ttu-id="62d77-195">-CContains</span><span class="sxs-lookup"><span data-stu-id="62d77-195">-CContains</span></span>

<span data-ttu-id="62d77-196">Geeft aan dat deze cmdlet objecten van een collectie ophaalt als de eigenschaps waarde van het object een exacte overeenkomst voor de opgegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="62d77-196">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="62d77-197">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-197">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-198">Bijvoorbeeld: `Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="62d77-198">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="62d77-199">**CContains** verwijst naar een verzameling waarden en is waar als de verzameling een item bevat dat exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-199">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="62d77-200">Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="62d77-200">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="62d77-201">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-202">-CEQ</span><span class="sxs-lookup"><span data-stu-id="62d77-202">-CEQ</span></span>

<span data-ttu-id="62d77-203">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-203">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="62d77-204">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-204">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-205">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-206">-CGE</span><span class="sxs-lookup"><span data-stu-id="62d77-206">-CGE</span></span>

<span data-ttu-id="62d77-207">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-207">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="62d77-208">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-208">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-209">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-209">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-210">-CGT</span><span class="sxs-lookup"><span data-stu-id="62d77-210">-CGT</span></span>

<span data-ttu-id="62d77-211">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-211">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="62d77-212">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-212">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-213">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-213">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-214">-CIn</span><span class="sxs-lookup"><span data-stu-id="62d77-214">-CIn</span></span>

<span data-ttu-id="62d77-215">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap de opgegeven waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="62d77-215">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="62d77-216">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-216">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-217">Bijvoorbeeld: `Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="62d77-217">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="62d77-218">**Cin** lijkt op **CContains** , behalve dat de positie van de eigenschap en de waarde worden omgekeerd.</span><span class="sxs-lookup"><span data-stu-id="62d77-218">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="62d77-219">De volgende instructies zijn bijvoorbeeld beide waar.</span><span class="sxs-lookup"><span data-stu-id="62d77-219">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="62d77-220">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-221">-CLE</span><span class="sxs-lookup"><span data-stu-id="62d77-221">-CLE</span></span>

<span data-ttu-id="62d77-222">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-222">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="62d77-223">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-223">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-224">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-225">-CLike</span><span class="sxs-lookup"><span data-stu-id="62d77-225">-CLike</span></span>

<span data-ttu-id="62d77-226">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="62d77-226">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="62d77-227">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-227">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-228">Bijvoorbeeld: `Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="62d77-228">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="62d77-229">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-230">-CLT</span><span class="sxs-lookup"><span data-stu-id="62d77-230">-CLT</span></span>

<span data-ttu-id="62d77-231">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-231">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="62d77-232">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-232">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-233">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-233">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-234">-CMatch</span><span class="sxs-lookup"><span data-stu-id="62d77-234">-CMatch</span></span>

<span data-ttu-id="62d77-235">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="62d77-235">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="62d77-236">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-236">This operation is case-sensitive.</span></span> <span data-ttu-id="62d77-237">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="62d77-237">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="62d77-238">Bijvoorbeeld: `Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="62d77-238">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="62d77-239">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-240">-CNE</span><span class="sxs-lookup"><span data-stu-id="62d77-240">-CNE</span></span>

<span data-ttu-id="62d77-241">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap anders is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-241">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="62d77-242">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-242">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-243">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-244">-CNotContains</span><span class="sxs-lookup"><span data-stu-id="62d77-244">-CNotContains</span></span>

<span data-ttu-id="62d77-245">Hiermee wordt aangegeven dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde van het object niet exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-245">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="62d77-246">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-246">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-247">Bijvoorbeeld: `Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="62d77-247">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="62d77-248">**NotContains** en **CNotContains** verwijzen naar een verzameling waarden en zijn waar wanneer de verzameling geen items bevat die exact overeenkomen voor de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-248">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="62d77-249">Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="62d77-249">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="62d77-250">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-251">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="62d77-251">-CNotIn</span></span>

<span data-ttu-id="62d77-252">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap niet exact overeenkomt met de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-252">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="62d77-253">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-253">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-254">Bijvoorbeeld: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="62d77-254">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="62d77-255">**NotIn** -en **CNotIn** -Opera tors lijken op **NotContains** en **CNotContains** , behalve dat de positie van de eigenschap en de waarde worden omgekeerd.</span><span class="sxs-lookup"><span data-stu-id="62d77-255">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="62d77-256">De volgende instructies zijn bijvoorbeeld waar.</span><span class="sxs-lookup"><span data-stu-id="62d77-256">For example, the following statements are true.</span></span>

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

### <span data-ttu-id="62d77-257">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="62d77-257">-CNotLike</span></span>

<span data-ttu-id="62d77-258">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="62d77-258">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="62d77-259">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-259">This operation is case-sensitive.</span></span>

<span data-ttu-id="62d77-260">Bijvoorbeeld: `Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="62d77-260">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="62d77-261">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-262">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="62d77-262">-CNotMatch</span></span>

<span data-ttu-id="62d77-263">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="62d77-263">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="62d77-264">Deze bewerking is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="62d77-264">This operation is case-sensitive.</span></span> <span data-ttu-id="62d77-265">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="62d77-265">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="62d77-266">Bijvoorbeeld: `Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="62d77-266">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="62d77-267">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-268">-Bevat</span><span class="sxs-lookup"><span data-stu-id="62d77-268">-Contains</span></span>

<span data-ttu-id="62d77-269">Geeft aan dat met deze cmdlet objecten worden opgehaald als een item in de waarde van de eigenschap van het object een exacte overeenkomst voor de opgegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="62d77-269">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="62d77-270">Bijvoorbeeld: `Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="62d77-270">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="62d77-271">Als de waarde van de eigenschap één object bevat, wordt deze door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="62d77-271">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="62d77-272">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-273">-EQ</span><span class="sxs-lookup"><span data-stu-id="62d77-273">-EQ</span></span>

<span data-ttu-id="62d77-274">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-274">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="62d77-275">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-276">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="62d77-276">-FilterScript</span></span>

<span data-ttu-id="62d77-277">Hiermee geeft u het script blok op dat wordt gebruikt voor het filteren van de objecten.</span><span class="sxs-lookup"><span data-stu-id="62d77-277">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="62d77-278">Plaats het script blok tussen accolades ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="62d77-278">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="62d77-279">De parameter naam **FilterScript** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="62d77-279">The parameter name, **FilterScript** , is optional.</span></span>

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

### <span data-ttu-id="62d77-280">-GE</span><span class="sxs-lookup"><span data-stu-id="62d77-280">-GE</span></span>

<span data-ttu-id="62d77-281">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-281">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="62d77-282">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-282">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-283">-GT</span><span class="sxs-lookup"><span data-stu-id="62d77-283">-GT</span></span>

<span data-ttu-id="62d77-284">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap groter is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-284">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="62d77-285">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-286">-In</span><span class="sxs-lookup"><span data-stu-id="62d77-286">-In</span></span>

<span data-ttu-id="62d77-287">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met een van de opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="62d77-287">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="62d77-288">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="62d77-288">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="62d77-289">Als de waarde van de para meter **Value** één object is, converteert Power shell deze naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="62d77-289">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="62d77-290">Als de eigenschaps waarde van een object een matrix is, gebruikt Power shell referentie gelijkheid om een overeenkomst te bepalen.</span><span class="sxs-lookup"><span data-stu-id="62d77-290">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="62d77-291">`Where-Object` retourneert het object alleen als de waarde van de **eigenschaps** parameter en een waarde van **waarde** hetzelfde exemplaar van een object zijn.</span><span class="sxs-lookup"><span data-stu-id="62d77-291">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="62d77-292">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-293">-Input object</span><span class="sxs-lookup"><span data-stu-id="62d77-293">-InputObject</span></span>

<span data-ttu-id="62d77-294">Geeft aan welke objecten moeten worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="62d77-294">Specifies the objects to be filtered.</span></span> <span data-ttu-id="62d77-295">U kunt de objecten ook door sluizen naar `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="62d77-295">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="62d77-296">Wanneer u de para meter **input object** gebruikt in `Where-Object` plaats van de resultaten van de pijpleiding opdracht, `Where-Object` wordt de waarde van **input object** behandeld als een enkel object.</span><span class="sxs-lookup"><span data-stu-id="62d77-296">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="62d77-297">Dit geldt ook als de waarde een verzameling is die het resultaat is van een opdracht, zoals `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="62d77-297">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="62d77-298">Omdat **input object** geen afzonderlijke eigenschappen van een matrix of verzameling van objecten kan retour neren, raden we u aan dat, als u gebruikt `Where-Object` om een verzameling objecten te filteren voor objecten die specifieke waarden in gedefinieerde eigenschappen hebben, u `Where-Object` in de pijp lijn gebruikt, zoals wordt weer gegeven in de voor beelden in dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="62d77-298">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="62d77-299">-Is</span><span class="sxs-lookup"><span data-stu-id="62d77-299">-Is</span></span>

<span data-ttu-id="62d77-300">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap een exemplaar van het opgegeven .NET-type is.</span><span class="sxs-lookup"><span data-stu-id="62d77-300">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="62d77-301">Plaats de type naam tussen vier Kante haken.</span><span class="sxs-lookup"><span data-stu-id="62d77-301">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="62d77-302">bijvoorbeeld `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="62d77-302">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="62d77-303">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-303">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-304">-IsNot</span><span class="sxs-lookup"><span data-stu-id="62d77-304">-IsNot</span></span>

<span data-ttu-id="62d77-305">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde geen exemplaar van het opgegeven .NET-type is.</span><span class="sxs-lookup"><span data-stu-id="62d77-305">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="62d77-306">bijvoorbeeld `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="62d77-306">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="62d77-307">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-307">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-308">-LE</span><span class="sxs-lookup"><span data-stu-id="62d77-308">-LE</span></span>

<span data-ttu-id="62d77-309">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan of gelijk is aan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-309">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="62d77-310">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-310">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-311">-Like</span><span class="sxs-lookup"><span data-stu-id="62d77-311">-Like</span></span>

<span data-ttu-id="62d77-312">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="62d77-312">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="62d77-313">Bijvoorbeeld: `Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="62d77-313">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="62d77-314">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-314">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-315">-LT</span><span class="sxs-lookup"><span data-stu-id="62d77-315">-LT</span></span>

<span data-ttu-id="62d77-316">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap kleiner is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-316">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="62d77-317">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-317">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-318">-Overeenkomst</span><span class="sxs-lookup"><span data-stu-id="62d77-318">-Match</span></span>

<span data-ttu-id="62d77-319">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="62d77-319">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="62d77-320">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="62d77-320">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="62d77-321">Bijvoorbeeld: `Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="62d77-321">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="62d77-322">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-323">-NE</span><span class="sxs-lookup"><span data-stu-id="62d77-323">-NE</span></span>

<span data-ttu-id="62d77-324">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap anders is dan de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-324">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="62d77-325">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-326">-Niet</span><span class="sxs-lookup"><span data-stu-id="62d77-326">-Not</span></span>

<span data-ttu-id="62d77-327">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschap niet bestaat of de waarde null of False heeft.</span><span class="sxs-lookup"><span data-stu-id="62d77-327">Indicates that this cmdlet gets objects if the property does not exist or has a value of null or false.</span></span>

<span data-ttu-id="62d77-328">Bijvoorbeeld: `Get-Service | where -Not "DependentServices"`</span><span class="sxs-lookup"><span data-stu-id="62d77-328">For example: `Get-Service | where -Not "DependentServices"`</span></span>

<span data-ttu-id="62d77-329">Deze para meter is geïntroduceerd in Windows Power shell 6,1.</span><span class="sxs-lookup"><span data-stu-id="62d77-329">This parameter was introduced in Windows PowerShell 6.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62d77-330">-NotContains</span><span class="sxs-lookup"><span data-stu-id="62d77-330">-NotContains</span></span>

<span data-ttu-id="62d77-331">Hiermee wordt aangegeven dat met deze cmdlet objecten worden opgehaald als geen van de items in de waarde van de eigenschap een exacte overeenkomst voor de opgegeven waarde is.</span><span class="sxs-lookup"><span data-stu-id="62d77-331">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="62d77-332">Bijvoorbeeld: `Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="62d77-332">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="62d77-333">**NotContains** verwijst naar een verzameling waarden en is waar als de verzameling geen items bevat die exact overeenkomen voor de opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="62d77-333">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="62d77-334">Als de invoer één object is, wordt dit door Power shell geconverteerd naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="62d77-334">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="62d77-335">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-335">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-336">-NotIn</span><span class="sxs-lookup"><span data-stu-id="62d77-336">-NotIn</span></span>

<span data-ttu-id="62d77-337">Geeft aan dat met deze cmdlet objecten worden opgehaald als de waarde van de eigenschap niet exact overeenkomt met een van de opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="62d77-337">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="62d77-338">Bijvoorbeeld: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="62d77-338">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="62d77-339">Als de waarde van de **waarde** één object is, converteert Power shell deze naar een verzameling van één object.</span><span class="sxs-lookup"><span data-stu-id="62d77-339">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="62d77-340">Als de eigenschaps waarde van een object een matrix is, gebruikt Power shell referentie gelijkheid om een overeenkomst te bepalen.</span><span class="sxs-lookup"><span data-stu-id="62d77-340">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="62d77-341">`Where-Object` retourneert het object alleen als de waarde van de **eigenschap** en een waarde van de **waarde** niet hetzelfde exemplaar van een object zijn.</span><span class="sxs-lookup"><span data-stu-id="62d77-341">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="62d77-342">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-342">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-343">-NotLike</span><span class="sxs-lookup"><span data-stu-id="62d77-343">-NotLike</span></span>

<span data-ttu-id="62d77-344">Geeft aan dat met deze cmdlet objecten worden opgehaald als de eigenschaps waarde niet overeenkomt met een waarde die joker tekens bevat.</span><span class="sxs-lookup"><span data-stu-id="62d77-344">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="62d77-345">Bijvoorbeeld: `Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="62d77-345">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="62d77-346">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-347">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="62d77-347">-NotMatch</span></span>

<span data-ttu-id="62d77-348">Geeft aan dat met deze cmdlet objecten worden opgehaald wanneer de eigenschaps waarde niet overeenkomt met de opgegeven reguliere expressie.</span><span class="sxs-lookup"><span data-stu-id="62d77-348">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="62d77-349">Wanneer de invoer scalair is, wordt de overeenkomende waarde opgeslagen in de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="62d77-349">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="62d77-350">Bijvoorbeeld: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="62d77-350">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="62d77-351">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-351">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="62d77-352">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="62d77-352">-Property</span></span>

<span data-ttu-id="62d77-353">Hiermee geeft u de naam van een object eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="62d77-353">Specifies the name of an object property.</span></span> <span data-ttu-id="62d77-354">De parameter naam, **eigenschap** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="62d77-354">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="62d77-355">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-355">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, CaseSensitiveNotLikeSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="62d77-356">-Waarde</span><span class="sxs-lookup"><span data-stu-id="62d77-356">-Value</span></span>

<span data-ttu-id="62d77-357">Geeft een eigenschaps waarde aan.</span><span class="sxs-lookup"><span data-stu-id="62d77-357">Specifies a property value.</span></span> <span data-ttu-id="62d77-358">De parameter naam, **waarde** , is optioneel.</span><span class="sxs-lookup"><span data-stu-id="62d77-358">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="62d77-359">Deze para meter accepteert joker tekens wanneer ze worden gebruikt met de volgende vergelijkings parameters:</span><span class="sxs-lookup"><span data-stu-id="62d77-359">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="62d77-360">**CLike**</span><span class="sxs-lookup"><span data-stu-id="62d77-360">**CLike**</span></span>
- <span data-ttu-id="62d77-361">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="62d77-361">**CNotLike**</span></span>
- <span data-ttu-id="62d77-362">**Zo**</span><span class="sxs-lookup"><span data-stu-id="62d77-362">**Like**</span></span>
- <span data-ttu-id="62d77-363">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="62d77-363">**NotLike**</span></span>

<span data-ttu-id="62d77-364">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="62d77-364">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Object
Parameter Sets: EqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="62d77-365">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="62d77-365">CommonParameters</span></span>

<span data-ttu-id="62d77-366">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="62d77-366">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="62d77-367">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="62d77-367">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="62d77-368">INVOER</span><span class="sxs-lookup"><span data-stu-id="62d77-368">INPUTS</span></span>

### <span data-ttu-id="62d77-369">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="62d77-369">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="62d77-370">U kunt de objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="62d77-370">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="62d77-371">UITVOER</span><span class="sxs-lookup"><span data-stu-id="62d77-371">OUTPUTS</span></span>

### <span data-ttu-id="62d77-372">Object</span><span class="sxs-lookup"><span data-stu-id="62d77-372">Object</span></span>

<span data-ttu-id="62d77-373">Met deze cmdlet worden geselecteerde items uit de invoer objectset geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="62d77-373">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="62d77-374">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="62d77-374">NOTES</span></span>

<span data-ttu-id="62d77-375">Starten in Windows Power Shell 4,0 `Where` en `ForEach` methoden zijn toegevoegd voor gebruik met verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="62d77-375">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="62d77-376">U kunt hier meer lezen over deze nieuwe methoden [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="62d77-376">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="62d77-377">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="62d77-377">RELATED LINKS</span></span>

[<span data-ttu-id="62d77-378">Compare-object</span><span class="sxs-lookup"><span data-stu-id="62d77-378">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="62d77-379">ForEach-object</span><span class="sxs-lookup"><span data-stu-id="62d77-379">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="62d77-380">Groep-object</span><span class="sxs-lookup"><span data-stu-id="62d77-380">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="62d77-381">Meting object</span><span class="sxs-lookup"><span data-stu-id="62d77-381">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="62d77-382">New-Object</span><span class="sxs-lookup"><span data-stu-id="62d77-382">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="62d77-383">Select-Object</span><span class="sxs-lookup"><span data-stu-id="62d77-383">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="62d77-384">Sorteer object</span><span class="sxs-lookup"><span data-stu-id="62d77-384">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="62d77-385">T-object</span><span class="sxs-lookup"><span data-stu-id="62d77-385">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)