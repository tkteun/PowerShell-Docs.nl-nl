---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 5dbaa126cf9ae3917c3a8787ffc5ef5ac77b19c1
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="c38f3-102">Basisklasse declareren</span><span class="sxs-lookup"><span data-stu-id="c38f3-102">Declare Base Class</span></span>
<span data-ttu-id="c38f3-103">U kunt een Windows PowerShell-klasse declareren als basistype voor een andere Windows PowerShell-klasse.</span><span class="sxs-lookup"><span data-stu-id="c38f3-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

```powershell
class bar
{
   [int]foo() 
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

<span data-ttu-id="c38f3-104">U kunt ook bestaande .NET Framework-typen als basisklassen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="c38f3-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

