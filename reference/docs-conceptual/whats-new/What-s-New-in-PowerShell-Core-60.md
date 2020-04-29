---
title: Wat is er nieuw in Power shell Core 6,0
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,0
ms.date: 08/06/2018
ms.openlocfilehash: 39bcb343c44c32d183c8bb90306a8f4a57397eb6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500478"
---
# <a name="whats-new-in-powershell-core-60"></a>Wat is er nieuw in Power shell Core 6,0

[Power shell Core 6,0][github] is een nieuwe editie van Power shell met meerdere platformen (Windows, MacOS en Linux), open source en gebouwd voor heterogene omgevingen en de hybride Cloud.

## <a name="moved-from-net-framework-to-net-core"></a>Verplaatst van .NET Framework naar .NET core

Power shell core maakt gebruik van [.net Core 2,0][] als runtime. Met .NET Core 2,0 kan Power shell Core op meerdere platformen (Windows, macOS en Linux) worden uitgevoerd. Power shell core geeft ook de API weer die wordt aangeboden door .NET Core 2,0 voor gebruik in Power shell-cmdlets en-scripts.

Windows Power Shell heeft de .NET Framework-runtime gebruikt voor het hosten van de Power shell-engine. Dit betekent dat Windows Power shell de API beschikbaar stelt die door .NET Framework wordt aangeboden.

De Api's die worden gedeeld tussen .NET core en .NET Framework worden gedefinieerd als onderdeel van [.NET Standard][].

Zie [achterwaartse compatibiliteit met Windows Power shell](#backwards-compatibility-with-windows-powershell)(Engelstalig) voor meer informatie over de wijze waarop dit van invloed is op module-en script compatibiliteit tussen Power shell core en Windows Power shell.

## <a name="support-for-macos-and-linux"></a>Ondersteuning voor macOS en Linux

Power shell biedt nu officieel ondersteuning voor macOS en Linux, waaronder:

- Windows 7, 8,1 en 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server Semi-Annual-kanaal][semi-annual]
- Ubuntu 14,04, 16,04 en 17,04
- Debian 8,7 + en 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42,2
- Fedora 25, 26
- macOS 10.12+

Onze community heeft ook pakketten bijgedragen voor de volgende platforms, maar ze worden niet officieel ondersteund:

- Arch Linux
- Kali Linux
- AppImage (werkt op meerdere Linux-platforms)

Er zijn ook experimentele (niet-ondersteunde) releases voor de volgende platforms:

- Windows op ARM32/ARM64
- Raspbian (stretch)

Er zijn een aantal wijzigingen aangebracht in Power shell Core 6,0, waardoor het beter werkt op niet-Windows-systemen. Sommige hiervan zijn belang rijke wijzigingen, die ook van invloed zijn op Windows. Andere zijn alleen aanwezig of van toepassing op niet-Windows-installaties van Power shell core.

- Er is ondersteuning toegevoegd voor de systeem eigen opdracht globbing op UNIX-platforms.
- De `more` functionaliteit houdt rekening met `$PAGER` de Linux en `less`wordt standaard ingesteld op. Dit betekent dat u nu Joker tekens kunt gebruiken met systeem eigen binaire bestanden/opdrachten ( `ls *.txt`bijvoorbeeld). (#3463)
- Afsluitende back slash wordt automatisch voorafgegaan tijdens het omgaan met systeem eigen opdracht argumenten. (#4965)
- De switch `-ExecutionPolicy` negeren bij het uitvoeren van Power shell op niet-Windows-platforms, omdat het ondertekenen van scripts momenteel niet wordt ondersteund. (#3481)
- Vaste ConsoleHost om te `NoEcho` voldoen aan UNIX-platforms. (#3801)
- Opgelost `Get-Help` voor ondersteuning van niet-hoofdletter gevoelige patroon overeenkomsten op UNIX-platforms. (#3852)
- `powershell`man-pagina toegevoegd aan pakket

### <a name="logging"></a>Logboekregistratie

Bij macOS gebruikt Power shell de systeem `os_log` eigen api's om zich aan te melden bij het [Unified logging-systeem][os_log]van Apple. In Linux maakt Power shell gebruik van [syslog][], een alomtegenwoordige-logboek oplossing.

### <a name="filesystem"></a>Bestandssysteem

Er zijn een aantal wijzigingen aangebracht in macOS en Linux ter ondersteuning van bestands namen die niet traditioneel worden ondersteund in Windows:

- Paden die aan cmdlets worden gegeven, zijn nu slash-neutraal (zowel/als \ werk als mappen scheidings teken)
- XDG basis directory-specificatie wordt nu gerespecteerd en standaard gebruikt:
  - Het pad naar het Linux/macOS-profiel bevindt zich op`~/.config/powershell/profile.ps1`
  - Het pad voor het opslaan van de geschiedenis bevindt zich op`~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Het pad naar de gebruikers module bevindt zich op`~/.local/share/powershell/Modules`
- Ondersteuning voor bestands-en mapnamen met de dubbele punt op UNIX. (#4959)
- Ondersteuning voor script namen of volledige paden met komma's. (#4136) (Bedankt [@TimCurwick](https://github.com/TimCurwick)!)
- Detecteren wanneer `-LiteralPath` wordt gebruikt om het uitbreiden van het Joker teken voor navigatie-cmdlets te onderdrukken. (#5038)
- Bijgewerkt `Get-ChildItem` om meer te weten te werken zoals `ls -R` de * nix `DIR /S` en de systeem eigen opdrachten van Windows. `Get-ChildItem`retourneert nu de symbolische koppelingen die zijn opgetreden tijdens een recursieve zoek opdracht en doorzoekt niet de mappen die de koppelingen doel hebben. (#3780)

### <a name="case-sensitivity"></a>Hoofdletter gevoeligheid

Linux en macOS zijn in het algemeen hoofdletter gevoelig terwijl Windows hoofdletter gevoelig is.
In het algemeen is Power shell niet hoofdletter gevoelig.

Zo zijn omgevings variabelen hoofdletter gevoelig in macOS en Linux, zodat de behuizing van de `PSModulePath` omgevings variabele is gestandaardiseerd. (#3255) `Import-Module` is hoofdletter gevoelig wanneer een bestandspad wordt gebruikt om de naam van de module te bepalen. (#5097)

## <a name="support-for-side-by-side-installations"></a>Ondersteuning voor side-by-side-installaties

Power shell Core is geïnstalleerd, geconfigureerd en wordt afzonderlijk uitgevoerd vanuit Windows Power shell.
Power shell Core heeft een ' draagbaar ' ZIP-pakket. Met behulp van het ZIP-pakket kunt u overal op schijf een wille keurig aantal versies installeren, met inbegrip van lokale toegang tot een toepassing die Power shell als afhankelijkheid gebruikt.
Met de side-by-side-installatie kunt u gemakkelijker nieuwe versies van Power shell testen en bestaande scripts na verloop van tijd migreren. Naast elkaar is achterwaartse compatibiliteit mogelijk, omdat scripts kunnen worden vastgemaakt aan specifieke versies die ze nodig hebben.

> [!NOTE]
> Het MSI-gebaseerde installatie programma in Windows voert standaard een installatie met update uit.

## <a name="renamed-powershellexe-to-pwshexe"></a>Naam van `powershell(.exe)` gewijzigd in `pwsh(.exe)`

De binaire naam voor de Power shell-kern is `powershell(.exe)` gewijzigd `pwsh(.exe)`van in. Deze wijziging biedt gebruikers een deterministische manier om Power shell Core op computers uit te voeren voor ondersteuning van Side-by-side Windows Power shell-en Power shell Core-installaties. `pwsh`is ook veel korter en eenvoudiger te typen.

Aanvullende wijzigingen in `pwsh(.exe)` van `powershell.exe`:

- De eerste positie parameter is gewijzigd van `-Command` in `-File`. Deze wijziging corrigeert het gebruik `#!` van (ook wel als een shebang) in Power shell-scripts die worden uitgevoerd vanuit niet-Power shell-shells op niet-Windows-platforms. Dit betekent ook dat u opdrachten kunt uitvoeren zoals `pwsh foo.ps1` of `pwsh fooScript` zonder op `-File`te geven. Voor deze wijziging moet u echter expliciet opgeven `-c` of `-Command` als u wilt proberen om opdrachten zoals `pwsh.exe -Command Get-Command`te gebruiken.
  (#4019)
- Power shell core accepteert `-i` de ( `-Interactive`of) switch om een interactieve shell aan te duiden.
  (#3558) Hierdoor kan Power shell worden gebruikt als een standaard shell op UNIX-platforms.
- De para `-importsystemmodules` `-psconsoleFile` meters `pwsh.exe`en van worden verwijderd. (#4995)
- Gewijzigde `pwsh -version` en ingebouwde Help voor `pwsh.exe` het uitlijnen met andere systeem eigen hulpprogram ma's. (#4958 & #4931) (Bedankt [@iSazonov](https://github.com/iSazonov))
- Ongeldige argument fout berichten voor `-File` en `-Command` en en afsluit codes die consistent zijn met Unix-standaarden (#4573)
- De `-WindowStyle` para meter is toegevoegd aan Windows. (#4573) Op deze manier worden updates op basis van pakket installaties op niet-Windows-platforms geïmplementeerd.

## <a name="backwards-compatibility-with-windows-powershell"></a>Achterwaartse compatibiliteit met Windows Power shell

Het doel van Power shell Core is om zo compatibel mogelijk te blijven met Windows Power shell.
Power shell core maakt gebruik van [.NET Standard][] 2,0 om binaire compatibiliteit met bestaande .net-assembly's te bieden. Veel Power shell-modules zijn afhankelijk van deze assembly's (vaak als dll-bestanden), zodat deze door .NET Standard kunnen blijven werken met .NET core. Power shell Core bevat ook een heuristiek voor het zoeken naar bekende mappen, zoals waar de globale assembly-cache zich doorgaans op schijf bevindt om .NET Framework DLL-afhankelijkheden te vinden.

Meer informatie over .NET Standard vindt u in de [.net-blog][], in deze [YouTube][] -video en via deze [Veelgestelde vragen][] over github.

Er zijn beste pogingen gedaan om ervoor te zorgen dat de Power shell-taal en ingebouwde modules (zoals `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`enzovoort) hetzelfde werken als in Windows Power shell. In veel gevallen hebben we met de Help van de Community nieuwe mogelijkheden en oplossingen voor fouten toegevoegd aan deze cmdlets. In sommige gevallen, vanwege een ontbrekende afhankelijkheid in onderliggende .NET-lagen, is de functionaliteit verwijderd of is deze niet beschikbaar.

De meeste modules die worden geleverd als onderdeel van Windows `DnsClient`(bijvoorbeeld `Hyper-V` `NetTCPIP` `Storage`,,, enzovoort) en andere micro soft-producten, waaronder Azure en Office, zijn nog niet *expliciet* naar .net core gestuurd. Het Power shell-team werkt met deze product groepen en teams om hun bestaande modules te valideren en te poorten naar Power shell core. Met .NET Standard en [CDXML][]lijken veel van deze traditionele Windows Power shell-modules in Power shell core te werken, maar ze zijn niet formeel gevalideerd en ze worden niet formeel ondersteund.

Door de [`WindowsPSModulePath`][windowspsmodulepath] module te installeren, kunt u Windows Power shell-modules gebruiken door de Windows `PSModulePath` Power shell aan uw `PSModulePath`Power shell core toe te voegen.

Installeer eerst de `WindowsPSModulePath` module vanaf de PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Na de installatie van deze module voert `Add-WindowsPSModulePath` u de cmdlet uit om de `PSModulePath` Windows Power shell toe te voegen aan Power shell core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-ondersteuning

Power shell core voegt ondersteuning toe voor docker-containers voor alle belang rijke platforms die we ondersteunen (inclusief meerdere Linux-distributies, Windows Server Core en nano server).

Bekijk de tags op [ `microsoft/powershell` de docker-hub][docker-hub]voor een volledige lijst. Zie [docker][] op github voor meer informatie over docker en Power shell core.

## <a name="ssh-based-powershell-remoting"></a>Externe toegang tot Power shell op basis van SSH

Het Power shell Remoting Protocol (PSRP) werkt nu met het SSH-protocol (Secure Shell) naast de traditionele op WinRM gebaseerde PSRP.

Dit betekent dat u cmdlets zoals `Enter-PSSession` en `New-PSSession` kunt gebruiken en verifiëren met SSH. Alles wat u moet doen, is Power shell registreren als subsysteem met een OpenSSH SSH-server, en u kunt uw bestaande op SSH gebaseerde authenticatie mechanismen (zoals wacht woorden of persoonlijke sleutels) gebruiken `PSSession` met de traditionele semantiek.

Zie voor meer informatie over het configureren en gebruiken van op SSH gebaseerde externe communicatie [Power shell voor externe toegang via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Standaard codering is UTF-8 zonder een stuk lijst, met uitzonde ring van New-ModuleManifest

In het verleden hebben Windows Power shell- `Get-Content`cmdlets `Set-Content` , zoals ASCII en UTF-16, gebruikt voor verschillende code ringen. Bij het combi neren van cmdlets worden er problemen met de variantie in de standaard waarden gegenereerd zonder dat er een code ring wordt opgegeven.

Niet-Windows-platforms gebruiken traditioneel UTF-8 zonder een byte order Mark (BOM) als de standaard codering voor tekst bestanden. Meer Windows-toepassingen en-hulpprogram ma's worden verwijderd van UTF-16 en naar een stuk lijst zonder UTF-8-code ring. Power shell core wijzigt de standaard codering zodat deze voldoet aan de bredere ecosystemen.

Dit betekent dat alle ingebouwde cmdlets die gebruikmaken van de `-Encoding` para meter, standaard `UTF8NoBOM` de waarde gebruiken. De volgende cmdlets worden beïnvloed door deze wijziging:

- Add-content
- Exporteren-Clixml
- Export-Csv
- Exporteren-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-file
- Selecteer teken reeks
- Bericht verzenden
- Set-Content

Deze cmdlets zijn ook bijgewerkt zodat de `-Encoding` para meter universele wordt geaccepteerd. `System.Text.Encoding`

De standaard waarde van `$OutputEncoding` is ook gewijzigd in UTF-8.

Als best practice moet u expliciet code ringen in scripts instellen met de `-Encoding` para meter om deterministisch gedrag op verschillende platforms te maken.

`New-ModuleManifest`de cmdlet heeft geen **Encoding** -para meter. De code ring van het module manifest bestand (. psd1) dat `New-ModuleManifest` is gemaakt met de cmdlet is afhankelijk van de omgeving: als Power shell core wordt uitgevoerd op Linux, wordt Encoding UTF-8 (geen stuk lijst). anders is de code ring UTF-16 (met stuk lijst). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Ondersteuning voor achtergronding van pijp lijnen met en`&`-teken (#3360)

Door `&` aan het einde van een pijp lijn te plaatsen, wordt de pijp lijn uitgevoerd als een Power shell-taak. Wanneer een pijp lijn wordt geachtergrondd, wordt een taak object geretourneerd. Zodra de pijp lijn als een taak wordt uitgevoerd, kunnen alle standaard `*-Job` -cmdlets worden gebruikt om de taak te beheren. Variabelen (het negeren van proces-specifieke variabelen) die in de pijp lijn worden gebruikt, worden automatisch naar `Copy-Item $foo $bar &` de taak gekopieerd zodat deze gewoon werkt. De taak wordt ook uitgevoerd in de huidige map in plaats van de basismap van de gebruiker. Zie [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)voor meer informatie over Power shell-taken.

## <a name="semantic-versioning"></a>Semantische versie beheer

- Compatibel `SemanticVersion` gemaakt met `SemVer 2.0`. (#5037) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- De standaard `ModuleVersion` waarde `New-ModuleManifest` is `0.0.1` gewijzigd in om uit te lijnen met SemVer. (#4842) (Bedankt [@LDSpits](https://github.com/LDSpits))
- Toegevoegd `semver` als een type Accelerator voor `System.Management.Automation.SemanticVersion`. (#4142) (Bedankt [@oising](https://github.com/oising)!)
- Ingeschakelde vergelijking tussen `SemanticVersion` een exemplaar en `Version` een exemplaar dat alleen is gebouwd `Major` met `Minor` en versie waarden.

## <a name="language-updates"></a>Taal updates

- Implementeer het parseren van Unicode-Escapes zodat gebruikers Unicode-tekens kunnen gebruiken als argumenten, teken reeksen of namen van variabelen. (#3958) (Bedankt [@rkeithhill](https://github.com/rkeithhill)!)
- Nieuw escape teken toegevoegd voor ESC:`` `e``
- Er is ondersteuning toegevoegd voor het converteren van enums naar String ( [@KirkMunro](https://github.com/KirkMunro)#4318) (bedankt)
- Vaste casting van een enkele element matrix naar een algemene verzameling. (#3170)
- De overbelasting van het teken `..` bereik is toegevoegd `'a'..'z'` aan de operator, dus retourneert tekens van ' a ' naar ' z '. (#5026) (Bedankt [@IISResetMe](https://github.com/IISResetMe)!)
- Vaste variabele toewijzing om alleen-lezen variabelen te overschrijven
- Lokale pushes van automatische variabelen naar ' DottedScopes ' verzenden als u script-cmdlets (#4709) wilt gebruiken
- Gebruik van de optie ' modus singleline, meerdere regels ' inschakelen in de operator Split (#4721 [@iSazonov](https://github.com/iSazonov))

## <a name="engine-updates"></a>Engine-updates

- `$PSVersionTable`heeft vier nieuwe eigenschappen:
  - `PSEdition`: Dit is ingesteld op `Core` in Power shell core `Desktop` en in Windows Power shell
  - `GitCommitId`: Dit is de Git-doorvoer-ID van de Git-vertakking of tag waarin Power shell is gebouwd.
    Op vrijgegeven builds is dit waarschijnlijk hetzelfde als `PSVersion`.
  - `OS`: Dit is een teken reeks voor de besturingssysteem versie die wordt geretourneerd door`[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Dit wordt geretourneerd door `[System.Environment]::OSVersion.Platform` op Windows, `Win32NT` `Unix` op macOS en `Unix` op Linux te worden ingesteld.
- De `BuildVersion` eigenschap is uit `$PSVersionTable`verwijderd. Deze eigenschap is sterk verbonden met de Windows-build-versie. In plaats daarvan raden we u aan `GitCommitId` gebruik te maken van om de exacte build-versie van Power shell Core op te halen. (#3877) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- Eigenschap `ClrVersion` verwijderen uit `$PSVersionTable`. Deze eigenschap is niet relevant voor .NET core en is alleen behouden in .NET core voor specifieke oudere doel einden die niet van toepassing zijn op Power shell.
- Er zijn drie nieuwe automatische variabelen toegevoegd om te bepalen of Power shell wordt uitgevoerd in `$IsWindows`een `$IsMacOs`bepaald besturings `$IsLinux`systeem:, en.
- Toevoegen `GitCommitId` aan banner van Power shell-kern. U hoeft nu niet te `$PSVersionTable` beginnen zodra u Power shell start om de versie op te halen. (#3916) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- Voeg een JSON-configuratie bestand `powershell.config.json` toe `$PSHome` met de naam in om bepaalde instellingen op te slaan die `ExecutionPolicy`vereist zijn voor de opstart tijd (bijvoorbeeld).
- Pijp lijn niet blok keren bij het uitvoeren van Windows EXE
- De inventarisatie van COM-verzamelingen is ingeschakeld. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet-updates

### <a name="new-cmdlets"></a>Nieuwe cmdLets

- Toevoegen `Get-Uptime` aan `Microsoft.PowerShell.Utility`.
- Opdracht `Remove-Alias` toevoegen. (#5143) (Bedankt [@PowershellNinja](https://github.com/PowershellNinja)!)
- Toevoegen `Remove-Service` aan beheer module. (#4858) (Bedankt [@joandrsn](https://github.com/joandrsn)!)

### <a name="web-cmdlets"></a>Web-cmdlets

- Ondersteuning voor certificaat verificatie voor web-cmdlets toevoegen. (#4646) (Bedankt [@markekraus](https://github.com/markekraus))
- Voeg ondersteuning toe voor inhouds headers voor web-cmdlets. (#4494 & #4640) (Bedankt [@markekraus](https://github.com/markekraus))
- Ondersteuning voor meerdere koppelings koppen toevoegen aan Web-cmdlets. (#5265) (Bedankt [@markekraus](https://github.com/markekraus)!)
- Koppelings header paginering in Web-cmdlets (#3828) ondersteunen
  - Voor `Invoke-WebRequest`, wanneer het antwoord een koppelings header bevat, maken we een RelationLink-eigenschap als een woorden lijst `rel` die de url's en kenmerken vertegenwoordigt en zorgt u ervoor dat de url's absoluut zijn, zodat de ontwikkelaar deze gemakkelijker kan gebruiken.
  - Voor `Invoke-RestMethod`, wanneer het antwoord een koppelings header bevat, wordt een `-FollowRelLink` switch beschikbaar voor het `next` `rel` automatisch volgen van koppelingen, totdat deze niet meer bestaan of wanneer `-MaximumFollowRelLink` de optionele parameter waarde wordt bereikt.
- Voeg `-CustomMethod` para meters toe aan Web-cmdlets voor het toestaan van niet-standaard methode termen. (#3142) (Bedankt @Lee303!)
- Voeg `SslProtocol` ondersteuning toe voor web-cmdlets. (#5329) (Bedankt [@markekraus](https://github.com/markekraus)!)
- Voeg meerdelige ondersteuning toe aan Web-cmdlets. (#4782) (Bedankt [@markekraus](https://github.com/markekraus))
- Voeg `-NoProxy` toe aan Web-cmdlets zodat deze de systeem-brede proxy instelling negeren. (#3447) (Bedankt [@TheFlyingCorpse](https://github.com/TheFlyingCorpse)!)
- Gebruikers agent van web-cmdlets rapporteert nu het OS-platform (#4937 [@LDSpits](https://github.com/LDSpits))
- Voeg `-SkipHeaderValidation` switch toe aan Web-cmdlets voor ondersteuning bij het toevoegen van headers zonder de header waarde te valideren. (#4085)
- Schakel Web-cmdlets in om het HTTPS-certificaat van de server, indien nodig, niet te valideren.
- Voeg verificatie parameters toe aan Web-cmdlets. (#5052) (Bedankt [@markekraus](https://github.com/markekraus))
  - Toevoegen `-Authentication` met drie opties: Basic, OAuth en Bearer.
  - Voeg `-Token` toe om het Bearer-token voor OAuth-en Bearer-opties te verkrijgen.
  - Voeg `-AllowUnencryptedAuthentication` de functie toe om de verificatie over te slaan voor een ander transport schema dan https.
- Voeg `-ResponseHeadersVariable` toe `Invoke-RestMethod` aan om het vastleggen van antwoord headers in te scha kelen.
  (#4888) (Bedankt [@markekraus](https://github.com/markekraus))
- Herstel Web-cmdlets om het HTTP-antwoord in de uitzonde ring op te halen wanneer de status code van de reactie niet is geslaagd. (#3201)
- Wijzig web- `UserAgent` cmdlets `WindowsPowerShell` van `PowerShell`naar. (#4914) (Bedankt [@markekraus](https://github.com/markekraus))
- Expliciete `ContentType` detectie toevoegen `Invoke-RestMethod` aan (#4692)
- Herstel Web-cmdlets `-SkipHeaderValidation` om te werken met niet-standaard headers van de gebruikers agent. (#4479 &
  #<a name="4512-thanks-markekraus"></a>4512) (bedankt [@markekraus](https://github.com/markekraus))

### <a name="json-cmdlets"></a>JSON-cmdlets

- Voeg `-AsHashtable` toe `ConvertFrom-Json` aan om in `Hashtable` plaats daarvan een te retour neren. (#5043) (Bedankt [@bergmeister](https://github.com/bergmeister)!)
- Gebruik prettier formatter met `ConvertTo-Json` uitvoer. (#2787) (Bedankt @kittholland!)
- Serialisatie-ondersteuning `Jobject` toevoegen `ConvertTo-Json`aan. (#5141)
- Oplossing `ConvertFrom-Json` voor het deserialiseren van een matrix met teken reeksen uit de pijp lijn die samen een volledige JSON-teken reeks bouwt. Dit corrigeert enkele gevallen waarin de JSON-parsering door een nieuwe regel wordt verbroken.
  (#3823)
- Verwijder de `AliasProperty "Count"` gedefinieerde voor `System.Array`. Hiermee verwijdert u de `Count` eigenschap overbodig voor `ConvertFrom-Json` bepaalde uitvoer. (#3231) (Bedankt [@PetSerAl](https://github.com/PetSerAl)!)

### <a name="csv-cmdlets"></a>CSV-cmdlets

- `Import-Csv`biedt nu ondersteuning voor de uitgebreide W3C-indeling van logboek bestand ( [@iSazonov](https://github.com/iSazonov)#2482) (hartelijk dank!)
- Ondersteuning `PSTypeName` voor `Import-Csv` en toe `ConvertFrom-Csv`te voegen. (#5389) (Bedankt [@markekraus](https://github.com/markekraus)!)
- Ondersteuning `Import-Csv` `CR`maken, `LF`en `CRLF` als lijn scheidings tekens. (#5363) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- Stel `-NoTypeInformation` de standaard waarde `Export-Csv` in `ConvertTo-Csv`op en. (#5164) (Bedankt [@markekraus](https://github.com/markekraus)!)

### <a name="service-cmdlets"></a>Service-cmdlets

- `UserName`Eigenschappen `Description`,, `DelayedAutoStart` `BinaryPathName`, en `StartupType` toevoegen aan de `ServiceController` objecten die worden geretourneerd `Get-Service`door. (#4907) (Bedankt [@joandrsn](https://github.com/joandrsn))
- Voeg functionaliteit toe om referenties in `Set-Service` te stellen op opdracht. (#4844) (Bedankt [@joandrsn](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Andere cmdlets

- Voeg een para meter `Get-ChildItem` toe `-FollowSymlink` die wordt aangeroepen om symlinks on demand door te lopen, met controles op koppelings lussen. (#4020)
- Update `Add-Type` voor ondersteuning `CSharpVersion7`. (#3933) (Bedankt [@iSazonov](https://github.com/iSazonov))
- Verwijder de `Microsoft.PowerShell.LocalAccounts` module vanwege het gebruik van niet-ondersteunde api's tot een betere oplossing is gevonden. (#4302)
- Verwijder de `*-Counter` cmdlets in `Microsoft.PowerShell.Diagnostics` vanwege het gebruik van niet-ondersteunde api's tot een betere oplossing is gevonden. (#4303)
- Voeg ondersteuning toe `Invoke-Item -Path <folder>`voor. (#4262)
- Voeg `-Extension` toe `-LeafBase` en Schakel `Split-Path` deze in zodat u paden kunt splitsen tussen de bestandsnaam extensie en de rest van de bestands naam. (#2721) (Bedankt [@powercode](https://github.com/powercode)!)
- Para `-Top` meters `-Bottom` en `Sort-Object` toevoegen voor bovenste/onderste N sorteren
- Maak een bovenliggend proces van het proces door de `CodeProperty "Parent"` toe te `System.Diagnostics.Process`voegen aan. (#2850) (Bedankt [@powercode](https://github.com/powercode)!)
- MB gebruiken in plaats van KB voor geheugen kolommen van`Get-Process`
- Schakel `-NoNewLine` optie toevoegen `Out-String`voor. (#5056) (Bedankt [@raghav710](https://github.com/raghav710))
- `Move-Item`de cmdlet `-Include`voldoet `-Exclude`aan de `-Filter` para meters, en. (#3878)
- Mogen `*` worden gebruikt in het registerpad voor `Remove-Item`. (#4866)
- Voeg `-Title` toe `Get-Credential` aan en verdeel de prompt ervaring op meerdere platforms.
- Voeg de `-TimeOut` para meter `Test-Connection`toe aan. (#2492)
- `Get-AuthenticodeSignature`cmdlets kunnen nu tijds tempel voor bestands handtekeningen ophalen. (#4061)
- Verwijder de niet- `-ShowWindow` ondersteunde switch `Get-Help`van. (#4903)
- Oplossing `Get-Content -Delimiter` voor geen scheidings teken in de geretourneerde matrix elementen (#3706) ( [@mklement0](https://github.com/mklement0)Bedankt)
- Toevoegen `Meta`, `Charset`en `Transitional` para meters `ConvertTo-HTML` aan (#4184) ( [@ergo3114](https://github.com/ergo3114)Bedankt)
- Het `WindowsUBR` `Get-ComputerInfo` resultaat `WindowsVersion` toevoegen en eigenschappen
- Para `-Group` meter toevoegen aan`Get-Verb`
- Voeg `ShouldProcess` ondersteuning toe `New-FileCatalog` aan `Test-FileCatalog` en ( `-WhatIf` oplossingen `-Confirm`en). (#3074) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- Switch `-WhatIf` toevoegen aan `Start-Process` cmdlet (#4735) (bedankt [@sarithsutha](https://github.com/sarithsutha))
- Er `ValidateNotNullOrEmpty` zijn te veel bestaande para meters toegevoegd.

## <a name="tab-completion"></a>Tabblad voltooiing

- Verbeterd het type afleiding in het tabblad voltooiing op basis van waarden van runtime variabelen. (#2744) (Bedankt [@powercode](https://github.com/powercode)!) Op die manier kan het tabblad worden aangevuld in situaties als:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Aanvulling van `Select-Object`het tabblad hashtabel `-Property` toevoegen voor. (#3625) (Bedankt [@powercode](https://github.com/powercode))
- Automatisch aanvullen van argumenten inschakelen `-ExcludeProperty` voor `-ExpandProperty` en `Select-Object`van.
  (#3443) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- Een bug in het tabblad volt ooien herstellen `native.exe --<tab>` om een systeem eigen volledige versie te kunnen aanroepen. (#3633) (Bedankt [@powercode](https://github.com/powercode)!)

## <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

We hebben een aantal belang rijke wijzigingen geïntroduceerd in Power shell Core 6,0.
Zie [belang rijke wijzigingen in Power shell Core 6,0][breaking-changes]voor meer informatie over deze details.

## <a name="debugging"></a>Foutopsporing

- Ondersteuning voor externe stap fout opsporing voor `Invoke-Command -ComputerName`. (#3015)
- Logboek registratie voor fout opsporing van Binder inschakelen in Power shell core

## <a name="filesystem-updates"></a>Bestandssysteem updates

- Het gebruik van de bestandssysteem provider vanaf een UNC-pad inschakelen. ($4998)
- `Split-Path`werkt nu met UNC-hoofd mappen
- `cd`zonder argumenten gedraagt zich nu als`cd ~`
- Vaste Power shell core om gebruik te maken van paden die meer dan 260 tekens lang zijn. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Problemen met oplossingen en prestatie verbeteringen

We hebben een *groot aantal* verbeteringen aangebracht in de prestaties van Power shell, inclusief de opstart tijd, verschillende ingebouwde cmdlets en interactie met systeem eigen binaire bestanden.

Daarnaast hebben we een aantal bugs in Power shell core opgelost. Bekijk onze [wijzigingen logboek][] op github voor een volledige lijst met oplossingen en wijzigingen.

## <a name="telemetry"></a>Telemetrie

- Power shell Core 6,0 heeft telemetrie aan de console-host toegevoegd om twee waarden te rapporteren (#3620):
  - het OS-platform`$PSVersionTable.OSDescription`()
  - de exacte versie van Power shell`$PSVersionTable.GitCommitId`()

Als u `POWERSHELL_TELEMETRY_OPTOUT` deze telemetrie wilt afmelden, maakt u een omgevings variabele met een van de volgende waarden: `true`, `1` of `yes`. Het maken van de variabele omzeilt alle telemetrie, zelfs vóór de eerste uitvoering van Power shell. We zijn ook van plan om deze telemetriegegevens en de inzichten die we beschikken van de telemetrie in het [dash board][community-dashboard]van de community beschikbaar te stellen. Meer informatie over hoe we deze gegevens in dit [blog bericht][telemetry-blog]gebruiken, vindt u hier.

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[wijzigingen logboek]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://devblogs.microsoft.com/powershell/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[Veelgestelde vragen]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: /previous-versions/windows/desktop/wmi_v2/getting-started-with-cdxml
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
