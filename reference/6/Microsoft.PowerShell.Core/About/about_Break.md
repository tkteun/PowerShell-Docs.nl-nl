---
description: Hierin wordt een instructie beschreven die u kunt gebruiken voor het direct afsluiten,,,, `foreach` `for` `while` `do` `switch` of `trap` instructies.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 8716f81163cfd34684c3ef7071f7827f2e9b5bcf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252375"
---
# <a name="about-break"></a>Over onderbreken

## <a name="short-description"></a>Korte beschrijving

Hierin wordt een instructie beschreven die u kunt gebruiken voor het direct afsluiten,,,, `foreach` `for` `while` `do` `switch` of `trap` instructies.

## <a name="long-description"></a>Lange beschrijving

De `break` instructie biedt een manier om het huidige besturings blok af te sluiten.
De uitvoering wordt voortgezet bij de volgende instructie na het controle blok. De instructie ondersteunt labels. Een label is een naam die u toewijst aan een instructie in een script.

## <a name="using-break-in-loops"></a>Einden in lussen gebruiken

Wanneer een `break` instructie wordt weer gegeven in een lus, zoals een `foreach` ,, `for` `do` , of `while` lus, wordt de lus onmiddellijk afgesloten door Power shell.

Een `break` instructie kan een label bevatten waarmee u Inge sloten lussen kunt sluiten. Een label kan elk wille keurig lus-tref woord opgeven, zoals `foreach` , `for` of `while` , in een script.

In het volgende voor beeld ziet u hoe u een instructie kunt gebruiken `break` om een instructie af te sluiten `for` :

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

In dit voor beeld `break` sluit de instructie de `for` lus af wanneer de `$i` variabele gelijk is aan 1. Hoewel de `for` instructie evalueert naar **True** tot `$i` groter is dan 10, heeft Power shell de instructie einde bereikt wanneer de lus voor het eerst `for` wordt uitgevoerd.

Het is vaak gebruikelijk om de instructie te gebruiken `break` in een lus waarbij aan een interne voor waarde moet worden voldaan. Bekijk het volgende `foreach` voor beeld van de instructie:

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

In dit voor beeld wordt de matrix door de `foreach` instructie herhaald `$varB` . De `if` instructie evalueert naar onwaar als de eerste twee keer dat de lus wordt uitgevoerd en de variabele `$i` wordt verhoogd met 1. De derde keer dat de lus wordt uitgevoerd, `$i` is gelijk aan 2 en de `$val` variabele is 30. Op dit punt wordt de `break` instructie uitgevoerd en wordt de `foreach` lus afgesloten.

### <a name="using-a-labeled-break-in-a-loop"></a>Een einde met een label in een lus gebruiken

Een `break` instructie kan een label bevatten. Als u het `break` sleutel woord met een label gebruikt, wordt de lus met het label in Power shell afgesloten in plaats van de huidige lus af te sluiten.
Het label is een dubbele punt gevolgd door een naam die u toewijst. Het label moet het eerste token in een instructie zijn en moet worden gevolgd door het tref woord voor herhaling, zoals `while` .

`break` Hiermee verplaatst u de uitvoering uit de gelabelde lus. In Inge sloten lussen heeft dit een ander resultaat dan het `break` tref woord heeft wanneer het wordt gebruikt door zichzelf. Dit voor beeld heeft een `while` instructie met een `for` instructie:

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

Als voor waarde 2 resulteert in **waar** , wordt de uitvoering van het script naar de instructie overgeslagen na de gelabelde lus. In het voor beeld wordt de uitvoering opnieuw gestart met de-instructie `$a = $c` .

U kunt veel gelabelde lussen nesten, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

Als de `$b` variabele wordt geëvalueerd als waar, wordt de uitvoering van het script hervat na de lus met de naam ' rood '. Als de `$c` variabele wordt geëvalueerd als waar, wordt de uitvoering van het script-besturings element hervat na de lus met de naam geel.

Als de `$a` variabele wordt geëvalueerd als waar, wordt de uitvoering hervat na de binnenste lus. Er is geen label vereist.

Power shell beperkt de uitvoering van de labels mogelijk niet. Het label kan zelfs de controle over de grenzen van scripts en functie aanroepen door geven.

## <a name="using-break-in-a-switch-statement"></a>De instructie Restore gebruiken voor een switch

In een `switch` Construct wordt `break` met Power shell het `switch` code blok afgesloten.

Het `break` sleutel woord wordt gebruikt om de `switch` Construct te verlaten. De volgende `switch` instructie gebruikt bijvoorbeeld `break` instructies om te testen op de meest specifieke voor waarde:

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

In dit voor beeld `$var` wordt de variabele gemaakt en geïnitialiseerd naar een teken reeks waarde van `word2` . De `switch` instructie gebruikt de **regex** -klasse om de variabele waarde eerst te vergelijken met de term `word2` . Omdat de waarde van de variabele en de eerste test in de `switch` instructie overeenkomen, wordt het eerste code blok in de `switch` instructie uitgevoerd.

Wanneer Power shell de eerste `break` instructie bereikt, wordt de `switch` instructie afgesloten. Als de vier `break` instructies uit het voor beeld worden verwijderd, worden aan alle vier voor waarden voldaan. In dit voor beeld wordt de- `break` instructie gebruikt voor het weer geven van resultaten wanneer aan de meest specifieke voor waarde wordt voldaan.

## <a name="using-break-in-a-trap-statement"></a>Onderbreken gebruiken in een instructie trap

Als de laatste instructie in de hoofd tekst van een `trap` instructie is uitgevoerd `break` , wordt het fout object onderdrukt en wordt de uitzonde ring opnieuw gegenereerd.

In het volgende voor beeld wordt een **DivideByZeroException** -uitzonde ring gemaakt die wordt gevuld met de- `trap` instructie.

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

U ziet dat de uitvoering stopt bij de uitzonde ring. De `After loop` is nooit bereikt.
De uitzonde ring wordt opnieuw gegenereerd na de `trap` uitvoering.

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
Attempted to divide by zero.
At line:10 char:6
+      "1 / $i = " + (1 / $i--)
+      ~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RuntimeException
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a>Geen breek punt gebruiken buiten een lus, switch of trap

Wanneer `break` wordt gebruikt buiten een constructie die deze direct ondersteunt (lussen, `switch` ,, `trap` ), zoekt Power shell _de aanroep stack_ voor een insluitende constructie. Als er geen insluitende constructie kan worden gevonden, wordt de huidige runs Pace stil beëindigd.

Dit betekent dat functies en scripts die per ongeluk gebruikmaken `break` van een insluitende constructie die het ondersteunt, de _aanroepers_ per ongeluk kunnen beëindigen.

`break`Als u een pijp lijn gebruikt `break` , zoals een- `ForEach-Object` script blok, wordt de pijp lijn niet alleen afgesloten, waardoor de volledige runs Pace wordt beëindigd.

## <a name="see-also"></a>Zie ook

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Continue](about_Continue.md)

[about_For](about_For.md)

[about_Foreach](about_Foreach.md)

[about_Switch](about_Switch.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

[about_While](about_While.md)
