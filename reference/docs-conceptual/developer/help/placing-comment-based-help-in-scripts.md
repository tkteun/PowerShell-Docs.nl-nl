---
ms.date: 09/12/2016
ms.topic: reference
title: Help op basis van opmerkingen in scripts plaatsen
description: Help op basis van opmerkingen in scripts plaatsen
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645437"
---
# <a name="placing-comment-based-help-in-scripts"></a>Help op basis van opmerkingen in scripts plaatsen

In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een script kunt plaatsen zodat de `Get-Help` cmdlet het Help-onderwerp op basis van opmerkingen koppelt aan scripts en niet met functies die mogelijk in het script zijn.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Waar kunt u Comment-Based Help voor een script plaatsen

- Aan het begin van het script bestand.

  De Help van het script kan alleen worden voorafgegaan door opmerkingen en lege regels in het script.

- Aan het einde van het script bestand.

  Als het eerste item in de hoofd tekst van het script (na de Help) een functie declaratie is, moeten er ten minste twee lege regels tussen het einde van de script-Help en de functie declaratie zijn. Anders wordt de Help geïnterpreteerd als hulp voor de functie, en niet bij het script.

## <a name="examples-of-help-placement-in-a-script"></a>Voor beelden van de plaatsing van een Help in een script

In de volgende voor beelden ziet u de plaatsings opties voor Help op basis van opmerkingen voor een script.

### <a name="help-at-the-beginning-of-a-script"></a>Help aan het begin van een script

In het volgende voor beeld wordt een opmerking weer gegeven aan het begin van een script.

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Help aan het einde van een script

 In het volgende voor beeld wordt een opmerking weer gegeven aan het einde van een script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
