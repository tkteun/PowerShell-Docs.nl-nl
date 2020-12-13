---
ms.date: 09/12/2016
ms.topic: reference
title: Weergegeven gegevens opmaken
description: Weergegeven gegevens opmaken
ms.openlocfilehash: 40f6b3b4fa36062ee0bad3f197ad159f571445c8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667858"
---
# <a name="formatting-displayed-data"></a>Weergegeven gegevens opmaken

U kunt opgeven hoe de afzonderlijke gegevens punten in de lijst, tabel of brede weer gave worden weer gegeven. U kunt het- `FormatString` element gebruiken bij het definiëren van de items van uw weer gave, of u kunt het `ScriptBlock` element gebruiken om de-methode aan te roepen `FormatString` voor de gegevens.

## <a name="using-the-formatstring-element"></a>Het element formats Tring gebruiken

In het volgende voor beeld wordt de waarde van de `TotalProcessorTime` eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) opgemaakt met het element formats Tring. de `TotalProcessorTime` eigenschap

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
