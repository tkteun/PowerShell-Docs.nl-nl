---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684498"
---
# <a name="convert-string"></a><span data-ttu-id="6dd22-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="6dd22-102">Convert-String</span></span>
<span data-ttu-id="6dd22-103">**Het omzetten van tekenreeks** bevat functionaliteit 'vervangen door magic'.</span><span class="sxs-lookup"><span data-stu-id="6dd22-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="6dd22-104">Bieden van voor en na voorbeelden van hoe u tekst om te zoeken, en **Convert-tekenreeks** uw tekst automatisch opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="6dd22-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="6dd22-105">Dit is een demo - waarbij iemand de voornaam en achternaam en vervangen door hun achternaam op, een door komma's, is de eerste oorspronkelijke van hun achternaam en een punt.</span><span class="sxs-lookup"><span data-stu-id="6dd22-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="6dd22-106">Probeer het met een reguliere expressie en Zie hoe lang duurt het.</span><span class="sxs-lookup"><span data-stu-id="6dd22-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
