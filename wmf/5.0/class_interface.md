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
# <a name="declare-implemented-interface"></a>Geïmplementeerde interface declareren

U kunt geïmplementeerde interfaces aangeven na basistypen of onmiddellijk nadat een dubbele punt (:), als er geen basistype dat is opgegeven. Alle namen worden gescheiden door komma's. Het is heel vergelijkbaar met C# syntaxis.

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
