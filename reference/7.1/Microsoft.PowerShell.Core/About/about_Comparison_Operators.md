---
description: Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: ea48d5928f71983f6d035f0e5e6074ce36754d80
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090508"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="12430-103">Over vergelijkings operatoren</span><span class="sxs-lookup"><span data-stu-id="12430-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="12430-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="12430-104">Short description</span></span>
<span data-ttu-id="12430-105">Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="12430-105">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="12430-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="12430-106">Long description</span></span>

<span data-ttu-id="12430-107">Met vergelijkings operatoren kunt u voor waarden opgeven voor het vergelijken van waarden en waarden zoeken die overeenkomen met opgegeven patronen.</span><span class="sxs-lookup"><span data-stu-id="12430-107">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="12430-108">Als u een vergelijkings operator wilt gebruiken, geeft u de waarden op die u wilt vergelijken samen met een operator die deze waarden scheidt.</span><span class="sxs-lookup"><span data-stu-id="12430-108">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="12430-109">Power shell bevat de volgende vergelijkings operatoren:</span><span class="sxs-lookup"><span data-stu-id="12430-109">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="12430-110">Type</span><span class="sxs-lookup"><span data-stu-id="12430-110">Type</span></span>        | <span data-ttu-id="12430-111">Operators</span><span class="sxs-lookup"><span data-stu-id="12430-111">Operators</span></span>    | <span data-ttu-id="12430-112">Description</span><span class="sxs-lookup"><span data-stu-id="12430-112">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="12430-113">Gelijkheid</span><span class="sxs-lookup"><span data-stu-id="12430-113">Equality</span></span>    | <span data-ttu-id="12430-114">-eq</span><span class="sxs-lookup"><span data-stu-id="12430-114">-eq</span></span>          | <span data-ttu-id="12430-115">is gelijk aan</span><span class="sxs-lookup"><span data-stu-id="12430-115">equals</span></span>                                      |
|             | <span data-ttu-id="12430-116">-ne</span><span class="sxs-lookup"><span data-stu-id="12430-116">-ne</span></span>          | <span data-ttu-id="12430-117">niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="12430-117">not equals</span></span>                                  |
|             | <span data-ttu-id="12430-118">-gt</span><span class="sxs-lookup"><span data-stu-id="12430-118">-gt</span></span>          | <span data-ttu-id="12430-119">groter dan</span><span class="sxs-lookup"><span data-stu-id="12430-119">greater than</span></span>                                |
|             | <span data-ttu-id="12430-120">-ge</span><span class="sxs-lookup"><span data-stu-id="12430-120">-ge</span></span>          | <span data-ttu-id="12430-121">groter dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="12430-121">greater than or equal</span></span>                       |
|             | <span data-ttu-id="12430-122">-lt</span><span class="sxs-lookup"><span data-stu-id="12430-122">-lt</span></span>          | <span data-ttu-id="12430-123">kleiner dan</span><span class="sxs-lookup"><span data-stu-id="12430-123">less than</span></span>                                   |
|             | <span data-ttu-id="12430-124">-Le</span><span class="sxs-lookup"><span data-stu-id="12430-124">-le</span></span>          | <span data-ttu-id="12430-125">kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="12430-125">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="12430-126">Matching</span><span class="sxs-lookup"><span data-stu-id="12430-126">Matching</span></span>    | <span data-ttu-id="12430-127">-like</span><span class="sxs-lookup"><span data-stu-id="12430-127">-like</span></span>        | <span data-ttu-id="12430-128">Retourneert waar als teken reeks overeenkomt met Joker teken</span><span class="sxs-lookup"><span data-stu-id="12430-128">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="12430-129">pattern</span><span class="sxs-lookup"><span data-stu-id="12430-129">pattern</span></span>                                     |
|             | <span data-ttu-id="12430-130">-notlike</span><span class="sxs-lookup"><span data-stu-id="12430-130">-notlike</span></span>     | <span data-ttu-id="12430-131">Retourneert waar als de teken reeks niet overeenkomt</span><span class="sxs-lookup"><span data-stu-id="12430-131">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="12430-132">Joker teken patroon</span><span class="sxs-lookup"><span data-stu-id="12430-132">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="12430-133">-match</span><span class="sxs-lookup"><span data-stu-id="12430-133">-match</span></span>       | <span data-ttu-id="12430-134">Retourneert True als teken reeks overeenkomt met regex</span><span class="sxs-lookup"><span data-stu-id="12430-134">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="12430-135">pattern $matches bevat overeenkomende teken reeksen</span><span class="sxs-lookup"><span data-stu-id="12430-135">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="12430-136">-notmatch</span><span class="sxs-lookup"><span data-stu-id="12430-136">-notmatch</span></span>    | <span data-ttu-id="12430-137">Retourneert waar als de teken reeks niet overeenkomt</span><span class="sxs-lookup"><span data-stu-id="12430-137">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="12430-138">regex-patroon; $matches bevat overeenkomende</span><span class="sxs-lookup"><span data-stu-id="12430-138">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="12430-139">tekenreeksen</span><span class="sxs-lookup"><span data-stu-id="12430-139">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="12430-140">Containment</span><span class="sxs-lookup"><span data-stu-id="12430-140">Containment</span></span> | <span data-ttu-id="12430-141">-contains</span><span class="sxs-lookup"><span data-stu-id="12430-141">-contains</span></span>    | <span data-ttu-id="12430-142">Retourneert waar als de referentie waarde bevat</span><span class="sxs-lookup"><span data-stu-id="12430-142">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="12430-143">in een verzameling</span><span class="sxs-lookup"><span data-stu-id="12430-143">in a collection</span></span>                             |
|             | <span data-ttu-id="12430-144">-notcontains</span><span class="sxs-lookup"><span data-stu-id="12430-144">-notcontains</span></span> | <span data-ttu-id="12430-145">Retourneert waar als de referentie waarde niet</span><span class="sxs-lookup"><span data-stu-id="12430-145">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="12430-146">opgenomen in een verzameling</span><span class="sxs-lookup"><span data-stu-id="12430-146">contained in a collection</span></span>                   |
|             | <span data-ttu-id="12430-147">-in</span><span class="sxs-lookup"><span data-stu-id="12430-147">-in</span></span>          | <span data-ttu-id="12430-148">Retourneert waar als de test waarde in een</span><span class="sxs-lookup"><span data-stu-id="12430-148">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="12430-149">verzameling</span><span class="sxs-lookup"><span data-stu-id="12430-149">collection</span></span>                                  |
|             | <span data-ttu-id="12430-150">-notin</span><span class="sxs-lookup"><span data-stu-id="12430-150">-notin</span></span>       | <span data-ttu-id="12430-151">Retourneert waar als de test waarde niet bevat</span><span class="sxs-lookup"><span data-stu-id="12430-151">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="12430-152">in een verzameling</span><span class="sxs-lookup"><span data-stu-id="12430-152">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="12430-153">Vervanging</span><span class="sxs-lookup"><span data-stu-id="12430-153">Replacement</span></span> | <span data-ttu-id="12430-154">-vervangen</span><span class="sxs-lookup"><span data-stu-id="12430-154">-replace</span></span>     | <span data-ttu-id="12430-155">Vervangt een teken reeks patroon</span><span class="sxs-lookup"><span data-stu-id="12430-155">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="12430-156">Type</span><span class="sxs-lookup"><span data-stu-id="12430-156">Type</span></span>        | <span data-ttu-id="12430-157">-is</span><span class="sxs-lookup"><span data-stu-id="12430-157">-is</span></span>          | <span data-ttu-id="12430-158">Retourneert waar als beide objecten hetzelfde zijn</span><span class="sxs-lookup"><span data-stu-id="12430-158">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="12430-159">type</span><span class="sxs-lookup"><span data-stu-id="12430-159">type</span></span>                                        |
|             | <span data-ttu-id="12430-160">-isnot</span><span class="sxs-lookup"><span data-stu-id="12430-160">-isnot</span></span>       | <span data-ttu-id="12430-161">Retourneert waar als de objecten niet hetzelfde zijn</span><span class="sxs-lookup"><span data-stu-id="12430-161">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="12430-162">type</span><span class="sxs-lookup"><span data-stu-id="12430-162">type</span></span>                                        |

<span data-ttu-id="12430-163">Standaard zijn alle vergelijkings operatoren niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="12430-163">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="12430-164">Als u een vergelijkings operator hoofdletter gevoelig wilt maken, moet u de naam van de operator vooraf vervangen door een `c` .</span><span class="sxs-lookup"><span data-stu-id="12430-164">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="12430-165">De hoofdletter gevoelige versie van `-eq` is bijvoorbeeld `-ceq` .</span><span class="sxs-lookup"><span data-stu-id="12430-165">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="12430-166">Als u de niet-hoofdletter gevoeligheid expliciet wilt maken, moet u voorafgaand aan de operator een `i` .</span><span class="sxs-lookup"><span data-stu-id="12430-166">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="12430-167">De versie van is bijvoorbeeld expliciet niet hoofdletter gevoelig `-eq` `-ieq` .</span><span class="sxs-lookup"><span data-stu-id="12430-167">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="12430-168">Wanneer de invoer voor een operator een scalaire waarde is, retour neren vergelijkings operatoren een Booleaanse waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-168">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="12430-169">Wanneer de invoer een verzameling waarden is, retour neren de vergelijkings operatoren alle overeenkomende waarden.</span><span class="sxs-lookup"><span data-stu-id="12430-169">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="12430-170">Als er geen overeenkomsten in een verzameling zijn, retour neren vergelijkings operatoren een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="12430-170">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="12430-171">De uitzonde ringen zijn de containment-Opera Tors, de Opera tors in en de type operator, die altijd een **Booleaanse** waarde Retour neren.</span><span class="sxs-lookup"><span data-stu-id="12430-171">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="12430-172">Als u een waarde wilt vergelijken `$null` , moet u aan `$null` de linkerkant van de vergelijking zetten.</span><span class="sxs-lookup"><span data-stu-id="12430-172">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="12430-173">Wanneer u vergelijkt `$null` met een **object []** , is het resultaat **False** omdat het vergelijkings object een matrix is.</span><span class="sxs-lookup"><span data-stu-id="12430-173">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="12430-174">Wanneer u een matrix vergelijkt met `$null` , worden de `$null` waarden die in de matrix zijn opgeslagen, door de vergelijking gefilterd.</span><span class="sxs-lookup"><span data-stu-id="12430-174">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="12430-175">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-175">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a><span data-ttu-id="12430-176">Gelijkheidsoperatoren</span><span class="sxs-lookup"><span data-stu-id="12430-176">Equality operators</span></span>

<span data-ttu-id="12430-177">De gelijkheids operatoren ( `-eq` , `-ne` ) retour neren de waarde True of de overeenkomsten wanneer een of meer invoer waarden identiek zijn aan het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="12430-177">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="12430-178">Het hele patroon moet overeenkomen met een volledige waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-178">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="12430-179">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-179">Example:</span></span>

### <a name="-eq"></a><span data-ttu-id="12430-180">-eq</span><span class="sxs-lookup"><span data-stu-id="12430-180">-eq</span></span>

<span data-ttu-id="12430-181">Beschrijving: gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="12430-181">Description: Equal to.</span></span> <span data-ttu-id="12430-182">Bevat een identieke waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-182">Includes an identical value.</span></span>

<span data-ttu-id="12430-183">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-183">Example:</span></span>

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

### <a name="-ne"></a><span data-ttu-id="12430-184">-ne</span><span class="sxs-lookup"><span data-stu-id="12430-184">-ne</span></span>

<span data-ttu-id="12430-185">Beschrijving: niet gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="12430-185">Description: Not equal to.</span></span> <span data-ttu-id="12430-186">Bevat een andere waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-186">Includes a different value.</span></span>

<span data-ttu-id="12430-187">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-187">Example:</span></span>

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

### <a name="-gt"></a><span data-ttu-id="12430-188">-gt</span><span class="sxs-lookup"><span data-stu-id="12430-188">-gt</span></span>

<span data-ttu-id="12430-189">Beschrijving: groter dan.</span><span class="sxs-lookup"><span data-stu-id="12430-189">Description: Greater-than.</span></span>

<span data-ttu-id="12430-190">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-190">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="12430-191">Dit mag niet worden verward met `>` , de operator groter dan in veel andere programmeer talen.</span><span class="sxs-lookup"><span data-stu-id="12430-191">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="12430-192">In Power shell `>` wordt gebruikt voor omleiding.</span><span class="sxs-lookup"><span data-stu-id="12430-192">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="12430-193">Zie [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12430-193">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

### <a name="-ge"></a><span data-ttu-id="12430-194">-ge</span><span class="sxs-lookup"><span data-stu-id="12430-194">-ge</span></span>

<span data-ttu-id="12430-195">Beschrijving: groter dan of gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="12430-195">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="12430-196">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-196">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a><span data-ttu-id="12430-197">-lt</span><span class="sxs-lookup"><span data-stu-id="12430-197">-lt</span></span>

<span data-ttu-id="12430-198">Beschrijving: kleiner dan.</span><span class="sxs-lookup"><span data-stu-id="12430-198">Description: Less-than.</span></span>

<span data-ttu-id="12430-199">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-199">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a><span data-ttu-id="12430-200">-Le</span><span class="sxs-lookup"><span data-stu-id="12430-200">-le</span></span>

<span data-ttu-id="12430-201">Beschrijving: kleiner dan of gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="12430-201">Description: Less-than or equal to.</span></span>

<span data-ttu-id="12430-202">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-202">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a><span data-ttu-id="12430-203">Overeenkomende Opera tors</span><span class="sxs-lookup"><span data-stu-id="12430-203">Matching operators</span></span>

<span data-ttu-id="12430-204">De like-Opera tors ( `-like` en `-notlike` ) vinden elementen die overeenkomen met of die niet overeenkomen met een opgegeven patroon met Joker teken expressies.</span><span class="sxs-lookup"><span data-stu-id="12430-204">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="12430-205">De syntaxis is:</span><span class="sxs-lookup"><span data-stu-id="12430-205">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="12430-206">De overeenkomende Opera tors ( `-match` en `-notmatch` ) vinden elementen die overeenkomen met of die niet overeenkomen met een opgegeven patroon met reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="12430-206">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="12430-207">De operators matchen vullen de `$Matches` Automatische variabele in wanneer de invoer (het argument aan de linkerkant) naar de operator is één scalair object.</span><span class="sxs-lookup"><span data-stu-id="12430-207">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="12430-208">Wanneer de invoer scalair is, `-match` `-notmatch` retour neren de Opera tors en wordt de waarde van de `$Matches` Automatische variabele ingesteld op de overeenkomende onderdelen van het argument.</span><span class="sxs-lookup"><span data-stu-id="12430-208">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="12430-209">De syntaxis is:</span><span class="sxs-lookup"><span data-stu-id="12430-209">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a><span data-ttu-id="12430-210">-like</span><span class="sxs-lookup"><span data-stu-id="12430-210">-like</span></span>

<span data-ttu-id="12430-211">Beschrijving: komt overeen met het Joker teken ( \* ).</span><span class="sxs-lookup"><span data-stu-id="12430-211">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="12430-212">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-212">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a><span data-ttu-id="12430-213">-notlike</span><span class="sxs-lookup"><span data-stu-id="12430-213">-notlike</span></span>

<span data-ttu-id="12430-214">Beschrijving: komt niet overeen met het Joker teken ( \* ).</span><span class="sxs-lookup"><span data-stu-id="12430-214">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="12430-215">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-215">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="12430-216">-match</span><span class="sxs-lookup"><span data-stu-id="12430-216">-match</span></span>

<span data-ttu-id="12430-217">Beschrijving: komt overeen met een teken reeks met reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="12430-217">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="12430-218">Wanneer de invoer scalair is, wordt de `$Matches` Automatische variabele gevuld.</span><span class="sxs-lookup"><span data-stu-id="12430-218">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="12430-219">Als de invoer een verzameling is, `-match` `-notmatch` retour neren de Opera tors en de overeenkomende leden van die verzameling, maar de operator vult de `$Matches` variabele niet in.</span><span class="sxs-lookup"><span data-stu-id="12430-219">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="12430-220">Met de volgende opdracht wordt bijvoorbeeld een verzameling teken reeksen naar de operator verzonden `-match` .</span><span class="sxs-lookup"><span data-stu-id="12430-220">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="12430-221">De `-match` operator retourneert de items in de verzameling die overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="12430-221">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="12430-222">De automatische variabele wordt niet gevuld `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="12430-222">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="12430-223">Met de volgende opdracht wordt daarentegen één teken reeks naar de `-match` operator verzonden.</span><span class="sxs-lookup"><span data-stu-id="12430-223">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="12430-224">De `-match` operator retourneert een Booleaanse waarde en vult de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="12430-224">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="12430-225">De `$Matches` Automatische variabele is een **hashtabel**.</span><span class="sxs-lookup"><span data-stu-id="12430-225">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="12430-226">Als er geen groepering of opname wordt gebruikt, wordt er slechts één sleutel ingevuld.</span><span class="sxs-lookup"><span data-stu-id="12430-226">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="12430-227">De `0` sleutel vertegenwoordigt alle tekst die overeenkomt.</span><span class="sxs-lookup"><span data-stu-id="12430-227">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="12430-228">Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie over het groeperen en vastleggen met behulp van reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="12430-228">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="12430-229">Het is belang rijk te weten dat de `$Matches` hashtabel alleen het eerste exemplaar van een overeenkomend patroon moet bevatten.</span><span class="sxs-lookup"><span data-stu-id="12430-229">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="12430-230">De `0` sleutel is een **geheel getal**.</span><span class="sxs-lookup"><span data-stu-id="12430-230">The `0` key is an **Integer**.</span></span> <span data-ttu-id="12430-231">U kunt elke **hash** -methode gebruiken om toegang te krijgen tot de opgeslagen waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-231">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```powershell
> PS> "Good Dog" -match "Dog"
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

<span data-ttu-id="12430-232">De `-notmatch` operator vult de `$Matches` Automatische variabele in wanneer de invoer scalair is en het resultaat ONWAAR is, wanneer er een overeenkomst wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="12430-232">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

### <a name="-notmatch"></a><span data-ttu-id="12430-233">-notmatch</span><span class="sxs-lookup"><span data-stu-id="12430-233">-notmatch</span></span>

<span data-ttu-id="12430-234">Beschrijving: komt niet overeen met een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="12430-234">Description: Does not match a string.</span></span> <span data-ttu-id="12430-235">Maakt gebruik van reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="12430-235">Uses regular expressions.</span></span> <span data-ttu-id="12430-236">Wanneer de invoer scalair is, wordt de `$Matches` Automatische variabele gevuld.</span><span class="sxs-lookup"><span data-stu-id="12430-236">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="12430-237">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-237">Example:</span></span>

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

## <a name="containment-operators"></a><span data-ttu-id="12430-238">Containment-Opera tors</span><span class="sxs-lookup"><span data-stu-id="12430-238">Containment operators</span></span>

<span data-ttu-id="12430-239">De containment-Opera tors ( `-contains` en `-notcontains` ) zijn vergelijkbaar met de gelijkheids operatoren.</span><span class="sxs-lookup"><span data-stu-id="12430-239">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="12430-240">De containment-Opera tors retour neren echter altijd een Booleaanse waarde, zelfs wanneer de invoer een verzameling is.</span><span class="sxs-lookup"><span data-stu-id="12430-240">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="12430-241">Ook, in tegens telling tot de gelijkheids operatoren, retour neren de container-Opera tors een waarde zodra ze de eerste overeenkomst detecteren.</span><span class="sxs-lookup"><span data-stu-id="12430-241">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="12430-242">De gelijkheids operatoren evalueren alle invoer en retour neren vervolgens alle overeenkomende items in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="12430-242">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

### <a name="-contains"></a><span data-ttu-id="12430-243">-contains</span><span class="sxs-lookup"><span data-stu-id="12430-243">-contains</span></span>

<span data-ttu-id="12430-244">Beschrijving: containment-operator.</span><span class="sxs-lookup"><span data-stu-id="12430-244">Description: Containment operator.</span></span> <span data-ttu-id="12430-245">Hiermee wordt aangegeven of een verzameling verwijzings waarden één test waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="12430-245">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="12430-246">Retourneert altijd een Boole-waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-246">Always returns a Boolean value.</span></span> <span data-ttu-id="12430-247">Retourneert alleen waar als de test waarde exact overeenkomt met ten minste een van de referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="12430-247">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="12430-248">Wanneer de test waarde een verzameling is, gebruikt de contains-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="12430-248">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="12430-249">Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.</span><span class="sxs-lookup"><span data-stu-id="12430-249">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="12430-250">In een zeer grote verzameling retourneert de `-contains` operator resultaten sneller dan de operator equal to.</span><span class="sxs-lookup"><span data-stu-id="12430-250">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="12430-251">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="12430-251">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="12430-252">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="12430-252">Examples:</span></span>

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

### <a name="-notcontains"></a><span data-ttu-id="12430-253">-notcontains</span><span class="sxs-lookup"><span data-stu-id="12430-253">-notcontains</span></span>

<span data-ttu-id="12430-254">Beschrijving: containment-operator.</span><span class="sxs-lookup"><span data-stu-id="12430-254">Description: Containment operator.</span></span> <span data-ttu-id="12430-255">Hiermee wordt aangegeven of een verzameling verwijzings waarden één test waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="12430-255">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="12430-256">Retourneert altijd een Boole-waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-256">Always returns a Boolean value.</span></span> <span data-ttu-id="12430-257">Retourneert waar als de test waarde geen exacte overeenkomsten voor ten minste een van de verwijzings waarden is.</span><span class="sxs-lookup"><span data-stu-id="12430-257">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="12430-258">Wanneer de test waarde een verzameling is, gebruikt de NotContains-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="12430-258">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="12430-259">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="12430-259">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="12430-260">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="12430-260">Examples:</span></span>

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

### <a name="-in"></a><span data-ttu-id="12430-261">-in</span><span class="sxs-lookup"><span data-stu-id="12430-261">-in</span></span>

<span data-ttu-id="12430-262">Beschrijving: in operator.</span><span class="sxs-lookup"><span data-stu-id="12430-262">Description: In operator.</span></span> <span data-ttu-id="12430-263">Hiermee wordt aangegeven of een test waarde wordt weer gegeven in een verzameling referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="12430-263">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="12430-264">Altijd retour neren als Booleaanse waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-264">Always return as Boolean value.</span></span> <span data-ttu-id="12430-265">Retourneert alleen waar als de test waarde exact overeenkomt met ten minste een van de referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="12430-265">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="12430-266">Wanneer de test waarde een verzameling is, gebruikt de in-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="12430-266">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="12430-267">Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.</span><span class="sxs-lookup"><span data-stu-id="12430-267">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="12430-268">De `-in` operator is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12430-268">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="12430-269">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="12430-269">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="12430-270">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="12430-270">Examples:</span></span>

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

### <a name="-notin"></a><span data-ttu-id="12430-271">-notin</span><span class="sxs-lookup"><span data-stu-id="12430-271">-notin</span></span>

<span data-ttu-id="12430-272">Beschrijving: Hiermee wordt aangegeven of een test waarde wordt weer gegeven in een verzameling referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="12430-272">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="12430-273">Retourneert altijd een Boole-waarde.</span><span class="sxs-lookup"><span data-stu-id="12430-273">Always returns a Boolean value.</span></span> <span data-ttu-id="12430-274">Retourneert waar als de test waarde niet exact overeenkomt voor ten minste een van de referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="12430-274">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="12430-275">Wanneer de test waarde een verzameling is, gebruikt de in-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="12430-275">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="12430-276">Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.</span><span class="sxs-lookup"><span data-stu-id="12430-276">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="12430-277">De `-notin` operator is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="12430-277">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="12430-278">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="12430-278">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="12430-279">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="12430-279">Examples:</span></span>

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

## <a name="replacement-operator"></a><span data-ttu-id="12430-280">Vervangings operator</span><span class="sxs-lookup"><span data-stu-id="12430-280">Replacement Operator</span></span>

<span data-ttu-id="12430-281">De `-replace` operator heeft de volgende syntaxis:</span><span class="sxs-lookup"><span data-stu-id="12430-281">The `-replace` operator has the following syntax:</span></span>

`<input> -replace <original>, <substitute>`

<span data-ttu-id="12430-282">De `<original>` tijdelijke aanduiding is een reguliere expressie die overeenkomt met de tekens die moeten worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="12430-282">The `<original>` placeholder is a regular expression matching the characters to be replaced.</span></span> <span data-ttu-id="12430-283">De `<substitute>` tijdelijke aanduiding is een letterlijke teken reeks waarmee ze worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="12430-283">The `<substitute>` placeholder is a literal string that replaces them.</span></span>

<span data-ttu-id="12430-284">De operator vervangt alle of een deel van een waarde met de opgegeven waarde met reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="12430-284">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="12430-285">U kunt de operator gebruiken voor veel beheer taken, zoals het wijzigen van de naam van bestanden.</span><span class="sxs-lookup"><span data-stu-id="12430-285">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="12430-286">Met de volgende opdracht worden bijvoorbeeld de bestandsnaam extensies van alle bestanden gewijzigd `.txt` in `.log` :</span><span class="sxs-lookup"><span data-stu-id="12430-286">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a><span data-ttu-id="12430-287">Hoofdletter gevoelige overeenkomsten</span><span class="sxs-lookup"><span data-stu-id="12430-287">Case-sensitive matches</span></span>

<span data-ttu-id="12430-288">Standaard `-replace` is de operator niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="12430-288">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="12430-289">Gebruik om het hoofdletter gevoelig te maken `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="12430-289">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="12430-290">Gebruik om het expliciet niet hoofdletter gevoelig te maken `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="12430-290">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="12430-291">Bekijk de volgende voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="12430-291">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="12430-292">Vervangingen in reguliere expressies</span><span class="sxs-lookup"><span data-stu-id="12430-292">Substitutions in regular expressions</span></span>

<span data-ttu-id="12430-293">Het is ook mogelijk om reguliere expressies te gebruiken om tekst dynamisch te vervangen met opname groepen en vervangingen.</span><span class="sxs-lookup"><span data-stu-id="12430-293">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="12430-294">Er kan in de teken reeks naar vastleg groepen worden verwezen `<substitute>` met het `$` teken voor het dollar teken () voor de groeps-id.</span><span class="sxs-lookup"><span data-stu-id="12430-294">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="12430-295">Naar vastleg groepen kan worden verwezen met een **getal** of **naam**</span><span class="sxs-lookup"><span data-stu-id="12430-295">Capture groups can be referenced by **Number** or **Name**</span></span>

- <span data-ttu-id="12430-296">Op **nummer** : het vastleggen van groepen wordt van links naar rechts genummerd.</span><span class="sxs-lookup"><span data-stu-id="12430-296">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="12430-297">Op **naam** : voor het vastleggen van groepen kan ook naar een naam worden verwezen.</span><span class="sxs-lookup"><span data-stu-id="12430-297">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> <span data-ttu-id="12430-298">Omdat het `$` teken wordt gebruikt in teken reeks uitbreiding, moet u letterlijke teken reeksen gebruiken of het teken escapeen `$` .</span><span class="sxs-lookup"><span data-stu-id="12430-298">Since the `$` character is used in string expansion, you will must use literal strings or escape the `$` character.</span></span>
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> <span data-ttu-id="12430-299">Omdat het `$` teken in substitutie wordt gebruikt, moet u ook alle exemplaren in de teken reeks verescapenen.</span><span class="sxs-lookup"><span data-stu-id="12430-299">Additionally, since the `$` character is used in substitution, you must escape any instances in your string.</span></span>
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

<span data-ttu-id="12430-300">Zie [about_Regular_Expressions](about_Regular_Expressions.md) en [vervangingen in reguliere expressies](/dotnet/standard/base-types/substitutions-in-regular-expressions) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="12430-300">To learn more see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="12430-301">Vervangen in een verzameling</span><span class="sxs-lookup"><span data-stu-id="12430-301">Substituting in a collection</span></span>

<span data-ttu-id="12430-302">Wanneer de `<input>` naar de `-replace` operator een verzameling is, past Power shell de vervanging toe op elke waarde in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="12430-302">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="12430-303">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-303">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="scriptblock-substitutions"></a><span data-ttu-id="12430-304">Script Block vervangingen</span><span class="sxs-lookup"><span data-stu-id="12430-304">ScriptBlock substitutions</span></span>

<span data-ttu-id="12430-305">Vanaf Power shell 6 kunt u een **script Block** -argument gebruiken voor de _vervangings_ tekst.</span><span class="sxs-lookup"><span data-stu-id="12430-305">Beginning in PowerShell 6, you can use a **ScriptBlock** argument for the _Substitution_ text.</span></span> <span data-ttu-id="12430-306">De **script Block** wordt uitgevoerd voor elke overeenkomst die in de _invoer_ teken reeks is gevonden.</span><span class="sxs-lookup"><span data-stu-id="12430-306">The **ScriptBlock** will execute for each match found in the _input_ string.</span></span>

<span data-ttu-id="12430-307">Gebruik in de **script Block** de `$_` Automatische variabele om te verwijzen naar het huidige **System. Text. RegularExpressions. match** -object.</span><span class="sxs-lookup"><span data-stu-id="12430-307">Within the **ScriptBlock**, use the `$_` automatic variable to refer to the current **System.Text.RegularExpressions.Match** object.</span></span> <span data-ttu-id="12430-308">Met het object **match** krijgt u toegang tot de huidige invoer tekst die wordt vervangen, evenals andere nuttige informatie.</span><span class="sxs-lookup"><span data-stu-id="12430-308">The **Match** object gives you access to the current input text being replaced, as well as other useful information.</span></span>

<span data-ttu-id="12430-309">In dit voor beeld wordt elke reeks van drie decimalen vervangen door het teken equivalent.</span><span class="sxs-lookup"><span data-stu-id="12430-309">This example replaces each sequence of three decimals with the character equivalent.</span></span> <span data-ttu-id="12430-310">De **script Block** wordt uitgevoerd voor elke set van drie decimalen die moeten worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="12430-310">The **ScriptBlock** is run for each set of three decimals that needs to be replaced.</span></span>

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

## <a name="type-comparison"></a><span data-ttu-id="12430-311">Type vergelijking</span><span class="sxs-lookup"><span data-stu-id="12430-311">Type comparison</span></span>

<span data-ttu-id="12430-312">De type vergelijkings operators ( `-is` en `-isnot` ) worden gebruikt om te bepalen of een object een specifiek type is.</span><span class="sxs-lookup"><span data-stu-id="12430-312">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

### <a name="-is"></a><span data-ttu-id="12430-313">-is</span><span class="sxs-lookup"><span data-stu-id="12430-313">-is</span></span>

<span data-ttu-id="12430-314">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="12430-314">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="12430-315">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-315">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a><span data-ttu-id="12430-316">-isnot</span><span class="sxs-lookup"><span data-stu-id="12430-316">-isnot</span></span>

<span data-ttu-id="12430-317">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="12430-317">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="12430-318">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="12430-318">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="12430-319">Zie ook</span><span class="sxs-lookup"><span data-stu-id="12430-319">See also</span></span>

- [<span data-ttu-id="12430-320">about_Operators</span><span class="sxs-lookup"><span data-stu-id="12430-320">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="12430-321">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="12430-321">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="12430-322">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="12430-322">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="12430-323">Compare-object</span><span class="sxs-lookup"><span data-stu-id="12430-323">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="12430-324">Foreach-object</span><span class="sxs-lookup"><span data-stu-id="12430-324">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="12430-325">Where-object</span><span class="sxs-lookup"><span data-stu-id="12430-325">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
