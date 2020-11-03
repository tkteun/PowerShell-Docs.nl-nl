---
description: Een lijst met de Power shell-Opera tors in volg orde van prioriteit.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 0510d63eec199c4dbc23d562c6fb64f296d42b9f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252844"
---
# <a name="about-operator-precedence"></a>Prioriteit van Opera tors

## <a name="short-description"></a>KORTE BESCHRIJVING
Een lijst met de Power shell-Opera tors in volg orde van prioriteit.

## <a name="long-description"></a>LANGE BESCHRIJVING

Met Power shell-Opera tors kunt u eenvoudige, maar krachtige expressies maken. In dit onderwerp vindt u de Opera tors in volg orde van prioriteit. Volg orde van prioriteit is de volg orde waarin de Opera tors door Power shell worden geëvalueerd wanneer meerdere opera tors in dezelfde expressie worden weer gegeven.

Wanneer Opera tors dezelfde prioriteit hebben, wordt deze door Power shell geëvalueerd van links naar rechts, zoals ze in de expressie worden weer gegeven. De uitzonde ringen zijn de toewijzings operatoren, de cast-Opera tors en de negatie Opera tors ( `!` , `-not` , `-bnot` ), die worden geëvalueerd van rechts naar links.

U kunt bijlagen, zoals haakjes, gebruiken om de standaard prioriteits volgorde te overschrijven en Power shell af te dwingen om het Inge sloten deel van een expressie te evalueren vóór een niet-Inge sloten gedeelte.

In de volgende lijst worden Opera tors weer gegeven in de volg orde waarin ze worden geëvalueerd. Opera tors op dezelfde regel, of in dezelfde groep, hebben dezelfde prioriteit.

De kolom operator geeft een lijst van de Opera tors. In de kolom referentie wordt het Help-onderwerp van Power shell weer gegeven waarin de operator wordt beschreven. Als u het onderwerp wilt weer geven, typt u `get-help <topic-name>` .

|         AND         |           REFERENTIELAAG            |
| ------------------------ | ------------------------------ |
| `$() @() ()`             | [about_Operators][]            |
| `. ?.` (leden toegang)   | [about_Operators][]            |
| `::` storing            | [about_Operators][]            |
| `[0] ?[0]` (operator index) | [about_Operators][]         |
| `[int]` (cast-Opera tors) | [about_Operators][]            |
| `-split` monadische         | [about_Split][]                |
| `-join` monadische          | [about_Join][]                 |
| `,` (komma operator)     | [about_Operators][]            |
| `++ --`                  | [about_Assignment_Operators][] |
| `! -not`                 | [about_Logical_Operators][]    |
| `..` (bereik operator)    | [about_Operators][]            |
| `-f` (operator voor indeling)   | [about_Operators][]            |
| `-` (Unair/negatief)     | [about_Arithmetic_Operators][] |
| `* / %`                  | [about_Arithmetic_Operators][] |
| `+ -`                    | [about_Arithmetic_Operators][] |

De volgende groep Opera tors hebben dezelfde prioriteit. Hun hoofdletter gevoelige en expliciet hoofdletter gevoelig varianten hebben dezelfde prioriteit.

|         AND          |           REFERENTIELAAG            |
| ------------------------- | ------------------------------ |
| `-split` waarde         | [about_Split][]                |
| `-join` waarde          | [about_Join][]                 |
| `-is -isnot -as`          | [about_Type_Operators][]       |
| `-eq -ne -gt -gt -lt -le` | [about_Comparison_Operators][] |
| `-like -notlike`          | [about_Comparison_Operators][] |
| `-match -notmatch`        | [about_Comparison_Operators][] |
| `-in -notIn`              | [about_Comparison_Operators][] |
| `-contains -notContains`  | [about_Comparison_Operators][] |
| `-replace`                | [about_Comparison_Operators][] |

De lijst wordt hier weer gegeven met de volgende Opera tors in volg orde van prioriteit:

|                AND                 |           REFERENTIELAAG            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | [about_Arithmetic_Operators][] |
| `-and -or -xor`                         | [about_Logical_Operators][]    |

De volgende items zijn niet waar Opera tors. Ze maken deel uit van de opdracht syntaxis van Power shell, geen expressie syntaxis. De toewijzing is altijd de laatste actie die er gebeurt.

|                SYNTAXIS                   |           REFERENTIELAAG            |
| --------------------------------------- | ------------------------------ |
| `.` (punt-bron)                        | [about_Operators][]            |
| `&` telefoon                              | [about_Operators][]            |
| `? <if-true> : <if-false>` (Ternaire operator) | [about_Operators][]      |
| `??` (operator null-remeern)            | [about_Operators][]            |
| <code>&#124;</code> (pijplijn operator) | [about_Operators][]            |
| `> >> 2> 2>> 2>&1`                      | [about_Redirection][]          |
| <code>&& &#124;&#124;</code> (pijplijn keten operators) | [about_Operators][] |
| `= += -= *= /= %= ??=`                  | [about_Assignment_Operators][] |

## <a name="examples"></a>VOORBEELDEN

Met de volgende twee opdrachten worden de reken kundige Opera tors en het effect van het gebruik van haakjes weer gegeven om Power shell te dwingen het Inge sloten deel van de expressie eerst te evalueren.

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

In het volgende voor beeld worden de alleen-lezen tekst bestanden opgehaald uit de lokale map en opgeslagen in de `$read_only` variabele.

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

Dit komt overeen met het volgende voor beeld.

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

Omdat de pijplijn operator ( `|` ) een hogere prioriteit heeft dan de toewijzings operator ( `=` ), worden de bestanden die de `Get-ChildItem` cmdlet krijgt, naar de `Where-Object` cmdlet verzonden voor het filteren voordat ze aan de `$read_only` variabele worden toegewezen.

In het volgende voor beeld ziet u dat de operator index voor rang krijgt boven de cast-operator.

Met deze expressie maakt u een matrix van drie teken reeksen. Vervolgens wordt de index operator met de waarde 0 gebruikt om het eerste object in de matrix te selecteren. Dit is de eerste teken reeks. Ten slotte wordt het geselecteerde object omgezet in een teken reeks. In dit geval heeft de cast geen effect.

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

Deze expressie gebruikt haakjes om de conversie bewerking af te dwingen vóór de index selectie. Als gevolg hiervan wordt de gehele matrix geconverteerd als een (enkele) teken reeks. Vervolgens selecteert de operator index het eerste item in de teken reeks matrix. Dit is het eerste teken.

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

In het volgende voor beeld, omdat de `-gt` operator (groter dan) een hogere prioriteit heeft dan de `-and` operator (logische en), is het resultaat van de expressie onwaar.

```powershell
PS> 2 -gt 4 -and 1
False
```

Deze is gelijk aan de volgende expressie.

```powershell
PS> (2 -gt 4) -and 1
False
```

Als de operator-en een hogere prioriteit heeft, zou het antwoord de waarde TRUE hebben.

```powershell
PS> 2 -gt (4 -and 1)
True
```

In dit voor beeld ziet u echter een belang rijk principe voor het beheren van de prioriteit van Opera tors. Wanneer een expressie moeilijk is te interpreteren door anderen, gebruik dan haakjes om de evaluatie volgorde af te dwingen, zelfs wanneer de standaard operator prioriteit wordt afgedwongen. De haakjes maken uw bedoelingen duidelijk voor mensen die uw scripts lezen en onderhouden.

## <a name="see-also"></a>ZIE OOK

[about_Operators][]

[about_Assignment_Operators][]

[about_Comparison_Operators][]

[about_Arithmetic_Operators][]

[about_Join][]

[about_Redirection][]

[about_Scopes][]

[about_Split][]

[about_Type_Operators][]

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
