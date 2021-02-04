---
description: Hierin wordt beschreven hoe de `continue` instructie direct de programma stroom retourneert naar de bovenkant van een programma-lus, een `switch` instructie of een- `trap` instructie.
keywords: powershell,cmdlet
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 2b299726b3fe75e5d13e91bbde7564705d3e2112
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/17/2020
ms.locfileid: "97614112"
---
# <a name="about-continue"></a>Over gaan

## <a name="short-description"></a>Korte beschrijving

Hierin wordt beschreven hoe de `continue` instructie direct de programma stroom retourneert naar de bovenkant van een programma-lus, een `switch` instructie of een- `trap` instructie.

## <a name="long-description"></a>Lange beschrijving

De `continue` instructie biedt een manier om het huidige besturings blok te sluiten, maar door te gaan met de uitvoering, in plaats van volledig te worden afgesloten. De instructie ondersteunt labels.
Een label is een naam die u toewijst aan een instructie in een script.

## <a name="using-continue-in-loops"></a>Door gaan in lussen gebruiken

Een instructie zonder label `continue` retourneert onmiddellijk de programma stroom naar de bovenkant van de binnenste lus die wordt beheerd door een `for` , `foreach` ,, `do` of- `while` instructie. De huidige herhaling van de lus wordt beëindigd en de lus gaat verder met de volgende iteratie.

In het volgende voor beeld keert programma flow terug naar de bovenkant van de `while` lus als de `$ctr` variabele gelijk is aan 5. Als gevolg hiervan worden alle getallen tussen 1 en 10 weer gegeven, met uitzonde ring van 5:

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

Wanneer u een `for` lus gebruikt, wordt de uitvoering voortgezet volgens de `<Repeat>` instructie, gevolgd door de `<Condition>` test. In het onderstaande voor beeld wordt een oneindige lus niet uitgevoerd omdat het verstrijken van `$i` plaatsvindt na het `continue` sleutel woord.

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a>Het gebruik van een label door gaan in een lus

Een `continue` instructie met het label beëindigt de uitvoering van de iteratie en brengt de controle over naar het doel label dat moet worden omsloten of `switch` afschriften.

In het volgende voor beeld wordt het binnenste `for` beëindigd wanneer `$condition` is ingesteld op **True** en wordt iteratie voortgezet met de tweede `for` lus op `labelB` .

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a>Door gaan in een switch-instructie gebruiken

Een niet-gelabelde `continue` instructie in `switch` de uitvoering van de huidige `switch` iteratie wordt beëindigd en de besturings elementen worden overgeboekt naar de bovenkant `switch` om het volgende invoer item op te halen.

Als er één invoer item is, wordt `continue` het volledige `switch` overzicht afgesloten.
Wanneer de `switch` invoer een verzameling is, wordt `switch` elk element van de verzameling getest. Hiermee wordt de `continue` huidige herhaling afgesloten en wordt het `switch` volgende element voortgezet.

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a>Door gaan in een trap-instructie gebruiken

Als de laatste instructie die wordt uitgevoerd in de hoofd tekst een `trap` instructie is `continue` , wordt de ondergevulde fout op de achtergrond genegeerd en wordt de uitvoering voortgezet met de instructie die de oorzaak is van het `trap` probleem.

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a>Gebruik niet door gaan buiten een lus, switch of trap

Wanneer `continue` wordt gebruikt buiten een constructie die deze direct ondersteunt (lussen, `switch` ,, `trap` ), zoekt Power shell _de aanroep stack_ voor een insluitende constructie. Als er geen insluitende constructie kan worden gevonden, wordt de huidige runs Pace stil beëindigd.

Dit betekent dat functies en scripts die per ongeluk gebruikmaken `continue` van een insluitende constructie die het ondersteunt, de _aanroepers_ per ongeluk kunnen beëindigen.

`continue`Als u een pijp lijn gebruikt, zoals een- `ForEach-Object` script blok, wordt de pijp lijn niet alleen afgesloten, waardoor de volledige runs Pace wordt beëindigd.

## <a name="see-also"></a>Zie ook

[about_Break](about_Break.md)

[about_For](about_For.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
