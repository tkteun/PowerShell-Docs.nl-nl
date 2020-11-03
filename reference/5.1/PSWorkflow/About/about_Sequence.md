---
description: Hierin wordt het `Sequence` tref woord beschreven waarmee geselecteerde activiteiten opeenvolgend worden uitgevoerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_sequence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Sequence
ms.openlocfilehash: a9dd4fb24274fe4e1478ca69c734b43a2f196792
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252400"
---
# <a name="about-sequence"></a><span data-ttu-id="d20ab-104">Volg orde</span><span class="sxs-lookup"><span data-stu-id="d20ab-104">About Sequence</span></span>

## <a name="short-description"></a><span data-ttu-id="d20ab-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="d20ab-105">Short description</span></span>

<span data-ttu-id="d20ab-106">Hierin wordt het `Sequence` tref woord beschreven waarmee geselecteerde activiteiten opeenvolgend worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d20ab-106">Describes the `Sequence` keyword that runs selected activities sequentially.</span></span>

## <a name="long-description"></a><span data-ttu-id="d20ab-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="d20ab-107">Long description</span></span>

<span data-ttu-id="d20ab-108">Met het `Sequence` sleutel woord worden de geselecteerde werk stroom activiteiten sequentieel uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d20ab-108">The `Sequence` keyword runs selected workflow activities sequentially.</span></span> <span data-ttu-id="d20ab-109">Werk stroom activiteiten worden uitgevoerd in de volg orde waarin ze worden weer gegeven en niet gelijktijdig worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d20ab-109">Workflow activities run in the order that they appear and do not run concurrently.</span></span> <span data-ttu-id="d20ab-110">Het `Sequence` sleutel woord is alleen geldig in een Power shell-werk stroom.</span><span class="sxs-lookup"><span data-stu-id="d20ab-110">The `Sequence` keyword is only valid in a PowerShell Workflow.</span></span>

<span data-ttu-id="d20ab-111">Het `Sequence` sleutel woord wordt gebruikt in een- `Parallel` script blok om de geselecteerde opdrachten sequentieel uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d20ab-111">The `Sequence` keyword is used in a `Parallel` script block to run selected commands sequentially.</span></span>

<span data-ttu-id="d20ab-112">Omdat werk stroom activiteiten standaard sequentieel worden uitgevoerd, `Sequence` is het sleutel woord alleen effectief in een- `Parallel` script blok.</span><span class="sxs-lookup"><span data-stu-id="d20ab-112">Because workflow activities run sequentially by default, the `Sequence` keyword is only effective in a `Parallel` script block.</span></span> <span data-ttu-id="d20ab-113">Als het `Sequence` sleutel woord niet is opgenomen in een `Parallel` -script blok, is dit geldig, maar niet effectief.</span><span class="sxs-lookup"><span data-stu-id="d20ab-113">If the `Sequence` keyword isn't included in a `Parallel` script block, it's valid but ineffective.</span></span>

<span data-ttu-id="d20ab-114">`Sequence`Met het script blok kunt u meerdere opdrachten parallel uitvoeren door de afhankelijke opdrachten sequentieel uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d20ab-114">The `Sequence` script block lets you run more commands in parallel by allowing you to run dependent commands sequentially.</span></span>

## <a name="syntax"></a><span data-ttu-id="d20ab-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="d20ab-115">Syntax</span></span>

### <a name="workflow-using-sequence"></a><span data-ttu-id="d20ab-116">Werk stroom met behulp van volg orde</span><span class="sxs-lookup"><span data-stu-id="d20ab-116">Workflow using Sequence</span></span>

```
workflow <Verb-Noun>
{
    Sequence
    {
        [<Activity>]
        [<Activity>]
        # ...
    }
}
```

### <a name="workflow-using-parallel-and-sequence"></a><span data-ttu-id="d20ab-117">Werk stroom met parallel en sequentieel</span><span class="sxs-lookup"><span data-stu-id="d20ab-117">Workflow using Parallel and Sequence</span></span>

```
workflow <Verb-Noun>
{
    Parallel
    {
        [<Activity>]
        Sequence
        {
            [<Activity>]
            [<Activity>]
            # ...
        }
    }
}
```

## <a name="detailed-description"></a><span data-ttu-id="d20ab-118">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="d20ab-118">Detailed description</span></span>

<span data-ttu-id="d20ab-119">De opdrachten in een- `Parallel` script blok kunnen gelijktijdig worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d20ab-119">The commands in a `Parallel` script block can run concurrently.</span></span> <span data-ttu-id="d20ab-120">De volg orde waarin ze worden uitgevoerd, wordt niet bepaald.</span><span class="sxs-lookup"><span data-stu-id="d20ab-120">The order in which they run is not determined.</span></span> <span data-ttu-id="d20ab-121">Deze functie verbetert de prestaties van een script werk stroom.</span><span class="sxs-lookup"><span data-stu-id="d20ab-121">This feature improves the performance of a script workflow.</span></span>

<span data-ttu-id="d20ab-122">U kunt een `Sequence` script blok gebruiken om geselecteerde activiteiten sequentieel uit te voeren, zelfs als de activiteiten in een script blok worden weer gegeven `Parallel` .</span><span class="sxs-lookup"><span data-stu-id="d20ab-122">You can use a `Sequence` script block to run selected activities sequentially, even though the activities appear in a `Parallel` script block.</span></span>

<span data-ttu-id="d20ab-123">De activiteiten in een `Sequence` script blok worden opeenvolgend uitgevoerd in de volg orde waarin ze worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="d20ab-123">The activities in a `Sequence` script block run consecutively in the order that they are listed.</span></span> <span data-ttu-id="d20ab-124">Een activiteit in een `Sequence` script blok start pas nadat de vorige activiteit is voltooid.</span><span class="sxs-lookup"><span data-stu-id="d20ab-124">An activity in a `Sequence` script block starts only after the previous activity completes.</span></span>

<span data-ttu-id="d20ab-125">Wanneer het `Sequence` script blok echter in een script blok wordt weer gegeven `Parallel` , wordt de volg orde waarin het `Sequence` script blok wordt uitgevoerd, niet bepaald.</span><span class="sxs-lookup"><span data-stu-id="d20ab-125">However, when the `Sequence` script block appears in a `Parallel` script block, the order in which the `Sequence` script block runs isn't determined.</span></span> <span data-ttu-id="d20ab-126">Dit kan vóór, na of gelijktijdig met andere activiteiten in het `Parallel` script blok worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d20ab-126">It might run before, after, or concurrent with other activities in the `Parallel` script block.</span></span>

<span data-ttu-id="d20ab-127">De volgende werk stroom bevat bijvoorbeeld een `Parallel` script blok dat activiteiten uitvoert die processen en services op de computer ophalen.</span><span class="sxs-lookup"><span data-stu-id="d20ab-127">For example, the following workflow includes a `Parallel` script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="d20ab-128">Het `Parallel` script blok bevat een `Sequence` script blok waarmee informatie uit een bestand wordt opgehaald en de informatie wordt gebruikt als invoer voor een script.</span><span class="sxs-lookup"><span data-stu-id="d20ab-128">The `Parallel` script block contains a `Sequence` script block that gets information from a file and uses the information as input to a script.</span></span>

<span data-ttu-id="d20ab-129">De `Get-Process` `Get-Service` opdrachten, en zijn onafhankelijk van elkaar.</span><span class="sxs-lookup"><span data-stu-id="d20ab-129">The `Get-Process`, `Get-Service`, and hotfix-related commands are independent of each other.</span></span> <span data-ttu-id="d20ab-130">De opdrachten kunnen gelijktijdig of in een wille keurige volg orde worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d20ab-130">The commands can run concurrently or in any order.</span></span> <span data-ttu-id="d20ab-131">Maar de opdracht die de hotfix-informatie ophaalt, moet worden uitgevoerd voordat de opdracht wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d20ab-131">But, the command that gets the hotfix information must run before the command that uses it.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
    Get-Process
    Get-Service

    Sequence
    {
        $Hotfix = Get-Content 'D:\HotFixes\Required.txt'
        Foreach ($h in $Hotfix) {'D:\Scripts\Verify-Hotfix' -Hotfix $h}
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d20ab-132">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d20ab-132">See also</span></span>

[<span data-ttu-id="d20ab-133">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="d20ab-133">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="d20ab-134">about_ForEach-parallel</span><span class="sxs-lookup"><span data-stu-id="d20ab-134">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="d20ab-135">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d20ab-135">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="d20ab-136">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="d20ab-136">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="d20ab-137">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="d20ab-137">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="d20ab-138">Een werkstroom maken met behulp van een Windows PowerShell-script</span><span class="sxs-lookup"><span data-stu-id="d20ab-138">Creating a Workflow by Using a Windows PowerShell Script</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
