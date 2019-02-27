---
title: De status van een Windows PowerShell-sessie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: 5d4effb508c9f2544832dad557671520cb0a7ac7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851700"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell-sessiestatus

Sessiestatus verwijst naar de huidige configuratie van een Windows PowerShell-sessie of de module. Een Windows PowerShell-sessie is de operationele omgeving die interactief wordt gebruikt door de gebruiker van de opdrachtregel of via een programma door een hosttoepassing. De sessiestatus voor een sessie wordt aangeduid als de globale sessiestatus.

Vanuit het oogpunt van ontwikkelaars verwijst een Windows PowerShell-sessie naar de tijd tussen wanneer een Windows PowerShell-runspace in een host-toepassing wordt geopend en wanneer deze de runspace wordt gesloten. De sessie is een andere manier bekeken, is de levensduur van een exemplaar van de Windows PowerShell-engine die wordt aangeroepen terwijl de runspace bestaat.

## <a name="module-session-state"></a>Module-sessiestatus

Status van de module-sessies worden gemaakt wanneer de module of een van de geneste modules in de sessie is geïmporteerd. Wanneer een module een element, zoals een cmdlet, een functie of een script exporteert, wordt een verwijzing naar dat element wordt toegevoegd aan de globale sessiestatus van de sessie. Echter, wanneer het element wordt uitgevoerd, deze uitgevoerd in de status van de sessie van de module.

## <a name="session-state-data"></a>Sessiestatusgegevens

Gegevens over de sessiestatus kan openbaar of privé zijn. Openbare gegevens is beschikbaar voor het aanroepen van buiten de sessiestatus terwijl persoonlijke gegevens alleen beschikbaar voor gesprekken vanuit de sessiestatus is. Een module kan bijvoorbeeld een privé-functie die alleen door de module of alleen intern kan worden aangeroepen door een openbare-element dat is geëxporteerd. Dit is vergelijkbaar met de persoonlijke en openbare leden van een .NET Framework-type.

Sessiestatus gegevens worden opgeslagen door het huidige exemplaar van de engine voor het uitvoeren in de context van de huidige Windows PowerShell-sessie. Sessiestatusgegevens bestaat uit de volgende items:

- Informatie over het pad

- Informatie over stations

- Informatie over Windows PowerShell-provider

- Informatie over de geïmporteerde modules en verwijzingen naar de module-elementen (zoals cmdlets, functies en scripts) die zijn geëxporteerd door de module. Deze informatie en deze verwijzingen zijn alleen de algemene sessiestatus.

- Informatie over de variabele van sessie-status

## <a name="accessing-session-state-data-within-cmdlets"></a>Toegang tot sessiestatusgegevens binnen Cmdlets

Cmdlets ofwel toegang kunt krijgen tot sessiestatusgegevens indirect via de [System.Management.Automation.Pscmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) eigenschap van de cmdlet-klasse of rechtstreeks via de [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasse. De [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) klasse-eigenschappen die kunnen worden gebruikt voor het onderzoeken van verschillende typen sessiestatusgegevens biedt.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Pscmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
