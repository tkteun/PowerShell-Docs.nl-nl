---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Bekende problemen voor PowerShell 6.0
ms.openlocfilehash: 6ad1bcaf1de06f204b57eb8ce23b3053ba4a5b38
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2018
---
# <a name="known-issues-for-powershell-60"></a>Bekende problemen voor PowerShell 6.0

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>Bekende problemen voor PowerShell op niet-Windows-Platforms

Alpha releases van PowerShell op Linux- en Mac OS zijn voornamelijk functioneel maar wel enkele belangrijke beperkingen en gebruiksproblemen. Beta vrijgegeven van PowerShell op Linux en Mac OS functionele en meer dan alfanumerieke releases stabiele maar nog steeds mogelijk ontbreken van een reeks functies en kan bevatten fouten. In sommige gevallen kan zijn deze problemen gewoon bugs die nog niet zijn opgelost. In andere gevallen (net als bij de standaardaliassen voor ls, cp, enzovoort), we zoekt feedback van de community met betrekking tot de keuzes die we maakt.

Opmerking: Als gevolg van de overeenkomsten van veel onderliggende subsystemen PowerShell op Linux- en Mac OS vaak delen van hetzelfde niveau van de vervaldatum in fouten en functies. Behalve zoals hieronder aangegeven, wordt de problemen in deze sectie voor beide besturingssystemen geldt.

### <a name="case-sensitivity-in-powershell"></a>Hoofdlettergevoeligheid in PowerShell

PowerShell is in het verleden hebben gelijkmatig niet hoofdlettergevoelig is, met enkele uitzonderingen. Op UNIX-achtige besturingssystemen, het bestandssysteem is hoofdzakelijk hoofdlettergevoelig en PowerShell voldoet aan de standaard van het bestandssysteem. Dit is toegankelijk via een aantal manieren duidelijker en niet duidelijk.

#### <a name="directly"></a>rechtstreeks

- Bij het opgeven van een bestand in PowerShell moet hoofdlettergevoelig worden gebruikt.

#### <a name="indirectly"></a>Indirect

- Als een script probeert een module laden en de naam van de module is niet correct geïntegreerd laden van de module zullen mislukken. Dit kan een probleem met de bestaande scripts veroorzaken als de naam waarmee de module waarnaar wordt verwezen, komt niet overeen met de werkelijke bestandsnaam.
- Tabblad voltooiing wordt niet automatisch aanvullen als het bestand hoofdletters en kleine letters onjuist is. Het fragment te voltooien moet juist worden geïntegreerd. (Voltooiing is niet hoofdlettergevoelig voor de naam en type lid voltooiingen.)

### <a name="ps1-file-extensions"></a>. Ps1 Bestandsextensies

PowerShell-scripts moeten eindigen op `.ps1` voor de interpreter om te begrijpen hoe laden en in het huidige proces worden uitgevoerd. Uitvoeren van scripts in het huidige proces is de gebruikelijke normaal voor PowerShell. De `#!` magische getal kan worden toegevoegd aan een script dat u beschikt niet over een `.ps1` uitbreiding, maar dit wordt het script moet worden uitgevoerd in een nieuwe PowerShell-sessie zo wordt voorkomen dat het script werken goed bij het uitwisselen van objecten. (Opmerking: dit kan het wenselijk gedrag worden bij het uitvoeren van een PowerShell-script uit `bash` of een andere shell.)

### <a name="missing-command-aliases"></a>Ontbrekende opdracht aliassen

Op Linux/Mac OS, 'gemak aliassen' voor de basisopdrachten `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps` zijn verwijderd. Op Windows biedt PowerShell een reeks aliassen die zijn toegewezen aan de namen van de Linux-opdrachten voor het gebruiksgemak. Deze aliassen zijn verwijderd uit de standaard PowerShell op Linux/Mac OS-distributies, zodat de systeemeigen uitvoerbaar bestand moet worden uitgevoerd zonder op te geven van een pad.

Er zijn voor- en nadelen voor dit te doen. Verwijderen van de aliassen beschrijft de ervaring systeemeigen opdracht naar de PowerShell-gebruiker, maar verlaagt functionaliteit in de shell omdat de systeemeigen opdrachten tekenreeksen in plaats van objecten retourneren.

> [!NOTE]
> Dit is een gebied waar het PowerShell-team is op zoek naar feedback.
> Wat is de aanbevolen oplossing? We laat of het gemak aliassen weer toevoegen? Zie [uitgeven #929](https://github.com/PowerShell/PowerShell/issues/929).

### <a name="missing-wildcard-globbing-support"></a>Jokertekens (Bij globbing) ondersteuning ontbreekt

Op dit moment komt PowerShell alleen jokertekens (Bij globbing) voor ingebouwde cmdlets in Windows en voor externe opdrachten of binaire bestanden, evenals op Linux-cmdlets. Dit betekent dat een opdracht zoals `ls
*.txt` mislukt omdat het sterretje zal niet worden uitgebreid zodat deze overeenkomen met bestandsnamen. U kunt dit oplossen door op deze manier kunt werken `ls (gci *.txt | % name)` of eenvoudigweg `gci *.txt` met behulp van het ingebouwde PowerShell-equivalent voor `ls`.

Zie [#954](https://github.com/PowerShell/PowerShell/issues/954) ons feedback geven over het verbeteren van de ervaring bij globbing op Linux/Mac OS.

### <a name="net-framework-vs-net-core-framework"></a>.NET framework-tegenover .NET Core Framework

PowerShell op Linux/Mac OS gebruikt .NET Core een subset van de volledige .NET Framework voor Microsoft Windows. Dit is van belang omdat PowerShell voorziet in directe toegang tot de onderliggende framework-typen, methoden, enzovoort. Scripts die worden uitgevoerd op Windows kunnen daardoor niet uitvoeren op niet-Windows-platforms vanwege de verschillen in de frameworks. Zie voor meer informatie over .NET Core Framework <https://dotnetfoundation.org/net-core>

Met de komst van [Standard 2.0 van .NET](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/), .NET Core 2.0 verschijnt back veel van de traditionele typen en methoden aanwezig zijn op het volledige .NET Framework. Dit betekent dat PowerShell Core kunt laden veel traditionele Windows PowerShell-modules zonder aanpassing. Kunt u ons .NET Standard 2.0 gerelateerde werk [hier](https://github.com/PowerShell/PowerShell/projects/4).

### <a name="redirection-issues"></a>Omleiding van problemen

Invoer omleiding wordt niet ondersteund in PowerShell op elk platform.
[Probleem #1629](https://github.com/PowerShell/PowerShell/issues/1629)

Gebruik `Get-Content` schrijven van de inhoud van een bestand in de pipeline.

Omgeleide uitvoer bevat de Unicode-bytevolgordemarkering (BOM) als de standaard UTF-8-codering wordt gebruikt. De stuklijst leidt tot problemen bij het werken met hulpprogramma's die niet verwacht of wanneer u toevoegt aan een bestand. Gebruik `-Encoding Ascii` ASCII-tekst (die niet wordt Unicode, heeft geen een stuklijst) te schrijven. (Opmerking: Zie [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) ons om feedback te geven over het verbeteren van de ervaring voor de codering voor PowerShell Core voor alle platforms. We werken aan ondersteuning voor UTF-8 zonder een stuklijst en mogelijk de codering standaardinstellingen voor verschillende cmdlets in verschillende platforms te wijzigen.)

### <a name="job-control"></a>Taakbeheer

Er is geen taak-control-ondersteuning in PowerShell op Linux/Mac OS.
De `fg` en `bg` opdrachten zijn niet beschikbaar.

Voorlopig, kunt u [PowerShell taken](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_jobs) die werken voor alle platforms.

### <a name="remoting-support"></a>Ondersteuning voor externe toegang

Op dit moment ondersteunt PowerShell Core PowerShell voor externe toegang (PSRP) via WSMan met basisverificatie op Mac OS- en Linux, en met verificatie op basis van NTLM op Linux. (Op basis van Kerberos-verificatie wordt niet ondersteund.)

Het werk voor externe toegang op basis van WSMan wordt uitgevoerd de [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) opslagplaats.

PowerShell Core ondersteunt ook PowerShell voor externe toegang (PSRP) via SSH op alle platforms (Windows, Mac OS en Linux). Terwijl dit wordt momenteel niet ondersteund in productie, kunt u meer informatie over om in te stellen [hier](../core-powershell/ssh-remoting-in-powershell-core.md).

### <a name="just-enough-administration-jea-support"></a>Ondersteuning voor Just Enough-beheer (JEA)

De mogelijkheid beperkte administration (JEA) voor externe toegang om eindpunten te maken is momenteel niet beschikbaar in PowerShell op Linux/Mac OS. Deze functie is momenteel niet binnen het bereik van 6.0 en iets we post 6.0 worden beschouwd als het vereist belangrijke ontwerpwerk.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec`, en PowerShell

Omdat PowerShell wordt uitgevoerd voor de meeste opdrachten in het geheugen (zoals Python of Ruby), kunt u sudo niet rechtstreeks met PowerShell dient te worden gebruiken. (U kunt uiteraard uitvoeren `powershell` van sudo.) Indien nodig een PowerShell-cmdlet van PowerShell uitvoeren met sudo, bijvoorbeeld `sudo Set-Date 8/18/2016`, en u doet `sudo powershell Set-Date 8/18/2016`. Evenzo is niet mogelijk een ingebouwde PowerShell exec rechtstreeks. U moet in plaats daarvan doen `exec powershell item_to_exec`.

Dit probleem wordt momenteel bijgehouden als onderdeel van #3232.

### <a name="missing-cmdlets"></a>Ontbrekende Cmdlets

Een groot aantal opdrachten (cmdlets) normaal gesproken beschikbaar in PowerShell zijn niet beschikbaar op Linux/Mac OS. In veel gevallen Breng deze opdrachten geen zin op deze platforms (bijvoorbeeld Windows-specifieke functies, zoals het register). Andere opdrachten, zoals opdrachten voor service-beheer (Get/starten/stoppen-Service) aanwezig zijn, maar niet in werking. Toekomstige releases verhelpt deze problemen, de verbroken cmdlets is hersteld en het toevoegen van nieuwe gedurende een bepaalde periode.

### <a name="command-availability"></a>Beschikbaarheid van de opdracht

De volgende tabel bevat opdrachten die bekend is dat deze niet werken in PowerShell op Linux/Mac OS.

<table>
<th>Opdrachten</th><th>Operationele status</th><th>Opmerkingen</th>
<tr>
<td>Get-Service, nieuwe Service, herstarten-Service, Resume-Service, Service instellen, Start-Service, Service stoppen, onderbreken-Service
<td>Niet beschikbaar.
<td>Deze opdrachten wordt niet herkend. Dit moet worden opgelost in een toekomstige release.
</tr>
<tr>
<td>Get-Acl, Set-Acl
<td>Niet beschikbaar.
<td>Deze opdrachten wordt niet herkend. Dit moet worden opgelost in een toekomstige release.
</tr>
<tr>
<td>Get-AuthenticodeSignature, Set AuthenticodeSignature
<td>Niet beschikbaar.
<td>Deze opdrachten wordt niet herkend. Dit moet worden opgelost in een toekomstige release.
</tr>
<tr>
<td>Wacht-proces
<td>Beschikbaar, werkt niet goed. <td>Bijvoorbeeld `Start-Process gvim -PassThru | Wait-Process` werkt niet; deze moet worden gewacht op het proces is mislukt.
</tr>
<tr>
<td>Register-PSSessionConfiguration, Unregister-PSSessionConfiguration, Get-PSSessionConfiguration
<td>Beschikbaar, maar werkt niet.
<td>Schrijft een foutbericht met de mededeling dat de opdrachten niet werken. Deze moeten worden hersteld in een toekomstige release.
</tr>
<tr>
<td>Get-gebeurtenis, nieuwe gebeurtenis, registreren EngineEvent, Register-WmiEvent, Remove-gebeurtenis, Unregister-gebeurtenis
<td>Beschikbaar, maar er zijn geen bronnen van gebeurtenissen zijn beschikbaar.
<td>De PowerShell-opdrachten eventing aanwezig zijn, maar de meeste van de bronnen van gebeurtenissen met de opdrachten (zoals System.Timers.Timer) gebruikt, zijn niet beschikbaar op Linux maken van de opdrachten die in de release Alpha onbruikbaar.
</tr>
<tr>
<td>Set-ExecutionPolicy
<td>Beschikbaar, maar werkt niet.
<td>Retourneert een bericht niet ondersteund op dit platform. Uitvoeringsbeleid is een gebruikersgerichte 'veiligheid band' die helpt voorkomen dat de gebruiker dure fouten. Het is niet een beveiligingsgrens.
</tr>
<tr>
<td>Nieuwe PSSessionOption, nieuwe PSTransportOption
<td>Beschikbaar, maar New-PSSession werkt niet.
<td>Nieuw PSSessionOption en nieuw PSTransportOption worden momenteel niet geverifieerd werkt nu dat New-PSSession werkt.
</tr>
</table>
