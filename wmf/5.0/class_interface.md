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
# <a name="declare-implemented-interface"></a>Geïmplementeerde interface declareren

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
