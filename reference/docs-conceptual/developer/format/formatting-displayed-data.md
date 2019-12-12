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
ms.openlocfilehash: e915ac71feb50cb58cfa9195f0de94763affdb77
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355011"
---
# <a name="formatting-displayed-data"></a><span data-ttu-id="5c187-102">Weergegeven gegevens opmaken</span><span class="sxs-lookup"><span data-stu-id="5c187-102">Formatting Displayed Data</span></span>

<span data-ttu-id="5c187-103">U kunt opgeven hoe de afzonderlijke gegevens punten in de lijst, tabel of brede weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5c187-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="5c187-104">U kunt het `FormatString`-element gebruiken bij het definiëren van de items van uw weer gave, of u kunt het element `ScriptBlock` gebruiken om de `FormatString`-methode aan te roepen voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="5c187-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="5c187-105">Het element formats Tring gebruiken</span><span class="sxs-lookup"><span data-stu-id="5c187-105">Using the FormatString Element</span></span>

<span data-ttu-id="5c187-106">In het volgende voor beeld wordt de waarde van de eigenschap `TotalProcessorTime` van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) opgemaakt met het element formats Tring.</span><span class="sxs-lookup"><span data-stu-id="5c187-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="5c187-107">de eigenschap `TotalProcessorTime`</span><span class="sxs-lookup"><span data-stu-id="5c187-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



