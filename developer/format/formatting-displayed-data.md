---
title: Opmaak gegevens weergegeven | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 38971643-2a3d-4f5b-a1fa-6334c162b8ed
caps.latest.revision: 4
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065662"
---
# <a name="formatting-displayed-data"></a>Weergegeven gegevens opmaken

U kunt opgeven hoe de afzonderlijke gegevenspunten in de lijst, een tabel of een brede weergave worden weergegeven. U kunt de `FormatString` element bij het definiëren van de items van de weergave, of u kunt de `ScriptBlock` element om aan te roepen de `FormatString` methode van de gegevens.

## <a name="using-the-formatstring-element"></a>Met behulp van het FormatString-Element

In het volgende voorbeeld de waarde van de `TotalProcessorTime` eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is geformatteerd met het FormatString-element. de `TotalProcessorTime` eigenschap

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



