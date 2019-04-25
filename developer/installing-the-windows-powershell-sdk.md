---
title: De Windows PowerShell SDK installeren
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082478"
---
# <a name="installing-the-windows-powershell-sdk"></a>De Windows PowerShell SDK installeren

Van toepassing op: Windows PowerShell 2.0, Windows PowerShell 3.0

Het volgende onderwerp wordt beschreven hoe u de PowerShell SDK installeren op verschillende versies van Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows PowerShell 3.0 installeren SDK voor Windows 8 en WindowsServer 2012

Windows PowerShell 3.0 wordt automatisch geïnstalleerd met Windows 8 en Windows Server 2012. U kunt bovendien downloaden en de assembly-verwijzingen voor Windows PowerShell 3.0 installeren als onderdeel van de SDK voor Windows 8. Deze assembly's kunnen u voor het schrijven van cmdlets en providers host programma's voor Windows PowerShell 3.0. Wanneer u de Windows SDK voor Windows 8 installeert, wordt de Windows PowerShell-assembly's worden automatisch geïnstalleerd in de map verwijzing assembly in \Program bestanden (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Zie de Windows 8 SDK downloaden van de site voor meer informatie. Windows PowerShell-codevoorbeelden zijn ook beschikbaar in het midden-ontwikkeling.
Zie voor meer informatie de pagina van de voorbeeld Desktop code op de site Dev center.

Windows PowerShell 3.0 is bovendien achterwaarts compatibel met de SDK van Windows PowerShell 2.0, waaronder een aantal voorbeelden van code. Zie hieronder voor meer informatie over het downloaden van de SDK van Windows PowerShell 2.0. (Houd er rekening mee de 2.0 codevoorbeelden zijn compatibel met Windows 8 en Windows PowerShell 3.0, niet u Windows PowerShell 2.0 op een Windows 8-platform installeren.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows PowerShell 3.0 installeren SDK voor Windows 7 en Windows Server 2008 R2

Windows 7 en Windows Server 2008 R2 hebben automatisch PowerShell 2.0 is geïnstalleerd. Bovendien kunt u PowerShell 3.0 installeren op deze systemen. (Zie voor meer informatie, Windows PowerShell installeren.). Zoals hierboven beschreven, kunt u ook de Windows 8 SDK installeren op Windows 7 en Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installatie van Windows PowerShell 2.0 SDK voor Windows 7, Vista, XP, Server 2003 en Server 2008

De Windows PowerShell 2.0 SDK biedt de referentie-assembly's die nodig zijn voor het schrijven van cmdlets, providers en hosting van toepassingen en biedt C# voorbeeldcode die kunnen worden gebruikt als startpunt wanneer u begint met het schrijven van code.

Zie de Windows PowerShell 2.0 SDK voor het installeren van deze SDK.

### <a name="reference-assemblies"></a>Assembly-verwijzingen

Assembly-verwijzingen worden standaard geïnstalleerd op de volgende locatie: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> Code die is samengesteld op basis van de Windows PowerShell 2.0-assembly's kan niet worden geladen in de Windows PowerShell 1.0-installaties. Code die is samengesteld op basis van de Windows PowerShell 1.0-assembly's kan echter worden geladen in de Windows PowerShell 2.0-installaties.


### <a name="samples"></a>Voorbeelden

Voorbeelden van code worden standaard geïnstalleerd op de volgende locatie: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. De volgende secties bevatten een korte beschrijving van wat elke voorbeeld doet.

#### <a name="cmdlet-samples"></a>Cmdlet-voorbeelden

- GetProcessSample01 - ziet u hoe u een eenvoudige cmdlet die worden opgehaald van alle processen op de lokale computer schrijft.
- GetProcessSample02 - ziet u hoe u parameters toevoegt aan de cmdlet. De cmdlet heeft een of meer procesnamen en retourneert de overeenkomende processen.
- GetProcessSample03 - laat zien hoe om toe te voegen van de parameters die invoer van de pijplijn worden geaccepteerd.
- GetProcessSample04 - laat zien hoe afsluitfouten worden verwerkt.
- GetProcessSample05 - laat zien hoe om een lijst van de opgegeven processen weer te geven.
- ObjectSelecteren - laat zien hoe het schrijven van een filter om alleen bepaalde objecten te selecteren.
- SelectString - laat zien hoe om te zoeken naar bestanden voor de opgegeven patronen.
- StopProcessSample01 - leest het implementeren van een parameter PassThru gebruikt, en om aan te vragen van feedback van gebruikers door het aanroepen van de methoden shouldprocess wordt overgeslagen en ShouldContinue. Gebruikers opgeven voor de parameter PassThru wanneer ze afdwingen dat de cmdlet wilt retourneert een object
- StopProcessSample02 - laat zien hoe een specifiek proces beëindigen.
- StopProcessSample03 - ziet hoe u aliassen voor parameters declareren en hoe u bieden ondersteuning voor jokertekens.
- StopProcessSample04 - ziet u hoe u declareren parametersets, het object dat de cmdlet wordt gebruikt als invoer en het opgeven van de standaardparameter ingesteld voor het gebruik.

#### <a name="remoting-samples"></a>Voorbeelden van externe toegang

- RemoteRunspace01 - laat zien hoe het maken van een externe runspace die wordt gebruikt om een externe verbinding te maken.
- RemoteRunspacePool01 - ziet hoe u een van de groep van een externe runspace en hoe u meerdere opdrachten gelijktijdig uitgevoerd met behulp van deze groep.
- Serialization01 - laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat gegevens uit de geselecteerde openbare eigenschappen van deze klasse wordt behouden in de serialisatie/deserialisatie.
- Serialization02 - laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat de informatie van de instantie van deze klasse is behouden in de serialisatie/deserialisatie wanneer de gegevens niet beschikbaar in de openbare eigenschappen van de klasse zijn.
- Serialization03 - laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat de exemplaren van deze klasse en afgeleide klassen worden gedeserialiseerd (gereactiveerd) in live .NET-objecten.

#### <a name="event-samples"></a>Voorbeelden van gebeurtenis

- Event01 - ziet u hoe u een cmdlet voor gebeurtenisregistratie maakt die is afgeleid van ObjectEventRegistrationBase.
- Event02 - laat zien hoe laat zien hoe u voor het ontvangen van meldingen van Windows PowerShell-gebeurtenissen die worden gegenereerd op externe computers aan. Hierbij de PSEventReceived gebeurtenis die toegankelijk is via de klasse Runspace.

#### <a name="hosting-application-samples"></a>Voorbeelden van de toepassing die als host fungeert

- Runspace01 - ziet u hoe u de PowerShell-klasse om uit te voeren de `Get-Process` cmdlet synchroon.
De `Get-Process` cmdlet retourneert proces objecten voor elk proces dat wordt uitgevoerd op de lokale computer.
- Runspace02 - ziet u hoe u de PowerShell-klasse om uit te voeren de `Get-Process` en `Sort-Object` cmdlets synchroon. De `Get-Process` cmdlet retourneert proces objecten voor elk proces dat wordt uitgevoerd op de lokale computer en de `Sort-Object` sorteert de objecten op basis van de Id-eigenschap. De resultaten van deze opdrachten wordt weergegeven met behulp van een besturingselement DataGridView.
- Runspace03 - ziet u hoe u de PowerShell-klasse voor synchrone uitvoering van een script gebruikt en hoe u voor het afhandelen van niet-afsluitfouten. Het script een lijst van procesnamen ontvangt en haalt vervolgens deze processen. De resultaten van het script, met inbegrip van eventuele niet-afsluitfouten fouten die zijn gegenereerd wanneer het script is uitgevoerd, worden weergegeven in een consolevenster weergegeven.
- Runspace04 - ziet over het gebruik van de klasse PowerShell-opdrachten uitvoeren, en hoe u om af te vangen fouten die zijn opgetreden bij het uitvoeren van de opdrachten wordt beëindigd. Twee opdrachten worden uitgevoerd en de laatste opdracht wordt een parameterargument dat is niet geldig doorgegeven. Als gevolg hiervan geen objecten worden geretourneerd en wordt er een afsluitfout wordt gegenereerd.
- Runspace05 - laat zien hoe een module toevoegen aan een object InitialSessionState zodat de cmdlet van de module beschikbaar is wanneer de runspace wordt geopend. De module biedt een Get-Proc cmdlet (gedefinieerd door het voorbeeld GetProcessSample01) die synchroon wordt uitgevoerd met behulp van een PowerShell-object.
- Runspace06 - laat zien hoe een module toevoegen aan een object InitialSessionState zodat de module wordt geladen wanneer de runspace wordt geopend. De module biedt een Get-Proc cmdlet (gedefinieerd door het voorbeeld GetProcessSample02) die synchroon wordt uitgevoerd met behulp van een PowerShell-object.
- Runspace07 - laat zien hoe een runspace maken en vervolgens die runspace twee cmdlets synchroon worden uitgevoerd met behulp van een PowerShell-object.
- Runspace08 - ziet opdrachten, argumenten en toevoegen aan de pijplijn met een PowerShell-object en hoe u de opdrachten synchroon worden uitgevoerd.
- Runspace09 - ziet hoe u een script toevoegen aan de pijplijn met een PowerShell-object en hoe u het script asynchroon uitgevoerd. Gebeurtenissen worden gebruikt voor het afhandelen van de uitvoer van het script.
- Runspace10 - ziet u het maken van een standaardinstelling voor de eerste sessie, een cmdlet toevoegen aan de InitialSessionState, over het maken van een runspace die gebruikmaakt van de sessiestatus van de eerste en hoe u de opdracht uitvoert met behulp van een PowerShell-object.
- Runspace11 - ziet u hoe u de klasse ProxyCommand om een proxy-opdracht die een bestaande cmdlet-aanroepen, maar Hiermee beperkt u de set beschikbare parameters te maken. De proxy-opdracht wordt vervolgens toegevoegd aan een eerste sessiestatus die wordt gebruikt voor het maken van een beperkte runspace. Dit betekent dat de gebruiker toegang heeft tot de functionaliteit van de cmdlet alleen via de proxy-opdracht.
- PowerShell01 - laat zien hoe een beperkte runspace met behulp van een object InitialSessionState maken.
- PowerShell02 - ziet u hoe u een pool runspace gelijktijdig meerdere opdrachten uitvoeren.

#### <a name="host-samples"></a>Voorbeelden van host

- Host01 - ziet u hoe u een hosttoepassing die gebruikmaakt van een aangepaste host implementeert. In dit voorbeeld die wordt een runspace gemaakt die gebruikmaakt van de aangepaste host, en vervolgens de PowerShell-API wordt gebruikt om uit te voeren een script dat roept "afsluiten". De hosttoepassing wordt vervolgens kijkt naar de uitvoer van het script en de resultaten het tekstvenster.
- Host02 - laat zien hoe het schrijven van een hosttoepassing die gebruikmaakt van de Windows PowerShell-runtime, samen met een aangepaste host-implementatie. De hosttoepassing wordt de cultuur van de host ingesteld op Duits, wordt uitgevoerd de `Get-Process` -cmdlet en geeft de resultaten op als u ze ziet met behulp van pwrsh.exe en vervolgens af te drukken om de huidige datum en tijd in het Duits.
- Host03 - laat zien hoe een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.
- Host04 - laat zien hoe een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console. Weergave prompts die toestaan dat de gebruiker om op te geven meerdere mogelijkheden biedt ook ondersteuning voor deze hosttoepassing.
- Host05 - laat zien hoe een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console. Deze hosttoepassing biedt ook ondersteuning voor aanroepen naar externe computers met behulp van de `Enter-PsSession` en `Exit-PsSession` cmdlets.
- Host06 - laat zien hoe een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console. Dit voorbeeld wordt bovendien de Tokenizer-API's gebruikt om op te geven van de kleur van de tekst die is ingevoerd door de gebruiker.

#### <a name="provider-samples"></a>Voorbeelden van provider

- AccessDBProviderSample01 - laat zien hoe een klasse in de provider die is afgeleid van de klasse CmdletProvider rechtstreeks declareren. Het is hier opgenomen voor de volledigheid.

- AccessDBProviderSample02 - ziet u hoe u de methoden NewDrive en RemoveDrive ter ondersteuning van aanroepen naar overschrijven de `New-PSDrive` en `Remove-PSDrive` cmdlets. De providerklasse in dit voorbeeld is afgeleid van de klasse DriveCmdletProvider.

- AccessDBProviderSample03 - ziet u hoe u de methoden GetItem en SetItem ter ondersteuning van aanroepen naar overschrijven de `Get-Item` en `Set-Item` cmdlets. De providerklasse in dit voorbeeld is afgeleid van de klasse ItemCmdletProvider.

- AccessDBProviderSample04 - ziet u hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Copy-Item`, `Get-ChildItem`, `New-Item`, en `Remove-Item` cmdlets. Deze methoden moeten worden uitgevoerd wanneer het gegevensarchief bevat items die containers zijn. Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item. De providerklasse in dit voorbeeld is afgeleid van de klasse ItemCmdletProvider.

- AccessDBProviderSample05 - ziet u hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Move-Item` en `Join-Path` cmdlets. Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft om items in een container te verplaatsen en als het gegevensarchief geneste containers bevat. De providerklasse in dit voorbeeld is afgeleid van de klasse NavigationCmdletProvider.

- AccessDBProviderSample06 - ziet u hoe u inhoud methoden ter ondersteuning van aanroepen naar overschrijven de `Clear-Content`, `Get-Content`, en `Set-Content` cmdlets. Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft voor het beheren van de inhoud van de items in het gegevensarchief. De providerklasse in dit voorbeeld is afgeleid van de klasse NavigationCmdletProvider en deze de IContentCmdletProvider-interface implementeert.
