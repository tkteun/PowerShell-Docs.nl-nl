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
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="3f010-102">Get-ChildItem heeft - diepte-parameter</span><span class="sxs-lookup"><span data-stu-id="3f010-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="3f010-103">**Get-ChildItem** heeft nu een **– diepte** u met de parameter **– Recurse** de recursie beperken:</span><span class="sxs-lookup"><span data-stu-id="3f010-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="3f010-104">PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 0</span><span class="sxs-lookup"><span data-stu-id="3f010-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="3f010-105">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3f010-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="3f010-106">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="3f010-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="3f010-107">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="3f010-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="3f010-108">-een---4-14-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="3f010-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="3f010-109">-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="3f010-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="3f010-110">-een---4-14-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="3f010-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="3f010-111">PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 1</span><span class="sxs-lookup"><span data-stu-id="3f010-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="3f010-112">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="3f010-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="3f010-113">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="3f010-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="3f010-114">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="3f010-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="3f010-115">-een---4-14-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="3f010-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="3f010-116">-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="3f010-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="3f010-117">-een---4-14-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="3f010-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="3f010-118">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld\\Depth0</span><span class="sxs-lookup"><span data-stu-id="3f010-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="3f010-119">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="3f010-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="3f010-120">d---4-14-2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="3f010-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
