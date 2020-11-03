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
# <a name="about-inlinescript"></a>Over InlineScript

## <a name="short-description"></a>Korte beschrijving

Beschrijft de `InlineScript` activiteit, waarmee Power shell-opdrachten in een werk stroom worden uitgevoerd.

## <a name="long-description"></a>Lange beschrijving

`InlineScript`Met de activiteit worden opdrachten uitgevoerd in de werk stroom van een gedeelde Power shell-sessie. `InlineScript` is alleen geldig in werk stromen.

## <a name="syntax"></a>Syntax

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a>Gedetailleerde beschrijving

`InlineScript`Met de activiteit worden opdrachten in een gedeelde Power shell-sessie uitgevoerd. U kunt deze in een werk stroom insluiten om opdrachten uit te voeren die gegevens en opdrachten delen die niet op een andere manier geldig zijn in een werk stroom.

Het `InlineScript` script blok kan alle geldige Power shell-opdrachten en-expressies bevatten. Omdat de opdrachten en expressies in een `InlineScript` script blok in dezelfde sessie worden uitgevoerd, delen ze alle status en gegevens, met inbegrip van geïmporteerde modules en de waarden van variabelen.

U kunt een `InlineScript` activiteit overal in een werk stroom of geneste werk stroom plaatsen, met inbegrip van een lus-of controle-instructie of een parallel-of sequence-script blok.

De `InlineScript` activiteit heeft de algemene activiteiten parameters, waaronder **PSPersist**. De opdrachten en expressies in een `InlineScript` script blok hebben echter niet de werk stroom functies, zoals controle punten, of persistentie, werk stroom of activiteit algemene para meters. Zie [about_ActivityCommonParameters](about_ActivityCommonParameters.md)voor meer informatie.

## <a name="inlinescript-variables"></a>InlineScript variabelen

Standaard zijn de variabelen die in een werk stroom zijn gedefinieerd, niet zichtbaar voor de opdrachten in het `InlineScript` script blok. Als u werk stroom variabelen zichtbaar wilt maken voor `InlineScript` , gebruikt u de `$Using` aanpassings functie voor bereik. De `$Using` aanpassing van het bereik is slechts eenmaal vereist voor elke variabele in de `InlineScript` .

Zie about_Remote_Variables voor meer informatie over de `$Using` aanpassing van het [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)bereik.

In het volgende voor beeld ziet `$Using` u dat de waarde van de `$a` werk stroom variabele op het hoogste niveau beschikbaar is voor de opdrachten in het- `InlineScript` script blok.

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

## <a name="returning-variables-in-inlinescript"></a>Variabelen retour neren in InlineScript

`InlineScript` opdrachten kunnen de waarde wijzigen van de variabele die vanuit het werk stroom bereik is geïmporteerd, maar de wijzigingen zijn niet zichtbaar in het werk stroom bereik. Als u ze zichtbaar wilt maken, retourneert u de gewijzigde waarde naar het werk stroom bereik, zoals wordt weer gegeven in het volgende voor beeld.

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
> Een instructie met de `$Using` bereik aanpassing moet vóór elk gebruik van de variabele in het script blok worden weer gegeven `InlineScript` .

## <a name="running-in-process"></a>In-process uitvoeren

Ter verbetering van de betrouw baarheid, worden de opdrachten in het `InlineScript` script blok uitgevoerd in hun eigen proces, gescheiden van het proces waarin de werk stroom wordt uitgevoerd, en retour neren ze hun uitvoer naar het werk stroom proces.

Als u Power shell wilt gebruiken om de `InlineScript` activiteit in het werk stroom proces uit te voeren, verwijdert u de `InlineScript` waarde van de eigenschap **OutOfProcessActivity** van de sessie configuratie, zoals met behulp van de- `New-PSWorkflowExecutionOption` cmdlet.

### <a name="example"></a>Voorbeeld

De `InlineScript` in de volgende werk stroom bevat opdrachten die geldig zijn in Power shell, maar die niet geldig zijn in werk stromen. Bijvoorbeeld de `New-Object` cmdlet met de para meter **ComObject** .

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

## <a name="see-also"></a>Zie ook

[about_ActivityCommonParameters](about_ActivityCommonParameters.md)

[about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)

[PSWorkflow](xref:PSWorkflow) -cmdlets

[Handleiding voor werkstromen](/previous-versions/powershell/scripting/components/workflows-guide)

[Een Windows PowerShell-werkstroom schrijven](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
