---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeelden van runspaces
description: Voorbeelden van runspaces
ms.openlocfilehash: 0171622f3ade3b341bc226f14398d6d293262f0c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657958"
---
# <a name="runspace-samples"></a>Voorbeelden van runspaces

Deze sectie bevat voorbeeld code die laat zien hoe u verschillende soorten runspaces kunt gebruiken om opdrachten synchroon en asynchroon uit te voeren. U kunt micro soft Visual Studio gebruiken om een console toepassing te maken en vervolgens de code uit de onderwerpen in deze sectie naar uw host-toepassing te kopiëren.

## <a name="in-this-section"></a>In deze sectie

> [!NOTE]
> Zie voor voor beelden van hosttoepassingen die aangepaste host-interfaces maken, voor [beelden van aangepaste hosts](./custom-host-samples.md).

 [Runspace01](./runspace01-sample.md) -voor beeld In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de [Get-process-](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon uit te voeren en de uitvoer weer te geven in een console venster.

 [Runspace02](./runspace02-sample.md) -voor beeld In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om de cmdlets voor [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) synchroon uit te voeren. De resultaten van deze opdrachten worden weer gegeven met behulp van een [System. Windows. Forms. DataGridView](/dotnet/api/System.Windows.Forms.DataGridView) -besturings element.

 [Runspace03](./runspace03-sample.md) -voor beeld In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om een script synchroon uit te voeren en niet-afsluit fouten te verwerken. Het script ontvangt een lijst met proces namen en haalt deze processen vervolgens op. De resultaten van het script, met inbegrip van eventuele niet-afsluit fouten die zijn gegenereerd bij het uitvoeren van het script, worden weer gegeven in een console venster.

 [Runspace04](./runspace04-sample.md) -voor beeld In dit voor beeld ziet u hoe u de klasse [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) gebruikt om opdrachten uit te voeren en hoe u afsluit fouten kunt opvangen die worden gegenereerd bij het uitvoeren van de opdrachten. Er worden twee opdrachten uitgevoerd en de laatste opdracht is een ongeldig parameter argument door gegeven. Als gevolg hiervan worden er geen objecten geretourneerd en wordt er een afsluit fout gegenereerd.

 [Runspace05](./runspace05-sample.md) -voor beeld In dit voor beeld ziet u hoe u een module kunt toevoegen aan een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object, zodat de cmdlet van de module beschikbaar is wanneer de runs Pace wordt geopend. De module bevat een Get-Proc-cmdlet (gedefinieerd door het voor [beeld GetProcessSample01](../cmdlet/getprocesssample01-sample.md)) die synchroon wordt uitgevoerd met behulp van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.

 [Runspace06](./runspace06-sample.md) -voor beeld In dit voor beeld ziet u hoe u een module kunt toevoegen aan een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -object, zodat de module wordt geladen wanneer de runs Pace wordt geopend. De module biedt een Get-Proc-cmdlet (gedefinieerd door het voor [beeld GetProcessSample02](../cmdlet/getprocesssample02-sample.md)) die synchroon wordt uitgevoerd met behulp van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.

 [Runspace07](./runspace07-sample.md) -voor beeld In dit voor beeld ziet u hoe u een runs Pace maakt en vervolgens die runs Pace gebruikt om twee cmdlets synchroon uit te voeren met behulp van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object.

 [Runspace08](./runspace08-sample.md) -voor beeld Dit voor beeld laat zien hoe u opdrachten en argumenten kunt toevoegen aan de pijp lijn van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object en hoe de opdrachten synchroon moeten worden uitgevoerd.

 [Runspace09](./runspace09-sample.md) -voor beeld In dit voor beeld ziet u hoe u een script toevoegt aan de pijp lijn van een [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) -object en hoe het script asynchroon kan worden uitgevoerd. Gebeurtenissen worden gebruikt voor het afhandelen van de uitvoer van het script.

 [Runspace10](./runspace10-sample.md) -voor beeld Dit voor beeld laat zien hoe u een standaard begin sessie status kunt maken, hoe u een cmdlet kunt toevoegen aan de [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), hoe u een runs Pace maakt die de oorspronkelijke sessie status gebruikt en hoe u de opdracht uitvoert met behulp van een object [System. Management. Automation. Power shell](/dotnet/api/system.management.automation.powershell) .

 [Runspace11](./runspace11-sample.md) -voor beeld Hier ziet u hoe u de klasse [System. Management. Automation. ProxyCommand](/dotnet/api/System.Management.Automation.ProxyCommand) gebruikt voor het maken van een proxy opdracht die een bestaande cmdlet aanroept, maar de set beschik bare para meters beperkt. De proxy opdracht wordt vervolgens toegevoegd aan een initiële sessie status die wordt gebruikt om een beperkte runs Pace te maken. Dit betekent dat de gebruiker alleen via de proxy opdracht toegang kan krijgen tot de functionaliteit van de cmdlet.

## <a name="see-also"></a>Zie ook
