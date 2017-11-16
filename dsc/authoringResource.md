---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Aangepaste Windows PowerShell Desired State Configuration Resources bouwen
ms.openlocfilehash: 75b494db4ee6e381491decb11d35b60105217a0f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a>Aangepaste Windows PowerShell Desired State Configuration Resources bouwen

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell Desired State Configuration (DSC) met de ingebouwde resources die u gebruiken kunt om uw omgeving te configureren. (Zie voor meer informatie [ingebouwde Windows PowerShell Desired status configuratie-bronnen](builtInResource.md).) In dit onderwerp biedt een overzicht van het ontwikkelen van resources en koppelingen naar onderwerpen met specifieke informatie over en voorbeelden.

## <a name="dsc-resource-components"></a>Onderdelen van DSC-resource

Een DSC-resource is een Windows PowerShell-module. De module bevat zowel het schema (de definitie van de configureerbare eigenschappen) en de implementatie (de code die het echte werk verricht dat door een opgegeven) voor de resource. Een DSC-resource schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een scriptmodule. U begint met de ondersteuning van PowerShell-klassen in versie 5, kunnen het schema en de implementatie zowel worden gedefinieerd in een klasse. De volgende onderwerpen wordt beschreven in meer detail DSC-resources te maken.

* [Schrijven van een aangepaste DSC-resource met MOF](authoringResourceMOF.md) 
* [Implementatie van een DSC-resource in C#](authoringResourceMofCS.md) 
* [Schrijven van een aangepaste DSC-resource met PowerShell-klassen](authoringResourceClass.md) 
* [Samengestelde bronnen: met een DSC-configuratie als een bron](authoringResourceComposite.md) 
* [Het hulpprogramma voor het Resource-Designer](authoringResourceMofDesigner.md) 

