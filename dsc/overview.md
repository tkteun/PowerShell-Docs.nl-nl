---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Windows PowerShell Desired State Configuration-overzicht
ms.openlocfilehash: c9069d7c9ce9c614330e36a42233b00363660a4b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187473"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell Desired State Configuration-overzicht

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC is een beheerplatform in PowerShell waarmee u voor het beheren van uw IT-afdeling en ontwikkeling infrastructuur met configuratie als de code.

- Zie voor een overzicht van de zakelijke voordelen van het gebruik van DSC [Desired Configuration overzicht voor besluitvormers](decisionMaker.md).
- Zie voor een overzicht van de technische voordelen van het gebruik van DSC [Desired Configuration overzicht voor Engineers](DscForEngineers.md).
- Zie het gebruik van DSC snel starten [DSC snel starten](quickStart.md).

## <a name="key-concepts"></a>Belangrijkste concepten

DSC is een declaratieve platform gebruikt voor de configuratie, implementatie en beheer van systemen. Deze bestaat uit drie primaire onderdelen:

- [Configuraties](configurations.md) zijn declaratieve PowerShell-scripts die definiëren en configureren van exemplaren van resources.
    Bij het uitvoeren van de configuratie, DSC (en de resources die wordt aangeroepen door de configuratie) wordt gewoon 'zodat het geval', ervoor zorgen dat het systeem in de status van de lay bestaat-out van de configuratie.
    DSC-configuraties zijn ook idempotent: de lokale Configuration Manager (LCM) blijven om ervoor te zorgen dat machines zijn geconfigureerd in de gewenste status van de configuratie wordt gedeclareerd.
- [Resources](resources.md) de 'kunt u dus' deel uitmaken van DSC. Ze bevatten de code die geplaatst en het doel van een configuratie in de opgegeven status houden.
    Bronnen bevinden zich in de PowerShell-modules en kunnen worden geschreven als model voor iets als algemeen als een bestand of een Windows-proces is, of zo specifiek een IIS-server of een virtuele machine in Azure wordt uitgevoerd.
- De [lokale Configuration Manager (LCM)](metaConfig.md) is de engine waarmee DSC de interactie tussen resources en configuraties vereenvoudigt.
    De LCM controleert regelmatig of het systeem met de Controlestroom geïmplementeerd door resources om ervoor te zorgen dat de status is gedefinieerd door een configuratie behouden blijft.
    Als het systeem onvoldoende status heeft, maakt de LCM aanroepen naar de code in resources zodat ' dit ' volgens de configuratie.

## <a name="see-also"></a>Zie ook

- [DSC-configuraties](configurations.md)
- [DSC-Resources](resources.md)
- [De lokale Configuration Manager configureren](metaConfig.md)