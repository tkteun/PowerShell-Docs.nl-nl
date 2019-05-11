---
title: Schrijven van een Windows PowerShell-Module | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229343"
---
# <a name="writing-a-windows-powershell-module"></a>Een Windows PowerShell-module schrijven

Dit document is geschreven voor beheerders, script-ontwikkelaars en cmdlet-ontwikkelaars die willen Inpakken en distribueren van de Windows PowerShell-cmdlets. Met behulp van Windows PowerShell-modules, kunt u Inpakken en distribueren van uw Windows PowerShell-oplossingen zonder een gecompileerde taal gebruikt.

Windows PowerShell-modules kunnen u naar partitie, organiseren en uw Windows PowerShell-code in zelfstandige, herbruikbare eenheden abstract. Met deze herbruikbare eenheden, kunt u eenvoudig uw modules rechtstreeks met anderen delen. Als u een script-ontwikkelaar bent, kunt u modules van derden voor het maken van aangepaste toepassingen op basis van een script ook verpakken. Modules, die vergelijkbaar is met modules in andere scripttalen zoals Perl en Python, kunt scripts gereed is voor productie-oplossingen die gebruikmaken van herbruikbare, herdistribueerbare onderdelen, met het voordeel van zodat u kunt verpakken en meerdere onderdelen te abstraheren aangepaste oplossingen maken.

Op de meest eenvoudige Windows PowerShell een geldige Windows PowerShell-script-code opgeslagen in een psm1-bestand als een module wordt behandeld. PowerShell wordt ook automatisch elke assembly binaire cmdlet behandelen als een module. U kunt echter ook gebruiken een module (of meer specifiek, een module-manifest) als u wilt een complete oplossing samen te bundelen. De volgende scenario's beschreven wordt doorgaans gebruikt voor Windows PowerShell-modules.

### <a name="libraries"></a>Bibliotheken

Modules kunnen worden gebruikt om te verpakken en distribueren samenhangend bibliotheken van de functies die veelvoorkomende taken uitvoeren. Normaal gesproken delen de namen van deze functies een of meer woorden die overeenkomen met de algemene taak die ze voor worden gebruikt. Deze functies kunnen ook worden die vergelijkbaar is met .NET Framework-klassen in dat ze kunnen openbare en privé-leden hebben. Een bibliotheek mag bijvoorbeeld een set functies voor bestandsoverdrachten. In dit geval het zelfstandig naamwoord zetten op basis van de algemene taak mogelijk 'file'.

### <a name="configuration"></a>Configuratie

Modules kunnen worden gebruikt voor het aanpassen van uw omgeving door toe te voegen bepaalde cmdlets, providers, functies en variabelen.

### <a name="compiled-code-development-and-distribution"></a>Gecompileerde Code-ontwikkeling en distributie

Cmdlet en provider ontwikkelaars kunnen modules gebruiken om te testen en distribueren van hun gecompileerde code hoeft te maken van modules. Hoeft te maken en -modules registreren, kunnen ze de assembly die de gecompileerde code als een module (een binaire-module bevat) importeren.

## <a name="see-also"></a>Zie ook

[Wat is een Windows PowerShell-Module?](./understanding-a-windows-powershell-module.md)

[Over het schrijven van een PowerShell-Script-Module](./how-to-write-a-powershell-script-module.md)

[Over het schrijven van een binaire waarde PowerShell-Module](./how-to-write-a-powershell-binary-module.md)

[Over het schrijven van een PowerShell-Module-Manifest](how-to-write-a-powershell-module-manifest.md)

[Het installatiepad PSModulePath wijzigen](./modifying-the-psmodulepath-installation-path.md)

[Een PowerShell-Module importeren](./importing-a-powershell-module.md)

[Een PowerShell-Module installeren](./installing-a-powershell-module.md)
