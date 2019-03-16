---
title: Voorbeelden van Cmdlet-Code | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056256"
---
# <a name="examples-of-cmdlet-code"></a>Voorbeelden van cmdlet-code

In deze sectie bevat voorbeelden van de cmdlet-code die u gebruiken kunt om te beginnen met het schrijven van uw eigen cmdlets.

> [!IMPORTANT]
> Als u wilt dat Stapsgewijze instructies voor het schrijven van cmdlets, raadpleegt u [zelfstudies voor het schrijven van Cmdlets](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>In deze sectie

[Over het schrijven van een eenvoudige Cmdlet](./how-to-write-a-simple-cmdlet.md) in dit voorbeeld ziet u de basisstructuur van de cmdlet-code.

[Hoe u de Cmdlet-Parameters declareren](./how-to-declare-cmdlet-parameters.md) in dit voorbeeld laat zien hoe de verschillende typen parameters declareren.

[Hoe parametersets declareren](./how-to-declare-parameter-sets.md) in dit voorbeeld laat zien hoe om te declareren van sets met parameters die de actie uitvoert voor een cmdlet kunnen wijzigen.

[Hoe u Parameter invoer valideren](./how-to-validate-parameter-input.md) deze voorbeelden laten zien hoe u voor het valideren van de parameter-invoer.

[Hoe u dynamische Parameters declareren](./how-to-declare-dynamic-parameters.md) in dit voorbeeld laat zien hoe een parameter die is toegevoegd tijdens runtime declareren.

[Hoe kunt u Scripts aanroepen vanuit een Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) in dit voorbeeld laat zien hoe u een script dat wordt doorgegeven aan een cmdlet aanroepen.

[Het onderdrukken van invoer verwerkingsmethoden](./how-to-override-input-processing-methods.md) deze voorbeelden ziet u de basisstructuur gebruikt voor het overschrijven van de methoden BeginProcessing ProcessRecord en EndProcessing.

[Hoe u ondersteuningsaanvragen shouldprocess wordt overgeslagen](./how-to-request-confirmations.md) dit voorbeeld laat zien hoe de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden moeten worden aangeroepen vanuit een cmdlet.

[Hoe u ondersteuning voor transacties](./how-to-support-transactions.md) dit voorbeeld laat zien hoe u om aan te geven dat de cmdlet biedt ondersteuning voor transacties en het implementeren van de actie die moet worden uitgevoerd wanneer de cmdlet wordt gebruikt binnen een transactie.

[Hoe u taken ondersteunen](./how-to-support-jobs.md) in dit voorbeeld laat zien hoe ter ondersteuning van taken bij het schrijven van cmdlets.

[Het aanroepen van een Cmdlet uit binnen een Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) dit voorbeeld wordt het aanroepen van een cmdlet uit binnen een andere cmdlet, zodat u kunt de functionaliteit van de cmdlet aangeroepen toevoegen aan de cmdlet die u ontwikkelt.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
