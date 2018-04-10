---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a>Convert-String
**Het omzetten van tekenreeks** 'vervangen door magic'-functionaliteit. Voor en na enkele voorbeelden van hoe u de tekst die moet worden gezocht wilt bieden en **Convert-tekenreeks** automatisch de tekst wordt opgemaakt. Hier volgt een demo - duurt iemand de voornaam en achternaam en vervangen door hun achternaam, een door komma's, de eerste initiële van hun achternaam en een punt. Probeer het met een reguliere expressie en Zie hoe lang duurt het.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```