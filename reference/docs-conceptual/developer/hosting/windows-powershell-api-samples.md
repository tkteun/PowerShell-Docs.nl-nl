---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeelden van Windows PowerShell-API's
description: Voorbeelden van Windows PowerShell-API's
ms.openlocfilehash: b6336ae7a2abb98cbbaa69bf6c9455f893db2d94
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657541"
---
# <a name="windows-powershell-api-samples"></a>Voorbeelden van Windows PowerShell-API's

Deze sectie bevat voorbeeld code die laat zien hoe u runspaces maakt die de functionaliteit beperkt en hoe u opdrachten asynchroon uitvoert met behulp van een runs Pace-groep om de runspaces op te geven. U kunt micro soft Visual Studio gebruiken om een console toepassing te maken en vervolgens de code uit de onderwerpen in deze sectie naar uw host-toepassing te kopiëren.

## <a name="in-this-section"></a>In deze sectie

[PowerShell01](./windows-powershell01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object gebruikt om de functionaliteit van een runs Pace te beperken. De uitvoer van dit voor beeld laat zien hoe u de taal modus van de runs Pace kunt beperken, hoe u een cmdlet als privé markeert, hoe u cmdlets en providers toevoegt en verwijdert, hoe u een proxy opdracht toevoegt, en meer.

[PowerShell02](./windows-powershell02-sample.md) -voor beeld In dit voor beeld ziet u hoe u opdrachten asynchroon uitvoert met behulp van de runspaces van een runs Pace-groep. Het voor beeld genereert een lijst met opdrachten en voert vervolgens deze opdrachten uit terwijl de Windows Power shell-engine een runs Pace uit de groep opent wanneer dit nodig is.
