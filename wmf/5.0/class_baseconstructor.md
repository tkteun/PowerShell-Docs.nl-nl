---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085878"
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="ce752-102">Klasseconstructor oproepbasis</span><span class="sxs-lookup"><span data-stu-id="ce752-102">Call Base Class Constructor</span></span>

<span data-ttu-id="ce752-103">Als u wilt een oproepbasis aanroepen vanuit een subklasse, gebruikt u het sleutelwoord **basis**:</span><span class="sxs-lookup"><span data-stu-id="ce752-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

<span data-ttu-id="ce752-104">Als een basisklasse heeft een standaardconstructor (Er is geen parameter), kunt u een expliciete constructoraanroep weglaten:</span><span class="sxs-lookup"><span data-stu-id="ce752-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
