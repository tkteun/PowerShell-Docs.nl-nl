---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Windows PowerShell Desired State Configuration-overzicht
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079964"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell Desired State Configuration-overzicht

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC is een beheerplatform in PowerShell waarmee u voor het beheren van uw IT-afdeling en infrastructuur voor ontwikkeling met configuratie als code.

- Zie voor een overzicht van de zakelijke voordelen van het gebruik van DSC, [overzicht van Desired State Configuration voor besluitvormers](decisionMaker.md).
- Zie voor een overzicht van de technische voordelen van het gebruik van DSC [overzicht van Desired State Configuration voor technici](DscForEngineers.md).
- Als u wilt gaan met behulp van DSC snel, Zie [snel starten met DSC](../quickstarts/website-quickstart.md).

## <a name="key-concepts"></a>Belangrijkste concepten

DSC is een declaratieve platform dat wordt gebruikt voor configuratie, implementatie en beheer van systemen. Deze bestaat uit drie primaire onderdelen:

- [Configuraties](../configurations/configurations.md) declaratieve PowerShell-scripts die definiëren en configureren van exemplaren van resources.
    Bij het uitvoeren van de configuratie, DSC (en de resources die wordt aangeroepen met de configuratie) wordt gewoon 'Maak het dus', ervoor zorgen dat het systeem in de status van de lay bestaat-out van de configuratie.
    DSC-configuraties zijn ook idempotent: de lokale Configuration Manager (LCM) blijven om ervoor te zorgen dat machines zijn geconfigureerd in de configuratie van de status wordt gedeclareerd.
- [Resources](../resources/resources.md) zijn het onderdeel 'Maak het dus' van DSC. Ze bevatten de code die plaats en sla het doel van een configuratie in de opgegeven status.
    Resources zich bevinden in de PowerShell-modules en kunnen worden geschreven naar iets als algemene als een bestand of een Windows-proces of een IIS-server of een virtuele machine die wordt uitgevoerd in Azure zo specifiek model.
- De [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is de engine waarmee DSC vereenvoudigt het uitvoeren van de interactie tussen resources en configuraties.
    De LCM controleert regelmatig of het systeem met behulp van de Controlestroom door resources worden geïmplementeerd om ervoor te zorgen dat de status die is gedefinieerd door een configuratie wordt bijgehouden.
    Als het systeem onvoldoende staat heeft, wordt de LCM in aanroepen naar de code in resources zodat "," op basis van de configuratie.

## <a name="see-also"></a>Zie ook

- [DSC-configuraties](../configurations/configurations.md)
- [DSC-Resources](../resources/resources.md)
- [De Local Configuration Manager configureren](../managing-nodes/metaConfig.md)
