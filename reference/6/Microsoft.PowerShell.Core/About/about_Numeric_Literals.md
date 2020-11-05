---
description: Zowel integere als reële numerieke letterlijke waarden kunnen type-en vermenigvuldiger-achtervoegsels hebben.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Numerieke letterlijke waarden
ms.openlocfilehash: dc1a55dbec1f0de99e06011645e6884b37480233
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354826"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="44e71-103">Numerieke letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="44e71-103">About numeric literals</span></span>

<span data-ttu-id="44e71-104">Er zijn twee soorten numerieke letterlijke waarden: geheel getal en werkelijk.</span><span class="sxs-lookup"><span data-stu-id="44e71-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="44e71-105">Beide kunnen type-en multiplier-achtervoegsels hebben.</span><span class="sxs-lookup"><span data-stu-id="44e71-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="44e71-106">Letterlijke tekens voor geheel getal</span><span class="sxs-lookup"><span data-stu-id="44e71-106">Integer literals</span></span>

<span data-ttu-id="44e71-107">Letterlijke tekens kunnen worden geschreven in decimale of hexadecimale notatie.</span><span class="sxs-lookup"><span data-stu-id="44e71-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="44e71-108">Hexadecimale letterlijke waarden worden voorafgegaan door met `0x` om ze te onderscheiden van decimale getallen.</span><span class="sxs-lookup"><span data-stu-id="44e71-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="44e71-109">Letterlijke tekens van een geheel getal kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.</span><span class="sxs-lookup"><span data-stu-id="44e71-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="44e71-110">Achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="44e71-110">Suffix</span></span> |            <span data-ttu-id="44e71-111">Betekenis</span><span class="sxs-lookup"><span data-stu-id="44e71-111">Meaning</span></span>             |          <span data-ttu-id="44e71-112">Notitie</span><span class="sxs-lookup"><span data-stu-id="44e71-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="44e71-113">y</span><span class="sxs-lookup"><span data-stu-id="44e71-113">y</span></span>      | <span data-ttu-id="44e71-114">gegevens type van ondertekend byte</span><span class="sxs-lookup"><span data-stu-id="44e71-114">signed byte data type</span></span>          | <span data-ttu-id="44e71-115">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="44e71-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="44e71-116">uy</span><span class="sxs-lookup"><span data-stu-id="44e71-116">uy</span></span>     | <span data-ttu-id="44e71-117">gegevens type niet-ondertekend byte</span><span class="sxs-lookup"><span data-stu-id="44e71-117">unsigned byte data type</span></span>        | <span data-ttu-id="44e71-118">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="44e71-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="44e71-119">s</span><span class="sxs-lookup"><span data-stu-id="44e71-119">s</span></span>      | <span data-ttu-id="44e71-120">kort gegevens type</span><span class="sxs-lookup"><span data-stu-id="44e71-120">short data type</span></span>                | <span data-ttu-id="44e71-121">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="44e71-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="44e71-122">VS</span><span class="sxs-lookup"><span data-stu-id="44e71-122">us</span></span>     | <span data-ttu-id="44e71-123">niet-ondertekend kort gegevens type</span><span class="sxs-lookup"><span data-stu-id="44e71-123">unsigned short data type</span></span>       | <span data-ttu-id="44e71-124">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="44e71-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="44e71-125">l</span><span class="sxs-lookup"><span data-stu-id="44e71-125">l</span></span>      | <span data-ttu-id="44e71-126">Long-gegevens type</span><span class="sxs-lookup"><span data-stu-id="44e71-126">long data type</span></span>                 |                         |
| <span data-ttu-id="44e71-127">h</span><span class="sxs-lookup"><span data-stu-id="44e71-127">u</span></span>      | <span data-ttu-id="44e71-128">niet-ondertekend int of Long-gegevens type</span><span class="sxs-lookup"><span data-stu-id="44e71-128">unsigned int or long data type</span></span> | <span data-ttu-id="44e71-129">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="44e71-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="44e71-130">UL</span><span class="sxs-lookup"><span data-stu-id="44e71-130">ul</span></span>     | <span data-ttu-id="44e71-131">niet-ondertekend Long-gegevens type</span><span class="sxs-lookup"><span data-stu-id="44e71-131">unsigned long data type</span></span>        | <span data-ttu-id="44e71-132">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="44e71-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="44e71-133">KB823980</span><span class="sxs-lookup"><span data-stu-id="44e71-133">kb</span></span>     | <span data-ttu-id="44e71-134">kilo byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="44e71-134">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="44e71-135">Bespaar</span><span class="sxs-lookup"><span data-stu-id="44e71-135">mb</span></span>     | <span data-ttu-id="44e71-136">Mega byte multiplier</span><span class="sxs-lookup"><span data-stu-id="44e71-136">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="44e71-137">GB</span><span class="sxs-lookup"><span data-stu-id="44e71-137">gb</span></span>     | <span data-ttu-id="44e71-138">Gigabyte multiplier</span><span class="sxs-lookup"><span data-stu-id="44e71-138">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="44e71-139">TB</span><span class="sxs-lookup"><span data-stu-id="44e71-139">tb</span></span>     | <span data-ttu-id="44e71-140">terabyte-vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="44e71-140">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="44e71-141">jager</span><span class="sxs-lookup"><span data-stu-id="44e71-141">pb</span></span>     | <span data-ttu-id="44e71-142">PETA byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="44e71-142">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="44e71-143">Het type van een letterlijke integerwaarde wordt bepaald door de waarde, het type achtervoegsel en het achtervoegsel van de numerieke vermenigvuldiger.</span><span class="sxs-lookup"><span data-stu-id="44e71-143">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="44e71-144">Voor een letterlijke integer zonder type achtervoegsel:</span><span class="sxs-lookup"><span data-stu-id="44e71-144">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="44e71-145">Als de waarde kan worden weer gegeven op type `[int]` , is dat van het type.</span><span class="sxs-lookup"><span data-stu-id="44e71-145">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="44e71-146">Als dat niet het geval is, kunt u ook de waarde van het `[long]` type opgeven.</span><span class="sxs-lookup"><span data-stu-id="44e71-146">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="44e71-147">Als dat niet het geval is, kunt u ook de waarde van het `[decimal]` type opgeven.</span><span class="sxs-lookup"><span data-stu-id="44e71-147">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="44e71-148">Anders wordt deze weer gegeven op type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="44e71-148">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="44e71-149">Voor een letterlijke integer met een type achtervoegsel:</span><span class="sxs-lookup"><span data-stu-id="44e71-149">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="44e71-150">Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[uint]` dan is het type ervan `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="44e71-150">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="44e71-151">Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[ulong]` dan is het type ervan `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="44e71-151">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="44e71-152">Als de waarde ervan kan worden weer gegeven op type dat is opgegeven, is het type ervan.</span><span class="sxs-lookup"><span data-stu-id="44e71-152">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="44e71-153">Anders is de letterlijke waarde niet goed gevormd.</span><span class="sxs-lookup"><span data-stu-id="44e71-153">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="44e71-154">Echte letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="44e71-154">Real literals</span></span>

<span data-ttu-id="44e71-155">Echte letterlijke waarden kunnen alleen worden geschreven in de decimale notatie.</span><span class="sxs-lookup"><span data-stu-id="44e71-155">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="44e71-156">Deze notatie kan breuk waarden bevatten na een decimaal teken en een weten schappelijke notatie met een exponentieel onderdeel.</span><span class="sxs-lookup"><span data-stu-id="44e71-156">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="44e71-157">Het exponentiële deel bevat een ' e ', gevolgd door een optioneel teken (+/) en een getal dat de exponent voor stelt.</span><span class="sxs-lookup"><span data-stu-id="44e71-157">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="44e71-158">De letterlijke waarde is bijvoorbeeld `1e2` gelijk aan de numerieke waarde 100.</span><span class="sxs-lookup"><span data-stu-id="44e71-158">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="44e71-159">Echte letterlijke waarden kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.</span><span class="sxs-lookup"><span data-stu-id="44e71-159">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="44e71-160">Achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="44e71-160">Suffix</span></span> |       <span data-ttu-id="44e71-161">Betekenis</span><span class="sxs-lookup"><span data-stu-id="44e71-161">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="44e71-162">d</span><span class="sxs-lookup"><span data-stu-id="44e71-162">d</span></span>      | <span data-ttu-id="44e71-163">Decimal-gegevens type</span><span class="sxs-lookup"><span data-stu-id="44e71-163">decimal data type</span></span>   |
| <span data-ttu-id="44e71-164">KB823980</span><span class="sxs-lookup"><span data-stu-id="44e71-164">kb</span></span>     | <span data-ttu-id="44e71-165">kilo byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="44e71-165">kilobyte multiplier</span></span> |
| <span data-ttu-id="44e71-166">Bespaar</span><span class="sxs-lookup"><span data-stu-id="44e71-166">mb</span></span>     | <span data-ttu-id="44e71-167">Mega byte multiplier</span><span class="sxs-lookup"><span data-stu-id="44e71-167">megabyte multiplier</span></span> |
| <span data-ttu-id="44e71-168">GB</span><span class="sxs-lookup"><span data-stu-id="44e71-168">gb</span></span>     | <span data-ttu-id="44e71-169">Gigabyte multiplier</span><span class="sxs-lookup"><span data-stu-id="44e71-169">gigabyte multiplier</span></span> |
| <span data-ttu-id="44e71-170">TB</span><span class="sxs-lookup"><span data-stu-id="44e71-170">tb</span></span>     | <span data-ttu-id="44e71-171">terabyte-vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="44e71-171">terabyte multiplier</span></span> |
| <span data-ttu-id="44e71-172">jager</span><span class="sxs-lookup"><span data-stu-id="44e71-172">pb</span></span>     | <span data-ttu-id="44e71-173">PETA byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="44e71-173">petabyte multiplier</span></span> |

<span data-ttu-id="44e71-174">Er zijn twee soorten echte letterlijke waarde: dubbel en decimaal.</span><span class="sxs-lookup"><span data-stu-id="44e71-174">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="44e71-175">Deze worden aangegeven door de afwezigheid of aanwezigheid, respectievelijk van het decimale-type achtervoegsel.</span><span class="sxs-lookup"><span data-stu-id="44e71-175">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="44e71-176">Power shell biedt geen ondersteuning voor een letterlijke representatie van een `[float]` waarde.</span><span class="sxs-lookup"><span data-stu-id="44e71-176">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="44e71-177">Een dubbele echte letterlijke waarde is van het type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="44e71-177">A double real literal has type `[double]`.</span></span> <span data-ttu-id="44e71-178">Een decimale echte letterlijke waarde is van het type `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="44e71-178">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="44e71-179">Volg nullen in het gedeelte van een decimale letterlijke teken reeks zijn aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="44e71-179">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="44e71-180">Als de waarde van de cijfers van exponenten in een `[double]` echte letterlijke teken reeks kleiner is dan de minimale ondersteunde waarde, is de waarden van die `[double]` echte literal 0.</span><span class="sxs-lookup"><span data-stu-id="44e71-180">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="44e71-181">Als de waarde van de cijfers van exponenten in een `[decimal]` echte letterlijke teken reeks kleiner is dan de minimale hoeveelheid die wordt ondersteund, is deze literal onjuist.</span><span class="sxs-lookup"><span data-stu-id="44e71-181">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="44e71-182">Als de waarde van de cijfers van exponenten in een `[double]` of `[decimal]` echte letterlijke teken reeks groter is dan het maximum aantal dat wordt ondersteund, is de letterlijke teken reeks onjuist.</span><span class="sxs-lookup"><span data-stu-id="44e71-182">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="44e71-183">De syntaxis laat een dubbele echte letterlijke waarde een achtervoegsel van het type lang.</span><span class="sxs-lookup"><span data-stu-id="44e71-183">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="44e71-184">Power shell behandelt deze case als een letterlijke integer waarvan de waarde wordt weer gegeven op type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="44e71-184">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="44e71-185">Deze functie is bewaard voor achterwaartse compatibiliteit met eerdere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="44e71-185">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="44e71-186">Programmeurs worden echter niet aangeraden om gehele letterlijke tekens van dit formulier te gebruiken, omdat de werkelijke waarde van de letterlijke teken reeks eenvoudig kan worden verborgen.</span><span class="sxs-lookup"><span data-stu-id="44e71-186">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="44e71-187">Bijvoorbeeld: `1.2L` heeft waarde 1, `1.2345e1L` heeft waarde 12 en `1.2345e-5L` heeft waarde 0, geen van beide direct duidelijk.</span><span class="sxs-lookup"><span data-stu-id="44e71-187">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="44e71-188">Numerieke vermenigvuldigers</span><span class="sxs-lookup"><span data-stu-id="44e71-188">Numeric multipliers</span></span>

<span data-ttu-id="44e71-189">Voor het gemak kunnen integers en reële letterlijke waarden een numerieke vermenigvuldiger bevatten, waarmee een van de meest gebruikte machten van 2 wordt aangegeven.</span><span class="sxs-lookup"><span data-stu-id="44e71-189">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="44e71-190">De numerieke vermenigvuldiger kan worden geschreven in een combi natie van hoofd letters of kleine letter.</span><span class="sxs-lookup"><span data-stu-id="44e71-190">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="44e71-191">De vermenigvuldiger achtervoegsels kunnen worden gebruikt in combi natie met de `u` , `ul` en `l` typen achtervoegsels.</span><span class="sxs-lookup"><span data-stu-id="44e71-191">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="44e71-192">Voor beelden van vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="44e71-192">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="44e71-193">Sneltoetsen voor numeriek type</span><span class="sxs-lookup"><span data-stu-id="44e71-193">Numeric type accelerators</span></span>

<span data-ttu-id="44e71-194">Power shell ondersteunt de volgende typen Accelerators:</span><span class="sxs-lookup"><span data-stu-id="44e71-194">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="44e71-195">Accelerator</span><span class="sxs-lookup"><span data-stu-id="44e71-195">Accelerator</span></span> |         <span data-ttu-id="44e71-196">Notitie</span><span class="sxs-lookup"><span data-stu-id="44e71-196">Note</span></span>         |           <span data-ttu-id="44e71-197">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="44e71-197">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="44e71-198">Byte (niet ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-198">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="44e71-199">Byte (ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-199">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="44e71-200">16-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="44e71-200">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="44e71-201">alias voor `[int16]`</span><span class="sxs-lookup"><span data-stu-id="44e71-201">alias for `[int16]`</span></span>  | <span data-ttu-id="44e71-202">16-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="44e71-202">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="44e71-203">16-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-203">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="44e71-204">alias voor `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="44e71-204">alias for `[uint16]`</span></span> | <span data-ttu-id="44e71-205">16-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-205">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="44e71-206">32-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="44e71-206">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="44e71-207">alias voor `[int32]`</span><span class="sxs-lookup"><span data-stu-id="44e71-207">alias for `[int32]`</span></span>  | <span data-ttu-id="44e71-208">32-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="44e71-208">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="44e71-209">32-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-209">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="44e71-210">alias voor `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="44e71-210">alias for `[uint32]`</span></span> | <span data-ttu-id="44e71-211">32-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-211">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="44e71-212">64-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="44e71-212">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="44e71-213">alias voor `[int64]`</span><span class="sxs-lookup"><span data-stu-id="44e71-213">alias for `[int64]`</span></span>  | <span data-ttu-id="44e71-214">64-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="44e71-214">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="44e71-215">64-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-215">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="44e71-216">alias voor `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="44e71-216">alias for `[uint64]`</span></span> | <span data-ttu-id="44e71-217">64-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="44e71-217">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="44e71-218">Zie [BigInteger struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="44e71-218">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="44e71-219">Drijvende komma met enkele precisie</span><span class="sxs-lookup"><span data-stu-id="44e71-219">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="44e71-220">alias voor `[single]`</span><span class="sxs-lookup"><span data-stu-id="44e71-220">alias for `[single]`</span></span> | <span data-ttu-id="44e71-221">Drijvende komma met enkele precisie</span><span class="sxs-lookup"><span data-stu-id="44e71-221">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="44e71-222">Drijvende komma met dubbele precisie</span><span class="sxs-lookup"><span data-stu-id="44e71-222">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="44e71-223">128-bits drijvende komma</span><span class="sxs-lookup"><span data-stu-id="44e71-223">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="44e71-224">De volgende typen Accelerators zijn toegevoegd aan Power shell 6,2: `[short]` , `[ushort]` , `[uint]` , `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="44e71-224">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="44e71-225">Werken met andere numerieke typen</span><span class="sxs-lookup"><span data-stu-id="44e71-225">Working with other numeric types</span></span>

<span data-ttu-id="44e71-226">Als u wilt werken met andere numerieke typen, moet u type Accelerators gebruiken. Dit is niet mogelijk zonder dat er problemen zijn.</span><span class="sxs-lookup"><span data-stu-id="44e71-226">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="44e71-227">Zo worden hoge integerwaarden altijd geparseerd als dubbele waarden voordat ze naar een ander type worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="44e71-227">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="44e71-228">De waarde wordt als twee keer geparseerd, waarbij de precisie in de hogere bereiken verloren gaat.</span><span class="sxs-lookup"><span data-stu-id="44e71-228">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="44e71-229">U kunt dit probleem voor komen door waarden als teken reeksen in te voeren en deze vervolgens te converteren:</span><span class="sxs-lookup"><span data-stu-id="44e71-229">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="44e71-230">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="44e71-230">Examples</span></span>

<span data-ttu-id="44e71-231">De volgende tabel bevat verschillende voor beelden van numerieke letterlijke waarden en een lijst met het type en de waarde:</span><span class="sxs-lookup"><span data-stu-id="44e71-231">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="44e71-232">Getal</span><span class="sxs-lookup"><span data-stu-id="44e71-232">Number</span></span>  |  <span data-ttu-id="44e71-233">Type</span><span class="sxs-lookup"><span data-stu-id="44e71-233">Type</span></span>   |    <span data-ttu-id="44e71-234">Waarde</span><span class="sxs-lookup"><span data-stu-id="44e71-234">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="44e71-235">100</span><span class="sxs-lookup"><span data-stu-id="44e71-235">100</span></span> | <span data-ttu-id="44e71-236">Int32</span><span class="sxs-lookup"><span data-stu-id="44e71-236">Int32</span></span>   |          <span data-ttu-id="44e71-237">100</span><span class="sxs-lookup"><span data-stu-id="44e71-237">100</span></span> |
|     <span data-ttu-id="44e71-238">100D</span><span class="sxs-lookup"><span data-stu-id="44e71-238">100D</span></span> | <span data-ttu-id="44e71-239">Decimaal</span><span class="sxs-lookup"><span data-stu-id="44e71-239">Decimal</span></span> |          <span data-ttu-id="44e71-240">100</span><span class="sxs-lookup"><span data-stu-id="44e71-240">100</span></span> |
|     <span data-ttu-id="44e71-241">100l</span><span class="sxs-lookup"><span data-stu-id="44e71-241">100l</span></span> | <span data-ttu-id="44e71-242">Int64</span><span class="sxs-lookup"><span data-stu-id="44e71-242">Int64</span></span>   |          <span data-ttu-id="44e71-243">100</span><span class="sxs-lookup"><span data-stu-id="44e71-243">100</span></span> |
|    <span data-ttu-id="44e71-244">100uL</span><span class="sxs-lookup"><span data-stu-id="44e71-244">100uL</span></span> | <span data-ttu-id="44e71-245">UInt64</span><span class="sxs-lookup"><span data-stu-id="44e71-245">UInt64</span></span>  |          <span data-ttu-id="44e71-246">100</span><span class="sxs-lookup"><span data-stu-id="44e71-246">100</span></span> |
|    <span data-ttu-id="44e71-247">100us</span><span class="sxs-lookup"><span data-stu-id="44e71-247">100us</span></span> | <span data-ttu-id="44e71-248">UInt16</span><span class="sxs-lookup"><span data-stu-id="44e71-248">UInt16</span></span>  |          <span data-ttu-id="44e71-249">100</span><span class="sxs-lookup"><span data-stu-id="44e71-249">100</span></span> |
|    <span data-ttu-id="44e71-250">100uy</span><span class="sxs-lookup"><span data-stu-id="44e71-250">100uy</span></span> | <span data-ttu-id="44e71-251">Byte</span><span class="sxs-lookup"><span data-stu-id="44e71-251">Byte</span></span>    |          <span data-ttu-id="44e71-252">100</span><span class="sxs-lookup"><span data-stu-id="44e71-252">100</span></span> |
|     <span data-ttu-id="44e71-253">100y</span><span class="sxs-lookup"><span data-stu-id="44e71-253">100y</span></span> | <span data-ttu-id="44e71-254">SByte</span><span class="sxs-lookup"><span data-stu-id="44e71-254">SByte</span></span>   |          <span data-ttu-id="44e71-255">100</span><span class="sxs-lookup"><span data-stu-id="44e71-255">100</span></span> |
|      <span data-ttu-id="44e71-256">1e2</span><span class="sxs-lookup"><span data-stu-id="44e71-256">1e2</span></span> | <span data-ttu-id="44e71-257">Dubbel</span><span class="sxs-lookup"><span data-stu-id="44e71-257">Double</span></span>  |          <span data-ttu-id="44e71-258">100</span><span class="sxs-lookup"><span data-stu-id="44e71-258">100</span></span> |
|     <span data-ttu-id="44e71-259">1. E2</span><span class="sxs-lookup"><span data-stu-id="44e71-259">1.e2</span></span> | <span data-ttu-id="44e71-260">Dubbel</span><span class="sxs-lookup"><span data-stu-id="44e71-260">Double</span></span>  |          <span data-ttu-id="44e71-261">100</span><span class="sxs-lookup"><span data-stu-id="44e71-261">100</span></span> |
|    <span data-ttu-id="44e71-262">0x1e2</span><span class="sxs-lookup"><span data-stu-id="44e71-262">0x1e2</span></span> | <span data-ttu-id="44e71-263">Int32</span><span class="sxs-lookup"><span data-stu-id="44e71-263">Int32</span></span>   |          <span data-ttu-id="44e71-264">482</span><span class="sxs-lookup"><span data-stu-id="44e71-264">482</span></span> |
|   <span data-ttu-id="44e71-265">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="44e71-265">0x1e2L</span></span> | <span data-ttu-id="44e71-266">Int64</span><span class="sxs-lookup"><span data-stu-id="44e71-266">Int64</span></span>   |          <span data-ttu-id="44e71-267">482</span><span class="sxs-lookup"><span data-stu-id="44e71-267">482</span></span> |
|   <span data-ttu-id="44e71-268">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="44e71-268">0x1e2D</span></span> | <span data-ttu-id="44e71-269">Int32</span><span class="sxs-lookup"><span data-stu-id="44e71-269">Int32</span></span>   |         <span data-ttu-id="44e71-270">7725</span><span class="sxs-lookup"><span data-stu-id="44e71-270">7725</span></span> |
|     <span data-ttu-id="44e71-271">482D</span><span class="sxs-lookup"><span data-stu-id="44e71-271">482D</span></span> | <span data-ttu-id="44e71-272">Decimaal</span><span class="sxs-lookup"><span data-stu-id="44e71-272">Decimal</span></span> |          <span data-ttu-id="44e71-273">482</span><span class="sxs-lookup"><span data-stu-id="44e71-273">482</span></span> |
|    <span data-ttu-id="44e71-274">482gb</span><span class="sxs-lookup"><span data-stu-id="44e71-274">482gb</span></span> | <span data-ttu-id="44e71-275">Int64</span><span class="sxs-lookup"><span data-stu-id="44e71-275">Int64</span></span>   | <span data-ttu-id="44e71-276">517543559168</span><span class="sxs-lookup"><span data-stu-id="44e71-276">517543559168</span></span> |
| <span data-ttu-id="44e71-277">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="44e71-277">0x1e2lgb</span></span> | <span data-ttu-id="44e71-278">Int64</span><span class="sxs-lookup"><span data-stu-id="44e71-278">Int64</span></span>   | <span data-ttu-id="44e71-279">517543559168</span><span class="sxs-lookup"><span data-stu-id="44e71-279">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="44e71-280">Opdrachten die eruitzien als numerieke letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="44e71-280">Commands that look like numeric literals</span></span>

<span data-ttu-id="44e71-281">Elke opdracht die eruitziet als een numerieke literal moet worden uitgevoerd met de aanroep operator ( `&` ), anders wordt deze geïnterpreteerd als een nummer van het bijbehorende type.</span><span class="sxs-lookup"><span data-stu-id="44e71-281">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="44e71-282">Toegang tot eigenschappen en methoden van numerieke objecten</span><span class="sxs-lookup"><span data-stu-id="44e71-282">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="44e71-283">Om toegang te krijgen tot een lid van een numerieke letterlijke waarde, zijn er situaties waarin u de letterlijke teken reeks tussen haakjes moet plaatsen.</span><span class="sxs-lookup"><span data-stu-id="44e71-283">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="44e71-284">De letterlijke waarde heeft geen decimaal teken</span><span class="sxs-lookup"><span data-stu-id="44e71-284">The literal does not have a decimal point</span></span>
- <span data-ttu-id="44e71-285">De letterlijke waarde heeft geen cijfers na het decimaal teken</span><span class="sxs-lookup"><span data-stu-id="44e71-285">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="44e71-286">De letterlijke waarde heeft geen achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="44e71-286">The literal does not have a suffix</span></span>

<span data-ttu-id="44e71-287">Het volgende voor beeld mislukt bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="44e71-287">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="44e71-288">De volgende voor beelden werken:</span><span class="sxs-lookup"><span data-stu-id="44e71-288">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="44e71-289">De eerste twee voor beelden werken zonder tussen haakjes, omdat de Power shell-parser kan bepalen waar de numerieke letterlijke waarde eindigt en de **gettype** -methode wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="44e71-289">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
