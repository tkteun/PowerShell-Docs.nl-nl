---
description: Hierin wordt een instructie beschreven die u kunt gebruiken voor het direct afsluiten,,,, `foreach` `for` `while` `do` `switch` of `trap` instructies.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: a50b98c1ec816658d353173eee9743c49e25c2a4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252632"
---
# <a name="about-break"></a><span data-ttu-id="9f185-104">Over onderbreken</span><span class="sxs-lookup"><span data-stu-id="9f185-104">About Break</span></span>

## <a name="short-description"></a><span data-ttu-id="9f185-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f185-105">Short description</span></span>

<span data-ttu-id="9f185-106">Hierin wordt een instructie beschreven die u kunt gebruiken voor het direct afsluiten,,,, `foreach` `for` `while` `do` `switch` of `trap` instructies.</span><span class="sxs-lookup"><span data-stu-id="9f185-106">Describes a statement you can use to immediately exit `foreach`, `for`, `while`, `do`, `switch`, or `trap` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="9f185-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="9f185-107">Long description</span></span>

<span data-ttu-id="9f185-108">De `break` instructie biedt een manier om het huidige besturings blok af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="9f185-108">The `break` statement provides a way to exit the current control block.</span></span>
<span data-ttu-id="9f185-109">De uitvoering wordt voortgezet bij de volgende instructie na het controle blok.</span><span class="sxs-lookup"><span data-stu-id="9f185-109">Execution continues at the next statement after the control block.</span></span> <span data-ttu-id="9f185-110">De instructie ondersteunt labels.</span><span class="sxs-lookup"><span data-stu-id="9f185-110">The statement supports labels.</span></span> <span data-ttu-id="9f185-111">Een label is een naam die u toewijst aan een instructie in een script.</span><span class="sxs-lookup"><span data-stu-id="9f185-111">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-break-in-loops"></a><span data-ttu-id="9f185-112">Einden in lussen gebruiken</span><span class="sxs-lookup"><span data-stu-id="9f185-112">Using break in loops</span></span>

<span data-ttu-id="9f185-113">Wanneer een `break` instructie wordt weer gegeven in een lus, zoals een `foreach` ,, `for` `do` , of `while` lus, wordt de lus onmiddellijk afgesloten door Power shell.</span><span class="sxs-lookup"><span data-stu-id="9f185-113">When a `break` statement appears in a loop, such as a `foreach`, `for`, `do`, or `while` loop, PowerShell immediately exits the loop.</span></span>

<span data-ttu-id="9f185-114">Een `break` instructie kan een label bevatten waarmee u Inge sloten lussen kunt sluiten.</span><span class="sxs-lookup"><span data-stu-id="9f185-114">A `break` statement can include a label that lets you exit embedded loops.</span></span> <span data-ttu-id="9f185-115">Een label kan elk wille keurig lus-tref woord opgeven, zoals `foreach` , `for` of `while` , in een script.</span><span class="sxs-lookup"><span data-stu-id="9f185-115">A label can specify any loop keyword, such as `foreach`, `for`, or `while`, in a script.</span></span>

<span data-ttu-id="9f185-116">In het volgende voor beeld ziet u hoe u een instructie kunt gebruiken `break` om een instructie af te sluiten `for` :</span><span class="sxs-lookup"><span data-stu-id="9f185-116">The following example shows how to use a `break` statement to exit a `for` statement:</span></span>

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

<span data-ttu-id="9f185-117">In dit voor beeld `break` sluit de instructie de `for` lus af wanneer de `$i` variabele gelijk is aan 1.</span><span class="sxs-lookup"><span data-stu-id="9f185-117">In this example, the `break` statement exits the `for` loop when the `$i` variable equals 1.</span></span> <span data-ttu-id="9f185-118">Hoewel de `for` instructie evalueert naar **True** tot `$i` groter is dan 10, heeft Power shell de instructie einde bereikt wanneer de lus voor het eerst `for` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f185-118">Even though the `for` statement evaluates to **True** until `$i` is greater than 10, PowerShell reaches the break statement the first time the `for` loop is run.</span></span>

<span data-ttu-id="9f185-119">Het is vaak gebruikelijk om de instructie te gebruiken `break` in een lus waarbij aan een interne voor waarde moet worden voldaan.</span><span class="sxs-lookup"><span data-stu-id="9f185-119">It is more common to use the `break` statement in a loop where an inner condition must be met.</span></span> <span data-ttu-id="9f185-120">Bekijk het volgende `foreach` voor beeld van de instructie:</span><span class="sxs-lookup"><span data-stu-id="9f185-120">Consider the following `foreach` statement example:</span></span>

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

<span data-ttu-id="9f185-121">In dit voor beeld wordt de matrix door de `foreach` instructie herhaald `$varB` .</span><span class="sxs-lookup"><span data-stu-id="9f185-121">In this example, the `foreach` statement iterates the `$varB` array.</span></span> <span data-ttu-id="9f185-122">De `if` instructie evalueert naar onwaar als de eerste twee keer dat de lus wordt uitgevoerd en de variabele `$i` wordt verhoogd met 1.</span><span class="sxs-lookup"><span data-stu-id="9f185-122">The `if` statement evaluates to False the first two times the loop is run and the variable `$i` is incremented by 1.</span></span> <span data-ttu-id="9f185-123">De derde keer dat de lus wordt uitgevoerd, `$i` is gelijk aan 2 en de `$val` variabele is 30.</span><span class="sxs-lookup"><span data-stu-id="9f185-123">The third time the loop is run, `$i` equals 2, and the `$val` variable equals 30.</span></span> <span data-ttu-id="9f185-124">Op dit punt wordt de `break` instructie uitgevoerd en wordt de `foreach` lus afgesloten.</span><span class="sxs-lookup"><span data-stu-id="9f185-124">At this point, the `break` statement runs, and the `foreach` loop exits.</span></span>

### <a name="using-a-labeled-break-in-a-loop"></a><span data-ttu-id="9f185-125">Een einde met een label in een lus gebruiken</span><span class="sxs-lookup"><span data-stu-id="9f185-125">Using a labeled break in a loop</span></span>

<span data-ttu-id="9f185-126">Een `break` instructie kan een label bevatten.</span><span class="sxs-lookup"><span data-stu-id="9f185-126">A `break` statement can include a label.</span></span> <span data-ttu-id="9f185-127">Als u het `break` sleutel woord met een label gebruikt, wordt de lus met het label in Power shell afgesloten in plaats van de huidige lus af te sluiten.</span><span class="sxs-lookup"><span data-stu-id="9f185-127">If you use the `break` keyword with a label, PowerShell exits the labeled loop instead of exiting the current loop.</span></span>
<span data-ttu-id="9f185-128">Het label is een dubbele punt gevolgd door een naam die u toewijst.</span><span class="sxs-lookup"><span data-stu-id="9f185-128">The label is a colon followed by a name that you assign.</span></span> <span data-ttu-id="9f185-129">Het label moet het eerste token in een instructie zijn en moet worden gevolgd door het tref woord voor herhaling, zoals `while` .</span><span class="sxs-lookup"><span data-stu-id="9f185-129">The label must be the first token in a statement, and it must be followed by the looping keyword, such as `while`.</span></span>

<span data-ttu-id="9f185-130">`break` Hiermee verplaatst u de uitvoering uit de gelabelde lus.</span><span class="sxs-lookup"><span data-stu-id="9f185-130">`break` moves execution out of the labeled loop.</span></span> <span data-ttu-id="9f185-131">In Inge sloten lussen heeft dit een ander resultaat dan het `break` tref woord heeft wanneer het wordt gebruikt door zichzelf.</span><span class="sxs-lookup"><span data-stu-id="9f185-131">In embedded loops, this has a different result than the `break` keyword has when it is used by itself.</span></span> <span data-ttu-id="9f185-132">Dit voor beeld heeft een `while` instructie met een `for` instructie:</span><span class="sxs-lookup"><span data-stu-id="9f185-132">This example has a `while` statement with a `for` statement:</span></span>

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

<span data-ttu-id="9f185-133">Als voor waarde 2 resulteert in **waar** , wordt de uitvoering van het script naar de instructie overgeslagen na de gelabelde lus.</span><span class="sxs-lookup"><span data-stu-id="9f185-133">If condition 2 evaluates to **True** , the execution of the script skips down to the statement after the labeled loop.</span></span> <span data-ttu-id="9f185-134">In het voor beeld wordt de uitvoering opnieuw gestart met de-instructie `$a = $c` .</span><span class="sxs-lookup"><span data-stu-id="9f185-134">In the example, execution starts again with the statement `$a = $c`.</span></span>

<span data-ttu-id="9f185-135">U kunt veel gelabelde lussen nesten, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="9f185-135">You can nest many labeled loops, as shown in the following example.</span></span>

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

<span data-ttu-id="9f185-136">Als de `$b` variabele wordt geëvalueerd als waar, wordt de uitvoering van het script hervat na de lus met de naam ' rood '.</span><span class="sxs-lookup"><span data-stu-id="9f185-136">If the `$b` variable evaluates to True, execution of the script resumes after the loop that is labeled "red".</span></span> <span data-ttu-id="9f185-137">Als de `$c` variabele wordt geëvalueerd als waar, wordt de uitvoering van het script-besturings element hervat na de lus met de naam geel.</span><span class="sxs-lookup"><span data-stu-id="9f185-137">If the `$c` variable evaluates to True, execution of the script control resumes after the loop that is labeled "yellow".</span></span>

<span data-ttu-id="9f185-138">Als de `$a` variabele wordt geëvalueerd als waar, wordt de uitvoering hervat na de binnenste lus.</span><span class="sxs-lookup"><span data-stu-id="9f185-138">If the `$a` variable evaluates to True, execution resumes after the innermost loop.</span></span> <span data-ttu-id="9f185-139">Er is geen label vereist.</span><span class="sxs-lookup"><span data-stu-id="9f185-139">No label is needed.</span></span>

<span data-ttu-id="9f185-140">Power shell beperkt de uitvoering van de labels mogelijk niet.</span><span class="sxs-lookup"><span data-stu-id="9f185-140">PowerShell does not limit how far labels can resume execution.</span></span> <span data-ttu-id="9f185-141">Het label kan zelfs de controle over de grenzen van scripts en functie aanroepen door geven.</span><span class="sxs-lookup"><span data-stu-id="9f185-141">The label can even pass control across script and function call boundaries.</span></span>

## <a name="using-break-in-a-switch-statement"></a><span data-ttu-id="9f185-142">De instructie Restore gebruiken voor een switch</span><span class="sxs-lookup"><span data-stu-id="9f185-142">Using break in a switch statement</span></span>

<span data-ttu-id="9f185-143">In een `switch` Construct wordt `break` met Power shell het `switch` code blok afgesloten.</span><span class="sxs-lookup"><span data-stu-id="9f185-143">In a `switch`construct, `break` causes PowerShell to exit the `switch` code block.</span></span>

<span data-ttu-id="9f185-144">Het `break` sleutel woord wordt gebruikt om de `switch` Construct te verlaten.</span><span class="sxs-lookup"><span data-stu-id="9f185-144">The `break` keyword is used to leave the `switch` construct.</span></span> <span data-ttu-id="9f185-145">De volgende `switch` instructie gebruikt bijvoorbeeld `break` instructies om te testen op de meest specifieke voor waarde:</span><span class="sxs-lookup"><span data-stu-id="9f185-145">For example, the following `switch` statement uses `break` statements to test for the most specific condition:</span></span>

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

<span data-ttu-id="9f185-146">In dit voor beeld `$var` wordt de variabele gemaakt en geïnitialiseerd naar een teken reeks waarde van `word2` .</span><span class="sxs-lookup"><span data-stu-id="9f185-146">In this example, the `$var` variable is created and initialized to a string value of `word2`.</span></span> <span data-ttu-id="9f185-147">De `switch` instructie gebruikt de **regex** -klasse om de variabele waarde eerst te vergelijken met de term `word2` .</span><span class="sxs-lookup"><span data-stu-id="9f185-147">The `switch` statement uses the **Regex** class to match the variable value first with the term `word2`.</span></span> <span data-ttu-id="9f185-148">Omdat de waarde van de variabele en de eerste test in de `switch` instructie overeenkomen, wordt het eerste code blok in de `switch` instructie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9f185-148">Because the variable value and the first test in the `switch` statement match, the first code block in the `switch` statement runs.</span></span>

<span data-ttu-id="9f185-149">Wanneer Power shell de eerste `break` instructie bereikt, wordt de `switch` instructie afgesloten.</span><span class="sxs-lookup"><span data-stu-id="9f185-149">When PowerShell reaches the first `break` statement, the `switch` statement exits.</span></span> <span data-ttu-id="9f185-150">Als de vier `break` instructies uit het voor beeld worden verwijderd, worden aan alle vier voor waarden voldaan.</span><span class="sxs-lookup"><span data-stu-id="9f185-150">If the four `break` statements are removed from the example, all four conditions are met.</span></span> <span data-ttu-id="9f185-151">In dit voor beeld wordt de- `break` instructie gebruikt voor het weer geven van resultaten wanneer aan de meest specifieke voor waarde wordt voldaan.</span><span class="sxs-lookup"><span data-stu-id="9f185-151">This example uses the `break` statement to display results when the most specific condition is met.</span></span>

## <a name="using-break-in-a-trap-statement"></a><span data-ttu-id="9f185-152">Onderbreken gebruiken in een instructie trap</span><span class="sxs-lookup"><span data-stu-id="9f185-152">Using break in a trap statement</span></span>

<span data-ttu-id="9f185-153">Als de laatste instructie in de hoofd tekst van een `trap` instructie is uitgevoerd `break` , wordt het fout object onderdrukt en wordt de uitzonde ring opnieuw gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9f185-153">If the final statement executed in the body of a `trap` statement is `break`, the error object is suppressed and the exception is re-thrown.</span></span>

<span data-ttu-id="9f185-154">In het volgende voor beeld wordt een **DivideByZeroException** -uitzonde ring gemaakt die wordt gevuld met de- `trap` instructie.</span><span class="sxs-lookup"><span data-stu-id="9f185-154">The following example create a **DivideByZeroException** exception that is trapped using the `trap` statement.</span></span>

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

U ziet dat de uitvoering stopt bij de uitzonde ring. <span data-ttu-id="9f185-156">De `After loop` is nooit bereikt.</span><span class="sxs-lookup"><span data-stu-id="9f185-156">The `After loop` is never reached.</span></span>
<span data-ttu-id="9f185-157">De uitzonde ring wordt opnieuw gegenereerd na de `trap` uitvoering.</span><span class="sxs-lookup"><span data-stu-id="9f185-157">The exception is re-thrown after the `trap` executes.</span></span>

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
Attempted to divide by zero.
At line:10 char:6
+      "1 / $i = " + (1 / $i--)
+      ~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RuntimeException
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="9f185-158">Geen breek punt gebruiken buiten een lus, switch of trap</span><span class="sxs-lookup"><span data-stu-id="9f185-158">Do not use break outside of a loop, switch, or trap</span></span>

<span data-ttu-id="9f185-159">Wanneer `break` wordt gebruikt buiten een constructie die deze direct ondersteunt (lussen, `switch` ,, `trap` ), zoekt Power shell _de aanroep stack_ voor een insluitende constructie.</span><span class="sxs-lookup"><span data-stu-id="9f185-159">When `break` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="9f185-160">Als er geen insluitende constructie kan worden gevonden, wordt de huidige runs Pace stil beëindigd.</span><span class="sxs-lookup"><span data-stu-id="9f185-160">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="9f185-161">Dit betekent dat functies en scripts die per ongeluk gebruikmaken `break` van een insluitende constructie die het ondersteunt, de _aanroepers_ per ongeluk kunnen beëindigen.</span><span class="sxs-lookup"><span data-stu-id="9f185-161">This means that functions and scripts that inadvertently use a `break` outside of an enclosing construct that supports it can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="9f185-162">`break`Als u een pijp lijn gebruikt `break` , zoals een- `ForEach-Object` script blok, wordt de pijp lijn niet alleen afgesloten, waardoor de volledige runs Pace wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="9f185-162">Using `break` inside a pipeline `break`, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f185-163">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9f185-163">See also</span></span>

[<span data-ttu-id="9f185-164">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="9f185-164">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="9f185-165">about_Continue</span><span class="sxs-lookup"><span data-stu-id="9f185-165">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="9f185-166">about_For</span><span class="sxs-lookup"><span data-stu-id="9f185-166">about_For</span></span>](about_For.md)

[<span data-ttu-id="9f185-167">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="9f185-167">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="9f185-168">about_Switch</span><span class="sxs-lookup"><span data-stu-id="9f185-168">about_Switch</span></span>](about_Switch.md)

[<span data-ttu-id="9f185-169">about_Throw</span><span class="sxs-lookup"><span data-stu-id="9f185-169">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="9f185-170">about_Trap</span><span class="sxs-lookup"><span data-stu-id="9f185-170">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="9f185-171">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="9f185-171">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

[<span data-ttu-id="9f185-172">about_While</span><span class="sxs-lookup"><span data-stu-id="9f185-172">about_While</span></span>](about_While.md)
