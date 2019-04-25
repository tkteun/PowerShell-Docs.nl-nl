---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Maken van aangepaste Windows PowerShell Desired State Configuration Resources
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076868"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Maken van aangepaste Windows PowerShell Desired State Configuration Resources

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) heeft ingebouwde resources die u gebruiken kunt om uw omgeving te configureren. Dit onderwerp bevat een overzicht van het ontwikkelen van resources en koppelingen naar onderwerpen met specifieke informatie over en voorbeelden.

## <a name="dsc-resource-components"></a>Onderdelen van de DSC-resource

Een DSC-resource is een Windows PowerShell-module. De module bevat zowel het schema (de definitie van de configureerbare eigenschappen) en de implementatie (de code die het echte werk dat is opgegeven door een configuratie) voor de resource. Een DSC-resource-schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een scriptmodule. U begint met de ondersteuning van PowerShell-klassen in versie 5, kunnen het schema en de implementatie zowel worden gedefinieerd in een klasse. De volgende onderwerpen wordt beschreven in meer detail over het maken van DSC-resources.

* [Een aangepaste DSC-resource met MOF schrijven](authoringResourceMOF.md)
* [Een DSC-resource in implementerenC#](authoringResourceMofCS.md)
* [Schrijven van een aangepaste DSC-resource met de PowerShell-klassen](authoringResourceClass.md)
* [Samengestelde resources: Met behulp van een DSC-configuratie als een resource](authoringResourceComposite.md)
* [Met behulp van de ontwerpfunctie voor Resource-hulpprogramma](../authoringResourceMofDesigner.md)
