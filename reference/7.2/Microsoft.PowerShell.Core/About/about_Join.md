---
description: Hierin wordt beschreven hoe meerdere teken reeksen worden gecombineerd tot één teken reeks met de operator voor samen voegen (-lid).
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Join
ms.openlocfilehash: d76e95aaeca1b5b94bb1a2216576a985ffb209c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705375"
---
# <a name="about-join"></a>Samen voegen

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe meerdere teken reeksen worden gecombineerd tot één teken reeks met de operator voor samen voegen (-lid).

## <a name="long-description"></a>LANGE BESCHRIJVING

De operator voor samen voegen voegt een set teken reeksen samen tot één teken reeks. De teken reeksen worden toegevoegd aan de resulterende teken reeks in de volg orde waarin ze worden weer gegeven in de opdracht.

### <a name="syntax"></a>Syntax

In het volgende diagram ziet u de syntaxis voor de operator voor samen voegen.

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a>Parameters

Teken reeks []-Hiermee geeft u een of meer teken reeksen moet worden toegevoegd.

Scheidings teken: Hiermee geeft u een of meer tekens op die tussen de aaneengeschakelde teken reeksen worden geplaatst. De standaard waarde is geen scheidings teken ("").

Opmerkingen

De monadische samenvoegings operator (-samen voegen <teken reeks [] >) heeft een hogere prioriteit dan een komma. Als u dus een door komma's gescheiden lijst met teken reeksen verzendt naar de monadische koppelings operator, wordt alleen de eerste teken reeks (vóór de eerste komma) verzonden naar de operator voor samen voegen.

Als u de monadische samenvoegings operator wilt gebruiken, plaatst u de teken reeksen tussen haakjes of slaat u de teken reeksen op in een variabele. vervolgens verzendt u de variabele om samen te voegen.

Bijvoorbeeld:

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a>Voorbeelden

Met de volgende instructie worden drie teken reeksen samengevoegd:

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

Met de volgende instructie worden drie teken reeksen gescheiden door een spatie:

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

In de volgende instructies wordt een scheidings teken met meerdere tekens gebruikt om drie teken reeksen samen te voegen:

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

Met de volgende instructie worden de regels in een hier-teken reeks toegevoegd aan één teken reeks. Omdat een hier-teken reeks één teken reeks is, moeten de lijnen in de teken reeks hier worden gesplitst voordat ze kunnen worden toegevoegd. U kunt deze methode gebruiken om de teken reeksen opnieuw samen te voegen in een XML-bestand dat is opgeslagen in een hier-teken reeks:

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a>ZIE OOK

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Split](about_Split.md)

