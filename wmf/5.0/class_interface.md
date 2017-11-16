---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="9af3a-102">Geïmplementeerde Interface declareren</span><span class="sxs-lookup"><span data-stu-id="9af3a-102">Declare Implemented Interface</span></span>

<span data-ttu-id="9af3a-103">U kunt geïmplementeerde interfaces declareren nadat basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9af3a-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="9af3a-104">Alle namen gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="9af3a-104">Separate all type names by using commas.</span></span> <span data-ttu-id="9af3a-105">Het is heel vergelijkbaar met C#-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="9af3a-105">It’s very similar to C# syntax.</span></span>

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

