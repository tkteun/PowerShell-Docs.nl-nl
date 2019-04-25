---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085277"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="12441-102">Get-ChildItem heeft parameter - Depth</span><span class="sxs-lookup"><span data-stu-id="12441-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="12441-103">**Get-ChildItem** heeft nu een **– diepte** parameter die u met gebruikt **– Recurse** de recursie beperken:</span><span class="sxs-lookup"><span data-stu-id="12441-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="12441-104">PS C:\\gebruikers\\slee\\Downloads\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 0</span><span class="sxs-lookup"><span data-stu-id="12441-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="12441-105">Map: C:\\gebruikers\\slee\\Downloads\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="12441-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="12441-106">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="12441-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="12441-107">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="12441-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="12441-108">-een---14-4-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="12441-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="12441-109">-een---14-4-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="12441-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="12441-110">-een---14-4-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="12441-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="12441-111">PS C:\\gebruikers\\slee\\Downloads\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 1</span><span class="sxs-lookup"><span data-stu-id="12441-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="12441-112">Map: C:\\gebruikers\\slee\\Downloads\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="12441-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="12441-113">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="12441-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="12441-114">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="12441-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="12441-115">-een---14-4-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="12441-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="12441-116">-een---14-4-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="12441-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="12441-117">-een---14-4-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="12441-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="12441-118">Map: C:\\gebruikers\\slee\\Downloads\\voorbeeld\\Depth0</span><span class="sxs-lookup"><span data-stu-id="12441-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="12441-119">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="12441-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="12441-120">d---4-14-2015 17:33:00 uur Depth1</span><span class="sxs-lookup"><span data-stu-id="12441-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
