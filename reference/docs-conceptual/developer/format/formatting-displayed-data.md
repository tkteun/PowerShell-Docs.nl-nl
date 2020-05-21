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
# <a name="formatting-displayed-data"></a><span data-ttu-id="d7e5f-102">Weergegeven gegevens opmaken</span><span class="sxs-lookup"><span data-stu-id="d7e5f-102">Formatting Displayed Data</span></span>

<span data-ttu-id="d7e5f-103">U kunt opgeven hoe de afzonderlijke gegevens punten in de lijst, tabel of brede weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="d7e5f-104">U kunt het- `FormatString` element gebruiken bij het definiëren van de items van uw weer gave, of u kunt het `ScriptBlock` element gebruiken om de-methode aan te roepen `FormatString` voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="d7e5f-105">Het element formats Tring gebruiken</span><span class="sxs-lookup"><span data-stu-id="d7e5f-105">Using the FormatString Element</span></span>

<span data-ttu-id="d7e5f-106">In het volgende voor beeld wordt de waarde van de `TotalProcessorTime` eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) opgemaakt met het element formats Tring.</span><span class="sxs-lookup"><span data-stu-id="d7e5f-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="d7e5f-107">de `TotalProcessorTime` eigenschap</span><span class="sxs-lookup"><span data-stu-id="d7e5f-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
