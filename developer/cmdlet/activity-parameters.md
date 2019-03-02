---
title: Activiteitsparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 489d8bcdabe904d6a3d2bc6cdb9d7e23d09cbef2
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251214"
---
# <a name="activity-parameters"></a>Activiteitsparameters

De volgende tabel bevat de aanbevolen namen en de functionaliteit voor de activiteitsparameters.

|Parameter|Functionaliteit|
|---|---|
|**Toevoegen**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de gebruikers inhoud aan het einde van een resource toevoegen kunnen als de parameter is opgegeven.|
|**CaseSensitive**<br>Gegevenstype: SwitchParameter|Deze parameter implementeren, zodat de gebruiker hoofdlettergevoeligheid vereisen kunt wanneer de parameter is opgegeven.|
|**Opdracht**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren, zodat de gebruiker een opdrachttekenreeks om uit te voeren kunt opgeven.|
|**CompatibleVersion**<br>Gegevenstype: System.Version object|Deze parameter implementeren, zodat de gebruiker de semantiek voor dat de cmdlet compatibel met voor compatibiliteit met eerdere versies zijn moet kunt opgeven.|
|**comprimeren**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de compressie van gegevens wordt gebruikt wanneer de parameter is opgegeven.|
|**comprimeren**<br>Gegevenstype: Trefwoord|Deze parameter implementeren zodat de gebruiker het algoritme moet worden gebruikt voor de compressie van gegevens kunt opgeven.|
|**Continue**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de gegevens worden verwerkt totdat de gebruiker de cmdlet wordt gesloten wanneer de parameter is opgegeven. Als de parameter niet opgegeven is, wordt de cmdlet verwerkt een vooraf gedefinieerde hoeveelheid gegevens en vervolgens de bewerking beëindigd.|
|**Maken**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter om aan te geven dat een resource wordt gemaakt als deze niet al bestaat als de parameter is opgegeven.|
|**Verwijderen**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat resources worden verwijderd wanneer de cmdlet kan de bewerking is voltooid wanneer de parameter is opgegeven.|
|**Clusterbesturingssysteem**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter om aan te geven dat er een uitstaande werkitems worden verwerkt voordat nieuwe gegevens in de cmdlet worden verwerkt wanneer de parameter is opgegeven. Als de parameter niet opgegeven is, worden de werkitems onmiddellijk verwerkt.|
|**Wissen**<br>Gegevenstype: Int32|Deze parameter implementeren zodat de gebruiker het aantal keren dat die een resource worden gewist opgeven kan voordat deze wordt verwijderd.|
|**ErrorLevel**<br>Gegevenstype: Int32|Implementeer deze parameter zodat de gebruiker kan het niveau van fouten naar het rapport opgeven.|
|**Uitsluiten**<br>Gegevenstype: String[]|Implementeer deze parameter zodat de gebruiker iets van een activiteit uitsluiten kunt. Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](input-filter-parameters.md).|
|**Filter**<br>Gegevenstype: Trefwoord|Deze parameter implementeren zodat de gebruiker kan een filter dat de resources waarop de actie van de cmdlet uit te voeren selecteert opgeven. Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).|
|**Ga als volgt**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de voortgang wordt bijgehouden wanneer de parameter is opgegeven.|
|**Force**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter om aan te geven dat de gebruiker een actie uitvoeren kan, zelfs als er beperkingen optreden als de parameter is opgegeven. De beveiliging is niet toegestaan. Deze parameter kunt bijvoorbeeld een gebruiker een alleen-lezenbestand overschrijven.|
|**Opnemen**<br>Gegevenstype: String[]|Implementeer deze parameter zodat de gebruiker iets in een activiteit opnemen kunt. Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](input-filter-parameters.md).|
|**Incrementele**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter om aan te geven dat de verwerking stapsgewijs wordt uitgevoerd wanneer de parameter is opgegeven. Met deze parameter kunt bijvoorbeeld het uitvoeren van incrementele back-ups die back-up van bestanden alleen sinds de laatste back-up van een gebruiker.|
|**InputObject**<br>Gegevenstype: Object|Deze parameter implementeren wanneer de cmdlet wordt de invoer uit andere cmdlets. Als u definieert een **InputObject** parameter altijd opgeven om de **ValueFromPipeline** sleutelwoord wanneer u declareert de **Parameter** kenmerk. Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).|
|**Invoegen**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet wordt een item ingevoegd als de parameter is opgegeven.|
|**Interactief**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet interactief met de gebruiker werkt wanneer de parameter is opgegeven.|
|**Interval**<br>Gegevenstype: Hash-tabel|Implementeer deze parameter zodat de gebruiker kan een hash-tabel met trefwoorden die de waarden bevat opgeven. Het volgende voorbeeld toont voorbeeldwaarden voor de **Interval** parameter: `-interval @{ResumeScan=15; Retry=3}`.|
|**Log**<br>Gegevenstype: SwitchParameter|Implementeer de controle voor deze parameter de acties van de cmdlet wanneer de parameter is opgegeven.|
|**NoClobber**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de bron niet worden overschreven wanneer de parameter is opgegeven. Deze parameter is algemeen van toepassing op de cmdlets die nieuwe objecten maken, zodat ze kunnen worden voorkomen van het overschrijven van bestaande objecten met dezelfde naam.|
|**Op de hoogte stellen**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de gebruiker ontvangt een melding dat de activiteit voltooid is wanneer de parameter is opgegeven.|
|**NotifyAddress**<br>Gegevenstype: E-mailadres|Deze parameter implementeren zodat de gebruiker kan het e-mailadres te gebruiken voor het verzenden van een melding opgeven wanneer de **waarschuwen** parameter is opgegeven.|
|**Overschrijven**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet worden alle bestaande gegevens overschreven wanneer de parameter is opgegeven.|
|**prompt**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren zodat de gebruiker kan een prompt voor de cmdlet opgeven.|
|**stille**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet feedback van gebruikers tijdens de acties onderdrukt als de parameter is opgegeven.|
|**Recurse**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de recursief cmdlet worden de acties uitgevoerd op resources als de parameter is opgegeven.|
|**Herstellen**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet probeert op te lossen iets uit een beschadigde status als de parameter is opgegeven.|
|**RepairString**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren zodat de gebruiker van een tekenreeks opgeven kan voor het gebruik van wanneer de **herstellen** parameter is opgegeven.|
|**Probeer het opnieuw**<br>Gegevenstype: Int32|Deze parameter implementeren, zodat de gebruiker kan het aantal keren dat de cmdlet een actie probeert opgeven.|
|**Selecteer**<br>Gegevenstype: Sleutelwoord matrix|Implementeer deze parameter zodat de gebruiker kan een matrix van de typen objecten opgeven.|
|**Stream**<br>Gegevenstype: SwitchParameter|Deze parameter implementeren, zodat de gebruiker meerdere uitvoer objecten via de pijplijn streamen kan wanneer de parameter is opgegeven.|
|**Strikte**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat alle fouten worden verwerkt als fouten wordt beëindigd wanneer de parameter is opgegeven.|
|**TempLocation**<br>Gegevenstype: Tekenreeks|Deze parameter implementeren, zodat de gebruiker de locatie van tijdelijke gegevens die worden gebruikt tijdens de bewerking van de cmdlet kunt opgeven.|
|**Timeout**<br>Gegevenstype: Int32|Implementeer deze parameter zodat de gebruiker kan de time-outinterval (in milliseconden) opgeven.|
|**Truncate**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet worden de acties worden afgekapt wanneer de parameter is opgegeven. Als de parameter niet opgegeven is, wordt door de cmdlet een andere actie uitvoert.|
|**Controleer of**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet test om te bepalen of een actie is opgetreden bij de parameter is opgegeven.|
|**Wacht**<br>Gegevenstype: SwitchParameter|Implementeer deze parameter zodat de cmdlet op invoer van de gebruiker wacht voordat u doorgaat als de parameter is opgegeven.
|**Wachttijd**<br>Gegevenstype: Int32|Deze parameter implementeren zodat de gebruiker kan de duur (in seconden) opgeven dat de cmdlet wordt gewacht op gebruiker invoer wanneer de **wacht** parameter is opgegeven.|

## <a name="see-also"></a>Zie ook

[Cmdlet-Parameters](./cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
