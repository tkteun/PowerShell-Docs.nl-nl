---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Bekende problemen voor PowerShell 6.0
ms.openlocfilehash: e3e718be903ff2223064d5790d3d0fe554ef04cd
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267997"
---
# <a name="known-issues-for-powershell-60"></a>Bekende problemen voor PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Bekende problemen voor PowerShell op niet-Windows-Platforms

Alpha versies van PowerShell in Linux en macOS zijn voornamelijk functioneel maar wel enkele belangrijke beperkingen en problemen betreffende de bruikbaarheid. Bètaversies. ook van PowerShell in Linux en macOS functionele en stabieler dan alpha releases, maar nog steeds kunnen worden zonder een reeks functies en kan bevatten fouten. In sommige gevallen kan zijn deze problemen gewoon bugs die nog niet zijn opgelost. In andere gevallen (net als bij de standaardaliassen voor ls, cp, enzovoort), we op zoek zijn naar feedback van de community met betrekking tot de opties die we.

Opmerking: Vanwege de overeenkomsten van veel onderliggende subsystemen PowerShell op Linux en Mac OS is meestal hetzelfde niveau van de rijpheid op fouten en functies. Behalve zoals hieronder aangegeven, worden de problemen in deze sectie wordt toegepast op beide besturingssystemen.

### <a name="case-sensitivity-in-powershell"></a>Hoofdlettergevoeligheid in PowerShell

PowerShell is in het verleden op uniforme wijze niet-hoofdlettergevoelig, met enkele uitzonderingen. Op UNIX-achtige besturingssystemen, het bestandssysteem is voornamelijk hoofdlettergevoelig en PowerShell voldoet aan de standaard van het bestandssysteem. Dit is toegankelijk via een aantal manieren, duidelijk en niet-duidelijk.

#### <a name="directly"></a>Rechtstreeks

- Bij het opgeven van een bestand in PowerShell, kan de juiste aanvraag moet worden gebruikt.

#### <a name="indirectly"></a>Indirect

- Als een script probeert te laden van een module en de naam van de module is niet correct, indeling, mislukt de laden van de module. Dit kan een probleem is met bestaande scripts veroorzaken als de naam waarmee de module waarnaar wordt verwezen, komt niet overeen met de werkelijke bestandsnaam.
- Tabvoltooiing wordt niet automatisch aanvullen als de aanvraag van de naam van bestand onjuist is. Het fragment om te voltooien moet juist worden geïntegreerd. (Voltooiing is niet hoofdlettergevoelig voor naam en type lid voltooiingen.)

### <a name="ps1-file-extensions"></a>. Ps1 Bestandsextensies

PowerShell-scripts moeten eindigen op `.ps1` voor de interpreter om te begrijpen hoe u laadt en voer ze uit in het huidige proces. Scripts uitvoeren in het huidige proces is de gebruikelijke normaal voor PowerShell. De `#!` magische getal kunnen worden toegevoegd aan een script waarmee u beschikt niet over een `.ps1` uitbreiding, maar dit zorgt ervoor dat het script moet worden uitgevoerd in een nieuwe PowerShell-sessie zo wordt voorkomen dat het script werken goed bij het uitwisselen van objecten. (Opmerking: dit kan het wenselijk gedrag worden bij het uitvoeren van een PowerShell-script uit `bash` of een andere shell.)

### <a name="missing-command-aliases"></a>Ontbrekende Opdrachtaliassen

Op Linux/macOS, de 'gemak aliassen' voor de basisopdrachten `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` zijn verwijderd. PowerShell biedt op Windows, een set aliassen die zijn toegewezen aan de namen van de Linux-opdrachten voor het gebruiksgemak. Deze aliassen zijn verwijderd uit de standaard PowerShell op Linux/macOS-distributies, zodat de systeemeigen uitvoerbare bestand dat moet worden uitgevoerd zonder een pad op te geven.

Er zijn voor- en nadelen op deze manier. Verwijderen van de aliassen wordt aangegeven dat de ervaring van de systeemeigen opdracht naar de PowerShell-gebruiker, maar verlaagt u functionaliteit in de shell omdat de systeemeigen opdrachten tekenreeksen in plaats van objecten retourneren.

> [!NOTE]
> Dit is een gebied waar het PowerShell-team is op zoek naar feedback.
> Wat is de beste oplossing? We laat dit zo is, of het gemak aliassen weer toevoegen? Zie [uitgeven #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Jokertekens (Bij globbing) ondersteuning ontbreekt

Op dit moment voert PowerShell alleen jokertekens (Bij globbing) voor ingebouwde cmdlets in Windows en voor externe opdrachten of binaire bestanden, evenals op Linux-cmdlets. Dit betekent dat een opdracht zoals `ls
*.txt` mislukken omdat het sterretje zal niet worden uitgebreid zodat deze overeenkomt met de namen van bestanden. U kunt dit oplossen door op deze manier kunt werken `ls (gci *.txt | % name)` of eenvoudiger gezegd, `gci *.txt` met behulp van de ingebouwde PowerShell-equivalent aan `ls`.

Zie [#954](https://github.com/PowerShell/PowerShell/issues/954) feedback wilt geven over het verbeteren van de ervaring bij globbing op Linux/macOS.

### <a name="net-framework-vs-net-core-framework"></a>.NET framework en .NET Core Framework

PowerShell op Linux/macOS maakt gebruik van .NET Core is een subset van het volledige .NET Framework op Microsoft Windows. Dit is van belang omdat PowerShell directe toegang tot de onderliggende framework-typen, methoden, enzovoort biedt. Als gevolg hiervan scripts die worden uitgevoerd op Windows mogelijk niet worden uitgevoerd op niet-Windows-platforms vanwege de verschillen in de frameworks. Zie voor meer informatie over .NET Core Framework. <https://dotnetfoundation.org/net-core>

Met de komst van [.NET Standard2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 gaat back veel van de traditionele typen en methoden die aanwezig in het volledige .NET Framework zijn. Dit betekent dat PowerShell Core kan veel traditionele Windows PowerShell-modules zonder wijzigingen aan te laden. U kunt ons .NET Standard 2.0 gerelateerde werk volgen [hier](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Omleiding van problemen

Invoer-omleiding wordt niet ondersteund in PowerShell op elk platform.
[Probleem #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Gebruik `Get-Content` schrijven van de inhoud van een bestand in de pijplijn.

Omgeleide uitvoer bevat byte-volgordemarkering voor Unicode (BOM) als de standaard UTF-8-codering wordt gebruikt. De stuklijst wordt problemen veroorzaken bij het werken met hulpprogramma's die niet verwachten of wanneer u toevoegt aan een bestand. Gebruik `-Encoding Ascii` ASCII-tekst (die niet wordt Unicode, heeft geen een stuklijst) te schrijven.

> [!Note]
> Zie [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) om ons feedback over het verbeteren van de ervaring van de codering voor PowerShell Core voor alle platformen. We werken aan ondersteuning voor UTF-8 zonder een stuklijst en wijzigen van de codering standaardwaarden voor verschillende cmdlets mogelijk verschillende platforms.

### <a name="job-control"></a>Controle van de taak

Er is geen taak-control-ondersteuning in PowerShell op Linux/macOS.
De `fg` en `bg` opdrachten zijn niet beschikbaar.

U kunt gebruiken voor de tijd die [PowerShell-taken](/powershell/module/microsoft.powershell.core/about/about_jobs) die werken voor alle platformen.

### <a name="remoting-support"></a>Ondersteuning voor externe toegang

Op dit moment ondersteunt PowerShell Core PowerShell Remoting (PSRP) via WSMan met basisverificatie in macOS en Linux, en met NTLM-verificatie op Linux. (Op basis van een Kerberos-verificatie wordt niet ondersteund.)

Het werk voor externe toegang op basis van WSMan is ingesteld in de [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) opslagplaats.

PowerShell Core ondersteunt ook PowerShell Remoting (PSRP) via SSH op alle platformen (Windows, macOS en Linux). Terwijl dit wordt momenteel niet ondersteund in de productieomgeving, kunt u meer informatie over het instellen van deze van [hier](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Ondersteuning voor Just Enough-beheer (JEA)

De mogelijkheid beperkte administration (JEA) voor externe toegang om eindpunten te maken is momenteel niet beschikbaar in PowerShell op Linux/macOS. Deze functie is momenteel niet binnen het bereik van 6.0 en iets zullen wij beschouwen als post 6.0 omdat hiervoor belangrijke ontwerp.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`, en PowerShell

Omdat PowerShell wordt uitgevoerd voor de meeste opdrachten in het geheugen (zoals Python of Ruby), kunt u sudo niet rechtstreeks met PowerShell dient te worden gebruiken. (U kunt natuurlijk uitvoeren `powershell` van sudo.) Indien nodig een PowerShell-cmdlet uit in PowerShell ook uitvoeren met sudo, bijvoorbeeld `sudo `Set-Date` 8/18/2016`, en vervolgens u zou doen `sudo powershell `Set-datum` 8/18/2016`. Evenzo, kunt u niet exec een ingebouwde PowerShell direct. In plaats daarvan moet u zou doen `exec powershell item_to_exec`.

Dit probleem wordt momenteel bijgehouden als onderdeel van #3232.

### <a name="missing-cmdlets"></a>Ontbrekende Cmdlets

Een groot aantal van de opdrachten (cmdlets) die doorgaans beschikbaar zijn in PowerShell zijn niet beschikbaar in Linux/macOS. In veel gevallen zinvol deze opdrachten zijn niet op deze platforms (bijvoorbeeld Windows-specifieke kenmerken, zoals het register). Andere opdrachten, zoals de opdrachten voor de service-beheer (Get/Start/Stop-Service) aanwezig zijn, maar niet in werking. Toekomstige versies zullen deze problemen, bepaling van de verbroken cmdlets en de nieuwe toevoegt na verloop van tijd te corrigeren.

### <a name="command-availability"></a>Beschikbaarheid van de opdracht

De volgende tabel bevat opdrachten die bekend zijn niet te werken in PowerShell op Linux/macOS.

|Opdrachten|Operationele status|Opmerkingen|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|Niet beschikbaar.|Deze opdrachten wordt niet herkend. Dit moet worden opgelost in een toekomstige release.|
|`Get-Acl`, `Set-Acl`|Niet beschikbaar.|Deze opdrachten wordt niet herkend. Dit moet worden opgelost in een toekomstige release.|
|`Get-AuthenticodeSignature`, `Set-AuthenticodeSignature`|Niet beschikbaar.|Deze opdrachten wordt niet herkend. Dit moet worden opgelost in een toekomstige release.|
|`Wait-Process`|Beschikbaar, werkt niet goed. |Bijvoorbeeld ' Start-proces gvim - PassThru gebruikt | Wacht-proces werkt niet. het wachten tot het proces is mislukt.|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|Beschikbare maar werkt niet.|Schrijft een foutbericht met de mededeling dat de opdrachten niet werkt. Deze moeten worden opgelost in een toekomstige release.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|Beschikbaar, maar er zijn geen gebeurtenisbronnen zijn beschikbaar.|De PowerShell-opdrachten eventing aanwezig zijn, maar de meeste van de bronnen van gebeurtenissen die worden gebruikt met de opdrachten (zoals System.Timers.Timer) zijn niet beschikbaar in Linux maken van de opdrachten die niet kan worden gebruikt in de Alpha-release.|
|`Set-ExecutionPolicy`|Beschikbare maar werkt niet.|Retourneert een bericht weergegeven dat niet wordt ondersteund op dit platform. Uitvoeringsbeleid is een gebruiker gerichte "veiligheid belt" die voorkomt dat de gebruiker van het maken van dure fouten. Het is niet een beveiligingsgrens.|
|`New-PSSessionOption`, `New-PSTransportOption`|Beschikbare maar `New-PSSession` werkt niet.|`New-PSSessionOption` en `New-PSTransportOption` niet op dit moment zijn geverifieerd om te werken nu die `New-PSSession` werkt.|