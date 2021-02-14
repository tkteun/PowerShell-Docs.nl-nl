---
description: Hierin worden de Opera tors beschreven waarmee waarden in Power shell worden vergeleken.
Locale: en-US
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: 179798b490855cd463e2348acaf1292f042ba173
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500156"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="1e795-103">Over vergelijkings operatoren</span><span class="sxs-lookup"><span data-stu-id="1e795-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="1e795-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="1e795-104">Short description</span></span>

<span data-ttu-id="1e795-105">Met de vergelijkings operatoren in Power shell kunt u twee waarden vergelijken of elementen van een verzameling filteren op basis van een invoer waarde.</span><span class="sxs-lookup"><span data-stu-id="1e795-105">The comparison operators in PowerShell can either compare two values or filter elements of a collection against an input value.</span></span>

## <a name="long-description"></a><span data-ttu-id="1e795-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="1e795-106">Long description</span></span>

<span data-ttu-id="1e795-107">Vergelijkings operatoren bieden u de mogelijkheid waarden te vergelijken of waarden te vinden die overeenkomen met opgegeven patronen.</span><span class="sxs-lookup"><span data-stu-id="1e795-107">Comparison operators let you compare values or finding values that match specified patterns.</span></span> <span data-ttu-id="1e795-108">Power shell bevat de volgende vergelijkings operatoren:</span><span class="sxs-lookup"><span data-stu-id="1e795-108">PowerShell includes the following comparison operators:</span></span>

|    <span data-ttu-id="1e795-109">Type</span><span class="sxs-lookup"><span data-stu-id="1e795-109">Type</span></span>     |   <span data-ttu-id="1e795-110">Operator</span><span class="sxs-lookup"><span data-stu-id="1e795-110">Operator</span></span>   |              <span data-ttu-id="1e795-111">Vergelijkings test</span><span class="sxs-lookup"><span data-stu-id="1e795-111">Comparison test</span></span>              |
| ----------- | ------------ | ----------------------------------------- |
| <span data-ttu-id="1e795-112">Gelijkheid</span><span class="sxs-lookup"><span data-stu-id="1e795-112">Equality</span></span>    | <span data-ttu-id="1e795-113">-eq</span><span class="sxs-lookup"><span data-stu-id="1e795-113">-eq</span></span>          | <span data-ttu-id="1e795-114">is gelijk aan</span><span class="sxs-lookup"><span data-stu-id="1e795-114">equals</span></span>                                    |
|             | <span data-ttu-id="1e795-115">-ne</span><span class="sxs-lookup"><span data-stu-id="1e795-115">-ne</span></span>          | <span data-ttu-id="1e795-116">niet gelijk aan</span><span class="sxs-lookup"><span data-stu-id="1e795-116">not equals</span></span>                                |
|             | <span data-ttu-id="1e795-117">-gt</span><span class="sxs-lookup"><span data-stu-id="1e795-117">-gt</span></span>          | <span data-ttu-id="1e795-118">groter dan</span><span class="sxs-lookup"><span data-stu-id="1e795-118">greater than</span></span>                              |
|             | <span data-ttu-id="1e795-119">-ge</span><span class="sxs-lookup"><span data-stu-id="1e795-119">-ge</span></span>          | <span data-ttu-id="1e795-120">groter dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="1e795-120">greater than or equal</span></span>                     |
|             | <span data-ttu-id="1e795-121">-lt</span><span class="sxs-lookup"><span data-stu-id="1e795-121">-lt</span></span>          | <span data-ttu-id="1e795-122">kleiner dan</span><span class="sxs-lookup"><span data-stu-id="1e795-122">less than</span></span>                                 |
|             | <span data-ttu-id="1e795-123">-Le</span><span class="sxs-lookup"><span data-stu-id="1e795-123">-le</span></span>          | <span data-ttu-id="1e795-124">kleiner dan of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="1e795-124">less than or equal</span></span>                        |
| <span data-ttu-id="1e795-125">Matching</span><span class="sxs-lookup"><span data-stu-id="1e795-125">Matching</span></span>    | <span data-ttu-id="1e795-126">-like</span><span class="sxs-lookup"><span data-stu-id="1e795-126">-like</span></span>        | <span data-ttu-id="1e795-127">teken reeks komt overeen met Joker patroon</span><span class="sxs-lookup"><span data-stu-id="1e795-127">string matches wildcard pattern</span></span>           |
|             | <span data-ttu-id="1e795-128">-notlike</span><span class="sxs-lookup"><span data-stu-id="1e795-128">-notlike</span></span>     | <span data-ttu-id="1e795-129">teken reeks komt niet overeen met Joker patroon</span><span class="sxs-lookup"><span data-stu-id="1e795-129">string does not match wildcard pattern</span></span>    |
|             | <span data-ttu-id="1e795-130">-match</span><span class="sxs-lookup"><span data-stu-id="1e795-130">-match</span></span>       | <span data-ttu-id="1e795-131">teken reeks komt overeen met regex-patroon</span><span class="sxs-lookup"><span data-stu-id="1e795-131">string matches regex pattern</span></span>              |
|             | <span data-ttu-id="1e795-132">-notmatch</span><span class="sxs-lookup"><span data-stu-id="1e795-132">-notmatch</span></span>    | <span data-ttu-id="1e795-133">teken reeks komt niet overeen met regex-patroon</span><span class="sxs-lookup"><span data-stu-id="1e795-133">string does not match regex pattern</span></span>       |
| <span data-ttu-id="1e795-134">Vervanging</span><span class="sxs-lookup"><span data-stu-id="1e795-134">Replacement</span></span> | <span data-ttu-id="1e795-135">-vervangen</span><span class="sxs-lookup"><span data-stu-id="1e795-135">-replace</span></span>     | <span data-ttu-id="1e795-136">vervangt teken reeksen die overeenkomen met een regex-patroon</span><span class="sxs-lookup"><span data-stu-id="1e795-136">replaces strings matching a regex pattern</span></span> |
| <span data-ttu-id="1e795-137">Containment</span><span class="sxs-lookup"><span data-stu-id="1e795-137">Containment</span></span> | <span data-ttu-id="1e795-138">-contains</span><span class="sxs-lookup"><span data-stu-id="1e795-138">-contains</span></span>    | <span data-ttu-id="1e795-139">verzameling bevat een waarde</span><span class="sxs-lookup"><span data-stu-id="1e795-139">collection contains a value</span></span>               |
|             | <span data-ttu-id="1e795-140">-notcontains</span><span class="sxs-lookup"><span data-stu-id="1e795-140">-notcontains</span></span> | <span data-ttu-id="1e795-141">verzameling bevat geen waarde</span><span class="sxs-lookup"><span data-stu-id="1e795-141">collection does not contain a value</span></span>       |
|             | <span data-ttu-id="1e795-142">-in</span><span class="sxs-lookup"><span data-stu-id="1e795-142">-in</span></span>          | <span data-ttu-id="1e795-143">waarde bevindt zich in een verzameling</span><span class="sxs-lookup"><span data-stu-id="1e795-143">value is in a collection</span></span>                  |
|             | <span data-ttu-id="1e795-144">-notin</span><span class="sxs-lookup"><span data-stu-id="1e795-144">-notin</span></span>       | <span data-ttu-id="1e795-145">waarde bevindt zich niet in een verzameling</span><span class="sxs-lookup"><span data-stu-id="1e795-145">value is not in a collection</span></span>              |
| <span data-ttu-id="1e795-146">Type</span><span class="sxs-lookup"><span data-stu-id="1e795-146">Type</span></span>        | <span data-ttu-id="1e795-147">-is</span><span class="sxs-lookup"><span data-stu-id="1e795-147">-is</span></span>          | <span data-ttu-id="1e795-148">beide objecten zijn van hetzelfde type</span><span class="sxs-lookup"><span data-stu-id="1e795-148">both objects are the same type</span></span>            |
|             | <span data-ttu-id="1e795-149">-isnot</span><span class="sxs-lookup"><span data-stu-id="1e795-149">-isnot</span></span>       | <span data-ttu-id="1e795-150">de objecten zijn niet van hetzelfde type</span><span class="sxs-lookup"><span data-stu-id="1e795-150">the objects are not the same type</span></span>         |

## <a name="common-features"></a><span data-ttu-id="1e795-151">Algemene functies</span><span class="sxs-lookup"><span data-stu-id="1e795-151">Common features</span></span>

<span data-ttu-id="1e795-152">Standaard zijn alle vergelijkings operatoren niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="1e795-152">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="1e795-153">Als u een vergelijkings operator hoofdletter gevoelig wilt maken, moet u een `c` na de toevoegen `-` .</span><span class="sxs-lookup"><span data-stu-id="1e795-153">To make a comparison operator case-sensitive, add a `c` after the `-`.</span></span> <span data-ttu-id="1e795-154">`-ceq`Is bijvoorbeeld de hoofdletter gevoelige versie van `-eq` .</span><span class="sxs-lookup"><span data-stu-id="1e795-154">For example, `-ceq` is the case-sensitive version of `-eq`.</span></span> <span data-ttu-id="1e795-155">Voeg een before toe om de hoofdletter gevoeligheid expliciet te maken `i` `-` .</span><span class="sxs-lookup"><span data-stu-id="1e795-155">To make the case-insensitivity explicit, add an `i` before `-`.</span></span> <span data-ttu-id="1e795-156">`-ieq`Is bijvoorbeeld de expliciete niet-hoofdletter gevoelige versie van `-eq` .</span><span class="sxs-lookup"><span data-stu-id="1e795-156">For example, `-ieq` is the explicitly case-insensitive version of `-eq`.</span></span>

<span data-ttu-id="1e795-157">Wanneer de invoer van een operator een scalaire waarde is, retourneert de operator een **Boole** -waarde.</span><span class="sxs-lookup"><span data-stu-id="1e795-157">When the input of an operator is a scalar value, the operator returns a **Boolean** value.</span></span> <span data-ttu-id="1e795-158">Wanneer de invoer een verzameling is, retourneert de operator de elementen van de verzameling die overeenkomen met de rechter waarde van de expressie.</span><span class="sxs-lookup"><span data-stu-id="1e795-158">When the input is a collection, the operator returns the elements of the collection that match the right-hand value of the expression.</span></span>
<span data-ttu-id="1e795-159">Als er geen overeenkomsten in de verzameling zijn, retour neren vergelijkings operatoren een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="1e795-159">If there are no matches in the collection, comparison operators return an empty array.</span></span> <span data-ttu-id="1e795-160">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-160">For example:</span></span>

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

<span data-ttu-id="1e795-161">Er zijn enkele uitzonde ringen:</span><span class="sxs-lookup"><span data-stu-id="1e795-161">There are a few exceptions:</span></span>

- <span data-ttu-id="1e795-162">De containment-en type-Opera tors retour neren altijd een **Booleaanse** waarde</span><span class="sxs-lookup"><span data-stu-id="1e795-162">The containment and type operators always return a **Boolean** value</span></span>
- <span data-ttu-id="1e795-163">De `-replace` operator retourneert het vervangings resultaat</span><span class="sxs-lookup"><span data-stu-id="1e795-163">The `-replace` operator returns the replacement result</span></span>
- <span data-ttu-id="1e795-164">De `-match` `-notmatch` Opera tors en vullen ook de `$Matches` Automatische variabele</span><span class="sxs-lookup"><span data-stu-id="1e795-164">The `-match` and `-notmatch` operators also populate the `$Matches` automatic variable</span></span>

## <a name="equality-operators"></a><span data-ttu-id="1e795-165">Gelijkheidsoperatoren</span><span class="sxs-lookup"><span data-stu-id="1e795-165">Equality operators</span></span>

### <a name="-eq-and--ne"></a><span data-ttu-id="1e795-166">-EQ en-ne</span><span class="sxs-lookup"><span data-stu-id="1e795-166">-eq and -ne</span></span>

<span data-ttu-id="1e795-167">Wanneer de linkerkant scalair is, `-eq` retourneert **waar** als de rechter kant een exacte overeenkomst heeft, anders `-eq` wordt **False** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e795-167">When the left-hand side is scalar, `-eq` returns **True** if the right-hand side is an exact match, otherwise, `-eq` returns **False**.</span></span> <span data-ttu-id="1e795-168">`-ne` doet het tegenovergestelde; Wanneer beide zijden overeenkomen, wordt **False** geretourneerd. anders `-ne` wordt waar geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e795-168">`-ne` does the opposite; it returns **False** when both sides match; otherwise, `-ne` returns True.</span></span>

<span data-ttu-id="1e795-169">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-169">Example:</span></span>

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

<span data-ttu-id="1e795-170">Wanneer de linkerkant een verzameling is, `-eq` retourneert de leden die aan de rechter kant overeenkomen, terwijl `-ne` deze worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="1e795-170">When the left-hand side is a collection, `-eq` returns those members that match the right-hand side, while `-ne` filters them out.</span></span>

<span data-ttu-id="1e795-171">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-171">Example:</span></span>

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

<span data-ttu-id="1e795-172">Deze opera tors verwerken alle elementen van de verzameling.</span><span class="sxs-lookup"><span data-stu-id="1e795-172">These operators process all elements of the collection.</span></span> <span data-ttu-id="1e795-173">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-173">Example:</span></span>

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

<span data-ttu-id="1e795-174">De gelijkheids operatoren accepteren twee objecten, niet alleen een scalair of verzameling.</span><span class="sxs-lookup"><span data-stu-id="1e795-174">The equality operators accept any two objects, not just a scalar or collection.</span></span>
<span data-ttu-id="1e795-175">Maar het vergelijkings resultaat is niet gegarandeerd dat dit zinvol is voor de eind gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1e795-175">But the comparison result is not guaranteed to be meaningful for the end-user.</span></span>
<span data-ttu-id="1e795-176">In het volgende voor beeld wordt het probleem gedemonstreerd.</span><span class="sxs-lookup"><span data-stu-id="1e795-176">The following example demonstrates the issue.</span></span>

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

<span data-ttu-id="1e795-177">In dit voor beeld hebben we twee objecten met identieke eigenschappen gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1e795-177">In this example, we created two objects with identical properties.</span></span> <span data-ttu-id="1e795-178">Het resultaat van de gelijkheids test is dan **Onwaar** , omdat deze verschillende objecten zijn.</span><span class="sxs-lookup"><span data-stu-id="1e795-178">Yet, the equality test result is **False** because they are different objects.</span></span> <span data-ttu-id="1e795-179">Als u vergelijk bare klassen wilt maken, moet u [System. \<T> IEquatable][2] in uw klasse implementeren.</span><span class="sxs-lookup"><span data-stu-id="1e795-179">To create comparable classes, you need to implement [System.IEquatable\<T>][2] in your class.</span></span> <span data-ttu-id="1e795-180">In het volgende voor beeld ziet u de gedeeltelijke implementatie van een **MyFileInfoSet** -klasse die [System. \<T> IEquatable][2] implementeert en twee eigenschappen, **bestand** en **grootte** heeft.</span><span class="sxs-lookup"><span data-stu-id="1e795-180">The following example demonstrates the partial implementation of a **MyFileInfoSet** class that implements [System.IEquatable\<T>][2] and has two properties, **File** and **Size**.</span></span> <span data-ttu-id="1e795-181">De `Equals()` methode retourneert True als de bestands-en grootte-eigenschappen van twee **MyFileInfoSet** -objecten hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="1e795-181">The `Equals()` method returns True if the File and Size properties of two **MyFileInfoSet** objects are the same.</span></span>

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

<span data-ttu-id="1e795-182">Een prominent voor beeld van het vergelijken van wille keurige objecten is om erachter te komen of ze null zijn.</span><span class="sxs-lookup"><span data-stu-id="1e795-182">A prominent example of comparing arbitrary objects is to find out if they are null.</span></span> <span data-ttu-id="1e795-183">Maar als u wilt bepalen of een variabele is `$null` , moet u `$null` aan de linkerkant van de gelijkheids operator.</span><span class="sxs-lookup"><span data-stu-id="1e795-183">But if you need to determine whether a variable is `$null`, you must put `$null` on the left-hand side of the equality operator.</span></span> <span data-ttu-id="1e795-184">Als u deze aan de rechter kant gebruikt, heeft dat niet de verwachte.</span><span class="sxs-lookup"><span data-stu-id="1e795-184">Putting it on the right-hand side does not do what you expect.</span></span>

<span data-ttu-id="1e795-185">U kunt bijvoorbeeld `$a` een matrix met null-elementen maken:</span><span class="sxs-lookup"><span data-stu-id="1e795-185">For example, let `$a` be an array containing null elements:</span></span>

```powershell
$a = 1, 2, $null, 4, $null, 6
```

<span data-ttu-id="1e795-186">De volgende tests die `$a` niet null zijn.</span><span class="sxs-lookup"><span data-stu-id="1e795-186">The following tests that `$a` is not null.</span></span>

```powershell
$null -ne $a
```

```output
False
```

<span data-ttu-id="1e795-187">De volgende bestanden zijn echter alle null-elementen van `$a` :</span><span class="sxs-lookup"><span data-stu-id="1e795-187">The following, however, filers out all null elements from `$a`:</span></span>

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a><span data-ttu-id="1e795-188">-gt,-ge,-lt en-Le</span><span class="sxs-lookup"><span data-stu-id="1e795-188">-gt, -ge, -lt, and -le</span></span>

<span data-ttu-id="1e795-189">`-gt`, `-ge` , `-lt` en `-le` gedragen zich op dezelfde manier.</span><span class="sxs-lookup"><span data-stu-id="1e795-189">`-gt`, `-ge`, `-lt`, and `-le` behave very similarly.</span></span> <span data-ttu-id="1e795-190">Wanneer beide zijden scalair zijn, retour neren ze **waar** of **Onwaar** , afhankelijk van de mate waarin de twee zijden elkaar vergelijken:</span><span class="sxs-lookup"><span data-stu-id="1e795-190">When both sides are scalar they return **True** or **False** depending on how the two sides compare:</span></span>

| <span data-ttu-id="1e795-191">Operator</span><span class="sxs-lookup"><span data-stu-id="1e795-191">Operator</span></span> | <span data-ttu-id="1e795-192">Retourneert waar als...</span><span class="sxs-lookup"><span data-stu-id="1e795-192">Returns True when...</span></span>                   |
| -------- | -------------------------------------- |
| <span data-ttu-id="1e795-193">-gt</span><span class="sxs-lookup"><span data-stu-id="1e795-193">-gt</span></span>      | <span data-ttu-id="1e795-194">De linkerkant is groter</span><span class="sxs-lookup"><span data-stu-id="1e795-194">The left-hand side is greater</span></span>          |
| <span data-ttu-id="1e795-195">-ge</span><span class="sxs-lookup"><span data-stu-id="1e795-195">-ge</span></span>      | <span data-ttu-id="1e795-196">De linkerkant is groter of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="1e795-196">The left-hand side is greater or equal</span></span> |
| <span data-ttu-id="1e795-197">-lt</span><span class="sxs-lookup"><span data-stu-id="1e795-197">-lt</span></span>      | <span data-ttu-id="1e795-198">De linkerkant is kleiner</span><span class="sxs-lookup"><span data-stu-id="1e795-198">The left-hand side is smaller</span></span>          |
| <span data-ttu-id="1e795-199">-Le</span><span class="sxs-lookup"><span data-stu-id="1e795-199">-le</span></span>      | <span data-ttu-id="1e795-200">De linkerkant is kleiner of gelijk aan</span><span class="sxs-lookup"><span data-stu-id="1e795-200">The left-hand side is smaller or equal</span></span> |

<span data-ttu-id="1e795-201">In de volgende voor beelden retour neren alle instructies waar.</span><span class="sxs-lookup"><span data-stu-id="1e795-201">In the following examples, all statements return True.</span></span>

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> <span data-ttu-id="1e795-202">In de meeste programmeer talen is de operator groter dan `>` .</span><span class="sxs-lookup"><span data-stu-id="1e795-202">In most programming languages the greater-than operator is `>`.</span></span> <span data-ttu-id="1e795-203">In Power shell wordt dit teken gebruikt voor omleiding.</span><span class="sxs-lookup"><span data-stu-id="1e795-203">In PowerShell, this character is used for redirection.</span></span> <span data-ttu-id="1e795-204">Zie [about_Redirection][3]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e795-204">For details, see [about_Redirection][3].</span></span>

<span data-ttu-id="1e795-205">Wanneer de linkerkant een verzameling is, vergelijken deze opera tors elk lid van de verzameling met de rechter kant.</span><span class="sxs-lookup"><span data-stu-id="1e795-205">When the left-hand side is a collection, these operators compare each member of the collection with the right-hand side.</span></span> <span data-ttu-id="1e795-206">Afhankelijk van hun logica, kunnen ze het lid blijven of negeren.</span><span class="sxs-lookup"><span data-stu-id="1e795-206">Depending on their logic, they either keep or discard the member.</span></span>

<span data-ttu-id="1e795-207">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-207">Example:</span></span>

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

<span data-ttu-id="1e795-208">Deze opera tors werken met elke klasse die [System. IComparable][1]implementeert.</span><span class="sxs-lookup"><span data-stu-id="1e795-208">These operators work with any class that implements [System.IComparable][1].</span></span>

<span data-ttu-id="1e795-209">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="1e795-209">Examples:</span></span>

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

<span data-ttu-id="1e795-210">In het volgende voor beeld ziet u dat er geen symbool is op een American QWERTY-toetsen bord dat na ' a ' wordt gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="1e795-210">The following example demonstrates that there is no symbol on an American QWERTY keyboard that gets sorted after 'a'.</span></span> <span data-ttu-id="1e795-211">Er wordt een set met al deze symbolen aan de `-gt` operator gevoed om ze te vergelijken met ' a '.</span><span class="sxs-lookup"><span data-stu-id="1e795-211">It feeds a set containing all such symbols to the `-gt` operator to compare them against 'a'.</span></span> <span data-ttu-id="1e795-212">De uitvoer is een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="1e795-212">The output is an empty array.</span></span>

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

<span data-ttu-id="1e795-213">Als de twee zijden van de Opera tors niet redelijk vergelijkbaar zijn, verhogen deze opera tors een fout die niet wordt beëindigd.</span><span class="sxs-lookup"><span data-stu-id="1e795-213">If the two sides of the operators are not reasonably comparable, these operators raise a non-terminating error.</span></span>

## <a name="matching-operators"></a><span data-ttu-id="1e795-214">Overeenkomende Opera tors</span><span class="sxs-lookup"><span data-stu-id="1e795-214">Matching operators</span></span>

<span data-ttu-id="1e795-215">De overeenkomende Opera tors ( `-like` ,, `-notlike` `-match` en `-notmatch` ) vinden elementen die overeenkomen of niet overeenkomen met een opgegeven patroon.</span><span class="sxs-lookup"><span data-stu-id="1e795-215">The matching operators (`-like`, `-notlike`, `-match`, and `-notmatch`) find elements that match or do not match a specified pattern.</span></span> <span data-ttu-id="1e795-216">Het patroon voor `-like` en `-notlike` is een Joker teken expressie (die `*` , `?` en `[ ]` ) en `-match` `-notmatch` een reguliere expressie (regex) accepteert.</span><span class="sxs-lookup"><span data-stu-id="1e795-216">The pattern for `-like` and `-notlike` is a wildcard expression (containing `*`, `?`, and `[ ]`), while `-match` and `-notmatch` accept a regular expression (Regex).</span></span>

<span data-ttu-id="1e795-217">De syntaxis is:</span><span class="sxs-lookup"><span data-stu-id="1e795-217">The syntax is:</span></span>

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

<span data-ttu-id="1e795-218">Wanneer de invoer van deze opera tors een scalaire waarde is, retour neren ze een **Booleaanse** waarde.</span><span class="sxs-lookup"><span data-stu-id="1e795-218">When the input of these operators is a scalar value, they return a **Boolean** value.</span></span> <span data-ttu-id="1e795-219">Wanneer de invoer een verzameling waarden is, retour neren de Opera tors overeenkomende leden.</span><span class="sxs-lookup"><span data-stu-id="1e795-219">When the input is a collection of values, the operators return any matching members.</span></span> <span data-ttu-id="1e795-220">Als er geen overeenkomsten in een verzameling zijn, retour neren de Opera tors een lege matrix.</span><span class="sxs-lookup"><span data-stu-id="1e795-220">If there are no matches in a collection, the operators return an empty array.</span></span>

### <a name="-like-and--notlike"></a><span data-ttu-id="1e795-221">-like en-notlike</span><span class="sxs-lookup"><span data-stu-id="1e795-221">-like and -notlike</span></span>

<span data-ttu-id="1e795-222">`-like` en `-notlike` gedragen zich op dezelfde manier als `-eq` en `-ne` , maar de rechter kant kan een teken reeks met [joker tekens](about_Wildcards.md)zijn.</span><span class="sxs-lookup"><span data-stu-id="1e795-222">`-like` and `-notlike` behave similarly to `-eq` and `-ne`, but the right-hand side could be a string containing [wildcards](about_Wildcards.md).</span></span>

<span data-ttu-id="1e795-223">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-223">Example:</span></span>

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a><span data-ttu-id="1e795-224">-Match and-notmatch</span><span class="sxs-lookup"><span data-stu-id="1e795-224">-match and -notmatch</span></span>

<span data-ttu-id="1e795-225">`-match` en `-notmatch` gebruik reguliere expressies om te zoeken naar een patroon in de waarden aan de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="1e795-225">`-match` and `-notmatch` use regular expressions to search for pattern in the left-hand side values.</span></span> <span data-ttu-id="1e795-226">Reguliere expressies kunnen overeenkomen met complexe patronen zoals e-mail adressen, UNC-paden of geformatteerde telefoon nummers.</span><span class="sxs-lookup"><span data-stu-id="1e795-226">Regular expressions can match complex patterns like email addresses, UNC paths, or formatted phone numbers.</span></span> <span data-ttu-id="1e795-227">De teken reeks aan de rechter kant moet voldoen aan de regels voor [reguliere expressies](about_Regular_Expressions.md) .</span><span class="sxs-lookup"><span data-stu-id="1e795-227">The right-hand side string must adhere to the [regular expressions](about_Regular_Expressions.md) rules.</span></span>

<span data-ttu-id="1e795-228">Scalaire voor beelden:</span><span class="sxs-lookup"><span data-stu-id="1e795-228">Scalar examples:</span></span>

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

<span data-ttu-id="1e795-229">Als de invoer een verzameling is, retour neren de Opera tors de overeenkomende leden van die verzameling.</span><span class="sxs-lookup"><span data-stu-id="1e795-229">If the input is a collection, the operators return the matching members of that collection.</span></span>

<span data-ttu-id="1e795-230">Voor beelden van verzamelingen:</span><span class="sxs-lookup"><span data-stu-id="1e795-230">Collection examples:</span></span>

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

<span data-ttu-id="1e795-231">`-match` en `-notmatch` ondersteunen regex Capture-groepen.</span><span class="sxs-lookup"><span data-stu-id="1e795-231">`-match` and `-notmatch` support regex capture groups.</span></span> <span data-ttu-id="1e795-232">Telkens wanneer ze worden uitgevoerd, wordt de `$Matches` Automatische variabele overschreven.</span><span class="sxs-lookup"><span data-stu-id="1e795-232">Each time they run, they overwrite the `$Matches` automatic variable.</span></span> <span data-ttu-id="1e795-233">Wanneer `<input>` is een verzameling de `$Matches` variabele `$null` .</span><span class="sxs-lookup"><span data-stu-id="1e795-233">When `<input>` is a collection the `$Matches` variable is `$null`.</span></span> <span data-ttu-id="1e795-234">`$Matches` is een **hashtabel** die altijd een sleutel met de naam ' 0 ' heeft, waarin de volledige overeenkomst wordt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1e795-234">`$Matches` is a **Hashtable** that always has a key named '0', which stores the entire match.</span></span> <span data-ttu-id="1e795-235">Als de reguliere expressie opname groepen bevat, `$Matches` bevat de extra sleutels voor elke groep.</span><span class="sxs-lookup"><span data-stu-id="1e795-235">If the regular expression contains capture groups, the `$Matches` contains additional keys for each group.</span></span>

<span data-ttu-id="1e795-236">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-236">Example:</span></span>

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

<span data-ttu-id="1e795-237">Zie [about_Regular_Expressions](about_Regular_Expressions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e795-237">For details, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

## <a name="replacement-operator"></a><span data-ttu-id="1e795-238">Vervangings operator</span><span class="sxs-lookup"><span data-stu-id="1e795-238">Replacement operator</span></span>

### <a name="replacement-with-regular-expressions"></a><span data-ttu-id="1e795-239">Vervangen door reguliere expressies</span><span class="sxs-lookup"><span data-stu-id="1e795-239">Replacement with regular expressions</span></span>

<span data-ttu-id="1e795-240">Net als `-match` : de `-replace` operator gebruikt reguliere expressies om het opgegeven patroon te vinden.</span><span class="sxs-lookup"><span data-stu-id="1e795-240">Like `-match`, the `-replace` operator uses regular expressions to find the specified pattern.</span></span> <span data-ttu-id="1e795-241">Maar in tegens telling tot `-match` , worden de overeenkomsten vervangen door een andere opgegeven waarde.</span><span class="sxs-lookup"><span data-stu-id="1e795-241">But unlike `-match`, it replaces the matches with another specified value.</span></span>

<span data-ttu-id="1e795-242">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="1e795-242">Syntax:</span></span>

```
<input> -replace <regular-expression>, <substitute>
```

<span data-ttu-id="1e795-243">De operator vervangt alle of een deel van een waarde met de opgegeven waarde met reguliere expressies.</span><span class="sxs-lookup"><span data-stu-id="1e795-243">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="1e795-244">U kunt de operator gebruiken voor veel beheer taken, zoals het wijzigen van de naam van bestanden.</span><span class="sxs-lookup"><span data-stu-id="1e795-244">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="1e795-245">Met de volgende opdracht worden bijvoorbeeld de bestandsnaam extensies van alle bestanden gewijzigd `.txt` in `.log` :</span><span class="sxs-lookup"><span data-stu-id="1e795-245">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="1e795-246">Standaard `-replace` is de operator niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="1e795-246">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="1e795-247">Gebruik om het hoofdletter gevoelig te maken `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="1e795-247">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="1e795-248">Gebruik om het expliciet niet hoofdletter gevoelig te maken `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="1e795-248">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="1e795-249">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="1e795-249">Examples:</span></span>

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a><span data-ttu-id="1e795-250">Vervangingen van reguliere expressies</span><span class="sxs-lookup"><span data-stu-id="1e795-250">Regular expressions substitutions</span></span>

<span data-ttu-id="1e795-251">Het is ook mogelijk om reguliere expressies te gebruiken om tekst dynamisch te vervangen met opname groepen en vervangingen.</span><span class="sxs-lookup"><span data-stu-id="1e795-251">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="1e795-252">Er kan in de teken reeks naar vastleg groepen worden verwezen `<substitute>` met het `$` teken voor het dollar teken () voor de groeps-id.</span><span class="sxs-lookup"><span data-stu-id="1e795-252">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="1e795-253">In het volgende voor beeld `-replace` accepteert de operator een gebruikers naam in de vorm van `DomainName\Username` en wordt geconverteerd naar de `Username@DomainName` indeling:</span><span class="sxs-lookup"><span data-stu-id="1e795-253">In the following example, the `-replace` operator accepts a username in the form of `DomainName\Username` and converts to the `Username@DomainName` format:</span></span>

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> <span data-ttu-id="1e795-254">Het `$` teken heeft syntatic-rollen in Power shell en reguliere expressies:</span><span class="sxs-lookup"><span data-stu-id="1e795-254">The `$` character has syntatic roles in both PowerShell and regular expressions:</span></span>
>
> - <span data-ttu-id="1e795-255">Tussen dubbele aanhalings tekens in Power shell worden variabelen aangeduid en fungeert als een operator voor subexpressie.</span><span class="sxs-lookup"><span data-stu-id="1e795-255">In PowerShell, between double quotation marks, it designates variables and acts as a subexpression operator.</span></span>
> - <span data-ttu-id="1e795-256">In regex-Zoek reeksen geeft het einde van de regel aan</span><span class="sxs-lookup"><span data-stu-id="1e795-256">In Regex search strings, it denotes end of the line</span></span>
> - <span data-ttu-id="1e795-257">In regex-vervangings teken reeksen worden vastgelegde groepen aangeduid. Zorg ervoor dat u de reguliere expressies tussen enkele aanhalings tekens plaatst of een apostroffen-teken () voor de hand hebt ingevoegd `` ` `` .</span><span class="sxs-lookup"><span data-stu-id="1e795-257">In Regex substitution strings, it denotes captured groups.Be sure to either put your regular expressions between single quotation marks or insert a backtick (`` ` ``) character before them.</span></span>

<span data-ttu-id="1e795-258">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-258">For example:</span></span>

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

<span data-ttu-id="1e795-259">`$$` in regex duidt een letterlijke teken reeks aan `$` .</span><span class="sxs-lookup"><span data-stu-id="1e795-259">`$$` in Regex denotes a literal `$`.</span></span> <span data-ttu-id="1e795-260">Hiermee wordt `$$` in de vervangings teken reeks een letterlijke waarde `$` in de resulterende vervanging ingevoegd.</span><span class="sxs-lookup"><span data-stu-id="1e795-260">This `$$` in the substitution string to include a literal `$` in the resulting replacement.</span></span> <span data-ttu-id="1e795-261">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-261">For example:</span></span>

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

<span data-ttu-id="1e795-262">Zie [about_Regular_Expressions](about_Regular_Expressions.md) en [vervangingen in reguliere expressies][4]voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1e795-262">To learn more, see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions][4].</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="1e795-263">Vervangen in een verzameling</span><span class="sxs-lookup"><span data-stu-id="1e795-263">Substituting in a collection</span></span>

<span data-ttu-id="1e795-264">Wanneer de `<input>` naar de `-replace` operator een verzameling is, past Power shell de vervanging toe op elke waarde in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="1e795-264">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="1e795-265">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-265">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a><span data-ttu-id="1e795-266">Vervanging met een script blok</span><span class="sxs-lookup"><span data-stu-id="1e795-266">Replacement with a script block</span></span>

<span data-ttu-id="1e795-267">In Power shell 6 en hoger `-replace` accepteert de operator ook een script blok dat de vervanging uitvoert.</span><span class="sxs-lookup"><span data-stu-id="1e795-267">In PowerShell 6 and later, the `-replace` operator also accepts a script block that performs the replacement.</span></span> <span data-ttu-id="1e795-268">Het script blok wordt één keer voor elke overeenkomst uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1e795-268">The script block runs once for every match.</span></span>

<span data-ttu-id="1e795-269">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="1e795-269">Syntax:</span></span>

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

<span data-ttu-id="1e795-270">Gebruik in het-script blok de `$_` Automatische variabele voor toegang tot de invoer tekst die wordt vervangen en andere nuttige informatie.</span><span class="sxs-lookup"><span data-stu-id="1e795-270">Within the script block, use the `$_` automatic variable to access the input text being replaced and other useful information.</span></span> <span data-ttu-id="1e795-271">Het klassen type van deze variabele is [System. Text. RegularExpressions. match][2].</span><span class="sxs-lookup"><span data-stu-id="1e795-271">This variable's class type is [System.Text.RegularExpressions.Match][2].</span></span>

<span data-ttu-id="1e795-272">In het volgende voor beeld wordt elke reeks van drie cijfers vervangen door de teken equivalenten.</span><span class="sxs-lookup"><span data-stu-id="1e795-272">The following example replaces each sequence of three digits with the character equivalents.</span></span> <span data-ttu-id="1e795-273">Het script blok wordt uitgevoerd voor elke set met drie cijfers die moeten worden vervangen.</span><span class="sxs-lookup"><span data-stu-id="1e795-273">The script block runs for each set of three digits that needs to be replaced.</span></span>

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a><span data-ttu-id="1e795-274">Containment-Opera tors</span><span class="sxs-lookup"><span data-stu-id="1e795-274">Containment operators</span></span>

<span data-ttu-id="1e795-275">De containment-Opera tors ( `-contains` ,, `-notcontains` `-in` en `-notin` ) zijn vergelijkbaar met de gelijkheids operatoren, behalve dat ze altijd een **Booleaanse** waarde Retour neren, zelfs wanneer de invoer een verzameling is.</span><span class="sxs-lookup"><span data-stu-id="1e795-275">The containment operators (`-contains`, `-notcontains`, `-in`, and `-notin`) are similar to the equality operators, except that they always return a **Boolean** value, even when the input is a collection.</span></span> <span data-ttu-id="1e795-276">Deze opera tors worden niet meer vergeleken wanneer ze de eerste overeenkomst detecteren, terwijl de gelijkheids operatoren alle invoer leden evalueren.</span><span class="sxs-lookup"><span data-stu-id="1e795-276">These operators stop comparing as soon as they detect the first match, whereas the equality operators evaluate all input members.</span></span> <span data-ttu-id="1e795-277">In een zeer grote verzameling retour neren deze opera tors sneller dan de gelijkheids operators.</span><span class="sxs-lookup"><span data-stu-id="1e795-277">In a very large collection, these operators return quicker than the equality operators.</span></span>

<span data-ttu-id="1e795-278">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="1e795-278">Syntax:</span></span>

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a><span data-ttu-id="1e795-279">-bevat en-notcontains</span><span class="sxs-lookup"><span data-stu-id="1e795-279">-contains and -notcontains</span></span>

<span data-ttu-id="1e795-280">Deze opera tors geven aan of een set een bepaald element bevat.</span><span class="sxs-lookup"><span data-stu-id="1e795-280">These operators tell whether a set includes a certain element.</span></span> <span data-ttu-id="1e795-281">`-contains` Retourneert waar wanneer de rechter kant (test object) overeenkomt met een van de elementen in de set.</span><span class="sxs-lookup"><span data-stu-id="1e795-281">`-contains` returns True when the right-hand side (test object) matches one of the elements in the set.</span></span> <span data-ttu-id="1e795-282">`-notcontains` in plaats daarvan wordt false geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e795-282">`-notcontains` returns False instead.</span></span> <span data-ttu-id="1e795-283">Wanneer het test object een verzameling is, gebruiken deze opera tors referentie gelijkheid, dat wil zeggen dat ze controleren of een van de set-elementen hetzelfde exemplaar van het test object is.</span><span class="sxs-lookup"><span data-stu-id="1e795-283">When the test object is a collection, these operators use reference equality, i.e. they check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="1e795-284">Voorbeelden:</span><span class="sxs-lookup"><span data-stu-id="1e795-284">Examples:</span></span>

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

<span data-ttu-id="1e795-285">Complexere voor beelden:</span><span class="sxs-lookup"><span data-stu-id="1e795-285">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a><span data-ttu-id="1e795-286">-in en-notin</span><span class="sxs-lookup"><span data-stu-id="1e795-286">-in and -notin</span></span>

<span data-ttu-id="1e795-287">De `-in` `notin` Opera tors en zijn geïntroduceerd in Power Shell 3 als de syntaxis van de `contains` `-notcontain` Opera tors van en.</span><span class="sxs-lookup"><span data-stu-id="1e795-287">The `-in` and -`notin` operators were introduced in PowerShell 3 as the syntactic reverse of the of `contains` and `-notcontain` operators.</span></span> <span data-ttu-id="1e795-288">`-in` retourneert **waar** wanneer de linkerkant `<test-object>` overeenkomt met een van de elementen in de set.</span><span class="sxs-lookup"><span data-stu-id="1e795-288">`-in` returns **True** when the left-hand side `<test-object>` matches one of the elements in the set.</span></span> <span data-ttu-id="1e795-289">`-notin` in plaats daarvan wordt **False** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1e795-289">`-notin` returns **False** instead.</span></span> <span data-ttu-id="1e795-290">Wanneer het test object een set is, gebruiken deze opera tors referentie gelijkheid om te controleren of een van de set-elementen hetzelfde exemplaar van het test object is.</span><span class="sxs-lookup"><span data-stu-id="1e795-290">When the test object is a set, these operators use reference equality to check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="1e795-291">De volgende voor beelden doen hetzelfde als de voor beelden voor `-contain` en `-notcontain` doen, maar ze zijn wel geschreven met `-in` en `-notin` in plaats daarvan.</span><span class="sxs-lookup"><span data-stu-id="1e795-291">The following examples do the same thing that the examples for `-contain` and `-notcontain` do, but they are written with `-in` and `-notin` instead.</span></span>

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

<span data-ttu-id="1e795-292">Complexere voor beelden:</span><span class="sxs-lookup"><span data-stu-id="1e795-292">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a><span data-ttu-id="1e795-293">Type vergelijking</span><span class="sxs-lookup"><span data-stu-id="1e795-293">Type comparison</span></span>

<span data-ttu-id="1e795-294">De type vergelijkings operators ( `-is` en `-isnot` ) worden gebruikt om te bepalen of een object een specifiek type is.</span><span class="sxs-lookup"><span data-stu-id="1e795-294">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

<span data-ttu-id="1e795-295">Syntaxis:</span><span class="sxs-lookup"><span data-stu-id="1e795-295">Syntax:</span></span>

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

<span data-ttu-id="1e795-296">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e795-296">Example:</span></span>

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a><span data-ttu-id="1e795-297">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="1e795-297">SEE ALSO</span></span>

- [<span data-ttu-id="1e795-298">about_Operators</span><span class="sxs-lookup"><span data-stu-id="1e795-298">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="1e795-299">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="1e795-299">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="1e795-300">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="1e795-300">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="1e795-301">Compare-object</span><span class="sxs-lookup"><span data-stu-id="1e795-301">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="1e795-302">Foreach-object</span><span class="sxs-lookup"><span data-stu-id="1e795-302">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="1e795-303">Where-object</span><span class="sxs-lookup"><span data-stu-id="1e795-303">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
