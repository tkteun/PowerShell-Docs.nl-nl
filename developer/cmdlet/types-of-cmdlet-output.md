---
title: Typen van de Cmdlet-uitvoer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845358"
---
# <a name="types-of-cmdlet-output"></a>Typen van de cmdlet-uitvoer

PowerShell biedt verschillende methoden die kunnen worden aangeroepen door cmdlets om uitvoer te genereren. Een specifieke bewerking deze methoden gebruiken om het hun uitvoer schrijven naar een specifieke-gegevensstroom, zoals de gegevensstroom geslaagd of de fout de gegevensstroom. Dit artikel wordt beschreven welke typen uitvoer en de gebruikte voor het genereren van deze methoden.

## <a name="types-of-output"></a>Typen uitvoer

### <a name="success-output"></a>Geslaagd-uitvoer

Cmdlets kunt melden door te retourneren een object dat kan worden verwerkt door de volgende opdracht in de pijplijn. Nadat de cmdlet heeft de bijbehorende actie is uitgevoerd, de cmdlet roept de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode. Het is raadzaam dat u deze methode in plaats van aanroepen de [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) of [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) methoden.

U krijgt u een **PassThru** overschakelen van de parameter voor de cmdlets die doorgaans niet objecten retourneren.
Wanneer de **PassThru** switch-parameter is opgegeven op de opdrachtregel, wordt de cmdlet gevraagd om een object te retourneren. Voor een voorbeeld van een cmdlet die heeft een **PassThru** parameter, Zie [toevoegen-geschiedenis](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Foutuitvoer

Cmdlets kunnen fouten rapporteren. Wanneer er een afsluitfout optreedt, wordt door de cmdlet een uitzondering genereert. Wanneer er een niet-afsluitfout optreedt, wordt de cmdlet roept de [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) methode voor het verzenden van een foutrecord voor een aan de gegevensstroom fout. Zie voor meer informatie over foutrapportage [fout Reporting concepten](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Uitgebreide uitvoer

Cmdlets nuttige informatie om u te kunnen bieden terwijl de cmdlet juist records is verwerkt door het aanroepen van de [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode. De methode genereert uitgebreide berichten die aangeven hoe de actie is voor u doorgaat.

Uitgebreide berichten worden niet standaard weergegeven. U kunt opgeven de **uitgebreid** parameter wanneer de cmdlet wordt uitgevoerd om deze berichten weer te geven. **Uitgebreide** is een algemene parameter die beschikbaar is voor alle cmdlets.

### <a name="progress-output"></a>Van voortgangsuitvoer

Cmdlets kan voortgangsinformatie bieden aan u, wanneer de cmdlet taken die erg lang duren om uit te voeren uitvoert, zoals het kopiëren van een directory recursief. Om weer te geven voortgangsgegevens van de cmdlet roept de [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) methode.

### <a name="debug-output"></a>Foutopsporingsuitvoer

Cmdlets kunt foutopsporingsberichten die nuttig zijn bij het oplossen van de cmdlet-code opgeven. Om weer te geven van de foutopsporingsgegevens van de cmdlet roept de [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode.

Standaard worden foutopsporingsberichten niet weergegeven. U kunt opgeven de **Debug** parameter wanneer de cmdlet wordt uitgevoerd om deze berichten weer te geven. **Fouten opsporen in** is een algemene parameter die beschikbaar is voor alle cmdlets.

### <a name="warning-output"></a>Waarschuwing-uitvoer

Cmdlets kunt waarschuwingsberichten weergeven door het aanroepen van de [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) methode.

Standaard worden waarschuwingsberichten weergegeven. U kunt waarschuwingsberichten echter configureren met behulp van de `$WarningPreference` variabele of met behulp van de **uitgebreid** en **Debug** parameters wanneer de cmdlet wordt aangeroepen.

## <a name="displaying-output"></a>Uitvoer weergeven

Voor alle schrijven-methode aanroepen, wordt de weergave van webinhoud bepaald door specifieke runtimevariabelen. De uitzondering hierop is de [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) methode. Met behulp van deze variabelen, kunt u de juiste oproep op de juiste plaats in uw code te schrijven en u geen zorgen over wanneer of als de uitvoer moet worden weergegeven.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Toegang tot de functionaliteit van de uitvoer van een host-toepassing

U kunt ook een cmdlet voor rechtstreekse toegang tot de functionaliteit van de uitvoer van een hosttoepassing via de PowerShell-runtime ontwerpen. Met behulp van de host API's die worden geleverd door PowerShell in plaats van [System.Console](/dotnet/api/System.Console) of [System.Windows.Forms](/dotnet/api/System.Windows.Forms) zorgt ervoor dat uw cmdlet met een verscheidenheid aan hosts werkt. Bijvoorbeeld: de **powershell.exe** consolehost, de **powershell_ise.exe** grafische host, de PowerShell remoting host en het externe hosts.

## <a name="see-also"></a>Zie ook

[Fout melden concepten](./error-reporting-concepts.md)

[Cmdlet-overzicht](./cmdlet-overview.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)