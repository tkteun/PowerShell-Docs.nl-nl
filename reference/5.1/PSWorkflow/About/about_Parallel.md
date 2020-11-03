---
description: Hierin wordt het sleutel woord parallel beschreven, waarmee de activiteiten in een werk stroom parallel worden uitgevoerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parallel
ms.openlocfilehash: 402e93672bbea4ec9b6bfda8d608f266f6c40a21
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252402"
---
# <a name="about-parallel"></a><span data-ttu-id="73c2a-104">Over parallel</span><span class="sxs-lookup"><span data-stu-id="73c2a-104">About Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="73c2a-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73c2a-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="73c2a-106">Hierin wordt het sleutel woord parallel beschreven, waarmee de activiteiten in een werk stroom parallel worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73c2a-106">Describes the Parallel keyword, which runs the activities in a workflow in parallel.</span></span>

## <a name="long-description"></a><span data-ttu-id="73c2a-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73c2a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="73c2a-108">Met het sleutel woord parallel worden werk stroom activiteiten parallel uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73c2a-108">The Parallel keyword runs workflow activities in parallel.</span></span> <span data-ttu-id="73c2a-109">Dit sleutel woord is alleen geldig in de Windows Power shell-werk stroom.</span><span class="sxs-lookup"><span data-stu-id="73c2a-109">This keyword is valid only in  Windows PowerShell  Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="73c2a-110">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="73c2a-110">SYNTAX</span></span>

```
workflow <Verb-Noun>
{
     Parallel
     {
          [<Activity>]
          [<Activity>]
        ...
     }
 }
```

## <a name="detailed-description"></a><span data-ttu-id="73c2a-111">GEDETAILLEERDE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73c2a-111">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="73c2a-112">De opdrachten in een parallel-script blok kunnen gelijktijdig worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73c2a-112">The commands in a Parallel script block can run concurrently.</span></span> <span data-ttu-id="73c2a-113">De volg orde waarin ze worden uitgevoerd, wordt niet bepaald.</span><span class="sxs-lookup"><span data-stu-id="73c2a-113">The order in which they run is not determined.</span></span>

<span data-ttu-id="73c2a-114">De volgende werk stroom bevat bijvoorbeeld een parallel-script blok dat activiteiten uitvoert die processen en services op de computer ophalen.</span><span class="sxs-lookup"><span data-stu-id="73c2a-114">For example, the following workflow includes a Parallel script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="73c2a-115">Omdat de opdrachten Get-Process en Get-Service onafhankelijk van elkaar zijn, kunnen ze gelijktijdig en in wille keurige volg orde worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="73c2a-115">Because the Get-Process and Get-Service commands are independent of each other, they can run concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
         Get-Process
         Get-Service
    }
}
```

<span data-ttu-id="73c2a-116">Het uitvoeren van parallelle opdrachten is zeer efficiënt en vermindert de tijd die nodig is om een werk stroom aanzienlijk te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="73c2a-116">Running commands in parallel is very efficient and reduces the time it takes to complete a workflow significantly.</span></span>

<span data-ttu-id="73c2a-117">Als u geselecteerde opdrachten in een sequentieel parallel script-blok wilt uitvoeren, gebruikt u het tref woord sequence.</span><span class="sxs-lookup"><span data-stu-id="73c2a-117">To run selected commands in a Parallel script block in sequential order, use the Sequence keyword.</span></span> <span data-ttu-id="73c2a-118">Zie about_Sequence voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73c2a-118">For more information, see about_Sequence.</span></span>

<span data-ttu-id="73c2a-119">Als u een parallel script blok wilt uitvoeren voor items in een verzameling, gebruikt u de zoek woorden ForEach of ForEach-parallel.</span><span class="sxs-lookup"><span data-stu-id="73c2a-119">To run a Parallel script block on items in a collection, use the ForEach or ForEach -Parallel keywords.</span></span>

## <a name="see-also"></a><span data-ttu-id="73c2a-120">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="73c2a-120">SEE ALSO</span></span>

<span data-ttu-id="73c2a-121">["Een script werk stroom schrijven"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="73c2a-121">["Writing a Script Workflow"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span></span>

[<span data-ttu-id="73c2a-122">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="73c2a-122">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="73c2a-123">about_ForEach-parallel</span><span class="sxs-lookup"><span data-stu-id="73c2a-123">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="73c2a-124">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="73c2a-124">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="73c2a-125">about_Sequence</span><span class="sxs-lookup"><span data-stu-id="73c2a-125">about_Sequence</span></span>](about_Sequence.md)

[<span data-ttu-id="73c2a-126">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="73c2a-126">about_Workflows</span></span>](about_workflows.md)
