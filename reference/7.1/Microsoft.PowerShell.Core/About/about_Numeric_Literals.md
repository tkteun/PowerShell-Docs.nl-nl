---
description: Zowel integere als reële numerieke letterlijke waarden kunnen type-en vermenigvuldiger-achtervoegsels hebben.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Numerieke letterlijke waarden
ms.openlocfilehash: 25518b80f87c90c59829bb575b059f0efcadd566
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252957"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="94189-103">Numerieke letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="94189-103">About numeric literals</span></span>

<span data-ttu-id="94189-104">Er zijn twee soorten numerieke letterlijke waarden: geheel getal en werkelijk.</span><span class="sxs-lookup"><span data-stu-id="94189-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="94189-105">Beide kunnen type-en multiplier-achtervoegsels hebben.</span><span class="sxs-lookup"><span data-stu-id="94189-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="94189-106">Letterlijke tekens voor geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-106">Integer literals</span></span>

<span data-ttu-id="94189-107">Letterlijke tekens kunnen worden geschreven in decimale, hexadecimale of binaire notaties.</span><span class="sxs-lookup"><span data-stu-id="94189-107">Integer literals can be written in decimal, hexadecimal, or binary notation.</span></span>
<span data-ttu-id="94189-108">Hexadecimale letterlijke waarden worden voorafgegaan door `0x` en binaire letterlijke waarden worden voorafgegaan door `0b` om ze te onderscheiden van decimale getallen.</span><span class="sxs-lookup"><span data-stu-id="94189-108">Hexadecimal literals are prefixed with `0x` and binary literals are prefixed with `0b` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="94189-109">Letterlijke tekens van een geheel getal kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.</span><span class="sxs-lookup"><span data-stu-id="94189-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="94189-110">Achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="94189-110">Suffix</span></span> |            <span data-ttu-id="94189-111">Betekenis</span><span class="sxs-lookup"><span data-stu-id="94189-111">Meaning</span></span>             |          <span data-ttu-id="94189-112">Opmerking</span><span class="sxs-lookup"><span data-stu-id="94189-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="94189-113">y</span><span class="sxs-lookup"><span data-stu-id="94189-113">y</span></span>      | <span data-ttu-id="94189-114">gegevens type van ondertekend byte</span><span class="sxs-lookup"><span data-stu-id="94189-114">signed byte data type</span></span>          | <span data-ttu-id="94189-115">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="94189-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="94189-116">uy</span><span class="sxs-lookup"><span data-stu-id="94189-116">uy</span></span>     | <span data-ttu-id="94189-117">gegevens type niet-ondertekend byte</span><span class="sxs-lookup"><span data-stu-id="94189-117">unsigned byte data type</span></span>        | <span data-ttu-id="94189-118">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="94189-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="94189-119">s</span><span class="sxs-lookup"><span data-stu-id="94189-119">s</span></span>      | <span data-ttu-id="94189-120">kort gegevens type</span><span class="sxs-lookup"><span data-stu-id="94189-120">short data type</span></span>                | <span data-ttu-id="94189-121">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="94189-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="94189-122">VS</span><span class="sxs-lookup"><span data-stu-id="94189-122">us</span></span>     | <span data-ttu-id="94189-123">niet-ondertekend kort gegevens type</span><span class="sxs-lookup"><span data-stu-id="94189-123">unsigned short data type</span></span>       | <span data-ttu-id="94189-124">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="94189-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="94189-125">l</span><span class="sxs-lookup"><span data-stu-id="94189-125">l</span></span>      | <span data-ttu-id="94189-126">Long-gegevens type</span><span class="sxs-lookup"><span data-stu-id="94189-126">long data type</span></span>                 |                         |
| <span data-ttu-id="94189-127">h</span><span class="sxs-lookup"><span data-stu-id="94189-127">u</span></span>      | <span data-ttu-id="94189-128">niet-ondertekend int of Long-gegevens type</span><span class="sxs-lookup"><span data-stu-id="94189-128">unsigned int or long data type</span></span> | <span data-ttu-id="94189-129">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="94189-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="94189-130">UL</span><span class="sxs-lookup"><span data-stu-id="94189-130">ul</span></span>     | <span data-ttu-id="94189-131">niet-ondertekend Long-gegevens type</span><span class="sxs-lookup"><span data-stu-id="94189-131">unsigned long data type</span></span>        | <span data-ttu-id="94189-132">Toegevoegd in Power shell 6,2</span><span class="sxs-lookup"><span data-stu-id="94189-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="94189-133">n</span><span class="sxs-lookup"><span data-stu-id="94189-133">n</span></span>      | <span data-ttu-id="94189-134">BigInteger-gegevens type</span><span class="sxs-lookup"><span data-stu-id="94189-134">BigInteger data type</span></span>           | <span data-ttu-id="94189-135">Toegevoegd in Power shell 7,0</span><span class="sxs-lookup"><span data-stu-id="94189-135">Added in PowerShell 7.0</span></span> |
| <span data-ttu-id="94189-136">KB823980</span><span class="sxs-lookup"><span data-stu-id="94189-136">kb</span></span>     | <span data-ttu-id="94189-137">kilo byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="94189-137">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="94189-138">Bespaar</span><span class="sxs-lookup"><span data-stu-id="94189-138">mb</span></span>     | <span data-ttu-id="94189-139">Mega byte multiplier</span><span class="sxs-lookup"><span data-stu-id="94189-139">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="94189-140">GB</span><span class="sxs-lookup"><span data-stu-id="94189-140">gb</span></span>     | <span data-ttu-id="94189-141">Gigabyte multiplier</span><span class="sxs-lookup"><span data-stu-id="94189-141">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="94189-142">TB</span><span class="sxs-lookup"><span data-stu-id="94189-142">tb</span></span>     | <span data-ttu-id="94189-143">terabyte-vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="94189-143">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="94189-144">jager</span><span class="sxs-lookup"><span data-stu-id="94189-144">pb</span></span>     | <span data-ttu-id="94189-145">PETA byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="94189-145">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="94189-146">Het type van een letterlijke integerwaarde wordt bepaald door de waarde, het type achtervoegsel en het achtervoegsel van de numerieke vermenigvuldiger.</span><span class="sxs-lookup"><span data-stu-id="94189-146">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="94189-147">Voor een letterlijke integer zonder type achtervoegsel:</span><span class="sxs-lookup"><span data-stu-id="94189-147">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="94189-148">Als de waarde kan worden weer gegeven op type `[int]` , is dat van het type.</span><span class="sxs-lookup"><span data-stu-id="94189-148">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="94189-149">Als dat niet het geval is, kunt u ook de waarde van het `[long]` type opgeven.</span><span class="sxs-lookup"><span data-stu-id="94189-149">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="94189-150">Als dat niet het geval is, kunt u ook de waarde van het `[decimal]` type opgeven.</span><span class="sxs-lookup"><span data-stu-id="94189-150">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="94189-151">Anders wordt deze weer gegeven op type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="94189-151">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="94189-152">Voor een letterlijke integer met een type achtervoegsel:</span><span class="sxs-lookup"><span data-stu-id="94189-152">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="94189-153">Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[uint]` dan is het type ervan `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="94189-153">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="94189-154">Als het type achtervoegsel is `u` en de waarde kan worden weer gegeven op type, `[ulong]` dan is het type ervan `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="94189-154">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="94189-155">Als de waarde ervan kan worden weer gegeven op type dat is opgegeven, is het type ervan.</span><span class="sxs-lookup"><span data-stu-id="94189-155">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="94189-156">Anders is de letterlijke waarde niet goed gevormd.</span><span class="sxs-lookup"><span data-stu-id="94189-156">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="94189-157">Echte letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="94189-157">Real literals</span></span>

<span data-ttu-id="94189-158">Echte letterlijke waarden kunnen alleen worden geschreven in de decimale notatie.</span><span class="sxs-lookup"><span data-stu-id="94189-158">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="94189-159">Deze notatie kan breuk waarden bevatten na een decimaal teken en een weten schappelijke notatie met een exponentieel onderdeel.</span><span class="sxs-lookup"><span data-stu-id="94189-159">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="94189-160">Het exponentiële deel bevat een ' e ', gevolgd door een optioneel teken (+/) en een getal dat de exponent voor stelt.</span><span class="sxs-lookup"><span data-stu-id="94189-160">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="94189-161">De letterlijke waarde is bijvoorbeeld `1e2` gelijk aan de numerieke waarde 100.</span><span class="sxs-lookup"><span data-stu-id="94189-161">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="94189-162">Echte letterlijke waarden kunnen een type achtervoegsel en een vermenigvuldigings achtervoegsel hebben.</span><span class="sxs-lookup"><span data-stu-id="94189-162">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="94189-163">Achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="94189-163">Suffix</span></span> |       <span data-ttu-id="94189-164">Betekenis</span><span class="sxs-lookup"><span data-stu-id="94189-164">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="94189-165">d</span><span class="sxs-lookup"><span data-stu-id="94189-165">d</span></span>      | <span data-ttu-id="94189-166">Decimal-gegevens type</span><span class="sxs-lookup"><span data-stu-id="94189-166">decimal data type</span></span>   |
| <span data-ttu-id="94189-167">KB823980</span><span class="sxs-lookup"><span data-stu-id="94189-167">kb</span></span>     | <span data-ttu-id="94189-168">kilo byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="94189-168">kilobyte multiplier</span></span> |
| <span data-ttu-id="94189-169">Bespaar</span><span class="sxs-lookup"><span data-stu-id="94189-169">mb</span></span>     | <span data-ttu-id="94189-170">Mega byte multiplier</span><span class="sxs-lookup"><span data-stu-id="94189-170">megabyte multiplier</span></span> |
| <span data-ttu-id="94189-171">GB</span><span class="sxs-lookup"><span data-stu-id="94189-171">gb</span></span>     | <span data-ttu-id="94189-172">Gigabyte multiplier</span><span class="sxs-lookup"><span data-stu-id="94189-172">gigabyte multiplier</span></span> |
| <span data-ttu-id="94189-173">TB</span><span class="sxs-lookup"><span data-stu-id="94189-173">tb</span></span>     | <span data-ttu-id="94189-174">terabyte-vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="94189-174">terabyte multiplier</span></span> |
| <span data-ttu-id="94189-175">jager</span><span class="sxs-lookup"><span data-stu-id="94189-175">pb</span></span>     | <span data-ttu-id="94189-176">PETA byte vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="94189-176">petabyte multiplier</span></span> |

<span data-ttu-id="94189-177">Er zijn twee soorten echte letterlijke waarde: dubbel en decimaal.</span><span class="sxs-lookup"><span data-stu-id="94189-177">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="94189-178">Deze worden aangegeven door de afwezigheid of aanwezigheid, respectievelijk van het decimale-type achtervoegsel.</span><span class="sxs-lookup"><span data-stu-id="94189-178">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="94189-179">Power shell biedt geen ondersteuning voor een letterlijke representatie van een `[float]` waarde.</span><span class="sxs-lookup"><span data-stu-id="94189-179">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="94189-180">Een dubbele echte letterlijke waarde is van het type `[double]` .</span><span class="sxs-lookup"><span data-stu-id="94189-180">A double real literal has type `[double]`.</span></span> <span data-ttu-id="94189-181">Een decimale echte letterlijke waarde is van het type `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="94189-181">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="94189-182">Volg nullen in het gedeelte van een decimale letterlijke teken reeks zijn aanzienlijk.</span><span class="sxs-lookup"><span data-stu-id="94189-182">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="94189-183">Als de waarde van de cijfers van exponenten in een `[double]` echte letterlijke teken reeks kleiner is dan de minimale ondersteunde waarde, is de waarden van die `[double]` echte literal 0.</span><span class="sxs-lookup"><span data-stu-id="94189-183">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="94189-184">Als de waarde van de cijfers van exponenten in een `[decimal]` echte letterlijke teken reeks kleiner is dan de minimale hoeveelheid die wordt ondersteund, is deze literal onjuist.</span><span class="sxs-lookup"><span data-stu-id="94189-184">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="94189-185">Als de waarde van de cijfers van exponenten in een `[double]` of `[decimal]` echte letterlijke teken reeks groter is dan het maximum aantal dat wordt ondersteund, is de letterlijke teken reeks onjuist.</span><span class="sxs-lookup"><span data-stu-id="94189-185">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="94189-186">De syntaxis laat een dubbele echte letterlijke waarde een achtervoegsel van het type lang.</span><span class="sxs-lookup"><span data-stu-id="94189-186">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="94189-187">Power shell behandelt deze case als een letterlijke integer waarvan de waarde wordt weer gegeven op type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="94189-187">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="94189-188">Deze functie is bewaard voor achterwaartse compatibiliteit met eerdere versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="94189-188">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="94189-189">Programmeurs worden echter niet aangeraden om gehele letterlijke tekens van dit formulier te gebruiken, omdat de werkelijke waarde van de letterlijke teken reeks eenvoudig kan worden verborgen.</span><span class="sxs-lookup"><span data-stu-id="94189-189">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="94189-190">Bijvoorbeeld: `1.2L` heeft waarde 1, `1.2345e1L` heeft waarde 12 en `1.2345e-5L` heeft waarde 0, geen van beide direct duidelijk.</span><span class="sxs-lookup"><span data-stu-id="94189-190">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="94189-191">Numerieke vermenigvuldigers</span><span class="sxs-lookup"><span data-stu-id="94189-191">Numeric multipliers</span></span>

<span data-ttu-id="94189-192">Voor het gemak kunnen integers en reële letterlijke waarden een numerieke vermenigvuldiger bevatten, waarmee een van de meest gebruikte machten van 2 wordt aangegeven.</span><span class="sxs-lookup"><span data-stu-id="94189-192">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="94189-193">De numerieke vermenigvuldiger kan worden geschreven in een combi natie van hoofd letters of kleine letter.</span><span class="sxs-lookup"><span data-stu-id="94189-193">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="94189-194">De vermenigvuldiger achtervoegsels kunnen worden gebruikt in combi natie met eventuele type achtervoegsels, maar moeten aanwezig zijn na het type achtervoegsel.</span><span class="sxs-lookup"><span data-stu-id="94189-194">The multiplier suffixes can be used in combination with any type suffixes, but must be present after the type suffix.</span></span> <span data-ttu-id="94189-195">De letterlijke waarde `100gbL` is bijvoorbeeld ongeldig, maar de letterlijke waarde `100Lgb` is geldig.</span><span class="sxs-lookup"><span data-stu-id="94189-195">For example, the literal `100gbL` is malformed, but the literal `100Lgb` is valid.</span></span>

<span data-ttu-id="94189-196">Als een vermenigvuldiger een waarde maakt die de mogelijke waarden voor het numerieke type dat het achtervoegsel opgeeft, overschrijdt, is de letterlijke teken reeks ongeldig.</span><span class="sxs-lookup"><span data-stu-id="94189-196">If a multiplier creates a value that exceeds the possible values for the numeric type that the suffix specifies, the literal is malformed.</span></span> <span data-ttu-id="94189-197">De letterlijke `1usgb` waarde is bijvoorbeeld onjuist, omdat deze `1gb` groter is dan is toegestaan voor het `[ushort]` type dat is opgegeven door het `us` achtervoegsel.</span><span class="sxs-lookup"><span data-stu-id="94189-197">For example, the literal `1usgb` is malformed, because the value `1gb` is larger than what is permitted for the `[ushort]` type specified by the `us` suffix.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="94189-198">Voor beelden van vermenigvuldiger</span><span class="sxs-lookup"><span data-stu-id="94189-198">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="94189-199">Sneltoetsen voor numeriek type</span><span class="sxs-lookup"><span data-stu-id="94189-199">Numeric type accelerators</span></span>

<span data-ttu-id="94189-200">Power shell ondersteunt de volgende typen Accelerators:</span><span class="sxs-lookup"><span data-stu-id="94189-200">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="94189-201">Accelerator</span><span class="sxs-lookup"><span data-stu-id="94189-201">Accelerator</span></span> |         <span data-ttu-id="94189-202">Opmerking</span><span class="sxs-lookup"><span data-stu-id="94189-202">Note</span></span>         |           <span data-ttu-id="94189-203">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="94189-203">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="94189-204">Byte (niet ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-204">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="94189-205">Byte (ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-205">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="94189-206">16-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-206">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="94189-207">alias voor `[int16]`</span><span class="sxs-lookup"><span data-stu-id="94189-207">alias for `[int16]`</span></span>  | <span data-ttu-id="94189-208">16-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-208">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="94189-209">16-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-209">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="94189-210">alias voor `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="94189-210">alias for `[uint16]`</span></span> | <span data-ttu-id="94189-211">16-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-211">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="94189-212">32-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-212">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="94189-213">alias voor `[int32]`</span><span class="sxs-lookup"><span data-stu-id="94189-213">alias for `[int32]`</span></span>  | <span data-ttu-id="94189-214">32-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-214">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="94189-215">32-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-215">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="94189-216">alias voor `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="94189-216">alias for `[uint32]`</span></span> | <span data-ttu-id="94189-217">32-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-217">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="94189-218">64-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-218">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="94189-219">alias voor `[int64]`</span><span class="sxs-lookup"><span data-stu-id="94189-219">alias for `[int64]`</span></span>  | <span data-ttu-id="94189-220">64-bits geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-220">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="94189-221">64-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-221">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="94189-222">alias voor `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="94189-222">alias for `[uint64]`</span></span> | <span data-ttu-id="94189-223">64-bits geheel getal (niet-ondertekend)</span><span class="sxs-lookup"><span data-stu-id="94189-223">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="94189-224">Zie [BigInteger struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="94189-224">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="94189-225">Drijvende komma met enkele precisie</span><span class="sxs-lookup"><span data-stu-id="94189-225">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="94189-226">alias voor `[single]`</span><span class="sxs-lookup"><span data-stu-id="94189-226">alias for `[single]`</span></span> | <span data-ttu-id="94189-227">Drijvende komma met enkele precisie</span><span class="sxs-lookup"><span data-stu-id="94189-227">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="94189-228">Drijvende komma met dubbele precisie</span><span class="sxs-lookup"><span data-stu-id="94189-228">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="94189-229">128-bits drijvende komma</span><span class="sxs-lookup"><span data-stu-id="94189-229">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="94189-230">De volgende typen Accelerators zijn toegevoegd aan Power shell 6,2: `[short]` , `[ushort]` , `[uint]` , `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="94189-230">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

## <a name="examples"></a><span data-ttu-id="94189-231">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="94189-231">Examples</span></span>

<span data-ttu-id="94189-232">De volgende tabel bevat verschillende voor beelden van numerieke letterlijke waarden en een lijst met het type en de waarde:</span><span class="sxs-lookup"><span data-stu-id="94189-232">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|   <span data-ttu-id="94189-233">Getal</span><span class="sxs-lookup"><span data-stu-id="94189-233">Number</span></span>    |    <span data-ttu-id="94189-234">Type</span><span class="sxs-lookup"><span data-stu-id="94189-234">Type</span></span>    |    <span data-ttu-id="94189-235">Waarde</span><span class="sxs-lookup"><span data-stu-id="94189-235">Value</span></span>     |
| ----------: | ---------- | -----------: |
|         <span data-ttu-id="94189-236">100</span><span class="sxs-lookup"><span data-stu-id="94189-236">100</span></span> | <span data-ttu-id="94189-237">Int32</span><span class="sxs-lookup"><span data-stu-id="94189-237">Int32</span></span>      |          <span data-ttu-id="94189-238">100</span><span class="sxs-lookup"><span data-stu-id="94189-238">100</span></span> |
|        <span data-ttu-id="94189-239">100u</span><span class="sxs-lookup"><span data-stu-id="94189-239">100u</span></span> | <span data-ttu-id="94189-240">UInt32</span><span class="sxs-lookup"><span data-stu-id="94189-240">UInt32</span></span>     |          <span data-ttu-id="94189-241">100</span><span class="sxs-lookup"><span data-stu-id="94189-241">100</span></span> |
|        <span data-ttu-id="94189-242">100D</span><span class="sxs-lookup"><span data-stu-id="94189-242">100D</span></span> | <span data-ttu-id="94189-243">Decimaal</span><span class="sxs-lookup"><span data-stu-id="94189-243">Decimal</span></span>    |          <span data-ttu-id="94189-244">100</span><span class="sxs-lookup"><span data-stu-id="94189-244">100</span></span> |
|        <span data-ttu-id="94189-245">100l</span><span class="sxs-lookup"><span data-stu-id="94189-245">100l</span></span> | <span data-ttu-id="94189-246">Int64</span><span class="sxs-lookup"><span data-stu-id="94189-246">Int64</span></span>      |          <span data-ttu-id="94189-247">100</span><span class="sxs-lookup"><span data-stu-id="94189-247">100</span></span> |
|       <span data-ttu-id="94189-248">100uL</span><span class="sxs-lookup"><span data-stu-id="94189-248">100uL</span></span> | <span data-ttu-id="94189-249">UInt64</span><span class="sxs-lookup"><span data-stu-id="94189-249">UInt64</span></span>     |          <span data-ttu-id="94189-250">100</span><span class="sxs-lookup"><span data-stu-id="94189-250">100</span></span> |
|       <span data-ttu-id="94189-251">100us</span><span class="sxs-lookup"><span data-stu-id="94189-251">100us</span></span> | <span data-ttu-id="94189-252">UInt16</span><span class="sxs-lookup"><span data-stu-id="94189-252">UInt16</span></span>     |          <span data-ttu-id="94189-253">100</span><span class="sxs-lookup"><span data-stu-id="94189-253">100</span></span> |
|       <span data-ttu-id="94189-254">100uy</span><span class="sxs-lookup"><span data-stu-id="94189-254">100uy</span></span> | <span data-ttu-id="94189-255">Byte</span><span class="sxs-lookup"><span data-stu-id="94189-255">Byte</span></span>       |          <span data-ttu-id="94189-256">100</span><span class="sxs-lookup"><span data-stu-id="94189-256">100</span></span> |
|        <span data-ttu-id="94189-257">100y</span><span class="sxs-lookup"><span data-stu-id="94189-257">100y</span></span> | <span data-ttu-id="94189-258">SByte</span><span class="sxs-lookup"><span data-stu-id="94189-258">SByte</span></span>      |          <span data-ttu-id="94189-259">100</span><span class="sxs-lookup"><span data-stu-id="94189-259">100</span></span> |
|         <span data-ttu-id="94189-260">1e2</span><span class="sxs-lookup"><span data-stu-id="94189-260">1e2</span></span> | <span data-ttu-id="94189-261">Dubbel</span><span class="sxs-lookup"><span data-stu-id="94189-261">Double</span></span>     |          <span data-ttu-id="94189-262">100</span><span class="sxs-lookup"><span data-stu-id="94189-262">100</span></span> |
|        <span data-ttu-id="94189-263">1. E2</span><span class="sxs-lookup"><span data-stu-id="94189-263">1.e2</span></span> | <span data-ttu-id="94189-264">Dubbel</span><span class="sxs-lookup"><span data-stu-id="94189-264">Double</span></span>     |          <span data-ttu-id="94189-265">100</span><span class="sxs-lookup"><span data-stu-id="94189-265">100</span></span> |
|       <span data-ttu-id="94189-266">0x1e2</span><span class="sxs-lookup"><span data-stu-id="94189-266">0x1e2</span></span> | <span data-ttu-id="94189-267">Int32</span><span class="sxs-lookup"><span data-stu-id="94189-267">Int32</span></span>      |          <span data-ttu-id="94189-268">482</span><span class="sxs-lookup"><span data-stu-id="94189-268">482</span></span> |
|      <span data-ttu-id="94189-269">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="94189-269">0x1e2L</span></span> | <span data-ttu-id="94189-270">Int64</span><span class="sxs-lookup"><span data-stu-id="94189-270">Int64</span></span>      |          <span data-ttu-id="94189-271">482</span><span class="sxs-lookup"><span data-stu-id="94189-271">482</span></span> |
|      <span data-ttu-id="94189-272">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="94189-272">0x1e2D</span></span> | <span data-ttu-id="94189-273">Int32</span><span class="sxs-lookup"><span data-stu-id="94189-273">Int32</span></span>      |         <span data-ttu-id="94189-274">7725</span><span class="sxs-lookup"><span data-stu-id="94189-274">7725</span></span> |
|        <span data-ttu-id="94189-275">482D</span><span class="sxs-lookup"><span data-stu-id="94189-275">482D</span></span> | <span data-ttu-id="94189-276">Decimaal</span><span class="sxs-lookup"><span data-stu-id="94189-276">Decimal</span></span>    |          <span data-ttu-id="94189-277">482</span><span class="sxs-lookup"><span data-stu-id="94189-277">482</span></span> |
|       <span data-ttu-id="94189-278">482gb</span><span class="sxs-lookup"><span data-stu-id="94189-278">482gb</span></span> | <span data-ttu-id="94189-279">Int64</span><span class="sxs-lookup"><span data-stu-id="94189-279">Int64</span></span>      | <span data-ttu-id="94189-280">517543559168</span><span class="sxs-lookup"><span data-stu-id="94189-280">517543559168</span></span> |
|      <span data-ttu-id="94189-281">482ngb</span><span class="sxs-lookup"><span data-stu-id="94189-281">482ngb</span></span> | <span data-ttu-id="94189-282">BigInteger</span><span class="sxs-lookup"><span data-stu-id="94189-282">BigInteger</span></span> | <span data-ttu-id="94189-283">517543559168</span><span class="sxs-lookup"><span data-stu-id="94189-283">517543559168</span></span> |
|    <span data-ttu-id="94189-284">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="94189-284">0x1e2lgb</span></span> | <span data-ttu-id="94189-285">Int64</span><span class="sxs-lookup"><span data-stu-id="94189-285">Int64</span></span>      | <span data-ttu-id="94189-286">517543559168</span><span class="sxs-lookup"><span data-stu-id="94189-286">517543559168</span></span> |
|   <span data-ttu-id="94189-287">0b1011011</span><span class="sxs-lookup"><span data-stu-id="94189-287">0b1011011</span></span> | <span data-ttu-id="94189-288">Int32</span><span class="sxs-lookup"><span data-stu-id="94189-288">Int32</span></span>      |           <span data-ttu-id="94189-289">91</span><span class="sxs-lookup"><span data-stu-id="94189-289">91</span></span> |
|     <span data-ttu-id="94189-290">0xFFFFs</span><span class="sxs-lookup"><span data-stu-id="94189-290">0xFFFFs</span></span> | <span data-ttu-id="94189-291">Int16</span><span class="sxs-lookup"><span data-stu-id="94189-291">Int16</span></span>      |           <span data-ttu-id="94189-292">-1</span><span class="sxs-lookup"><span data-stu-id="94189-292">-1</span></span> |
|  <span data-ttu-id="94189-293">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="94189-293">0xFFFFFFFF</span></span> | <span data-ttu-id="94189-294">Int32</span><span class="sxs-lookup"><span data-stu-id="94189-294">Int32</span></span>      |           <span data-ttu-id="94189-295">-1</span><span class="sxs-lookup"><span data-stu-id="94189-295">-1</span></span> |
| <span data-ttu-id="94189-296">-0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="94189-296">-0xFFFFFFFF</span></span> | <span data-ttu-id="94189-297">Int32</span><span class="sxs-lookup"><span data-stu-id="94189-297">Int32</span></span>      |            <span data-ttu-id="94189-298">1</span><span class="sxs-lookup"><span data-stu-id="94189-298">1</span></span> |
| <span data-ttu-id="94189-299">0xFFFFFFFFu</span><span class="sxs-lookup"><span data-stu-id="94189-299">0xFFFFFFFFu</span></span> | <span data-ttu-id="94189-300">UInt32</span><span class="sxs-lookup"><span data-stu-id="94189-300">UInt32</span></span>     |   <span data-ttu-id="94189-301">4294967295</span><span class="sxs-lookup"><span data-stu-id="94189-301">4294967295</span></span> |

### <a name="working-with-binary-or-hexadecimal-numbers"></a><span data-ttu-id="94189-302">Werken met binaire of hexadecimale getallen</span><span class="sxs-lookup"><span data-stu-id="94189-302">Working with binary or hexadecimal numbers</span></span>

<span data-ttu-id="94189-303">Over grote binaire of hexadecimale letterlijke tekens kan worden geretourneerd `[bigint]` in plaats van het mislukken van de parser, als en alleen als het `n` achtervoegsel is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="94189-303">Overly large binary or hexadecimal literals can return as `[bigint]` rather than failing the parse, if and only if the `n` suffix is specified.</span></span> <span data-ttu-id="94189-304">Onderteken-bits worden nog steeds boven even `[decimal]` bereiken geëerbiedigd, echter:</span><span class="sxs-lookup"><span data-stu-id="94189-304">Sign bits are still respected above even `[decimal]` ranges, however:</span></span>

- <span data-ttu-id="94189-305">Als een binaire teken reeks een meervoud van 8 bits lang is, wordt de hoogste bit beschouwd als de teken-bit.</span><span class="sxs-lookup"><span data-stu-id="94189-305">If a binary string is some multiple of 8 bits long, the highest bit is treated as the sign bit.</span></span>
- <span data-ttu-id="94189-306">Als een hexadecimale teken reeks met een lengte die een meervoud van 8 is, het eerste cijfer met 8 of hoger heeft, wordt het cijfer als negatief beschouwd.</span><span class="sxs-lookup"><span data-stu-id="94189-306">If a hex string, which has a length that is a multiple of 8, has the first digit with 8 or higher, the numeral is treated as negative.</span></span>

<span data-ttu-id="94189-307">Als u een niet-ondertekend achtervoegsel opgeeft voor binaire en hexadecimale letterlijke tekens, worden teken-bits genegeerd.</span><span class="sxs-lookup"><span data-stu-id="94189-307">Specifying an unsigned suffix on binary and hex literals ignores sign bits.</span></span> <span data-ttu-id="94189-308">`0xFFFFFFFF`Retourneert bijvoorbeeld `-1` , maar `0xFFFFFFFFu` retourneert de waarde `[uint]::MaxValue` van 4294967295.</span><span class="sxs-lookup"><span data-stu-id="94189-308">For example, `0xFFFFFFFF` returns `-1`, but `0xFFFFFFFFu` returns the `[uint]::MaxValue` of 4294967295.</span></span>

<span data-ttu-id="94189-309">In Power shell 7,1 retourneert het gebruik van een type achtervoegsel voor een hex literal nu een ondertekende waarde van dat type.</span><span class="sxs-lookup"><span data-stu-id="94189-309">In PowerShell 7.1, using a type suffix on a hex literal now returns a signed value of that type.</span></span> <span data-ttu-id="94189-310">In Power shell 7,0 retourneert de expressie bijvoorbeeld `0xFFFFs` een fout omdat de positieve waarde te groot is voor een `[int16]` type.</span><span class="sxs-lookup"><span data-stu-id="94189-310">For example, in PowerShell 7.0 the expression `0xFFFFs` returns an error because the positive value is too large for an `[int16]` type.</span></span>
<span data-ttu-id="94189-311">Power shell 7,1 interpreteert dit als `-1` een `[int16]` type.</span><span class="sxs-lookup"><span data-stu-id="94189-311">PowerShell 7.1 interprets this as `-1` that is an `[int16]` type.</span></span>

<span data-ttu-id="94189-312">Voor het voor voegsel van de letterlijke waarde met a `0` wordt deze omzeild en beschouwd als niet-ondertekend.</span><span class="sxs-lookup"><span data-stu-id="94189-312">Prefixing the literal with a `0` will bypass this and be treated as unsigned.</span></span>
<span data-ttu-id="94189-313">Bijvoorbeeld: `0b011111111`.</span><span class="sxs-lookup"><span data-stu-id="94189-313">For example: `0b011111111`.</span></span> <span data-ttu-id="94189-314">Dit kan nodig zijn bij het werken met letterlijke waarden in het `[bigint]` bereik, omdat de `u` `n` achtervoegsels niet kunnen worden gecombineerd.</span><span class="sxs-lookup"><span data-stu-id="94189-314">This can be necessary when working with literals in the `[bigint]` range, as the `u` and `n` suffixes cannot be combined.</span></span>

<span data-ttu-id="94189-315">U kunt ook binaire en hexadecimale letterlijke waarden negeren met het `-` voor voegsel.</span><span class="sxs-lookup"><span data-stu-id="94189-315">You can also negate binary and hex literals using the `-` prefix.</span></span> <span data-ttu-id="94189-316">Dit kan resulteren in een positief getal sinds de aanmeldings-bits zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="94189-316">This can result in a positive number since sign bits are permitted.</span></span>

<span data-ttu-id="94189-317">Onderteken bits worden geaccepteerd voor BigInteger cijfers:</span><span class="sxs-lookup"><span data-stu-id="94189-317">Sign bits are accepted for BigInteger-suffixed numerals:</span></span>

- <span data-ttu-id="94189-318">Met BigInteger-achtervoegseld hex wordt de grote bit van elke letterlijke waarde met een lengte van meer dan acht tekens beschouwd als de teken-bit.</span><span class="sxs-lookup"><span data-stu-id="94189-318">BigInteger-suffixed hex treats the high bit of any literal with a length multiple of 8 characters as the sign bit.</span></span> <span data-ttu-id="94189-319">De lengte bevat niet het `0x` voor voegsel of achtervoegsels.</span><span class="sxs-lookup"><span data-stu-id="94189-319">The length does not include the `0x` prefix or any suffixes.</span></span>
- <span data-ttu-id="94189-320">BigInteger-achtervoegsels accepteren binaire aanmeldingen op 96 en 128 tekens, en om de 8 tekens na.</span><span class="sxs-lookup"><span data-stu-id="94189-320">BigInteger-suffixed binary accepts sign bits at 96 and 128 characters, and at every 8 characters after.</span></span>

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="94189-321">Opdrachten die eruitzien als numerieke letterlijke waarden</span><span class="sxs-lookup"><span data-stu-id="94189-321">Commands that look like numeric literals</span></span>

<span data-ttu-id="94189-322">Elke opdracht die eruitziet als een geldige numerieke literal moet worden uitgevoerd met de aanroep operator ( `&` ), anders wordt deze geïnterpreteerd als een getal.</span><span class="sxs-lookup"><span data-stu-id="94189-322">Any command that looks like a valid numeric literal must be executed using the call operator (`&`), otherwise it is interpreted as a number.</span></span> <span data-ttu-id="94189-323">Onjuist gevormde letterlijke waarden met een geldige syntaxis als `1usgb` resultaat hebben de volgende fout:</span><span class="sxs-lookup"><span data-stu-id="94189-323">Malformed literals with valid syntax like `1usgb` will result in the following error:</span></span>

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

<span data-ttu-id="94189-324">Onjuist ingedeelde letterlijke tekens met een ongeldige syntaxis zoals `1gbus` wordt geïnterpreteerd als een standaard bare teken reeks en kan worden geïnterpreteerd als een geldige opdracht naam in contexten waar opdrachten kunnen worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="94189-324">However, malformed literals with invalid syntax like `1gbus` will be interpreted as a standard bare string, and can be interpreted as a valid command name in contexts where commands may be called.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="94189-325">Toegang tot eigenschappen en methoden van numerieke objecten</span><span class="sxs-lookup"><span data-stu-id="94189-325">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="94189-326">Om toegang te krijgen tot een lid van een numerieke letterlijke waarde, zijn er situaties waarin u de letterlijke teken reeks tussen haakjes moet plaatsen.</span><span class="sxs-lookup"><span data-stu-id="94189-326">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="94189-327">De letterlijke waarde heeft geen decimaal teken</span><span class="sxs-lookup"><span data-stu-id="94189-327">The literal does not have a decimal point</span></span>
- <span data-ttu-id="94189-328">De letterlijke waarde heeft geen cijfers na het decimaal teken</span><span class="sxs-lookup"><span data-stu-id="94189-328">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="94189-329">De letterlijke waarde heeft geen achtervoegsel</span><span class="sxs-lookup"><span data-stu-id="94189-329">The literal does not have a suffix</span></span>

<span data-ttu-id="94189-330">Het volgende voor beeld mislukt bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="94189-330">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="94189-331">De volgende voor beelden werken:</span><span class="sxs-lookup"><span data-stu-id="94189-331">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="94189-332">De eerste twee voor beelden werken zonder tussen haakjes, omdat de Power shell-parser kan bepalen waar de numerieke letterlijke waarde eindigt en de **gettype** -methode wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="94189-332">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

## <a name="how-powershell-parses-numeric-literals"></a><span data-ttu-id="94189-333">Hoe in Power shell numerieke letterlijke waarden worden geparseerd</span><span class="sxs-lookup"><span data-stu-id="94189-333">How PowerShell parses numeric literals</span></span>

<span data-ttu-id="94189-334">Power shell v 7.0 heeft de manier gewijzigd waarop numerieke letterlijke waarden worden geparseerd om de nieuwe functies in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="94189-334">PowerShell v7.0 changed the way numeric literals are parsed to enable the new features.</span></span>

### <a name="parsing-real-numeric-literals"></a><span data-ttu-id="94189-335">Werkelijke numerieke letterlijke waarden parseren</span><span class="sxs-lookup"><span data-stu-id="94189-335">Parsing real numeric literals</span></span>

<span data-ttu-id="94189-336">Als de letterlijke waarde een decimaal teken of de e-notatie bevat, wordt de letterlijke teken reeks geparseerd als een reëel getal.</span><span class="sxs-lookup"><span data-stu-id="94189-336">If the literal contains a decimal point or the e-notation, the literal string is parsed a real number.</span></span>

- <span data-ttu-id="94189-337">Als het decimale achtervoegsel direct in wordt weer gegeven `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="94189-337">If the decimal-suffix is present then directly into `[decimal]`.</span></span>
- <span data-ttu-id="94189-338">Else, parse as `[Double]` en apply vermenigvuldigen met de waarde.</span><span class="sxs-lookup"><span data-stu-id="94189-338">Else, parse as `[Double]` and apply multiplier to the value.</span></span> <span data-ttu-id="94189-339">Controleer vervolgens het type achtervoegsels en probeer het naar het juiste type te casten.</span><span class="sxs-lookup"><span data-stu-id="94189-339">Then check the type suffixes and attempt to cast into appropriate type.</span></span>
- <span data-ttu-id="94189-340">Als de teken reeks geen type achtervoegsel heeft, vervolgens parseren als `[Double]` .</span><span class="sxs-lookup"><span data-stu-id="94189-340">If the string has no type suffix, then parse as `[Double]`.</span></span>

### <a name="paring-integer-numeric-literals"></a><span data-ttu-id="94189-341">Numerieke letterlijke waarden voor paring geheel getal</span><span class="sxs-lookup"><span data-stu-id="94189-341">Paring integer numeric literals</span></span>

<span data-ttu-id="94189-342">Letterlijke waarden van het type integer worden geparseerd met behulp van de volgende stappen:</span><span class="sxs-lookup"><span data-stu-id="94189-342">Integer type literals are parsed using the following steps:</span></span>

1. <span data-ttu-id="94189-343">De indeling van het grondtal bepalen</span><span class="sxs-lookup"><span data-stu-id="94189-343">Determine the radix format</span></span>
   - <span data-ttu-id="94189-344">Voor binaire indelingen parseren naar `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="94189-344">For binary formats, parse into `[BigInteger]`.</span></span>
   - <span data-ttu-id="94189-345">Voor hexadecimale notaties Parset u in `[BigInteger]` met behulp van speciale casies om oorspronkelijke gedragingen te behouden wanneer de waarde in de `[int]` of het bereik ligt `[long]` .</span><span class="sxs-lookup"><span data-stu-id="94189-345">For hexidecimal formats, parse into `[BigInteger]` using special casies to retain original behaviours when the value is in the `[int]` or `[long]` range.</span></span>
   - <span data-ttu-id="94189-346">Als binair noch hex, worden geparseerd als een `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="94189-346">If neither binary nor hex, parse normally as a `[BigInteger]`.</span></span>
2. <span data-ttu-id="94189-347">Pas de vermenigvuldiger waarde toe voordat u een casts probeert te maken om ervoor te zorgen dat type bindingen op de juiste wijze kunnen worden gecontroleerd zonder overloop.</span><span class="sxs-lookup"><span data-stu-id="94189-347">Apply the multiplier value before attempting any casts to ensure type bounds can be appropriately checked without overflows.</span></span>
3. <span data-ttu-id="94189-348">Controleer type achtervoegsels.</span><span class="sxs-lookup"><span data-stu-id="94189-348">Check type suffixes.</span></span>
   - <span data-ttu-id="94189-349">Controleer type grenzen en probeer te parseren naar dat type.</span><span class="sxs-lookup"><span data-stu-id="94189-349">Check type bounds and attempt to parse into that type.</span></span>
   - <span data-ttu-id="94189-350">Als er geen achtervoegsel wordt gebruikt, wordt de waarde ingesteld op grenzen-ingeschakeld in de volgende volg orde, wat resulteert in de eerste geslaagde test die het type van het getal bepaalt.</span><span class="sxs-lookup"><span data-stu-id="94189-350">If no suffix is used, then the value is bounds-checked in the following order, resulting in the first successful test determining the type of the number.</span></span>
     - `[int]`
     - `[long]`
     - <span data-ttu-id="94189-351">`[decimal]` (alleen base-10 letterlijke waarden)</span><span class="sxs-lookup"><span data-stu-id="94189-351">`[decimal]` (base-10 literals only)</span></span>
     - <span data-ttu-id="94189-352">`[double]` (alleen base-10 letterlijke waarden)</span><span class="sxs-lookup"><span data-stu-id="94189-352">`[double]` (base-10 literals only)</span></span>
   - <span data-ttu-id="94189-353">Als de waarde buiten het `[long]` bereik van hexadecimale en binaire getallen ligt, mislukt de parsering.</span><span class="sxs-lookup"><span data-stu-id="94189-353">If the value is outside the `[long]` range for hex and binary numbers, the parse fails.</span></span>
   - <span data-ttu-id="94189-354">Als de waarde buiten het `[double]` bereik van het grondtal 10 nummer valt, mislukt de parsering.</span><span class="sxs-lookup"><span data-stu-id="94189-354">If the value is outside the `[double]` range for base 10 number, the parse fails.</span></span>
   - <span data-ttu-id="94189-355">Hogere waarden moeten expliciet worden geschreven met behulp van het `n` achtervoegsel voor het parseren van de letterlijke waarde als een `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="94189-355">Higher values must be explicitly written using the `n` suffix to parse the literal as a `BigInteger`.</span></span>

### <a name="parsing-large-value-literals"></a><span data-ttu-id="94189-356">Letterlijke waarden voor grote waarden parseren</span><span class="sxs-lookup"><span data-stu-id="94189-356">Parsing large value literals</span></span>

<span data-ttu-id="94189-357">Voorheen werden hogere integerwaarden geparseerd als dubbele waarden voordat ze naar een ander type worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="94189-357">Previously, higher integer values were parsed as double before being cast to any other type.</span></span> <span data-ttu-id="94189-358">Dit resulteert in een verlies van nauw keurigheid in de hogere bereiken.</span><span class="sxs-lookup"><span data-stu-id="94189-358">This results in a loss of precision in the higher ranges.</span></span> <span data-ttu-id="94189-359">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="94189-359">For example:</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="94189-360">U kunt dit probleem voor komen door waarden te schrijven als teken reeksen en ze vervolgens te converteren:</span><span class="sxs-lookup"><span data-stu-id="94189-360">To avoid this problem you had to write values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="94189-361">In Power shell 7,0 moet u het `N` achtervoegsel gebruiken.</span><span class="sxs-lookup"><span data-stu-id="94189-361">In PowerShell 7.0 you must use the `N` suffix.</span></span>

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="94189-362">Ook waarden tussen `[ulong]::MaxValue` en `[decimal]::MaxValue` moeten worden aangegeven met het decimale achtervoegsel `D` om nauw keurigheid te behouden.</span><span class="sxs-lookup"><span data-stu-id="94189-362">Also values between `[ulong]::MaxValue` and `[decimal]::MaxValue` should be denoted using the decimal-suffix `D` to maintain accuracy.</span></span> <span data-ttu-id="94189-363">Zonder achtervoegsel worden deze waarden geparseerd als `[Double]` het gebruik van de modus voor real-parseren.</span><span class="sxs-lookup"><span data-stu-id="94189-363">Without the suffix, these values are parsed as `[Double]` using the real-parsing mode.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger?view=netcore-2.2
