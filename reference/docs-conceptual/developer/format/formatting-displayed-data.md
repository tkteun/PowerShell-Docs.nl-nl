---
title: Weer gegeven gegevens opmaken | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: 9f3a3176ae16ac7c014cadce6b4e856f9bd3b5da
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560386"
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
