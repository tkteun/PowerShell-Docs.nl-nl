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
# <a name="about-foreach-parallel"></a>Over Foreach-Parallel

## <a name="short-description"></a>KORTE BESCHRIJVING
Beschrijft de `ForEach -Parallel` taal constructie in de Windows Power shell-werk stroom.

## <a name="long-description"></a>LANGE BESCHRIJVING

De **parallelle** para meter van het `ForEach` sleutel woord voert de opdrachten in een `ForEach` script blok één keer uit voor elk item in een opgegeven verzameling.

De items in de verzameling, zoals een schijf in een verzameling schijven, worden parallel verwerkt. De opdrachten in het script blok worden opeenvolgend uitgevoerd op elk item in de verzameling.

`ForEach -Parallel` is alleen geldig in een Windows Power shell-werk stroom.

### <a name="syntax"></a>SYNTAXIS

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a>GEDETAILLEERDE BESCHRIJVING

Net als de instructie ForEach in Windows Power shell moet de variabele die verzameling bevat `$<collection>` , worden gedefinieerd vóór de `ForEach -Parallel` instructie, maar de variabele die het huidige item vertegenwoordigt, `$<item>` wordt gedefinieerd in de `ForEach -Parallel` instructie.

De `ForEach -Parallel` Construct wijkt af van het `ForEach` sleutel woord en de **parallelle** para meter. `ForEach`Met het tref woord worden de items in de verzameling in volg orde verwerkt. De **parallelle** para meter voert opdrachten parallel uit in een script blok. U kunt een parallel script blok insluiten in een `ForEach -Parallel` script blok.

De doel computers in een werk stroom, zoals die zijn opgegeven door de algemene para meter **PSComputerName** workflow, worden altijd parallel verwerkt.
U hoeft het `ForEach -Parallel` tref woord voor dit doel niet op te geven.

### <a name="examples"></a>VOORBEELDEN

De volgende werk stroom bevat een `ForEach -Parallel` instructie die de schijven verwerkt die door de `Get-Disk` activiteit worden opgehaald. De opdrachten in het `ForEach -Parallel` script blok worden opeenvolgend uitgevoerd, maar ze worden parallel uitgevoerd op de schijven. De schijven kunnen gelijktijdig en in een wille keurige volg orde worden verwerkt.

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

## <a name="see-also"></a>ZIE OOK

[Een script werk stroom schrijven](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)
