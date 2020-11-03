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
# <a name="about-parallel"></a>Over parallel

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt het sleutel woord parallel beschreven, waarmee de activiteiten in een werk stroom parallel worden uitgevoerd.

## <a name="long-description"></a>LANGE BESCHRIJVING

Met het sleutel woord parallel worden werk stroom activiteiten parallel uitgevoerd. Dit sleutel woord is alleen geldig in de Windows Power shell-werk stroom.

### <a name="syntax"></a>SYNTAXIS

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

## <a name="detailed-description"></a>GEDETAILLEERDE BESCHRIJVING

De opdrachten in een parallel-script blok kunnen gelijktijdig worden uitgevoerd. De volg orde waarin ze worden uitgevoerd, wordt niet bepaald.

De volgende werk stroom bevat bijvoorbeeld een parallel-script blok dat activiteiten uitvoert die processen en services op de computer ophalen. Omdat de opdrachten Get-Process en Get-Service onafhankelijk van elkaar zijn, kunnen ze gelijktijdig en in wille keurige volg orde worden uitgevoerd.

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

Het uitvoeren van parallelle opdrachten is zeer efficiënt en vermindert de tijd die nodig is om een werk stroom aanzienlijk te volt ooien.

Als u geselecteerde opdrachten in een sequentieel parallel script-blok wilt uitvoeren, gebruikt u het tref woord sequence. Zie about_Sequence voor meer informatie.

Als u een parallel script blok wilt uitvoeren voor items in een verzameling, gebruikt u de zoek woorden ForEach of ForEach-parallel.

## <a name="see-also"></a>ZIE OOK

["Een script werk stroom schrijven"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))

[about_ForEach](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[about_ForEach-parallel](about_ForEach-Parallel.md)

[about_Language_Keywords](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[about_Sequence](about_Sequence.md)

[about_Workflows](about_workflows.md)
