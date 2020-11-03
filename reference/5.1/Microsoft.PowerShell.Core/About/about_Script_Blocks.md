---
description: Definieert wat een script blok is en legt uit hoe script blokken moeten worden gebruikt in de programmeer taal Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: f842701d83c525e4695debf99c4725580661b1de
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252565"
---
# <a name="about-script-blocks"></a><span data-ttu-id="c82ae-104">Over script blokken</span><span class="sxs-lookup"><span data-stu-id="c82ae-104">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="c82ae-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="c82ae-105">Short description</span></span>

<span data-ttu-id="c82ae-106">Definieert wat een script blok is en legt uit hoe script blokken moeten worden gebruikt in de programmeer taal Power shell.</span><span class="sxs-lookup"><span data-stu-id="c82ae-106">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="c82ae-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="c82ae-107">Long description</span></span>

<span data-ttu-id="c82ae-108">In de programmeer taal van Power shell is een script blok een verzameling instructies of expressies die kunnen worden gebruikt als één eenheid.</span><span class="sxs-lookup"><span data-stu-id="c82ae-108">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="c82ae-109">Een script blok kan argumenten en retour waarden accepteren.</span><span class="sxs-lookup"><span data-stu-id="c82ae-109">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="c82ae-110">Een script blok is syntactisch een instructie lijst in accolades, zoals wordt weer gegeven in de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="c82ae-110">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="c82ae-111">Een script blok retourneert de uitvoer van alle opdrachten in het script blok, hetzij als een enkel object of als een matrix.</span><span class="sxs-lookup"><span data-stu-id="c82ae-111">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="c82ae-112">U kunt ook een retour waarde opgeven met behulp van het `return` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="c82ae-112">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="c82ae-113">Het `return` tref woord heeft geen invloed op of onderdrukt andere uitvoer die wordt geretourneerd door het script blok.</span><span class="sxs-lookup"><span data-stu-id="c82ae-113">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="c82ae-114">Het `return` sleutel woord sluit echter het script blok af op die regel.</span><span class="sxs-lookup"><span data-stu-id="c82ae-114">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="c82ae-115">Zie [about_Return](about_Return.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c82ae-115">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="c82ae-116">Net als bij functies kan een script blok para meters bevatten.</span><span class="sxs-lookup"><span data-stu-id="c82ae-116">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="c82ae-117">Gebruik het sleutel woord param om benoemde para meters toe te wijzen, zoals wordt weer gegeven in de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="c82ae-117">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="c82ae-118">In een-script blok, in tegens telling tot een functie, kunt u geen para meters opgeven buiten de accolades.</span><span class="sxs-lookup"><span data-stu-id="c82ae-118">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="c82ae-119">Net als bij functies kunnen script blokken de `DynamicParam` `Begin` `Process` sleutel woorden,, en bevatten `End` .</span><span class="sxs-lookup"><span data-stu-id="c82ae-119">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="c82ae-120">Zie [about_Functions](about_Functions.md) en [about_Functions_Advanced](about_Functions_Advanced.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c82ae-120">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="c82ae-121">Script blokken gebruiken</span><span class="sxs-lookup"><span data-stu-id="c82ae-121">Using Script Blocks</span></span>

<span data-ttu-id="c82ae-122">Een script blok is een exemplaar van een Microsoft .NET Framework-type `System.Management.Automation.ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="c82ae-122">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="c82ae-123">Opdrachten kunnen script Block-parameter waarden bevatten.</span><span class="sxs-lookup"><span data-stu-id="c82ae-123">Commands can have script block parameter values.</span></span> <span data-ttu-id="c82ae-124">De `Invoke-Command` cmdlet heeft bijvoorbeeld een `ScriptBlock` para meter die een script blok waarde nodig heeft, zoals wordt weer gegeven in dit voor beeld:</span><span class="sxs-lookup"><span data-stu-id="c82ae-124">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

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

<span data-ttu-id="c82ae-125">`Invoke-Command` kan ook script blokken met parameter blokken uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="c82ae-125">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="c82ae-126">Para meters worden toegewezen op basis van de positie met behulp van de para meter **argument List** .</span><span class="sxs-lookup"><span data-stu-id="c82ae-126">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

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

<span data-ttu-id="c82ae-127">In het script blok in het voor gaande voor beeld wordt het `param` sleutel woord gebruikt voor het maken van para meters `$p1` en `$p2` .</span><span class="sxs-lookup"><span data-stu-id="c82ae-127">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="c82ae-128">De teken reeks ' First ' is gebonden aan de eerste para meter ( `$p1` ) en ' Second ' is gebonden aan ( `$p2` ).</span><span class="sxs-lookup"><span data-stu-id="c82ae-128">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="c82ae-129">Zie [about_Splatting](about_Splatting.md#splatting-with-arrays)voor meer informatie over het gedrag van **argument List**.</span><span class="sxs-lookup"><span data-stu-id="c82ae-129">For more information about the behavior of **ArgumentList** , see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="c82ae-130">U kunt variabelen gebruiken om script blokken op te slaan en uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c82ae-130">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="c82ae-131">In het onderstaande voor beeld wordt een script blok in een variabele opgeslagen en door gegeven aan `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="c82ae-131">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="c82ae-132">De aanroep operator is een andere manier om script blokken uit te voeren die zijn opgeslagen in een variabele.</span><span class="sxs-lookup"><span data-stu-id="c82ae-132">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="c82ae-133">Net als `Invoke-Command` de aanroep operator voert het script blok uit in een onderliggend bereik.</span><span class="sxs-lookup"><span data-stu-id="c82ae-133">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="c82ae-134">De operator oproep kan het gemakkelijker maken om para meters met uw script blokken te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c82ae-134">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

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

<span data-ttu-id="c82ae-135">U kunt de uitvoer van uw script blokken in een variabele opslaan met behulp van de toewijzing.</span><span class="sxs-lookup"><span data-stu-id="c82ae-135">You can store the output from your script blocks in a variable using assignment.</span></span>

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

<span data-ttu-id="c82ae-136">Zie [about_Operators](about_Operators.md)voor meer informatie over de aanroep operator.</span><span class="sxs-lookup"><span data-stu-id="c82ae-136">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="c82ae-137">Gebruiken van vertraging-BIND script blokken met para meters</span><span class="sxs-lookup"><span data-stu-id="c82ae-137">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="c82ae-138">Een getypeerde para meter die pijplijn invoer ( `by Value` ) of () accepteert, `by PropertyName` maakt het gebruik van script blokken met **vertragings bindingen** mogelijk voor de para meter.</span><span class="sxs-lookup"><span data-stu-id="c82ae-138">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="c82ae-139">Binnen het script blok voor de **vertragings binding** kunt u verwijzen naar het pipet in object met behulp van de pijplijn variabele `$_` .</span><span class="sxs-lookup"><span data-stu-id="c82ae-139">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="c82ae-140">In complexere cmdlets kunt u met vertraging-BIND script blokken één piped in object opnieuw gebruiken om andere para meters in te vullen.</span><span class="sxs-lookup"><span data-stu-id="c82ae-140">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="c82ae-141">Opmerkingen bij **vertraging-** script blokken als para meters binden:</span><span class="sxs-lookup"><span data-stu-id="c82ae-141">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="c82ae-142">U moet expliciet parameter namen opgeven die u gebruikt met **vertragings-BIND** script blokken.</span><span class="sxs-lookup"><span data-stu-id="c82ae-142">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="c82ae-143">De para meter mag niet van het type ungetypeerde zijn en het parameter type mag niet zijn `[scriptblock]` of `[object]` .</span><span class="sxs-lookup"><span data-stu-id="c82ae-143">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="c82ae-144">U ontvangt een fout melding als u een **vertragings-BIND** script blok gebruikt zonder de invoer van de pijp lijn te leveren.</span><span class="sxs-lookup"><span data-stu-id="c82ae-144">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c82ae-145">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c82ae-145">See Also</span></span>

[<span data-ttu-id="c82ae-146">about_Functions</span><span class="sxs-lookup"><span data-stu-id="c82ae-146">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="c82ae-147">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="c82ae-147">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="c82ae-148">about_Operators</span><span class="sxs-lookup"><span data-stu-id="c82ae-148">about_Operators</span></span>](about_Operators.md)
