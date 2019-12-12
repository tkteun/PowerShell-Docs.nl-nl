---
title: Help op basis van opmerkingen in scripts plaatsen | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353247"
---
# <a name="placing-comment-based-help-in-scripts"></a>Help op basis van opmerkingen in scripts plaatsen

In dit onderwerp wordt uitgelegd waar u op opmerkingen gebaseerde hulp voor een script kunt plaatsen zodat de cmdlet `Get-Help` het Help-onderwerp op basis van opmerkingen koppelt aan scripts en niet met functies die zich in het script bevindt.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Waar kunt u op opmerkingen gebaseerde hulp voor een script plaatsen

- Aan het begin van het script bestand. De Help van het script kan alleen worden voorafgegaan door opmerkingen en lege regels in het script.

- Aan het einde van het script bestand.

  Als het eerste item in de hoofd tekst van het script (na de Help) een functie declaratie is, moeten er ten minste twee lege regels tussen het einde van de script-Help en de functie declaratie zijn. Anders wordt de Help geïnterpreteerd als hulp voor de functie, en niet bij het script.

## <a name="examples-of-help-placement-in-a-script"></a>Voor beelden van de plaatsing van een Help in een script

 In de volgende voor beelden ziet u de plaatsings opties voor Help op basis van opmerkingen voor een script.

### <a name="help-at-the-beginning-of-a-script"></a>Help aan het begin van een script

 In het volgende voor beeld wordt een opmerking weer gegeven aan het begin van een script.

```
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