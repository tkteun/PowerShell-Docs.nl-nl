---
title: Syntaxis van op opmerkingen gebaseerde Help | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357832"
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

 Help op basis van opmerkingen wordt geschreven als een reeks opmerkingen. U kunt vóór elke regel met opmerkingen een opmerkings symbool (#) typen, maar u kunt ook de symbolen "\< #" en "# >" gebruiken om een opmerkingen blok te maken. Alle regels in het opmerkingen blok worden geïnterpreteerd als opmerkingen.

 Elke sectie van Help op basis van opmerkingen is gedefinieerd met een tref woord en elk tref woord wordt voorafgegaan door een punt (.). De tref woorden kunnen in elke wille keurige volg orde worden weer gegeven. De namen van tref woorden zijn niet hoofdletter gevoelig.

 Een opmerkingen blok moet ten minste één Help-tref woord bevatten. Sommige tref woorden, zoals voor beeld, kunnen vaak in hetzelfde commentaar blok worden weer gegeven. De Help-inhoud voor elk tref woord begint op de regel na het sleutel woord en kan meerdere regels omvatten.

 Alle regels in een Help-onderwerp op basis van opmerkingen moeten aaneengesloten zijn. Als een Help-onderwerp op basis van opmerkingen een opmerking volgt die geen deel uitmaakt van het Help-onderwerp, moet er ten minste één lege regel tussen de laatste niet-Help opmerkings regel en het begin van de op opmerkingen gebaseerde Help zijn.

 Het volgende Help-onderwerp op basis van opmerkingen bevat bijvoorbeeld de. Het tref woord Description en de bijbehorende waarde, een beschrijving van een functie of script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```