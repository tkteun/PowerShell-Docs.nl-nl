---
description: Beschrijft de `Suspend-Workflow` activiteit, waardoor de werk stroom wordt onderbroken waarin de activiteit wordt weer gegeven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Suspend werk stroom
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252395"
---
# <a name="about-suspend-workflow"></a><span data-ttu-id="e33f5-104">Over Suspend-Workflow</span><span class="sxs-lookup"><span data-stu-id="e33f5-104">About Suspend-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="e33f5-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="e33f5-105">Short description</span></span>

<span data-ttu-id="e33f5-106">Beschrijft de `Suspend-Workflow` activiteit, waardoor de werk stroom wordt onderbroken waarin de activiteit wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e33f5-106">Describes the `Suspend-Workflow` activity, which suspends the workflow in which the activity appears.</span></span>

## <a name="long-description"></a><span data-ttu-id="e33f5-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="e33f5-107">Long description</span></span>

<span data-ttu-id="e33f5-108">De `Suspend-Workflow` activiteit stopt de verwerking van werk stromen tijdelijk vanuit de werk stroom.</span><span class="sxs-lookup"><span data-stu-id="e33f5-108">The `Suspend-Workflow` activity temporarily stops workflow processing from within the workflow.</span></span> <span data-ttu-id="e33f5-109">Voordat u de werk stroom uitbreekt, wordt een controle punt gebruikt, zodat de status en gegevens van de werk stroom behouden blijven en de werk stroom kan worden hervat vanaf het onderbrekings punt.</span><span class="sxs-lookup"><span data-stu-id="e33f5-109">Before suspending, Windows PowerShell Workflow takes a checkpoint so the workflow's state and data are preserved and the workflow can resume from the suspension point.</span></span>

<span data-ttu-id="e33f5-110">De gebruiker die de werk stroom uitvoert, maakt gebruik van de cmdlet om de werk stroom te hervatten `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-110">To resume the workflow, the user running the workflow uses the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="e33f5-111">U kunt een werk stroom niet vanuit de werk stroom hervatten.</span><span class="sxs-lookup"><span data-stu-id="e33f5-111">You can't resume a workflow from within the workflow.</span></span>

## <a name="syntax"></a><span data-ttu-id="e33f5-112">Syntax</span><span class="sxs-lookup"><span data-stu-id="e33f5-112">Syntax</span></span>

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a><span data-ttu-id="e33f5-113">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="e33f5-113">Detailed description</span></span>

<span data-ttu-id="e33f5-114">De `Suspend-Workflow` werk stroom wordt tijdelijk gestopt en retourneert een taak object dat de werk stroom taak vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e33f5-114">The `Suspend-Workflow` temporarily stops the workflow and returns a job object that represents the workflow job.</span></span> <span data-ttu-id="e33f5-115">Er wordt een taak object geretourneerd, zelfs als u de werk stroom niet als een taak hebt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="e33f5-115">A job object is returned even if you didn't run the workflow as a job.</span></span> <span data-ttu-id="e33f5-116">Bijvoorbeeld, bijvoorbeeld met behulp van de algemene para meter **AsJob** workflow.</span><span class="sxs-lookup"><span data-stu-id="e33f5-116">For example, such as by using the **AsJob** workflow common parameter.</span></span> <span data-ttu-id="e33f5-117">De taak status is **onderbroken**.</span><span class="sxs-lookup"><span data-stu-id="e33f5-117">The job state is **Suspended**.</span></span>

<span data-ttu-id="e33f5-118">U kunt de taak-cmdlets gebruiken om de onderbroken werk stroom taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="e33f5-118">You can use the job cmdlets to manage the suspended workflow job.</span></span> <span data-ttu-id="e33f5-119">Gebruik de cmdlet om de werk stroom taak te hervatten `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-119">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span>

<span data-ttu-id="e33f5-120">Wanneer u de werk stroom taak hervat, wordt de werk stroom hervat vanaf de opdracht die volgt op de `Suspend-Workflow` activiteit.</span><span class="sxs-lookup"><span data-stu-id="e33f5-120">When you resume the workflow job, the workflow resumes at the command that follows the `Suspend-Workflow` activity.</span></span>

<span data-ttu-id="e33f5-121">De volgende werk stroom bevat bijvoorbeeld de `Suspend-Workflow` activiteit.</span><span class="sxs-lookup"><span data-stu-id="e33f5-121">For example, the following workflow includes the `Suspend-Workflow` activity.</span></span>
<span data-ttu-id="e33f5-122">Wanneer u de werk stroom uitvoert, wordt de `Get-Date` activiteit uitgevoerd, wordt de uitvoer ervan opgeslagen in de `$a` variabele, wordt de werk stroom onderbroken en wordt een taak object geretourneerd dat de onderbroken werk stroom vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="e33f5-122">When you run the workflow, it runs the `Get-Date` activity, saves its output in the `$a` variable, and then suspends the workflow, and returns a job object that represents the suspended workflow.</span></span> <span data-ttu-id="e33f5-123">Het taak type is **PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="e33f5-123">The job type is **PSWorkflowJob**.</span></span>

<span data-ttu-id="e33f5-124">U kunt de taak-cmdlets, zoals `Get-Job` , gebruiken om de werk stroom taak te beheren.</span><span class="sxs-lookup"><span data-stu-id="e33f5-124">You can use the job cmdlets, such as `Get-Job`, to manage the workflow job.</span></span>

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a><span data-ttu-id="e33f5-125">Een werk stroom taak hervatten</span><span class="sxs-lookup"><span data-stu-id="e33f5-125">Resuming a workflow job</span></span>

<span data-ttu-id="e33f5-126">Gebruik de cmdlet om de werk stroom taak te hervatten `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-126">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="e33f5-127">De `Resume-Job` cmdlet retourneert onmiddellijk het object van de werk stroom taak, zelfs als dit nog niet is hervat.</span><span class="sxs-lookup"><span data-stu-id="e33f5-127">The `Resume-Job` cmdlet returns the workflow job object immediately, even though it might not yet be resumed.</span></span> <span data-ttu-id="e33f5-128">Als u wilt wachten tot de taak wordt hervat, gebruikt u de para meter **wait** of gebruikt `Get-Job` u de cmdlet om het huidige taak object op te halen.</span><span class="sxs-lookup"><span data-stu-id="e33f5-128">To wait for the job to be resumed, use the **Wait** parameter, or use the `Get-Job` cmdlet to get the current job object.</span></span>

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a><span data-ttu-id="e33f5-129">De uitvoer van een werk stroom taak ophalen</span><span class="sxs-lookup"><span data-stu-id="e33f5-129">Getting the output of a workflow job</span></span>

<span data-ttu-id="e33f5-130">Gebruik de cmdlet om de uitvoer van een werk stroom taak op te halen `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="e33f5-130">To get the output of a workflow job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="e33f5-131">In de uitvoer ziet u dat de werk stroom is hervat bij de opdracht die de `Suspend-Workflow` cmdlet volgde.</span><span class="sxs-lookup"><span data-stu-id="e33f5-131">The output shows that the workflow resumed at the command that followed the `Suspend-Workflow` cmdlet.</span></span> <span data-ttu-id="e33f5-132">De waarde van de `$a` variabele, die vóór de onderbreking is ingevuld, is beschikbaar voor de werk stroom wanneer deze wordt hervat.</span><span class="sxs-lookup"><span data-stu-id="e33f5-132">The value of the `$a` variable, which was populated before the suspension, is available to the workflow when it resumes.</span></span>

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a><span data-ttu-id="e33f5-133">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e33f5-133">See also</span></span>

[<span data-ttu-id="e33f5-134">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="e33f5-134">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="e33f5-135">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="e33f5-135">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="e33f5-136">[PSWorkflow](xref:PSWorkflow) -cmdlets</span><span class="sxs-lookup"><span data-stu-id="e33f5-136">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="e33f5-137">Handleiding voor werkstromen</span><span class="sxs-lookup"><span data-stu-id="e33f5-137">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="e33f5-138">Een Windows PowerShell-werkstroom schrijven</span><span class="sxs-lookup"><span data-stu-id="e33f5-138">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
