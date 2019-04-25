---
title: Help op basis van een opmerking plaatsen in Functions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083192"
---
# <a name="placing-comment-based-help-in-functions"></a>Help op basis van opmerkingen in functies plaatsen

Dit onderwerp wordt uitgelegd waar u de help voor een functie op basis van een opmerking plaatsen zodat het `Get-Help` cmdlet het helponderwerp op basis van een opmerking koppelt aan de juiste functie.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Waar plaatst u de Help op basis van een opmerking voor een functie

- Aan het begin van de hoofdtekst van de functie.

- Aan het einde van de hoofdtekst van de functie.

- Voordat u de `Function` trefwoord. Wanneer de functie zich in een script of een scriptmodule, er mag niet meer dan één lege regel tussen de laatste regel van de help op basis van een opmerking en de `Function` trefwoord. Anders `Get-Help` koppelt u de help met het script, niet met de functie.

## <a name="examples-of-help-placement-in-a-function"></a>Voorbeelden van de plaatsing van de Help-informatie in een functie

 De volgende voorbeelden ziet elk van de van de drie plaatsingsopties voor meer informatie over op basis van een opmerking voor een functie.

### <a name="help-at-the-beginning-of-a-function-body"></a>Help weer bij het begin van de hoofdtekst van een functie

 Het volgende voorbeeld ziet u op basis van een opmerking aan het begin van de hoofdtekst van een functie.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>Help weer bij het einde van de hoofdtekst van een functie

 Het volgende voorbeeld ziet Opmerking gebaseerde aan het einde van de hoofdtekst van een functie.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Help voor de functie-trefwoord

 De volgende voorbeelden ziet u op basis van een opmerking op de regel voor de functie trefwoord.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```