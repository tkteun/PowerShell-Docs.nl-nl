---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941171"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

Windows Power shell desired state Configuration (DSC) heeft ingebouwde resources die u kunt gebruiken voor het configureren van uw omgeving. In dit onderwerp vindt u een overzicht van het ontwikkelen van resources en koppelingen naar onderwerpen met specifieke informatie en voor beelden.

## <a name="dsc-resource-components"></a>DSC-resource onderdelen

Een DSC-resource is een Windows Power shell-module. De module bevat zowel het schema (de definitie van de Configureer bare eigenschappen) als de implementatie (de code die het werkelijke werk opgeeft dat is opgegeven door een configuratie) voor de resource. Een DSC-resource schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een script module. Vanaf de ondersteuning van Power shell-klassen in versie 5 kunnen het schema en de implementatie worden gedefinieerd in een-klasse. In de volgende onderwerpen vindt u meer informatie over het maken van DSC-resources.

* [Een aangepaste DSC-resource schrijven met MOF](authoringResourceMOF.md)
* [Een DSC-resource implementeren inC#](authoringResourceMofCS.md)
* [Een aangepaste DSC-resource schrijven met Power shell-klassen](authoringResourceClass.md)
* [Composite resources: Een DSC-configuratie gebruiken als resource @ no__t-0
* [Het hulp programma resource Designer gebruiken](authoringResourceMofDesigner.md)
