---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a><span data-ttu-id="aede9-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="aede9-102">Convert-String</span></span>
<span data-ttu-id="aede9-103">**Het omzetten van tekenreeks** 'vervangen door magic'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="aede9-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="aede9-104">Voor en na enkele voorbeelden van hoe u de tekst die moet worden gezocht wilt bieden en **Convert-tekenreeks** automatisch de tekst wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="aede9-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="aede9-105">Hier volgt een demo - duurt iemand de voornaam en achternaam en vervangen door hun achternaam, een door komma's, de eerste initiële van hun achternaam en een punt.</span><span class="sxs-lookup"><span data-stu-id="aede9-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="aede9-106">Probeer het met een reguliere expressie en Zie hoe lang duurt het.</span><span class="sxs-lookup"><span data-stu-id="aede9-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
