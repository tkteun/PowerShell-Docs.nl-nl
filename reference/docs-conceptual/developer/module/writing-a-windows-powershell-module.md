---
ms.date: 09/13/2016
ms.topic: reference
title: Een Windows PowerShell-module schrijven
description: Een Windows PowerShell-module schrijven
ms.openlocfilehash: 307241f0fb4d12c1a5cbd651a0ae4d5303098b27
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659434"
---
# <a name="writing-a-windows-powershell-module"></a>Een Windows PowerShell-module schrijven

Dit document is geschreven voor beheerders, script ontwikkelaars en cmdlet-ontwikkel aars die hun Windows Power shell-cmdlets moeten inpakken en distribueren. Met behulp van Windows Power shell-modules kunt u uw Windows Power shell-oplossingen verpakken en distribueren zonder een gecompileerde taal te gebruiken.

Met Windows Power shell-modules kunt u uw Windows Power shell-code partitioneren, ordenen en samen stellen in zelfstandige, herbruikbare eenheden. Met deze herbruikbare eenheden kunt u uw modules eenvoudig rechtstreeks met anderen delen. Als u een script ontwikkelaar bent, kunt u de modules van derden ook opnieuw inpakken om aangepaste toepassingen op basis van een script te maken. Modules, vergelijkbaar met modules in andere script talen, zoals perl en Python, bieden kant-en-klare script oplossingen die gebruikmaken van herbruikbare, herdistribueerbare onderdelen, met het toegevoegde voor deel van het mogelijk maken om meerdere onderdelen opnieuw te verpakken en samen te voegen om aangepaste oplossingen te creëren.

Windows Power shell behandelt op zijn meest eenvoudige wijze alle geldige Windows Power shell-script code die is opgeslagen in een. psm1-bestand als een module. Power shell behandelt ook automatisch een binaire cmdlet-assembly als een module. U kunt echter ook een module (of specifiek een module manifest) gebruiken om een volledige oplossing samen te bundelen. In de volgende scenario's worden veelvoorkomende toepassingen voor Windows Power shell-modules beschreven.

### <a name="libraries"></a>Bibliotheken

Modules kunnen worden gebruikt voor het inpakken en distribueren van samenhangende bibliotheken met functies die algemene taken uitvoeren. De namen van deze functies delen meestal een of meer zelfstandige naam woorden die overeenkomen met de algemene taak waarvoor ze worden gebruikt. Deze functies kunnen ook vergelijkbaar zijn met .NET Framework klassen, zodat ze open bare en privé-leden kunnen hebben. Een bibliotheek kan bijvoorbeeld een set met functies voor bestands overdrachten bevatten. In dit geval kan het zelfstandige naam woord dat de algemene taak weerspiegelt ' file ' zijn.

### <a name="configuration"></a>Configuratie

Modules kunnen worden gebruikt voor het aanpassen van uw omgeving door specifieke cmdlets, providers, functies en variabelen toe te voegen.

### <a name="compiled-code-development-and-distribution"></a>Gecompileerde code ontwikkeling en-distributie

Cmdlets en provider ontwikkelaars kunnen modules gebruiken om hun gecompileerde code te testen en te distribueren zonder dat ze modules hoeven te maken. Ze kunnen de assembly met de gecompileerde code importeren als een module (een binaire module) zonder dat ze modules hoeven te maken en registreren.

## <a name="see-also"></a>Zie ook

[Inzicht in een Windows PowerShell-module](./understanding-a-windows-powershell-module.md)

[Een PowerShell-scriptmodule schrijven](./how-to-write-a-powershell-script-module.md)

[Een binaire PowerShell-module schrijven](./how-to-write-a-powershell-binary-module.md)

[Een manifest voor een PowerShell-module schrijven](how-to-write-a-powershell-module-manifest.md)

[Het PSModulePath-installatiepad wijzigen](./modifying-the-psmodulepath-installation-path.md)

[Een PowerShell-module importeren](./importing-a-powershell-module.md)

[Een PowerShell-module installeren](./installing-a-powershell-module.md)
