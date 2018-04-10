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
# <a name="convert-string"></a><span data-ttu-id="69a03-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="69a03-102">Convert-String</span></span>
<span data-ttu-id="69a03-103">**Het omzetten van tekenreeks** 'vervangen door magic'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="69a03-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="69a03-104">Voor en na enkele voorbeelden van hoe u de tekst die moet worden gezocht wilt bieden en **Convert-tekenreeks** automatisch de tekst wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="69a03-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="69a03-105">Hier volgt een demo - duurt iemand de voornaam en achternaam en vervangen door hun achternaam, een door komma's, de eerste initiële van hun achternaam en een punt.</span><span class="sxs-lookup"><span data-stu-id="69a03-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="69a03-106">Probeer het met een reguliere expressie en Zie hoe lang duurt het.</span><span class="sxs-lookup"><span data-stu-id="69a03-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```