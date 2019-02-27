---
title: De datum en tijdparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71da921b-7c32-4155-b2f8-b19f30ec774d
caps.latest.revision: 7
ms.openlocfilehash: 49f6c667b0fd9678586559af39a33f982de0a68c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846709"
---
# <a name="date-and-time-parameters"></a>Datum- en tijdparameters

De volgende tabel bevat de namen van de aanbevolen en de functionaliteit voor parameters die werken met gegevens van de datum en tijd. Datum en tijd-parameters worden meestal gebruikt om vast te leggen wanneer iets wordt gemaakt of geopend.

Gebruikte gegevens typt u: SwitchParameter

Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op de resources die zijn gebruikt op basis van de datum en tijd die is opgegeven door de `Before` en `After` parameters.

Als deze parameter is opgegeven, de `Created` en `Modified` parameters moeten niet worden opgegeven.

Na het gegevenstype: DateTime

Implementeer deze parameter om op te geven van de datum en tijd waarna de cmdlet is gebruikt. Voor de `After` parameter om te werken, de cmdlet moet ook beschikken over een `Accessed`, `Created`, of `Modified` parameter. En deze parameter moet worden ingesteld op `true` wanneer de cmdlet wordt aangeroepen.

Voordat u het gegevenstype: DateTime

Implementeer deze parameter om op te geven van de datum en tijd waarbinnen de cmdlet is gebruikt. Voor de `Before` parameter om te werken, de cmdlet moet ook beschikken over een `Accessed`, `Created`, of `Modified` parameter. En deze parameter moet worden ingesteld op `true` wanneer de cmdlet wordt aangeroepen.

Gegevens van het type gemaakt: SwitchParameter

Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op de resources die zijn gemaakt op basis van de datum en tijd die is opgegeven door de `Before` en `After` parameters.

Als deze parameter is opgegeven, de `Accessed` en `Modified` parameters moeten niet worden opgegeven.

Exacte gegevenstype: SwitchParameter

Implementeer deze parameter zodat wanneer deze de termijn van de resource is opgegeven moet precies overeenkomen met de naam van de resource. Als de parameter niet is opgegeven hoeft de termijn van de resource en de naam niet precies.

Gewijzigde gegevens typt u: DateTime

Deze parameter implementeren, zodat wanneer deze is opgegeven de cmdlet wordt uitgevoerd op resources die zijn gewijzigd op basis van de datum en tijd die is opgegeven door de `Before` en `After` parameters.

Als deze parameter is opgegeven, de `Accessed` en `Created` parameters moeten niet worden opgegeven.

## <a name="see-also"></a>Zie ook

[Cmdlet-Parameters](./cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
