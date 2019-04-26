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
# <a name="formatting-displayed-data"></a><span data-ttu-id="cf8ba-102">Weergegeven gegevens opmaken</span><span class="sxs-lookup"><span data-stu-id="cf8ba-102">Formatting Displayed Data</span></span>

<span data-ttu-id="cf8ba-103">U kunt opgeven hoe de afzonderlijke gegevenspunten in de lijst, een tabel of een brede weergave worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="cf8ba-104">U kunt de `FormatString` element bij het definiëren van de items van de weergave, of u kunt de `ScriptBlock` element om aan te roepen de `FormatString` methode van de gegevens.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="cf8ba-105">Met behulp van het FormatString-Element</span><span class="sxs-lookup"><span data-stu-id="cf8ba-105">Using the FormatString Element</span></span>

<span data-ttu-id="cf8ba-106">In het volgende voorbeeld de waarde van de `TotalProcessorTime` eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is geformatteerd met het FormatString-element.</span><span class="sxs-lookup"><span data-stu-id="cf8ba-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="cf8ba-107">de `TotalProcessorTime` eigenschap</span><span class="sxs-lookup"><span data-stu-id="cf8ba-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```



