---
title: Typen cmdlet-uitvoer | Microsoft Docs
ms.date: 01/18/2019
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.openlocfilehash: 8f761fdddd264b7c580c4a860081fdc5d2776ee7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786353"
---
# <a name="types-of-cmdlet-output"></a>Typen cmdlet-uitvoer

Power shell biedt verschillende methoden die kunnen worden aangeroepen door-cmdlets voor het genereren van uitvoer. Deze methoden gebruiken een specifieke bewerking om de uitvoer naar een specifieke gegevens stroom te schrijven, zoals de gegevens stroom geslaagd of de gegevens stroom fout. In dit artikel worden de typen uitvoer en de methoden beschreven die worden gebruikt om ze te genereren.

## <a name="types-of-output"></a>Typen uitvoer

### <a name="success-output"></a>Geslaagde uitvoer

Met-cmdlets kunt u successen rapporteren door een object te retour neren dat kan worden verwerkt door de volgende opdracht in de pijp lijn. Nadat de cmdlet is uitgevoerd, roept de cmdlet de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) aan. U wordt aangeraden deze methode aan te roepen in plaats van de methoden [System. console. WriteLine](/dotnet/api/System.Console.WriteLine) of [System. Management. Automation. host. PSHostUserInterface. WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) .

U kunt een para meter voor de **PassThru** -switch opgeven voor cmdlets die doorgaans geen objecten retour neren.
Wanneer de para meter **PassThru** switch is opgegeven op de opdracht regel, wordt de cmdlet gevraagd een object te retour neren. Zie voor een voor beeld van een cmdlet met een **PassThru** -para meter [toevoegen-geschiedenis](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Fout uitvoer

Cmdlets kunnen fouten rapporteren. Wanneer er een afsluit fout optreedt, genereert de cmdlet een uitzonde ring. Wanneer er een niet-afsluit fout optreedt, roept de cmdlet de methode [System. Management. Automation. provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) aan om een fout record naar de gegevens stroom van de fout te verzenden. Zie voor meer informatie over fout rapportage [concepten voor fouten rapportage](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Uitgebreide uitvoer

Cmdlets kunnen u nuttige informatie geven terwijl de cmdlet records correct verwerkt door de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) aan te roepen. De methode genereert uitgebreide berichten die aangeven hoe de actie wordt voortgezet.

Standaard worden uitgebreide berichten niet weer gegeven. U kunt de para meter **uitgebreid** opgeven wanneer de cmdlet wordt uitgevoerd om deze berichten weer te geven. **Verbose** is een gemeen schappelijke para meter die beschikbaar is voor alle cmdlets.

### <a name="progress-output"></a>Uitvoer van voortgang

Met cmdlets kunt u voortgangs gegevens aan u door geven wanneer de cmdlet taken uitvoert die veel tijd in beslag nemen, zoals het kopiëren van een map recursief. Om voortgangs gegevens weer te geven, roept de cmdlet de methode [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) aan.

### <a name="debug-output"></a>Debug-uitvoer

Met cmdlets kunnen fout opsporingsgegevens worden geboden die handig zijn bij het oplossen van problemen met de cmdlet-code. Als u fout opsporingsgegevens wilt weer geven, roept de cmdlet de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) aan.

Standaard worden fout opsporings berichten niet weer gegeven. U kunt de para meter **debug** opgeven wanneer de cmdlet wordt uitgevoerd om deze berichten weer te geven. **Debug** is een gemeen schappelijke para meter die beschikbaar is voor alle cmdlets.

### <a name="warning-output"></a>Uitvoer van waarschuwing

Met cmdlets kunt u waarschuwings berichten weer geven door de methode [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) aan te roepen.

Standaard worden waarschuwings berichten weer gegeven. U kunt echter waarschuwings berichten configureren met behulp van de `$WarningPreference` variabele of door gebruik te maken van de para meters **uitgebreid** en **fout opsporing** wanneer de cmdlet wordt aangeroepen.

## <a name="displaying-output"></a>Uitvoer weer geven

Voor alle aanroepen van write-methoden wordt de inhoud weer gegeven door specifieke runtime variabelen. De uitzonde ring hierop is de methode [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Door deze variabelen te gebruiken, kunt u de juiste schrijf aanroep uitvoeren op de juiste plaats in uw code en hoeft u zich geen zorgen te maken wanneer of de uitvoer moet worden weer gegeven.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Toegang tot de uitvoer functionaliteit van een hosttoepassing

U kunt ook een cmdlet ontwerpen om rechtstreeks toegang te krijgen tot de uitvoer functionaliteit van een host-toepassing via de Power shell-runtime. Het gebruik van de host-Api's van Power shell in plaats van [System. console](/dotnet/api/System.Console) -of [System. Windows. Forms](/dotnet/api/System.Windows.Forms) zorgt ervoor dat uw cmdlet werkt met diverse hosts. Bijvoorbeeld: de **powershell.exe** -console host, de **powershell_ise.exe** grafische host, de Power shell Remoting host en hosts van derden.

## <a name="see-also"></a>Zie ook

[Concepten voor foutrapportage](./error-reporting-concepts.md)

[Overzicht van cmdlets](./cmdlet-overview.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
