---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a><span data-ttu-id="39531-102">Het omzetten van tekenreeks</span><span class="sxs-lookup"><span data-stu-id="39531-102">Convert-String</span></span>
<span data-ttu-id="39531-103">**Het omzetten van tekenreeks** 'vervangen door magic'-functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="39531-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="39531-104">Voor en na enkele voorbeelden van hoe u de tekst die moet worden gezocht wilt bieden en **Convert-tekenreeks** automatisch de tekst wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="39531-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="39531-105">Hier volgt een demo - duurt iemand de voornaam en achternaam en vervangen door hun achternaam, een door komma's, de eerste initiële van hun achternaam en een punt.</span><span class="sxs-lookup"><span data-stu-id="39531-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="39531-106">Probeer het met een reguliere expressie en Zie hoe lang duurt het.</span><span class="sxs-lookup"><span data-stu-id="39531-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

