---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683777"
---
# <a name="call-base-class-constructor"></a>Klasseconstructor oproepbasis

Als u wilt een oproepbasis aanroepen vanuit een subklasse, gebruikt u het sleutelwoord **basis**:

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

Als een basisklasse heeft een standaardconstructor (Er is geen parameter), kunt u een expliciete constructoraanroep weglaten:

```powershell
class C : B
{
    C([int]$c) {}
}
```
