---
title: Cmdlets en scripts aanroepen binnen een cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355424"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Cmdlets en scripts in een cmdlet aanroepen

Met een cmdlet kunnen andere cmdlets en scripts worden aangeroepen in de invoer verwerkings methode van de cmdlet. Hierdoor kunt u de functionaliteit van bestaande cmdlets en scripts toevoegen aan uw cmdlet zonder dat u de code opnieuw hoeft te schrijven.

## <a name="the-invoke-method"></a>De methode Invoke

Alle cmdlets kunnen een bestaande cmdlet aanroepen door het aanroepen van de methode [System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) vanuit een invoer verwerkings methode, zoals [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), die wordt overschreven door de cmdlet. U kunt echter alleen de cmdlets aanroepen die rechtstreeks zijn afgeleid van de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . U kunt geen cmdlet aanroepen die is afgeleid van de klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

De methode [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) heeft de volgende varianten.

[System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) als u deze variant aanroept, wordt het cmdlet-object aangeroepen en wordt een verzameling van type-objecten geretourneerd.

[System. Management. Automation. cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) als u deze variant aanroept, wordt het cmdlet-object aangeroepen en wordt een sterk getypeerde emumerator geretourneerd. Met deze variant kan de gebruiker de objecten in de verzameling gebruiken om aangepaste bewerkingen uit te voeren.

## <a name="examples"></a>Voorbeelden

|Voorbeeld|Beschrijving|
|-------------|-----------------|
|[Cmdlets aanroepen binnen een cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|In dit voor beeld ziet u hoe u een cmdlet aanroept vanuit een andere cmdlet.|
|[Scripts aanroepen binnen een cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|In dit voor beeld ziet u hoe u een script aanroept dat bij de cmdlet wordt geleverd vanuit een andere cmdlet.|

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
