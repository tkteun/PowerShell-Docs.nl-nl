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
# <a name="formatting-displayed-data"></a><span data-ttu-id="be4fa-102">Weergegeven gegevens opmaken</span><span class="sxs-lookup"><span data-stu-id="be4fa-102">Formatting Displayed Data</span></span>

<span data-ttu-id="be4fa-103">U kunt opgeven hoe de afzonderlijke gegevens punten in de lijst, tabel of brede weer gave worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="be4fa-103">You can specify how the individual data points in your List, Table, or Wide view are displayed.</span></span> <span data-ttu-id="be4fa-104">U kunt het- `FormatString` element gebruiken bij het definiëren van de items van uw weer gave, of u kunt het `ScriptBlock` element gebruiken om de-methode aan te roepen `FormatString` voor de gegevens.</span><span class="sxs-lookup"><span data-stu-id="be4fa-104">You can use the `FormatString` element when defining the items of your view, or you can use the `ScriptBlock` element to call the `FormatString` method on the data.</span></span>

## <a name="using-the-formatstring-element"></a><span data-ttu-id="be4fa-105">Het element formats Tring gebruiken</span><span class="sxs-lookup"><span data-stu-id="be4fa-105">Using the FormatString Element</span></span>

<span data-ttu-id="be4fa-106">In het volgende voor beeld wordt de waarde van de `TotalProcessorTime` eigenschap van het object [System. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) opgemaakt met het element formats Tring.</span><span class="sxs-lookup"><span data-stu-id="be4fa-106">In the following example the value of the `TotalProcessorTime` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object is formatted using the FormatString element.</span></span> <span data-ttu-id="be4fa-107">de `TotalProcessorTime` eigenschap</span><span class="sxs-lookup"><span data-stu-id="be4fa-107">the `TotalProcessorTime` property</span></span>

```
<TableColumnItem>
  <PropertyName>TotalProcessorTime</PropertyName>
  <FormatString>{0:MMM}{0:dd}{0:HH}:{0:mm}</FormatString>
</TableColumnItem>
```
