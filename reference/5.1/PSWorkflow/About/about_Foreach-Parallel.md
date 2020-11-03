---
description: Beschrijft de `ForEach -Parallel` taal constructie in de Windows Power shell-werk stroom.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach parallel
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252406"
---
# <a name="about-foreach-parallel"></a><span data-ttu-id="1838d-104">Over Foreach-Parallel</span><span class="sxs-lookup"><span data-stu-id="1838d-104">About Foreach-Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="1838d-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1838d-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="1838d-106">Beschrijft de `ForEach -Parallel` taal constructie in de Windows Power shell-werk stroom.</span><span class="sxs-lookup"><span data-stu-id="1838d-106">Describes the `ForEach -Parallel` language construct in Windows PowerShell Workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="1838d-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1838d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="1838d-108">De **parallelle** para meter van het `ForEach` sleutel woord voert de opdrachten in een `ForEach` script blok één keer uit voor elk item in een opgegeven verzameling.</span><span class="sxs-lookup"><span data-stu-id="1838d-108">The **Parallel** parameter of the `ForEach` keyword runs the commands in a `ForEach` script block once for each item in a specified collection.</span></span>

<span data-ttu-id="1838d-109">De items in de verzameling, zoals een schijf in een verzameling schijven, worden parallel verwerkt.</span><span class="sxs-lookup"><span data-stu-id="1838d-109">The items in the collection, such as a disk in a collection of disks, are processed in parallel.</span></span> <span data-ttu-id="1838d-110">De opdrachten in het script blok worden opeenvolgend uitgevoerd op elk item in de verzameling.</span><span class="sxs-lookup"><span data-stu-id="1838d-110">The commands in the script block run sequentially on each item in the collection.</span></span>

<span data-ttu-id="1838d-111">`ForEach -Parallel` is alleen geldig in een Windows Power shell-werk stroom.</span><span class="sxs-lookup"><span data-stu-id="1838d-111">`ForEach -Parallel` is valid only in a Windows PowerShell Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="1838d-112">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="1838d-112">SYNTAX</span></span>

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a><span data-ttu-id="1838d-113">GEDETAILLEERDE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="1838d-113">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="1838d-114">Net als de instructie ForEach in Windows Power shell moet de variabele die verzameling bevat `$<collection>` , worden gedefinieerd vóór de `ForEach -Parallel` instructie, maar de variabele die het huidige item vertegenwoordigt, `$<item>` wordt gedefinieerd in de `ForEach -Parallel` instructie.</span><span class="sxs-lookup"><span data-stu-id="1838d-114">Like the ForEach statement in Windows PowerShell, the variable that contains collection `$<collection>` must be defined before the `ForEach -Parallel` statement, but the variable that represents the current item `$<item>` is defined in the `ForEach -Parallel` statement.</span></span>

<span data-ttu-id="1838d-115">De `ForEach -Parallel` Construct wijkt af van het `ForEach` sleutel woord en de **parallelle** para meter.</span><span class="sxs-lookup"><span data-stu-id="1838d-115">The `ForEach -Parallel` construct is different from the `ForEach` keyword and the **Parallel** parameter.</span></span> <span data-ttu-id="1838d-116">`ForEach`Met het tref woord worden de items in de verzameling in volg orde verwerkt.</span><span class="sxs-lookup"><span data-stu-id="1838d-116">The `ForEach` keyword processes the items in the collection in sequence.</span></span> <span data-ttu-id="1838d-117">De **parallelle** para meter voert opdrachten parallel uit in een script blok.</span><span class="sxs-lookup"><span data-stu-id="1838d-117">The **Parallel** parameter runs commands in a script block in parallel.</span></span> <span data-ttu-id="1838d-118">U kunt een parallel script blok insluiten in een `ForEach -Parallel` script blok.</span><span class="sxs-lookup"><span data-stu-id="1838d-118">You can enclose a Parallel script block in a `ForEach -Parallel` script block.</span></span>

<span data-ttu-id="1838d-119">De doel computers in een werk stroom, zoals die zijn opgegeven door de algemene para meter **PSComputerName** workflow, worden altijd parallel verwerkt.</span><span class="sxs-lookup"><span data-stu-id="1838d-119">The target computers in a workflow, such as those specified by the **PSComputerName** workflow common parameter, are always processed in parallel.</span></span>
<span data-ttu-id="1838d-120">U hoeft het `ForEach -Parallel` tref woord voor dit doel niet op te geven.</span><span class="sxs-lookup"><span data-stu-id="1838d-120">You do not need to specify the `ForEach -Parallel` keyword for this purpose.</span></span>

### <a name="examples"></a><span data-ttu-id="1838d-121">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1838d-121">EXAMPLES</span></span>

<span data-ttu-id="1838d-122">De volgende werk stroom bevat een `ForEach -Parallel` instructie die de schijven verwerkt die door de `Get-Disk` activiteit worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="1838d-122">The following workflow contains a `ForEach -Parallel` statement that processes the disks that the `Get-Disk` activity gets.</span></span> <span data-ttu-id="1838d-123">De opdrachten in het `ForEach -Parallel` script blok worden opeenvolgend uitgevoerd, maar ze worden parallel uitgevoerd op de schijven.</span><span class="sxs-lookup"><span data-stu-id="1838d-123">The commands in the `ForEach -Parallel` script block run sequentially, but they run on the disks in parallel.</span></span> <span data-ttu-id="1838d-124">De schijven kunnen gelijktijdig en in een wille keurige volg orde worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="1838d-124">The disks might be processed concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="1838d-125">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="1838d-125">SEE ALSO</span></span>

[<span data-ttu-id="1838d-126">Een script werk stroom schrijven</span><span class="sxs-lookup"><span data-stu-id="1838d-126">Writing a Script Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[<span data-ttu-id="1838d-127">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="1838d-127">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[<span data-ttu-id="1838d-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="1838d-128">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="1838d-129">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="1838d-129">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="1838d-130">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="1838d-130">about_Workflows</span></span>](about_Workflows.md)
