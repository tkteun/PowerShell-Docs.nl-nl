---
description: Hierin wordt beschreven hoe de `continue` instructie direct de programma stroom retourneert naar de bovenkant van een programma-lus, een `switch` instructie of een- `trap` instructie.
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 36c14dc0489345083e8938c066cefa77e3f5ef8d
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/17/2020
ms.locfileid: "97614061"
---
# <a name="about-continue"></a><span data-ttu-id="b3e0a-103">Over gaan</span><span class="sxs-lookup"><span data-stu-id="b3e0a-103">About Continue</span></span>

## <a name="short-description"></a><span data-ttu-id="b3e0a-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="b3e0a-104">Short description</span></span>

<span data-ttu-id="b3e0a-105">Hierin wordt beschreven hoe de `continue` instructie direct de programma stroom retourneert naar de bovenkant van een programma-lus, een `switch` instructie of een- `trap` instructie.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-105">Describes how the `continue` statement immediately returns the program flow to the top of a program loop, a `switch` statement, or a `trap` statement.</span></span>

## <a name="long-description"></a><span data-ttu-id="b3e0a-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="b3e0a-106">Long description</span></span>

<span data-ttu-id="b3e0a-107">De `continue` instructie biedt een manier om het huidige besturings blok te sluiten, maar door te gaan met de uitvoering, in plaats van volledig te worden afgesloten.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-107">The `continue` statement provides a way to exit the current control block but continue execution, rather than exit completely.</span></span> <span data-ttu-id="b3e0a-108">De instructie ondersteunt labels.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-108">The statement supports labels.</span></span>
<span data-ttu-id="b3e0a-109">Een label is een naam die u toewijst aan een instructie in een script.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-109">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-continue-in-loops"></a><span data-ttu-id="b3e0a-110">Door gaan in lussen gebruiken</span><span class="sxs-lookup"><span data-stu-id="b3e0a-110">Using continue in loops</span></span>

<span data-ttu-id="b3e0a-111">Een instructie zonder label `continue` retourneert onmiddellijk de programma stroom naar de bovenkant van de binnenste lus die wordt beheerd door een `for` , `foreach` ,, `do` of- `while` instructie.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-111">An unlabeled `continue` statement immediately returns the program flow to the top of the innermost loop that is controlled by a `for`, `foreach`, `do`, or `while` statement.</span></span> <span data-ttu-id="b3e0a-112">De huidige herhaling van de lus wordt beëindigd en de lus gaat verder met de volgende iteratie.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-112">The current iteration of the loop is terminated and the loop continues with the next iteration.</span></span>

<span data-ttu-id="b3e0a-113">In het volgende voor beeld keert programma flow terug naar de bovenkant van de `while` lus als de `$ctr` variabele gelijk is aan 5.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-113">In the following example, program flow returns to the top of the `while` loop if the `$ctr` variable is equal to 5.</span></span> <span data-ttu-id="b3e0a-114">Als gevolg hiervan worden alle getallen tussen 1 en 10 weer gegeven, met uitzonde ring van 5:</span><span class="sxs-lookup"><span data-stu-id="b3e0a-114">As a result, all the numbers between 1 and 10 are displayed except for 5:</span></span>

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

<span data-ttu-id="b3e0a-115">Wanneer u een `for` lus gebruikt, wordt de uitvoering voortgezet volgens de `<Repeat>` instructie, gevolgd door de `<Condition>` test.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-115">When using a `for` loop, execution continues at the `<Repeat>` statement, followed by the `<Condition>` test.</span></span> <span data-ttu-id="b3e0a-116">In het onderstaande voor beeld wordt een oneindige lus niet uitgevoerd omdat het verstrijken van `$i` plaatsvindt na het `continue` sleutel woord.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-116">In the example below, an infinite loop will not occur because the decrement of `$i` occurs after the `continue` keyword.</span></span>

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a><span data-ttu-id="b3e0a-117">Het gebruik van een label door gaan in een lus</span><span class="sxs-lookup"><span data-stu-id="b3e0a-117">Using a labeled continue in a loop</span></span>

<span data-ttu-id="b3e0a-118">Een `continue` instructie met het label beëindigt de uitvoering van de iteratie en brengt de controle over naar het doel label dat moet worden omsloten of `switch` afschriften.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-118">A labeled `continue` statement terminates execution of the iteration and transfers control to the targeted enclosing iteration or `switch` statement label.</span></span>

<span data-ttu-id="b3e0a-119">In het volgende voor beeld wordt het binnenste `for` beëindigd wanneer `$condition` is ingesteld op **True** en wordt iteratie voortgezet met de tweede `for` lus op `labelB` .</span><span class="sxs-lookup"><span data-stu-id="b3e0a-119">In the following example, the innermost `for` is terminated when `$condition` is **True** and iteration continues with the second `for` loop at `labelB`.</span></span>

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a><span data-ttu-id="b3e0a-120">Door gaan in een switch-instructie gebruiken</span><span class="sxs-lookup"><span data-stu-id="b3e0a-120">Using continue in a switch statement</span></span>

<span data-ttu-id="b3e0a-121">Een niet-gelabelde `continue` instructie in `switch` de uitvoering van de huidige `switch` iteratie wordt beëindigd en de besturings elementen worden overgeboekt naar de bovenkant `switch` om het volgende invoer item op te halen.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-121">An unlabeled `continue` statement within a `switch` terminates execution of the current `switch` iteration and transfers control to the top of the `switch` to get the next input item.</span></span>

<span data-ttu-id="b3e0a-122">Als er één invoer item is, wordt `continue` het volledige `switch` overzicht afgesloten.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-122">When there is a single input item `continue` exits the entire `switch` statement.</span></span>
<span data-ttu-id="b3e0a-123">Wanneer de `switch` invoer een verzameling is, wordt `switch` elk element van de verzameling getest.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-123">When the `switch` input is a collection, the `switch` tests each element of the collection.</span></span> <span data-ttu-id="b3e0a-124">Hiermee wordt de `continue` huidige herhaling afgesloten en wordt het `switch` volgende element voortgezet.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-124">The `continue` exits the current iteration and the `switch` continues with the next element.</span></span>

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a><span data-ttu-id="b3e0a-125">Door gaan in een trap-instructie gebruiken</span><span class="sxs-lookup"><span data-stu-id="b3e0a-125">Using continue in a trap statement</span></span>

<span data-ttu-id="b3e0a-126">Als de laatste instructie die wordt uitgevoerd in de hoofd tekst een `trap` instructie is `continue` , wordt de ondergevulde fout op de achtergrond genegeerd en wordt de uitvoering voortgezet met de instructie die de oorzaak is van het `trap` probleem.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-126">If the final statement executed in the body a `trap` statement is `continue`, the trapped error is silently ignored and execution continues with the statement immediately following the one that caused `trap` to occur.</span></span>

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="b3e0a-127">Gebruik niet door gaan buiten een lus, switch of trap</span><span class="sxs-lookup"><span data-stu-id="b3e0a-127">Do not use continue outside of a loop, switch, or trap</span></span>

<span data-ttu-id="b3e0a-128">Wanneer `continue` wordt gebruikt buiten een constructie die deze direct ondersteunt (lussen, `switch` ,, `trap` ), zoekt Power shell _de aanroep stack_ voor een insluitende constructie.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-128">When `continue` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="b3e0a-129">Als er geen insluitende constructie kan worden gevonden, wordt de huidige runs Pace stil beëindigd.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-129">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="b3e0a-130">Dit betekent dat functies en scripts die per ongeluk gebruikmaken `continue` van een insluitende constructie die het ondersteunt, de _aanroepers_ per ongeluk kunnen beëindigen.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-130">This means that functions and scripts that inadvertently use a `continue` outside of an enclosing construct that supports it, can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="b3e0a-131">`continue`Als u een pijp lijn gebruikt, zoals een- `ForEach-Object` script blok, wordt de pijp lijn niet alleen afgesloten, waardoor de volledige runs Pace wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="b3e0a-131">Using `continue` inside a pipeline, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3e0a-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b3e0a-132">See also</span></span>

[<span data-ttu-id="b3e0a-133">about_Break</span><span class="sxs-lookup"><span data-stu-id="b3e0a-133">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="b3e0a-134">about_For</span><span class="sxs-lookup"><span data-stu-id="b3e0a-134">about_For</span></span>](about_For.md)

[<span data-ttu-id="b3e0a-135">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="b3e0a-135">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="b3e0a-136">about_Throw</span><span class="sxs-lookup"><span data-stu-id="b3e0a-136">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="b3e0a-137">about_Trap</span><span class="sxs-lookup"><span data-stu-id="b3e0a-137">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="b3e0a-138">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="b3e0a-138">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)