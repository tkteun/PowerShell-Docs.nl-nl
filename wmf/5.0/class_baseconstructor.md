---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225603"
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
