---
title: Voor beeld van Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72357531"
---
# <a name="windows-powershell02-sample"></a>Voorbeeld Windows PowerShell02

In dit voor beeld ziet u hoe u opdrachten asynchroon uitvoert met behulp van de runspaces van een runs Pace-groep. Het voor beeld genereert een lijst met opdrachten en voert vervolgens deze opdrachten uit terwijl de Windows Power shell-engine een runs Pace uit de groep opent wanneer dit nodig is.

## <a name="requirements"></a>Vereisten

- Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Laat zien

In dit voor beeld ziet u het volgende:

- Het maken van een RunspacePool-object met het minimum en maximum aantal runspaces dat tegelijkertijd mag worden geopend.

- Een lijst met opdrachten maken.

- De opdrachten asynchroon uitvoeren.

- De methode [System. Management. Automation. Runspaces. Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) aanroepen om te zien hoeveel Runspaces gratis zijn.

- Vastleggen van de uitvoer van de opdracht met de methode [System. Management. Automation. Power shell. Endinvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u de runspaces van een runs Pace-groep opent en hoe u asynchrone opdrachten kunt uitvoeren in deze runspaces.

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-hosttoepassing schrijven](./writing-a-windows-powershell-host-application.md)
