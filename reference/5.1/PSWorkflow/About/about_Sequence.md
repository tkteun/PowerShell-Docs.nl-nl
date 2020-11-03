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
# <a name="about-sequence"></a>Volg orde

## <a name="short-description"></a>Korte beschrijving

Hierin wordt het `Sequence` tref woord beschreven waarmee geselecteerde activiteiten opeenvolgend worden uitgevoerd.

## <a name="long-description"></a>Lange beschrijving

Met het `Sequence` sleutel woord worden de geselecteerde werk stroom activiteiten sequentieel uitgevoerd. Werk stroom activiteiten worden uitgevoerd in de volg orde waarin ze worden weer gegeven en niet gelijktijdig worden uitgevoerd. Het `Sequence` sleutel woord is alleen geldig in een Power shell-werk stroom.

Het `Sequence` sleutel woord wordt gebruikt in een- `Parallel` script blok om de geselecteerde opdrachten sequentieel uit te voeren.

Omdat werk stroom activiteiten standaard sequentieel worden uitgevoerd, `Sequence` is het sleutel woord alleen effectief in een- `Parallel` script blok. Als het `Sequence` sleutel woord niet is opgenomen in een `Parallel` -script blok, is dit geldig, maar niet effectief.

`Sequence`Met het script blok kunt u meerdere opdrachten parallel uitvoeren door de afhankelijke opdrachten sequentieel uit te voeren.

## <a name="syntax"></a>Syntax

### <a name="workflow-using-sequence"></a>Werk stroom met behulp van volg orde

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

### <a name="workflow-using-parallel-and-sequence"></a>Werk stroom met parallel en sequentieel

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

## <a name="detailed-description"></a>Gedetailleerde beschrijving

De opdrachten in een- `Parallel` script blok kunnen gelijktijdig worden uitgevoerd. De volg orde waarin ze worden uitgevoerd, wordt niet bepaald. Deze functie verbetert de prestaties van een script werk stroom.

U kunt een `Sequence` script blok gebruiken om geselecteerde activiteiten sequentieel uit te voeren, zelfs als de activiteiten in een script blok worden weer gegeven `Parallel` .

De activiteiten in een `Sequence` script blok worden opeenvolgend uitgevoerd in de volg orde waarin ze worden weer gegeven. Een activiteit in een `Sequence` script blok start pas nadat de vorige activiteit is voltooid.

Wanneer het `Sequence` script blok echter in een script blok wordt weer gegeven `Parallel` , wordt de volg orde waarin het `Sequence` script blok wordt uitgevoerd, niet bepaald. Dit kan vóór, na of gelijktijdig met andere activiteiten in het `Parallel` script blok worden uitgevoerd.

De volgende werk stroom bevat bijvoorbeeld een `Parallel` script blok dat activiteiten uitvoert die processen en services op de computer ophalen. Het `Parallel` script blok bevat een `Sequence` script blok waarmee informatie uit een bestand wordt opgehaald en de informatie wordt gebruikt als invoer voor een script.

De `Get-Process` `Get-Service` opdrachten, en zijn onafhankelijk van elkaar. De opdrachten kunnen gelijktijdig of in een wille keurige volg orde worden uitgevoerd. Maar de opdracht die de hotfix-informatie ophaalt, moet worden uitgevoerd voordat de opdracht wordt gebruikt.

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

## <a name="see-also"></a>Zie ook

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-parallel](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Parallel](about_Parallel.md)

[about_Workflows](about_Workflows.md)

[Een werkstroom maken met behulp van een Windows PowerShell-script](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
