---
title: Activiteit parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355669"
---
# <a name="activity-parameters"></a>Activiteitsparameters

De volgende tabel geeft een lijst van de aanbevolen namen en functionaliteiten voor activiteit parameters.

|Parameter|Functionaliteit|
|---|---|
|**Toevoegen**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de gebruiker inhoud kan toevoegen aan het einde van een resource als de para meter is opgegeven.|
|**CaseSensitive**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de gebruiker hoofdletter gevoeligheid kan vereisen wanneer de para meter is opgegeven.|
|**Cmd**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een opdracht reeks kan opgeven die moet worden uitgevoerd.|
|**CompatibleVersion**<br>Gegevens type: System. Version-object|Implementeer deze para meter zodat de gebruiker de semantiek kan opgeven waarmee de cmdlet compatibel moet zijn voor compatibiliteit met eerdere versies.|
|**Comprimeren**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat gegevens compressie wordt gebruikt wanneer de para meter is opgegeven.|
|**Comprimeren**<br>Gegevens type: tref woord|Implementeer deze para meter zodat de gebruiker het algoritme kan opgeven dat moet worden gebruikt voor gegevens compressie.|
|**Elkaar**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de gegevens worden verwerkt totdat de gebruiker de cmdlet beëindigt wanneer de para meter is opgegeven. Als de para meter niet is opgegeven, wordt door de cmdlet een vooraf gedefinieerde hoeveelheid gegevens verwerkt, waarna de bewerking wordt beëindigd.|
|**Creëren**<br>Gegevens type: SwitchParameter|Implementeer deze para meter om aan te geven dat een resource wordt gemaakt als er nog geen bestaat wanneer de para meter is opgegeven.|
|**Verwijderd**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat resources worden verwijderd wanneer de cmdlet de bewerking heeft voltooid wanneer de para meter is opgegeven.|
|**Loopt**<br>Gegevens type: SwitchParameter|Implementeer deze para meter om aan te geven dat uitstaande werk items worden verwerkt voordat de cmdlet nieuwe gegevens verwerkt wanneer de para meter is opgegeven. Als de para meter niet is opgegeven, worden de werk items onmiddellijk verwerkt.|
|**Uitgummen**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker het aantal keren kan opgeven dat een resource wordt gewist voordat deze wordt verwijderd.|
|**Gelijk**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker het fout niveau kan opgeven dat moet worden gerapporteerd.|
|**Weekend**<br>Gegevens type: teken reeks []|Implementeer deze para meter zodat de gebruiker iets kan uitsluiten van een activiteit. Voor meer informatie over het gebruik van invoer filters, Zie [para meters voor invoer filter](input-filter-parameters.md).|
|**Filterwebonderdelen**<br>Gegevens type: tref woord|Implementeer deze para meter zodat de gebruiker een filter kan opgeven waarmee de resources worden geselecteerd waarop de cmdlet-actie moet worden uitgevoerd. Voor meer informatie over het gebruik van invoer filters, Zie [para meters voor invoer filter](./input-filter-parameters.md).|
|**Volg**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de voortgang wordt bijgehouden wanneer de para meter is opgegeven.|
|**Verkopers**<br>Gegevens type: SwitchParameter|Implementeer deze para meter om aan te geven dat de gebruiker een actie kan uitvoeren, zelfs als er beperkingen zijn aangetroffen wanneer de para meter is opgegeven. De para meter staat niet toe dat beveiliging wordt aangetast. Met deze para meter kan een gebruiker bijvoorbeeld een alleen-lezen bestand overschrijven.|
|**Behoort**<br>Gegevens type: teken reeks []|Implementeer deze para meter zodat de gebruiker iets kan bevatten in een activiteit. Voor meer informatie over het gebruik van invoer filters, Zie [para meters voor invoer filter](input-filter-parameters.md).|
|**Incrementele**<br>Gegevens type: SwitchParameter|Implementeer deze para meter om aan te geven dat de verwerking incrementeel wordt uitgevoerd wanneer de para meter is opgegeven. Met deze para meter kan een gebruiker bijvoorbeeld incrementele back-ups uitvoeren die alleen back-ups maken van bestanden sinds de laatste back-up.|
|**Input object**<br>Gegevens type: object|Implementeer deze para meter wanneer de cmdlet invoer van andere cmdlets gebruikt. Wanneer u een **input object** para meter definieert, moet u altijd het sleutel woord **ValueFromPipeline** opgeven wanneer u het **parameter** kenmerk declareert. Zie [para meters voor invoer filter](./input-filter-parameters.md)voor meer informatie over het gebruik van invoer filters.|
|**Invoegen**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet een item invoegt wanneer de para meter is opgegeven.|
|**SBSI**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet interactief werkt met de gebruiker wanneer de para meter is opgegeven.|
|**Bereik**<br>Gegevens type: hashtabel|Implementeer deze para meter zodat de gebruiker een hash-tabel met tref woorden kan opgeven die de waarden bevat. In het volgende voor beeld ziet u voorbeeld waarden voor de para meter **interval** : `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Gegevens type: SwitchParameter|Implementeer deze para meter om de acties van de cmdlet te controleren wanneer de para meter is opgegeven.|
|**NoClobber**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de resource niet wordt overschreven wanneer de para meter is opgegeven. Deze para meter is over het algemeen van toepassing op cmdlets waarmee nieuwe objecten worden gemaakt, zodat kan worden voor komen dat bestaande objecten met dezelfde naam worden overschreven.|
|**Meldingen**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de gebruiker wordt gewaarschuwd dat de activiteit is voltooid wanneer de para meter wordt opgegeven.|
|**NotifyAddress**<br>Gegevens type: e-mail adres|Implementeer deze para meter zodat de gebruiker het e-mail adres kan opgeven dat moet worden gebruikt om een melding te verzenden wanneer de para meter **Notify** is opgegeven.|
|**Schrijft**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet eventuele bestaande gegevens overschrijft wanneer de para meter is opgegeven.|
|**Verschijnt**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een prompt kan opgeven voor de cmdlet.|
|**Stil**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet gebruikers feedback onderdrukt tijdens de acties wanneer de para meter is opgegeven.|
|**Recurse**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet de acties recursief uitvoert op resources wanneer de para meter is opgegeven.|
|**Steller**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet probeert iets te corrigeren van een verbroken status wanneer de para meter is opgegeven.|
|**RepairString**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker een teken reeks kan opgeven die moet worden gebruikt wanneer de **herstel** parameter wordt opgegeven.|
|**Voeren**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker kan opgeven hoe vaak een actie moet worden uitgevoerd met de cmdlet.|
|**Uitgeschakeld**<br>Gegevens type: trefwoord matrix|Implementeer deze para meter zodat de gebruiker een matrix van de typen items kan opgeven.|
|**Bitsnelheid**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de gebruiker meerdere uitvoer objecten kan streamen via de pijp lijn wanneer de para meter is opgegeven.|
|**Beperking**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodanig dat alle fouten worden verwerkt als afsluit fouten wanneer de para meter is opgegeven.|
|**TempLocation**<br>Gegevens type: teken reeks|Implementeer deze para meter zodat de gebruiker de locatie van tijdelijke gegevens kan opgeven die wordt gebruikt tijdens de werking van de cmdlet.|
|**Out**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker het time-outinterval (in milliseconden) kan opgeven.|
|**Afkappen**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet de acties afkapt wanneer de para meter wordt opgegeven. Als de para meter niet is opgegeven, voert de cmdlet een andere actie uit.|
|**Punten**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet test om te bepalen of er een actie is uitgevoerd wanneer de para meter is opgegeven.|
|**Bewerking**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de cmdlet wacht op invoer van de gebruiker voordat u doorgaat wanneer de para meter is opgegeven.
|**WaitTime**<br>Gegevens type: Int32|Implementeer deze para meter zodat de gebruiker de duur (in seconden) kan opgeven die door de cmdlet wordt gewacht op de invoer van de gebruiker wanneer de **wait** -para meter is opgegeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-para meters](./cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
