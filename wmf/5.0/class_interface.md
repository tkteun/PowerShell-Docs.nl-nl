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
# <a name="declare-implemented-interface"></a>Geïmplementeerde Interface declareren

U kunt geïmplementeerde interfaces declareren nadat basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven. Alle namen gescheiden door komma's. Het is heel vergelijkbaar met C#-syntaxis.

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

