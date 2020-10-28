---
ms.date: 09/12/2016
ms.topic: reference
title: Weergegeven gegevens opmaken
description: Weergegeven gegevens opmaken
ms.openlocfilehash: 40f6b3b4fa36062ee0bad3f197ad159f571445c8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667858"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="3b74d-103">Weergegeven gegevens opmaken</span><span class="sxs-lookup"><span data-stu-id="3b74d-103">Formatting Displayed Data</span></span>

<span data-ttu-id="3b74d-104">U kunt opgeven hoe de afzonderlijke gegevens punten in de lijst, tabel of brede weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3b74d-104">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="3b74d-105">U kunt het- `FormatString` element gebruiken bij het definiëren van de items van uw weer gave, of u kunt het `ScriptBlock` element gebruiken om de-methode aan te roepen `FormatString` voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="3b74d-105">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="3b74d-106">Het element formats Tring gebruiken</span><span class="sxs-lookup"><span data-stu-id="3b74d-106">Using the FormatString Element</span></span>

<span data-ttu-id="3b74d-107">In het volgende voor beeld wordt de waarde van de `TotalProcessorTime` eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) opgemaakt met het element formats Tring.</span><span class="sxs-lookup"><span data-stu-id="3b74d-107">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="3b74d-108">de `TotalProcessorTime` eigenschap</span><span class="sxs-lookup"><span data-stu-id="3b74d-108">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
