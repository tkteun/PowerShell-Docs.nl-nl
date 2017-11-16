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
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="7480c-102">Get-ChildItem heeft - diepte-parameter</span><span class="sxs-lookup"><span data-stu-id="7480c-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="7480c-103">**Get-ChildItem** heeft nu een **– diepte** u met de parameter **– Recurse** de recursie beperken:</span><span class="sxs-lookup"><span data-stu-id="7480c-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="7480c-104">PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 0</span><span class="sxs-lookup"><span data-stu-id="7480c-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="7480c-105">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7480c-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="7480c-106">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="7480c-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7480c-107">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="7480c-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="7480c-108">-een---4-14-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="7480c-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="7480c-109">-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="7480c-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="7480c-110">-een---4-14-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="7480c-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="7480c-111">PS C:\\gebruikers\\slee\\downloadt\\voorbeeld&gt; Get-ChildItem-Recurse - diepte 1</span><span class="sxs-lookup"><span data-stu-id="7480c-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="7480c-112">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7480c-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="7480c-113">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="7480c-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7480c-114">d---4-14-2015 17:36 uur Depth0</span><span class="sxs-lookup"><span data-stu-id="7480c-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="7480c-115">-een---4-14-2015 13:19 uur 0 Bestand1.txt</span><span class="sxs-lookup"><span data-stu-id="7480c-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="7480c-116">-een---4-14-2015 13:19 uur 0 bestand2.txt samengevoegd</span><span class="sxs-lookup"><span data-stu-id="7480c-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="7480c-117">-een---4-14-2015 13:19 uur 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="7480c-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="7480c-118">Map: C:\\gebruikers\\slee\\downloadt\\voorbeeld\\Depth0</span><span class="sxs-lookup"><span data-stu-id="7480c-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="7480c-119">Modus LastWriteTime lengte naam</span><span class="sxs-lookup"><span data-stu-id="7480c-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7480c-120">d---4-14-2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="7480c-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

