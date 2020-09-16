---
title: Resource parameters | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e618951d57ff1cf303b38f0278858144df31afaf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786523"
---
# <a name="resource-parameters"></a>Resourceparameters

De volgende tabel bevat de aanbevolen namen en functies voor resource parameters. Voor deze para meters is het mogelijk dat de resources de assembly zijn die de cmdlet-klasse bevat of de hosttoepassing waarop de cmdlet wordt uitgevoerd.

|Parameter|Functionaliteit|
|---|---|
|**App**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een toepassing kan opgeven.|
|**Assembly**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een assembly kan opgeven.|
|**Kenmerk**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een kenmerk kan opgeven.|
|**Klas**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een Microsoft .NET Framework-klasse kan opgeven.|
|**Cluster**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een cluster kan opgeven.|
|**Cultuur**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de cultuur kan opgeven waarin de cmdlet moet worden uitgevoerd.|
|**Domein**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de domein naam kan opgeven.|
|**Station**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam van een station kan opgeven.|
|**Gebeurtenis**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een gebeurtenis naam kan opgeven.|
|**Interface**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam van een netwerk interface kan opgeven.|
|**IPAdres**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een IP-adres kan opgeven.|
|**Taak**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een taak kan opgeven.|
|**LiteralPath**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker het pad naar een resource kan opgeven wanneer joker tekens niet worden ondersteund. (Gebruik de para meter **Path** als joker tekens worden ondersteund.)|
|**Mac**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een MAC-adres (Media Access Controller) kan opgeven.|
|**ParentId**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de bovenliggende id kan opgeven.|
|**Pad**<br>Gegevens type: teken reeks, teken reeks []|Implementeer deze para meter zodat de gebruiker de paden naar een resource kan aangeven wanneer joker tekens worden ondersteund. (Gebruik de para meter **LiteralPath** als joker tekens niet worden ondersteund.) U wordt aangeraden deze para meter te ontwikkelen zodat deze de volledige `provider:path` syntaxis ondersteunt die wordt gebruikt door providers. We raden u ook aan deze te ontwikkelen zodat deze samen met zoveel mogelijk providers werkt.|
|**Poort**<br>Gegevens type: geheel getal, teken reeks|Implementeer deze para meter zodat de gebruiker een geheel getal voor netwerken of een teken reeks waarde zoals ' BizTalk ' kan opgeven voor andere typen poort.|
|**Printer**<br>Gegevens type: geheel getal, teken reeks|Implementeer deze para meter zodat de gebruiker de printer kan opgeven die moet worden gebruikt voor de cmdlet.|
|**Grootte**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker een grootte kan opgeven.|
|**TID**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een trans actie-id (TID) kan opgeven voor de cmdlet.|
|**Type**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker het type resource kan opgeven waarvoor moet worden gewerkt.|
|**URL**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een Uniform Resource Locator (URL) kan opgeven.|
|**Gebruiker**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de naam of de naam van een andere gebruiker kan opgeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-parameters](./cmdlet-parameters.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
