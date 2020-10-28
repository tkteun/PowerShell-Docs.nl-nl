---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Windows PowerShell02
description: Voorbeeld Windows PowerShell02
ms.openlocfilehash: 61dedd72d93d4000edf9a12f12bbb49fbaeb9f3c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657349"
---
# <a name="windows-powershell02-sample"></a>Voorbeeld Windows PowerShell02

Dit voor beeld laat zien hoe u opdrachten asynchroon kunt uitvoeren met behulp van de runspaces van een runs Pace-groep. Het voor beeld genereert een lijst met opdrachten en voert vervolgens deze opdrachten uit terwijl de Windows Power shell-engine een runs Pace uit de groep opent wanneer dit nodig is.

## <a name="requirements"></a>Vereisten

- Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Demonstreert

In dit voor beeld ziet u het volgende:

- Het maken van een RunspacePool-object met het minimum en maximum aantal runspaces dat tegelijkertijd mag worden geopend.
- Een lijst met opdrachten maken.
- De opdrachten asynchroon uitvoeren.
- De methode [System. Management. Automation. Runspaces. Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) aanroepen om te zien hoeveel Runspaces gratis zijn.
- Vastleggen van de uitvoer van de opdracht met de methode [System. Management. Automation. Power shell. Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de runspaces van een runs Pace-groep opent en hoe u asynchrone opdrachten kunt uitvoeren in deze runspaces.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs" range="11-96":::

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-hosttoepassing schrijven](./writing-a-windows-powershell-host-application.md)
