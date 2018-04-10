---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: eeafdd8d7a50e0bfc5ebd0ca8e9852c3d7405bf0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-method"></a>Klassemethode oproepbasis

U kunt bestaande methoden in subklassen overschrijven. U doet dit door methoden met behulp van dezelfde naam en handtekening te declareren:

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

Voor het aanroepen van methoden van de basisklasse van overschreven implementaties, geconverteerd naar de basisklasse ([baseClass] $dit) op aanroepen:

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Alle methoden van PowerShell zijn virtueel. U kunt niet-virtuele .NET-methoden in een subklasse verbergen met behulp van dezelfde syntaxis als voor een onderdrukking: alleen methoden met dezelfde naam en handtekening declareren.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```