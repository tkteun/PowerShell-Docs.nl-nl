---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058621"
---
# <a name="call-base-class-method"></a><span data-ttu-id="c2b47-102">Klassemethode oproepbasis</span><span class="sxs-lookup"><span data-stu-id="c2b47-102">Call Base Class Method</span></span>

<span data-ttu-id="c2b47-103">U kunt bestaande methoden in subklassen overschrijven.</span><span class="sxs-lookup"><span data-stu-id="c2b47-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="c2b47-104">U doet dit door methoden met behulp van dezelfde naam en handtekening te declareren:</span><span class="sxs-lookup"><span data-stu-id="c2b47-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="c2b47-105">Voor het aanroepen van methoden van de basisklasse van overschreven-implementaties, geconverteerd naar de basisklasse ([baseClass] $dit) op voor aanroepen:</span><span class="sxs-lookup"><span data-stu-id="c2b47-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="c2b47-106">Alle methoden voor PowerShell zijn virtueel.</span><span class="sxs-lookup"><span data-stu-id="c2b47-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="c2b47-107">U kunt niet-virtuele .NET-methoden in een subklasse verbergen met behulp van dezelfde syntaxis als voor een onderdrukking: alleen methoden met dezelfde naam en handtekening declareren.</span><span class="sxs-lookup"><span data-stu-id="c2b47-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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
