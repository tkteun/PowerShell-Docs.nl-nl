---
title: Syntaxis van de Help op basis van een opmerking | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846492"
---
# <a name="syntax-of-comment-based-help"></a>Syntaxis van de Help op basis van opmerkingen

Deze sectie beschrijft de syntaxis van de help op basis van een opmerking.

## <a name="syntax-diagram"></a>Syntaxisschema

 De syntaxis voor meer informatie over op basis van een opmerking is als volgt:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Van de syntaxisbeschrijving

 Help op basis van een opmerking wordt geschreven als een reeks met opmerkingen. Typt u een opmerkingensymbool (#) voor elke regel van opmerkingen of kunt u de '\<# ' en ' #> "symbolen te maken van een opmerkingenblok. Alle regels binnen het Opmerkingenblok worden geïnterpreteerd als opmerkingen.

 Elke sectie van de Help op basis van een opmerking wordt gedefinieerd door een trefwoord en elk trefwoord wordt voorafgegaan door een punt (.). De trefwoorden kunnen worden weergegeven in een willekeurige volgorde. Het sleutelwoord namen zijn niet hoofdlettergevoelig.

 Een opmerkingenblok moet ten minste één Help-informatie sleutelwoord bevatten. Enkele van de trefwoorden, zoals bijvoorbeeld kunnen vaak worden weergegeven in het hetzelfde opmerkingenblok. De Help-inhoud voor elk trefwoord begint op de regel na het sleutelwoord en kan meerdere regels omvatten.

 Alle regels in een opmerking op basis van Help-onderwerp moeten aaneengesloten zijn. Als een opmerking op basis van Help-onderwerp wordt gevolgd door een opmerking die geen deel uitmaakt van het Help-onderwerp, moet er ten minste één lege regel tussen de laatste opmerkingsregel van de niet-Help en het begin van de Help op basis van een opmerking.

 Bijvoorbeeld, het volgende op basis van een opmerking help-onderwerp bevat de. Beschrijving trefwoord en de waarde, een beschrijving van een functie of script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```