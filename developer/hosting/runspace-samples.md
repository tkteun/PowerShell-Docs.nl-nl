---
title: Voorbeelden van runspace | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c92a6d3d-8d34-4a76-bdc3-dea923d9858e
caps.latest.revision: 17
ms.openlocfilehash: e24d40746da91f60aaf2af655ddcadc88ab6a4db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847745"
---
# <a name="runspace-samples"></a>Voorbeelden van runspaces

In deze sectie bevat voorbeelden van code die laat zien hoe u verschillende soorten runspaces opdrachten synchroon en asynchroon uitvoeren. Microsoft Visual Studio kunt u een consoletoepassing maken en kopieer vervolgens de code van de onderwerpen in deze sectie in uw hosttoepassing.

## <a name="in-this-section"></a>In deze sectie

> [!NOTE]
> Zie voor voorbeelden van hosttoepassingen die aangepaste hostinterfaces maken [voorbeelden van aangepaste Host](./custom-host-samples.md).

 [Voorbeeld Runspace01](./runspace01-sample.md) in dit voorbeeld laat zien hoe u de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse om uit te voeren de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon en de uitvoer in een console weergeven het venster.

 [Voorbeeld van Runspace02](./runspace02-sample.md) in dit voorbeeld laat zien hoe u de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse om uit te voeren de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchroon. De resultaten van deze opdrachten wordt weergegeven met behulp van een [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) besturingselement.

 [Voorbeeld van Runspace03](./runspace03-sample.md) in dit voorbeeld laat zien hoe u de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse voor synchrone uitvoering van een script, en hoe u voor het afhandelen van niet-afsluitfouten. Het script een lijst van procesnamen ontvangt en haalt vervolgens deze processen. De resultaten van het script, met inbegrip van eventuele niet-afsluitfouten fouten die zijn gegenereerd wanneer het script is uitgevoerd, worden weergegeven in een consolevenster weergegeven.

 [Voorbeeld Runspace04](./runspace04-sample.md) in dit voorbeeld laat zien hoe u de [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klasse voor het uitvoeren van opdrachten, en hoe u afsluitende catch-fouten die worden gegenereerd wanneer de opdrachten uitvoert. Twee opdrachten worden uitgevoerd en de laatste opdracht wordt een parameterargument dat is niet geldig doorgegeven. Als gevolg hiervan geen objecten worden geretourneerd en wordt er een afsluitfout wordt gegenereerd.

 [Voorbeeld van Runspace05](./runspace05-sample.md) in dit voorbeeld laat zien hoe u een module toevoegen aan een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object zodat de cmdlet van de module beschikbaar is wanneer de runspace wordt geopend. De module biedt u een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample01 voorbeeld](../cmdlet/getprocesssample01-sample.md)) die wordt uitgevoerd synchroon met een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

 [Voorbeeld van Runspace06](./runspace06-sample.md) in dit voorbeeld laat zien hoe u een module om in te voegen een [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object zodat de module wordt geladen wanneer de runspace wordt geopend. De module biedt een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample02 voorbeeld](../cmdlet/getprocesssample02-sample.md)) die wordt uitgevoerd synchroon met een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

 [Voorbeeld van Runspace07](./runspace07-sample.md) in dit voorbeeld laat zien hoe u een runspace maken en vervolgens die runspace twee cmdlets synchroon worden uitgevoerd met behulp van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

 [Voorbeeld Runspace08](./runspace08-sample.md) in dit voorbeeld laat zien hoe u opdrachten en argumenten toevoegen aan de pijplijn met een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object en hoe u de opdrachten synchroon worden uitgevoerd.

 [Voorbeeld Runspace09](./runspace09-sample.md) in dit voorbeeld laat zien hoe u een script toevoegen aan de pijplijn met een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object en hoe u kunt het script asynchroon uitvoeren. Gebeurtenissen worden gebruikt voor het afhandelen van de uitvoer van het script.

 [Runspace10 voorbeeld](./runspace10-sample.md) dit voorbeeld laat zien hoe u een initiële standaard sessiestatus gebruikt, maakt het toevoegen van een cmdlet voor het [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), over het maken van een runspace die gebruikmaakt van de status van de eerste sessie en hoe u de opdracht uitvoert met behulp van een [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.

 [Voorbeeld van Runspace11](./runspace11-sample.md) dit laat zien hoe u de [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) klasse te maken van een proxy-opdracht die een bestaande cmdlet-aanroepen, maar Hiermee beperkt u de set beschikbare parameters. De proxy-opdracht wordt vervolgens toegevoegd aan een eerste sessiestatus die wordt gebruikt voor het maken van een beperkte runspace. Dit betekent dat de gebruiker toegang heeft tot de functionaliteit van de cmdlet alleen via de proxy-opdracht.

## <a name="see-also"></a>Zie ook
