---
title: De Windows PowerShell SDK installeren
ms.date: 03/30/2020
ms.topic: article
ms.openlocfilehash: b47dddaf167024d30a7a31596f96569f976109d7
ms.sourcegitcommit: bf71c8c5e2a4fc7d5c3a67a537db1285089d03a7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80394980"
---
# <a name="installing-the-windows-powershell-sdk"></a>De Windows PowerShell SDK installeren

Van toepassing op: Windows Power Shell 2,0, Windows Power Shell 3,0

In het volgende onderwerp wordt beschreven hoe u de Power shell SDK installeert op verschillende versies van Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Windows Power Shell 3,0 SDK voor Windows 8 en Windows Server 2012 installeren

Windows Power Shell 3,0 wordt automatisch geïnstalleerd met Windows 8 en Windows Server 2012. Daarnaast kunt u de referentie-assembly's voor Windows Power Shell 3,0 downloaden en installeren als onderdeel van de SDK van Windows 8. Met deze assembly's kunt u cmdlets, providers en host-Program ma's schrijven voor Windows Power Shell 3,0. Wanneer u de Windows SDK voor Windows 8 installeert, worden de Windows Power shell-assembly's automatisch geïnstalleerd in de map Reference assembly, in `\Program Files
(x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`. Zie de download site voor Windows 8 SDK voor meer informatie. Voor beelden van Windows Power shell-code zijn ook beschikbaar in de opslag plaats [Power shell-SDK-samples](https://github.com/MicrosoftDocs/powershell-sdk-samples/tree/master/SDK-3.0) .

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Windows Power Shell 3,0 SDK installeren voor Windows 7 en Windows Server 2008 R2

In Windows 7 en Windows Server 2008 R2 is Power Shell 2,0 automatisch geïnstalleerd. Daarnaast kunt u Power Shell 3,0 installeren op deze systemen. U kunt ook de Windows 8 SDK installeren op Windows 7 en Windows Server 2008 R2, zoals hierboven wordt beschreven.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Windows Power Shell 2,0 SDK installeren voor Windows 7, Vista, XP, Server 2003 en Server 2008

De Windows Power Shell 2,0 SDK bevat de referentie assemblages die nodig zijn voor het schrijven van cmdlets, providers en hosting C# toepassingen, en biedt voorbeeld code die kan worden gebruikt als uitgangs punt wanneer u code gaat schrijven. U kunt de code voorbeelden downloaden van [https://www.microsoft.com/download/details.aspx?id=2560](https://www.microsoft.com/download/details.aspx?id=2560).

### <a name="reference-assemblies"></a>Referentie-assembly's

Referentie-assembly's worden standaard geïnstalleerd op de volgende locatie: `c:\Program Files\Reference
Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE]
> Code die is gecompileerd op basis van de Windows Power Shell 2,0-assembly's, kan niet worden geladen in Windows Power shell 1,0-installaties. Code die wordt gecompileerd op basis van de Windows Power shell 1,0-assembly's kan echter worden geladen in Windows Power Shell 2,0-installaties.

### <a name="samples"></a>Voorbeelden

Code voorbeelden worden standaard op de volgende locatie geïnstalleerd: `C:\Program Files\Microsoft
SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`. In de volgende secties vindt u een korte beschrijving van wat elk voor beeld doet.

#### <a name="cmdlet-samples"></a>Voor beelden van cmdlets

- GetProcessSample01: hier wordt beschreven hoe u een eenvoudige cmdlet schrijft waarmee alle processen op de lokale computer worden opgehaald.
- GetProcessSample02: hier ziet u hoe u para meters toevoegt aan de cmdlet. De cmdlet accepteert een of meer proces namen en retourneert de overeenkomende processen.
- GetProcessSample03: hier ziet u hoe u para meters toevoegt die invoer van de pijp lijn accepteren.
- GetProcessSample04: laat zien hoe u niet-afsluit fouten kunt verwerken.
- GetProcessSample05: hier ziet u hoe u een lijst met opgegeven processen weergeeft.
- Select object: laat zien hoe u een filter kunt schrijven om alleen bepaalde objecten te selecteren.
- SelectString: hier wordt weer gegeven hoe u bestanden zoekt voor opgegeven patronen.
- StopProcessSample01: toont hoe u een PassThru-para meter implementeert en hoe u feedback van gebruikers aanvraagt door aanroepen van de ShouldProcess-en ShouldContinue-methoden. Gebruikers opgeven de para meter PassThru wanneer ze willen afdwingen dat de cmdlet een object retourneert.
- StopProcessSample02: laat zien hoe u een specifiek proces kunt stoppen.
- StopProcessSample03: laat zien hoe u aliassen declareert voor para meters en hoe u Joker tekens kunt ondersteunen.
- StopProcessSample04: toont hoe u parameter sets declareert, het object dat de cmdlet als invoer gebruikt en hoe u de standaard parameterset opgeeft die moet worden gebruikt.

#### <a name="remoting-samples"></a>Externe voor beelden

- RemoteRunspace01: laat zien hoe u een externe runs Pace maakt die wordt gebruikt om een externe verbinding tot stand te brengen.
- RemoteRunspacePool01: hier wordt beschreven hoe u een externe runs Pace-groep bouwt en hoe u meerdere opdrachten gelijktijdig kunt uitvoeren met behulp van deze groep.
- Serialization01: hier ziet u hoe u een bestaande .NET-klasse bekijkt en ervoor zorgt dat de gegevens van de geselecteerde open bare eigenschappen van deze klasse behouden blijven in de serialisatie/deserialisatie.
- Serialization02: hier ziet u hoe u een bestaande .NET-klasse bekijkt en ervoor zorgt dat de gegevens van het exemplaar van deze klasse behouden blijven in de serialisatie/deserialisatie wanneer de informatie niet beschikbaar is in open bare eigenschappen van de klasse.
- Serialization03: hier ziet u hoe u een bestaande .NET-klasse bekijkt en ervoor zorgt dat instanties van deze klasse en afgeleide klassen worden gedeserialiseerd in Live .NET-objecten.

#### <a name="event-samples"></a>Gebeurtenis voorbeelden

- Event01: laat zien hoe u een cmdlet voor gebeurtenis registratie maakt door af te leiden van ObjectEventRegistrationBase.
- Event02: laat zien hoe u meldingen ontvangt van Windows Power shell-gebeurtenissen die op externe computers worden gegenereerd. De gebeurtenis PSEventReceived wordt gebruikt die beschikbaar is via de klasse runs Pace.

#### <a name="hosting-application-samples"></a>Voor beelden van hosting toepassingen

- Runspace01: laat zien hoe u de Power shell-klasse kunt gebruiken om de `Get-Process`-cmdlet synchroon uit te voeren.
  De `Get-Process` cmdlet retourneert proces objecten voor elk proces dat wordt uitgevoerd op de lokale computer.
- Runspace02: laat zien hoe u de Power shell-klasse kunt gebruiken om de `Get-Process`-en `Sort-Object`-cmdlets synchroon uit te voeren. De `Get-Process` cmdlet retourneert proces objecten voor elk proces dat wordt uitgevoerd op de lokale computer, en de `Sort-Object` sorteert de objecten op basis van hun id-eigenschap. De resultaten van deze opdrachten worden weer gegeven met behulp van een DataGridView-besturings element.
- Runspace03: laat zien hoe u de Power shell-klasse kunt gebruiken om een script synchroon uit te voeren en om niet-afsluit fouten te verwerken. Het script ontvangt een lijst met proces namen en haalt deze processen vervolgens op. De resultaten van het script, met inbegrip van eventuele niet-afsluit fouten die zijn gegenereerd bij het uitvoeren van het script, worden weer gegeven in een console venster.
- Runspace04: toont hoe u de Power shell-klasse gebruikt om opdrachten uit te voeren en hoe u afsluit fouten kunt opvangen die worden gegenereerd bij het uitvoeren van de opdrachten. Er worden twee opdrachten uitgevoerd en de laatste opdracht is een ongeldig parameter argument door gegeven. Als gevolg hiervan worden er geen objecten geretourneerd en wordt er een afsluit fout gegenereerd.
- Runspace05: laat zien hoe u een module kunt toevoegen aan een InitialSessionState-object, zodat de cmdlet van de module beschikbaar is wanneer de runs Pace wordt geopend. De module biedt een Get-proc-cmdlet (gedefinieerd door het GetProcessSample01-voor beeld) die synchroon wordt uitgevoerd met behulp van een Power shell-object.
- Runspace06: laat zien hoe u een module aan een InitialSessionState-object toevoegt, zodat de module wordt geladen wanneer de runs Pace wordt geopend. De module biedt een Get-proc-cmdlet (gedefinieerd door het GetProcessSample02-voor beeld) die synchroon wordt uitgevoerd met behulp van een Power shell-object.
- Runspace07: laat zien hoe u een runs Pace maakt en vervolgens die runs Pace gebruikt om twee cmdlets synchroon uit te voeren met behulp van een Power shell-object.
- Runspace08: laat zien hoe u opdrachten en argumenten kunt toevoegen aan de pijp lijn van een Power shell-object en hoe de opdrachten synchroon moeten worden uitgevoerd.
- Runspace09: hier wordt uitgelegd hoe u een script toevoegt aan de pijp lijn van een Power shell-object en hoe u het script asynchroon uitvoert. Gebeurtenissen worden gebruikt voor het afhandelen van de uitvoer van het script.
- Runspace10: laat zien hoe u een standaard begin sessie status maakt, hoe u een cmdlet toevoegt aan de InitialSessionState, hoe u een runs Pace maakt die de oorspronkelijke sessie status gebruikt en hoe u de opdracht uitvoert met behulp van een Power shell-object.
- Runspace11: laat zien hoe u de ProxyCommand-klasse kunt gebruiken om een proxy opdracht te maken die een bestaande cmdlet aanroept, maar beperkt de set beschik bare para meters. De proxy opdracht wordt vervolgens toegevoegd aan een initiële sessie status die wordt gebruikt om een beperkte runs Pace te maken. Dit betekent dat de gebruiker alleen via de proxy opdracht toegang kan krijgen tot de functionaliteit van de cmdlet.
- PowerShell01: laat zien hoe u een beperkte runs Pace maakt met behulp van een InitialSessionState-object.
- PowerShell02: laat zien hoe u een runs Pace-groep gebruikt om gelijktijdig meerdere opdrachten uit te voeren.

#### <a name="host-samples"></a>Host-voor beelden

- Host01: laat zien hoe u een host-toepassing implementeert die gebruikmaakt van een aangepaste host. In dit voor beeld wordt een runs Pace gemaakt die gebruikmaakt van de aangepaste host, waarna de Power shell-API wordt gebruikt om een script uit te voeren dat `exit`aanroept. De hosttoepassing bekijkt vervolgens de uitvoer van het script en de resultaten worden afgedrukt.
- Host02: laat zien hoe u een hosttoepassing schrijft die gebruikmaakt van de Windows Power shell-runtime samen met een aangepaste implementatie van de host. Met de hosttoepassing wordt de host-cultuur ingesteld op Duits, wordt de `Get-Process`-cmdlet uitgevoerd en worden de resultaten weer gegeven zoals u deze zou zien met behulp van pwrsh. exe, waarna de huidige gegevens en tijd in het Duits worden afgedrukt.
- Host03: hier ziet u hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console.
- Host04: hier ziet u hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console. Deze hosttoepassing biedt ook ondersteuning voor het weer geven van prompts waarmee de gebruiker meerdere keuzes kan opgeven.
- Host05: hier ziet u hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console. Deze hosttoepassing ondersteunt ook aanroepen naar externe computers met behulp van de cmdlets `Enter-PsSession` en `Exit-PsSession`.
- Host06: hier ziet u hoe u een interactieve op een console gebaseerde host-toepassing bouwt waarmee opdrachten worden gelezen vanaf de opdracht regel, de opdrachten worden uitgevoerd en de resultaten vervolgens worden weer gegeven in de console. Daarnaast gebruikt dit voor beeld de Tokenizer-Api's om de kleur van de tekst op te geven die door de gebruiker wordt ingevoerd.

#### <a name="provider-samples"></a>Provider voorbeelden

- AccessDBProviderSample01: hier wordt uitgelegd hoe u een provider klasse declareert die rechtstreeks is afgeleid van de CmdletProvider-klasse. Deze is alleen opgenomen voor volledigheid.

- AccessDBProviderSample02: laat zien hoe u de NewDrive-en RemoveDrive-methoden overschrijft ter ondersteuning van aanroepen naar de `New-PSDrive`-en `Remove-PSDrive`-cmdlets. De provider klasse in dit voor beeld is afgeleid van de DriveCmdletProvider-klasse.

- AccessDBProviderSample03: laat zien hoe u de GetItem-en SetItem-methoden overschrijft ter ondersteuning van aanroepen naar de `Get-Item`-en `Set-Item`-cmdlets. De provider klasse in dit voor beeld is afgeleid van de ItemCmdletProvider-klasse.

- AccessDBProviderSample04: hier wordt beschreven hoe u container methoden overschrijft om aanroepen naar de `Copy-Item`, `Get-ChildItem`, `New-Item`en `Remove-Item`-cmdlets te ondersteunen. Deze methoden moeten worden geïmplementeerd wanneer het gegevens archief items bevat die containers zijn. Een container is een groep onderliggende items onder een gemeen schappelijk bovenliggend item. De provider klasse in dit voor beeld is afgeleid van de ItemCmdletProvider-klasse.

- AccessDBProviderSample05: hier wordt beschreven hoe u container methoden overschrijft voor ondersteuning van aanroepen naar de `Move-Item`-en `Join-Path`-cmdlets. Deze methoden moeten worden geïmplementeerd wanneer de gebruiker items in een container moet verplaatsen en als het gegevens archief geneste containers bevat. De provider klasse in dit voor beeld is afgeleid van de NavigationCmdletProvider-klasse.

- AccessDBProviderSample06: laat zien hoe u inhouds methoden overschrijft om aanroepen naar de `Clear-Content`, `Get-Content`en `Set-Content`-cmdlets te ondersteunen. Deze methoden moeten worden geïmplementeerd wanneer de gebruiker de inhoud van de items in het gegevens archief moet beheren. De provider klasse in dit voor beeld is afgeleid van de NavigationCmdletProvider-klasse en implementeert de IContentCmdletProvider-interface.
