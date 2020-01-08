---
ms.date: 12/18/2019
keywords: Power shell, kern
title: Belang rijke wijzigingen voor Power shell 6,0
ms.openlocfilehash: dfbbeb5e5bb3d43959ce144afffc5b10193f8b30
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415698"
---
# <a name="breaking-changes-for-powershell-6x"></a>Belang rijke wijzigingen voor Power shell 6. x

## <a name="features-no-longer-available-in-powershell-core"></a>Functies die niet meer beschikbaar zijn in Power shell core

### <a name="powershell-workflow"></a>PowerShell-werkstroom

[Power shell workflow][workflow] is een functie in Windows Power shell die is gebaseerd op [Windows Workflow Foundation (WF)][workflow-foundation] waarmee robuuste runbooks kunnen worden gemaakt voor langdurige of geparalleleerde taken.

Vanwege het ontbreken van ondersteuning voor Windows Workflow Foundation in .NET core, bieden we geen ondersteuning voor Power shell-werk stroom in Power shell core.

In de toekomst willen we native parallellisme/gelijktijdigheid inschakelen in de Power shell-taal zonder dat Power shell-werk stroom nodig is.

Als er een controle punt moet worden gebruikt om een script te hervatten nadat het besturings systeem opnieuw is opgestart, raden we u aan taak planner te gebruiken om een script uit te voeren op het opstarten van het besturings systeem, maar moet het script een eigen status behouden (zoals het persistent maken van een bestand).

[workflow]: /powershell/scripting/components/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Aangepaste modules

[Power shell-][snapin] modules zijn een voorganger van Power shell-modules die geen uitgebreide aanneming hebben in de Power shell-community.

Vanwege de complexiteit van ondersteunende modules en het ontbreken van gebruik in de Community ondersteunen we geen aangepaste modules meer in Power shell core.

Nu worden de `ActiveDirectory`-en `DnsClient`-modules in Windows en Windows Server onderbroken.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1-cmdlets

Vanwege de complexiteit van het ondersteunen van twee sets WMI-modules, hebben we de WMI v1-cmdlets uit Power shell core verwijderd:

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

In plaats daarvan wordt u aangeraden de CIM-cmdlets (ook wel WMI v2) te gebruiken die dezelfde functionaliteit bieden als nieuwe functionaliteit en een opnieuw ontworpen syntaxis:

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

### <a name="microsoftpowershelllocalaccounts"></a>Micro soft. Power shell. LocalAccounts

Als gevolg van het gebruik van niet-ondersteunde Api's, is `Microsoft.PowerShell.LocalAccounts` verwijderd uit Power shell core totdat er een betere oplossing is gevonden.

### <a name="new-webserviceproxy-cmdlet-removed"></a>`New-WebServiceProxy`-cmdlet verwijderd

.NET core biedt geen ondersteuning voor het Windows Communication Framework, dat services biedt voor het gebruik van het SOAP-protocol. Deze cmdlet is verwijderd omdat SOAP is vereist.

### <a name="-computer-cmdlets"></a>`*-Computer`-cmdlets

Als gevolg van het gebruik van niet-ondersteunde Api's, zijn de volgende cmdlets uit Power shell core verwijderd totdat er een betere oplossing is gevonden.

- Add-Computer
- Checkpoint-Computer
- Remove-Computer
- Herstellen-computer

### <a name="-counter-cmdlets"></a>`*-Counter`-cmdlets

Als gevolg van het gebruik van niet-ondersteunde Api's, is het `*-Counter` verwijderd uit Power shell core totdat er een betere oplossing is gevonden.

### <a name="-eventlog-cmdlets"></a>`*-EventLog`-cmdlets

Als gevolg van het gebruik van niet-ondersteunde Api's, is het `*-EventLog` verwijderd uit Power shell core. totdat er een betere oplossing is gevonden. `Get-WinEvent` en `Create-WinEvent` zijn beschikbaar voor het ophalen en maken van gebeurtenissen in Windows.

## <a name="enginelanguage-changes"></a>Wijzigingen in de engine/taal

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>Wijzig de naam van `powershell.exe` in `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Om gebruikers een deterministische manier te geven om Power shell core aan te roepen in Windows (in plaats van Windows Power shell), is het binaire bestand van Power shell core gewijzigd in `pwsh.exe` op Windows en `pwsh` op niet-Windows-platforms.

De kortere naam is ook consistent met de naamgeving van shells op niet-Windows-platforms.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>Geen regel einden invoegen in uitvoer (met uitzonde ring van tabellen) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Voorheen werd de uitvoer uitgelijnd op de breedte van de console en worden er regel einden toegevoegd aan de eind breedte van de console, wat betekent dat de uitvoer niet opnieuw is ingedeeld zoals verwacht als de grootte van de Terminal is gewijzigd. Deze wijziging is niet toegepast op tabellen, omdat de regel einden nood zakelijk zijn om de kolommen uitgelijnd te laten worden.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>Null-element controle overs laan voor verzamelingen met een waarde type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Voor de para meter `Mandatory` en de kenmerken `ValidateNotNull` en `ValidateNotNullOrEmpty` slaat u de null-element controle uit als het element type van de verzameling het waardetype is.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>Wijzig `$OutputEncoding` om `UTF-8 NoBOM` code ring te gebruiken in plaats van ASCII- [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

De vorige code ring, ASCII (7-bits), resulteert in sommige gevallen in een onjuiste wijziging van de uitvoer. Deze wijziging is het maken van `UTF-8 NoBOM` standaard, waarmee Unicode-uitvoer wordt bewaard met een code ring die door de meeste hulpprogram ma's en besturings systemen wordt ondersteund.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>Verwijder `AllScope` van de meeste standaard aliassen [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Om het maken van het bereik te versnellen, is `AllScope` verwijderd uit de meeste standaard aliassen. `AllScope` is overgebleven voor een aantal veelgebruikte aliassen waarbij de zoek opdracht sneller is uitgevoerd.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` en `-Debug` worden niet meer overschreven `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Voorheen, als `-Verbose` of `-Debug` zijn opgegeven, overrode het gedrag van `$ErrorActionPreference`. Met deze wijziging zijn `-Verbose` en `-Debug` niet langer van invloed op het gedrag van `$ErrorActionPreference`.

## <a name="cmdlet-changes"></a>Cmdlet-wijzigingen

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>Invoke-RestMethod retourneert geen nuttige informatie wanneer er geen gegevens worden geretourneerd. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Wanneer een API wordt geretourneerd alleen `null`, werd invoke-RestMethod als teken `"null"` reeks geserialiseerd in plaats van `$null`. Deze wijziging corrigeert de logica in `Invoke-RestMethod` om een geldige JSON van een logische `null` waarde te serialiseren als `$null`.

### <a name="remove--protocol-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>`-Protocol` verwijderen uit `*-Computer`-cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Als gevolg van problemen met RPC-externe toegang in CoreFX (met name op niet-Windows-platforms) en het garanderen van een consistente externe ervaring in Power shell, is de para meter `-Protocol` verwijderd uit de `\*-Computer`-cmdlets. DCOM wordt niet meer ondersteund voor externe communicatie. De volgende cmdlets bieden alleen ondersteuning voor externe WSMAN-communicatie:

- Naam wijzigen-computer
- Restart-Computer
- Stop-computer

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>`-ComputerName` verwijderen uit `*-Service`-cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

Om het consistente gebruik van PSRP te stimuleren, is de para meter `-ComputerName` verwijderd uit `*-Service`-cmdlets.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>Herstel `Get-Item -LiteralPath a*b` als `a*b` niet echt bestaat om fout te retour neren [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Voorheen zou `-LiteralPath` op basis van een Joker teken hetzelfde doen als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten. Het juiste gedrag is dat `-LiteralPath` een letterlijke waarde heeft, zodat het een fout moet zijn als het bestand niet bestaat. Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>`Import-Csv` moet `PSTypeNames` Toep assen bij het importeren wanneer type gegevens aanwezig zijn in het CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Voorheen behouden objecten die zijn geëxporteerd met `Export-CSV` met `TypeInformation` geïmporteerd met `ConvertFrom-Csv` de type gegevens niet. Met deze wijziging wordt de type-informatie aan `PSTypeNames` lid toegevoegd als deze beschikbaar is vanuit het CSV-bestand.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` moet standaard zijn op `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Deze wijziging is doorgevoerd om de feedback van klanten te verhelpen over het standaard gedrag van `Export-CSV` om type gegevens op te nemen.

Voorheen voert de cmdlet een opmerking uit als de eerste regel met de type naam van het object. De wijziging is het onderdrukken van deze standaard instelling, omdat deze niet wordt begrepen door de meeste hulpprogram ma's. Gebruik `-IncludeTypeInformation` om het vorige gedrag te bewaren.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>Web-cmdlets moeten worden gewaarschuwd wanneer `-Credential` wordt verzonden via niet-versleutelde verbindingen [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Wanneer u HTTP gebruikt, worden inhoud, inclusief wacht woorden, verzonden als ongecodeerde tekst. Deze wijziging is het is niet toegestaan dit standaard te voor komen en een fout te retour neren als de referenties op een onveilige manier worden door gegeven. Gebruikers kunnen dit omzeilen door gebruik te maken van de `-AllowUnencryptedAuthentication` switch.

## <a name="api-changes"></a>API-wijzigingen

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>`AddTypeCommandBase` klasse verwijderen [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

De `AddTypeCommandBase` klasse is verwijderd uit `Add-Type` om de prestaties te verbeteren. Deze klasse wordt alleen gebruikt door de cmdlet Add-type en mag geen invloed hebben op gebruikers.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>Verenigen cmdlets met para meter `-Encoding` van het type `System.Text.Encoding` zijn [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

De `-Encoding` waarde `Byte` is verwijderd uit de cmdlets van het bestands systeem provider. Er wordt nu een nieuwe para meter, `-AsByteStream`, gebruikt om op te geven dat een byte stroom als invoer is vereist of dat de uitvoer een stroom van bytes is.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>Een beter fout bericht toevoegen voor een lege `-UFormat`-para meter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Wanneer een lege indelings teken reeks wordt door gegeven aan `-UFormat`, wordt een fout bericht weer gegeven. Er is een meer beschrijvende fout toegevoegd.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>Console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995) opschonen

De volgende functies zijn verwijderd omdat ze niet worden ondersteund in Power shell core en er zijn geen plannen om ondersteuning toe te voegen, omdat deze bestaan voor verouderde redenen voor Windows Power shell: `-psconsolefile` switch en code, `-importsystemmodules` switch en code, en het wijzigen van de code.

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>`RunspaceConfiguration` ondersteunings [#4942](https://github.com/PowerShell/PowerShell/issues/4942) is verwijderd

Wanneer u een Power shell-runs Pace programmatisch maakt met behulp van de API, kunt u de verouderde [`RunspaceConfiguration`][runspaceconfig] of de nieuwere [`InitialSessionState`][iss]gebruiken. Deze wijziging heeft ondersteuning voor `RunspaceConfiguration` verwijderd en ondersteunt alleen `InitialSessionState`.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` BIND argumenten aan `$input` in plaats van `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Een onjuiste positie van een para meter resulteerde in de argumenten die zijn door gegeven als invoer in plaats van als argumenten.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>Verwijder de niet-ondersteunde `-showwindow` switch van `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` is afhankelijk van WPF, wat niet wordt ondersteund op CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>Toestaan dat * wordt gebruikt in het registerpad voor `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Voorheen zou `-LiteralPath` op basis van een Joker teken hetzelfde doen als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten. Het juiste gedrag is dat `-LiteralPath` een letterlijke waarde heeft, zodat het een fout moet zijn als het bestand niet bestaat. Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>Fix `Set-Service` mislukte test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

Als `New-Service -StartupType foo` eerder is gebruikt, wordt `foo` genegeerd en is de service gemaakt met een standaard opstart type. Deze wijziging is het expliciet genereren van een fout voor een ongeldig opstart type.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>Wijzig de naam van `$IsOSX` in `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

De naamgeving in Power shell moet consistent zijn met de naamgeving en voldoen aan het gebruik van macOS in plaats van OSX. Voor de Lees baarheid en consistent wordt er echter geadviseerd dat de Pascal-behuizing.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>Fout bericht consistent maken wanneer ongeldig script wordt door gegeven aan-bestand, betere fout bij het door geven van een dubbel zinnig argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

De afsluit codes van `pwsh.exe` wijzigen in uitlijnen met UNIX-conventies

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>Het verwijderen van `LocalAccount` en cmdlets van `Diagnostics` modules. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Als gevolg van niet-ondersteunde Api's, zijn de `LocalAccounts`-module en de `Counter`-cmdlets in de `Diagnostics`-module verwijderd totdat er een betere oplossing is gevonden.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Het uitvoeren van een Power shell-script met de BOOL-para meter werkt niet [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Voorheen werd het gebruik van **Power shell. exe** (nu **pwsh. exe**) uitgevoerd om een Power shell-script uit te voeren met `-File` zonder dat u `$true`/`$false` als parameter waarden kunt door geven. Ondersteuning voor `$true`/`$false` als geparseerde waarden aan para meters is toegevoegd. Switch waarden worden ook ondersteund, omdat de syntaxis die momenteel wordt beschreven, niet werkt.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>`ClrVersion` eigenschap verwijderen uit `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

De eigenschap `ClrVersion` van `$PSVersionTable` is niet nuttig met CoreCLR. eind gebruikers moeten deze waarde niet gebruiken om de compatibiliteit te bepalen.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>Positionele para meter voor `powershell.exe` van `-Command` wijzigen in `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Schakel het shebang-gebruik van Power shell in op niet-Windows-platforms. Dit betekent dat u op UNIX gebaseerde systemen een uitvoerbaar script kunt maken dat Power shell automatisch aanroept in plaats van `pwsh`expliciet aan te roepen. Dit betekent ook dat u nu dingen als `powershell foo.ps1` of `powershell fooScript` kunt doen zonder `-File`op te geven. Voor deze wijziging moet u echter expliciet `-c` of `-Command` opgeven bij het uitvoeren van dingen als `powershell.exe Get-Command`.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>[#3958](https://github.com/PowerShell/PowerShell/issues/3958) voor het parseren van Unicode-escape implementeren

`` `u####`` of `` `u{####}`` wordt geconverteerd naar het bijbehorende Unicode-teken. Als u een letterlijke `` `u``wilt uitvoeren, sluit u de apostroffen: ``` ``u```.

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>`New-ModuleManifest` code ring wijzigen in `UTF8NoBOM` op niet-Windows-platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Voorheen maakt `New-ModuleManifest` psd1-manifesten in UTF-16 met stuk lijst en maakt u een probleem voor Linux-hulpprogram ma's. Door deze wijziging wordt de code ring van `New-ModuleManifest` gewijzigd in UTF (geen stuk lijst) in niet-Windows-platforms.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>Voor komen dat `Get-ChildItem` worden herhaald in symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Deze wijziging brengt `Get-ChildItem` meer in overeenstemming met de UNIX-`ls -r` en de Windows `dir /s` systeem eigen opdrachten. Net als de vermelde opdrachten worden met de cmdlet symbolische koppelingen weer gegeven naar directory's die tijdens recursie zijn gevonden, maar worden ze niet herhaald.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>Corrigeer `Get-Content -Delimiter` zodat het scheidings teken niet in de geretourneerde regels wordt vermeld [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Voorheen was de uitvoer tijdens het gebruik van `Get-Content -Delimiter` inconsistent en onhandig omdat het verdere verwerking van de gegevens nodig was om het scheidings teken te verwijderen. Met deze wijziging verwijdert u het scheidings teken in geretourneerde regels.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>Indeling-hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320) implementeren

De para meter `-Raw` is nu een ' Nee-op ' (in dat geval gebeurt er niets). Alle uitvoer wordt weer gegeven met een echte representatie van getallen die alle bytes voor het type bevat (waarvoor de para meter `-Raw` formeel vóór deze wijziging werd uitgevoerd).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>Power shell werkt als standaard shell niet met script opdracht [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

In UNIX is het een Conventie voor houders om `-i` te accepteren voor een interactieve shell en veel hulp middelen verwachten dit gedrag (`script` bijvoorbeeld en wanneer Power shell als de standaard shell wordt ingesteld) en wordt de shell aangeroepen met de `-i` switch. Deze wijziging is opgesplitst in dat `-i` eerder als korte hand zou kunnen worden gebruikt om te voldoen aan `-inputformat`, die nu moet worden `-in`.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Type correctie in Get-ComputerInfo eigenschap name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` verkeerd gespeld als `BiosSeralNumber` en is gewijzigd in de juiste spelling.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>`Get-StringHash`-en `Get-FileHash`-cmdlets toevoegen [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Deze wijziging is dat sommige hash-algoritmen niet worden ondersteund door CoreFX, dus zijn ze niet meer beschikbaar:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>Validatie toevoegen bij `Get-*`-cmdlets waarbij het door geven van $null alle objecten retourneert in plaats van fout [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Als `$null` wordt door gegeven aan een van de volgende, wordt een fout gegenereerd:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>De uitgebreide W3C-indeling voor logboek bestanden toevoegen in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

Voorheen kan de cmdlet `Import-Csv` niet worden gebruikt om de logboek bestanden rechtstreeks te importeren in de uitgebreide W3C-logboek indeling en dat er extra actie moet worden ondernomen. Met deze wijziging wordt de uitgebreide W3C-logboek indeling ondersteund.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>Fout bij het binden van de para meter met `ValueFromRemainingArguments` in PS-functies [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` retourneert nu de waarden als een matrix in plaats van een enkele waarde die zelf een matrix is.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`BuildVersion` is uit `$PSVersionTable` verwijderd [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Verwijder de eigenschap `BuildVersion` van `$PSVersionTable`. Deze eigenschap is gekoppeld aan de Windows-build-versie. In plaats daarvan raden we u aan `GitCommitId` te gebruiken om de exacte build-versie van Power shell Core op te halen.

### <a name="changes-to-web-cmdlets"></a>Wijzigingen in Web-cmdlets

De onderliggende .NET API van de Web-cmdlets is gewijzigd in `System.Net.Http.HttpClient`. Deze wijziging biedt veel voor delen. Deze wijziging in combi natie met een gebrek aan interoperabiliteit met Internet Explorer heeft geresulteerd in verschillende belang rijke wijzigingen in `Invoke-WebRequest` en `Invoke-RestMethod`.

- `Invoke-WebRequest` ondersteunt nu alleen eenvoudige HTML-parsering. `Invoke-WebRequest` retourneert altijd een `BasicHtmlWebResponseObject`-object. De eigenschappen `ParsedHtml` en `Forms` zijn verwijderd.
- `BasicHtmlWebResponseObject.Headers` waarden zijn nu `String[]` in plaats van `String`.
- `BasicHtmlWebResponseObject.BaseResponse` is nu een `System.Net.Http.HttpResponseMessage`-object.
- De eigenschap `Response` op Web cmdlet Exceptions is nu een `System.Net.Http.HttpResponseMessage`-object.
- Strikte RFC-header parseren is nu standaard voor de para meter `-Headers` en `-UserAgent`. Dit kan worden overgeslagen met `-SkipHeaderValidation`.
- `file://`-en `ftp://` URI-schema's worden niet meer ondersteund.
- `System.Net.ServicePointManager`-instellingen worden niet meer nageleefd.
- Er is momenteel geen authenticatie op basis van certificaten beschikbaar in macOS.
- Het gebruik van `-Credential` over een `http://` URI resulteert in een fout. Gebruik een `https://` URI of geef de para meter `-AllowUnencryptedAuthentication` op om de fout te onderdrukken.
- `-MaximumRedirection` maakt nu een afsluit fout als de omleidings pogingen de gegeven limiet overschrijden in plaats van de resultaten van de laatste omleiding te retour neren.
- In Power shell 6,2 is een wijziging aangebracht in UTF-8-code ring voor JSON-reacties. Wanneer een charset niet wordt opgegeven voor een JSON-antwoord, moet de standaard codering UTF-8 zijn per RFC 8259.
