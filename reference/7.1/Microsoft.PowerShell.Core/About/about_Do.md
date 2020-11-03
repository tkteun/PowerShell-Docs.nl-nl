---
description: Voert een lijst met instructies uit met een of meer keren, afhankelijk van de voor waarde while of until.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 2cffc5293ee8c636eb58d1f9951e34852eb465f0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252456"
---
# <a name="about-do"></a>Over doen

## <a name="short-description"></a>KORTE BESCHRIJVING
Voert een lijst met instructies uit met een of meer keren, afhankelijk van de voor waarde while of until.

## <a name="long-description"></a>LANGE BESCHRIJVING

Het sleutel woord do werkt met het sleutel woord while of het sleutel woord until om de instructies in een script blok uit te voeren, onder voor waarde. In tegens telling tot de lus while, voert het script blok in een do-lus altijd ten minste één keer uit.

Een lus **-while** is een verscheidenheid van de while-lus. In een lus **-while** wordt de voor waarde geëvalueerd nadat het script blok is uitgevoerd. Net als bij een while-lus wordt het script blok herhaald, zolang de voor waarde resulteert in waar.

Net als **bij** een lus wordt een **do-until-** lus altijd ten minste één keer uitgevoerd voordat de voor waarde wordt geëvalueerd. Het script blok kan echter alleen worden uitgevoerd als de voor waarde ONWAAR is.

De zoek woorden *continue* en outcontrol *flow kunnen* worden gebruikt in een **do-while-** lus of in een **do-until-** lus.

### <a name="syntax"></a>Syntax

Hieronder ziet u de syntaxis van de instructie **do-while** :

```powershell
do {<statement list>} while (<condition>)
```

Hieronder ziet u de syntaxis van de instructie **do-until** :

```powershell
do {<statement list>} until (<condition>)
```

De lijst met instructies bevat een of meer instructies die worden uitgevoerd elke keer dat de lus wordt ingevoerd of herhaald.

Het voor waarde-gedeelte van de instructie wordt omgezet in waar of onwaar.

### <a name="example"></a>Voorbeeld

In het volgende voor beeld van de instructie do worden de items in een matrix geteld, totdat het item met de waarde 0 wordt bereikt.

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

In het volgende voor beeld wordt het sleutel woord until gebruikt. Merk op dat de operator niet gelijk is aan ( `-ne` ) wordt vervangen door de operator equal to ( `-eq` ).

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

In het volgende voor beeld worden alle waarden van een matrix geschreven, waarbij elke waarde die kleiner is dan nul, wordt overgeslagen.

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a>ZIE OOK

[about_While](about_While.md)

[about_Operators](about_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

