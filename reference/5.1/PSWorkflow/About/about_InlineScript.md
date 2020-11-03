---
description: Beschrijft de `InlineScript` activiteit, waarmee Power shell-opdrachten in een werk stroom worden uitgevoerd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_inlinescript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_InlineScript
ms.openlocfilehash: 2eaeb02c6441865551b586e27a39c4000826752b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252405"
---
# <a name="about-inlinescript"></a><span data-ttu-id="495d6-104">Over InlineScript</span><span class="sxs-lookup"><span data-stu-id="495d6-104">About InlineScript</span></span>

## <a name="short-description"></a><span data-ttu-id="495d6-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="495d6-105">Short description</span></span>

<span data-ttu-id="495d6-106">Beschrijft de `InlineScript` activiteit, waarmee Power shell-opdrachten in een werk stroom worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="495d6-106">Describes the `InlineScript` activity, that runs PowerShell commands in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="495d6-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="495d6-107">Long description</span></span>

<span data-ttu-id="495d6-108">`InlineScript`Met de activiteit worden opdrachten uitgevoerd in de werk stroom van een gedeelde Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="495d6-108">The `InlineScript` activity runs commands in a shared PowerShell session's workflow.</span></span> <span data-ttu-id="495d6-109">`InlineScript` is alleen geldig in werk stromen.</span><span class="sxs-lookup"><span data-stu-id="495d6-109">`InlineScript` is only valid in workflows.</span></span>

## <a name="syntax"></a><span data-ttu-id="495d6-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="495d6-110">Syntax</span></span>

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a><span data-ttu-id="495d6-111">Gedetailleerde beschrijving</span><span class="sxs-lookup"><span data-stu-id="495d6-111">Detailed description</span></span>

<span data-ttu-id="495d6-112">`InlineScript`Met de activiteit worden opdrachten in een gedeelde Power shell-sessie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="495d6-112">The `InlineScript` activity runs commands in a shared PowerShell session.</span></span> <span data-ttu-id="495d6-113">U kunt deze in een werk stroom insluiten om opdrachten uit te voeren die gegevens en opdrachten delen die niet op een andere manier geldig zijn in een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="495d6-113">You can include it in a workflow to run commands that share data and commands that aren't otherwise valid in a workflow.</span></span>

<span data-ttu-id="495d6-114">Het `InlineScript` script blok kan alle geldige Power shell-opdrachten en-expressies bevatten.</span><span class="sxs-lookup"><span data-stu-id="495d6-114">The `InlineScript` script block can include all valid PowerShell commands and expressions.</span></span> <span data-ttu-id="495d6-115">Omdat de opdrachten en expressies in een `InlineScript` script blok in dezelfde sessie worden uitgevoerd, delen ze alle status en gegevens, met inbegrip van geïmporteerde modules en de waarden van variabelen.</span><span class="sxs-lookup"><span data-stu-id="495d6-115">Because the commands and expressions in an `InlineScript` script block run in the same session, they share all state and data, including imported modules and the values of variables.</span></span>

<span data-ttu-id="495d6-116">U kunt een `InlineScript` activiteit overal in een werk stroom of geneste werk stroom plaatsen, met inbegrip van een lus-of controle-instructie of een parallel-of sequence-script blok.</span><span class="sxs-lookup"><span data-stu-id="495d6-116">You can place an `InlineScript` activity anywhere in a workflow or nested workflow, including inside a loop or control statement or a Parallel or Sequence script block.</span></span>

<span data-ttu-id="495d6-117">De `InlineScript` activiteit heeft de algemene activiteiten parameters, waaronder **PSPersist**.</span><span class="sxs-lookup"><span data-stu-id="495d6-117">The `InlineScript` activity has the activity common parameters, including **PSPersist**.</span></span> <span data-ttu-id="495d6-118">De opdrachten en expressies in een `InlineScript` script blok hebben echter niet de werk stroom functies, zoals controle punten, of persistentie, werk stroom of activiteit algemene para meters.</span><span class="sxs-lookup"><span data-stu-id="495d6-118">However, the commands and expressions in an `InlineScript` script block don't have the workflow features such as checkpointing, or persistence, and workflow or activity common parameters.</span></span> <span data-ttu-id="495d6-119">Zie [about_ActivityCommonParameters](about_ActivityCommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="495d6-119">For more information, see [about_ActivityCommonParameters](about_ActivityCommonParameters.md).</span></span>

## <a name="inlinescript-variables"></a><span data-ttu-id="495d6-120">InlineScript variabelen</span><span class="sxs-lookup"><span data-stu-id="495d6-120">InlineScript Variables</span></span>

<span data-ttu-id="495d6-121">Standaard zijn de variabelen die in een werk stroom zijn gedefinieerd, niet zichtbaar voor de opdrachten in het `InlineScript` script blok.</span><span class="sxs-lookup"><span data-stu-id="495d6-121">By default, the variables that are defined in a workflow aren't visible to the commands in the `InlineScript` script block.</span></span> <span data-ttu-id="495d6-122">Als u werk stroom variabelen zichtbaar wilt maken voor `InlineScript` , gebruikt u de `$Using` aanpassings functie voor bereik.</span><span class="sxs-lookup"><span data-stu-id="495d6-122">To make workflow variables visible to the `InlineScript`, use the `$Using` scope modifier.</span></span> <span data-ttu-id="495d6-123">De `$Using` aanpassing van het bereik is slechts eenmaal vereist voor elke variabele in de `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="495d6-123">The `$Using` scope modifier is required only once for each variable in the `InlineScript`.</span></span>

<span data-ttu-id="495d6-124">Zie about_Remote_Variables voor meer informatie over de `$Using` aanpassing van het [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)bereik.</span><span class="sxs-lookup"><span data-stu-id="495d6-124">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

<span data-ttu-id="495d6-125">In het volgende voor beeld ziet `$Using` u dat de waarde van de `$a` werk stroom variabele op het hoogste niveau beschikbaar is voor de opdrachten in het- `InlineScript` script blok.</span><span class="sxs-lookup"><span data-stu-id="495d6-125">The following example shows that the `$Using` scope modifier makes the value of the `$a` top-level workflow variable available to the commands in the `InlineScript` script block.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ## Without $Using, the $a workflow variable isn't visible
  ## in inline script.
  InlineScript {"Inline A0 = $a"}

  ## $Using imports the variable and its current value.
  InlineScript {"Inline A1 = $Using:a"}
}

Test-Workflow
```

```output
Inline A0 =
Inline A1 = 3
```

## <a name="returning-variables-in-inlinescript"></a><span data-ttu-id="495d6-126">Variabelen retour neren in InlineScript</span><span class="sxs-lookup"><span data-stu-id="495d6-126">Returning variables in InlineScript</span></span>

<span data-ttu-id="495d6-127">`InlineScript` opdrachten kunnen de waarde wijzigen van de variabele die vanuit het werk stroom bereik is geïmporteerd, maar de wijzigingen zijn niet zichtbaar in het werk stroom bereik.</span><span class="sxs-lookup"><span data-stu-id="495d6-127">`InlineScript` commands can change the value of the variable that was imported from workflow scope, but the changes aren't visible in workflow scope.</span></span> <span data-ttu-id="495d6-128">Als u ze zichtbaar wilt maken, retourneert u de gewijzigde waarde naar het werk stroom bereik, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="495d6-128">To make them visible, return the changed value to the workflow scope, as shown in the following example.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ##  Changes to the InlineScript variable value don't
  ##  change the workflow variable.
  InlineScript {
    $a = $Using:a+1;
    "Inline A = $a"
  }
  "Workflow A = $a"

  ##  To change the variable in workflow scope, return the
  ##  new value.
  $a = InlineScript {$b = $Using:a+1; $b}
  "Workflow New A = $a"
}

Test-Workflow
```

```output
Inline A = 4
Workflow A = 3
Workflow New A = 4
```

> [!NOTE]
> <span data-ttu-id="495d6-129">Een instructie met de `$Using` bereik aanpassing moet vóór elk gebruik van de variabele in het script blok worden weer gegeven `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="495d6-129">A statement with the `$Using` scope modifier should appear before any use of the variable in the `InlineScript` script block.</span></span>

## <a name="running-in-process"></a><span data-ttu-id="495d6-130">In-process uitvoeren</span><span class="sxs-lookup"><span data-stu-id="495d6-130">Running in-process</span></span>

<span data-ttu-id="495d6-131">Ter verbetering van de betrouw baarheid, worden de opdrachten in het `InlineScript` script blok uitgevoerd in hun eigen proces, gescheiden van het proces waarin de werk stroom wordt uitgevoerd, en retour neren ze hun uitvoer naar het werk stroom proces.</span><span class="sxs-lookup"><span data-stu-id="495d6-131">To improve reliability, the commands in the `InlineScript` script block run in their own process, separate from the process in which the workflow runs, and then return their output to the workflow process.</span></span>

<span data-ttu-id="495d6-132">Als u Power shell wilt gebruiken om de `InlineScript` activiteit in het werk stroom proces uit te voeren, verwijdert u de `InlineScript` waarde van de eigenschap **OutOfProcessActivity** van de sessie configuratie, zoals met behulp van de- `New-PSWorkflowExecutionOption` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="495d6-132">To direct PowerShell to run the `InlineScript` activity in the workflow process, remove the `InlineScript` value from the **OutOfProcessActivity** property of the session configuration, such as by using the `New-PSWorkflowExecutionOption` cmdlet.</span></span>

### <a name="example"></a><span data-ttu-id="495d6-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="495d6-133">Example</span></span>

<span data-ttu-id="495d6-134">De `InlineScript` in de volgende werk stroom bevat opdrachten die geldig zijn in Power shell, maar die niet geldig zijn in werk stromen.</span><span class="sxs-lookup"><span data-stu-id="495d6-134">The `InlineScript` in the following workflow includes commands that are valid in PowerShell but aren't valid in workflows.</span></span> <span data-ttu-id="495d6-135">Bijvoorbeeld de `New-Object` cmdlet met de para meter **ComObject** .</span><span class="sxs-lookup"><span data-stu-id="495d6-135">For example, the `New-Object` cmdlet with the **ComObject** parameter.</span></span>

```powershell
workflow Test-Workflow
{
  $ie = InlineScript {
    $ie = New-Object -ComObject InternetExplorer.Application -Property @{navigate2="www.microsoft.com"}

    $ie.Visible = $true
  }

  $ie
}

Test-Workflow
```

## <a name="see-also"></a><span data-ttu-id="495d6-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="495d6-136">See also</span></span>

[<span data-ttu-id="495d6-137">about_ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="495d6-137">about_ActivityCommonParameters</span></span>](about_ActivityCommonParameters.md)

[<span data-ttu-id="495d6-138">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="495d6-138">about_Remote_Variables</span></span>](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[<span data-ttu-id="495d6-139">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="495d6-139">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="495d6-140">[PSWorkflow](xref:PSWorkflow) -cmdlets</span><span class="sxs-lookup"><span data-stu-id="495d6-140">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="495d6-141">Handleiding voor werkstromen</span><span class="sxs-lookup"><span data-stu-id="495d6-141">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="495d6-142">Een Windows PowerShell-werkstroom schrijven</span><span class="sxs-lookup"><span data-stu-id="495d6-142">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
