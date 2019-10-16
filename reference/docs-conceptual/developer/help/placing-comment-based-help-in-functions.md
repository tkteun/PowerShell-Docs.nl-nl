---
title: Help in functies op basis van opmerkingen plaatsen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357846"
---
# <a name="placing-comment-based-help-in-functions"></a>Help op basis van opmerkingen in functies plaatsen

In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een functie kunt plaatsen zodat de cmdlet `Get-Help` het Help-onderwerp op basis van opmerkingen koppelt aan de juiste functie.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Waar kunt u op opmerkingen gebaseerde hulp voor een functie plaatsen

- Aan het begin van de hoofd tekst van de functie.

- Aan het einde van de hoofd tekst van de functie.

- Vóór het sleutel woord `Function`. Wanneer de functie zich in een script of script module bevindt, kan er niet meer dan één lege regel tussen de laatste regel van de op opmerkingen gebaseerde Help en het sleutel woord `Function` zijn. Anders wordt de Help door `Get-Help` gekoppeld aan het script, niet met de functie.

## <a name="examples-of-help-placement-in-a-function"></a>Voor beelden van de plaatsing van een Help in een functie

 In de volgende voor beelden ziet u de drie plaatsings opties voor op opmerkingen gebaseerde Help voor een functie.

### <a name="help-at-the-beginning-of-a-function-body"></a>Help aan het begin van een functie hoofd tekst

 In het volgende voor beeld wordt aan het begin van een functie hoofdtekst een opmerking weer gegeven.

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

### <a name="help-at-the-end-of-a-function-body"></a>Help aan het einde van een functie hoofd tekst

 In het volgende voor beeld wordt een opmerking weer gegeven aan het einde van de hoofd tekst van een functie.

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

### <a name="help-before-the-function-keyword"></a>Help voor het tref woord function

 In de volgende voor beelden ziet u opmerkingen op basis van de regel voor het gereserveerde woord function.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```