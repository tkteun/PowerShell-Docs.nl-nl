---
title: Resource parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 460c43aa-f5c5-4a1a-a6f2-5e07db143de1
caps.latest.revision: 5
ms.openlocfilehash: 9752570e5c997ef4da56a08df14f39b77ba37a4a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359234"
---
# <a name="resource-parameters"></a>Resourceparameters

De volgende tabel bevat de aanbevolen namen en functies voor resource parameters. Voor deze para meters is het mogelijk dat de resources de assembly zijn die de cmdlet-klasse bevat of de hosttoepassing waarop de cmdlet wordt uitgevoerd.

|Parameter|Functionaliteit|
|---|---|
|**Toepassing**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een toepassing kan opgeven.|
|**Assembly**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een assembly kan opgeven.|
|**Geschreven**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een kenmerk kan opgeven.|
|**Klasse**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een Microsoft .NET Framework-klasse kan opgeven.|
|**Cluster**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een cluster kan opgeven.|
|**Culturele**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de cultuur kan opgeven waarin de cmdlet moet worden uitgevoerd.|
|**Domein**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de domein naam kan opgeven.|
|**Stationsletter**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de naam van een station kan opgeven.|
|**Gebeurtenis**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een gebeurtenis naam kan opgeven.|
|**Interface**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de naam van een netwerk interface kan opgeven.|
|**IPAdres**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een IP-adres kan opgeven.|
|**Job**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een taak kan opgeven.|
|**LiteralPath**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker het pad naar een resource kan opgeven wanneer joker tekens niet worden ondersteund. (Gebruik de para meter **Path** als joker tekens worden ondersteund.)|
|**Mac**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een MAC-adres (Media Access Controller) kan opgeven.|
|**ParentId**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de bovenliggende id kan opgeven.|
|**Pad**<br>Gegevens type: teken reeks, teken reeks []|Implementeer deze para meter zodat de gebruiker de paden naar een resource kan aangeven wanneer joker tekens worden ondersteund. (Gebruik de para meter **LiteralPath** als joker tekens niet worden ondersteund.) U wordt aangeraden deze para meter te ontwikkelen zodat deze de volledige `provider:path` syntaxis ondersteunt die wordt gebruikt door providers. We raden u ook aan deze te ontwikkelen zodat deze samen met zoveel mogelijk providers werkt.|
|**Poort**<br>Gegevens type: geheel getal, teken reeks|Implementeer deze para meter zodat de gebruiker een geheel getal voor netwerken of een teken reeks waarde zoals ' BizTalk ' kan opgeven voor andere typen poort.|
|**Stuur**<br>Gegevens type: geheel getal, teken reeks|Implementeer deze para meter zodat de gebruiker de printer kan opgeven die moet worden gebruikt voor de cmdlet.|
|**Grootte**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker een grootte kan opgeven.|
|**TID**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een trans actie-id (TID) kan opgeven voor de cmdlet.|
|**Type**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker het type resource kan opgeven waarvoor moet worden gewerkt.|
|**URL**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een Uniform Resource Locator (URL) kan opgeven.|
|**Gebruiker**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de naam of de naam van een andere gebruiker kan opgeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-para meters](./cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
