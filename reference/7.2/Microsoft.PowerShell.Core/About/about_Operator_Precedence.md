---
description: Een lijst met de Power shell-Opera tors in volg orde van prioriteit.
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: d4031a9d9a67340470d5418a9c2d3e33c5caed13
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705647"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="ebba4-103">Prioriteit van Opera tors</span><span class="sxs-lookup"><span data-stu-id="ebba4-103">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="ebba4-104">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ebba4-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ebba4-105">Een lijst met de Power shell-Opera tors in volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="ebba4-105">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="ebba4-106">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="ebba4-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="ebba4-107">Met Power shell-Opera tors kunt u eenvoudige, maar krachtige expressies maken.</span><span class="sxs-lookup"><span data-stu-id="ebba4-107">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="ebba4-108">In dit onderwerp vindt u de Opera tors in volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="ebba4-108">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="ebba4-109">Volg orde van prioriteit is de volg orde waarin de Opera tors door Power shell worden geëvalueerd wanneer meerdere opera tors in dezelfde expressie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ebba4-109">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="ebba4-110">Wanneer Opera tors dezelfde prioriteit hebben, wordt deze door Power shell geëvalueerd van links naar rechts, zoals ze in de expressie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="ebba4-110">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="ebba4-111">De uitzonde ringen zijn de toewijzings operatoren, de cast-Opera tors en de negatie Opera tors ( `!` , `-not` , `-bnot` ), die worden geëvalueerd van rechts naar links.</span><span class="sxs-lookup"><span data-stu-id="ebba4-111">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="ebba4-112">U kunt bijlagen, zoals haakjes, gebruiken om de standaard prioriteits volgorde te overschrijven en Power shell af te dwingen om het Inge sloten deel van een expressie te evalueren vóór een niet-Inge sloten gedeelte.</span><span class="sxs-lookup"><span data-stu-id="ebba4-112">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="ebba4-113">In de volgende lijst worden Opera tors weer gegeven in de volg orde waarin ze worden geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="ebba4-113">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="ebba4-114">Opera tors op dezelfde regel, of in dezelfde groep, hebben dezelfde prioriteit.</span><span class="sxs-lookup"><span data-stu-id="ebba4-114">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="ebba4-115">De kolom operator geeft een lijst van de Opera tors.</span><span class="sxs-lookup"><span data-stu-id="ebba4-115">The Operator column lists the operators.</span></span> <span data-ttu-id="ebba4-116">In de kolom referentie wordt het Help-onderwerp van Power shell weer gegeven waarin de operator wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="ebba4-116">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="ebba4-117">Als u het onderwerp wilt weer geven, typt u `get-help <topic-name>` .</span><span class="sxs-lookup"><span data-stu-id="ebba4-117">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="ebba4-118">AND</span><span class="sxs-lookup"><span data-stu-id="ebba4-118">OPERATOR</span></span>         |           <span data-ttu-id="ebba4-119">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="ebba4-119">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | <span data-ttu-id="ebba4-120">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-120">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-121">`. ?.` (leden toegang)</span><span class="sxs-lookup"><span data-stu-id="ebba4-121">`. ?.` (member access)</span></span>   | <span data-ttu-id="ebba4-122">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-122">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-123">`::` storing</span><span class="sxs-lookup"><span data-stu-id="ebba4-123">`::` (static)</span></span>            | <span data-ttu-id="ebba4-124">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-124">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-125">`[0] ?[0]` (operator index)</span><span class="sxs-lookup"><span data-stu-id="ebba4-125">`[0] ?[0]` (index operator)</span></span> | <span data-ttu-id="ebba4-126">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-126">[about_Operators][]</span></span>         |
| <span data-ttu-id="ebba4-127">`[int]` (cast-Opera tors)</span><span class="sxs-lookup"><span data-stu-id="ebba4-127">`[int]` (cast operators)</span></span> | <span data-ttu-id="ebba4-128">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-128">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-129">`-split` monadische</span><span class="sxs-lookup"><span data-stu-id="ebba4-129">`-split` (unary)</span></span>         | <span data-ttu-id="ebba4-130">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-130">[about_Split][]</span></span>                |
| <span data-ttu-id="ebba4-131">`-join` monadische</span><span class="sxs-lookup"><span data-stu-id="ebba4-131">`-join` (unary)</span></span>          | <span data-ttu-id="ebba4-132">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-132">[about_Join][]</span></span>                 |
| <span data-ttu-id="ebba4-133">`,` (komma operator)</span><span class="sxs-lookup"><span data-stu-id="ebba4-133">`,` (comma operator)</span></span>     | <span data-ttu-id="ebba4-134">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-134">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="ebba4-135">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-135">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="ebba4-136">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-136">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="ebba4-137">`..` (bereik operator)</span><span class="sxs-lookup"><span data-stu-id="ebba4-137">`..` (range operator)</span></span>    | <span data-ttu-id="ebba4-138">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-138">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-139">`-f` (operator voor indeling)</span><span class="sxs-lookup"><span data-stu-id="ebba4-139">`-f` (format operator)</span></span>   | <span data-ttu-id="ebba4-140">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-140">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-141">`-` (Unair/negatief)</span><span class="sxs-lookup"><span data-stu-id="ebba4-141">`-` (unary/negative)</span></span>     | <span data-ttu-id="ebba4-142">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-142">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="ebba4-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-143">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="ebba4-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-144">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="ebba4-145">De volgende groep Opera tors hebben dezelfde prioriteit.</span><span class="sxs-lookup"><span data-stu-id="ebba4-145">The following group of operators have equal precedence.</span></span> <span data-ttu-id="ebba4-146">Hun hoofdletter gevoelige en expliciet hoofdletter gevoelig varianten hebben dezelfde prioriteit.</span><span class="sxs-lookup"><span data-stu-id="ebba4-146">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="ebba4-147">AND</span><span class="sxs-lookup"><span data-stu-id="ebba4-147">OPERATOR</span></span>          |           <span data-ttu-id="ebba4-148">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="ebba4-148">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="ebba4-149">`-split` waarde</span><span class="sxs-lookup"><span data-stu-id="ebba4-149">`-split` (binary)</span></span>         | <span data-ttu-id="ebba4-150">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-150">[about_Split][]</span></span>                |
| <span data-ttu-id="ebba4-151">`-join` waarde</span><span class="sxs-lookup"><span data-stu-id="ebba4-151">`-join` (binary)</span></span>          | <span data-ttu-id="ebba4-152">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-152">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="ebba4-153">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-153">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="ebba4-154">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-154">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="ebba4-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-155">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="ebba4-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-156">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="ebba4-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-157">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="ebba4-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-158">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="ebba4-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-159">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="ebba4-160">De lijst wordt hier weer gegeven met de volgende Opera tors in volg orde van prioriteit:</span><span class="sxs-lookup"><span data-stu-id="ebba4-160">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="ebba4-161">AND</span><span class="sxs-lookup"><span data-stu-id="ebba4-161">OPERATOR</span></span>                 |           <span data-ttu-id="ebba4-162">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="ebba4-162">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="ebba4-163">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-163">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="ebba4-164">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-164">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="ebba4-165">De volgende items zijn niet waar Opera tors.</span><span class="sxs-lookup"><span data-stu-id="ebba4-165">The following items are not true operators.</span></span> <span data-ttu-id="ebba4-166">Ze maken deel uit van de opdracht syntaxis van Power shell, geen expressie syntaxis.</span><span class="sxs-lookup"><span data-stu-id="ebba4-166">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="ebba4-167">De toewijzing is altijd de laatste actie die er gebeurt.</span><span class="sxs-lookup"><span data-stu-id="ebba4-167">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="ebba4-168">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="ebba4-168">SYNTAX</span></span>                   |           <span data-ttu-id="ebba4-169">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="ebba4-169">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="ebba4-170">`.` (punt-bron)</span><span class="sxs-lookup"><span data-stu-id="ebba4-170">`.` (dot-source)</span></span>                        | <span data-ttu-id="ebba4-171">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-171">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-172">`&` telefoon</span><span class="sxs-lookup"><span data-stu-id="ebba4-172">`&` (call)</span></span>                              | <span data-ttu-id="ebba4-173">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-173">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-174">`? <if-true> : <if-false>` (Ternaire operator)</span><span class="sxs-lookup"><span data-stu-id="ebba4-174">`? <if-true> : <if-false>` (Ternary operator)</span></span> | <span data-ttu-id="ebba4-175">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-175">[about_Operators][]</span></span>      |
| <span data-ttu-id="ebba4-176">`??` (operator null-remeern)</span><span class="sxs-lookup"><span data-stu-id="ebba4-176">`??` (null-coalese operator)</span></span>            | <span data-ttu-id="ebba4-177">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-177">[about_Operators][]</span></span>            |
| <span data-ttu-id="ebba4-178"><code>&#124;</code> (pijplijn operator)</span><span class="sxs-lookup"><span data-stu-id="ebba4-178"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="ebba4-179">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-179">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="ebba4-180">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-180">[about_Redirection][]</span></span>          |
| <span data-ttu-id="ebba4-181"><code>&& &#124;&#124;</code> (pijplijn keten operators)</span><span class="sxs-lookup"><span data-stu-id="ebba4-181"><code>&& &#124;&#124;</code> (pipeline chain operators)</span></span> | <span data-ttu-id="ebba4-182">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-182">[about_Operators][]</span></span> |
| `= += -= *= /= %= ??=`                  | <span data-ttu-id="ebba4-183">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-183">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="ebba4-184">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="ebba4-184">EXAMPLES</span></span>

<span data-ttu-id="ebba4-185">Met de volgende twee opdrachten worden de reken kundige Opera tors en het effect van het gebruik van haakjes weer gegeven om Power shell te dwingen het Inge sloten deel van de expressie eerst te evalueren.</span><span class="sxs-lookup"><span data-stu-id="ebba4-185">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="ebba4-186">In het volgende voor beeld worden de alleen-lezen tekst bestanden opgehaald uit de lokale map en opgeslagen in de `$read_only` variabele.</span><span class="sxs-lookup"><span data-stu-id="ebba4-186">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="ebba4-187">Dit komt overeen met het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="ebba4-187">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="ebba4-188">Omdat de pijplijn operator ( `|` ) een hogere prioriteit heeft dan de toewijzings operator ( `=` ), worden de bestanden die de `Get-ChildItem` cmdlet krijgt, naar de `Where-Object` cmdlet verzonden voor het filteren voordat ze aan de `$read_only` variabele worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="ebba4-188">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="ebba4-189">In het volgende voor beeld ziet u dat de operator index voor rang krijgt boven de cast-operator.</span><span class="sxs-lookup"><span data-stu-id="ebba4-189">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="ebba4-190">Met deze expressie maakt u een matrix van drie teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="ebba4-190">This expression creates an array of three strings.</span></span> <span data-ttu-id="ebba4-191">Vervolgens wordt de index operator met de waarde 0 gebruikt om het eerste object in de matrix te selecteren. Dit is de eerste teken reeks.</span><span class="sxs-lookup"><span data-stu-id="ebba4-191">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="ebba4-192">Ten slotte wordt het geselecteerde object omgezet in een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="ebba4-192">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="ebba4-193">In dit geval heeft de cast geen effect.</span><span class="sxs-lookup"><span data-stu-id="ebba4-193">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="ebba4-194">Deze expressie gebruikt haakjes om de conversie bewerking af te dwingen vóór de index selectie.</span><span class="sxs-lookup"><span data-stu-id="ebba4-194">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="ebba4-195">Als gevolg hiervan wordt de gehele matrix geconverteerd als een (enkele) teken reeks.</span><span class="sxs-lookup"><span data-stu-id="ebba4-195">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="ebba4-196">Vervolgens selecteert de operator index het eerste item in de teken reeks matrix. Dit is het eerste teken.</span><span class="sxs-lookup"><span data-stu-id="ebba4-196">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="ebba4-197">In het volgende voor beeld, omdat de `-gt` operator (groter dan) een hogere prioriteit heeft dan de `-and` operator (logische en), is het resultaat van de expressie onwaar.</span><span class="sxs-lookup"><span data-stu-id="ebba4-197">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="ebba4-198">Deze is gelijk aan de volgende expressie.</span><span class="sxs-lookup"><span data-stu-id="ebba4-198">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="ebba4-199">Als de operator-en een hogere prioriteit heeft, zou het antwoord de waarde TRUE hebben.</span><span class="sxs-lookup"><span data-stu-id="ebba4-199">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="ebba4-200">In dit voor beeld ziet u echter een belang rijk principe voor het beheren van de prioriteit van Opera tors.</span><span class="sxs-lookup"><span data-stu-id="ebba4-200">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="ebba4-201">Wanneer een expressie moeilijk is te interpreteren door anderen, gebruik dan haakjes om de evaluatie volgorde af te dwingen, zelfs wanneer de standaard operator prioriteit wordt afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="ebba4-201">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="ebba4-202">De haakjes maken uw bedoelingen duidelijk voor mensen die uw scripts lezen en onderhouden.</span><span class="sxs-lookup"><span data-stu-id="ebba4-202">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebba4-203">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="ebba4-203">SEE ALSO</span></span>

<span data-ttu-id="ebba4-204">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-204">[about_Operators][]</span></span>

<span data-ttu-id="ebba4-205">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-205">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="ebba4-206">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-206">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="ebba4-207">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-207">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="ebba4-208">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-208">[about_Join][]</span></span>

<span data-ttu-id="ebba4-209">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-209">[about_Redirection][]</span></span>

<span data-ttu-id="ebba4-210">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-210">[about_Scopes][]</span></span>

<span data-ttu-id="ebba4-211">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-211">[about_Split][]</span></span>

<span data-ttu-id="ebba4-212">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="ebba4-212">[about_Type_Operators][]</span></span>

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
