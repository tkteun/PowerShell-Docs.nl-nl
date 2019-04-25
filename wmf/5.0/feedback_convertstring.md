---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057788"
---
# <a name="convert-string"></a>Convert-String
**Het omzetten van tekenreeks** bevat functionaliteit 'vervangen door magic'. Bieden van voor en na voorbeelden van hoe u tekst om te zoeken, en **Convert-tekenreeks** uw tekst automatisch opgemaakt. Dit is een demo - waarbij iemand de voornaam en achternaam en vervangen door hun achternaam op, een door komma's, is de eerste oorspronkelijke van hun achternaam en een punt. Probeer het met een reguliere expressie en Zie hoe lang duurt het.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
