---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="46c8a-102">Get-ChildItem heeft - diepte-parameter</span><span class="sxs-lookup"><span data-stu-id="46c8a-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="46c8a-103">**Get-ChildItem** heeft nu een **– diepte** u met de parameter **– Recurse** de recursie beperken:</span><span class="sxs-lookup"><span data-stu-id="46c8a-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="46c8a-104">PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 0</span><span class="sxs-lookup"><span data-stu-id="46c8a-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="46c8a-105">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="46c8a-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="46c8a-106">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="46c8a-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="46c8a-107">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="46c8a-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="46c8a-108">-een---4-14-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="46c8a-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="46c8a-109">-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="46c8a-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="46c8a-110">-een---4-14-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="46c8a-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="46c8a-111">PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 1</span><span class="sxs-lookup"><span data-stu-id="46c8a-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="46c8a-112">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="46c8a-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="46c8a-113">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="46c8a-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="46c8a-114">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="46c8a-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="46c8a-115">-een---4-14-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="46c8a-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="46c8a-116">-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="46c8a-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="46c8a-117">-een---4-14-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="46c8a-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="46c8a-118">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld\\Depth0</span><span class="sxs-lookup"><span data-stu-id="46c8a-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="46c8a-119">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="46c8a-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="46c8a-120">d---4-14-2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="46c8a-120">d----- 4/14/2015 5:33 PM Depth1</span></span>