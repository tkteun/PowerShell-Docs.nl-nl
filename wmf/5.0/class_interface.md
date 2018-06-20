---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225484"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="b012c-102">Geïmplementeerde interface declareren</span><span class="sxs-lookup"><span data-stu-id="b012c-102">Declare Implemented Interface</span></span>

<span data-ttu-id="b012c-103">U kunt geïmplementeerde interfaces declareren nadat basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b012c-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="b012c-104">Alle namen gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="b012c-104">Separate all type names by using commas.</span></span> <span data-ttu-id="b012c-105">Het is heel vergelijkbaar met C#-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="b012c-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```
