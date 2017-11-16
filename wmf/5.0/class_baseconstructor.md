---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-constructor"></a><span data-ttu-id="f1d83-102">Roep basisklasse-Constructor</span><span class="sxs-lookup"><span data-stu-id="f1d83-102">Call Base Class Constructor</span></span>

<span data-ttu-id="f1d83-103">Als u een constructor basisklasse vanuit een subklasse, gebruikt u het sleutelwoord **base**:</span><span class="sxs-lookup"><span data-stu-id="f1d83-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="f1d83-104">Als een basisklasse heeft een standaardconstructor (niets parameter), kunt u een expliciete constructoraanroep weglaten:</span><span class="sxs-lookup"><span data-stu-id="f1d83-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

