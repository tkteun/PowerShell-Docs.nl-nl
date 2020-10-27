---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeelden van aangepaste hosts
description: Voorbeelden van aangepaste hosts
ms.openlocfilehash: 939b9f5d6bbc3ccf1ac95343e897ecffef0a2f42
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649307"
---
# <a name="custom-host-samples"></a>Voorbeelden van aangepaste hosts

Deze sectie bevat voorbeeld code voor het schrijven van een aangepaste host. U kunt micro soft Visual Studio gebruiken om een console toepassing te maken en vervolgens de code uit de onderwerpen in deze sectie naar uw host-toepassing te kopiëren.

## <a name="in-this-section"></a>In deze sectie

 [Host01](./host01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een host-toepassing implementeert die gebruikmaakt van een eenvoudige aangepaste host.

 [Host02](./host02-sample.md) -voor beeld In dit voor beeld ziet u hoe u een host-toepassing schrijft die gebruikmaakt van de Windows Power shell-runtime samen met een aangepaste implementatie van de host. Met de hosttoepassing wordt de host-cultuur ingesteld op Duits, wordt de cmdlet [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) uitgevoerd en worden de resultaten weer gegeven zoals u deze zou zien met behulp van pwrsh.exe, waarna de huidige gegevens en tijd in het Duits worden afgedrukt.

 [Host03](./host03-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console.

 [Host04](./host04-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console. Deze hosttoepassing biedt ook ondersteuning voor het weer geven van prompts waarmee de gebruiker meerdere keuzes kan opgeven.

 [Host05](./host05-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console. Deze hosttoepassing ondersteunt ook aanroepen naar externe computers met behulp van de cmdlets [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) en [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession)

 [Host06](./host06-sample.md) -voor beeld Dit voor beeld laat zien hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console. Daarnaast gebruikt dit voor beeld de Tokenizer-Api's om de kleur van de tekst op te geven die door de gebruiker wordt ingevoerd.

## <a name="see-also"></a>Zie ook
