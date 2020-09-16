---
title: Weer gegeven gegevens opmaken | Microsoft Docs
ms.date: 09/12/2016
ms.openlocfilehash: 97d23b3079b2779e518b6b6d2f2ac0c5e9d1f3a3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781508"
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
