---
ms.date: 09/12/2016
ms.topic: reference
title: Syntaxis van de Help op basis van opmerkingen
description: Syntaxis van de Help op basis van opmerkingen
ms.openlocfilehash: 3866f25b40fc970e8d219af6f423b7a25f5b875c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659520"
---
# <a name="syntax-of-comment-based-help"></a>Syntaxis van de Help op basis van opmerkingen

In deze sectie wordt de syntaxis van op opmerkingen gebaseerde Help beschreven.

## <a name="syntax-diagram"></a>Syntaxis diagram

 De syntaxis voor op opmerkingen gebaseerde Help is als volgt:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Syntaxis beschrijving

 Help op basis van opmerkingen wordt geschreven als een reeks opmerkingen. U kunt een opmerkings symbool ( `#` ) voor elke regel met opmerkingen typen, maar u kunt ook `<#` de `#>` symbolen en gebruiken om een opmerkingen blok te maken. Alle regels in het opmerkingen blok worden geïnterpreteerd als opmerkingen.

 Elke sectie van Help op basis van opmerkingen is gedefinieerd met een tref woord en elk tref woord wordt voorafgegaan door een punt ( `.` ). De tref woorden kunnen in elke wille keurige volg orde worden weer gegeven. De namen van tref woorden zijn niet hoofdletter gevoelig.

 Een opmerkingen blok moet ten minste één Help-tref woord bevatten. Sommige tref woorden, zoals **voor beeld** , kunnen vaak in hetzelfde commentaar blok worden weer gegeven. De Help-inhoud voor elk tref woord begint op de regel na het sleutel woord en kan meerdere regels omvatten.

 Alle regels in een Help-onderwerp op basis van opmerkingen moeten aaneengesloten zijn. Als een Help-onderwerp op basis van opmerkingen een opmerking volgt die geen deel uitmaakt van het Help-onderwerp, moet er ten minste één lege regel tussen de laatste niet-Help opmerkings regel en het begin van de op opmerkingen gebaseerde Help zijn.

 Het volgende Help-onderwerp op basis van opmerkingen bevat bijvoorbeeld de. Het tref woord Description en de bijbehorende waarde, een beschrijving van een functie of script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
