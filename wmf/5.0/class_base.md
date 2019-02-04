---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 8b3ebd22e03bf9bdd5f26965137a1b1ce9f47c3e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686745"
---
# <a name="declare-base-class"></a><span data-ttu-id="bafd8-102">Basisklasse declareren</span><span class="sxs-lookup"><span data-stu-id="bafd8-102">Declare Base Class</span></span>
<span data-ttu-id="bafd8-103">Als een basistype op voor een andere Windows PowerShell-klasse kunt u een Windows PowerShell-klasse declareren.</span><span class="sxs-lookup"><span data-stu-id="bafd8-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="bafd8-104">U kunt ook bestaande .NET Framework-typen gebruiken als basisklassen:</span><span class="sxs-lookup"><span data-stu-id="bafd8-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
