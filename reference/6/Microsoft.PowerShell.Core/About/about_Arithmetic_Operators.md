---
description: Hierin worden de Opera tors beschreven voor het uitvoeren van berekeningen in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: c7885e31e4b5b661473d5241b6629bbe05810824
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252385"
---
# <a name="about-arithmetic-operators"></a><span data-ttu-id="0547e-104">Over reken kundige Opera tors</span><span class="sxs-lookup"><span data-stu-id="0547e-104">About Arithmetic Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="0547e-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0547e-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="0547e-106">Hierin worden de Opera tors beschreven voor het uitvoeren van berekeningen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0547e-106">Describes the operators that perform arithmetic in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="0547e-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="0547e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="0547e-108">Reken kundige Opera tors berekenen numerieke waarden.</span><span class="sxs-lookup"><span data-stu-id="0547e-108">Arithmetic operators calculate numeric values.</span></span> <span data-ttu-id="0547e-109">U kunt een of meer wiskundige opera toren gebruiken om waarden toe te voegen, af te trekken, te vermenigvuldigen en te delen en om de rest (modulus) van een delings bewerking te berekenen.</span><span class="sxs-lookup"><span data-stu-id="0547e-109">You can use one or more arithmetic operators to add, subtract, multiply, and divide values, and to calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="0547e-110">Daarnaast kunnen de operator voor optellen ( `+` ) en de operator voor vermenigvuldiging ( `*` ) ook worden gebruikt voor teken reeksen, matrices en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="0547e-110">In addition, the addition operator (`+`) and multiplication operator (`*`) also operate on strings, arrays, and hash tables.</span></span> <span data-ttu-id="0547e-111">De operator voor optellen voegt de invoer toe.</span><span class="sxs-lookup"><span data-stu-id="0547e-111">The addition operator concatenates the input.</span></span> <span data-ttu-id="0547e-112">De vermenigvuldigings operator retourneert meerdere exemplaren van de invoer.</span><span class="sxs-lookup"><span data-stu-id="0547e-112">The multiplication operator returns multiple copies of the input.</span></span> <span data-ttu-id="0547e-113">U kunt zelfs object typen in een reken kundige instructie combi neren.</span><span class="sxs-lookup"><span data-stu-id="0547e-113">You can even mix object types in an arithmetic statement.</span></span> <span data-ttu-id="0547e-114">De methode die wordt gebruikt om de instructie te evalueren, wordt bepaald door het type van het meest linkse object in de expressie.</span><span class="sxs-lookup"><span data-stu-id="0547e-114">The method that is used to evaluate the statement is determined by the type of the leftmost object in the expression.</span></span>

<span data-ttu-id="0547e-115">Vanaf Power Shell 2,0 werken alle reken kundige Opera tors met 64-bits getallen.</span><span class="sxs-lookup"><span data-stu-id="0547e-115">Beginning in PowerShell 2.0, all arithmetic operators work on 64-bit numbers.</span></span>

<span data-ttu-id="0547e-116">Vanaf Power Shell 3,0 worden de `-shr` (Shift-rechts) en `-shl` (Shift-links) toegevoegd ter ondersteuning van bitsgewijze berekeningen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0547e-116">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are added to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="0547e-117">Power shell ondersteunt de volgende reken kundige Opera tors:</span><span class="sxs-lookup"><span data-stu-id="0547e-117">PowerShell supports the following arithmetic operators:</span></span>

|<span data-ttu-id="0547e-118">Operator</span><span class="sxs-lookup"><span data-stu-id="0547e-118">Operator</span></span>|<span data-ttu-id="0547e-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0547e-119">Description</span></span>                       |<span data-ttu-id="0547e-120">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="0547e-120">Example</span></span>                      |
|--------|----------------------------------|-----------------------------|
| +      |<span data-ttu-id="0547e-121">Voegt gehele getallen toe; voegt</span><span class="sxs-lookup"><span data-stu-id="0547e-121">Adds integers; concatenates</span></span>       |`6 + 2`                      |
|        |<span data-ttu-id="0547e-122">Teken reeksen, matrices en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="0547e-122">strings, arrays, and hash tables.</span></span> |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |<span data-ttu-id="0547e-123">Trekt een waarde van een ander af</span><span class="sxs-lookup"><span data-stu-id="0547e-123">Subtracts one value from another</span></span>  |`6 - 2`                      |
|        |<span data-ttu-id="0547e-124">waarde</span><span class="sxs-lookup"><span data-stu-id="0547e-124">value</span></span>                             |                             |
| -      |<span data-ttu-id="0547e-125">Maakt een getal een negatief getal</span><span class="sxs-lookup"><span data-stu-id="0547e-125">Makes a number a negative number</span></span>  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |<span data-ttu-id="0547e-126">Getallen vermenigvuldigen of teken reeksen kopiëren</span><span class="sxs-lookup"><span data-stu-id="0547e-126">Multiply numbers or copy strings</span></span>  |`6 * 2`                      |
|        |<span data-ttu-id="0547e-127">en arrays het opgegeven getal</span><span class="sxs-lookup"><span data-stu-id="0547e-127">and arrays the specified number</span></span>   |`@("!") * 4`                 |
|        |<span data-ttu-id="0547e-128">van de tijden.</span><span class="sxs-lookup"><span data-stu-id="0547e-128">of times.</span></span>                         |`"!" * 3`                    |
| /      |<span data-ttu-id="0547e-129">Deelt twee waarden.</span><span class="sxs-lookup"><span data-stu-id="0547e-129">Divides two values.</span></span>               |`6 / 2`                      |
| %      |<span data-ttu-id="0547e-130">Modulus-retourneert het restant van</span><span class="sxs-lookup"><span data-stu-id="0547e-130">Modulus - returns the remainder of</span></span>|`7 % 2`                      |
|        |<span data-ttu-id="0547e-131">een delings bewerking.</span><span class="sxs-lookup"><span data-stu-id="0547e-131">a division operation.</span></span>             |                             |
|<span data-ttu-id="0547e-132">-band</span><span class="sxs-lookup"><span data-stu-id="0547e-132">-band</span></span>   |<span data-ttu-id="0547e-133">Bitsgewijze AND</span><span class="sxs-lookup"><span data-stu-id="0547e-133">Bitwise AND</span></span>                       |`5 -band 3`                  |
|<span data-ttu-id="0547e-134">-bniet</span><span class="sxs-lookup"><span data-stu-id="0547e-134">-bnot</span></span>   |<span data-ttu-id="0547e-135">Bitsgewijze NOT</span><span class="sxs-lookup"><span data-stu-id="0547e-135">Bitwise NOT</span></span>                       |`-bnot 5`                    |
|<span data-ttu-id="0547e-136">-Bof</span><span class="sxs-lookup"><span data-stu-id="0547e-136">-bor</span></span>    |<span data-ttu-id="0547e-137">Bitsgewijze OR</span><span class="sxs-lookup"><span data-stu-id="0547e-137">Bitwise OR</span></span>                        |`5 -bor 0x03`                |
|<span data-ttu-id="0547e-138">-bxor</span><span class="sxs-lookup"><span data-stu-id="0547e-138">-bxor</span></span>   |<span data-ttu-id="0547e-139">Bitsgewijze XOR</span><span class="sxs-lookup"><span data-stu-id="0547e-139">Bitwise XOR</span></span>                       |`5 -bxor 3`                  |
|<span data-ttu-id="0547e-140">-shl</span><span class="sxs-lookup"><span data-stu-id="0547e-140">-shl</span></span>    |<span data-ttu-id="0547e-141">Hiermee worden bits naar links geschoven</span><span class="sxs-lookup"><span data-stu-id="0547e-141">Shifts bits to the left</span></span>           |`102 -shl 2`                 |
|<span data-ttu-id="0547e-142">-SHR</span><span class="sxs-lookup"><span data-stu-id="0547e-142">-shr</span></span>    |<span data-ttu-id="0547e-143">Hiermee worden de bits naar rechts verplaatst</span><span class="sxs-lookup"><span data-stu-id="0547e-143">Shifts bits to the right</span></span>          |`102 -shr 2`                 |

<span data-ttu-id="0547e-144">De operator voor bitsgewijs werken alleen bij typen van gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="0547e-144">The bitwise operators only work on integer types.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="0547e-145">OPERATOR PRIORITEIT</span><span class="sxs-lookup"><span data-stu-id="0547e-145">OPERATOR PRECEDENCE</span></span>

<span data-ttu-id="0547e-146">Power shell verwerkt reken kundige Opera tors in de volgende volg orde:</span><span class="sxs-lookup"><span data-stu-id="0547e-146">PowerShell processes arithmetic operators in the following order:</span></span>

|<span data-ttu-id="0547e-147">Prioriteit</span><span class="sxs-lookup"><span data-stu-id="0547e-147">Precedence</span></span>|<span data-ttu-id="0547e-148">Operator</span><span class="sxs-lookup"><span data-stu-id="0547e-148">Operator</span></span>          |<span data-ttu-id="0547e-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0547e-149">Description</span></span>                            |
|----------|------------------|---------------------------------------|
|<span data-ttu-id="0547e-150">1</span><span class="sxs-lookup"><span data-stu-id="0547e-150">1</span></span>         | `()`             |<span data-ttu-id="0547e-151">Haakjes</span><span class="sxs-lookup"><span data-stu-id="0547e-151">Parentheses</span></span>                            |
|<span data-ttu-id="0547e-152">2</span><span class="sxs-lookup"><span data-stu-id="0547e-152">2</span></span>         | `-`              |<span data-ttu-id="0547e-153">Voor een negatief getal of een unaire operator</span><span class="sxs-lookup"><span data-stu-id="0547e-153">For a negative number or unary operator</span></span>|
|<span data-ttu-id="0547e-154">3</span><span class="sxs-lookup"><span data-stu-id="0547e-154">3</span></span>         | <span data-ttu-id="0547e-155">`*`, `/`, `%`</span><span class="sxs-lookup"><span data-stu-id="0547e-155">`*`, `/`, `%`</span></span>    |<span data-ttu-id="0547e-156">Voor vermenigvuldiging en deling</span><span class="sxs-lookup"><span data-stu-id="0547e-156">For multiplication and division</span></span>        |
|<span data-ttu-id="0547e-157">4</span><span class="sxs-lookup"><span data-stu-id="0547e-157">4</span></span>         | <span data-ttu-id="0547e-158">`+`, `-`</span><span class="sxs-lookup"><span data-stu-id="0547e-158">`+`, `-`</span></span>         |<span data-ttu-id="0547e-159">Voor optellen en aftrekken</span><span class="sxs-lookup"><span data-stu-id="0547e-159">For addition and subtraction</span></span>           |
|<span data-ttu-id="0547e-160">5</span><span class="sxs-lookup"><span data-stu-id="0547e-160">5</span></span>         | <span data-ttu-id="0547e-161">`-band`, `-bnot`</span><span class="sxs-lookup"><span data-stu-id="0547e-161">`-band`, `-bnot`</span></span> |<span data-ttu-id="0547e-162">Voor bitsgewijze bewerkingen</span><span class="sxs-lookup"><span data-stu-id="0547e-162">For bitwise operations</span></span>                 |
|<span data-ttu-id="0547e-163">5</span><span class="sxs-lookup"><span data-stu-id="0547e-163">5</span></span>         | <span data-ttu-id="0547e-164">`-bor`, `-bxor`</span><span class="sxs-lookup"><span data-stu-id="0547e-164">`-bor`, `-bxor`</span></span>  |<span data-ttu-id="0547e-165">Voor bitsgewijze bewerkingen</span><span class="sxs-lookup"><span data-stu-id="0547e-165">For bitwise operations</span></span>                 |
|<span data-ttu-id="0547e-166">5</span><span class="sxs-lookup"><span data-stu-id="0547e-166">5</span></span>         | <span data-ttu-id="0547e-167">`-shr`, `-shl`</span><span class="sxs-lookup"><span data-stu-id="0547e-167">`-shr`, `-shl`</span></span>   |<span data-ttu-id="0547e-168">Voor bitsgewijze bewerkingen</span><span class="sxs-lookup"><span data-stu-id="0547e-168">For bitwise operations</span></span>                 |

<span data-ttu-id="0547e-169">Power shell verwerkt de expressies van links naar rechts volgens de prioriteits regels.</span><span class="sxs-lookup"><span data-stu-id="0547e-169">PowerShell processes the expressions from left to right according to the precedence rules.</span></span> <span data-ttu-id="0547e-170">In de volgende voor beelden ziet u het effect van de prioriteits regels:</span><span class="sxs-lookup"><span data-stu-id="0547e-170">The following examples show the effect of the precedence rules:</span></span>

|<span data-ttu-id="0547e-171">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-171">Expression</span></span> |<span data-ttu-id="0547e-172">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-172">Result</span></span>|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

<span data-ttu-id="0547e-173">De volg orde waarin in Power shell expressies worden geëvalueerd, kunnen afwijken van andere programmeer-en script talen die u hebt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="0547e-173">The order in which PowerShell evaluates expressions might differ from other programming and scripting languages that you have used.</span></span> <span data-ttu-id="0547e-174">In het volgende voor beeld ziet u een gecompliceerde toewijzings instructie.</span><span class="sxs-lookup"><span data-stu-id="0547e-174">The following example shows a complicated assignment statement.</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

<span data-ttu-id="0547e-175">In dit voor beeld wordt de expressie `$a++` eerder geëvalueerd `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="0547e-175">In this example, the expression `$a++` is evaluated before `$b[$a]`.</span></span>
<span data-ttu-id="0547e-176">`$a++`Als u een evaluatie wijzigt, wordt de waarde van `$a` nadat deze is gebruikt in de instructie, `$c[$a++]` maar voordat deze wordt gebruikt in `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="0547e-176">Evaluating `$a++` changes the value of `$a` after it is used in the statement `$c[$a++]`; but, before it is used in `$b[$a]`.</span></span> <span data-ttu-id="0547e-177">De variabele `$a` `$b[$a]` is gelijk aan `1` , niet `0` ; daarom wijst de instructie een waarde toe aan `$b[1]` , niet `$b[0]` .</span><span class="sxs-lookup"><span data-stu-id="0547e-177">The variable `$a` in `$b[$a]` equals `1`, not `0`; so, the statement assigns a value to `$b[1]`, not `$b[0]`.</span></span>

<span data-ttu-id="0547e-178">De bovenstaande code is gelijk aan:</span><span class="sxs-lookup"><span data-stu-id="0547e-178">The above code is equivalent to:</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a><span data-ttu-id="0547e-179">DELEN EN AFRONDEN</span><span class="sxs-lookup"><span data-stu-id="0547e-179">DIVISION AND ROUNDING</span></span>

<span data-ttu-id="0547e-180">Wanneer het quotiënt van een delings bewerking een geheel getal is, wordt de waarde door Power shell afgerond op het dichtstbijzijnde gehele getal.</span><span class="sxs-lookup"><span data-stu-id="0547e-180">When the quotient of a division operation is an integer, PowerShell rounds the value to the nearest integer.</span></span> <span data-ttu-id="0547e-181">Wanneer de waarde is `.5` , wordt deze afgerond op het dichtstbijzijnde even gehele getal.</span><span class="sxs-lookup"><span data-stu-id="0547e-181">When the value is `.5`, it rounds to the nearest even integer.</span></span>

<span data-ttu-id="0547e-182">In het volgende voor beeld ziet u het effect van het afronden op het dichtstbijzijnde even gehele getal.</span><span class="sxs-lookup"><span data-stu-id="0547e-182">The following example shows the effect of rounding to the nearest even integer.</span></span>

|<span data-ttu-id="0547e-183">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-183">Expression</span></span>      |<span data-ttu-id="0547e-184">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-184">Result</span></span>|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

<span data-ttu-id="0547e-185">U ziet hoe **_5/2_ = 2,5** wordt afgerond op **2**.</span><span class="sxs-lookup"><span data-stu-id="0547e-185">Notice how **_5/2_ = 2.5** gets rounded to **2**.</span></span> <span data-ttu-id="0547e-186">Maar **_7/2_ = 3,5** wordt afgerond op **4**.</span><span class="sxs-lookup"><span data-stu-id="0547e-186">But, **_7/2_ = 3.5** gets rounded to **4**.</span></span>

<span data-ttu-id="0547e-187">U kunt de `[Math]` klasse gebruiken om verschillende Afrondings gedrag te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="0547e-187">You can use the `[Math]` class to get different rounding behavior.</span></span>

|                          <span data-ttu-id="0547e-188">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-188">Expression</span></span>                          | <span data-ttu-id="0547e-189">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-189">Result</span></span> |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

<span data-ttu-id="0547e-190">Zie de methode [Math. Round](/dotnet/api/system.math.round) (Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0547e-190">For more information, see the [Math.Round](/dotnet/api/system.math.round) method.</span></span>

## <a name="adding-and-multiplying-non-numeric-types"></a><span data-ttu-id="0547e-191">NIET-NUMERIEKE TYPEN TOEVOEGEN EN VERMENIGVULDIGEN</span><span class="sxs-lookup"><span data-stu-id="0547e-191">ADDING AND MULTIPLYING NON-NUMERIC TYPES</span></span>

<span data-ttu-id="0547e-192">U kunt cijfers, teken reeksen, matrices en hash-tabellen toevoegen.</span><span class="sxs-lookup"><span data-stu-id="0547e-192">You can add numbers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="0547e-193">En u kunt getallen, teken reeksen en matrices vermenigvuldigen.</span><span class="sxs-lookup"><span data-stu-id="0547e-193">And, you can multiply numbers, strings, and arrays.</span></span> <span data-ttu-id="0547e-194">U kunt hash-tabellen echter niet vermenigvuldigen.</span><span class="sxs-lookup"><span data-stu-id="0547e-194">However, you cannot multiply hash tables.</span></span>

<span data-ttu-id="0547e-195">Wanneer u teken reeksen, matrices of hash-tabellen toevoegt, worden de elementen samengevoegd.</span><span class="sxs-lookup"><span data-stu-id="0547e-195">When you add strings, arrays, or hash tables, the elements are concatenated.</span></span> <span data-ttu-id="0547e-196">Wanneer u verzamelingen samenvoegt, zoals matrices of hash-tabellen, wordt er een nieuw object gemaakt met daarin de objecten uit beide verzamelingen.</span><span class="sxs-lookup"><span data-stu-id="0547e-196">When you concatenate collections, such as arrays or hash tables, a new object is created that contains the objects from both collections.</span></span> <span data-ttu-id="0547e-197">Als u hash-tabellen met dezelfde sleutel probeert samen te voegen, mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="0547e-197">If you try to concatenate hash tables that have the same key, the operation fails.</span></span>

<span data-ttu-id="0547e-198">Met de volgende opdrachten worden bijvoorbeeld twee matrices gemaakt en vervolgens toegevoegd:</span><span class="sxs-lookup"><span data-stu-id="0547e-198">For example, the following commands create two arrays and then add them:</span></span>

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

<span data-ttu-id="0547e-199">U kunt ook reken kundige bewerkingen uitvoeren op objecten van verschillende typen.</span><span class="sxs-lookup"><span data-stu-id="0547e-199">You can also perform arithmetic operations on objects of different types.</span></span>
<span data-ttu-id="0547e-200">De bewerking die Power shell uitvoert, wordt bepaald door het Microsoft .NET Framework-type van het meest linkse object in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="0547e-200">The operation that PowerShell performs is determined by the Microsoft .NET Framework type of the leftmost object in the operation.</span></span> <span data-ttu-id="0547e-201">Power shell probeert alle objecten in de bewerking te converteren naar het .NET Framework type van het eerste object.</span><span class="sxs-lookup"><span data-stu-id="0547e-201">PowerShell tries to convert all the objects in the operation to the .NET Framework type of the first object.</span></span> <span data-ttu-id="0547e-202">Als de objecten zijn geconverteerd, wordt de bewerking uitgevoerd die geschikt is voor het .NET Framework type van het eerste object.</span><span class="sxs-lookup"><span data-stu-id="0547e-202">If it succeeds in converting the objects, it performs the operation appropriate to the .NET Framework type of the first object.</span></span> <span data-ttu-id="0547e-203">Als een van de objecten niet kan worden geconverteerd, mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="0547e-203">If it fails to convert any of the objects, the operation fails.</span></span>

<span data-ttu-id="0547e-204">In de volgende voor beelden wordt het gebruik van de Opera tors voor toevoegen en vermenigvuldigen gedemonstreerd. in bewerkingen die verschillende object typen bevatten.</span><span class="sxs-lookup"><span data-stu-id="0547e-204">The following examples demonstrate the use of the addition and multiplication operators; in operations that include different object types.</span></span> <span data-ttu-id="0547e-205">Aannemen `$array = 1,2,3` :</span><span class="sxs-lookup"><span data-stu-id="0547e-205">Assume `$array = 1,2,3`:</span></span>

|<span data-ttu-id="0547e-206">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-206">Expression</span></span>       |<span data-ttu-id="0547e-207">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-207">Result</span></span>                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |<span data-ttu-id="0547e-208">`1`,`2`,`3`,`16`</span><span class="sxs-lookup"><span data-stu-id="0547e-208">`1`,`2`,`3`,`16`</span></span>       |
|`$array + "file"`|<span data-ttu-id="0547e-209">`1`,`2`,`3`,`file`</span><span class="sxs-lookup"><span data-stu-id="0547e-209">`1`,`2`,`3`,`file`</span></span>     |
|`$array * 2`     |<span data-ttu-id="0547e-210">`1`,`2`,`3`,`1`,`2`,`3`</span><span class="sxs-lookup"><span data-stu-id="0547e-210">`1`,`2`,`3`,`1`,`2`,`3`</span></span>|
|`"file" * 3`     |`filefilefile`         |

<span data-ttu-id="0547e-211">Omdat de methode die wordt gebruikt om-instructies te evalueren, wordt bepaald door het meest linkse object, is toevoeging en vermenigvuldiging in Power shell niet strikt Commutative.</span><span class="sxs-lookup"><span data-stu-id="0547e-211">Because the method that is used to evaluate statements is determined by the leftmost object, addition and multiplication in PowerShell are not strictly commutative.</span></span> <span data-ttu-id="0547e-212">Is bijvoorbeeld `(a + b)` niet altijd gelijk aan `(b + a)` en is `(ab)` niet altijd gelijk aan `(ba)` .</span><span class="sxs-lookup"><span data-stu-id="0547e-212">For example, `(a + b)` does not always equal `(b + a)`, and `(ab)` does not always equal `(ba)`.</span></span>

<span data-ttu-id="0547e-213">In de volgende voor beelden ziet u dit principe:</span><span class="sxs-lookup"><span data-stu-id="0547e-213">The following examples demonstrate this principle:</span></span>

|<span data-ttu-id="0547e-214">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-214">Expression</span></span>   |<span data-ttu-id="0547e-215">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-215">Result</span></span>                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |<span data-ttu-id="0547e-216">+ 16 + "bestand" "</span><span class="sxs-lookup"><span data-stu-id="0547e-216">+ 16 + "file"\`</span></span>                                       |

<span data-ttu-id="0547e-217">Hash-tabellen zijn iets anders.</span><span class="sxs-lookup"><span data-stu-id="0547e-217">Hash tables are a slightly different case.</span></span> <span data-ttu-id="0547e-218">U kunt hash-tabellen toevoegen aan een andere hash-tabel, op voor waarde dat de toegevoegde hash-tabellen geen dubbele sleutels hebben.</span><span class="sxs-lookup"><span data-stu-id="0547e-218">You can add hash tables to another hash table, as long as, the added hash tables don't have duplicate keys.</span></span>

<span data-ttu-id="0547e-219">In het volgende voor beeld ziet u hoe u hash-tabellen aan elkaar kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="0547e-219">The following example show how to add hash tables to each other.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

<span data-ttu-id="0547e-220">In het volgende voor beeld wordt een fout gegenereerd omdat een van de sleutels in beide hash-tabellen is gedupliceerd.</span><span class="sxs-lookup"><span data-stu-id="0547e-220">The following example throws an error because one of the keys is duplicated in both hash tables.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

<span data-ttu-id="0547e-221">U kunt ook een hash-tabel aan een matrix toevoegen. en de gehele hash-tabel wordt een item in de matrix.</span><span class="sxs-lookup"><span data-stu-id="0547e-221">Also, you can add a hash table to an array; and, the entire hash table becomes an item in the array.</span></span>

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

<span data-ttu-id="0547e-222">U kunt echter geen ander type toevoegen aan een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="0547e-222">However, you cannot add any other type to a hash table.</span></span>

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

<span data-ttu-id="0547e-223">Hoewel de optellings operatoren erg nuttig zijn, gebruikt u de toewijzings operatoren om elementen toe te voegen aan hash-tabellen en-matrices.</span><span class="sxs-lookup"><span data-stu-id="0547e-223">Although the addition operators are very useful, use the assignment operators to add elements to hash tables and arrays.</span></span> <span data-ttu-id="0547e-224">Zie [about_assignment_operators](about_Assignment_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0547e-224">For more information see [about_assignment_operators](about_Assignment_Operators.md).</span></span> <span data-ttu-id="0547e-225">De volgende voor beelden gebruiken de `+=` toewijzings operator om items toe te voegen aan een matrix:</span><span class="sxs-lookup"><span data-stu-id="0547e-225">The following examples use the `+=` assignment operator to add items to an array:</span></span>

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a><span data-ttu-id="0547e-226">TYPE CONVERSIE OM RESULTAAT TE BIEDEN</span><span class="sxs-lookup"><span data-stu-id="0547e-226">TYPE CONVERSION TO ACCOMMODATE RESULT</span></span>

<span data-ttu-id="0547e-227">Power shell selecteert automatisch het .NET Framework numerieke type dat het resultaat het beste oplevert zonder dat de precisie verloren gaat.</span><span class="sxs-lookup"><span data-stu-id="0547e-227">PowerShell automatically selects the .NET Framework numeric type that best expresses the result without losing precision.</span></span> <span data-ttu-id="0547e-228">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0547e-228">For example:</span></span>

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

<span data-ttu-id="0547e-229">Als het resultaat van een bewerking te groot is voor het type, wordt het type van het resultaat uitgebreid met het resultaat, zoals in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="0547e-229">If the result of an operation is too large for the type, the type of the result is widened to accommodate the result, as in the following example:</span></span>

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

<span data-ttu-id="0547e-230">Het type van het resultaat is niet noodzakelijkerwijs hetzelfde als een van de operanden.</span><span class="sxs-lookup"><span data-stu-id="0547e-230">The type of the result will not necessarily be the same as one of the operands.</span></span> <span data-ttu-id="0547e-231">In het volgende voor beeld kan de negatieve waarde niet worden geconverteerd naar een niet-ondertekend geheel getal en is het niet-ondertekende gehele getal te groot om te worden geconverteerd naar `Int32` :</span><span class="sxs-lookup"><span data-stu-id="0547e-231">In the following example, the negative value cannot be cast to an unsigned integer, and the unsigned integer is too large to be cast to `Int32`:</span></span>

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

<span data-ttu-id="0547e-232">In dit voor beeld `Int64` kan dit elk type bevatten.</span><span class="sxs-lookup"><span data-stu-id="0547e-232">In this example, `Int64` can accommodate both types.</span></span>

<span data-ttu-id="0547e-233">Het `System.Decimal` type is een uitzonde ring.</span><span class="sxs-lookup"><span data-stu-id="0547e-233">The `System.Decimal` type is an exception.</span></span> <span data-ttu-id="0547e-234">Als een van beide operanden het decimale type heeft, is het resultaat van het decimale type.</span><span class="sxs-lookup"><span data-stu-id="0547e-234">If either operand has the Decimal type, the result will be of the Decimal type.</span></span> <span data-ttu-id="0547e-235">Als het resultaat te groot is voor het decimale type, wordt dit niet geconverteerd naar double.</span><span class="sxs-lookup"><span data-stu-id="0547e-235">If the result is too large for the Decimal type, it will not be cast to Double.</span></span> <span data-ttu-id="0547e-236">In plaats daarvan treedt er een fout op.</span><span class="sxs-lookup"><span data-stu-id="0547e-236">Instead, an error results.</span></span>

|<span data-ttu-id="0547e-237">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-237">Expression</span></span>               |<span data-ttu-id="0547e-238">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-238">Result</span></span>                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a><span data-ttu-id="0547e-239">WISKUNDIGE OPERA TORS EN VARIABELEN</span><span class="sxs-lookup"><span data-stu-id="0547e-239">ARITHMETIC OPERATORS AND VARIABLES</span></span>

<span data-ttu-id="0547e-240">U kunt ook reken kundige Opera tors met variabelen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0547e-240">You can also use arithmetic operators with variables.</span></span> <span data-ttu-id="0547e-241">De Opera tors handelen op de waarden van de variabelen.</span><span class="sxs-lookup"><span data-stu-id="0547e-241">The operators act on the values of the variables.</span></span> <span data-ttu-id="0547e-242">In de volgende voor beelden wordt het gebruik van reken kundige Opera tors met variabelen gedemonstreerd:</span><span class="sxs-lookup"><span data-stu-id="0547e-242">The following examples demonstrate the use of arithmetic operators with variables:</span></span>

| <span data-ttu-id="0547e-243">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-243">Expression</span></span>                                    |<span data-ttu-id="0547e-244">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-244">Result</span></span>      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a><span data-ttu-id="0547e-245">WISKUNDIGE OPERA TORS EN OPDRACHTEN</span><span class="sxs-lookup"><span data-stu-id="0547e-245">ARITHMETIC OPERATORS AND COMMANDS</span></span>

<span data-ttu-id="0547e-246">Normaal gesp roken gebruikt u de reken kundige Opera tors in expressies met getallen, teken reeksen en matrices.</span><span class="sxs-lookup"><span data-stu-id="0547e-246">Typically, you use the arithmetic operators in expressions with numbers, strings, and arrays.</span></span> <span data-ttu-id="0547e-247">U kunt echter ook reken kundige Opera tors gebruiken met de objecten die door opdrachten worden geretourneerd en met de eigenschappen van deze objecten.</span><span class="sxs-lookup"><span data-stu-id="0547e-247">However, you can also use arithmetic operators with the objects that commands return and with the properties of those objects.</span></span>

<span data-ttu-id="0547e-248">In de volgende voor beelden ziet u hoe u wiskundige Opera tors gebruikt in expressies met Power shell-opdrachten:</span><span class="sxs-lookup"><span data-stu-id="0547e-248">The following examples show how to use the arithmetic operators in expressions with PowerShell commands:</span></span>

```powershell
(get-date) + (new-timespan -day 1)
```

<span data-ttu-id="0547e-249">De operator voor haakjes afdwingt de evaluatie van de `get-date` cmdlet en de evaluatie van de `new-timespan -day 1` cmdlet-expressie, in die volg orde.</span><span class="sxs-lookup"><span data-stu-id="0547e-249">The parenthesis operator forces the evaluation of the `get-date` cmdlet and the evaluation of the `new-timespan -day 1` cmdlet expression, in that order.</span></span> <span data-ttu-id="0547e-250">Beide resultaten worden vervolgens toegevoegd met behulp van de `+` operator.</span><span class="sxs-lookup"><span data-stu-id="0547e-250">Both results are then added using the `+` operator.</span></span>

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

<span data-ttu-id="0547e-251">In de bovenstaande expressie wordt elk proces werk ruimte ( `$_.ws` ) vermenigvuldigd met `2` ; en wordt het resultaat vergeleken met `50mb` om te zien of het groter is dan dat.</span><span class="sxs-lookup"><span data-stu-id="0547e-251">In the above expression, each process working space (`$_.ws`) is multiplied by `2`; and, the result, compared against `50mb` to see if it is greater than that.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="0547e-252">Bitsgewijze Opera tors</span><span class="sxs-lookup"><span data-stu-id="0547e-252">Bitwise Operators</span></span>

<span data-ttu-id="0547e-253">Power shell ondersteunt de standaard bitsgewijze Opera Tors, waaronder bitsgewijze-en ( `-bAnd` ), de inclusieve en exclusieve BITSGEWIJZE or-Opera tors ( `-bOr` en `-bXor` ) en bitsgewijze-not ( `-bNot` ).</span><span class="sxs-lookup"><span data-stu-id="0547e-253">PowerShell supports the standard bitwise operators, including bitwise-AND (`-bAnd`), the inclusive and exclusive bitwise-OR operators (`-bOr` and `-bXor`), and bitwise-NOT (`-bNot`).</span></span>

<span data-ttu-id="0547e-254">Vanaf Power Shell 2,0 werken alle bitsgewijze Opera tors met 64-bits geheel getal.</span><span class="sxs-lookup"><span data-stu-id="0547e-254">Beginning in PowerShell 2.0, all bitwise operators work with 64-bit integers.</span></span>

<span data-ttu-id="0547e-255">Vanaf Power Shell 3,0 worden de `-shr` (Shift-rechts) en `-shl` (Shift-links) geïntroduceerd voor de ondersteuning van bitsgewijze berekeningen in Power shell.</span><span class="sxs-lookup"><span data-stu-id="0547e-255">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are introduced to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="0547e-256">Power shell ondersteunt de volgende bitsgewijze Opera tors.</span><span class="sxs-lookup"><span data-stu-id="0547e-256">PowerShell supports the following bitwise operators.</span></span>

| <span data-ttu-id="0547e-257">Operator</span><span class="sxs-lookup"><span data-stu-id="0547e-257">Operator</span></span> | <span data-ttu-id="0547e-258">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0547e-258">Description</span></span>            | <span data-ttu-id="0547e-259">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-259">Expression</span></span>   | <span data-ttu-id="0547e-260">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-260">Result</span></span> |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | <span data-ttu-id="0547e-261">Bitsgewijze AND</span><span class="sxs-lookup"><span data-stu-id="0547e-261">Bitwise AND</span></span>            | `10 -band 3` | <span data-ttu-id="0547e-262">2</span><span class="sxs-lookup"><span data-stu-id="0547e-262">2</span></span>      |
| `-bor`   | <span data-ttu-id="0547e-263">Bitsgewijze OR (inclusief)</span><span class="sxs-lookup"><span data-stu-id="0547e-263">Bitwise OR (inclusive)</span></span> | `10 -bor 3`  | <span data-ttu-id="0547e-264">11</span><span class="sxs-lookup"><span data-stu-id="0547e-264">11</span></span>     |
| `-bxor`  | <span data-ttu-id="0547e-265">Bitsgewijze OR (exclusief)</span><span class="sxs-lookup"><span data-stu-id="0547e-265">Bitwise OR (exclusive)</span></span> | `10 -bxor 3` | <span data-ttu-id="0547e-266">9</span><span class="sxs-lookup"><span data-stu-id="0547e-266">9</span></span>      |
| `-bnot`  | <span data-ttu-id="0547e-267">Bitsgewijze NOT</span><span class="sxs-lookup"><span data-stu-id="0547e-267">Bitwise NOT</span></span>            | `-bNot 10`   | <span data-ttu-id="0547e-268">-11</span><span class="sxs-lookup"><span data-stu-id="0547e-268">-11</span></span>    |
| `-shl`   | <span data-ttu-id="0547e-269">Shift-links</span><span class="sxs-lookup"><span data-stu-id="0547e-269">Shift-left</span></span>             | `102 -shl 2` | <span data-ttu-id="0547e-270">408</span><span class="sxs-lookup"><span data-stu-id="0547e-270">408</span></span>    |
| `-shr`   | <span data-ttu-id="0547e-271">Shift-rechts</span><span class="sxs-lookup"><span data-stu-id="0547e-271">Shift-right</span></span>            | `102 -shr 1` | <span data-ttu-id="0547e-272">51</span><span class="sxs-lookup"><span data-stu-id="0547e-272">51</span></span>     |

<span data-ttu-id="0547e-273">Bitsgewijze Opera tors handelen op de binaire indeling van een waarde.</span><span class="sxs-lookup"><span data-stu-id="0547e-273">Bitwise operators act on the binary format of a value.</span></span> <span data-ttu-id="0547e-274">De bits-structuur voor het nummer 10 is bijvoorbeeld 00001010 (op basis van 1 byte) en de bit-structuur voor het nummer 3 is 00000011.</span><span class="sxs-lookup"><span data-stu-id="0547e-274">For example, the bit structure for the number 10 is 00001010 (based on 1 byte), and the bit structure for the number 3 is 00000011.</span></span> <span data-ttu-id="0547e-275">Wanneer u een bitsgewijze operator gebruikt om 10 tot 3 te vergelijken, worden de afzonderlijke bits in elke byte vergeleken.</span><span class="sxs-lookup"><span data-stu-id="0547e-275">When you use a bitwise operator to compare 10 to 3, the individual bits in each byte are compared.</span></span>

<span data-ttu-id="0547e-276">In een bitsgewijze AND-bewerking wordt de resulterende bit ingesteld op 1 alleen wanneer beide invoer bits 1 zijn.</span><span class="sxs-lookup"><span data-stu-id="0547e-276">In a bitwise AND operation, the resulting bit is set to 1 only when both input bits are 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

<span data-ttu-id="0547e-277">In een bitsgewijze of (inclusief) bewerking wordt de resulterende bit ingesteld op 1 wanneer een van beide of beide invoer bits 1 zijn.</span><span class="sxs-lookup"><span data-stu-id="0547e-277">In a bitwise OR (inclusive) operation, the resulting bit is set to 1 when either or both input bits are 1.</span></span> <span data-ttu-id="0547e-278">De resulterende bit wordt alleen ingesteld op 0 als beide invoer bits zijn ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="0547e-278">The resulting bit is set to 0 only when both input bits are set to 0.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

<span data-ttu-id="0547e-279">In een bitsgewijze of (exclusieve) bewerking wordt de resulterende bit ingesteld op 1 alleen als één invoer bit 1 is.</span><span class="sxs-lookup"><span data-stu-id="0547e-279">In a bitwise OR (exclusive) operation, the resulting bit is set to 1 only when one input bit is 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

<span data-ttu-id="0547e-280">De operator Bitsgewijze NOT is een unaire operator die de binaire complement waarde produceert.</span><span class="sxs-lookup"><span data-stu-id="0547e-280">The bitwise NOT operator is a unary operator that produces the binary complement of the value.</span></span> <span data-ttu-id="0547e-281">Een bit van 1 is ingesteld op 0 en een bit van 0 is ingesteld op 1.</span><span class="sxs-lookup"><span data-stu-id="0547e-281">A bit of 1 is set to 0 and a bit of 0 is set to 1.</span></span>

<span data-ttu-id="0547e-282">Bijvoorbeeld, de binaire complement van 0 is-1, het Maxi maal niet-ondertekende gehele getal (0xFFFFFFFF) en het binaire complement van-1 is 0.</span><span class="sxs-lookup"><span data-stu-id="0547e-282">For example, the binary complement of 0 is -1, the maximum unsigned integer (0xffffffff), and the binary complement of -1 is 0.</span></span>

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

<span data-ttu-id="0547e-283">In een bitsgewijze bewerking met een bitsgewijs verplaatsen, worden alle bits ' n ' naar links verplaatst, waarbij ' n ' de waarde van de rechter operand is.</span><span class="sxs-lookup"><span data-stu-id="0547e-283">In a bitwise shift-left operation, all bits are moved "n" places to the left, where "n" is the value of the right operand.</span></span> <span data-ttu-id="0547e-284">Er wordt een nul ingevoegd op de locatie.</span><span class="sxs-lookup"><span data-stu-id="0547e-284">A zero is inserted in the ones place.</span></span>

<span data-ttu-id="0547e-285">Wanneer de linkeroperand een geheel getal (32-bits) is, bepaalt de onderste 5 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.</span><span class="sxs-lookup"><span data-stu-id="0547e-285">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="0547e-286">Wanneer de linkeroperand een lange (64-bits) waarde heeft, bepaalt de onderste 6 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.</span><span class="sxs-lookup"><span data-stu-id="0547e-286">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="0547e-287">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-287">Expression</span></span> |<span data-ttu-id="0547e-288">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-288">Result</span></span>|<span data-ttu-id="0547e-289">Binair resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-289">Binary Result</span></span>|
|-----------|------|-------------|
|`21 -shl 0`|<span data-ttu-id="0547e-290">21</span><span class="sxs-lookup"><span data-stu-id="0547e-290">21</span></span>    |<span data-ttu-id="0547e-291">0001 0101</span><span class="sxs-lookup"><span data-stu-id="0547e-291">0001 0101</span></span>    |
|`21 -shl 1`|<span data-ttu-id="0547e-292">42</span><span class="sxs-lookup"><span data-stu-id="0547e-292">42</span></span>    |<span data-ttu-id="0547e-293">0010 1010</span><span class="sxs-lookup"><span data-stu-id="0547e-293">0010 1010</span></span>    |
|`21 -shl 2`|<span data-ttu-id="0547e-294">84</span><span class="sxs-lookup"><span data-stu-id="0547e-294">84</span></span>    |<span data-ttu-id="0547e-295">0101 0100</span><span class="sxs-lookup"><span data-stu-id="0547e-295">0101 0100</span></span>    |

<span data-ttu-id="0547e-296">In een bitsgewijs-rechts bewerking worden alle bits ' n ' naar rechts verplaatst, waarbij ' n ' wordt opgegeven door de rechter operand.</span><span class="sxs-lookup"><span data-stu-id="0547e-296">In a bitwise shift-right operation, all bits are moved "n" places to the right, where "n" is specified by the right operand.</span></span> <span data-ttu-id="0547e-297">Met de operator Shift-Right (-SHR) wordt een nul ingevoegd op de meest linkse positie wanneer een positieve of niet-ondertekende waarde naar rechts wordt geschoven.</span><span class="sxs-lookup"><span data-stu-id="0547e-297">The shift-right operator (-shr) inserts a zero in the left-most place when shifting a positive or unsigned value to the right.</span></span>

<span data-ttu-id="0547e-298">Wanneer de linkeroperand een geheel getal (32-bits) is, bepaalt de onderste 5 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.</span><span class="sxs-lookup"><span data-stu-id="0547e-298">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="0547e-299">Wanneer de linkeroperand een lange (64-bits) waarde heeft, bepaalt de onderste 6 bits van de rechter operand hoe veel bits van de linkeroperand worden verschoven.</span><span class="sxs-lookup"><span data-stu-id="0547e-299">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="0547e-300">Expression</span><span class="sxs-lookup"><span data-stu-id="0547e-300">Expression</span></span>              |<span data-ttu-id="0547e-301">Resultaat</span><span class="sxs-lookup"><span data-stu-id="0547e-301">Result</span></span>      |<span data-ttu-id="0547e-302">Binair</span><span class="sxs-lookup"><span data-stu-id="0547e-302">Binary</span></span>     |<span data-ttu-id="0547e-303">Bovenaanzicht</span><span class="sxs-lookup"><span data-stu-id="0547e-303">Hex</span></span>         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | <span data-ttu-id="0547e-304">21</span><span class="sxs-lookup"><span data-stu-id="0547e-304">21</span></span>         | <span data-ttu-id="0547e-305">0001 0101</span><span class="sxs-lookup"><span data-stu-id="0547e-305">0001 0101</span></span> | <span data-ttu-id="0547e-306">0x15</span><span class="sxs-lookup"><span data-stu-id="0547e-306">0x15</span></span>       |
|`21 -shr 1`             | <span data-ttu-id="0547e-307">10</span><span class="sxs-lookup"><span data-stu-id="0547e-307">10</span></span>         | <span data-ttu-id="0547e-308">0000 1010</span><span class="sxs-lookup"><span data-stu-id="0547e-308">0000 1010</span></span> | <span data-ttu-id="0547e-309">0x0A</span><span class="sxs-lookup"><span data-stu-id="0547e-309">0x0A</span></span>       |
|`21 -shr 2`             | <span data-ttu-id="0547e-310">5</span><span class="sxs-lookup"><span data-stu-id="0547e-310">5</span></span>          | <span data-ttu-id="0547e-311">0000 0101</span><span class="sxs-lookup"><span data-stu-id="0547e-311">0000 0101</span></span> | <span data-ttu-id="0547e-312">0x05</span><span class="sxs-lookup"><span data-stu-id="0547e-312">0x05</span></span>       |
|`21 -shr 31`            | <span data-ttu-id="0547e-313">0</span><span class="sxs-lookup"><span data-stu-id="0547e-313">0</span></span>          | <span data-ttu-id="0547e-314">0000 0000</span><span class="sxs-lookup"><span data-stu-id="0547e-314">0000 0000</span></span> | <span data-ttu-id="0547e-315">0x00</span><span class="sxs-lookup"><span data-stu-id="0547e-315">0x00</span></span>       |
|`21 -shr 32`            | <span data-ttu-id="0547e-316">21</span><span class="sxs-lookup"><span data-stu-id="0547e-316">21</span></span>         | <span data-ttu-id="0547e-317">0001 0101</span><span class="sxs-lookup"><span data-stu-id="0547e-317">0001 0101</span></span> | <span data-ttu-id="0547e-318">0x15</span><span class="sxs-lookup"><span data-stu-id="0547e-318">0x15</span></span>       |
|`21 -shr 64`            | <span data-ttu-id="0547e-319">21</span><span class="sxs-lookup"><span data-stu-id="0547e-319">21</span></span>         | <span data-ttu-id="0547e-320">0001 0101</span><span class="sxs-lookup"><span data-stu-id="0547e-320">0001 0101</span></span> | <span data-ttu-id="0547e-321">0x15</span><span class="sxs-lookup"><span data-stu-id="0547e-321">0x15</span></span>       |
|`21 -shr 65`            | <span data-ttu-id="0547e-322">10</span><span class="sxs-lookup"><span data-stu-id="0547e-322">10</span></span>         | <span data-ttu-id="0547e-323">0000 1010</span><span class="sxs-lookup"><span data-stu-id="0547e-323">0000 1010</span></span> | <span data-ttu-id="0547e-324">0x0A</span><span class="sxs-lookup"><span data-stu-id="0547e-324">0x0A</span></span>       |
|`21 -shr 66`            | <span data-ttu-id="0547e-325">5</span><span class="sxs-lookup"><span data-stu-id="0547e-325">5</span></span>          | <span data-ttu-id="0547e-326">0000 0101</span><span class="sxs-lookup"><span data-stu-id="0547e-326">0000 0101</span></span> | <span data-ttu-id="0547e-327">0x05</span><span class="sxs-lookup"><span data-stu-id="0547e-327">0x05</span></span>       |
|`[int]::MaxValue -shr 1`| <span data-ttu-id="0547e-328">1073741823</span><span class="sxs-lookup"><span data-stu-id="0547e-328">1073741823</span></span> |           | <span data-ttu-id="0547e-329">0x3FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="0547e-329">0x3FFFFFFF</span></span> |
|`[int]::MinValue -shr 1`| <span data-ttu-id="0547e-330">-1073741824</span><span class="sxs-lookup"><span data-stu-id="0547e-330">-1073741824</span></span>|           | <span data-ttu-id="0547e-331">0xC0000000</span><span class="sxs-lookup"><span data-stu-id="0547e-331">0xC0000000</span></span> |
|`-1 -shr 1`             | <span data-ttu-id="0547e-332">-1</span><span class="sxs-lookup"><span data-stu-id="0547e-332">-1</span></span>         |           | <span data-ttu-id="0547e-333">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="0547e-333">0xFFFFFFFF</span></span> |

## <a name="see-also"></a><span data-ttu-id="0547e-334">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="0547e-334">SEE ALSO</span></span>

- [<span data-ttu-id="0547e-335">about_arrays</span><span class="sxs-lookup"><span data-stu-id="0547e-335">about_arrays</span></span>](about_Arrays.md)
- [<span data-ttu-id="0547e-336">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="0547e-336">about_assignment_operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="0547e-337">about_comparison_operators</span><span class="sxs-lookup"><span data-stu-id="0547e-337">about_comparison_operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="0547e-338">about_hash_tables</span><span class="sxs-lookup"><span data-stu-id="0547e-338">about_hash_tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="0547e-339">about_operators</span><span class="sxs-lookup"><span data-stu-id="0547e-339">about_operators</span></span>](about_Operators.md)
- [<span data-ttu-id="0547e-340">about_variables</span><span class="sxs-lookup"><span data-stu-id="0547e-340">about_variables</span></span>](about_Variables.md)
- [<span data-ttu-id="0547e-341">Ophalen datum</span><span class="sxs-lookup"><span data-stu-id="0547e-341">Get-Date</span></span>](xref:Microsoft.PowerShell.Utility.Get-Date)
- [<span data-ttu-id="0547e-342">Nieuw-time span</span><span class="sxs-lookup"><span data-stu-id="0547e-342">New-TimeSpan</span></span>](xref:Microsoft.PowerShell.Utility.New-TimeSpan)