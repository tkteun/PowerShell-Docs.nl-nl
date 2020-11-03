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
# <a name="about-suspend-workflow"></a>Over Suspend-Workflow

## <a name="short-description"></a>Korte beschrijving

Beschrijft de `Suspend-Workflow` activiteit, waardoor de werk stroom wordt onderbroken waarin de activiteit wordt weer gegeven.

## <a name="long-description"></a>Lange beschrijving

De `Suspend-Workflow` activiteit stopt de verwerking van werk stromen tijdelijk vanuit de werk stroom. Voordat u de werk stroom uitbreekt, wordt een controle punt gebruikt, zodat de status en gegevens van de werk stroom behouden blijven en de werk stroom kan worden hervat vanaf het onderbrekings punt.

De gebruiker die de werk stroom uitvoert, maakt gebruik van de cmdlet om de werk stroom te hervatten `Resume-Job` . U kunt een werk stroom niet vanuit de werk stroom hervatten.

## <a name="syntax"></a>Syntax

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a>Gedetailleerde beschrijving

De `Suspend-Workflow` werk stroom wordt tijdelijk gestopt en retourneert een taak object dat de werk stroom taak vertegenwoordigt. Er wordt een taak object geretourneerd, zelfs als u de werk stroom niet als een taak hebt uitgevoerd. Bijvoorbeeld, bijvoorbeeld met behulp van de algemene para meter **AsJob** workflow. De taak status is **onderbroken**.

U kunt de taak-cmdlets gebruiken om de onderbroken werk stroom taak te beheren. Gebruik de cmdlet om de werk stroom taak te hervatten `Resume-Job` .

Wanneer u de werk stroom taak hervat, wordt de werk stroom hervat vanaf de opdracht die volgt op de `Suspend-Workflow` activiteit.

De volgende werk stroom bevat bijvoorbeeld de `Suspend-Workflow` activiteit.
Wanneer u de werk stroom uitvoert, wordt de `Get-Date` activiteit uitgevoerd, wordt de uitvoer ervan opgeslagen in de `$a` variabele, wordt de werk stroom onderbroken en wordt een taak object geretourneerd dat de onderbroken werk stroom vertegenwoordigt. Het taak type is **PSWorkflowJob**.

U kunt de taak-cmdlets, zoals `Get-Job` , gebruiken om de werk stroom taak te beheren.

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

## <a name="resuming-a-workflow-job"></a>Een werk stroom taak hervatten

Gebruik de cmdlet om de werk stroom taak te hervatten `Resume-Job` . De `Resume-Job` cmdlet retourneert onmiddellijk het object van de werk stroom taak, zelfs als dit nog niet is hervat. Als u wilt wachten tot de taak wordt hervat, gebruikt u de para meter **wait** of gebruikt `Get-Job` u de cmdlet om het huidige taak object op te halen.

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

## <a name="getting-the-output-of-a-workflow-job"></a>De uitvoer van een werk stroom taak ophalen

Gebruik de cmdlet om de uitvoer van een werk stroom taak op te halen `Receive-Job` . In de uitvoer ziet u dat de werk stroom is hervat bij de opdracht die de `Suspend-Workflow` cmdlet volgde. De waarde van de `$a` variabele, die vóór de onderbreking is ingevuld, is beschikbaar voor de werk stroom wanneer deze wordt hervat.

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

## <a name="see-also"></a>Zie ook

[about_Workflows](about_Workflows.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

[PSWorkflow](xref:PSWorkflow) -cmdlets

[Handleiding voor werkstromen](/previous-versions/powershell/scripting/components/workflows-guide)

[Een Windows PowerShell-werkstroom schrijven](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
