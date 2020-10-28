---
ms.date: 09/12/2016
ms.topic: reference
title: Help op basis van opmerkingen in functies plaatsen
description: Help op basis van opmerkingen in functies plaatsen
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658214"
---
# <a name="placing-comment-based-help-in-functions"></a>Help op basis van opmerkingen in functies plaatsen

In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een functie kunt plaatsen zodat de `Get-Help` cmdlet het Help-onderwerp op basis van opmerkingen koppelt aan de juiste functie.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Waar kunt u Comment-Based hulp voor een functie plaatsen

- Aan het begin van de hoofd tekst van de functie.

- Aan het einde van de hoofd tekst van de functie.

- Vóór het `Function` sleutel woord. Wanneer de functie zich in een script of script module bevindt, kan er niet meer dan één lege regel tussen de laatste regel van de op opmerkingen gebaseerde Help en het `Function` tref woord zijn. Als dat niet het geval is, `Get-Help` koppelt u de Help aan het script, niet met de functie.

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
