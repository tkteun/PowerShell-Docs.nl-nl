---
description: Beschrijft de Checkpoint-Workflow activiteit, waarmee een controle punt in een werk stroom wordt gebruikt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_checkpoint-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Checkpoint werk stroom
ms.openlocfilehash: 223deb07ff6ed387cf04736116ea0ce3f998bb59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252407"
---
# <a name="about-checkpoint-workflow"></a><span data-ttu-id="82b6c-104">Over Checkpoint-Workflow</span><span class="sxs-lookup"><span data-stu-id="82b6c-104">About Checkpoint-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="82b6c-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="82b6c-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="82b6c-106">Beschrijft de Checkpoint-Workflow activiteit, waarmee een controle punt in een werk stroom wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="82b6c-106">Describes the Checkpoint-Workflow activity, which takes a checkpoint in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="82b6c-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="82b6c-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="82b6c-108">De activiteit Checkpoint-Workflow maakt een controle punt, waarmee de status en gegevens in de werk stroom worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="82b6c-108">The Checkpoint-Workflow activity takes a checkpoint, which saves state and data in the workflow.</span></span> <span data-ttu-id="82b6c-109">Als de werk stroom wordt onderbroken of onderbroken, kan deze worden hervat vanaf het laatste controle punt en niet opnieuw moeten worden gestart.</span><span class="sxs-lookup"><span data-stu-id="82b6c-109">If the workflow is suspended or interrupted, it can be resumed from the most recent checkpoint, rather than having to be restarted.</span></span>

<span data-ttu-id="82b6c-110">De Checkpoint-Workflow-activiteit is alleen geldig in een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="82b6c-110">The Checkpoint-Workflow activity is valid only in a workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="82b6c-111">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="82b6c-111">SYNTAX</span></span>

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

<span data-ttu-id="82b6c-112">De Checkpoint-Workflow-activiteit accepteert geen para meters, waaronder algemene para meters en algemene werk stroom parameters.</span><span class="sxs-lookup"><span data-stu-id="82b6c-112">The Checkpoint-Workflow activity does not accept any parameters, including common parameters and workflow common parameters.</span></span>

<span data-ttu-id="82b6c-113">U kunt het Checkpoint-Activity controle punt overal in een werk stroom plaatsen na de CmdletBinding-of param-instructie.</span><span class="sxs-lookup"><span data-stu-id="82b6c-113">You can place the Checkpoint-Activity checkpoint anywhere in a workflow after the CmdletBinding or Param statement.</span></span> <span data-ttu-id="82b6c-114">Bij het plaatsen van controle punten kunt u echter de prestaties van de gegevens verzamelen en deze naar de schijf schrijven op de computer waarop de werk stroom wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="82b6c-114">However, when placing checkpoints, consider the performance cost of collecting the data and writing it to disk on the computer that is running the workflow.</span></span>

<span data-ttu-id="82b6c-115">Zorg ervoor dat de tijd die nodig is om een sectie van de werk stroom opnieuw uit te voeren als deze wordt onderbroken, groter is dan de tijd die nodig is om de status van het controle punt en de gegevens naar de schijf te schrijven.</span><span class="sxs-lookup"><span data-stu-id="82b6c-115">Be sure that the time it takes to rerun a section of the workflow if it is interrupted is greater than the time it takes to write the checkpoint state and data to disk.</span></span>

<span data-ttu-id="82b6c-116">Overweeg het nemen van controle punten na kritieke stappen, zodat de werk stroom kan worden hervat in plaats van opnieuw te worden gestart.</span><span class="sxs-lookup"><span data-stu-id="82b6c-116">Consider taking checkpoints after critical steps so the workflow can be resumed rather than restarted.</span></span> <span data-ttu-id="82b6c-117">Neem bijvoorbeeld een controle punt na opdrachten die niet idempotent zijn.</span><span class="sxs-lookup"><span data-stu-id="82b6c-117">For example, take a checkpoint after commands that are not idempotent.</span></span>

### <a name="about-checkpoints"></a><span data-ttu-id="82b6c-118">OVER CONTROLE PUNTEN</span><span class="sxs-lookup"><span data-stu-id="82b6c-118">ABOUT CHECKPOINTS</span></span>

<span data-ttu-id="82b6c-119">Een controle punt is een moment opname van de huidige status van de werk stroom, met inbegrip van de huidige waarden van variabelen en een uitvoer die tot dat punt wordt gegenereerd, en slaat deze op schijf op.</span><span class="sxs-lookup"><span data-stu-id="82b6c-119">A checkpoint is a snapshot of the current state of the workflow, including the current values of variables, and any output generated up to that point, and it saves it to disk.</span></span>

<span data-ttu-id="82b6c-120">Als een werk stroom wordt onderbroken, met opzet of per ongeluk, gebruikt Windows Power shell-werk stroom automatisch de gegevens in het nieuwste controle punt om de werk stroom te herstellen en weer te hervatten.</span><span class="sxs-lookup"><span data-stu-id="82b6c-120">If a workflow is interrupted, intentionally or unintentionally, Windows PowerShell Workflow automatically uses the data in newest checkpoint to recover and resume the workflow.</span></span>

<span data-ttu-id="82b6c-121">Wanneer u de werk stroom uitvoert als een taak, bijvoorbeeld met behulp van de algemene para meter AsJob workflow, worden de controle punten van werk stromen bewaard totdat u de taak verwijdert, bijvoorbeeld met behulp van de cmdlet Remove-Job.</span><span class="sxs-lookup"><span data-stu-id="82b6c-121">When you run the workflow as a job, such as by using the AsJob workflow common parameter, the workflow checkpoints are retained until you delete the job, such as by using the Remove-Job cmdlet.</span></span>
<span data-ttu-id="82b6c-122">Anders worden werk stroom controlepunten verwijderd wanneer de werk stroom is voltooid.</span><span class="sxs-lookup"><span data-stu-id="82b6c-122">Otherwise, workflow checkpoints are deleted when the workflow completes.</span></span>

### <a name="other-checkpointing-techniques"></a><span data-ttu-id="82b6c-123">ANDERE TECHNIEKEN VOOR CONTROLE PUNTEN</span><span class="sxs-lookup"><span data-stu-id="82b6c-123">OTHER CHECKPOINTING TECHNIQUES</span></span>

<span data-ttu-id="82b6c-124">Naast de Checkpoint-Workflow-activiteit, ondersteunt de Windows Power shell-werk stroom andere controlepunt technieken, waaronder de volgende:</span><span class="sxs-lookup"><span data-stu-id="82b6c-124">In addition to the Checkpoint-Workflow activity, Windows PowerShell Workflow supports other checkpointing techniques, including the following:</span></span>

- <span data-ttu-id="82b6c-125">Algemene para meter voor de PSPersist-werk stroom</span><span class="sxs-lookup"><span data-stu-id="82b6c-125">PSPersist workflow common parameter</span></span>
- <span data-ttu-id="82b6c-126">Algemene para meter PSPersist-activiteit</span><span class="sxs-lookup"><span data-stu-id="82b6c-126">PSPersist activity common parameter</span></span>
- <span data-ttu-id="82b6c-127">De variabele PSPersistPreference (in een werk stroom)</span><span class="sxs-lookup"><span data-stu-id="82b6c-127">PSPersistPreference variable (in a workflow)</span></span>

<span data-ttu-id="82b6c-128">Zie "controle punten toevoegen aan een werk stroom" voor meer informatie over het toevoegen van een controle punt aan een werk stroom.</span><span class="sxs-lookup"><span data-stu-id="82b6c-128">For more information about adding a checkpoint to a workflow, see "How to Add Checkpoints to a Workflow."</span></span>

## <a name="examples"></a><span data-ttu-id="82b6c-129">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="82b6c-129">EXAMPLES</span></span>

<span data-ttu-id="82b6c-130">De volgende werk stroom bevat een aanroep van de Checkpoint-Workflow-activiteit nadat u een langlopende functie en een script voor het delen van gegevens hebt voltooid.</span><span class="sxs-lookup"><span data-stu-id="82b6c-130">The following workflow includes a call to the Checkpoint-Workflow activity after completing a long-running function and a script that share data.</span></span>

```powershell
Workflow Test-Workflow
{
    $a = Invoke-LongRunningFunction
    InlineScript { \\Server\Share\Get-DataPacks.ps1 $Using:a}
    Checkpoint-Workflow

    Invoke-LongRunningFunction
    {
        ...
    }
}
```

## <a name="see-also"></a><span data-ttu-id="82b6c-131">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="82b6c-131">SEE ALSO</span></span>

[<span data-ttu-id="82b6c-132">Een Windows PowerShell-werkstroom schrijven</span><span class="sxs-lookup"><span data-stu-id="82b6c-132">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
