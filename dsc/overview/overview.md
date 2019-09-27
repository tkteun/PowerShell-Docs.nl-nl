---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Overzicht van desired state Configuration voor Windows Power shell
ms.openlocfilehash: 5c4853cb059ca0cf063a9450f97230732bc56b10
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324915"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Overzicht van desired state Configuration voor Windows Power shell

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

DSC is een beheer platform in Power shell waarmee u uw IT-en ontwikkelings infrastructuur met configuratie als code kunt beheren.

- Voor een overzicht van de zakelijke voor delen van het gebruik van DSC raadpleegt u [overzicht van desired state Configuration voor besluit vormers](decisionMaker.md).
- Voor een overzicht van de technische voor delen van het gebruik van DSC, Zie [desired state Configuration-overzicht voor technici](DscForEngineers.md).
- Zie [DSC Quick Start](../quickstarts/website-quickstart.md)om DSC snel te gaan gebruiken.

## <a name="key-concepts"></a>Belangrijkste concepten

DSC is een declaratief platform dat wordt gebruikt voor de configuratie, implementatie en het beheer van systemen. Het bestaat uit drie primaire onderdelen:

- [Configuraties](../configurations/configurations.md) zijn declaratieve Power shell-scripts waarmee instanties van resources worden gedefinieerd en geconfigureerd.
    Bij het uitvoeren van de configuratie zal DSC (en de bronnen die worden aangeroepen door de configuratie) het ' zo maken ' dat het systeem bestaat in de status die is opgenomen in de configuratie.
    DSC-configuraties zijn ook idempotent: de lokale Configuration Manager (LCM) blijft ervoor zorgen dat machines worden geconfigureerd in welke staat de configuratie declareert.
- [Resources](../resources/resources.md) zijn het deel van DSC. Ze bevatten de code die het doel van een configuratie in de opgegeven status plaatst en bewaart.
    Resources bevinden zich in Power shell-modules en kunnen worden geschreven om iets te model leren als een bestand of een Windows-proces, of als een IIS-server of een VM die wordt uitgevoerd in Azure.
- De [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is de engine waarmee DSC de interactie tussen bronnen en configuraties vereenvoudigt.
    De LCM pollt regel matig het systeem met behulp van de controle stroom die door resources wordt geïmplementeerd om ervoor te zorgen dat de status die is gedefinieerd door een configuratie wordt behouden.
    Als het systeem niet in staat is, wordt de code in de bronnen door de LCM aangeroepen volgens de configuratie.

## <a name="see-also"></a>Zie ook

- [DSC-configuraties](../configurations/configurations.md)
- [DSC-resources](../resources/resources.md)
- [De lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)
