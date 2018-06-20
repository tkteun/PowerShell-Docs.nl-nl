---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: DSC-Resources
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219807"
---
# <a name="dsc-resources"></a>DSC-Resources

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Desired dat State Configuration (DSC) bronnen vindt u de bouwstenen voor een DSC-configuratie. Een bron beschrijft eigenschappen die kunnen worden geconfigureerd (schema) en bevat de functies van de PowerShell-script die de lokale Configuration Manager (LCM) ' om deze te maken zodat' aanroept.

Een resource kan iets als algemene als een bestand of de instelling van een IIS-server zo specifiek model.  Groepen van zoals bronnen worden gecombineerd in naar een DSC-Module, waarbij alle vereiste bestanden in een structuur die overdraagbaar en bevat metagegevens om te bepalen hoe de resources zijn bedoeld om te worden gebruikt.

De volgende onderwerpen beschrijven DSC-resources:

- [Ingebouwde DSC-resources](builtInResource.md)
- [Maken van aangepaste DSC-resources](authoringResource.md)
- [Ingebouwde DSC-resources voor Linux](lnxBuiltInResources.md)