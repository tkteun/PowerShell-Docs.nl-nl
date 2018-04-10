---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="7b391-102">Geïmplementeerde interface declareren</span><span class="sxs-lookup"><span data-stu-id="7b391-102">Declare Implemented Interface</span></span>

<span data-ttu-id="7b391-103">U kunt geïmplementeerde interfaces declareren nadat basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="7b391-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="7b391-104">Alle namen gescheiden door komma's.</span><span class="sxs-lookup"><span data-stu-id="7b391-104">Separate all type names by using commas.</span></span> <span data-ttu-id="7b391-105">Het is heel vergelijkbaar met C#-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="7b391-105">It’s very similar to C# syntax.</span></span>

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