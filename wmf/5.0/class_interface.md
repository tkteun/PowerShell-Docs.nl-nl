---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085850"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="6416e-102">Geïmplementeerde interface declareren</span><span class="sxs-lookup"><span data-stu-id="6416e-102">Declare Implemented Interface</span></span>

<span data-ttu-id="6416e-103">U kunt geïmplementeerde interfaces aangeven na basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6416e-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="6416e-104">Alle namen worden gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="6416e-104">Separate all type names by using commas.</span></span> <span data-ttu-id="6416e-105">Het is heel vergelijkbaar met C# syntaxis.</span><span class="sxs-lookup"><span data-stu-id="6416e-105">It’s very similar to C# syntax.</span></span>

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
