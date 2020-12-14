---
description: Hierin worden de Opera tors beschreven waarmee instructies in Power shell worden verbonden.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 8602551f3ecf74027b59715e1f47aab1b10bea92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705357"
---
# <a name="about_logical_operators"></a><span data-ttu-id="f1248-103">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="f1248-103">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="f1248-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f1248-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f1248-105">Hierin worden de Opera tors beschreven waarmee instructies in Power shell worden verbonden.</span><span class="sxs-lookup"><span data-stu-id="f1248-105">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f1248-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f1248-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="f1248-107">De logische Power shell-Opera tors verbinden expressies en instructies, zodat u één expressie kunt gebruiken om te testen op meerdere voor waarden.</span><span class="sxs-lookup"><span data-stu-id="f1248-107">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="f1248-108">De volgende instructie gebruikt bijvoorbeeld de operator and en de operator OR om drie voorwaardelijke instructies te verbinden.</span><span class="sxs-lookup"><span data-stu-id="f1248-108">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="f1248-109">De instructie is alleen waar als de waarde van $a groter is dan de waarde van $b en $a of $b kleiner is dan</span><span class="sxs-lookup"><span data-stu-id="f1248-109">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="f1248-110">Power shell ondersteunt de volgende logische Opera tors.</span><span class="sxs-lookup"><span data-stu-id="f1248-110">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="f1248-111">Operator</span><span class="sxs-lookup"><span data-stu-id="f1248-111">Operator</span></span>|<span data-ttu-id="f1248-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f1248-112">Description</span></span>                        |<span data-ttu-id="f1248-113">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f1248-113">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="f1248-114">Logische en.</span><span class="sxs-lookup"><span data-stu-id="f1248-114">Logical AND.</span></span> <span data-ttu-id="f1248-115">WAAR wanneer beide</span><span class="sxs-lookup"><span data-stu-id="f1248-115">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="f1248-116">-instructies zijn waar.</span><span class="sxs-lookup"><span data-stu-id="f1248-116">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="f1248-117">Logische of.</span><span class="sxs-lookup"><span data-stu-id="f1248-117">Logical OR.</span></span> <span data-ttu-id="f1248-118">WAAR wanneer</span><span class="sxs-lookup"><span data-stu-id="f1248-118">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="f1248-119">de instructie is waar.</span><span class="sxs-lookup"><span data-stu-id="f1248-119">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="f1248-120">Logische exclusieve of.</span><span class="sxs-lookup"><span data-stu-id="f1248-120">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="f1248-121">WAAR wanneer</span><span class="sxs-lookup"><span data-stu-id="f1248-121">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="f1248-122">Er is slechts één instructie waar</span><span class="sxs-lookup"><span data-stu-id="f1248-122">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="f1248-123">Logische not.</span><span class="sxs-lookup"><span data-stu-id="f1248-123">Logical not.</span></span> <span data-ttu-id="f1248-124">De instructie wordt genegeerd</span><span class="sxs-lookup"><span data-stu-id="f1248-124">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="f1248-125">dat volgt.</span><span class="sxs-lookup"><span data-stu-id="f1248-125">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="f1248-126">Hetzelfde als `-not`</span><span class="sxs-lookup"><span data-stu-id="f1248-126">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="f1248-127">Opmerking:</span><span class="sxs-lookup"><span data-stu-id="f1248-127">Note:</span></span>

<span data-ttu-id="f1248-128">In de vorige voor beelden wordt ook gebruikgemaakt van de operator gelijk aan vergelijkend `-eq` .</span><span class="sxs-lookup"><span data-stu-id="f1248-128">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="f1248-129">Zie [about_Comparison_Operators](about_Comparison_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f1248-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="f1248-130">In de voor beelden wordt ook gebruikgemaakt van de Booleaanse waarden van gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="f1248-130">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="f1248-131">Het gehele getal 0 heeft de waarde FALSE.</span><span class="sxs-lookup"><span data-stu-id="f1248-131">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="f1248-132">Alle andere gehele getallen hebben de waarde TRUE.</span><span class="sxs-lookup"><span data-stu-id="f1248-132">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="f1248-133">De syntaxis van de logische Opera Tors is als volgt:</span><span class="sxs-lookup"><span data-stu-id="f1248-133">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="f1248-134">Instructies die gebruikmaken van logische Opera Tors, retour neren Boole-waarden (waar of onwaar).</span><span class="sxs-lookup"><span data-stu-id="f1248-134">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="f1248-135">De logische Power shell-Opera tors evalueren alleen de instructies die nodig zijn om de waarheids waarde van de instructie te bepalen.</span><span class="sxs-lookup"><span data-stu-id="f1248-135">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="f1248-136">Als de linkeroperand in een instructie die de operator and bevat is ingesteld op FALSE, wordt de rechter operand niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="f1248-136">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="f1248-137">Als de linkeroperand in een instructie met de or-instructie is ingesteld op TRUE, wordt de rechter operand niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="f1248-137">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="f1248-138">Als gevolg hiervan kunt u deze instructies op dezelfde manier gebruiken als de `If` instructie.</span><span class="sxs-lookup"><span data-stu-id="f1248-138">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1248-139">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="f1248-139">SEE ALSO</span></span>

[<span data-ttu-id="f1248-140">about_Operators</span><span class="sxs-lookup"><span data-stu-id="f1248-140">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="f1248-141">Compare-object</span><span class="sxs-lookup"><span data-stu-id="f1248-141">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="f1248-142">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="f1248-142">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="f1248-143">about_If</span><span class="sxs-lookup"><span data-stu-id="f1248-143">about_If</span></span>](about_If.md)

