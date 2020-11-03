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
# <a name="about_logical_operators"></a>about_Logical_Operators

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de Opera tors beschreven waarmee instructies in Power shell worden verbonden.

## <a name="long-description"></a>LANGE BESCHRIJVING

De logische Power shell-Opera tors verbinden expressies en instructies, zodat u één expressie kunt gebruiken om te testen op meerdere voor waarden.

De volgende instructie gebruikt bijvoorbeeld de operator and en de operator OR om drie voorwaardelijke instructies te verbinden. De instructie is alleen waar als de waarde van $a groter is dan de waarde van $b en $a of $b kleiner is dan
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

Power shell ondersteunt de volgende logische Opera tors.

|Operator|Beschrijving                        |Voorbeeld                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |Logische en. WAAR wanneer beide        |`(1 -eq 1) -and (1 -eq 2)`|
|        |-instructies zijn waar.               |`False`                   |
|`-or`   |Logische of. WAAR wanneer       |`(1 -eq 1) -or (1 -eq 2)` |
|        |de instructie is waar.                 |`True`                    |
|`-xor`  |Logische exclusieve of. WAAR wanneer    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |Er is slechts één instructie waar         |`False`                   |
|`-not`  |Logische not. De instructie wordt genegeerd |`-not (1 -eq 1)`          |
|        |dat volgt.                      |`False`                   |
|`!`     |Hetzelfde als `-not`                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 Opmerking:

In de vorige voor beelden wordt ook gebruikgemaakt van de operator gelijk aan vergelijkend `-eq` . Zie [about_Comparison_Operators](about_Comparison_Operators.md)voor meer informatie. In de voor beelden wordt ook gebruikgemaakt van de Booleaanse waarden van gehele getallen. Het gehele getal 0 heeft de waarde FALSE. Alle andere gehele getallen hebben de waarde TRUE.

De syntaxis van de logische Opera Tors is als volgt:

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

Instructies die gebruikmaken van logische Opera Tors, retour neren Boole-waarden (waar of onwaar).

De logische Power shell-Opera tors evalueren alleen de instructies die nodig zijn om de waarheids waarde van de instructie te bepalen. Als de linkeroperand in een instructie die de operator and bevat is ingesteld op FALSE, wordt de rechter operand niet geëvalueerd.
Als de linkeroperand in een instructie met de or-instructie is ingesteld op TRUE, wordt de rechter operand niet geëvalueerd. Als gevolg hiervan kunt u deze instructies op dezelfde manier gebruiken als de `If` instructie.

## <a name="see-also"></a>ZIE OOK

[about_Operators](about_Operators.md)

[Compare-object](xref:Microsoft.PowerShell.Utility.Compare-Object)

[about_Comparison_operators](about_Comparison_Operators.md)

[about_If](about_If.md)
