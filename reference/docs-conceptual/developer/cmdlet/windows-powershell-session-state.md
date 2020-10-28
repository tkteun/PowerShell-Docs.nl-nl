---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell-sessiestatus
description: Windows PowerShell-sessiestatus
ms.openlocfilehash: 51de92f1f392f708cf49c7ccb4a6808fd628076c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668130"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell-sessiestatus

Sessie status verwijst naar de huidige configuratie van een Windows Power shell-sessie of-module. Een Windows Power shell-sessie is de operationele omgeving die interactief wordt gebruikt door de opdracht regel gebruiker of via een programma door een hosttoepassing. De sessie status voor een sessie wordt de status van de globale sessie genoemd.

Vanuit een oogpunt van ontwikkel aars verwijst een Windows Power shell-sessie naar de tijd tussen het moment waarop een hosttoepassing een Windows Power shell-runs Pace opent en wanneer de runs Pace wordt gesloten. Op een andere manier is de sessie de levens duur van een exemplaar van de Windows Power shell-engine die wordt aangeroepen terwijl de runs Pace bestaat.

## <a name="module-session-state"></a>Sessie status van de module

De sessie status van de module wordt gemaakt wanneer de module of een van de geneste modules in de sessie wordt geïmporteerd. Wanneer een module een element, zoals een cmdlet, functie of script, exporteert, wordt een verwijzing naar dat element toegevoegd aan de algemene sessie status van de sessie. Wanneer het element echter wordt uitgevoerd, wordt het uitgevoerd binnen de sessie status van de module.

## <a name="session-state-data"></a>Session-State gegevens

Sessie status gegevens kunnen openbaar of privé zijn. Open bare gegevens zijn beschikbaar voor aanroepen buiten de sessie status terwijl privé gegevens alleen beschikbaar zijn voor aanroepen vanuit de sessie status. Een module kan bijvoorbeeld een persoonlijke functie hebben die alleen door de module kan worden aangeroepen of alleen intern door een openbaar element dat is geëxporteerd. Dit is vergelijkbaar met de persoonlijke en open bare leden van een .NET Framework type.

Sessie status gegevens worden opgeslagen door het huidige exemplaar van de uitvoerings engine binnen de context van de huidige Windows Power shell-sessie. De sessie status gegevens bestaan uit de volgende items:

- Padgegevens

- Informatie over station

- Informatie over Windows Power shell-provider

- Informatie over de geïmporteerde modules en verwijzingen naar de module-elementen (zoals cmdlets, functies en scripts) die worden geëxporteerd door de module. Deze informatie en deze verwijzingen gelden alleen voor de status van de globale sessie.

- Informatie over sessie status variabele

## <a name="accessing-session-state-data-within-cmdlets"></a>Toegang tot Session-State gegevens in cmdlets

-Cmdlets kunnen indirect toegang krijgen tot sessie status gegevens via de eigenschap [System. Management. Automation. PSCmdlet. sessionState *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) van de cmdlet-klasse of rechtstreeks via de klasse [System. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) . De klasse [System. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) biedt eigenschappen die kunnen worden gebruikt om verschillende soorten sessie status gegevens te onderzoeken.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. PSCmdlet. sessionState](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System. Management. Automation. sessionState? Displayproperty = FullName](/dotnet/api/System.Management.Automation.SessionState)

[Windows Power shell-cmdlets](./cmdlet-overview.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell shell SDK](../windows-powershell-reference.md)
