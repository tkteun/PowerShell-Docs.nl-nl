---
description: Een lijst met de Power shell-Opera tors in volg orde van prioriteit.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 88a24c04d3d24d1df1b93ab2eefef401063252a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252295"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="c5f54-104">Prioriteit van Opera tors</span><span class="sxs-lookup"><span data-stu-id="c5f54-104">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="c5f54-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c5f54-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c5f54-106">Een lijst met de Power shell-Opera tors in volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="c5f54-106">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="c5f54-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c5f54-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c5f54-108">Met Power shell-Opera tors kunt u eenvoudige, maar krachtige expressies maken.</span><span class="sxs-lookup"><span data-stu-id="c5f54-108">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="c5f54-109">In dit onderwerp vindt u de Opera tors in volg orde van prioriteit.</span><span class="sxs-lookup"><span data-stu-id="c5f54-109">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="c5f54-110">Volg orde van prioriteit is de volg orde waarin de Opera tors door Power shell worden geëvalueerd wanneer meerdere opera tors in dezelfde expressie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c5f54-110">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="c5f54-111">Wanneer Opera tors dezelfde prioriteit hebben, wordt deze door Power shell geëvalueerd van links naar rechts, zoals ze in de expressie worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="c5f54-111">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="c5f54-112">De uitzonde ringen zijn de toewijzings operatoren, de cast-Opera tors en de negatie Opera tors ( `!` , `-not` , `-bnot` ), die worden geëvalueerd van rechts naar links.</span><span class="sxs-lookup"><span data-stu-id="c5f54-112">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="c5f54-113">U kunt bijlagen, zoals haakjes, gebruiken om de standaard prioriteits volgorde te overschrijven en Power shell af te dwingen om het Inge sloten deel van een expressie te evalueren vóór een niet-Inge sloten gedeelte.</span><span class="sxs-lookup"><span data-stu-id="c5f54-113">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="c5f54-114">In de volgende lijst worden Opera tors weer gegeven in de volg orde waarin ze worden geëvalueerd.</span><span class="sxs-lookup"><span data-stu-id="c5f54-114">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="c5f54-115">Opera tors op dezelfde regel, of in dezelfde groep, hebben dezelfde prioriteit.</span><span class="sxs-lookup"><span data-stu-id="c5f54-115">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="c5f54-116">De kolom operator geeft een lijst van de Opera tors.</span><span class="sxs-lookup"><span data-stu-id="c5f54-116">The Operator column lists the operators.</span></span> <span data-ttu-id="c5f54-117">In de kolom referentie wordt het Help-onderwerp van Power shell weer gegeven waarin de operator wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="c5f54-117">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="c5f54-118">Als u het onderwerp wilt weer geven, typt u `get-help <topic-name>` .</span><span class="sxs-lookup"><span data-stu-id="c5f54-118">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="c5f54-119">AND</span><span class="sxs-lookup"><span data-stu-id="c5f54-119">OPERATOR</span></span>         |           <span data-ttu-id="c5f54-120">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="c5f54-120">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() ()`             | <span data-ttu-id="c5f54-121">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-121">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-122">`.` (leden toegang)</span><span class="sxs-lookup"><span data-stu-id="c5f54-122">`.` (member access)</span></span>      | <span data-ttu-id="c5f54-123">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-123">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-124">`::` storing</span><span class="sxs-lookup"><span data-stu-id="c5f54-124">`::` (static)</span></span>            | <span data-ttu-id="c5f54-125">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-125">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-126">`[0]` (operator index)</span><span class="sxs-lookup"><span data-stu-id="c5f54-126">`[0]` (index operator)</span></span>   | <span data-ttu-id="c5f54-127">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-127">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-128">`[int]` (cast-Opera tors)</span><span class="sxs-lookup"><span data-stu-id="c5f54-128">`[int]` (cast operators)</span></span> | <span data-ttu-id="c5f54-129">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-129">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-130">`-split` monadische</span><span class="sxs-lookup"><span data-stu-id="c5f54-130">`-split` (unary)</span></span>         | <span data-ttu-id="c5f54-131">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-131">[about_Split][]</span></span>                |
| <span data-ttu-id="c5f54-132">`-join` monadische</span><span class="sxs-lookup"><span data-stu-id="c5f54-132">`-join` (unary)</span></span>          | <span data-ttu-id="c5f54-133">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-133">[about_Join][]</span></span>                 |
| <span data-ttu-id="c5f54-134">`,` (komma operator)</span><span class="sxs-lookup"><span data-stu-id="c5f54-134">`,` (comma operator)</span></span>     | <span data-ttu-id="c5f54-135">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-135">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="c5f54-136">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-136">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="c5f54-137">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-137">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="c5f54-138">`..` (bereik operator)</span><span class="sxs-lookup"><span data-stu-id="c5f54-138">`..` (range operator)</span></span>    | <span data-ttu-id="c5f54-139">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-139">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-140">`-f` (operator voor indeling)</span><span class="sxs-lookup"><span data-stu-id="c5f54-140">`-f` (format operator)</span></span>   | <span data-ttu-id="c5f54-141">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-141">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-142">`-` (Unair/negatief)</span><span class="sxs-lookup"><span data-stu-id="c5f54-142">`-` (unary/negative)</span></span>     | <span data-ttu-id="c5f54-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-143">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="c5f54-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-144">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="c5f54-145">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-145">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="c5f54-146">De volgende groep Opera tors hebben dezelfde prioriteit.</span><span class="sxs-lookup"><span data-stu-id="c5f54-146">The following group of operators have equal precedence.</span></span> <span data-ttu-id="c5f54-147">Hun hoofdletter gevoelige en expliciet hoofdletter gevoelig varianten hebben dezelfde prioriteit.</span><span class="sxs-lookup"><span data-stu-id="c5f54-147">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="c5f54-148">AND</span><span class="sxs-lookup"><span data-stu-id="c5f54-148">OPERATOR</span></span>          |           <span data-ttu-id="c5f54-149">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="c5f54-149">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="c5f54-150">`-split` waarde</span><span class="sxs-lookup"><span data-stu-id="c5f54-150">`-split` (binary)</span></span>         | <span data-ttu-id="c5f54-151">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-151">[about_Split][]</span></span>                |
| <span data-ttu-id="c5f54-152">`-join` waarde</span><span class="sxs-lookup"><span data-stu-id="c5f54-152">`-join` (binary)</span></span>          | <span data-ttu-id="c5f54-153">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-153">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="c5f54-154">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-154">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="c5f54-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-155">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="c5f54-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-156">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="c5f54-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-157">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="c5f54-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-158">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="c5f54-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-159">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="c5f54-160">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-160">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="c5f54-161">De lijst wordt hier weer gegeven met de volgende Opera tors in volg orde van prioriteit:</span><span class="sxs-lookup"><span data-stu-id="c5f54-161">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="c5f54-162">AND</span><span class="sxs-lookup"><span data-stu-id="c5f54-162">OPERATOR</span></span>                 |           <span data-ttu-id="c5f54-163">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="c5f54-163">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="c5f54-164">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-164">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="c5f54-165">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-165">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="c5f54-166">De volgende items zijn niet waar Opera tors.</span><span class="sxs-lookup"><span data-stu-id="c5f54-166">The following items are not true operators.</span></span> <span data-ttu-id="c5f54-167">Ze maken deel uit van de opdracht syntaxis van Power shell, geen expressie syntaxis.</span><span class="sxs-lookup"><span data-stu-id="c5f54-167">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="c5f54-168">De toewijzing is altijd de laatste actie die er gebeurt.</span><span class="sxs-lookup"><span data-stu-id="c5f54-168">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="c5f54-169">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="c5f54-169">SYNTAX</span></span>                   |           <span data-ttu-id="c5f54-170">REFERENTIELAAG</span><span class="sxs-lookup"><span data-stu-id="c5f54-170">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="c5f54-171">`.` (punt-bron)</span><span class="sxs-lookup"><span data-stu-id="c5f54-171">`.` (dot-source)</span></span>                        | <span data-ttu-id="c5f54-172">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-172">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-173">`&` telefoon</span><span class="sxs-lookup"><span data-stu-id="c5f54-173">`&` (call)</span></span>                              | <span data-ttu-id="c5f54-174">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-174">[about_Operators][]</span></span>            |
| <span data-ttu-id="c5f54-175"><code>&#124;</code> (pijplijn operator)</span><span class="sxs-lookup"><span data-stu-id="c5f54-175"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="c5f54-176">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-176">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="c5f54-177">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-177">[about_Redirection][]</span></span>          |
| `= += -= *= /= %=`                      | <span data-ttu-id="c5f54-178">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-178">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="c5f54-179">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="c5f54-179">EXAMPLES</span></span>

<span data-ttu-id="c5f54-180">Met de volgende twee opdrachten worden de reken kundige Opera tors en het effect van het gebruik van haakjes weer gegeven om Power shell te dwingen het Inge sloten deel van de expressie eerst te evalueren.</span><span class="sxs-lookup"><span data-stu-id="c5f54-180">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="c5f54-181">In het volgende voor beeld worden de alleen-lezen tekst bestanden opgehaald uit de lokale map en opgeslagen in de `$read_only` variabele.</span><span class="sxs-lookup"><span data-stu-id="c5f54-181">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="c5f54-182">Dit komt overeen met het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="c5f54-182">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="c5f54-183">Omdat de pijplijn operator ( `|` ) een hogere prioriteit heeft dan de toewijzings operator ( `=` ), worden de bestanden die de `Get-ChildItem` cmdlet krijgt, naar de `Where-Object` cmdlet verzonden voor het filteren voordat ze aan de `$read_only` variabele worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="c5f54-183">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="c5f54-184">In het volgende voor beeld ziet u dat de operator index voor rang krijgt boven de cast-operator.</span><span class="sxs-lookup"><span data-stu-id="c5f54-184">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="c5f54-185">Met deze expressie maakt u een matrix van drie teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="c5f54-185">This expression creates an array of three strings.</span></span> <span data-ttu-id="c5f54-186">Vervolgens wordt de index operator met de waarde 0 gebruikt om het eerste object in de matrix te selecteren. Dit is de eerste teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c5f54-186">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="c5f54-187">Ten slotte wordt het geselecteerde object omgezet in een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c5f54-187">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="c5f54-188">In dit geval heeft de cast geen effect.</span><span class="sxs-lookup"><span data-stu-id="c5f54-188">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="c5f54-189">Deze expressie gebruikt haakjes om de conversie bewerking af te dwingen vóór de index selectie.</span><span class="sxs-lookup"><span data-stu-id="c5f54-189">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="c5f54-190">Als gevolg hiervan wordt de gehele matrix geconverteerd als een (enkele) teken reeks.</span><span class="sxs-lookup"><span data-stu-id="c5f54-190">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="c5f54-191">Vervolgens selecteert de operator index het eerste item in de teken reeks matrix. Dit is het eerste teken.</span><span class="sxs-lookup"><span data-stu-id="c5f54-191">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="c5f54-192">In het volgende voor beeld, omdat de `-gt` operator (groter dan) een hogere prioriteit heeft dan de `-and` operator (logische en), is het resultaat van de expressie onwaar.</span><span class="sxs-lookup"><span data-stu-id="c5f54-192">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="c5f54-193">Deze is gelijk aan de volgende expressie.</span><span class="sxs-lookup"><span data-stu-id="c5f54-193">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="c5f54-194">Als de operator-en een hogere prioriteit heeft, zou het antwoord de waarde TRUE hebben.</span><span class="sxs-lookup"><span data-stu-id="c5f54-194">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="c5f54-195">In dit voor beeld ziet u echter een belang rijk principe voor het beheren van de prioriteit van Opera tors.</span><span class="sxs-lookup"><span data-stu-id="c5f54-195">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="c5f54-196">Wanneer een expressie moeilijk is te interpreteren door anderen, gebruik dan haakjes om de evaluatie volgorde af te dwingen, zelfs wanneer de standaard operator prioriteit wordt afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="c5f54-196">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="c5f54-197">De haakjes maken uw bedoelingen duidelijk voor mensen die uw scripts lezen en onderhouden.</span><span class="sxs-lookup"><span data-stu-id="c5f54-197">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5f54-198">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="c5f54-198">SEE ALSO</span></span>

<span data-ttu-id="c5f54-199">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-199">[about_Operators][]</span></span>

<span data-ttu-id="c5f54-200">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-200">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="c5f54-201">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-201">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="c5f54-202">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-202">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="c5f54-203">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-203">[about_Join][]</span></span>

<span data-ttu-id="c5f54-204">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-204">[about_Redirection][]</span></span>

<span data-ttu-id="c5f54-205">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-205">[about_Scopes][]</span></span>

<span data-ttu-id="c5f54-206">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-206">[about_Split][]</span></span>

<span data-ttu-id="c5f54-207">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="c5f54-207">[about_Type_Operators][]</span></span>

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