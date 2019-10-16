---
title: Een Windows Power shell-module schrijven | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352848"
---
# <a name="writing-a-windows-powershell-module"></a>Een Windows PowerShell-module schrijven

Dit document is geschreven voor beheerders, script ontwikkelaars en cmdlet-ontwikkel aars die hun Windows Power shell-cmdlets moeten inpakken en distribueren. Met behulp van Windows Power shell-modules kunt u uw Windows Power shell-oplossingen verpakken en distribueren zonder een gecompileerde taal te gebruiken.

Met Windows Power shell-modules kunt u uw Windows Power shell-code partitioneren, ordenen en samen stellen in zelfstandige, herbruikbare eenheden. Met deze herbruikbare eenheden kunt u uw modules eenvoudig rechtstreeks met anderen delen. Als u een script ontwikkelaar bent, kunt u de modules van derden ook opnieuw inpakken om aangepaste toepassingen op basis van een script te maken. Modules, vergelijkbaar met modules in andere script talen, zoals perl en Python, maken kant-en-klare script oplossingen mogelijk die gebruikmaken van herbruikbare, herdistribueerbare onderdelen, met het toegevoegde voor deel van het inschakelen van het opnieuw verpakken en samen voegen van meerdere onderdelen naar aangepaste oplossingen maken.

Windows Power shell behandelt op zijn meest eenvoudige wijze alle geldige Windows Power shell-script code die is opgeslagen in een. psm1-bestand als een module. Power shell behandelt ook automatisch een binaire cmdlet-assembly als een module. U kunt echter ook een module (of specifiek een module manifest) gebruiken om een volledige oplossing samen te bundelen. In de volgende scenario's worden veelvoorkomende toepassingen voor Windows Power shell-modules beschreven.

### <a name="libraries"></a>Library

Modules kunnen worden gebruikt voor het inpakken en distribueren van samenhangende bibliotheken met functies die algemene taken uitvoeren. De namen van deze functies delen meestal een of meer zelfstandige naam woorden die overeenkomen met de algemene taak waarvoor ze worden gebruikt. Deze functies kunnen ook vergelijkbaar zijn met .NET Framework klassen, zodat ze open bare en privé-leden kunnen hebben. Een bibliotheek kan bijvoorbeeld een set met functies voor bestands overdrachten bevatten. In dit geval kan het zelfstandige naam woord dat de algemene taak weerspiegelt ' file ' zijn.

### <a name="configuration"></a>Configuratie

Modules kunnen worden gebruikt voor het aanpassen van uw omgeving door specifieke cmdlets, providers, functies en variabelen toe te voegen.

### <a name="compiled-code-development-and-distribution"></a>Gecompileerde code ontwikkeling en-distributie

Cmdlets en provider ontwikkelaars kunnen modules gebruiken om hun gecompileerde code te testen en te distribueren zonder dat ze modules hoeven te maken. Ze kunnen de assembly met de gecompileerde code importeren als een module (een binaire module) zonder dat ze modules hoeven te maken en registreren.

## <a name="see-also"></a>Zie ook

[Informatie over een Windows Power shell-module](./understanding-a-windows-powershell-module.md)

[Een Power shell-script module schrijven](./how-to-write-a-powershell-script-module.md)

[Een binaire Power shell-module schrijven](./how-to-write-a-powershell-binary-module.md)

[Een Power shell-module manifest schrijven](how-to-write-a-powershell-module-manifest.md)

[Het installatiepad van PSModulePath wijzigen](./modifying-the-psmodulepath-installation-path.md)

[Een Power shell-module importeren](./importing-a-powershell-module.md)

[Een Power shell-module installeren](./installing-a-powershell-module.md)
