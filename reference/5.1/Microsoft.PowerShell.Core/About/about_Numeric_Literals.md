---
description: Zowel integere als reële numerieke letterlijke waarden kunnen type-en vermenigvuldiger-achtervoegsels hebben.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Numerieke letterlijke waarden
ms.openlocfilehash: 99fa8c1a751551d028fe6df0b0cec94e07f19c59
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253169"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="52ab9-103">Numerieke letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="52ab9-103">About numeric literals</span></span>

<span data-ttu-id="52ab9-104">Er zijn twee soorten numerieke letterlijke waarden: geheel getal en werkelijk.</span><span class="sxs-lookup"><span data-stu-id="52ab9-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="52ab9-105">Beide kunnen type-en multiplier-achtervoegsels hebben.</span><span class="sxs-lookup"><span data-stu-id="52ab9-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="52ab9-106">Letterlijke tekens voor geheel getal</span><span class="sxs-lookup"><span data-stu-id="52ab9-106">Integer literals</span></span>

<span data-ttu-id="52ab9-107">Letterlijke tekens kunnen worden geschreven in decimale of hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="52ab9-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="52ab9-108">Hexadecimale letterlijke waarden worden voorafgegaan door met `0x` om ze te onderscheiden van decimale getallen.</span><span class="sxs-lookup"><span data-stu-id="52ab9-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="52ab9-109">Letterlijke tekens van een geheel getal kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.</span><span class="sxs-lookup"><span data-stu-id="52ab9-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="52ab9-110">Achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="52ab9-110">Suffix</span></span> |       <span data-ttu-id="52ab9-111">Betekenis</span><span class="sxs-lookup"><span data-stu-id="52ab9-111">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="52ab9-112">l</span><span class="sxs-lookup"><span data-stu-id="52ab9-112">l</span></span>      | <span data-ttu-id="52ab9-113">Long-gegevens type</span><span class="sxs-lookup"><span data-stu-id="52ab9-113">long data type</span></span>      |
| <span data-ttu-id="52ab9-114">KB823980</span><span class="sxs-lookup"><span data-stu-id="52ab9-114">kb</span></span>     | <span data-ttu-id="52ab9-115">kilo byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="52ab9-115">kilobyte multiplier</span></span> |
| <span data-ttu-id="52ab9-116">Bespaar</span><span class="sxs-lookup"><span data-stu-id="52ab9-116">mb</span></span>     | <span data-ttu-id="52ab9-117">Mega byte multiplier</span><span class="sxs-lookup"><span data-stu-id="52ab9-117">megabyte multiplier</span></span> |
| <span data-ttu-id="52ab9-118">GB</span><span class="sxs-lookup"><span data-stu-id="52ab9-118">gb</span></span>     | <span data-ttu-id="52ab9-119">Gigabyte multiplier</span><span class="sxs-lookup"><span data-stu-id="52ab9-119">gigabyte multiplier</span></span> |
| <span data-ttu-id="52ab9-120">TB</span><span class="sxs-lookup"><span data-stu-id="52ab9-120">tb</span></span>     | <span data-ttu-id="52ab9-121">terabyte-vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="52ab9-121">terabyte multiplier</span></span> |
| <span data-ttu-id="52ab9-122">jager</span><span class="sxs-lookup"><span data-stu-id="52ab9-122">pb</span></span>     | <span data-ttu-id="52ab9-123">PETA byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="52ab9-123">petabyte multiplier</span></span> |

<span data-ttu-id="52ab9-124">Het type van een letterlijke integerwaarde wordt bepaald door de waarde, het type achtervoegsel en het achtervoegsel van de numerieke vermenigvuldiger.</span><span class="sxs-lookup"><span data-stu-id="52ab9-124">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="52ab9-125">Voor een letterlijke integer zonder type achtervoegsel:</span><span class="sxs-lookup"><span data-stu-id="52ab9-125">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="52ab9-126">Als de waarde kan worden weer gegeven op type `[int]` , is dat van het type.</span><span class="sxs-lookup"><span data-stu-id="52ab9-126">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="52ab9-127">Als dat niet het geval is, kunt u ook de waarde van het `[long]` type opgeven.</span><span class="sxs-lookup"><span data-stu-id="52ab9-127">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="52ab9-128">Als dat niet het geval is, kunt u ook de waarde van het `[decimal]` type opgeven.</span><span class="sxs-lookup"><span data-stu-id="52ab9-128">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="52ab9-129">Anders wordt deze weer gegeven op type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="52ab9-129">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="52ab9-130">Voor een letterlijke integer met een type achtervoegsel:</span><span class="sxs-lookup"><span data-stu-id="52ab9-130">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="52ab9-131">Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[int]` dan is het type ervan `[int]` .</span><span class="sxs-lookup"><span data-stu-id="52ab9-131">If the type suffix is `u` and the value can be represented by type `[int]` then its type is `[int]`.</span></span>
- <span data-ttu-id="52ab9-132">Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[long]` dan is het type ervan `[long]` .</span><span class="sxs-lookup"><span data-stu-id="52ab9-132">If the type suffix is `u` and the value can be represented by type `[long]` then its type is `[long]`.</span></span>
- <span data-ttu-id="52ab9-133">Als de waarde ervan kan worden weer gegeven op type dat is opgegeven, is het type ervan.</span><span class="sxs-lookup"><span data-stu-id="52ab9-133">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="52ab9-134">Anders is de letterlijke waarde niet goed gevormd.</span><span class="sxs-lookup"><span data-stu-id="52ab9-134">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="52ab9-135">Echte letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="52ab9-135">Real literals</span></span>

<span data-ttu-id="52ab9-136">Echte letterlijke waarden kunnen alleen worden geschreven in de decimale notatie.</span><span class="sxs-lookup"><span data-stu-id="52ab9-136">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="52ab9-137">Deze notatie kan breuk waarden bevatten na een decimaal teken en een weten schappelijke notatie met een exponentieel onderdeel.</span><span class="sxs-lookup"><span data-stu-id="52ab9-137">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="52ab9-138">Het exponentiële deel bevat een ' e ', gevolgd door een optioneel teken (+/) en een getal dat de exponent voor stelt.</span><span class="sxs-lookup"><span data-stu-id="52ab9-138">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="52ab9-139">De letterlijke waarde is bijvoorbeeld `1e2` gelijk aan de numerieke waarde 100.</span><span class="sxs-lookup"><span data-stu-id="52ab9-139">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="52ab9-140">Echte letterlijke waarden kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.</span><span class="sxs-lookup"><span data-stu-id="52ab9-140">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="52ab9-141">Achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="52ab9-141">Suffix</span></span> |       <span data-ttu-id="52ab9-142">Betekenis</span><span class="sxs-lookup"><span data-stu-id="52ab9-142">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="52ab9-143">d</span><span class="sxs-lookup"><span data-stu-id="52ab9-143">d</span></span>      | <span data-ttu-id="52ab9-144">Decimal-gegevens type</span><span class="sxs-lookup"><span data-stu-id="52ab9-144">decimal data type</span></span>   |
| <span data-ttu-id="52ab9-145">KB823980</span><span class="sxs-lookup"><span data-stu-id="52ab9-145">kb</span></span>     | <span data-ttu-id="52ab9-146">kilo byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="52ab9-146">kilobyte multiplier</span></span> |
| <span data-ttu-id="52ab9-147">Bespaar</span><span class="sxs-lookup"><span data-stu-id="52ab9-147">mb</span></span>     | <span data-ttu-id="52ab9-148">Mega byte multiplier</span><span class="sxs-lookup"><span data-stu-id="52ab9-148">megabyte multiplier</span></span> |
| <span data-ttu-id="52ab9-149">GB</span><span class="sxs-lookup"><span data-stu-id="52ab9-149">gb</span></span>     | <span data-ttu-id="52ab9-150">Gigabyte multiplier</span><span class="sxs-lookup"><span data-stu-id="52ab9-150">gigabyte multiplier</span></span> |
| <span data-ttu-id="52ab9-151">TB</span><span class="sxs-lookup"><span data-stu-id="52ab9-151">tb</span></span>     | <span data-ttu-id="52ab9-152">terabyte-vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="52ab9-152">terabyte multiplier</span></span> |
| <span data-ttu-id="52ab9-153">jager</span><span class="sxs-lookup"><span data-stu-id="52ab9-153">pb</span></span>     | <span data-ttu-id="52ab9-154">PETA byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="52ab9-154">petabyte multiplier</span></span> |

<span data-ttu-id="52ab9-155">Er zijn twee soorten echte letterlijke waarde: dubbel en decimaal.</span><span class="sxs-lookup"><span data-stu-id="52ab9-155">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="52ab9-156">Deze worden aangegeven door de afwezigheid of aanwezigheid, respectievelijk van het decimale-type achtervoegsel.</span><span class="sxs-lookup"><span data-stu-id="52ab9-156">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="52ab9-157">Power shell biedt geen ondersteuning voor een letterlijke representatie van een `[float]` waarde.</span><span class="sxs-lookup"><span data-stu-id="52ab9-157">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="52ab9-158">Een dubbele echte letterlijke waarde is van het type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="52ab9-158">A double real literal has type `[double]`.</span></span> <span data-ttu-id="52ab9-159">Een decimale echte letterlijke waarde is van het type `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="52ab9-159">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="52ab9-160">Volg nullen in het gedeelte van een decimale letterlijke teken reeks zijn aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="52ab9-160">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="52ab9-161">Als de waarde van de cijfers van exponenten in een `[double]` echte letterlijke teken reeks kleiner is dan de minimale ondersteunde waarde, is de waarden van die `[double]` echte literal 0.</span><span class="sxs-lookup"><span data-stu-id="52ab9-161">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="52ab9-162">Als de waarde van de cijfers van exponenten in een `[decimal]` echte letterlijke teken reeks kleiner is dan de minimale hoeveelheid die wordt ondersteund, is deze literal onjuist.</span><span class="sxs-lookup"><span data-stu-id="52ab9-162">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="52ab9-163">Als de waarde van de cijfers van exponenten in een `[double]` of `[decimal]` echte letterlijke teken reeks groter is dan het maximum aantal dat wordt ondersteund, is de letterlijke teken reeks onjuist.</span><span class="sxs-lookup"><span data-stu-id="52ab9-163">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="52ab9-164">De syntaxis laat een dubbele echte letterlijke waarde een achtervoegsel van het type lang.</span><span class="sxs-lookup"><span data-stu-id="52ab9-164">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="52ab9-165">Power shell behandelt deze case als een letterlijke integer waarvan de waarde wordt weer gegeven op type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="52ab9-165">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="52ab9-166">Deze functie is bewaard voor achterwaartse compatibiliteit met eerdere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="52ab9-166">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="52ab9-167">Programmeurs worden echter niet aangeraden om gehele letterlijke tekens van dit formulier te gebruiken, omdat de werkelijke waarde van de letterlijke teken reeks eenvoudig kan worden verborgen.</span><span class="sxs-lookup"><span data-stu-id="52ab9-167">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="52ab9-168">Bijvoorbeeld: `1.2L` heeft waarde 1, `1.2345e1L` heeft waarde 12 en `1.2345e-5L` heeft waarde 0, geen van beide direct duidelijk.</span><span class="sxs-lookup"><span data-stu-id="52ab9-168">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="52ab9-169">Numerieke vermenigvuldigers</span><span class="sxs-lookup"><span data-stu-id="52ab9-169">Numeric multipliers</span></span>

<span data-ttu-id="52ab9-170">Voor het gemak kunnen integers en reële letterlijke waarden een numerieke vermenigvuldiger bevatten, waarmee een van de meest gebruikte machten van 2 wordt aangegeven.</span><span class="sxs-lookup"><span data-stu-id="52ab9-170">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="52ab9-171">De numerieke vermenigvuldiger kan worden geschreven in een combi natie van hoofd letters of kleine letter.</span><span class="sxs-lookup"><span data-stu-id="52ab9-171">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="52ab9-172">De vermenigvuldiger achtervoegsels kunnen worden gebruikt in combi natie met de `u` , `ul` en `l` typen achtervoegsels.</span><span class="sxs-lookup"><span data-stu-id="52ab9-172">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="52ab9-173">Voor beelden van vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="52ab9-173">Multiplier examples</span></span>

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a><span data-ttu-id="52ab9-174">Sneltoetsen voor numeriek type</span><span class="sxs-lookup"><span data-stu-id="52ab9-174">Numeric type accelerators</span></span>

<span data-ttu-id="52ab9-175">Power shell ondersteunt de volgende typen Accelerators:</span><span class="sxs-lookup"><span data-stu-id="52ab9-175">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="52ab9-176">Accelerator</span><span class="sxs-lookup"><span data-stu-id="52ab9-176">Accelerator</span></span> |         <span data-ttu-id="52ab9-177">Opmerking</span><span class="sxs-lookup"><span data-stu-id="52ab9-177">Note</span></span>         |           <span data-ttu-id="52ab9-178">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="52ab9-178">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="52ab9-179">Byte (niet ondertekend)</span><span class="sxs-lookup"><span data-stu-id="52ab9-179">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="52ab9-180">Byte (ondertekend)</span><span class="sxs-lookup"><span data-stu-id="52ab9-180">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="52ab9-181">16-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="52ab9-181">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="52ab9-182">16-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="52ab9-182">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="52ab9-183">32-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="52ab9-183">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="52ab9-184">alias voor `[int32]`</span><span class="sxs-lookup"><span data-stu-id="52ab9-184">alias for `[int32]`</span></span>  | <span data-ttu-id="52ab9-185">32-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="52ab9-185">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="52ab9-186">32-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="52ab9-186">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="52ab9-187">64-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="52ab9-187">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="52ab9-188">alias voor `[int64]`</span><span class="sxs-lookup"><span data-stu-id="52ab9-188">alias for `[int64]`</span></span>  | <span data-ttu-id="52ab9-189">64-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="52ab9-189">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="52ab9-190">64-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="52ab9-190">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="52ab9-191">Zie [BigInteger struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="52ab9-191">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="52ab9-192">Drijvende komma met enkele precisie</span><span class="sxs-lookup"><span data-stu-id="52ab9-192">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="52ab9-193">alias voor `[single]`</span><span class="sxs-lookup"><span data-stu-id="52ab9-193">alias for `[single]`</span></span> | <span data-ttu-id="52ab9-194">Drijvende komma met enkele precisie</span><span class="sxs-lookup"><span data-stu-id="52ab9-194">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="52ab9-195">Drijvende komma met dubbele precisie</span><span class="sxs-lookup"><span data-stu-id="52ab9-195">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="52ab9-196">128-bits drijvende komma</span><span class="sxs-lookup"><span data-stu-id="52ab9-196">128-bit floating point</span></span>           |

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="52ab9-197">Werken met andere numerieke typen</span><span class="sxs-lookup"><span data-stu-id="52ab9-197">Working with other numeric types</span></span>

<span data-ttu-id="52ab9-198">Als u wilt werken met andere numerieke typen, moet u type Accelerators gebruiken. Dit is niet mogelijk zonder dat er problemen zijn.</span><span class="sxs-lookup"><span data-stu-id="52ab9-198">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="52ab9-199">Zo worden hoge integerwaarden altijd geparseerd als dubbele waarden voordat ze naar een ander type worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="52ab9-199">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="52ab9-200">De waarde wordt als twee keer geparseerd, waarbij de precisie in de hogere bereiken verloren gaat.</span><span class="sxs-lookup"><span data-stu-id="52ab9-200">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="52ab9-201">U kunt dit probleem voor komen door waarden als teken reeksen in te voeren en deze vervolgens te converteren:</span><span class="sxs-lookup"><span data-stu-id="52ab9-201">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="52ab9-202">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="52ab9-202">Examples</span></span>

<span data-ttu-id="52ab9-203">De volgende tabel bevat verschillende voor beelden van numerieke letterlijke waarden en een lijst met het type en de waarde:</span><span class="sxs-lookup"><span data-stu-id="52ab9-203">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="52ab9-204">Getal</span><span class="sxs-lookup"><span data-stu-id="52ab9-204">Number</span></span>  |  <span data-ttu-id="52ab9-205">Type</span><span class="sxs-lookup"><span data-stu-id="52ab9-205">Type</span></span>   |    <span data-ttu-id="52ab9-206">Waarde</span><span class="sxs-lookup"><span data-stu-id="52ab9-206">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="52ab9-207">100</span><span class="sxs-lookup"><span data-stu-id="52ab9-207">100</span></span> | <span data-ttu-id="52ab9-208">Int32</span><span class="sxs-lookup"><span data-stu-id="52ab9-208">Int32</span></span>   |          <span data-ttu-id="52ab9-209">100</span><span class="sxs-lookup"><span data-stu-id="52ab9-209">100</span></span> |
|     <span data-ttu-id="52ab9-210">100D</span><span class="sxs-lookup"><span data-stu-id="52ab9-210">100D</span></span> | <span data-ttu-id="52ab9-211">Decimaal</span><span class="sxs-lookup"><span data-stu-id="52ab9-211">Decimal</span></span> |          <span data-ttu-id="52ab9-212">100</span><span class="sxs-lookup"><span data-stu-id="52ab9-212">100</span></span> |
|     <span data-ttu-id="52ab9-213">100l</span><span class="sxs-lookup"><span data-stu-id="52ab9-213">100l</span></span> | <span data-ttu-id="52ab9-214">Int64</span><span class="sxs-lookup"><span data-stu-id="52ab9-214">Int64</span></span>   |          <span data-ttu-id="52ab9-215">100</span><span class="sxs-lookup"><span data-stu-id="52ab9-215">100</span></span> |
|      <span data-ttu-id="52ab9-216">1e2</span><span class="sxs-lookup"><span data-stu-id="52ab9-216">1e2</span></span> | <span data-ttu-id="52ab9-217">Dubbel</span><span class="sxs-lookup"><span data-stu-id="52ab9-217">Double</span></span>  |          <span data-ttu-id="52ab9-218">100</span><span class="sxs-lookup"><span data-stu-id="52ab9-218">100</span></span> |
|     <span data-ttu-id="52ab9-219">1. E2</span><span class="sxs-lookup"><span data-stu-id="52ab9-219">1.e2</span></span> | <span data-ttu-id="52ab9-220">Dubbel</span><span class="sxs-lookup"><span data-stu-id="52ab9-220">Double</span></span>  |          <span data-ttu-id="52ab9-221">100</span><span class="sxs-lookup"><span data-stu-id="52ab9-221">100</span></span> |
|    <span data-ttu-id="52ab9-222">0x1e2</span><span class="sxs-lookup"><span data-stu-id="52ab9-222">0x1e2</span></span> | <span data-ttu-id="52ab9-223">Int32</span><span class="sxs-lookup"><span data-stu-id="52ab9-223">Int32</span></span>   |          <span data-ttu-id="52ab9-224">482</span><span class="sxs-lookup"><span data-stu-id="52ab9-224">482</span></span> |
|   <span data-ttu-id="52ab9-225">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="52ab9-225">0x1e2L</span></span> | <span data-ttu-id="52ab9-226">Int64</span><span class="sxs-lookup"><span data-stu-id="52ab9-226">Int64</span></span>   |          <span data-ttu-id="52ab9-227">482</span><span class="sxs-lookup"><span data-stu-id="52ab9-227">482</span></span> |
|   <span data-ttu-id="52ab9-228">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="52ab9-228">0x1e2D</span></span> | <span data-ttu-id="52ab9-229">Int32</span><span class="sxs-lookup"><span data-stu-id="52ab9-229">Int32</span></span>   |         <span data-ttu-id="52ab9-230">7725</span><span class="sxs-lookup"><span data-stu-id="52ab9-230">7725</span></span> |
|     <span data-ttu-id="52ab9-231">482D</span><span class="sxs-lookup"><span data-stu-id="52ab9-231">482D</span></span> | <span data-ttu-id="52ab9-232">Decimaal</span><span class="sxs-lookup"><span data-stu-id="52ab9-232">Decimal</span></span> |          <span data-ttu-id="52ab9-233">482</span><span class="sxs-lookup"><span data-stu-id="52ab9-233">482</span></span> |
|    <span data-ttu-id="52ab9-234">482gb</span><span class="sxs-lookup"><span data-stu-id="52ab9-234">482gb</span></span> | <span data-ttu-id="52ab9-235">Int64</span><span class="sxs-lookup"><span data-stu-id="52ab9-235">Int64</span></span>   | <span data-ttu-id="52ab9-236">517543559168</span><span class="sxs-lookup"><span data-stu-id="52ab9-236">517543559168</span></span> |
| <span data-ttu-id="52ab9-237">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="52ab9-237">0x1e2lgb</span></span> | <span data-ttu-id="52ab9-238">Int64</span><span class="sxs-lookup"><span data-stu-id="52ab9-238">Int64</span></span>   | <span data-ttu-id="52ab9-239">517543559168</span><span class="sxs-lookup"><span data-stu-id="52ab9-239">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="52ab9-240">Opdrachten die eruitzien als numerieke letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="52ab9-240">Commands that look like numeric literals</span></span>

<span data-ttu-id="52ab9-241">Elke opdracht die eruitziet als een numerieke literal moet worden uitgevoerd met de aanroep operator ( `&` ), anders wordt deze geïnterpreteerd als een nummer van het bijbehorende type.</span><span class="sxs-lookup"><span data-stu-id="52ab9-241">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="52ab9-242">Toegang tot eigenschappen en methoden van numerieke objecten</span><span class="sxs-lookup"><span data-stu-id="52ab9-242">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="52ab9-243">Om toegang te krijgen tot een lid van een numerieke letterlijke waarde, zijn er situaties waarin u de letterlijke teken reeks tussen haakjes moet plaatsen.</span><span class="sxs-lookup"><span data-stu-id="52ab9-243">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="52ab9-244">De letterlijke waarde heeft geen decimaal teken</span><span class="sxs-lookup"><span data-stu-id="52ab9-244">The literal does not have a decimal point</span></span>
- <span data-ttu-id="52ab9-245">De letterlijke waarde heeft geen cijfers na het decimaal teken</span><span class="sxs-lookup"><span data-stu-id="52ab9-245">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="52ab9-246">De letterlijke waarde heeft geen achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="52ab9-246">The literal does not have a suffix</span></span>

<span data-ttu-id="52ab9-247">Het volgende voor beeld mislukt bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="52ab9-247">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="52ab9-248">De volgende voor beelden werken:</span><span class="sxs-lookup"><span data-stu-id="52ab9-248">The following examples work:</span></span>

```
PS> 2L.GetType().Name
Int64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="52ab9-249">De eerste twee voor beelden werken zonder tussen haakjes, omdat de Power shell-parser kan bepalen waar de numerieke letterlijke waarde eindigt en de **gettype** -methode wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="52ab9-249">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
