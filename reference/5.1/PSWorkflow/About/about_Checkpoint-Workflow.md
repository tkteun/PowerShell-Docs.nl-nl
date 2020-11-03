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
# <a name="about-checkpoint-workflow"></a>Over Checkpoint-Workflow

## <a name="short-description"></a>KORTE BESCHRIJVING
Beschrijft de Checkpoint-Workflow activiteit, waarmee een controle punt in een werk stroom wordt gebruikt.

## <a name="long-description"></a>LANGE BESCHRIJVING

De activiteit Checkpoint-Workflow maakt een controle punt, waarmee de status en gegevens in de werk stroom worden opgeslagen. Als de werk stroom wordt onderbroken of onderbroken, kan deze worden hervat vanaf het laatste controle punt en niet opnieuw moeten worden gestart.

De Checkpoint-Workflow-activiteit is alleen geldig in een werk stroom.

### <a name="syntax"></a>SYNTAXIS

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

De Checkpoint-Workflow-activiteit accepteert geen para meters, waaronder algemene para meters en algemene werk stroom parameters.

U kunt het Checkpoint-Activity controle punt overal in een werk stroom plaatsen na de CmdletBinding-of param-instructie. Bij het plaatsen van controle punten kunt u echter de prestaties van de gegevens verzamelen en deze naar de schijf schrijven op de computer waarop de werk stroom wordt uitgevoerd.

Zorg ervoor dat de tijd die nodig is om een sectie van de werk stroom opnieuw uit te voeren als deze wordt onderbroken, groter is dan de tijd die nodig is om de status van het controle punt en de gegevens naar de schijf te schrijven.

Overweeg het nemen van controle punten na kritieke stappen, zodat de werk stroom kan worden hervat in plaats van opnieuw te worden gestart. Neem bijvoorbeeld een controle punt na opdrachten die niet idempotent zijn.

### <a name="about-checkpoints"></a>OVER CONTROLE PUNTEN

Een controle punt is een moment opname van de huidige status van de werk stroom, met inbegrip van de huidige waarden van variabelen en een uitvoer die tot dat punt wordt gegenereerd, en slaat deze op schijf op.

Als een werk stroom wordt onderbroken, met opzet of per ongeluk, gebruikt Windows Power shell-werk stroom automatisch de gegevens in het nieuwste controle punt om de werk stroom te herstellen en weer te hervatten.

Wanneer u de werk stroom uitvoert als een taak, bijvoorbeeld met behulp van de algemene para meter AsJob workflow, worden de controle punten van werk stromen bewaard totdat u de taak verwijdert, bijvoorbeeld met behulp van de cmdlet Remove-Job.
Anders worden werk stroom controlepunten verwijderd wanneer de werk stroom is voltooid.

### <a name="other-checkpointing-techniques"></a>ANDERE TECHNIEKEN VOOR CONTROLE PUNTEN

Naast de Checkpoint-Workflow-activiteit, ondersteunt de Windows Power shell-werk stroom andere controlepunt technieken, waaronder de volgende:

- Algemene para meter voor de PSPersist-werk stroom
- Algemene para meter PSPersist-activiteit
- De variabele PSPersistPreference (in een werk stroom)

Zie "controle punten toevoegen aan een werk stroom" voor meer informatie over het toevoegen van een controle punt aan een werk stroom.

## <a name="examples"></a>VOORBEELDEN

De volgende werk stroom bevat een aanroep van de Checkpoint-Workflow-activiteit nadat u een langlopende functie en een script voor het delen van gegevens hebt voltooid.

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

## <a name="see-also"></a>ZIE OOK

[Een Windows PowerShell-werkstroom schrijven](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
