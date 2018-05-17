---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a>Convert-String
**Het omzetten van tekenreeks** 'vervangen door magic'-functionaliteit. Voor en na enkele voorbeelden van hoe u de tekst die moet worden gezocht wilt bieden en **Convert-tekenreeks** automatisch de tekst wordt opgemaakt. Hier volgt een demo - duurt iemand de voornaam en achternaam en vervangen door hun achternaam, een door komma's, de eerste initiële van hun achternaam en een punt. Probeer het met een reguliere expressie en Zie hoe lang duurt het.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
