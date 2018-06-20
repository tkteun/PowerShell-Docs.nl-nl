---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221898"
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem heeft - diepte-parameter
**Get-ChildItem** heeft nu een **– diepte** u met de parameter **– Recurse** de recursie beperken:

PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 0

Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld

Modus LastWriteTime lengte naam

---- ------------- ------ ----

d---4-14-2015 17:36 uur Depth0

-een---4-14-2015 13:19 uur 0 Bestand1.txt

-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd

-een---4-14-2015 13:19 uur 0 File3.txt

PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 1

Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld

Modus LastWriteTime lengte naam

---- ------------- ------ ----

d---4-14-2015 17:36 uur Depth0

-een---4-14-2015 13:19 uur 0 Bestand1.txt

-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd

-een---4-14-2015 13:19 uur 0 File3.txt

Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld\\Depth0

Modus LastWriteTime lengte naam

---- ------------- ------ ----

d---4-14-2015 5:33 PM Depth1
