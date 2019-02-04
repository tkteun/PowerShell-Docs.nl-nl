---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687914"
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem heeft parameter - Depth
**Get-ChildItem** heeft nu een **– diepte** parameter die u met gebruikt **– Recurse** de recursie beperken:

PS C:\\gebruikers\\slee\\Downloads\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 0

Map: C:\\gebruikers\\slee\\Downloads\\voorbeeld

Modus LastWriteTime lengte naam

---- ------------- ------ ----

d---4-14-2015 17:36 uur Depth0

-een---14-4-2015 13:19 uur 0 Bestand1.txt

-een---14-4-2015 13:19 uur 0 bestand2.txt samengevoegd

-een---14-4-2015 13:19 uur 0 File3.txt

PS C:\\gebruikers\\slee\\Downloads\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 1

Map: C:\\gebruikers\\slee\\Downloads\\voorbeeld

Modus LastWriteTime lengte naam

---- ------------- ------ ----

d---4-14-2015 17:36 uur Depth0

-een---14-4-2015 13:19 uur 0 Bestand1.txt

-een---14-4-2015 13:19 uur 0 bestand2.txt samengevoegd

-een---14-4-2015 13:19 uur 0 File3.txt

Map: C:\\gebruikers\\slee\\Downloads\\voorbeeld\\Depth0

Modus LastWriteTime lengte naam

---- ------------- ------ ----

d---4-14-2015 17:33:00 uur Depth1
