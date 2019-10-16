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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359234"
---
# <a name="resource-parameters"></a>Resourceparameters

De volgende tabel bevat de aanbevolen namen en functies voor resource parameters. Voor deze para meters is het mogelijk dat de resources de assembly zijn die de cmdlet-klasse bevat of de hosttoepassing waarop de cmdlet wordt uitgevoerd.

|Parameter|Functionaliteit|
|---|---|
|**Modules**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een toepassing kan opgeven.|
|**Assemblage**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een assembly kan opgeven.|
|**Geschreven**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een kenmerk kan opgeven.|
|**Klasse**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een Microsoft .NET Framework-klasse kan opgeven.|
|**Cluster**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een cluster kan opgeven.|
|**Culturele**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de cultuur kan opgeven waarin de cmdlet moet worden uitgevoerd.|
|**Domeinen**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de domein naam kan opgeven.|
|**Stationsletter**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam van een station kan opgeven.|
|**Gebeurtenislog**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een gebeurtenis naam kan opgeven.|
|**Interface**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam van een netwerk interface kan opgeven.|
|**IPAdres**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een IP-adres kan opgeven.|
|**Taak**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een taak kan opgeven.|
|**LiteralPath**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker het pad naar een resource kan opgeven wanneer joker tekens niet worden ondersteund. (Gebruik de para meter **Path** als joker tekens worden ondersteund.)|
|**Mac**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een MAC-adres (Media Access Controller) kan opgeven.|
|**ParentId**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de bovenliggende id kan opgeven.|
|**Programmapad**<br>Gegevens type: teken reeks, teken reeks []|Implementeer deze para meter zodat de gebruiker de paden naar een resource kan aangeven wanneer joker tekens worden ondersteund. (Gebruik de para meter **LiteralPath** als joker tekens niet worden ondersteund.) U wordt aangeraden deze para meter te ontwikkelen zodat deze de volledige `provider:path`-syntaxis ondersteunt die wordt gebruikt door providers. We raden u ook aan deze te ontwikkelen zodat deze samen met zoveel mogelijk providers werkt.|
|**Importeer**<br>Gegevens type: geheel getal, teken reeks|Implementeer deze para meter zodat de gebruiker een geheel getal voor netwerken of een teken reeks waarde zoals ' BizTalk ' kan opgeven voor andere typen poort.|
|**Stuur**<br>Gegevens type: geheel getal, teken reeks|Implementeer deze para meter zodat de gebruiker de printer kan opgeven die moet worden gebruikt voor de cmdlet.|
|**Size**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker een grootte kan opgeven.|
|**TID**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een trans actie-id (TID) kan opgeven voor de cmdlet.|
|**Voert**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker het type resource kan opgeven waarvoor moet worden gewerkt.|
|**URL**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een Uniform Resource Locator (URL) kan opgeven.|
|**Gebruiker**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam of de naam van een andere gebruiker kan opgeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-para meters](./cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
