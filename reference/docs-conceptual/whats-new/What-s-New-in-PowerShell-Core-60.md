# <a name="whats-new-in-powershell-core-60"></a>Wat is er nieuw in PowerShell-kern 6.0

[PowerShell Core 6.0] [ github] is een nieuwe versie van PowerShell die cross-platform (Windows, Mac OS en Linux), open source en gebouwd voor heterogene omgevingen en de hybride cloud.

## <a name="moved-from-net-framework-to-net-core"></a>.NET Framework is verplaatst naar .NET Core

Maakt gebruik van PowerShell Core [.NET Core 2.0][] als de runtime.
.NET core 2.0 kunt PowerShell Core werken op meerdere platforms (Windows, Mac OS en Linux).
PowerShell Core wordt ook de API-set die worden aangeboden door .NET Core 2.0 moet worden gebruikt in de PowerShell-cmdlets en -scripts.

Windows PowerShell gebruikt de .NET Framework runtime voor het hosten van de PowerShell-engine.
Dit betekent dat Windows PowerShell de API-set die worden aangeboden door .NET Framework beschrijft.

De API's gedeeld tussen .NET Core en .NET Framework zijn gedefinieerd als onderdeel van [.NET Standard][].

Zie voor meer informatie over hoe dit van invloed op module-script compatibiliteit tussen PowerShell Core en Windows PowerShell, [Backwards compatibiliteit met Windows PowerShell](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>Ondersteuning voor Mac OS- en Linux

PowerShell officieel ondersteunt nu Mac OS- en Linux, met inbegrip van:

- Windows 7, 8.1 en 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows-serverkanaal puntkomma per jaar][semi-annual]
- Ubuntu 14.04 16.04 en 17.04
- Debian 8,7 + en 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42,2
- Fedora 25, 26
- macOS 10.12+

Onze community heeft ook bijgedragen pakketten voor de volgende platforms, maar ze zijn niet officieel ondersteund:

- Boog Linux
- Kali Linux
- AppImage (werkt op meerdere platforms voor Linux)

Ook hebben we experimentele (niet-ondersteunde) versies voor de volgende platforms:

- Windows via ARM32/ARM64
- Raspbian (Stretch)

Een aantal wijzigingen zijn aangebracht in PowerShell Core 6.0 zodat deze beter werkt op niet-Windows-systemen.
Sommige van deze zijn wijzigingen, die ook van invloed op Windows splitsen.
Andere zijn alleen aanwezig of is van toepassing in niet-Windows-installaties van PowerShell Core.

- Ondersteuning toegevoegd voor systeemeigen opdracht bij globbing op Unix-platforms.
- De `more` functionaliteit respecteert de Linux `$PAGER` en wordt standaard ingesteld op `less`.
  Dit betekent dat u kunt nu met gebruik van jokertekens systeemeigen binaire bestanden/opdrachten (bijvoorbeeld `ls *.txt`). (#3463)
- Afsluitende backslash is automatisch ontsnapt systeemeigen opdrachtargumenten betreft. (#4965)
- Negeer de `-ExecutionPolicy` overschakelen wanneer PowerShell op niet-Windows-platforms worden uitgevoerd omdat de ondertekening van het script wordt momenteel niet ondersteund. (#3481)
- Vaste ConsoleHost inwilligen `NoEcho` op Unix-platforms. (#3801)
- Vaste `Get-Help` ter ondersteuning van hoofdlettergevoelig patroon overeen op de Unix-platforms. (#3852)
- `powershell` Man-pagina toegevoegd aan het pakket

### <a name="logging"></a>Logboekregistratie

Op Mac OS, PowerShell wordt het native `os_log` API's om Apple [unified logboekregistratie system][os_log].
Op Linux, PowerShell wordt [Syslog][], een oplossing alomtegenwoordige logboekregistratie.

### <a name="filesystem"></a>Bestandssysteem

Een aantal wijzigingen zijn aangebracht op Mac OS- en Linux ter ondersteuning van oudsher niet ondersteund op Windows tekens:

- Paden die tot de cmdlets zijn nu slash-networkdirect (zowel / en \ werk directory scheiding)
- XDG Base Directory specificatie is nu in acht genomen en standaard gebruikt:
  - Het pad van het Linux/Mac OS-profiel bevindt zich op `~/.config/powershell/profile.ps1`
  - De geschiedenis pad op te slaan bevindt zich op `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - Het pad van de gebruiker-module bevindt zich op `~/.local/share/powershell/Modules`
- Ondersteuning voor bestands- en mapnamen met de dubbele punt op Unix. (#4959)
- Ondersteuning voor scriptnamen- of volledige paden met komma's. (#4136) (Dank aan @TimCurwick!)
- Detecteren wanneer `-LiteralPath` wordt gebruikt voor het onderdrukken van jokertekens voor navigatie-cmdlets. (#5038)
- Bijgewerkt `Get-ChildItem` meer achtige werkt de * nix `ls -R` en de Windows `DIR /S` systeemeigen opdrachten.
  `Get-ChildItem` nu retourneert de symbolische koppelingen aangetroffen tijdens een recursieve zoekopdracht en niet in de mappen die het doel van deze koppelingen. (#3780)

### <a name="case-sensitivity"></a>Hoofdlettergevoeligheid

Linux- en Mac OS zijn meestal hoofdlettergevoelig terwijl Windows behoud van de aanvraag niet hoofdlettergevoelig is.
In het algemeen is PowerShell niet hoofdlettergevoelig.

Omgevingsvariabelen zijn bijvoorbeeld hoofdlettergevoelig op Mac OS- en Linux, dus het hoofdlettergebruik van de `PSModulePath` omgevingsvariabele is gestandaardiseerd. (#3255) `Import-Module` is niet hoofdlettergevoelig bij het gebruik van een bestandspad om te bepalen van de naam van de module. (#5097)

## <a name="support-for-side-by-side-installations"></a>Ondersteuning voor side-by-side-installaties

PowerShell Core is geïnstalleerd, geconfigureerd en afzonderlijk verwerkt vanuit de Windows PowerShell.
PowerShell Core is een 'draagbare' ZIP-pakket.
Het ZIP-pakket gebruikt, kunt u installeren een willekeurig aantal versies overal op schijf, met inbegrip van een lokale bron naar een toepassing die nodig is PowerShell als een afhankelijkheid.
Side-by-side installation vergemakkelijkt het testen van nieuwe versies van PowerShell en migreren van bestaande scripts gedurende een bepaalde periode.
Naast elkaar kan ook achterwaartse compatibiliteit zoals scripts kunnen worden gekoppeld aan specifieke versies die ze nodig hebben.

> [!NOTE]
> Het installatieprogramma (MSI) gebaseerde in Windows biedt standaard een in-place update-installatie.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>Hernoemd `powershell(.exe)` naar `pwsh(.exe)`

De binaire naam voor de belangrijkste PowerShell is gewijzigd van `powershell(.exe)` naar `pwsh(.exe)`.
Deze wijziging biedt een deterministische manier voor gebruikers PowerShell Core uitvoeren op machines ter ondersteuning van side-by-side Windows PowerShell en PowerShell Core-installaties.
`pwsh` is het ook veel korter en beter typt.

Aanvullende wijzigingen aan `pwsh(.exe)` van `powershell.exe`:

- De eerste positionele parameter van gewijzigd `-Command` naar `-File`.
  Deze wijziging kunt u het gebruik van `#!` (ook bekend als een shebang) in de PowerShell-scripts die worden uitgevoerd van de niet-PowerShell schalen op niet-Windows-platforms.
  Het betekent ook dat u opdrachten zoals kunt uitvoeren `pwsh foo.ps1` of `pwsh fooScript` zonder op te geven `-File`.
  Deze wijziging vereist echter dat u expliciet opgeeft `-c` of `-Command` tijdens het uitvoeren van opdrachten zoals `pwsh.exe -Command Get-Command`. (#4019)
- PowerShell Core accepteert de `-i` (of `-Interactive`) switch om aan te geven van een interactieve shell. (#3558) Hiermee kunt PowerShell om te worden gebruikt als een standaardshell voor op Unix-platforms.
- Parameters verwijderd `-importsystemmodules` en `-psconsoleFile` van `pwsh.exe`. (#4995)
- Gewijzigd `pwsh -version` en ingebouwde help voor `pwsh.exe` uitgelijnd met andere systeemeigen hulpprogramma's. (#4958 & #4931) (Met vriendelijke groet @iSazonov)
- Ongeldig argument foutberichten voor `-File` en `-Command` en afsluitcodes consistent zijn met Unix-standaarden (#4573)
- Toegevoegd `-WindowStyle` parameter in Windows. (#4573) Installaties op basis van pakket-updates op niet-Windows-platforms zijn op dezelfde manier in-place updates.

## <a name="backwards-compatibility-with-windows-powershell"></a>Achterwaartse compatibiliteit met Windows PowerShell

Het doel van PowerShell Core is om te blijven als compatibel mogelijk met Windows PowerShell.
Maakt gebruik van PowerShell Core [.NET Standard][] 2.0 voor binaire compatibiliteit met bestaande .NET-assembly's.
Veel PowerShell-modules, is afhankelijk van deze assembly's (vaak tijden dll-bestanden), zodat de standaard .NET kunnen ze blijven werken met .NET Core.
PowerShell Core bevat ook een heuristiek in bekende mappen--toe, zoals waar de Global Assembly Cache bevindt zich doorgaans op schijf--om te zoeken naar afhankelijkheden van .NET Framework-dll-bestand te zoeken.

Voor meer informatie over .NET standaard op de [.NET-Blog][], in dit [YouTube][] video en via dit [Veelgestelde vragen over][] op GitHub.

Best mogelijke is gedaan om ervoor te zorgen dat de PowerShell-modules voor taal en 'ingebouwde' (zoals `Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility`, enzovoort) werken op dezelfde manier als in Windows PowerShell.
In veel gevallen met behulp van de community toegevoegd nieuwe functies en foutoplossingen voor die cmdlets.
In sommige gevallen kan vanwege een ontbrekende afhankelijkheid in onderliggende .NET lagen functionaliteit is verwijderd of is niet beschikbaar.

De meeste van de modules die worden geleverd als onderdeel van Windows (bijvoorbeeld `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage`, enzovoort) en andere Microsoft-producten met inbegrip van Azure en Office zijn niet *expliciet* overgezet naar. Nog NET Core.
Het PowerShell-team werkt samen met deze productfamilies en teams om te valideren en poort van hun bestaande modules naar PowerShell-kern.
Met .NET Standard en [CDXML][]veel van deze traditionele Windows PowerShell-modules lijken te werken in PowerShell Core, maar ze niet formeel zijn gevalideerd en worden ze niet officieel ondersteund.

Door het installeren van de [ `WindowsPSModulePath` ] [ windowspsmodulepath] -module, kunt u Windows PowerShell-modules gebruiken door de Windows PowerShell toe te voegen `PSModulePath` naar uw PowerShell-kern `PSModulePath`.

Installeer eerst de `WindowsPSModulePath` module op basis van de PowerShell-galerie:

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

Voer na het installeren van deze module de `Add-WindowsPSModulePath` cmdlet om toe te voegen van de Windows PowerShell `PSModulePath` naar PowerShell-kern:

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker-ondersteuning

PowerShell Core voegt ondersteuning toe voor Docker-containers voor de primaire platforms die wordt ondersteund (met inbegrip van meerdere Linux-distributies, Windows Server Core en Nano Server).

Voor een volledige lijst, bekijk de labels op [ `microsoft/powershell` op Docker Hub][docker-hub].
Zie voor meer informatie over Docker en PowerShell Core [Docker][] op GitHub.

## <a name="ssh-based-powershell-remoting"></a>SSH op basis van PowerShell voor externe toegang

De PowerShell Remoting Protocol (PSRP) werkt nu met het protocol Secure Shell (SSH) naast de traditionele PSRP op basis van WinRM.

Dit betekent dat u cmdlets, zoals kunt `Enter-PSSession` en `New-PSSession` en verifiëren met behulp van SSH.
Hoeft u PowerShell registreren als een subsysteem met een OpenSSH op basis van een SSH-server is en u kunt uw bestaande SSH gebaseerde verificatie mechanismen (zoals wachtwoorden of persoonlijke sleutels) met de traditionele `PSSession` semantiek.

Zie voor meer informatie over het configureren en gebruiken van externe toegang op basis van SSH [PowerShell voor externe toegang via SSH][ssh-remoting].

## <a name="default-encoding-is-utf-8-without-a-bom"></a>Standaardcodering is UTF-8 zonder een stuklijst

In het verleden Windows PowerShell-cmdlets, zoals `Get-Content`, `Set-Content` verschillende coderingen, zoals ASCII- en UTF-16 wordt gebruikt.
De verschillen in de Aanvraagcodering gemaakt problemen wanneer de combinatie van cmdlets zonder op te geven een codering.

Zonder een Byte Order Mark (BOM) UTF-8 niet-Windows-platforms oudsher gebruiken als de standaardversleuteling voor tekstbestanden.
Meer Windows-toepassingen en hulpprogramma's zijn bewegende weg UTF-16 en naar BOM minder UTF-8-codering.
PowerShell Core verandert de standaardversleuteling die voldoen aan de breder ecosystemen.

Dit betekent dat alle ingebouwde cmdlets die gebruikmaken van de `-Encoding` parameter gebruik de `UTF8NoBOM` waarde standaard.
De volgende cmdlets worden beïnvloed door deze wijziging:

- Add-Content
- Export Clixml
- Export-Csv
- Export-PSSession
- Indeling Hex
- Get-Content
- Import-Csv
- New-ModuleManifest
- Out-File
- Selecteer-tekenreeks
- Send-MailMessage
- Set-Content

Deze cmdlets ook zijn bijgewerkt zodat de `-Encoding` -parameter accepteert universeel `System.Text.Encoding`.

De standaardwaarde van `$OutputEncoding` ook is gewijzigd in UTF-8.

Als een best practice moet u expliciet coderingen instellen in scripts met de `-Encoding` parameter voor het produceren van deterministische gedrag in verschillende platforms.

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>Ondersteuning voor backgrounding van pijplijnen met en-teken (`&`) (#3360)

Plaatsen `&` aan het einde van een pijplijn zorgt ervoor dat de pijplijn worden uitgevoerd als een PowerShell-taak.
Wanneer u een pijplijn is backgrounded, wordt een taakobject geretourneerd.
Zodra de pijplijn wordt uitgevoerd als een taak, alle van de standaard `*-Job` cmdlets kunnen worden gebruikt voor het beheren van de taak.
Variabelen (proces-specifieke variabelen op) gebruikt in de pijplijn worden automatisch gekopieerd naar de taak dus `Copy-Item $foo $bar &` gewoon werkt.
De taak wordt ook uitgevoerd in de huidige map in plaats van de basismap van de gebruiker.
Zie voor meer informatie over PowerShell taken [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs).

## <a name="semantic-versioning"></a>Semantische versiebeheer

- Aangebracht `SemanticVersion` compatibel is met `SemVer 2.0`. (#5037) (Met vriendelijke groet @iSazonov!)
- Standaard gewijzigd `ModuleVersion` in `New-ModuleManifest` naar `0.0.1` uitgelijnd met SemVer. (#4842) (Met vriendelijke groet @LDSpits)
- Toegevoegd `semver` als een type accelerator voor `System.Management.Automation.SemanticVersion`. (#4142) (Dank aan @oising!)
- Vergelijking tussen ingeschakeld een `SemanticVersion` exemplaar en een `Version` exemplaar dat is opgesteld alleen met `Major` en `Minor` Versiewaarden.

## <a name="language-updates"></a>Taalupdates

- Unicode-escape parseren zodat gebruikers Unicode-tekens als argumenten, tekenreeksen of namen van variabelen gebruiken kunnen worden geïmplementeerd. (#3958) (Dank aan @rkeithhill!)
- Toegevoegde nieuwe escape-teken voor ESC: `` `e``
- Ondersteuning toegevoegd voor het converteren van enum-waarden voor de tekenreeks (#4318) (met vriendelijke groet @KirkMunro)
- Vaste casten één element matrix aan een algemene verzameling. (#3170)
- Toegevoegde teken bereik overbelasting aan de `..` operator, dus `'a'..'z'` tekens retourneert tussen "a" en "z". (#5026) (Met vriendelijke groet @IISResetMe!)
- Toewijzing van vaste variabele alleen-lezen-variabelen niet overschrijven
- Push-locals van automatische variabelen naar 'DottedScopes' wanneer dotting script cmdlets (#4709)
- Gebruik van 'Singleline, Multiline' optie in splitsingsoperator inschakelen (#4721) (met vriendelijke groet @iSazonov)

## <a name="engine-updates"></a>Engine-updates

- `$PSVersionTable` heeft vier nieuwe eigenschappen:
  - `PSEdition`: Dit is ingesteld op `Core` op PowerShell Core en `Desktop` op Windows PowerShell
  - `GitCommitId`: Dit is de Git commit-ID van de Git-vertakking of code waarbij PowerShell is opgebouwd.
    Uitgebrachte builds voor waarschijnlijk moeten hetzelfde zijn als `PSVersion`.
  - `OS`: Dit is een OS-versie-tekenreeks geretourneerd door `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`
  - `Platform`: Dit wordt geretourneerd door `[System.Environment]::OSVersion.Platform` is ingesteld op `Win32NT` op Windows, `MacOSX` op Mac OS, en `Unix` op Linux.
- Verwijderd de `BuildVersion` eigenschap uit `$PSVersionTable`.
  Deze eigenschap is sterk gekoppeld aan de build-versie van Windows.
  In plaats daarvan het is raadzaam dat u `GitCommitId` voor het ophalen van de exacte build-versie van PowerShell Core. (#3877) (Dank aan @iSazonov!)
- Verwijder `ClrVersion` eigenschap uit `$PSVersionTable`.
  Deze eigenschap is niet relevant voor .NET Core en is alleen voor specifieke verouderde doeleinden die niet van toepassing op PowerShell zijn in .NET Core behouden blijven.
- Drie nieuwe automatische variabelen om te bepalen of PowerShell wordt uitgevoerd in een bepaald besturingssysteem toegevoegd: `$IsWindows`, `$IsMacOs`, en `$IsLinux`.
- Voeg `GitCommitId` naar PowerShell Core banner.
  Nu u hoeft te worden uitgevoerd `$PSVersionTable` zodra u PowerShell als u de versie begint! (#3916) (Dank aan @iSazonov!)
- Toevoegen van een JSON-configuratiebestand aangeroepen `powershell.config.json` in `$PSHome` voor het opslaan van enkele instellingen die vereist zijn voor opstarten (bijvoorbeeld `ExecutionPolicy`).
- Pijplijn niet blokkeren wanneer Windows-EXE wordt uitgevoerd
- De inventarisatie van COM-verzamelingen is ingeschakeld. (#4553)

## <a name="cmdlet-updates"></a>Updates van de cmdlet

### <a name="new-cmdlets"></a>Nieuwe cmdlets

- Voeg `Get-Uptime` naar `Microsoft.PowerShell.Utility`.
- Voeg `Remove-Alias` opdracht. (#5143) (Met vriendelijke groet @PowershellNinja!)
- Voeg `Remove-Service` aan Management-module. (#4858) (Met vriendelijke groet @joandrsn!)

### <a name="web-cmdlets"></a>Web-cmdlets

- Certificaat verificatie ondersteuning toevoegen voor web-cmdlets. (#4646) (Met vriendelijke groet @markekraus)
- Ondersteuning voor inhoud headers toevoegen aan de web-cmdlets. (#4494 & #4640) (Met vriendelijke groet @markekraus)
- Ondersteuning voor meerdere koppeling header toevoegen aan Web-Cmdlets. (#5265) (Met vriendelijke groet @markekraus!)
- Ondersteuning voor koppeling header paginering in web-cmdlets (#3828)
  - Voor `Invoke-WebRequest`, wanneer het antwoord bevat de header van een koppeling maken we een eigenschap RelationLink als een woordenlijst die vertegenwoordigt de URL's en `rel` kenmerken en zorg ervoor dat de URL's zijn absolute eenvoudiger voor ontwikkelaars om te gebruiken.
  - Voor `Invoke-RestMethod`, wanneer het antwoord bevat een koppeling koptekst we geven een `-FollowRelLink` switch automatisch volgen `next` `rel` koppelingen totdat ze niet langer bestaat of één keer wordt bereikt het optionele `-MaximumFollowRelLink` parameterwaarde.
- Voeg `-CustomMethod` -parameter voor web-cmdlets om toe te staan voor niet-standaard methode termen. (#3142) (Dank aan @Lee303!)
- Voeg `SslProtocol` ondersteuning voor Web-Cmdlets. (#5329) (Met vriendelijke groet @markekraus!)
- Toevoegen van Multipart ondersteuning voor web-cmdlets. (#4782) (Met vriendelijke groet @markekraus)
- Voeg `-NoProxy` naar web cmdlets zodat ze het hele systeem proxy-instelling negeren. (#3447) (Dank aan @TheFlyingCorpse!)
- Gebruiker-Agent van de Web-Cmdlets rapporteert nu het besturingssysteem of platform (#4937) (met vriendelijke groet @LDSpits)
- Voeg `-SkipHeaderValidation` overschakelen naar de web-cmdlets voor de ondersteuning van headers toe te voegen zonder het valideren van de headerwaarde. (#4085)
- Web-cmdlets voor het HTTPS-certificaat van de server niet valideren als vereist inschakelen.
- Parameters voor verificatie toevoegen aan web-cmdlets. (#5052) (Met vriendelijke groet @markekraus)
  - Voeg `-Authentication` biedt drie opties: Basic, OAuth en Bearer.
  - Voeg `-Token` de bearer-token ophalen voor OAuth en Bearer-opties.
  - Voeg `-AllowUnencryptedAuthentication` authentication dat is opgegeven voor een transportschema dan HTTPS overslaan.
- Voeg `-ResponseHeadersVariable` naar `Invoke-RestMethod` waarmee het vastleggen van antwoordheaders. (#4888) (Met vriendelijke groet @markekraus)
- Los de web-cmdlets voor het HTTP-antwoord opnemen in de uitzondering wanneer de code voor antwoordstatus niet geslaagd is. (#3201)
- Web-cmdlets wijzigen `UserAgent` van `WindowsPowerShell` naar `PowerShell`. (#4914) (Met vriendelijke groet @markekraus)
- Voeg expliciete `ContentType` detectie om `Invoke-RestMethod` (#4692)
- Web-cmdlets los `-SkipHeaderValidation` werkt met niet-standaard gebruikersagent headers. (#4479 & #4512) (Met vriendelijke groet @markekraus)

### <a name="json-cmdlets"></a>JSON-cmdlets

- Voeg `-AsHashtable` naar `ConvertFrom-Json` retourneren een `Hashtable` in plaats daarvan. (#5043) (Met vriendelijke groet @bergmeister!)
- Gebruik kleurcodes formatter met `ConvertTo-Json` uitvoer. (#2787) (Dank aan @kittholland!)
- Voeg `Jobject` ondersteuning van serialisatie `ConvertTo-Json`. (#5141)
- Los `ConvertFrom-Json` voor het deserialiseren van een matrix met tekenreeksen vanuit de pipeline die samen een volledige JSON-tekenreeks te maken.
  Dit wordt soms waarbij nieuwe regels strijdig is met JSON parseren opgelost. (#3823)
- Verwijder de `AliasProperty "Count"` gedefinieerd voor `System.Array`.
  Hiermee verwijdert u de overbodige `Count` eigenschap voor een aantal `ConvertFrom-Json` uitvoer. (#3231) (Dank aan @PetSerAl!)

### <a name="csv-cmdlets"></a>CSV-cmdlets

- Voeg `PSTypeName` ondersteuning voor `Import-Csv` en `ConvertFrom-Csv`. (#5389) (Met vriendelijke groet @markekraus!)
- Controleer `Import-Csv` ondersteunen `CR`, `LF`, en `CRLF` als scheidingstekens regel. (#5363) (Met vriendelijke groet @iSazonov!)
- Controleer `-NoTypeInformation` de standaardwaarde op `Export-Csv` en `ConvertTo-Csv`. (#5164) (Met vriendelijke groet @markekraus)

### <a name="service-cmdlets"></a>Service-cmdlets

- Eigenschappen toevoegen `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName`, en `StartupType` naar de `ServiceController` objecten geretourneerd door `Get-Service`. (#4907) (Met vriendelijke groet @joandrsn)
- Toevoegen van functionaliteit om referenties te stellen op `Set-Service` opdracht. (#4844) (Met vriendelijke groet @joandrsn)

### <a name="other-cmdlets"></a>Andere cmdlets

- Toevoegen van een parameter voor `Get-ChildItem` aangeroepen `-FollowSymlink` dat symlinks op aanvraag met de controles voor koppeling lussen passeert. (#4020)
- Update `Add-Type` ter ondersteuning van `CSharpVersion7`. (#3933) (Dank aan @iSazonov)
- Verwijder de `Microsoft.PowerShell.LocalAccounts` module vanwege het gebruik van niet-ondersteunde API's tot een betere oplossing is gevonden. (#4302)
- Verwijder de `*-Counter` -cmdlets in `Microsoft.PowerShell.Diagnostics` vanwege het gebruik van niet-ondersteunde API's tot een betere oplossing is gevonden. (#4303)
- Ondersteuning toevoegen voor `Invoke-Item -Path <folder>`. (#4262)
- Voeg `-Extension` en `-LeafBase` verandert in een `Split-Path` zodat u paden tussen de bestandsnaamextensie en de rest van de bestandsnaam verdelen kunt. (#2721) (Dank aan @powercode!)
- Voeg parameters toe `-Top` en `-Bottom` naar `Sort-Object` voor bovenste/onderste N sorteren
- Een proces bovenliggende proces weergeven door toe te voegen de `CodeProperty "Parent"` naar `System.Diagnostics.Process`. (#2850) (Dank aan @powercode!)
- MB gebruiken in plaats van KB voor geheugenkolommen van het `Get-Process`
- Voeg `-NoNewLine` overschakelen voor `Out-String`. (#5056) (Met vriendelijke groet @raghav710)
- `Move-Item` cmdlet respecteert `-Include`, `-Exclude`, en `-Filter` parameters. (#3878)
- Toestaan dat `*` moet worden gebruikt in het registerpad voor `Remove-Item`. (#4866)
- Voeg `-Title` naar `Get-Credential` en Combineer de ervaring van de vragen in verschillende platforms.
- Voeg de `-TimeOut` -parameter voor `Test-Connection`. (#2492)
- `Get-AuthenticodeSignature` cmdlets kunt nu handtekening bestandtijdstempel krijgen. (#4061)
- Verwijder niet-ondersteunde `-ShowWindow` overschakelen van `Get-Help`. (#4903)
- Los `Get-Content -Delimiter` aan het scheidingsteken niet opnemen in de matrixelementen geretourneerd (#3706) (met vriendelijke groet @mklement0)
- Voeg `Meta`, `Charset`, en `Transitional` parameters `ConvertTo-HTML` (#4184) (met vriendelijke groet @ergo3114)
- Voeg `WindowsUBR` en `WindowsVersion` eigenschappen `Get-ComputerInfo` resultaat
- Voeg `-Group` parameter `Get-Verb`
- Voeg `ShouldProcess` ondersteuning voor `New-FileCatalog` en `Test-FileCatalog` (corrigeert `-WhatIf` en `-Confirm`). (#3074) (Dank aan @iSazonov!)
- Voeg `-WhatIf` overschakelen naar `Start-Process` cmdlet (#4735) (met vriendelijke groet @sarithsutha)
- Voeg `ValidateNotNullOrEmpty` te veel bestaande parameters.

## <a name="tab-completion"></a>Tab-aanvulling

- De typeverwijzing in de tab-aanvulling op basis van waarden van de runtime-variabelen zijn uitgebreid. (#2744) (Dank aan @powercode!) Hiermee kunt de tab-Aanvulling in dergelijke situaties:

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- Toevoegen van hash-tabel tab-aanvulling voor `-Property` van `Select-Object`. (#3625) (Dank aan @powercode)
- Argument automatisch aanvullen voor inschakelen `-ExcludeProperty` en `-ExpandProperty` van `Select-Object`. (#3443) (Dank aan @iSazonov!)
- Los van een fout op de tab-Aanvulling aanbrengen `native.exe --<tab>` -aanroep in systeemeigen voltooien. (#3633) (Dank aan @powercode!)

## <a name="breaking-changes"></a>Wijzigingen op te splitsen

Er zijn een aantal grote wijzigingen in PowerShell Core 6.0 hebt geïntroduceerd.
Voor meer informatie over deze in detail zien [wijzigingen op te splitsen in PowerShell Core 6.0][breaking-changes].

## <a name="debugging"></a>Foutopsporing

- Ondersteuning voor step-in Foutopsporing op afstand voor `Invoke-Command -ComputerName`. (#3015)
- Binder logboekregistratie voor foutopsporing in PowerShell Core inschakelen

## <a name="filesystem-updates"></a>Bestandssysteem updates

- Informatie over het gebruik van de provider van het bestandssysteem van een UNC-pad inschakelen. ($4998)
- `Split-Path` werkt nu met UNC-toegangspunten
- `cd` zonder argumenten nu gedraagt zich als `cd ~`
- Vaste PowerShell-kern toestaan gebruik van paden die meer dan 260 tekens lang zijn. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Oplossingen voor problemen en verbeterde prestaties

We hebben aangebracht *veel* verbeteringen via PowerShell, zoals in het starten van de tijd, verschillende ingebouwde cmdlets en interactie met systeemeigen binaire bestanden voor de prestaties.

We hebben ook een aantal fouten in PowerShell Core opgelost.
Bekijk voor een volledige lijst van wijzigingen en correcties onze [changelog][] op GitHub.

## <a name="telemetry"></a>Telemetrie

- PowerShell Core 6.0 toegevoegd telemetrie naar de host van de console om te rapporteren twee waarden (#3620):
  - het besturingssysteem of platform (`$PSVersionTable.OSDescription`)
  - de exacte versie van PowerShell (`$PSVersionTable.GitCommitId`)

Als u opt-out van deze telemetrie, verwijderen `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY` of maak `POWERSHELL_TELEMETRY_OPTOUT` omgevingsvariabele met een van de volgende waarden: `true`, `1` of `yes`.
Verwijderen van dit bestand of maken van de variabele wordt overgeslagen alle telemetrie zelfs vóór de eerste uitvoering van PowerShell.
We zullen ook op het blootstellen van deze telemetriegegevens en de inzichten die we verzamelen van de telemetrie in de [community dashboard][community-dashboard].
U vindt meer informatie over hoe deze worden gebruikt in deze [blogbericht][telemetry-blog].

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET-Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[Veelgestelde vragen over]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
