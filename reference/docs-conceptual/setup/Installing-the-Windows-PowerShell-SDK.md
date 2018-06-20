---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De Windows PowerShell SDK installeren
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953562"
---
# <a name="installing-the-windows-powershell-sdk"></a>De Windows PowerShell SDK installeren

Het volgende onderwerp wordt beschreven hoe de PowerShell-SDK installeren op verschillende versies van Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows PowerShell 3.0 installeren SDK voor Windows 8 en WindowsServer 2012

Windows PowerShell 3.0 wordt automatisch geïnstalleerd met Windows 8 en Windows Server 2012.
Bovendien kunt u downloaden en de verwijzings-assembly's voor Windows PowerShell 3.0 installeren als onderdeel van de Windows 8-SDK.
Deze assembly's kunnen u voor het schrijven van cmdlets, providers en host-programma's voor Windows PowerShell 3.0.
Wanneer u de Windows SDK voor Windows 8 installeert, wordt de Windows PowerShell-assembly's worden automatisch geïnstalleerd in de map van de verwijzing naar assembly in \Program bestanden (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0.
Zie voor meer informatie de [site voor het downloaden van Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Windows PowerShell-codevoorbeelden zijn ook beschikbaar in het Center ontwikkeling.
Zie voor meer informatie de voorbeeldpagina bureaublad code op de [Dev center site](http://code.msdn.microsoft.com/windowsdesktop/).

Windows PowerShell 3.0 is bovendien achterwaarts compatibel met de Windows PowerShell 2.0 SDK, waaronder een aantal codevoorbeelden.
Zie hieronder voor meer informatie over het downloaden van de Windows PowerShell 2.0-SDK.
(Opmerking terwijl de 2.0 codevoorbeelden die compatibel met Windows 8 en Windows PowerShell 3.0 zijn, u Windows PowerShell 2.0 op een Windows 8-platform installeren kunt).

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows PowerShell 3.0 installeren SDK voor Windows 7 en Windows Server 2008 R2

Windows 7 en Windows Server 2008 R2 hebben automatisch PowerShell 2.0 is geïnstalleerd.
Bovendien kunt u PowerShell 3.0 installeren op deze systemen.
(Zie voor meer informatie [Windows PowerShell installeren](Installing-Windows-PowerShell.md).).
Zoals hierboven wordt beschreven, kunt u ook de Windows 8-SDK installeren op Windows 7 en Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Windows PowerShell 2.0 installeren SDK voor Windows 7, Vista, XP, Server 2003 en Server 2008

De Windows PowerShell 2.0 SDK biedt de verwijzings-assembly's die nodig zijn voor het schrijven van cmdlets, providers en hosting van toepassingen en biedt C# voorbeeldcode die kan worden gebruikt als uitgangspunt wanneer u begint met het schrijven van code.

Zie het installeren van deze SDK [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).

## <a name="reference-assemblies"></a>Assembly-verwijzingen

Verwijzings-assembly's worden standaard geïnstalleerd in de volgende locatie: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Opmerking**: Code die wordt samengesteld op basis van de Windows PowerShell 2.0-assembly's kan niet worden geladen in de Windows PowerShell 1.0-installaties.
>Code die wordt samengesteld op basis van de Windows PowerShell 1.0-assembly's kan echter worden geladen in de Windows PowerShell 2.0-installaties.

## <a name="samples"></a>Voorbeelden

Codevoorbeelden zijn standaard geïnstalleerd in de volgende locatie: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

De volgende secties bieden een korte beschrijving van wat elk voorbeeld doet.

## <a name="cmdlet-samples"></a>Voorbeelden van de cmdlet
**GetProcessSample01**

Toont hoe u een eenvoudige cmdlet die alle processen op de lokale computer wordt schrijft.

**GetProcessSample02**

Toont hoe u parameters toevoegt aan de cmdlet.
De cmdlet heeft een of meer procesnamen en retourneert het overeenkomende processen.

**GetProcessSample03**

Laat zien hoe u de parameters die vanuit de pipeline-invoer accepteren toevoegen.

**GetProcessSample04**

Laat zien hoe nonterminating fouten worden verwerkt.

**GetProcessSample05**

Laat zien hoe u een lijst weergegeven met de opgegeven processen.

**SelectObject**

Laat zien hoe een schrijffilter is als alleen bepaalde objecten wilt selecteren.

**SelectString**

Laat zien hoe u bestanden voor de opgegeven patronen te zoeken.

**StopProcessSample01**

Toont hoe u implementeert een *PassThru* parameter en het aanvragen van feedback van gebruikers door het aanroepen van de [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) en [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) methoden.
Gebruikers opgeven de *PassThru* parameter wanneer ze graag willen afdwingen van de cmdlet om een object te retourneren

**StopProcessSample02**

Laat zien hoe u een specifiek proces stoppen.

**StopProcessSample03**

Toont hoe declareren aliassen voor parameters en hoe u kunt jokertekens ondersteunen.

**StopProcessSample04**

Laat zien hoe declareren parametersets, het object dat de cmdlet neemt als invoer- en het opgeven van de standaardparameter ingesteld om te gebruiken.

## <a name="remoting-samples"></a>Voorbeelden van externe toegang

**RemoteRunspace01**

Toont het maken van een externe runspace die wordt gebruikt om een externe verbinding te maken.

**RemoteRunspacePool01**

Leest het samenstellen van een groep met externe runspace en meerdere opdrachten gelijktijdig worden uitgevoerd met behulp van deze groep.

**Serialization01**

Laat zien hoe u kijken naar een bestaande .NET-klasse en zorg ervoor dat de gegevens van de geselecteerde openbare eigenschappen van deze klasse behouden tussen serialisatie/deserialisatie blijft.

**Serialization02**

Laat zien hoe u kijken naar een bestaande .NET-klasse en zorg ervoor dat de gegevens van het exemplaar van deze klasse is behouden in serialisatie/deserialisatie wanneer de gegevens niet beschikbaar in de openbare eigenschappen van de klasse zijn.

**Serialization03**

Laat zien hoe u kijken naar een bestaande .NET-klasse en zorg ervoor dat de exemplaren van deze klasse en afgeleide klassen (zijn gerehydrateerd) in live .NET-objecten worden gedeserialiseerd.

## <a name="event-samples"></a>Voorbeelden van gebeurtenis

**Event01**

Toont hoe u een cmdlet voor gebeurtenisregistratie maakt die zijn afgeleid van ObjectEventRegistrationBase.

**Event02**

Toont hoe om te zien hoe ontvangen van meldingen van Windows PowerShell-gebeurtenissen die worden gegenereerd op externe computers.
Deze maakt gebruik van de gebeurtenis PSEventReceived is beschikbaar via de [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) klasse.

## <a name="hosting-application-samples"></a>Voorbeelden van de toepassing die als host fungeert

**Runspace01**

Laat zien hoe u de [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasse om uit te voeren de [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synchroon.
De [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet retourneert [proces](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objecten voor elk proces dat wordt uitgevoerd op de lokale computer.

**Runspace02**

Laat zien hoe u de [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasse om uit te voeren de [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) en [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synchroon.
De [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet retourneert [proces](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objecten voor elk verwerkt op de lokale computer en de Sort-Object sorteert de objecten op basis van hun [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) eigenschap.
De resultaten van deze opdrachten wordt weergegeven met behulp van een [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) besturingselement.

**Runspace03**

Laat zien hoe u de [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasse synchroon een script uitvoeren en het afhandelen van fouten niet wordt beëindigd.
Het script ontvangt een lijst met procesnamen en wordt vervolgens opgehaald die processen.
De resultaten van het script, met inbegrip van eventuele fouten niet wordt beëindigd, die zijn gegenereerd tijdens het uitvoeren van het script worden weergegeven in een consolevenster.

**Runspace04**

Laat zien hoe u de [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klasse uitvoeren van opdrachten, en hoe wordt beëindigd catch-fouten die worden gegenereerd wanneer de opdrachten uit te voeren.
Twee opdrachten worden uitgevoerd en de laatste opdracht wordt een parameterargument is niet geldig doorgegeven.
Als gevolg hiervan geen objecten worden geretourneerd en een beëindigingsfout gegenereerd.

**Runspace05**

Laat zien hoe een module toevoegen aan een [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object zodat de cmdlet van de module beschikbaar is wanneer de runspace wordt geopend.
De invoegtoepassing biedt u een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample01 voorbeeld](https://technet.microsoft.com/library/ff602028.aspx)) die synchroon wordt uitgevoerd met behulp van een [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.

**Runspace06**

Ziet u het toevoegen van een module die u wilt een [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object zodat de module wordt geladen wanneer de runspace wordt geopend.
De module biedt een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample02 voorbeeld](https://technet.microsoft.com/library/ff602027.aspx)) die synchroon wordt uitgevoerd met behulp van een [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.

**Runspace07**

Laat zien hoe een runspace maken en vervolgens die runspace gebruiken voor het uitvoeren van de twee cmdlets synchroon met behulp van een [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object.

**Runspace08**

Laat zien hoe u opdrachten, argumenten en toevoegen aan de pijplijn met een [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object en het uitvoeren van de opdrachten synchroon.

**Runspace09**

Laat zien hoe u een script toevoegen aan de pijplijn met een [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) object en hoe u het script asynchroon uitgevoerd.
Gebeurtenissen worden gebruikt voor het afhandelen van de uitvoer van het script.

**Runspace10**

Het maken van een eerste sessie standaardstatus het toevoegen van een cmdlet voor het [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), het maken van een runspace die gebruikmaakt van de status van de eerste sessie en hoe u de opdracht uitvoert met behulp van een [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)object.

**Runspace11**

Laat zien hoe u de [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) klasse voor het maken van een proxy-opdracht die een bestaande cmdlet aangeroepen, maar Hiermee beperkt u de set beschikbare parameters.
De proxy-opdracht wordt vervolgens toegevoegd aan de status van een eerste sessie die wordt gebruikt voor het maken van een beperkte runspace.
Dit betekent dat de gebruiker toegang krijgen de functionaliteit van de cmdlet alleen via de proxy-opdracht tot.

**PowerShell01**

Het maken van een beperkte runspace met een [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) object.

**PowerShell02**

Toont hoe u een groep runspace met meerdere opdrachten gelijktijdig worden uitgevoerd.

## <a name="host-samples"></a>Voorbeelden van host

**Host01**

Laat zien hoe u een hosttoepassing die gebruikmaakt van een aangepaste host implementeren.
In dit voorbeeld wordt een runspace gemaakt die gebruikmaakt van de aangepaste host, en vervolgens de [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API wordt gebruikt voor het uitvoeren van een script dat roept 'afsluiten'.
De hosttoepassing vervolgens kijkt naar de uitvoer van het script en de resultaten wordt afgedrukt.

**Host02**

Laat zien hoe u een hosttoepassing die gebruikmaakt van de Windows PowerShell-runtime samen met een aangepaste host-implementatie schrijven.
De hosttoepassing wordt de cultuur host ingesteld op Duits, wordt uitgevoerd de [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet en geeft de resultaten op als u ze met behulp van pwrsh.exe en vervolgens afdrukken bestellen uit de huidige datum en tijd in het Duits zou zien.

**Host03**

Laat zien hoe een interactieve via de console-hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, voert de opdrachten en vervolgens de resultaten naar de console weergegeven.

**Host04**

Laat zien hoe een interactieve via de console-hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, voert de opdrachten en vervolgens de resultaten naar de console weergegeven.
Deze hosttoepassing ondersteunt ook weergeven prompts waarmee de gebruiker meerdere keuzes opgeven.

**Host05**

Laat zien hoe een interactieve via de console-hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, voert de opdrachten en vervolgens de resultaten naar de console weergegeven.
Deze hosttoepassing ondersteunt ook aanroepen naar externe computers met behulp van de [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) en [afsluiten-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.

**Host06**

Laat zien hoe een interactieve via de console-hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, voert de opdrachten en vervolgens de resultaten naar de console weergegeven.
Dit voorbeeld gebruikt bovendien de Tokenizer-API's de kleur van de tekst die is ingevoerd door de gebruiker opgeven.

## <a name="provider-samples"></a>Voorbeelden van de provider

**AccessDBProviderSample01**

Laat zien hoe declareren een providerklasse die is afgeleid rechtstreeks vanuit de [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) klasse.
Het is hier opgenomen voor de volledigheid.

**AccessDBProviderSample02**

Laat zien hoe overschrijven de [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) en [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) methoden voor het aanroepen van de cmdlets nieuw PSDrive en verwijder PSDrive ondersteunen.
De providerklasse in dit voorbeeld is afgeleid van de [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) klasse.

**AccessDBProviderSample03**

Laat zien hoe overschrijven de [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) en [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) methoden ter ondersteuning van aanroepen naar de cmdlets Get-Item en Set-Item.
De providerklasse in dit voorbeeld is afgeleid van de [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klasse.

**AccessDBProviderSample04**

Laat zien hoe overschrijven containermethoden ter ondersteuning van aanroepen naar de Copy-Item, Get-ChildItem New-Item en Remove-Item-cmdlets.
Deze methoden moeten worden uitgevoerd wanneer het gegevensarchief bevat items die containers zijn.
Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item.
De providerklasse in dit voorbeeld is afgeleid van de [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klasse.

**AccessDBProviderSample05**

Laat zien hoe overschrijven containermethoden ter ondersteuning van aanroepen naar de cmdlets Item verplaatsen en Join-pad.
Deze methoden moeten worden uitgevoerd wanneer de gebruiker moet items binnen een container verplaatsen en als het gegevensarchief geneste containers bevat.
De providerklasse in dit voorbeeld is afgeleid van de [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klasse.

**AccessDBProviderSample06**

Laat zien hoe u inhoud methoden ter ondersteuning van aanroepen naar de versleutelde inhoud overschrijven Get-inhoud en Set-Content-cmdlets.
Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft voor het beheren van de inhoud van de items in het gegevensarchief.
De providerklasse in dit voorbeeld is afgeleid van de [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klasse en implementeert de [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) interface.