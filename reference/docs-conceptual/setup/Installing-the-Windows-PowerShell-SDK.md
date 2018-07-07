---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De Windows PowerShell SDK installeren
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893535"
---
# <a name="installing-the-windows-powershell-sdk"></a>De Windows PowerShell SDK installeren

Het volgende onderwerp wordt beschreven hoe u de PowerShell SDK installeren op verschillende versies van Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows PowerShell 3.0 installeren SDK voor Windows 8 en WindowsServer 2012

Windows PowerShell 3.0 wordt automatisch geïnstalleerd met Windows 8 en Windows Server 2012.
U kunt bovendien downloaden en de assembly-verwijzingen voor Windows PowerShell 3.0 installeren als onderdeel van de SDK voor Windows 8.
Deze assembly's kunnen u voor het schrijven van cmdlets en providers host programma's voor Windows PowerShell 3.0.
Wanneer u de Windows SDK voor Windows 8 installeert, de Windows PowerShell-assembly's worden automatisch geïnstalleerd in de map van de assembly reference in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.
Zie voor meer informatie de [site voor het downloaden van Windows 8 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
Windows PowerShell-codevoorbeelden zijn ook beschikbaar in het midden-ontwikkeling.
Zie voor meer informatie de pagina van de voorbeeld Desktop code op de [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).

Windows PowerShell 3.0 is bovendien achterwaarts compatibel met de SDK van Windows PowerShell 2.0, waaronder een aantal voorbeelden van code.
Zie hieronder voor meer informatie over het downloaden van de SDK van Windows PowerShell 2.0.
(Houd er rekening mee de 2.0 codevoorbeelden zijn compatibel met Windows 8 en Windows PowerShell 3.0, niet u Windows PowerShell 2.0 op een Windows 8-platform installeren.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows PowerShell 3.0 installeren SDK voor Windows 7 en Windows Server 2008 R2

Windows 7 en Windows Server 2008 R2 hebben automatisch PowerShell 2.0 is geïnstalleerd.
Bovendien kunt u PowerShell 3.0 installeren op deze systemen.
(Zie voor meer informatie, [Windows PowerShell installeren](Installing-Windows-PowerShell.md).).
Zoals hierboven beschreven, kunt u ook de Windows 8 SDK installeren op Windows 7 en Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installatie van Windows PowerShell 2.0 SDK voor Windows 7, Vista, XP, Server 2003 en Server 2008

De Windows PowerShell 2.0 SDK biedt de referentie-assembly's die nodig zijn voor het schrijven van cmdlets, providers en hosting van toepassingen en C#-voorbeeldcode die kan worden gebruikt als startpunt wanneer u begint met het schrijven van code biedt.

Zie voor het installeren van deze SDK [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).

## <a name="reference-assemblies"></a>Assembly-verwijzingen

Assembly-verwijzingen worden standaard geïnstalleerd op de volgende locatie: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> Code die is samengesteld op basis van de Windows PowerShell 2.0-assembly's kan niet worden geladen in de Windows PowerShell 1.0-installaties.
> Code die is samengesteld op basis van de Windows PowerShell 1.0-assembly's kan echter worden geladen in de Windows PowerShell 2.0-installaties.

## <a name="samples"></a>Voorbeelden

Voorbeelden van code worden standaard geïnstalleerd op de volgende locatie: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

De volgende secties bevatten een korte beschrijving van wat elke voorbeeld doet.

## <a name="cmdlet-samples"></a>Cmdlet-voorbeelden

### <a name="getprocesssample01"></a>GetProcessSample01

Laat zien hoe u een eenvoudige cmdlet die worden opgehaald van alle processen op de lokale computer schrijft.

### <a name="getprocesssample02"></a>GetProcessSample02

Laat zien hoe u parameters toevoegt aan de cmdlet.
De cmdlet heeft een of meer procesnamen en retourneert de overeenkomende processen.

### <a name="getprocesssample03"></a>GetProcessSample03

Laat zien hoe u parameters die invoer van de pijplijn toevoegen.

### <a name="getprocesssample04"></a>GetProcessSample04

Laat zien hoe afsluitfouten worden verwerkt.

### <a name="getprocesssample05"></a>GetProcessSample05

Laat zien hoe u een lijst weergeven met de opgegeven processen.

### <a name="selectobject"></a>ObjectSelecteren

Laat zien hoe het schrijven van een filter om alleen bepaalde objecten te selecteren.

### <a name="selectstring"></a>SelectString

Laat zien hoe om te zoeken naar bestanden voor de opgegeven patronen.

### <a name="stopprocesssample01"></a>StopProcessSample01

Laat zien hoe u voor het implementeren van een *PassThru* parameter en het aanvragen van feedback van gebruikers op aanroepen naar de [shouldprocess wordt overgeslagen](/dotnet/api/system.management.automation.cmdlet.shouldprocess) en [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methoden.
Gebruikers opgeven de *PassThru* parameter wanneer ze afdwingen dat de cmdlet wilt retourneert een object

### <a name="stopprocesssample02"></a>StopProcessSample02

Laat zien hoe u een specifiek proces beëindigen.

### <a name="stopprocesssample03"></a>StopProcessSample03

Laat zien hoe om te declareren aliassen voor de parameters en hoe u ondersteuning voor jokertekens.

### <a name="stopprocesssample04"></a>StopProcessSample04

Laat zien hoe u declareren parametersets, het object dat de cmdlet wordt gebruikt als invoer en het opgeven van de standaardparameter ingesteld voor het gebruik.

## <a name="remoting-samples"></a>Voorbeelden van externe toegang

### <a name="remoterunspace01"></a>RemoteRunspace01

Laat zien hoe het maken van een externe runspace die wordt gebruikt om een externe verbinding te maken.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Laat zien hoe u een van de groep van een externe runspace en hoe u meerdere opdrachten gelijktijdig uitgevoerd met behulp van deze groep.

### <a name="serialization01"></a>Serialization01

Laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat gegevens uit de geselecteerde openbare eigenschappen van deze klasse wordt behouden in de serialisatie/deserialisatie.

### <a name="serialization02"></a>Serialization02

Laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat de informatie van de instantie van deze klasse is behouden in de serialisatie/deserialisatie wanneer de gegevens niet beschikbaar in de openbare eigenschappen van de klasse zijn.

### <a name="serialization03"></a>Serialization03

Laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat de exemplaren van deze klasse en afgeleide klassen worden gedeserialiseerd (gereactiveerd) in live .NET-objecten.

## <a name="event-samples"></a>Voorbeelden van gebeurtenis

### <a name="event01"></a>Event01

Laat zien hoe u een cmdlet voor gebeurtenisregistratie maakt die is afgeleid van ObjectEventRegistrationBase.

### <a name="event02"></a>Event02

Laat zien hoe laat zien hoe u voor het ontvangen van meldingen van Windows PowerShell-gebeurtenissen die worden gegenereerd op externe computers aan.
Hierbij de PSEventReceived gebeurtenis die toegankelijk is via de [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) klasse.

## <a name="hosting-application-samples"></a>Voorbeelden van de toepassing die als host fungeert

### <a name="runspace01"></a>Runspace01

Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse om uit te voeren de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon.
De [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retourneert [proces](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objecten voor elk proces dat wordt uitgevoerd op de lokale computer.

### <a name="runspace02"></a>Runspace02

Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse om uit te voeren de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchroon.
De [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retourneert [proces](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objecten voor elk proces dat wordt uitgevoerd op de lokale computer en de `Sort-Object` sorteert de objecten op basis van hun [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) de eigenschap.
De resultaten van deze opdrachten wordt weergegeven met behulp van een [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) besturingselement.

### <a name="runspace03"></a>Runspace03

Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse voor synchrone uitvoering van een script, en hoe u voor het afhandelen van niet-afsluitfouten.
Het script een lijst van procesnamen ontvangt en haalt vervolgens deze processen.
De resultaten van het script, met inbegrip van eventuele niet-afsluitfouten fouten die zijn gegenereerd wanneer het script is uitgevoerd, worden weergegeven in een consolevenster weergegeven.

### <a name="runspace04"></a>Runspace04

Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse voor het uitvoeren van opdrachten, en hoe u afsluitende catch-fouten die worden gegenereerd wanneer de opdrachten uitvoert.
Twee opdrachten worden uitgevoerd en de laatste opdracht wordt een parameterargument dat is niet geldig doorgegeven.
Als gevolg hiervan geen objecten worden geretourneerd en wordt er een afsluitfout wordt gegenereerd.

### <a name="runspace05"></a>Runspace05

Laat zien hoe u een module toevoegen aan een [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object zodat de cmdlet van de module beschikbaar is wanneer de runspace wordt geopend.
De module biedt u een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample01 voorbeeld](https://technet.microsoft.com/library/ff602028.aspx)) die synchroon wordt uitgevoerd met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell) object.

### <a name="runspace06"></a>Runspace06

Laat zien hoe een module toevoegt een [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object zodat de module wordt geladen wanneer de runspace wordt geopend.
De module biedt een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample02 voorbeeld](https://technet.microsoft.com/library/ff602027.aspx)) die synchroon wordt uitgevoerd met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell) object.

### <a name="runspace07"></a>Runspace07

Laat zien hoe u een runspace maken en vervolgens die runspace twee cmdlets synchroon worden uitgevoerd met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell) object.

### <a name="runspace08"></a>Runspace08

Laat zien hoe u opdrachten en argumenten toevoegen aan de pijplijn met een [PowerShell](/dotnet/api/system.management.automation.powershell) object en hoe u de opdrachten synchroon worden uitgevoerd.

### <a name="runspace09"></a>Runspace09

Laat zien hoe u een script toevoegen aan de pijplijn met een [PowerShell](/dotnet/api/system.management.automation.powershell) object en hoe u kunt het script asynchroon uitvoeren.
Gebeurtenissen worden gebruikt voor het afhandelen van de uitvoer van het script.

### <a name="runspace10"></a>Runspace10

Laat zien hoe u een initiële standaard sessiestatus gebruikt, maakt het toevoegen van een cmdlet voor de [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), over het maken van een runspace die gebruikmaakt van de sessiestatus van de eerste en hoe u de opdracht uitvoert met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell)object.

### <a name="runspace11"></a>Runspace11

Laat zien hoe u de [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) klasse te maken van een proxy-opdracht die een bestaande cmdlet-aanroepen, maar Hiermee beperkt u de set beschikbare parameters.
De proxy-opdracht wordt vervolgens toegevoegd aan een eerste sessiestatus die wordt gebruikt voor het maken van een beperkte runspace.
Dit betekent dat de gebruiker toegang heeft tot de functionaliteit van de cmdlet alleen via de proxy-opdracht.

### <a name="powershell01"></a>PowerShell01

Laat zien hoe u het maken van een beperkte runspace met een [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.

### <a name="powershell02"></a>PowerShell02

Ziet u hoe u een pool runspace gelijktijdig meerdere opdrachten uitvoeren.

## <a name="host-samples"></a>Voorbeelden van host

### <a name="host01"></a>Host01

Laat zien hoe u een hosttoepassing die gebruikmaakt van een aangepaste host implementeert.
In dit voorbeeld wordt een runspace gemaakt die gebruikmaakt van de aangepaste host, en vervolgens de [PowerShell](/dotnet/api/system.management.automation.powershell) API wordt gebruikt om uit te voeren een script waarmee "afsluiten" wordt aangeroepen.
De hosttoepassing wordt vervolgens kijkt naar de uitvoer van het script en de resultaten het tekstvenster.

### <a name="host02"></a>Host02

Laat zien hoe het schrijven van een hosttoepassing die gebruikmaakt van de Windows PowerShell-runtime, samen met een aangepaste host-implementatie.
De hosttoepassing wordt de cultuur van de host ingesteld op Duits, wordt uitgevoerd de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -cmdlet en geeft de resultaten op als u ze ziet met behulp van pwrsh.exe en vervolgens af te drukken om de huidige datum en tijd in het Duits.

### <a name="host03"></a>Host03

Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.

### <a name="host04"></a>Host04

Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.
Weergave prompts die toestaan dat de gebruiker om op te geven meerdere mogelijkheden biedt ook ondersteuning voor deze hosttoepassing.

### <a name="host05"></a>Host05

Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.
Deze hosttoepassing biedt ook ondersteuning voor aanroepen naar externe computers met behulp van de [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) en [afsluiten PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.

### <a name="host06"></a>Host06

Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.
Dit voorbeeld wordt bovendien de Tokenizer-API's gebruikt om op te geven van de kleur van de tekst die is ingevoerd door de gebruiker.

## <a name="provider-samples"></a>Voorbeelden van provider

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Laat zien hoe u een providerklasse die is afgeleid rechtstreeks van declareert de [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) klasse.
Het is hier opgenomen voor de volledigheid.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Laat zien hoe u overschrijven de [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) en [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methoden voor de ondersteuning van aanroepen naar de `New-PSDrive` en `Remove-PSDrive` cmdlets.
De providerklasse in dit voorbeeld is afgeleid van de [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) klasse.

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Laat zien hoe u overschrijven de [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) en [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methoden voor de ondersteuning van aanroepen naar de `Get-Item` en `Set-Item` cmdlets.
De providerklasse in dit voorbeeld is afgeleid van de [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasse.

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Copy-Item`, `Get-ChildItem`, `New-Item`, en `Remove-Item` cmdlets.
Deze methoden moeten worden uitgevoerd wanneer het gegevensarchief bevat items die containers zijn.
Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item.
De providerklasse in dit voorbeeld is afgeleid van de [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasse.

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Move-Item` en `Join-Path` cmdlets.
Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft om items in een container te verplaatsen en als het gegevensarchief geneste containers bevat.
De providerklasse in dit voorbeeld is afgeleid van de [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasse.

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Laat zien hoe u inhoud methoden ter ondersteuning van aanroepen naar overschrijven de `Clear-Content`, `Get-Content`, en `Set-Content` cmdlets.
Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft voor het beheren van de inhoud van de items in het gegevensarchief.
De providerklasse in dit voorbeeld is afgeleid van de [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasse en implementeert de [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.