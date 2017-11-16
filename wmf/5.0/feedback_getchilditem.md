---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
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

