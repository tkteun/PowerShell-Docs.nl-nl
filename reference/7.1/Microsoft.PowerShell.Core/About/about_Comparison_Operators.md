---
description: Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: fe00608edd4cbada275112cb3ce7c20b34f5c5c6
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/16/2020
ms.locfileid: "93253065"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="15dee-104">Over vergelijkings operatoren</span><span class="sxs-lookup"><span data-stu-id="15dee-104">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="15dee-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="15dee-105">Short description</span></span>
<span data-ttu-id="15dee-106">Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.</span><span class="sxs-lookup"><span data-stu-id="15dee-106">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="15dee-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="15dee-107">Long description</span></span>

<span data-ttu-id="15dee-108">Met vergelijkings operatoren kunt u voor waarden opgeven voor het vergelijken van waarden en waarden zoeken die overeenkomen met opgegeven patronen.</span><span class="sxs-lookup"><span data-stu-id="15dee-108">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="15dee-109">Als u een vergelijkings operator wilt gebruiken, geeft u de waarden op die u wilt vergelijken samen met een operator die deze waarden scheidt.</span><span class="sxs-lookup"><span data-stu-id="15dee-109">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="15dee-110">Power shell bevat de volgende vergelijkings operatoren:</span><span class="sxs-lookup"><span data-stu-id="15dee-110">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="15dee-111">Type</span><span class="sxs-lookup"><span data-stu-id="15dee-111">Type</span></span>        | <span data-ttu-id="15dee-112">Operators</span><span class="sxs-lookup"><span data-stu-id="15dee-112">Operators</span></span>    | <span data-ttu-id="15dee-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="15dee-113">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="15dee-114">Gelijkheid</span><span class="sxs-lookup"><span data-stu-id="15dee-114">Equality</span></span>    | <span data-ttu-id="15dee-115">-eq</span><span class="sxs-lookup"><span data-stu-id="15dee-115">-eq</span></span>          | <span data-ttu-id="15dee-116">is gelijk aan</span><span class="sxs-lookup"><span data-stu-id="15dee-116">equals</span></span>                                      |
|             | <span data-ttu-id="15dee-117">-ne</span><span class="sxs-lookup"><span data-stu-id="15dee-117">-ne</span></span>          | <span data-ttu-id="15dee-118">niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="15dee-118">not equals</span></span>                                  |
|             | <span data-ttu-id="15dee-119">-gt</span><span class="sxs-lookup"><span data-stu-id="15dee-119">-gt</span></span>          | <span data-ttu-id="15dee-120">groter dan</span><span class="sxs-lookup"><span data-stu-id="15dee-120">greater than</span></span>                                |
|             | <span data-ttu-id="15dee-121">-ge</span><span class="sxs-lookup"><span data-stu-id="15dee-121">-ge</span></span>          | <span data-ttu-id="15dee-122">groter dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="15dee-122">greater than or equal</span></span>                       |
|             | <span data-ttu-id="15dee-123">-lt</span><span class="sxs-lookup"><span data-stu-id="15dee-123">-lt</span></span>          | <span data-ttu-id="15dee-124">kleiner dan</span><span class="sxs-lookup"><span data-stu-id="15dee-124">less than</span></span>                                   |
|             | <span data-ttu-id="15dee-125">-Le</span><span class="sxs-lookup"><span data-stu-id="15dee-125">-le</span></span>          | <span data-ttu-id="15dee-126">kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="15dee-126">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="15dee-127">Matching</span><span class="sxs-lookup"><span data-stu-id="15dee-127">Matching</span></span>    | <span data-ttu-id="15dee-128">-like</span><span class="sxs-lookup"><span data-stu-id="15dee-128">-like</span></span>        | <span data-ttu-id="15dee-129">Retourneert waar als teken reeks overeenkomt met Joker teken</span><span class="sxs-lookup"><span data-stu-id="15dee-129">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="15dee-130">pattern</span><span class="sxs-lookup"><span data-stu-id="15dee-130">pattern</span></span>                                     |
|             | <span data-ttu-id="15dee-131">-notlike</span><span class="sxs-lookup"><span data-stu-id="15dee-131">-notlike</span></span>     | <span data-ttu-id="15dee-132">Retourneert waar als de teken reeks niet overeenkomt</span><span class="sxs-lookup"><span data-stu-id="15dee-132">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="15dee-133">Joker teken patroon</span><span class="sxs-lookup"><span data-stu-id="15dee-133">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="15dee-134">-match</span><span class="sxs-lookup"><span data-stu-id="15dee-134">-match</span></span>       | <span data-ttu-id="15dee-135">Retourneert True als teken reeks overeenkomt met regex</span><span class="sxs-lookup"><span data-stu-id="15dee-135">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="15dee-136">pattern $matches bevat overeenkomende teken reeksen</span><span class="sxs-lookup"><span data-stu-id="15dee-136">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="15dee-137">-notmatch</span><span class="sxs-lookup"><span data-stu-id="15dee-137">-notmatch</span></span>    | <span data-ttu-id="15dee-138">Retourneert waar als de teken reeks niet overeenkomt</span><span class="sxs-lookup"><span data-stu-id="15dee-138">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="15dee-139">regex-patroon; $matches bevat overeenkomende</span><span class="sxs-lookup"><span data-stu-id="15dee-139">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="15dee-140">tekenreeksen</span><span class="sxs-lookup"><span data-stu-id="15dee-140">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="15dee-141">Containment</span><span class="sxs-lookup"><span data-stu-id="15dee-141">Containment</span></span> | <span data-ttu-id="15dee-142">-contains</span><span class="sxs-lookup"><span data-stu-id="15dee-142">-contains</span></span>    | <span data-ttu-id="15dee-143">Retourneert waar als de referentie waarde bevat</span><span class="sxs-lookup"><span data-stu-id="15dee-143">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="15dee-144">in een verzameling</span><span class="sxs-lookup"><span data-stu-id="15dee-144">in a collection</span></span>                             |
|             | <span data-ttu-id="15dee-145">-notcontains</span><span class="sxs-lookup"><span data-stu-id="15dee-145">-notcontains</span></span> | <span data-ttu-id="15dee-146">Retourneert waar als de referentie waarde niet</span><span class="sxs-lookup"><span data-stu-id="15dee-146">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="15dee-147">opgenomen in een verzameling</span><span class="sxs-lookup"><span data-stu-id="15dee-147">contained in a collection</span></span>                   |
|             | <span data-ttu-id="15dee-148">-in</span><span class="sxs-lookup"><span data-stu-id="15dee-148">-in</span></span>          | <span data-ttu-id="15dee-149">Retourneert waar als de test waarde in een</span><span class="sxs-lookup"><span data-stu-id="15dee-149">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="15dee-150">verzameling</span><span class="sxs-lookup"><span data-stu-id="15dee-150">collection</span></span>                                  |
|             | <span data-ttu-id="15dee-151">-notin</span><span class="sxs-lookup"><span data-stu-id="15dee-151">-notin</span></span>       | <span data-ttu-id="15dee-152">Retourneert waar als de test waarde niet bevat</span><span class="sxs-lookup"><span data-stu-id="15dee-152">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="15dee-153">in een verzameling</span><span class="sxs-lookup"><span data-stu-id="15dee-153">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="15dee-154">Vervanging</span><span class="sxs-lookup"><span data-stu-id="15dee-154">Replacement</span></span> | <span data-ttu-id="15dee-155">-vervangen</span><span class="sxs-lookup"><span data-stu-id="15dee-155">-replace</span></span>     | <span data-ttu-id="15dee-156">Vervangt een teken reeks patroon</span><span class="sxs-lookup"><span data-stu-id="15dee-156">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="15dee-157">Type</span><span class="sxs-lookup"><span data-stu-id="15dee-157">Type</span></span>        | <span data-ttu-id="15dee-158">-is</span><span class="sxs-lookup"><span data-stu-id="15dee-158">-is</span></span>          | <span data-ttu-id="15dee-159">Retourneert waar als beide objecten hetzelfde zijn</span><span class="sxs-lookup"><span data-stu-id="15dee-159">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="15dee-160">type</span><span class="sxs-lookup"><span data-stu-id="15dee-160">type</span></span>                                        |
|             | <span data-ttu-id="15dee-161">-isnot</span><span class="sxs-lookup"><span data-stu-id="15dee-161">-isnot</span></span>       | <span data-ttu-id="15dee-162">Retourneert waar als de objecten niet hetzelfde zijn</span><span class="sxs-lookup"><span data-stu-id="15dee-162">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="15dee-163">type</span><span class="sxs-lookup"><span data-stu-id="15dee-163">type</span></span>                                        |

<span data-ttu-id="15dee-164">Standaard zijn alle vergelijkings operatoren niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="15dee-164">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="15dee-165">Als u een vergelijkings operator hoofdletter gevoelig wilt maken, moet u de naam van de operator vooraf vervangen door een `c` .</span><span class="sxs-lookup"><span data-stu-id="15dee-165">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="15dee-166">De hoofdletter gevoelige versie van `-eq` is bijvoorbeeld `-ceq` .</span><span class="sxs-lookup"><span data-stu-id="15dee-166">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="15dee-167">Als u de niet-hoofdletter gevoeligheid expliciet wilt maken, moet u voorafgaand aan de operator een `i` .</span><span class="sxs-lookup"><span data-stu-id="15dee-167">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="15dee-168">De versie van is bijvoorbeeld expliciet niet hoofdletter gevoelig `-eq` `-ieq` .</span><span class="sxs-lookup"><span data-stu-id="15dee-168">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="15dee-169">Wanneer de invoer voor een operator een scalaire waarde is, retour neren vergelijkings operatoren een Booleaanse waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-169">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="15dee-170">Wanneer de invoer een verzameling waarden is, retour neren de vergelijkings operatoren alle overeenkomende waarden.</span><span class="sxs-lookup"><span data-stu-id="15dee-170">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="15dee-171">Als er geen overeenkomsten in een verzameling zijn, retour neren vergelijkings operatoren een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="15dee-171">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="15dee-172">De uitzonde ringen zijn de containment-Opera Tors, de Opera tors in en de type operator, die altijd een **Booleaanse** waarde Retour neren.</span><span class="sxs-lookup"><span data-stu-id="15dee-172">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="15dee-173">Als u een waarde wilt vergelijken `$null` , moet u aan `$null` de linkerkant van de vergelijking zetten.</span><span class="sxs-lookup"><span data-stu-id="15dee-173">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="15dee-174">Wanneer u vergelijkt `$null` met een **object []** , is het resultaat **False** omdat het vergelijkings object een matrix is.</span><span class="sxs-lookup"><span data-stu-id="15dee-174">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="15dee-175">Wanneer u een matrix vergelijkt met `$null` , worden de `$null` waarden die in de matrix zijn opgeslagen, door de vergelijking gefilterd.</span><span class="sxs-lookup"><span data-stu-id="15dee-175">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="15dee-176">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-176">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

### <a name="equality-operators"></a><span data-ttu-id="15dee-177">Gelijkheids operatoren</span><span class="sxs-lookup"><span data-stu-id="15dee-177">Equality Operators</span></span>

<span data-ttu-id="15dee-178">De gelijkheids operatoren ( `-eq` , `-ne` ) retour neren de waarde True of de overeenkomsten wanneer een of meer invoer waarden identiek zijn aan het opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="15dee-178">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="15dee-179">Het hele patroon moet overeenkomen met een volledige waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-179">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="15dee-180">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-180">Example:</span></span>

#### <a name="-eq"></a><span data-ttu-id="15dee-181">-eq</span><span class="sxs-lookup"><span data-stu-id="15dee-181">-eq</span></span>

<span data-ttu-id="15dee-182">Beschrijving: gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="15dee-182">Description: Equal to.</span></span> <span data-ttu-id="15dee-183">Bevat een identieke waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-183">Includes an identical value.</span></span>

<span data-ttu-id="15dee-184">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-184">Example:</span></span>

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

#### <a name="-ne"></a><span data-ttu-id="15dee-185">-ne</span><span class="sxs-lookup"><span data-stu-id="15dee-185">-ne</span></span>

<span data-ttu-id="15dee-186">Beschrijving: niet gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="15dee-186">Description: Not equal to.</span></span> <span data-ttu-id="15dee-187">Bevat een andere waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-187">Includes a different value.</span></span>

<span data-ttu-id="15dee-188">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-188">Example:</span></span>

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

#### <a name="-gt"></a><span data-ttu-id="15dee-189">-gt</span><span class="sxs-lookup"><span data-stu-id="15dee-189">-gt</span></span>

<span data-ttu-id="15dee-190">Beschrijving: groter dan.</span><span class="sxs-lookup"><span data-stu-id="15dee-190">Description: Greater-than.</span></span>

<span data-ttu-id="15dee-191">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-191">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="15dee-192">Dit mag niet worden verward met `>` , de operator groter dan in veel andere programmeer talen.</span><span class="sxs-lookup"><span data-stu-id="15dee-192">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="15dee-193">In Power shell `>` wordt gebruikt voor omleiding.</span><span class="sxs-lookup"><span data-stu-id="15dee-193">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="15dee-194">Zie [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="15dee-194">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

#### <a name="-ge"></a><span data-ttu-id="15dee-195">-ge</span><span class="sxs-lookup"><span data-stu-id="15dee-195">-ge</span></span>

<span data-ttu-id="15dee-196">Beschrijving: groter dan of gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="15dee-196">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="15dee-197">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-197">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

#### <a name="-lt"></a><span data-ttu-id="15dee-198">-lt</span><span class="sxs-lookup"><span data-stu-id="15dee-198">-lt</span></span>

<span data-ttu-id="15dee-199">Beschrijving: kleiner dan.</span><span class="sxs-lookup"><span data-stu-id="15dee-199">Description: Less-than.</span></span>

<span data-ttu-id="15dee-200">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-200">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

#### <a name="-le"></a><span data-ttu-id="15dee-201">-Le</span><span class="sxs-lookup"><span data-stu-id="15dee-201">-le</span></span>

<span data-ttu-id="15dee-202">Beschrijving: kleiner dan of gelijk aan.</span><span class="sxs-lookup"><span data-stu-id="15dee-202">Description: Less-than or equal to.</span></span>

<span data-ttu-id="15dee-203">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-203">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

### <a name="matching-operators"></a><span data-ttu-id="15dee-204">Overeenkomende Opera tors</span><span class="sxs-lookup"><span data-stu-id="15dee-204">Matching Operators</span></span>

<span data-ttu-id="15dee-205">De like-Opera tors ( `-like` en `-notlike` ) vinden elementen die overeenkomen met of die niet overeenkomen met een opgegeven patroon met Joker teken expressies.</span><span class="sxs-lookup"><span data-stu-id="15dee-205">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="15dee-206">De syntaxis is:</span><span class="sxs-lookup"><span data-stu-id="15dee-206">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="15dee-207">De overeenkomende Opera tors ( `-match` en `-notmatch` ) vinden elementen die overeenkomen met of die niet overeenkomen met een opgegeven patroon met reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="15dee-207">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="15dee-208">De operators matchen vullen de `$Matches` Automatische variabele in wanneer de invoer (het argument aan de linkerkant) naar de operator is één scalair object.</span><span class="sxs-lookup"><span data-stu-id="15dee-208">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="15dee-209">Wanneer de invoer scalair is, `-match` `-notmatch` retour neren de Opera tors en wordt de waarde van de `$Matches` Automatische variabele ingesteld op de overeenkomende onderdelen van het argument.</span><span class="sxs-lookup"><span data-stu-id="15dee-209">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="15dee-210">De syntaxis is:</span><span class="sxs-lookup"><span data-stu-id="15dee-210">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

#### <a name="-like"></a><span data-ttu-id="15dee-211">-like</span><span class="sxs-lookup"><span data-stu-id="15dee-211">-like</span></span>

<span data-ttu-id="15dee-212">Beschrijving: komt overeen met het Joker teken ( \* ).</span><span class="sxs-lookup"><span data-stu-id="15dee-212">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="15dee-213">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-213">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

#### <a name="-notlike"></a><span data-ttu-id="15dee-214">-notlike</span><span class="sxs-lookup"><span data-stu-id="15dee-214">-notlike</span></span>

<span data-ttu-id="15dee-215">Beschrijving: komt niet overeen met het Joker teken ( \* ).</span><span class="sxs-lookup"><span data-stu-id="15dee-215">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="15dee-216">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-216">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="15dee-217">-match</span><span class="sxs-lookup"><span data-stu-id="15dee-217">-match</span></span>

<span data-ttu-id="15dee-218">Beschrijving: komt overeen met een teken reeks met reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="15dee-218">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="15dee-219">Wanneer de invoer scalair is, wordt de `$Matches` Automatische variabele gevuld.</span><span class="sxs-lookup"><span data-stu-id="15dee-219">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="15dee-220">Als de invoer een verzameling is, `-match` `-notmatch` retour neren de Opera tors en de overeenkomende leden van die verzameling, maar de operator vult de `$Matches` variabele niet in.</span><span class="sxs-lookup"><span data-stu-id="15dee-220">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="15dee-221">Met de volgende opdracht wordt bijvoorbeeld een verzameling teken reeksen naar de operator verzonden `-match` .</span><span class="sxs-lookup"><span data-stu-id="15dee-221">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="15dee-222">De `-match` operator retourneert de items in de verzameling die overeenkomen.</span><span class="sxs-lookup"><span data-stu-id="15dee-222">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="15dee-223">De automatische variabele wordt niet gevuld `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="15dee-223">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="15dee-224">Met de volgende opdracht wordt daarentegen één teken reeks naar de `-match` operator verzonden.</span><span class="sxs-lookup"><span data-stu-id="15dee-224">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="15dee-225">De `-match` operator retourneert een Booleaanse waarde en vult de `$Matches` Automatische variabele.</span><span class="sxs-lookup"><span data-stu-id="15dee-225">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="15dee-226">De `$Matches` Automatische variabele is een **hashtabel**.</span><span class="sxs-lookup"><span data-stu-id="15dee-226">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="15dee-227">Als er geen groepering of opname wordt gebruikt, wordt er slechts één sleutel ingevuld.</span><span class="sxs-lookup"><span data-stu-id="15dee-227">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="15dee-228">De `0` sleutel vertegenwoordigt alle tekst die overeenkomt.</span><span class="sxs-lookup"><span data-stu-id="15dee-228">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="15dee-229">Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie over het groeperen en vastleggen met behulp van reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="15dee-229">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="15dee-230">Het is belang rijk te weten dat de `$Matches` hashtabel alleen het eerste exemplaar van een overeenkomend patroon moet bevatten.</span><span class="sxs-lookup"><span data-stu-id="15dee-230">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="15dee-231">De `0` sleutel is een **geheel getal**.</span><span class="sxs-lookup"><span data-stu-id="15dee-231">The `0` key is an **Integer**.</span></span> <span data-ttu-id="15dee-232">U kunt elke **hash** -methode gebruiken om toegang te krijgen tot de opgeslagen waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-232">You can use any **Hashtable** method to access the value stored.</span></span>
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

<span data-ttu-id="15dee-233">De `-notmatch` operator vult de `$Matches` Automatische variabele in wanneer de invoer scalair is en het resultaat ONWAAR is, wanneer er een overeenkomst wordt gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="15dee-233">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

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

#### <a name="-notmatch"></a><span data-ttu-id="15dee-234">-notmatch</span><span class="sxs-lookup"><span data-stu-id="15dee-234">-notmatch</span></span>

<span data-ttu-id="15dee-235">Beschrijving: komt niet overeen met een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="15dee-235">Description: Does not match a string.</span></span> <span data-ttu-id="15dee-236">Maakt gebruik van reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="15dee-236">Uses regular expressions.</span></span> <span data-ttu-id="15dee-237">Wanneer de invoer scalair is, wordt de `$Matches` Automatische variabele gevuld.</span><span class="sxs-lookup"><span data-stu-id="15dee-237">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="15dee-238">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-238">Example:</span></span>

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

### <a name="containment-operators"></a><span data-ttu-id="15dee-239">Containment-Opera tors</span><span class="sxs-lookup"><span data-stu-id="15dee-239">Containment Operators</span></span>

<span data-ttu-id="15dee-240">De containment-Opera tors ( `-contains` en `-notcontains` ) zijn vergelijkbaar met de gelijkheids operatoren.</span><span class="sxs-lookup"><span data-stu-id="15dee-240">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="15dee-241">De containment-Opera tors retour neren echter altijd een Booleaanse waarde, zelfs wanneer de invoer een verzameling is.</span><span class="sxs-lookup"><span data-stu-id="15dee-241">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="15dee-242">Ook, in tegens telling tot de gelijkheids operatoren, retour neren de container-Opera tors een waarde zodra ze de eerste overeenkomst detecteren.</span><span class="sxs-lookup"><span data-stu-id="15dee-242">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="15dee-243">De gelijkheids operatoren evalueren alle invoer en retour neren vervolgens alle overeenkomende items in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="15dee-243">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

#### <a name="-contains"></a><span data-ttu-id="15dee-244">-contains</span><span class="sxs-lookup"><span data-stu-id="15dee-244">-contains</span></span>

<span data-ttu-id="15dee-245">Beschrijving: containment-operator.</span><span class="sxs-lookup"><span data-stu-id="15dee-245">Description: Containment operator.</span></span> <span data-ttu-id="15dee-246">Hiermee wordt aangegeven of een verzameling verwijzings waarden één test waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="15dee-246">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="15dee-247">Retourneert altijd een Boole-waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-247">Always returns a Boolean value.</span></span> <span data-ttu-id="15dee-248">Retourneert alleen waar als de test waarde exact overeenkomt met ten minste een van de referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="15dee-248">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="15dee-249">Wanneer de test waarde een verzameling is, gebruikt de contains-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="15dee-249">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="15dee-250">Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.</span><span class="sxs-lookup"><span data-stu-id="15dee-250">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="15dee-251">In een zeer grote verzameling retourneert de `-contains` operator resultaten sneller dan de operator equal to.</span><span class="sxs-lookup"><span data-stu-id="15dee-251">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="15dee-252">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="15dee-252">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="15dee-253">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="15dee-253">Examples:</span></span>

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

#### <a name="-notcontains"></a><span data-ttu-id="15dee-254">-notcontains</span><span class="sxs-lookup"><span data-stu-id="15dee-254">-notcontains</span></span>

<span data-ttu-id="15dee-255">Beschrijving: containment-operator.</span><span class="sxs-lookup"><span data-stu-id="15dee-255">Description: Containment operator.</span></span> <span data-ttu-id="15dee-256">Hiermee wordt aangegeven of een verzameling verwijzings waarden één test waarde bevat.</span><span class="sxs-lookup"><span data-stu-id="15dee-256">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="15dee-257">Retourneert altijd een Boole-waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-257">Always returns a Boolean value.</span></span> <span data-ttu-id="15dee-258">Retourneert waar als de test waarde geen exacte overeenkomsten voor ten minste een van de verwijzings waarden is.</span><span class="sxs-lookup"><span data-stu-id="15dee-258">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="15dee-259">Wanneer de test waarde een verzameling is, gebruikt de NotContains-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="15dee-259">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="15dee-260">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="15dee-260">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="15dee-261">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="15dee-261">Examples:</span></span>

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

#### <a name="-in"></a><span data-ttu-id="15dee-262">-in</span><span class="sxs-lookup"><span data-stu-id="15dee-262">-in</span></span>

<span data-ttu-id="15dee-263">Beschrijving: in operator.</span><span class="sxs-lookup"><span data-stu-id="15dee-263">Description: In operator.</span></span> <span data-ttu-id="15dee-264">Hiermee wordt aangegeven of een test waarde wordt weer gegeven in een verzameling referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="15dee-264">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="15dee-265">Altijd retour neren als Booleaanse waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-265">Always return as Boolean value.</span></span> <span data-ttu-id="15dee-266">Retourneert alleen waar als de test waarde exact overeenkomt met ten minste een van de referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="15dee-266">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="15dee-267">Wanneer de test waarde een verzameling is, gebruikt de in-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="15dee-267">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="15dee-268">Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.</span><span class="sxs-lookup"><span data-stu-id="15dee-268">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="15dee-269">De `-in` operator is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="15dee-269">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="15dee-270">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="15dee-270">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="15dee-271">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="15dee-271">Examples:</span></span>

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

#### <a name="-notin"></a><span data-ttu-id="15dee-272">-notin</span><span class="sxs-lookup"><span data-stu-id="15dee-272">-notin</span></span>

<span data-ttu-id="15dee-273">Beschrijving: Hiermee wordt aangegeven of een test waarde wordt weer gegeven in een verzameling referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="15dee-273">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="15dee-274">Retourneert altijd een Boole-waarde.</span><span class="sxs-lookup"><span data-stu-id="15dee-274">Always returns a Boolean value.</span></span> <span data-ttu-id="15dee-275">Retourneert waar als de test waarde niet exact overeenkomt voor ten minste een van de referentie waarden.</span><span class="sxs-lookup"><span data-stu-id="15dee-275">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="15dee-276">Wanneer de test waarde een verzameling is, gebruikt de in-operator referentie gelijkheid.</span><span class="sxs-lookup"><span data-stu-id="15dee-276">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="15dee-277">Het retourneert alleen waar als een van de referentie waarden hetzelfde exemplaar van het object test waarde is.</span><span class="sxs-lookup"><span data-stu-id="15dee-277">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="15dee-278">De `-notin` operator is geïntroduceerd in Power shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="15dee-278">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="15dee-279">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="15dee-279">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="15dee-280">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="15dee-280">Examples:</span></span>

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

### <a name="replacement-operator"></a><span data-ttu-id="15dee-281">Vervangings operator</span><span class="sxs-lookup"><span data-stu-id="15dee-281">Replacement Operator</span></span>

<span data-ttu-id="15dee-282">De `-replace` operator vervangt alle of een deel van een waarde met de opgegeven waarde met reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="15dee-282">The `-replace` operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="15dee-283">U kunt de `-replace` operator gebruiken voor veel beheer taken, zoals het wijzigen van de naam van bestanden.</span><span class="sxs-lookup"><span data-stu-id="15dee-283">You can use the `-replace` operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="15dee-284">Met de volgende opdracht wordt bijvoorbeeld de bestandsnaam extensies van alle txt-bestanden gewijzigd in. log:</span><span class="sxs-lookup"><span data-stu-id="15dee-284">For example, the following command changes the file name extensions of all .txt files to .log:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="15dee-285">De syntaxis van de `-replace` operator is als volgt, waarbij de `<original>` tijdelijke aanduiding staat voor de tekens die moeten worden vervangen en de `<substitute>` tijdelijke aanduiding staat voor de tekens die ze vervangen:</span><span class="sxs-lookup"><span data-stu-id="15dee-285">The syntax of the `-replace` operator is as follows, where the `<original>` placeholder represents the characters to be replaced, and the `<substitute>` placeholder represents the characters that will replace them:</span></span>

`<input> <operator> <original>, <substitute>`

<span data-ttu-id="15dee-286">Standaard `-replace` is de operator niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="15dee-286">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="15dee-287">Gebruik om het hoofdletter gevoelig te maken `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="15dee-287">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="15dee-288">Gebruik om het expliciet niet hoofdletter gevoelig te maken `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="15dee-288">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="15dee-289">Bekijk de volgende voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="15dee-289">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
```

```Output
Cook
```

```powershell
"book" -ireplace "B", "C"
```

```Output
Cook
```

```powershell
"book" -creplace "B", "C"
```

```Output
book
```

<span data-ttu-id="15dee-290">Het is ook mogelijk om reguliere expressies te gebruiken om tekst dynamisch te vervangen met opname groepen en vervangingen.</span><span class="sxs-lookup"><span data-stu-id="15dee-290">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="15dee-291">Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="15dee-291">For more information, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="scriptblock-substitutions"></a><span data-ttu-id="15dee-292">Script Block vervangingen</span><span class="sxs-lookup"><span data-stu-id="15dee-292">ScriptBlock substitutions</span></span>

<span data-ttu-id="15dee-293">Vanaf Power shell 6 kunt u een **script Block** -argument gebruiken voor de *vervangings* tekst.</span><span class="sxs-lookup"><span data-stu-id="15dee-293">Beginning in PowerShell 6, you can use a **ScriptBlock** argument for the *Substitution* text.</span></span> <span data-ttu-id="15dee-294">De **script Block** wordt uitgevoerd voor elke overeenkomst die in de *invoer* teken reeks is gevonden.</span><span class="sxs-lookup"><span data-stu-id="15dee-294">The **ScriptBlock** will execute for each match found in the *input* string.</span></span>

<span data-ttu-id="15dee-295">Gebruik in de **script Block** de `$_` Automatische variabele om te verwijzen naar het huidige **System. Text. RegularExpressions. match** -object.</span><span class="sxs-lookup"><span data-stu-id="15dee-295">Within the **ScriptBlock** , use the `$_` automatic variable to refer to the current **System.Text.RegularExpressions.Match** object.</span></span> <span data-ttu-id="15dee-296">Met het object **match** krijgt u toegang tot de huidige invoer tekst die wordt vervangen, evenals andere nuttige informatie.</span><span class="sxs-lookup"><span data-stu-id="15dee-296">The **Match** object gives you access to the current input text being replaced, as well as other useful information.</span></span>

<span data-ttu-id="15dee-297">In dit voor beeld wordt elke reeks van drie decimalen vervangen door het teken equivalent.</span><span class="sxs-lookup"><span data-stu-id="15dee-297">This example replaces each sequence of three decimals with the character equivalent.</span></span> <span data-ttu-id="15dee-298">De **script Block** wordt uitgevoerd voor elke set van drie decimalen die moeten worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="15dee-298">The **ScriptBlock** is run for each set of three decimals that needs to be replaced.</span></span>

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

### <a name="type-comparison"></a><span data-ttu-id="15dee-299">Type vergelijking</span><span class="sxs-lookup"><span data-stu-id="15dee-299">Type comparison</span></span>

<span data-ttu-id="15dee-300">De type vergelijkings operators ( `-is` en `-isnot` ) worden gebruikt om te bepalen of een object een specifiek type is.</span><span class="sxs-lookup"><span data-stu-id="15dee-300">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

#### <a name="-is"></a><span data-ttu-id="15dee-301">-is</span><span class="sxs-lookup"><span data-stu-id="15dee-301">-is</span></span>

<span data-ttu-id="15dee-302">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="15dee-302">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="15dee-303">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-303">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

#### <a name="-isnot"></a><span data-ttu-id="15dee-304">-isnot</span><span class="sxs-lookup"><span data-stu-id="15dee-304">-isnot</span></span>

<span data-ttu-id="15dee-305">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="15dee-305">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="15dee-306">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="15dee-306">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="15dee-307">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="15dee-307">SEE ALSO</span></span>

- [<span data-ttu-id="15dee-308">about_Operators</span><span class="sxs-lookup"><span data-stu-id="15dee-308">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="15dee-309">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="15dee-309">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="15dee-310">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="15dee-310">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="15dee-311">Compare-object</span><span class="sxs-lookup"><span data-stu-id="15dee-311">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="15dee-312">Foreach-object</span><span class="sxs-lookup"><span data-stu-id="15dee-312">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="15dee-313">Where-object</span><span class="sxs-lookup"><span data-stu-id="15dee-313">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
