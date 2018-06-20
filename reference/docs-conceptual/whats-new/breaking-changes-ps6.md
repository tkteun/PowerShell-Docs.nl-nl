---
ms.date: 05/17/2018
keywords: PowerShell, core
title: Wijzigingen op te splitsen voor PowerShell 6.0
ms.openlocfilehash: 60ce7a1676403bb08b57bf852ba725acde86a30c
ms.sourcegitcommit: 2d9cf1ccb9a653db7726a408ebcb65530dcb1522
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34309572"
---
# <a name="breaking-changes-for-powershell-60"></a>Wijzigingen op te splitsen voor PowerShell 6.0

## <a name="features-no-longer-available-in-powershell-core"></a>Functies die niet meer beschikbaar zijn in PowerShell Core

### <a name="powershell-workflow"></a>PowerShell-werkstroom

[PowerShell-werkstroom] [ workflow] is een functie in Windows PowerShell die boven voortbouwt [Windows Workflow Foundation (WF)] [ workflow-foundation] waarmee het maken van robuuste runbooks voor langlopende of geparallelliseerde taken.

Vanwege het ontbreken van ondersteuning voor Windows Workflow Foundation in .NET Core we kan niet worden voortgezet ter ondersteuning van PowerShell Workflow in PowerShell Core.

In de toekomst, willen we systeemeigen parallelle uitvoering/gelijktijdigheid van taken in de taal PowerShell zonder de noodzaak van PowerShell Workflow inschakelen.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Aangepaste modules

[PowerShell-modules] [ snapin] zijn van een voorafgaande PowerShell-modules bevatten geen algemene acceptatie in de PowerShell-community.

Vanwege de complexiteit van ondersteunende-modules en hun weinig gebruikt in de community ondersteuning we niet langer voor aangepaste modules in PowerShell Core.

Vandaag de dag dit verbreekt de `ActiveDirectory` en `DnsClient` modules in Windows en Windows Server.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1-cmdlets

Vanwege de complexiteit van twee sets van WMI-gebaseerde modules ondersteunen, wordt de WMI v1-cmdlets uit PowerShell Core verwijderd:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

In plaats daarvan raden we u het gebruik van de CIM (ook wel WMI v2)-cmdlets die nieuwe functionaliteit en een vernieuwde syntaxis dezelfde functionaliteit bieden:

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

Vanwege het gebruik van niet-ondersteunde API's, `Microsoft.PowerShell.LocalAccounts` is verwijderd uit de PowerShell-kern tot een betere oplossing is gevonden.

### <a name="-counter-cmdlets"></a>`*-Counter`-cmdlets

Vanwege het gebruik van niet-ondersteunde API's, de `*-Counter` is verwijderd uit de PowerShell-kern tot een betere oplossing is gevonden.

## <a name="enginelanguage-changes"></a>Engine/wijzigen

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Wijzig de naam van `powershell.exe` naar `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Om te kunnen geven gebruikers een deterministische manier aan te roepen PowerShell Core voor Windows (in plaats van Windows PowerShell), het PowerShell-kern binaire bestand is gewijzigd in `pwsh.exe` in Windows en `pwsh` op niet-Windows-platforms.

Er is ook de korte naam consistent zijn met de naam van de houders op niet-Windows-platforms.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Voeg geen regeleinden om uit te voeren (met uitzondering van tabellen) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Eerder uitvoer is afgestemd op de breedte van de console en regeleinden zijn toegevoegd aan de eindbreedte van de console, wat betekent dat de uitvoer niet ophalen geformatteerd zoals verwacht als de terminal is gewijzigd. Deze wijziging is niet toegepast op tabellen, zoals de regeleinden nodig zijn voor het behouden van de kolommen uitgelijnd.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Controle van null-element voor verzamelingen met een waardetype elementtype overslaan [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Voor de `Mandatory` parameter en `ValidateNotNull` en `ValidateNotNullOrEmpty` kenmerken, de null-element-controle overslaan als het elementtype van de verzameling is een waardetype.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Wijziging `$OutputEncoding` gebruiken `UTF-8 NoBOM` in plaats van ASCII-codering [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

De vorige codering, ASCII (7-bits) zou leiden tot onjuiste afwijking van de uitvoer in sommige gevallen. Deze wijziging is ervoor `UTF-8 NoBOM` standaard behouden Unicode-uitvoer blijft met een codering wordt ondersteund door de meeste hulpprogramma's en besturingssystemen.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Verwijder `AllScope` van de meeste standaardaliassen [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Bereik voor het maken, versnellen `AllScope` is verwijderd uit de meeste standaardaliassen. `AllScope` is gegeven voor een aantal veelgebruikte aliassen waarop de zoekactie is sneller.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` en `-Debug` niet langer overschrijft `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Voorheen als `-Verbose` of `-Debug` zijn opgegeven, wordt het gedrag van overrode `$ErrorActionPreference`. Met deze wijziging `-Verbose` en `-Debug` geen invloed meer op het gedrag van `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Wijzigingen van de cmdlet

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Aanroepen RestMethod niet nuttige informatie geretourneerd wanneer er geen gegevens worden geretourneerd. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Wanneer een API retourneert alleen `null`, Invoke RestMethod dit als de tekenreeks is serialiseren `"null"` in plaats van `$null`. Deze wijziging corrigeert de logica in `Invoke-RestMethod` goed serialiseren geen geldige enkele waarde JSON `null` letterlijke als `$null`.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>Verwijder `-ComputerName` van `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Vanwege problemen met RPC voor externe toegang in CoreFX (met name op niet-Windows-platforms) en het waarborgen dat een consistente remoting ervaring in PowerShell de `-ComputerName` parameter is verwijderd uit de `\*-Computer` cmdlets. Gebruik `Invoke-Command` in plaats daarvan de manier cmdlets op afstand uitvoeren.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>Verwijder `-ComputerName` van `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Om aan te raden het consistent gebruik van PSRP, de `-ComputerName` parameter is verwijderd uit `*-Service` cmdlets.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Los `Get-Item -LiteralPath a*b` als `a*b` bestaat niet als u wilt terugkeren fout [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Voorheen `-LiteralPath` gegeven een jokerteken zou behandelen hetzelfde als `-Path` en als het jokerteken er worden geen bestanden gevonden, deze zou achtergrond af te sluiten. Juiste gedrag die moet worden `-LiteralPath` letterlijke is dus als het bestand niet bestaat, deze fout moet. Wijziging is op dezelfde manier behandelen jokertekens gebruikt in combinatie met `-Literal` als literal.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` van toepassing moeten zijn `PSTypeNames` tijdens het importeren wanneer typegegevens aanwezig is in de CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Voorheen objecten geëxporteerd met `Export-CSV` met `TypeInformation` met geïmporteerd `ConvertFrom-Csv` zijn de type-informatie niet behouden. Deze wijziging wordt toegevoegd aan de type-informatie `PSTypeNames` lid indien beschikbaar vanuit het CSV-bestand.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` standaard moet zich op `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Deze wijziging is aangebracht naar aanleiding van feedback op het standaardgedrag van `Export-CSV` type informatie op te nemen.

Voorheen zou de cmdlet een opmerking uitvoer als de eerste regel met de typenaam van het object. De wijziging is dit standaard onderdrukken als dit niet wordt begrepen door de meeste hulpprogramma's. Gebruik `-IncludeTypeInformation` om de werking van de vorige te behouden.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Web-Cmdlets moet waarschuwen bij `-Credential` wordt verzonden via niet-versleutelde verbindingen [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Wanneer u HTTP gebruikt, worden inhoud, met inbegrip van wachtwoorden als leesbare tekst verzonden. Deze wijziging is niet toestaan dit standaard en retourneert een fout als de referenties in een onbeveiligde manier worden doorgegeven. Gebruikers kunnen dit omzeilen met behulp van de `-AllowUnencryptedAuthentication` overschakelen.

## <a name="api-changes"></a>Wijzigingen van de API

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>Verwijder `AddTypeCommandBase` klasse [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

De `AddTypeCommandBase` klasse is verwijderd uit `Add-Type` om prestaties te verbeteren. Deze klasse wordt alleen gebruikt door de cmdlet Add-Type en mag geen invloed op gebruikers.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Combineer cmdlets met de parameter `-Encoding` van het type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

De `-Encoding` waarde `Byte` is verwijderd uit de cmdlets van de provider bestandssysteem. Een nieuwe parameter `-AsByteStream`, wordt nu gebruikt om op te geven dat een bytestream vereist als is invoer of dat de uitvoer een stream van bytes is.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Toevoegen van betere foutbericht voor leeg en null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Voorheen wanneer het doorgeven van een leeg indeling string naar `-UFormat`, een onnuttige foutbericht wordt weergegeven. Een meer beschrijvend foutbericht Er is toegevoegd.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Opruimen van de console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

De volgende onderdelen zijn verwijderd als ze worden niet ondersteund in PowerShell Core, en er geen plannen ondersteuning toevoegen zijn als deze bestaan om oudere redenen voor Windows PowerShell: `-psconsolefile` switch en code, `-importsystemmodules` switch en code en lettertype programmacode wijzigen.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>Verwijderd `RunspaceConfiguration` ondersteunen [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

Voorheen bij het maken van een PowerShell-runspace programmatisch met behulp van de API kunt u de verouderde [ `RunspaceConfiguration` ] [ runspaceconfig] of de nieuwere [ `InitialSessionState` ] [ iss]. Deze wijziging niet langer ondersteuning voor `RunspaceConfiguration` en biedt alleen ondersteuning voor `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` argumenten voor BIND `$input` in plaats van `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

De positie van een parameter van een onjuist ertoe geleid dat de argumenten doorgegeven als invoer in plaats van als argumenten.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Verwijder niet-ondersteunde `-showwindow` overschakelen van `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` is afhankelijk van WPF, wat niet wordt ondersteund op CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Toestaan dat * moet worden gebruikt in het registerpad voor `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Voorheen `-LiteralPath` gegeven een jokerteken zou behandelen hetzelfde als `-Path` en als het jokerteken er worden geen bestanden gevonden, deze zou achtergrond af te sluiten. Juiste gedrag die moet worden `-LiteralPath` letterlijke is dus als het bestand niet bestaat, deze fout moet. Wijziging is op dezelfde manier behandelen jokertekens gebruikt in combinatie met `-Literal` als literal.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Los `Set-Service` test mislukt [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Voorheen als `New-Service -StartupType foo` is gebruikt, `foo` is genegeerd en de service is gemaakt met het opstarttype van bepaalde standaard. Deze wijziging wordt expliciet genereert een fout voor een ongeldige opstarttype.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Wijzig de naam van `$IsOSX` naar `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

De naamgeving in PowerShell moet in overeenstemming zijn met onze naming en voldoen aan Apples gebruik van Mac OS in plaats van OSX. Echter, voor de leesbaarheid en consistent we zijn bijwerkt met Pascal hoofdlettergebruik.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Fout bij het bericht consistent maken wanneer ongeldig script wordt doorgegeven voor - bestand, een fout opgetreden tijdens het niet-eenduidige argument doorgegeven voor een betere [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Wijzigen van de afsluitcodes van `pwsh.exe` uitgelijnd met de Unix-overeenkomsten

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Verwijderen van `LocalAccount` en cmdlets van `Diagnostics` modules. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Als gevolg van niet-ondersteunde API's, de `LocalAccounts` module en de `Counter` -cmdlets in de `Diagnostics` module zijn verwijderd tot een betere oplossing is gevonden.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Uitvoeren van powershell-script met Boole-parameter werkt niet [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Gebruikte powershell.exe (nu `pwsh.exe`) uit te voeren met een PowerShell-script met `-File` opgegeven geen manier om door te geven $true/$false als parameterwaarden. Ondersteuning voor $true $false als geparseerde waarden parameters is toegevoegd. Switch-waarden worden ook ondersteund als momenteel gedocumenteerde syntaxis werkt niet.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>Verwijder `ClrVersion` eigenschap uit `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

De `ClrVersion` eigenschap van `$PSVersionTable` is niet nuttig met CoreCLR eindgebruikers mag worden gemaakt van die waarde om te bepalen van de compatibiliteit.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Wijzig positionele parameter voor `powershell.exe` van `-Command` naar `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Schakel shebang gebruik van PowerShell op niet-Windows-platforms. Dit betekent dat op Unix gebaseerde systemen, kunt u een script uitvoerbaar bestand dat PowerShell zouden oproepen automatisch in plaats van de expliciet aanroepen `pwsh`. Dit betekent ook dat u kunt nu bijvoorbeeld doen `powershell foo.ps1` of `powershell fooScript` zonder op te geven `-File`. Deze wijziging nu vereist echter dat u expliciet opgeeft `-c` of `-Command` bij een poging voor handelingen zoals `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>Bij het parseren van Unicode escape implementeren [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` of `` `u{####} `` wordt geconverteerd naar het overeenkomstige Unicode-teken. Om uit te voeren, letterlijke waarde `` `u ``, escape voor de backtick: ``` ``u ```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>Wijziging `New-ModuleManifest` codering op `UTF8NoBOM` op niet-Windows-platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Voorheen `New-ModuleManifest` psd1 manifesten maakt in UTF-16 met stuklijst, het maken van een probleem voor Linux-hulpprogramma's. Deze wijziging laatste verandert de codering van `New-ModuleManifest` UTF (geen BOM) zich in niet-Windows-platforms.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Voorkomen dat `Get-ChildItem` van recursing in symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Deze wijziging brengt `Get-ChildItem` meer in overeenstemming met de Unix `ls -r` en de Windows `dir /s` systeemeigen opdrachten. Als de genoemde opdrachten de cmdlet geeft symbolische koppelingen naar de mappen die zijn gevonden tijdens recursie, maar komt niet in deze recurse.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Los `Get-Content -Delimiter` niet op te nemen het scheidingsteken in de geretourneerde regels [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Voorheen werd door de uitvoer tijdens het gebruik van `Get-Content -Delimiter` is inconsistent en onhandig dit verdere verwerking van de gegevens te verwijderen van het scheidingsteken vereist. Deze wijziging verwijdert het scheidingsteken in de geretourneerde regels.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Indeling Hex implementeren in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

De `-Raw` parameter is nu een 'no-op' (in dat er niets gebeurt). Voortaan alle van de uitvoer wordt weergegeven met een goede afspiegeling zijn van de getallen die met alle van de bytes voor het type bevat (wat de `-Raw` parameter formeel voordat deze wijziging werd uitgevoerd).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>PowerShell als een standaardshell werkt niet met scriptopdracht [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

Op Unix is een conventie voor houders accepteren `-i` voor een interactieve shell en veel hulpprogramma's voor dit gedrag verwacht (`script` bijvoorbeeld en wanneer PowerShell instellen als de standaardshell) en roept de shell met de `-i` overschakelen. Deze wijziging is afbreken in die `-i` eerder kan worden gebruikt als korte hand overeenkomen met `-inputformat`, welke nu moet `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Fix typefout in de naam van de eigenschap Get-ComputerInfo [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` verkeerd is gespeld als `BiosSeralNumber` en is gewijzigd in de juiste spelling.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>Voeg `Get-StringHash` en `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Deze wijziging is dat bepaalde hash-algoritmen worden niet ondersteund door CoreFX, ze zijn daarom niet langer beschikbaar:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Validatie toevoegen op `Get-*` cmdlets waarbij alle objecten in plaats van de fout doorgeven $null retourneert [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Doorgegeven `$null` aan een van de volgende nu er wordt een fout geretourneerd:

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>Voeg ondersteuning W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Voorheen de `Import-Csv` cmdlet kan niet worden gebruikt voor het importeren van de logboekbestanden in de uitgebreide W3C-logboekindeling rechtstreeks en verdere actie zijn vereist. Met deze wijziging wordt uitgebreide W3C-logboekindeling ondersteund.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Parameter bindingsprobleem met `ValueFromRemainingArguments` in PS functies [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` nu retourneert de waarden als matrix in plaats van één welke zelf waarde is een matrix.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` wordt verwijderd uit `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Verwijder de `BuildVersion` eigenschap uit `$PSVersionTable`. Deze eigenschap is gekoppeld aan de build-versie van Windows. In plaats daarvan het is raadzaam dat u `GitCommitId` voor het ophalen van de exacte build-versie van PowerShell Core.

### <a name="changes-to-web-cmdlets"></a>Wijzigingen in de Web-Cmdlets

De onderliggende .NET API van de Web-Cmdlets is gewijzigd in `System.Net.Http.HttpClient`. Deze wijziging biedt veel voordelen. Maar deze wijziging samen met een gebrek aan interoperabiliteit met Internet Explorer heeft geleid tot enkele grote wijzigingen binnen `Invoke-WebRequest` en `Invoke-RestMethod`.

- `Invoke-WebRequest` ondersteunt nu basic parseren van HTML alleen. `Invoke-WebRequest` retourneert altijd een `BasicHtmlWebResponseObject` object. De `ParsedHtml` en `Forms` eigenschappen zijn verwijderd.
- `BasicHtmlWebResponseObject.Headers` waarden zijn nu `String[]` in plaats van `String`.
- `BasicHtmlWebResponseObject.BaseResponse` is nu een `System.Net.Http.HttpResponseMessage` object.
- De `Response` eigenschap op het Web Cmdlet uitzonderingen is nu een `System.Net.Http.HttpResponseMessage` object.
- Strikte RFC-header parseren is nu standaard voor de `-Headers` en `-UserAgent` parameter. Dit kan worden overgeslagen met `-SkipHeaderValidation`.
- `file://` en `ftp://` URI-schema's worden niet langer ondersteund.
- `System.Net.ServicePointManager` instellingen worden niet langer gehonoreerd.
- Er is momenteel geen certificaatverificatie op basis van beschikbaar op Mac OS.
- Het gebruik van `-Credential` via een `http://` URI in een fout resulteert. Gebruik een `https://` URI of geef de `-AllowUnencryptedAuthentication` -parameter voor het onderdrukken van de fout.
