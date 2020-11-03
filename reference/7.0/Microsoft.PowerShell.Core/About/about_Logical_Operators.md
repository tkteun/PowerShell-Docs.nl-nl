---
description: Hierin worden de Opera tors beschreven waarmee instructies in Power shell worden verbonden.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 1262ed0f5797d8dcb8cb4719cad69ac6b6a28d59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252476"
---
# <a name="about_logical_operators"></a><span data-ttu-id="6d2b0-104">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="6d2b0-104">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="6d2b0-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6d2b0-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="6d2b0-106">Hierin worden de Opera tors beschreven waarmee instructies in Power shell worden verbonden.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-106">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="6d2b0-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6d2b0-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6d2b0-108">De logische Power shell-Opera tors verbinden expressies en instructies, zodat u één expressie kunt gebruiken om te testen op meerdere voor waarden.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-108">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="6d2b0-109">De volgende instructie gebruikt bijvoorbeeld de operator and en de operator OR om drie voorwaardelijke instructies te verbinden.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-109">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="6d2b0-110">De instructie is alleen waar als de waarde van $a groter is dan de waarde van $b en $a of $b kleiner is dan</span><span class="sxs-lookup"><span data-stu-id="6d2b0-110">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="6d2b0-111">Power shell ondersteunt de volgende logische Opera tors.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-111">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="6d2b0-112">Operator</span><span class="sxs-lookup"><span data-stu-id="6d2b0-112">Operator</span></span>|<span data-ttu-id="6d2b0-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6d2b0-113">Description</span></span>                        |<span data-ttu-id="6d2b0-114">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="6d2b0-114">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="6d2b0-115">Logische en.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-115">Logical AND.</span></span> <span data-ttu-id="6d2b0-116">WAAR wanneer beide</span><span class="sxs-lookup"><span data-stu-id="6d2b0-116">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="6d2b0-117">-instructies zijn waar.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-117">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="6d2b0-118">Logische of.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-118">Logical OR.</span></span> <span data-ttu-id="6d2b0-119">WAAR wanneer</span><span class="sxs-lookup"><span data-stu-id="6d2b0-119">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="6d2b0-120">de instructie is waar.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-120">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="6d2b0-121">Logische exclusieve of.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-121">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="6d2b0-122">WAAR wanneer</span><span class="sxs-lookup"><span data-stu-id="6d2b0-122">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="6d2b0-123">Er is slechts één instructie waar</span><span class="sxs-lookup"><span data-stu-id="6d2b0-123">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="6d2b0-124">Logische not.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-124">Logical not.</span></span> <span data-ttu-id="6d2b0-125">De instructie wordt genegeerd</span><span class="sxs-lookup"><span data-stu-id="6d2b0-125">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="6d2b0-126">dat volgt.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-126">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="6d2b0-127">Hetzelfde als `-not`</span><span class="sxs-lookup"><span data-stu-id="6d2b0-127">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="6d2b0-128">Opmerking:</span><span class="sxs-lookup"><span data-stu-id="6d2b0-128">Note:</span></span>

<span data-ttu-id="6d2b0-129">In de vorige voor beelden wordt ook gebruikgemaakt van de operator gelijk aan vergelijkend `-eq` .</span><span class="sxs-lookup"><span data-stu-id="6d2b0-129">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="6d2b0-130">Zie [about_Comparison_Operators](about_Comparison_Operators.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-130">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="6d2b0-131">In de voor beelden wordt ook gebruikgemaakt van de Booleaanse waarden van gehele getallen.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-131">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="6d2b0-132">Het gehele getal 0 heeft de waarde FALSE.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-132">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="6d2b0-133">Alle andere gehele getallen hebben de waarde TRUE.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-133">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="6d2b0-134">De syntaxis van de logische Opera Tors is als volgt:</span><span class="sxs-lookup"><span data-stu-id="6d2b0-134">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="6d2b0-135">Instructies die gebruikmaken van logische Opera Tors, retour neren Boole-waarden (waar of onwaar).</span><span class="sxs-lookup"><span data-stu-id="6d2b0-135">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="6d2b0-136">De logische Power shell-Opera tors evalueren alleen de instructies die nodig zijn om de waarheids waarde van de instructie te bepalen.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-136">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="6d2b0-137">Als de linkeroperand in een instructie die de operator and bevat is ingesteld op FALSE, wordt de rechter operand niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-137">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="6d2b0-138">Als de linkeroperand in een instructie met de or-instructie is ingesteld op TRUE, wordt de rechter operand niet geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-138">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="6d2b0-139">Als gevolg hiervan kunt u deze instructies op dezelfde manier gebruiken als de `If` instructie.</span><span class="sxs-lookup"><span data-stu-id="6d2b0-139">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d2b0-140">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="6d2b0-140">SEE ALSO</span></span>

[<span data-ttu-id="6d2b0-141">about_Operators</span><span class="sxs-lookup"><span data-stu-id="6d2b0-141">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="6d2b0-142">Compare-object</span><span class="sxs-lookup"><span data-stu-id="6d2b0-142">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="6d2b0-143">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="6d2b0-143">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="6d2b0-144">about_If</span><span class="sxs-lookup"><span data-stu-id="6d2b0-144">about_If</span></span>](about_If.md)
