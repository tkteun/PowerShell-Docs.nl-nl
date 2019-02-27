---
title: Aanroepen van de Cmdlets en -Scripts in een Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846240"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Cmdlets en scripts in een cmdlet aanroepen

Een cmdlet kunt aanroepen andere cmdlets en -scripts uit binnen de invoer-methode van de cmdlet verwerkt. Hiermee kunt u de functionaliteit van bestaande cmdlets en -scripts toevoegen aan uw cmdlet zonder de code te herschrijven.

## <a name="the-invoke-method"></a>De methode aanroepen

Alle cmdlets kan aanroepen van een bestaande cmdlet door het aanroepen van de [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) methode uit binnen een invoer verwerken methode, zoals [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), dat wil zeggen overschreven door de cmdlet. Echter, kunt u alleen die cmdlets die zijn afgeleid rechtstreeks van aanroepen de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse. U kunt geen aanroepen een cmdlet die is afgeleid van de [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klasse.

De [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) methode heeft de volgende varianten.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) deze variant roept de cmdlet-object en retourneert een verzameling van objecten van het type "T".

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) deze variant roept de cmdlet-object en geeft als resultaat een sterk getypeerde emumerator. Deze variant kan de gebruiker de objecten te gebruiken in de verzameling aangepaste bewerkingen uit te voeren.

## <a name="examples"></a>Voorbeelden

|Voorbeeld|Description|
|-------------|-----------------|
|[Cmdlets binnen een Cmdlet aanroepen](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|In dit voorbeeld laat zien hoe een cmdlet uit binnen een andere cmdlet aanroepen.|
|[Aanroepen van Scripts in een Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|In dit voorbeeld laat zien hoe een script dat wordt doorgegeven aan de cmdlet uit binnen een andere cmdlet aanroepen.|

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
