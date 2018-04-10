---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="call-base-class-constructor"></a>Klasseconstructor oproepbasis

Als u een constructor basisklasse vanuit een subklasse, gebruikt u het sleutelwoord **base**:

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

Als een basisklasse heeft een standaardconstructor (niets parameter), kunt u een expliciete constructoraanroep weglaten:

```powershell
class C : B
{
    C([int]$c) {}
}
```