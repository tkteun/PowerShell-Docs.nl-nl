---
title: Wat is er nieuw in Power shell Core 6,0
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,0
ms.date: 08/06/2018
ms.openlocfilehash: d1bc1ef2676da60062b8bdd57042331f0f245bec
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995493"
---
# <a name="whats-new-in-powershell-core-60"></a>Wat is er nieuw in Power shell Core 6,0

[Power shell Core 6,0][github] is een nieuwe editie van Power shell met meerdere platformen (Windows, MacOS en Linux), open source en gebouwd voor heterogene omgevingen en de hybride Cloud.

## <a name="moved-from-net-framework-to-net-core"></a>Verplaatst van .NET Framework naar .NET core

Power shell core maakt gebruik van [.NET Core 2.0][] als runtime. Met .NET Core 2,0 kan Power shell Core op meerdere platformen (Windows, macOS en Linux) worden uitgevoerd. Power shell core geeft ook de API weer die wordt aangeboden door .NET Core 2,0 voor gebruik in Power shell-cmdlets en-scripts.

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
- De functionaliteit van `more` respecteert de Linux-`$PAGER` en de standaard waarden voor `less`. Dit betekent dat u nu Joker tekens kunt gebruiken met systeem eigen binaire bestanden/opdrachten (bijvoorbeeld `ls *.txt`). (#3463)
- Afsluitende back slash wordt automatisch voorafgegaan tijdens het omgaan met systeem eigen opdracht argumenten. (#4965)
- De `-ExecutionPolicy` switch negeren bij het uitvoeren van Power shell op niet-Windows-platforms, omdat het ondertekenen van scripts momenteel niet wordt ondersteund. (#3481)
- Vaste ConsoleHost om te voldoen aan de `NoEcho` op UNIX-platforms. (#3801)
- Vaste `Get-Help` voor ondersteuning van niet-hoofdletter gevoelige patroon matching op UNIX-platforms. (#3852)
- `powershell` man-pagina die is toegevoegd aan het pakket

### <a name="logging"></a>Logboekregistratie

Bij macOS gebruikt Power shell de systeem eigen `os_log`-Api's om zich aan te melden bij het [Unified logging-systeem][os_log]van Apple. In Linux maakt Power shell gebruik van [syslog][], een alomtegenwoordige-logboek oplossing.

### <a name="filesystem"></a>Bestandssysteem

Er zijn een aantal wijzigingen aangebracht in macOS en Linux ter ondersteuning van bestands namen die niet traditioneel worden ondersteund in Windows:

- Paden die aan cmdlets worden gegeven, zijn nu slash-neutraal (zowel/als \ werk als mappen scheidings teken)
- XDG basis directory-specificatie wordt nu gerespecteerd en standaard gebruikt:
  - Het pad naar het Linux/macOS-profiel bevindt zich op `~/.config/powershell/profile.ps1`
  - Het pad voor het opslaan van de geschiedenis bevindt zich op `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Het pad naar de gebruikers module bevindt zich op `~/.local/share/powershell/Modules`
- Ondersteuning voor bestands-en mapnamen met de dubbele punt op UNIX. (#4959)
- Ondersteuning voor script namen of volledige paden met komma's. (#4136) (Bedankt voor [@TimCurwick](https://github.com/TimCurwick)!)
- Detecteren wanneer `-LiteralPath` wordt gebruikt om het uitbreiden van het Joker teken voor navigatie-cmdlets te onderdrukken. (#5038)
- `Get-ChildItem` bijgewerkt om meer te doen, zoals de * nix `ls -R` en de Windows `DIR /S` systeem eigen opdrachten. `Get-ChildItem` retourneert nu de symbolische koppelingen die zijn opgetreden tijdens een recursieve zoek opdracht en doorzoekt niet de mappen die de koppelingen doel hebben. (#3780)

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

De binaire naam voor Power shell Core is gewijzigd van `powershell(.exe)` naar `pwsh(.exe)`. Deze wijziging biedt gebruikers een deterministische manier om Power shell Core op computers uit te voeren voor ondersteuning van Side-by-side Windows Power shell-en Power shell Core-installaties. `pwsh` is ook veel korter en eenvoudiger te typen.

Aanvullende wijzigingen in `pwsh(.exe)` van `powershell.exe`:

- De eerste positie parameter is gewijzigd van `-Command` naar `-File`. Deze wijziging corrigeert het gebruik van `#!` (ook wel als shebang) in Power shell-scripts die worden uitgevoerd vanuit niet-Power shell-shells op niet-Windows-platforms. Dit betekent ook dat u opdrachten als `pwsh foo.ps1` of `pwsh fooScript` kunt uitvoeren zonder `-File`op te geven. Deze wijziging vereist echter dat u `-c` of `-Command` expliciet opgeeft bij het uitvoeren van opdrachten als `pwsh.exe -Command Get-Command`.
  (#4019)
- Power shell core accepteert de `-i` (of `-Interactive`) om een interactieve shell aan te duiden.
  (#3558) Hierdoor kan Power shell worden gebruikt als een standaard shell op UNIX-platforms.
- De para meters `-importsystemmodules` en `-psconsoleFile` zijn verwijderd uit `pwsh.exe`. (#4995)
- `pwsh -version` en ingebouwde Help voor `pwsh.exe` is gewijzigd om te worden uitgelijnd met andere systeem eigen hulpprogram ma's. (#4958 & #4931) (Bedankt [@iSazonov](https://github.com/iSazonov))
- Ongeldige argument fout berichten voor `-File` en `-Command` en afsluit codes die consistent zijn met UNIX-standaarden (#4573)
- `-WindowStyle` para meter toegevoegd aan Windows. (#4573) Op deze manier worden updates op basis van pakket installaties op niet-Windows-platforms geïmplementeerd.

## <a name="backwards-compatibility-with-windows-powershell"></a>Achterwaartse compatibiliteit met Windows Power shell

Het doel van Power shell Core is om zo compatibel mogelijk te blijven met Windows Power shell.
Power shell core maakt gebruik van [.NET Standard][] 2,0 om binaire compatibiliteit met bestaande .net-assembly's te bieden. Veel Power shell-modules zijn afhankelijk van deze assembly's (vaak als dll-bestanden), zodat deze door .NET Standard kunnen blijven werken met .NET core. Power shell Core bevat ook een heuristiek voor het zoeken naar bekende mappen, zoals waar de globale assembly-cache zich doorgaans op schijf bevindt om .NET Framework DLL-afhankelijkheden te vinden.

Meer informatie over .NET Standard vindt u in de [.NET Blog][], in deze [YouTube][] -video en via deze [Veelgestelde vragen][] over github.

Er zijn beste inspanningen gedaan om ervoor te zorgen dat de Power shell-taal en ingebouwde modules (zoals `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`enzovoort) hetzelfde werken als in Windows Power shell. In veel gevallen hebben we met de Help van de Community nieuwe mogelijkheden en oplossingen voor fouten toegevoegd aan deze cmdlets. In sommige gevallen, vanwege een ontbrekende afhankelijkheid in onderliggende .NET-lagen, is de functionaliteit verwijderd of is deze niet beschikbaar.

De meeste modules die worden geleverd als onderdeel van Windows (bijvoorbeeld `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`enzovoort) en andere micro soft-producten, waaronder Azure en Office, zijn nog niet *expliciet* naar .net core gestuurd. Het Power shell-team werkt met deze product groepen en teams om hun bestaande modules te valideren en te poorten naar Power shell core. Met .NET Standard en [CDXML][]lijken veel van deze traditionele Windows Power shell-modules in Power shell core te werken, maar ze zijn niet formeel gevalideerd en ze worden niet formeel ondersteund.

Door de [`WindowsPSModulePath`][windowspsmodulepath] -module te installeren, kunt u Windows Power shell-modules gebruiken door de Windows Power shell-`PSModulePath` toe te voegen aan uw Power shell Core-`PSModulePath`.

Installeer eerst de module `WindowsPSModulePath` vanuit de PowerShell Gallery:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

Na de installatie van deze module voert u de `Add-WindowsPSModulePath`-cmdlet uit om de Windows Power shell-`PSModulePath` toe te voegen aan Power shell core:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-ondersteuning

Power shell core voegt ondersteuning toe voor docker-containers voor alle belang rijke platforms die we ondersteunen (inclusief meerdere Linux-distributies, Windows Server Core en nano server).

Bekijk de labels op [`microsoft/powershell` op docker hub][docker-hub]voor een volledige lijst. Zie [docker][] op github voor meer informatie over docker en Power shell core.

## <a name="ssh-based-powershell-remoting"></a>Externe toegang tot Power shell op basis van SSH

Het Power shell Remoting Protocol (PSRP) werkt nu met het SSH-protocol (Secure Shell) naast de traditionele op WinRM gebaseerde PSRP.

Dit betekent dat u cmdlets zoals `Enter-PSSession` en `New-PSSession` kunt gebruiken en verifiëren met behulp van SSH. Alles wat u moet doen, is Power shell registreren als subsysteem met een op OpenSSH gebaseerde SSH-server en u kunt uw bestaande op SSH gebaseerde authenticatie mechanismen (zoals wacht woorden of persoonlijke sleutels) gebruiken met de traditionele `PSSession` semantiek.

Zie voor meer informatie over het configureren en gebruiken van op SSH gebaseerde externe communicatie [Power shell voor externe toegang via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>Standaard codering is UTF-8 zonder een stuk lijst, met uitzonde ring van New-ModuleManifest

In het verleden hebben Windows Power shell-cmdlets, zoals `Get-Content`, `Set-Content` verschillende code ringen gebruikt, zoals ASCII en UTF-16. Bij het combi neren van cmdlets worden er problemen met de variantie in de standaard waarden gegenereerd zonder dat er een code ring wordt opgegeven.

Niet-Windows-platforms gebruiken traditioneel UTF-8 zonder een byte order Mark (BOM) als de standaard codering voor tekst bestanden. Meer Windows-toepassingen en-hulpprogram ma's worden verwijderd van UTF-16 en naar een stuk lijst zonder UTF-8-code ring. Power shell core wijzigt de standaard codering zodat deze voldoet aan de bredere ecosystemen.

Dit betekent dat alle ingebouwde cmdlets die gebruikmaken van de para meter `-Encoding` standaard de `UTF8NoBOM` waarde gebruiken. De volgende cmdlets worden beïnvloed door deze wijziging:

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

Deze cmdlets zijn ook bijgewerkt zodat de para meter `-Encoding` universele `System.Text.Encoding`accepteert.

De standaard waarde van `$OutputEncoding` is ook gewijzigd in UTF-8.

Als best practice moet u de para meters voor het maken van code ringen in scripts expliciet instellen met behulp van de `-Encoding` parameter.

`New-ModuleManifest`-cmdlet heeft geen **Encoding** -para meter. De code ring van het module manifest bestand (. psd1) dat is gemaakt met `New-ModuleManifest` cmdlet is afhankelijk van de omgeving: als de Power shell-kern op Linux wordt uitgevoerd, wordt de code ring UTF-8 (geen stuk lijst). anders is de code ring UTF-16 (met stuk lijst). (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Ondersteuning voor achtergronding van pijp lijnen met en-teken (`&`) (#3360)

Als u `&` aan het einde van een pijp lijn plaatst, wordt de pijp lijn uitgevoerd als een Power shell-taak. Wanneer een pijp lijn wordt geachtergrondd, wordt een taak object geretourneerd. Zodra de pijp lijn als een taak wordt uitgevoerd, kunnen alle standaard `*-Job`-cmdlets worden gebruikt om de taak te beheren. Variabelen (proces-specifieke variabelen worden genegeerd) die in de pijp lijn worden gebruikt, worden automatisch naar de taak gekopieerd, zodat `Copy-Item $foo $bar &` gewoon werkt. De taak wordt ook uitgevoerd in de huidige map in plaats van de basismap van de gebruiker. Zie [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)voor meer informatie over Power shell-taken.

## <a name="semantic-versioning"></a>Semantische versie beheer

- `SemanticVersion` compatibel zijn gemaakt met `SemVer 2.0`. (#5037) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- De standaard `ModuleVersion` in `New-ModuleManifest` is gewijzigd in `0.0.1` om te worden uitgelijnd met SemVer. (#4842) (Bedankt [@LDSpits](https://github.com/LDSpits))
- `semver` toegevoegd als type Accelerator voor `System.Management.Automation.SemanticVersion`. (#4142) (Bedankt voor [@oising](https://github.com/oising)!)
- Ingeschakelde vergelijking tussen een `SemanticVersion` exemplaar en een `Version`-exemplaar dat alleen is gebouwd met `Major` en `Minor` versie waarden.

## <a name="language-updates"></a>Taal updates

- Implementeer het parseren van Unicode-Escapes zodat gebruikers Unicode-tekens kunnen gebruiken als argumenten, teken reeksen of namen van variabelen. (#3958) (Bedankt voor [@rkeithhill](https://github.com/rkeithhill)!)
- Nieuw escape teken toegevoegd voor ESC: `` `e``
- Er is ondersteuning toegevoegd voor het converteren van enums naar String (#4318) (bedankt [@KirkMunro](https://github.com/KirkMunro))
- Vaste casting van een enkele element matrix naar een algemene verzameling. (#3170)
- De overbelasting van het teken bereik is toegevoegd aan de operator `..`, dus `'a'..'z'` retourneert tekens van ' a ' naar ' z '. (#5026) (Bedankt [@IISResetMe](https://github.com/IISResetMe)!)
- Vaste variabele toewijzing om alleen-lezen variabelen te overschrijven
- Lokale pushes van automatische variabelen naar ' DottedScopes ' verzenden als u script-cmdlets (#4709) wilt gebruiken
- Gebruik van de optie ' modus singleline, meerdere regels ' inschakelen in de operator Split (#4721) (bedankt [@iSazonov](https://github.com/iSazonov))

## <a name="engine-updates"></a>Engine-updates

- `$PSVersionTable` heeft vier nieuwe eigenschappen:
  - `PSEdition`: dit is ingesteld op `Core` op Power shell core en `Desktop` in Windows Power shell
  - `GitCommitId`: dit is de Git-doorvoer-ID van de Git-vertakking of tag waarin Power shell is gebouwd.
    Op vrijgegeven builds is dit waarschijnlijk hetzelfde als `PSVersion`.
  - `OS`: dit is een teken reeks voor de besturingssysteem versie die wordt geretourneerd door `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: dit wordt geretourneerd door `[System.Environment]::OSVersion.Platform` deze is ingesteld op `Win32NT` in Windows, `Unix` in macOS en `Unix` op Linux.
- De eigenschap `BuildVersion` van `$PSVersionTable`is verwijderd. Deze eigenschap is sterk verbonden met de Windows-build-versie. In plaats daarvan raden we u aan `GitCommitId` te gebruiken om de exacte build-versie van Power shell Core op te halen. (#3877) (Bedankt voor [@iSazonov](https://github.com/iSazonov)!)
- Verwijder de eigenschap `ClrVersion` van `$PSVersionTable`. Deze eigenschap is niet relevant voor .NET core en is alleen behouden in .NET core voor specifieke oudere doel einden die niet van toepassing zijn op Power shell.
- Er zijn drie nieuwe automatische variabelen toegevoegd om te bepalen of Power shell wordt uitgevoerd in een bepaald besturings systeem: `$IsWindows`, `$IsMacOs`en `$IsLinux`.
- `GitCommitId` toevoegen aan banner van Power shell-kern. U hoeft de `$PSVersionTable` nu niet uit te voeren zodra u Power shell start om de versie op te halen. (#3916) (Bedankt voor [@iSazonov](https://github.com/iSazonov)!)
- Voeg een JSON-configuratie bestand met de naam `powershell.config.json` in `$PSHome` toe om sommige instellingen op te slaan die vereist zijn voor de opstart tijd (bijvoorbeeld `ExecutionPolicy`).
- Pijp lijn niet blok keren bij het uitvoeren van Windows EXE
- De inventarisatie van COM-verzamelingen is ingeschakeld. (#4553)

## <a name="cmdlet-updates"></a>Cmdlet-updates

### <a name="new-cmdlets"></a>Nieuwe cmdLets

- Voeg `Get-Uptime` toe aan `Microsoft.PowerShell.Utility`.
- `Remove-Alias` opdracht toevoegen. (#5143) (Bedankt [@PowershellNinja](https://github.com/PowershellNinja)!)
- Voeg `Remove-Service` toe aan de beheer module. (#4858) (Bedankt [@joandrsn](https://github.com/joandrsn)!)

### <a name="web-cmdlets"></a>Web-cmdlets

- Ondersteuning voor certificaat verificatie voor web-cmdlets toevoegen. (#4646) (Bedankt [@markekraus](https://github.com/markekraus))
- Voeg ondersteuning toe voor inhouds headers voor web-cmdlets. (#4494 & #4640) (Bedankt [@markekraus](https://github.com/markekraus))
- Ondersteuning voor meerdere koppelings koppen toevoegen aan Web-cmdlets. (#5265) (Bedankt [@markekraus](https://github.com/markekraus)!)
- Koppelings header paginering in Web-cmdlets (#3828) ondersteunen
  - Voor `Invoke-WebRequest`, wanneer het antwoord een koppelings header bevat, maken we een RelationLink-eigenschap als een woorden lijst die de Url's en `rel` kenmerken vertegenwoordigt, en zorgt u ervoor dat de Url's absoluut zijn zodat de ontwikkelaar deze gemakkelijker kan gebruiken.
  - Voor `Invoke-RestMethod`, wanneer het antwoord een koppelings header bevat, wordt er een `-FollowRelLink` schakelaar weer gegeven waarmee `next` `rel` koppelingen automatisch worden gevolgd totdat deze niet meer bestaan of wanneer de optionele waarde voor `-MaximumFollowRelLink` para meter is bereikt.
- Voeg `-CustomMethod`-para meter toe aan Web-cmdlets voor het toestaan van niet-standaard methode werk woorden. (#3142) (Bedankt voor [@Lee303](https://github.com/Lee303)!)
- Voeg `SslProtocol` ondersteuning toe aan Web-cmdlets. (#5329) (Bedankt [@markekraus](https://github.com/markekraus)!)
- Voeg meerdelige ondersteuning toe aan Web-cmdlets. (#4782) (Bedankt [@markekraus](https://github.com/markekraus))
- Voeg `-NoProxy` toe aan Web-cmdlets zodat ze de systeem-brede proxy instelling negeren. (#3447) (Bedankt voor [@TheFlyingCorpse](https://github.com/TheFlyingCorpse)!)
- Gebruikers agent van web-cmdlets rapporteert nu het OS-platform (#4937) (bedankt [@LDSpits](https://github.com/LDSpits))
- Voeg `-SkipHeaderValidation` switch toe aan Web-cmdlets om het toevoegen van headers te ondersteunen zonder de header waarde te valideren. (#4085)
- Schakel Web-cmdlets in om het HTTPS-certificaat van de server, indien nodig, niet te valideren.
- Voeg verificatie parameters toe aan Web-cmdlets. (#5052) (Bedankt [@markekraus](https://github.com/markekraus))
  - Voeg `-Authentication` toe die drie opties biedt: Basic, OAuth en Bearer.
  - Voeg `-Token` toe om het Bearer-token voor OAuth-en Bearer-opties te verkrijgen.
  - Voeg `-AllowUnencryptedAuthentication` toe voor het overs laan van verificatie voor andere transport schema's dan HTTPS.
- Voeg `-ResponseHeadersVariable` toe aan `Invoke-RestMethod` om het vastleggen van antwoord headers in te scha kelen.
  (#4888) (Bedankt [@markekraus](https://github.com/markekraus))
- Herstel Web-cmdlets om het HTTP-antwoord in de uitzonde ring op te halen wanneer de status code van de reactie niet is geslaagd. (#3201)
- Web-cmdlets `UserAgent` wijzigen van `WindowsPowerShell` in `PowerShell`. (#4914) (Bedankt [@markekraus](https://github.com/markekraus))
- Expliciete detectie van `ContentType` toevoegen aan `Invoke-RestMethod` (#4692)
- Herstel Web-cmdlets `-SkipHeaderValidation` om met niet-standaard headers voor de gebruikers agent te werken. (#4479 &
  #<a name="4512-thanks-markekraushttpsgithubcommarkekraus"></a>4512) (bedankt [@markekraus](https://github.com/markekraus))

### <a name="json-cmdlets"></a>JSON-cmdlets

- Voeg `-AsHashtable` toe aan `ConvertFrom-Json` om in plaats daarvan een `Hashtable` te retour neren. (#5043) (Bedankt [@bergmeister](https://github.com/bergmeister)!)
- Gebruik prettier formatter met `ConvertTo-Json` uitvoer. (#2787) (Bedankt voor @kittholland!)
- Voeg `Jobject` serialisatie-ondersteuning toe aan `ConvertTo-Json`. (#5141)
- Herstel `ConvertFrom-Json` om een matrix met teken reeksen uit de pijp lijn te deserialiseren die samen een volledige JSON-teken reeks bouwt. Dit corrigeert enkele gevallen waarin de JSON-parsering door een nieuwe regel wordt verbroken.
  (#3823)
- Verwijder de `AliasProperty "Count"` die is gedefinieerd voor `System.Array`. Hiermee verwijdert u de eigenschap van het externe `Count` van sommige `ConvertFrom-Json` uitvoer. (#3231) (Bedankt voor [@PetSerAl](https://github.com/PetSerAl)!)

### <a name="csv-cmdlets"></a>CSV-cmdlets

- `Import-Csv` ondersteunt nu de uitgebreide W3C-indeling van logboek bestand (#2482) (bedankt [@iSazonov](https://github.com/iSazonov)!)
- Voeg `PSTypeName` ondersteuning toe voor `Import-Csv` en `ConvertFrom-Csv`. (#5389) (Bedankt [@markekraus](https://github.com/markekraus)!)
- Zorg `Import-Csv` ondersteuning `CR`, `LF`en `CRLF` als regel scheidings tekens. (#5363) (Bedankt [@iSazonov](https://github.com/iSazonov)!)
- Maak `-NoTypeInformation` de standaard waarde op `Export-Csv` en `ConvertTo-Csv`. (#5164) (Bedankt [@markekraus](https://github.com/markekraus)!)

### <a name="service-cmdlets"></a>Service-cmdlets

- Eigenschappen `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`en `StartupType` toevoegen aan de `ServiceController` objecten die door `Get-Service`worden geretourneerd. (#4907) (Bedankt [@joandrsn](https://github.com/joandrsn))
- Voeg functionaliteit toe om referenties in te stellen voor `Set-Service` opdracht. (#4844) (Bedankt [@joandrsn](https://github.com/joandrsn))

### <a name="other-cmdlets"></a>Andere cmdlets

- Voeg een para meter toe aan `Get-ChildItem` met de naam `-FollowSymlink` die symlinks op aanvraag doorloopt, met controles voor koppelings lussen. (#4020)
- Update `Add-Type` om `CSharpVersion7`te ondersteunen. (#3933) (Bedankt voor [@iSazonov](https://github.com/iSazonov))
- Verwijder de module `Microsoft.PowerShell.LocalAccounts` als gevolg van het gebruik van niet-ondersteunde Api's tot een betere oplossing is gevonden. (#4302)
- Verwijder de `*-Counter`-cmdlets in `Microsoft.PowerShell.Diagnostics` vanwege het gebruik van niet-ondersteunde Api's totdat er een betere oplossing wordt gevonden. (#4303)
- Voeg ondersteuning toe voor `Invoke-Item -Path <folder>`. (#4262)
- Voeg `-Extension`-en `-LeafBase`-switches toe aan `Split-Path` zodat u paden kunt splitsen tussen de bestandsnaam extensie en de rest van de bestands naam. (#2721) (Bedankt voor [@powercode](https://github.com/powercode)!)
- Para meters `-Top` en `-Bottom` toevoegen aan `Sort-Object` voor de bovenste/onderste x-Sorteer bewerking
- Maak een bovenliggend proces van het proces door de `CodeProperty "Parent"` toe te voegen aan `System.Diagnostics.Process`. (#2850) (Bedankt voor [@powercode](https://github.com/powercode)!)
- MB gebruiken in plaats van KB voor geheugen kolommen van `Get-Process`
- `-NoNewLine` switch toevoegen voor `Out-String`. (#5056) (Bedankt [@raghav710](https://github.com/raghav710))
- `Move-Item`-cmdlet voldoet aan de para meters `-Include`, `-Exclude`en `-Filter`. (#3878)
- Toestaan dat `*` worden gebruikt in het registerpad voor `Remove-Item`. (#4866)
- Voeg `-Title` toe aan `Get-Credential` en verdeel de prompt ervaring op verschillende platforms.
- Voeg de para meter `-TimeOut` toe aan `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature`-cmdlets kunnen nu tijds tempel voor bestands handtekeningen ophalen. (#4061)
- Verwijder de niet-ondersteunde `-ShowWindow` switch van `Get-Help`. (#4903)
- Corrigeer `Get-Content -Delimiter` zonder het scheidings teken in de geretourneerde matrix elementen (#3706) (bedankt [@mklement0](https://github.com/mklement0)) te gebruiken
- `Meta`-, `Charset`-en `Transitional`-para meters toevoegen aan `ConvertTo-HTML` (#4184) (bedankt [@ergo3114](https://github.com/ergo3114))
- `WindowsUBR`-en `WindowsVersion` eigenschappen toevoegen aan `Get-ComputerInfo` resultaat
- `-Group` para meter toevoegen aan `Get-Verb`
- Voeg `ShouldProcess` ondersteuning toe aan `New-FileCatalog` en `Test-FileCatalog` (oplossingen `-WhatIf` en `-Confirm`). (#3074) (Bedankt voor [@iSazonov](https://github.com/iSazonov)!)
- `-WhatIf` switch toevoegen aan `Start-Process`-cmdlet (#4735) (bedankt [@sarithsutha](https://github.com/sarithsutha))
- Voeg `ValidateNotNullOrEmpty` te veel bestaande para meters toe.

## <a name="tab-completion"></a>Tabblad voltooiing

- Verbeterd het type afleiding in het tabblad voltooiing op basis van waarden van runtime variabelen. (#2744) (Bedankt voor [@powercode](https://github.com/powercode)!) Op die manier kan het tabblad worden aangevuld in situaties als:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Aanvulling op het tabblad hashtabel toevoegen voor `-Property` van `Select-Object`. (#3625) (Bedankt voor [@powercode](https://github.com/powercode))
- Automatisch aanvullen van argumenten inschakelen voor `-ExcludeProperty` en `-ExpandProperty` van `Select-Object`.
  (#3443) (Bedankt voor [@iSazonov](https://github.com/iSazonov)!)
- Een bug in tab volt ooien om de systeem eigen volledige versie van `native.exe --<tab>` aan te roepen. (#3633) (Bedankt voor [@powercode](https://github.com/powercode)!)

## <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

We hebben een aantal belang rijke wijzigingen geïntroduceerd in Power shell Core 6,0.
Zie [belang rijke wijzigingen in Power shell Core 6,0][breaking-changes]voor meer informatie over deze details.

## <a name="debugging"></a>Foutopsporing

- Ondersteuning voor externe stap fout opsporing voor `Invoke-Command -ComputerName`. (#3015)
- Logboek registratie voor fout opsporing van Binder inschakelen in Power shell core

## <a name="filesystem-updates"></a>Bestandssysteem updates

- Het gebruik van de bestandssysteem provider vanaf een UNC-pad inschakelen. ($4998)
- `Split-Path` werkt nu met UNC-hoofd mappen
- `cd` zonder argumenten gedraagt zich nu als `cd ~`
- Vaste Power shell core om gebruik te maken van paden die meer dan 260 tekens lang zijn. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Problemen met oplossingen en prestatie verbeteringen

We hebben een *groot aantal* verbeteringen aangebracht in de prestaties van Power shell, inclusief de opstart tijd, verschillende ingebouwde cmdlets en interactie met systeem eigen binaire bestanden.

Daarnaast hebben we een aantal bugs in Power shell core opgelost. Bekijk onze [wijzigingen logboek][] op github voor een volledige lijst met oplossingen en wijzigingen.

## <a name="telemetry"></a>Telemetrie

- Power shell Core 6,0 heeft telemetrie aan de console-host toegevoegd om twee waarden te rapporteren (#3620):
  - het OS-platform (`$PSVersionTable.OSDescription`)
  - de exacte versie van Power shell (`$PSVersionTable.GitCommitId`)

Als u deze telemetrie wilt afmelden, maakt u `POWERSHELL_TELEMETRY_OPTOUT` omgevings variabele met een van de volgende waarden: `true`, `1` of `yes`. Het maken van de variabele omzeilt alle telemetrie, zelfs vóór de eerste uitvoering van Power shell. We zijn ook van plan om deze telemetriegegevens en de inzichten die we beschikken van de telemetrie in het [dash board][community-dashboard]van de community beschikbaar te stellen. Meer informatie over hoe we deze gegevens in dit [blog bericht][telemetry-blog]gebruiken, vindt u hier.

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
