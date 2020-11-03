---
description: Hierin wordt een taal instructie beschreven die u kunt gebruiken om een opdracht blok uit te voeren op basis van de resultaten van een voorwaardelijke test.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 60b944d3f09db786b54a1c7afb685543de808a92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252857"
---
# <a name="about-while"></a>Over hoewel

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt een taal instructie beschreven die u kunt gebruiken om een opdracht blok uit te voeren op basis van de resultaten van een voorwaardelijke test.

## <a name="long-description"></a>LANGE BESCHRIJVING

De instructie while (ook wel een while-lus genoemd) is een taal constructie voor het maken van een lus waarbij opdrachten in een opdracht blok worden uitgevoerd zolang een voorwaardelijke test resulteert in waar. De instructie while is gemakkelijker te maken dan een for-instructie, omdat de syntaxis minder gecompliceerd is. Daarnaast is het flexibeler dan de instructie foreach, omdat u een voorwaardelijke test in de instructie while opgeeft om te bepalen hoe vaak de lus wordt uitgevoerd.

Hieronder ziet u de syntaxis while-instructie:

```powershell
while (<condition>){<statement list>}
```

Wanneer u een while-instructie uitvoert, evalueert Power shell de `<condition>` sectie van de instructie voordat de sectie wordt ingevoerd `<statement list>` . Het voor waarde-gedeelte van de instructie wordt omgezet in waar of onwaar. Zolang de voor waarde waar is, voert Power shell de sectie opnieuw uit `<statement list>` .

De `<statement list>` sectie van de instructie bevat een of meer opdrachten die elke keer dat de lus wordt ingevoerd of herhaald worden uitgevoerd.

Met de volgende instructie while worden bijvoorbeeld de getallen 1 tot en met 3 weer gegeven als de variabele $val niet is gemaakt of als de $val variabele is gemaakt en geïnitialiseerd op 0.

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

In dit voor beeld is de voor waarde ($val niet gelijk aan 3) waar wanneer $val \= 0, 1, 2. Elke keer door de lus $val wordt verhoogd met 1 met behulp van de \+ \+ unaire operator voor aflopen ($Val \+ \+ ). De laatste keer door loop, $val \= 3. Als $val gelijk is aan 3, wordt de voor waarde-instructie geëvalueerd als False en wordt de lus afgesloten.

Als u deze opdracht op de Power shell-opdracht prompt handig wilt schrijven, kunt u deze op de volgende manier invoeren:

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

U ziet dat de punt komma de eerste opdracht scheidt waarmee 1 wordt toegevoegd aan $val van de tweede opdracht die de waarde van $val naar de-console schrijft.

## <a name="see-also"></a>ZIE OOK

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Do](about_Do.md)

[about_Foreach](about_Foreach.md)

[about_For](about_For.md)

[about_Language_Keywords](about_Language_Keywords.md)

