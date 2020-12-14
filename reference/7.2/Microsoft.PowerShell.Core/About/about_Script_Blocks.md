---
description: Definieert wat een script blok is en legt uit hoe script blokken moeten worden gebruikt in de programmeer taal Power shell.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 1ba5e92bedc03a2d61d528715ab13c5d96eb3075
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706212"
---
# <a name="about-script-blocks"></a><span data-ttu-id="d076d-103">Over script blokken</span><span class="sxs-lookup"><span data-stu-id="d076d-103">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="d076d-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="d076d-104">Short description</span></span>

<span data-ttu-id="d076d-105">Definieert wat een script blok is en legt uit hoe script blokken moeten worden gebruikt in de programmeer taal Power shell.</span><span class="sxs-lookup"><span data-stu-id="d076d-105">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="d076d-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="d076d-106">Long description</span></span>

<span data-ttu-id="d076d-107">In de programmeer taal van Power shell is een script blok een verzameling instructies of expressies die kunnen worden gebruikt als één eenheid.</span><span class="sxs-lookup"><span data-stu-id="d076d-107">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="d076d-108">Een script blok kan argumenten en retour waarden accepteren.</span><span class="sxs-lookup"><span data-stu-id="d076d-108">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="d076d-109">Een script blok is syntactisch een instructie lijst in accolades, zoals wordt weer gegeven in de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="d076d-109">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="d076d-110">Een script blok retourneert de uitvoer van alle opdrachten in het script blok, hetzij als een enkel object of als een matrix.</span><span class="sxs-lookup"><span data-stu-id="d076d-110">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="d076d-111">U kunt ook een retour waarde opgeven met behulp van het `return` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="d076d-111">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="d076d-112">Het `return` tref woord heeft geen invloed op of onderdrukt andere uitvoer die wordt geretourneerd door het script blok.</span><span class="sxs-lookup"><span data-stu-id="d076d-112">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="d076d-113">Het `return` sleutel woord sluit echter het script blok af op die regel.</span><span class="sxs-lookup"><span data-stu-id="d076d-113">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="d076d-114">Zie [about_Return](about_Return.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d076d-114">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="d076d-115">Net als bij functies kan een script blok para meters bevatten.</span><span class="sxs-lookup"><span data-stu-id="d076d-115">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="d076d-116">Gebruik het sleutel woord param om benoemde para meters toe te wijzen, zoals wordt weer gegeven in de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="d076d-116">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="d076d-117">In een-script blok, in tegens telling tot een functie, kunt u geen para meters opgeven buiten de accolades.</span><span class="sxs-lookup"><span data-stu-id="d076d-117">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="d076d-118">Net als bij functies kunnen script blokken de `DynamicParam` `Begin` `Process` sleutel woorden,, en bevatten `End` .</span><span class="sxs-lookup"><span data-stu-id="d076d-118">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="d076d-119">Zie [about_Functions](about_Functions.md) en [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d076d-119">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="d076d-120">Script blokken gebruiken</span><span class="sxs-lookup"><span data-stu-id="d076d-120">Using Script Blocks</span></span>

<span data-ttu-id="d076d-121">Een script blok is een exemplaar van een Microsoft .NET Framework-type `System.Management.Automation.ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="d076d-121">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="d076d-122">Opdrachten kunnen script Block-parameter waarden bevatten.</span><span class="sxs-lookup"><span data-stu-id="d076d-122">Commands can have script block parameter values.</span></span> <span data-ttu-id="d076d-123">De `Invoke-Command` cmdlet heeft bijvoorbeeld een `ScriptBlock` para meter die een script blok waarde nodig heeft, zoals wordt weer gegeven in dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="d076d-123">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

<span data-ttu-id="d076d-124">`Invoke-Command` kan ook script blokken met parameter blokken uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d076d-124">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="d076d-125">Para meters worden toegewezen op basis van de positie met behulp van de para meter **argument List** .</span><span class="sxs-lookup"><span data-stu-id="d076d-125">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

<span data-ttu-id="d076d-126">In het script blok in het voor gaande voor beeld wordt het `param` sleutel woord gebruikt voor het maken van para meters `$p1` en `$p2` .</span><span class="sxs-lookup"><span data-stu-id="d076d-126">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="d076d-127">De teken reeks ' First ' is gebonden aan de eerste para meter ( `$p1` ) en ' Second ' is gebonden aan ( `$p2` ).</span><span class="sxs-lookup"><span data-stu-id="d076d-127">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="d076d-128">Zie [about_Splatting](about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="d076d-128">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="d076d-129">U kunt variabelen gebruiken om script blokken op te slaan en uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d076d-129">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="d076d-130">In het onderstaande voor beeld wordt een script blok in een variabele opgeslagen en door gegeven aan `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="d076d-130">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="d076d-131">De aanroep operator is een andere manier om script blokken uit te voeren die zijn opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="d076d-131">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="d076d-132">Net als `Invoke-Command` de aanroep operator voert het script blok uit in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="d076d-132">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="d076d-133">De operator oproep kan het gemakkelijker maken om para meters met uw script blokken te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d076d-133">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

<span data-ttu-id="d076d-134">U kunt de uitvoer van uw script blokken in een variabele opslaan met behulp van de toewijzing.</span><span class="sxs-lookup"><span data-stu-id="d076d-134">You can store the output from your script blocks in a variable using assignment.</span></span>

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

<span data-ttu-id="d076d-135">Zie [about_Operators](about_Operators.md)voor meer informatie over de aanroep operator.</span><span class="sxs-lookup"><span data-stu-id="d076d-135">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="d076d-136">Gebruiken van vertraging-BIND script blokken met para meters</span><span class="sxs-lookup"><span data-stu-id="d076d-136">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="d076d-137">Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met **vertragings bindingen** mogelijk voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="d076d-137">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="d076d-138">Binnen het script blok voor de **vertragings binding** kunt u verwijzen naar het pipet in object met behulp van de pijplijn variabele `$_` .</span><span class="sxs-lookup"><span data-stu-id="d076d-138">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="d076d-139">In complexere cmdlets kunt u met vertraging-BIND script blokken één piped in object opnieuw gebruiken om andere para meters in te vullen.</span><span class="sxs-lookup"><span data-stu-id="d076d-139">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="d076d-140">Opmerkingen bij **vertraging-** script blokken als para meters binden:</span><span class="sxs-lookup"><span data-stu-id="d076d-140">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="d076d-141">U moet expliciet parameter namen opgeven die u gebruikt met **vertragings-BIND** script blokken.</span><span class="sxs-lookup"><span data-stu-id="d076d-141">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="d076d-142">De para meter mag niet van het type ungetypeerde zijn en het parameter type mag niet zijn `[scriptblock]` of `[object]` .</span><span class="sxs-lookup"><span data-stu-id="d076d-142">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="d076d-143">U ontvangt een fout melding als u een **vertragings-BIND** script blok gebruikt zonder de invoer van de pijp lijn te leveren.</span><span class="sxs-lookup"><span data-stu-id="d076d-143">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a><span data-ttu-id="d076d-144">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d076d-144">See Also</span></span>

[<span data-ttu-id="d076d-145">about_Functions</span><span class="sxs-lookup"><span data-stu-id="d076d-145">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="d076d-146">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="d076d-146">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="d076d-147">about_Operators</span><span class="sxs-lookup"><span data-stu-id="d076d-147">about_Operators</span></span>](about_Operators.md)

