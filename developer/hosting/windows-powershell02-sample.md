---
title: Voorbeeld van de Windows-PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850356"
---
# <a name="windows-powershell02-sample"></a>Voorbeeld Windows PowerShell02

In dit voorbeeld laat zien hoe opdrachten asynchroon uitvoeren met behulp van de runspaces van een groep runspace. Het voorbeeld genereert een lijst met opdrachten en vervolgens deze opdrachten worden uitgevoerd terwijl de Windows PowerShell-engine wordt een runspace geopend uit de pool wanneer dat nodig is.

## <a name="requirements"></a>Vereisten

- In dit voorbeeld is Windows PowerShell 2.0 vereist.

## <a name="demonstrates"></a>Hier ziet u

In dit voorbeeld ziet u het volgende:

- Het maken van een object RunspacePool met een minimum en maximum aantal runspaces kunnen worden geopend op hetzelfde moment.

- Het maken van een lijst met opdrachten.

- De opdrachten asynchroon uitgevoerd.

- Aanroepen van de [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) methode om te zien hoeveel runspaces zijn gratis.

- Vastleggen van de uitvoer van de opdracht met de [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) methode.

## <a name="example"></a>Voorbeeld

Dit voorbeeld laat zien hoe u opent de runspaces van een groep runspace en asynchroon uitvoeren van opdrachten in deze runspaces genoemd.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-hosttoepassing schrijven](./writing-a-windows-powershell-host-application.md)