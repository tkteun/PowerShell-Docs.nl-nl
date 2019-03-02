---
title: Resourceparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251197"
---
# <a name="resource-parameters"></a>Resourceparameters

De volgende tabel bevat de aanbevolen namen en de functionaliteit voor resourceparameters. Voor deze parameters kunnen de resources worden de assembly waarin de cmdlet-klasse of de hosttoepassing die de cmdlet wordt uitgevoerd.

|Parameter|Functionaliteit|
|---|---|
|**Toepassing**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een toepassing opgeven.|
|**Assembly**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een assembly opgeven.|
|**Kenmerk**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een kenmerk opgeven.|
|**Klasse**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een Microsoft .NET Framework-klasse opgeven.|
|**Cluster**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een cluster opgeven.|
|**cultuur**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren zodat de gebruiker kan de cultuur waarin u de cmdlet uitvoeren opgeven.|
|**Domein**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de domeinnaam opgeven.|
|**Drive**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de naam van een station opgeven.|
|**Gebeurtenis**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de naam van een gebeurtenis opgeven.|
|**Interface**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren zodat de gebruiker kan een network interface-naam opgeven.|
|**IpAddress**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een IP-adres opgeven.|
|**Job**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een taak opgeven.|
|**LiteralPath**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker het pad naar een resource opgeven kan als jokertekens worden niet ondersteund. (Gebruik de **pad** parameter wanneer jokertekens worden ondersteund.)|
|**Mac**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een adres media access controller (MAC) opgeven.|
|**ParentId**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de bovenliggende id opgeven.|
|**Pad**<br>Gegevenstype: String, String[]|Implementeer deze parameter zodat de gebruiker de paden naar een resource aangeven kan wanneer jokertekens worden ondersteund. (Gebruik de **LiteralPath** parameter wanneer jokertekens worden niet ondersteund.) Het is raadzaam dat u deze parameter ontwikkelen, zodat deze ondersteuning biedt voor de volledige `provider:path` syntaxis die wordt gebruikt door providers. We raden u ook aan dat u ontwikkeling ervan zodat het werkt met zo veel providers mogelijk.|
|**Poort**<br>Gegevenstype: Integer, String|Implementeer deze parameter zodat de gebruiker kan een geheel getal voor het netwerk of een string-waarde, zoals 'biztalk' voor andere typen van poort opgeven.|
|**Printer**<br>Gegevenstype: Integer, String|Deze parameter implementeren zodat de gebruiker de printer voor de cmdlet te gebruiken kunt opgeven.|
|**Grootte**<br>Gegevenstype: Int32|Implementeer deze parameter zodat de gebruiker kan een grootte opgeven.|
|**TID**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een transactie-id (TID) voor de cmdlet opgeven.|
|**Type**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren zodat de gebruiker van het type resource waarop opgeven kan moet worden uitgevoerd.|
|**URL**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan een URL (Uniform Resource Locator) opgeven.|
|**User**<br>Gegevenstype: Tekenreeks|Implementeer deze parameter zodat de gebruiker kan de naam of de naam van een andere gebruiker opgeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-Parameters](./cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
