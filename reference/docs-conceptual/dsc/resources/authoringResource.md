---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen
description: Dit artikel bevat een overzicht van het ontwikkelen van resources en koppelingen naar artikelen met specifieke informatie en voor beelden.
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656408"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

Windows Power shell desired state Configuration (DSC) heeft ingebouwde resources die u kunt gebruiken voor het configureren van uw omgeving. Dit artikel bevat een overzicht van het ontwikkelen van resources en koppelingen naar artikelen met specifieke informatie en voor beelden.

## <a name="dsc-resource-components"></a>DSC-resource onderdelen

Een DSC-resource is een Windows Power shell-module. De module bevat zowel het schema (de definitie van de Configureer bare eigenschappen) als de implementatie (de code die het werkelijke werk opgeeft dat is opgegeven door een configuratie) voor de resource. Een DSC-resource schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een script module. Vanaf de ondersteuning van Power shell-klassen in versie 5 kunnen het schema en de implementatie worden gedefinieerd in een-klasse. In de volgende artikelen vindt u meer informatie over het maken van DSC-resources.

- [Een aangepaste DSC-resource schrijven met MOF](authoringResourceMOF.md)
- [Een DSC-resource implementeren in C #](authoringResourceMofCS.md)
- [Een aangepaste DSC-resource schrijven met Power shell-klassen](authoringResourceClass.md)
- [Samengestelde resources: het gebruik van een DSC-configuratie als een resource](authoringResourceComposite.md)
- [Het hulp programma resource Designer gebruiken](authoringResourceMofDesigner.md)
