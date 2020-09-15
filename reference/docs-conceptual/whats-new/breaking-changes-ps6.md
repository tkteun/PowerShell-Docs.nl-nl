---
ms.date: 02/03/2020
keywords: Power shell, kern
title: Belang rijke wijzigingen voor Power shell 6,0
ms.openlocfilehash: 9ead635232930598634141369fd2cc299f0b1799
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158187"
---
# <a name="breaking-changes-for-powershell-6x"></a>Belang rijke wijzigingen voor Power shell 6. x

## <a name="features-no-longer-available-in-powershell-core"></a>Functies die niet meer beschikbaar zijn in Power shell core

### <a name="modules-not-shipped-for-powershell-6x"></a>Modules die niet zijn verzonden voor Power shell 6. x

De volgende modules zijn niet voor verschillende compatibiliteits redenen opgenomen in Power shell 6.

- ISE
- Micro soft. Power shell. LocalAccounts
- Micro soft. Power shell. ODataUtils
- Micro soft. Power shell. Operation. validatie
- PSScheduledJob
- PSWorkflow
- PSWorkflowUtility

### <a name="powershell-workflow"></a>PowerShell-werkstroom

[Power shell workflow][workflow] is een functie in Windows Power shell die is gebaseerd op [Windows Workflow Foundation (WF)][workflow-foundation] waarmee robuuste runbooks kunnen worden gemaakt voor langdurige of geparalleleerde taken.

Vanwege het ontbreken van ondersteuning voor Windows Workflow Foundation in .NET core, bieden we geen ondersteuning voor Power shell-werk stroom in Power shell core.

In de toekomst willen we native parallellisme/gelijktijdigheid inschakelen in de Power shell-taal zonder dat Power shell-werk stroom nodig is.

Als er een controle punt moet worden gebruikt om een script te hervatten nadat het besturings systeem opnieuw is opgestart, raden we u aan taak planner te gebruiken om een script uit te voeren op het opstarten van het besturings systeem, maar moet het script een eigen status behouden (zoals het persistent maken van een bestand).

[workflow]: /previous-versions/powershell/scripting/components/workflows-guide
[workflow-foundation]: /dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>Aangepaste modules

[Power shell-][snapin] modules zijn een voorganger van Power shell-modules die geen uitgebreide aanneming hebben in de Power shell-community.

Vanwege de complexiteit van ondersteunende modules en het ontbreken van gebruik in de Community ondersteunen we geen aangepaste modules meer in Power shell core.

Nu worden de `ActiveDirectory` `DnsClient` modules en in Windows en Windows Server onderbroken.

[snapin]: /powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1-cmdlets

Vanwege de complexiteit van het ondersteunen van twee sets WMI-modules, hebben we de WMI v1-cmdlets uit Power shell core verwijderd:

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

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

Als gevolg van het gebruik van niet-ondersteunde Api's, `Microsoft.PowerShell.LocalAccounts` is verwijderd uit Power shell core totdat een betere oplossing is gevonden.

### <a name="new-webserviceproxy-cmdlet-removed"></a>`New-WebServiceProxy` cmdlet verwijderd

.NET core biedt geen ondersteuning voor het Windows Communication Framework, dat services biedt voor het gebruik van het SOAP-protocol. Deze cmdlet is verwijderd omdat SOAP is vereist.

### <a name="-transaction-cmdlets-removed"></a>`*-Transaction` cmdlets verwijderd

Deze cmdlets hebben een zeer beperkt gebruik. De beslissing is genomen om de ondersteuning voor hen te stoppen.

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a>Beveiligings-cmdlets die niet beschikbaar zijn op niet-Windows-platforms

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a>`*-Computer`en andere Windows-specifieke cmdlets

Als gevolg van het gebruik van niet-ondersteunde Api's, zijn de volgende cmdlets uit Power shell core verwijderd totdat er een betere oplossing is gevonden.

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a>`*-Counter` cmdlets

Als gevolg van het gebruik van niet-ondersteunde Api's, `*-Counter` is het uit Power shell core verwijderd totdat er een betere oplossing is gevonden.

### <a name="-eventlog-cmdlets"></a>`*-EventLog` cmdlets

Als gevolg van het gebruik van niet-ondersteunde Api's, `*-EventLog` is het verwijderd uit Power shell core. totdat er een betere oplossing is gevonden. `Get-WinEvent` en `Create-WinEvent` zijn beschikbaar voor het ophalen en maken van gebeurtenissen in Windows.

### <a name="cmdlets-that-use-wpf-removed"></a>Cmdlets die gebruikmaken van WPF verwijderd

Het Windows Presentation Framework wordt niet ondersteund op CoreCLR. De volgende cmdlets worden beïnvloed:

- `Show-Command`
- `Out-GridView`
- De **ShowWindow** -para meter van `Get-Help`

### <a name="some-dsc-cmdlets-removed"></a>Sommige DSC-cmdlets zijn verwijderd

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a>Wijzigingen in de engine/taal

### <a name="rename-powershellexe-to-pwshexe-5101"></a>Naam wijzigen `powershell.exe` in `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Om gebruikers een deterministische manier te geven om Power shell core aan te roepen in Windows (in plaats van Windows Power shell), is het binaire bestand van Power shell core gewijzigd in `pwsh.exe` op Windows en `pwsh` op niet-Windows-platforms.

De kortere naam is ook consistent met de naamgeving van shells op niet-Windows-platforms.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a>Geen regel einden invoegen in uitvoer (met uitzonde ring van tabellen) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

Voorheen werd de uitvoer uitgelijnd op de breedte van de console en worden er regel einden toegevoegd aan de eind breedte van de console, wat betekent dat de uitvoer niet opnieuw is ingedeeld zoals verwacht als de grootte van de Terminal is gewijzigd. Deze wijziging is niet toegepast op tabellen, omdat de regel einden nood zakelijk zijn om de kolommen uitgelijnd te laten worden.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a>Null-element controle overs laan voor verzamelingen met een waarde type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

Voor de `Mandatory` para meter en `ValidateNotNull` en `ValidateNotNullOrEmpty` -kenmerken slaat u de null-element controle op als het element type van de verzameling het waardetype is.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a>Wijziging `$OutputEncoding` van het gebruik `UTF-8 NoBOM` van code ring in plaats van ASCII- [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

De vorige code ring, ASCII (7-bits), resulteert in sommige gevallen in een onjuiste wijziging van de uitvoer. Deze wijziging is `UTF-8 NoBOM` standaard, waarbij Unicode-uitvoer wordt bewaard met een code ring die wordt ondersteund door de meeste hulpprogram ma's en besturings systemen.

### <a name="remove-allscope-from-most-default-aliases-5268"></a>Verwijderen `AllScope` uit de meeste standaard aliassen [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

Om het bereik sneller te maken, `AllScope` is verwijderd uit de meeste standaard aliassen. `AllScope` is overgebleven voor enkele veelgebruikte aliassen waarbij de zoek opdracht sneller is uitgevoerd.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a>`-Verbose` en worden `-Debug` niet meer overschreven `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

Voorheen, als `-Verbose` of `-Debug` was opgegeven, overrode het gedrag van `$ErrorActionPreference` . Met deze wijziging `-Verbose` en `-Debug` niet langer van invloed op het gedrag van `$ErrorActionPreference` .

## <a name="cmdlet-changes"></a>Cmdlet-wijzigingen

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a>Invoke-RestMethod retourneert geen nuttige informatie wanneer er geen gegevens worden geretourneerd. [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

Wanneer een API net retourneert `null` , wordt invoke-RestMethod als teken reeks geserialiseerd `"null"` in plaats van `$null` . Met deze wijziging wordt de logica in `Invoke-RestMethod` voor het op de juiste wijze serialiseren van een geldige letterlijke JSON-waarde met een bepaalde teken `null` reeks `$null` .

### <a name="remove--protocol-from--computer-cmdlets-5277"></a>Verwijderen `-Protocol` uit `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

Als gevolg van problemen met RPC-externe toegang in CoreFX (met name op niet-Windows-platforms) en het garanderen van een consistente externe ervaring in Power shell, `-Protocol` is de para meter uit de `\*-Computer` cmdlets verwijderd. DCOM wordt niet meer ondersteund voor externe communicatie. De volgende cmdlets bieden alleen ondersteuning voor externe WSMAN-communicatie:

- Naam wijzigen-computer
- Restart-Computer
- Stop-computer

### <a name="remove--computername-from--service-cmdlets-5090"></a>Verwijderen `-ComputerName` uit `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

De `-ComputerName` para meter is verwijderd uit cmdlets om het consistente gebruik van PSRP te stimuleren `*-Service` .

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a>Herstellen `Get-Item -LiteralPath a*b` Indien `a*b` niet echt bestaat om fout te retour neren [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

Als er eerder `-LiteralPath` een Joker teken wordt gegeven, zou dit hetzelfde zijn als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten. Het juiste gedrag `-LiteralPath` is een letterlijke waarde, dus als het bestand niet bestaat, moet het een fout zijn. Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a>`Import-Csv` moet worden toegepast bij `PSTypeNames` het importeren wanneer type gegevens aanwezig zijn in het CSV- [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

Voorheen behouden objecten die zijn geëxporteerd met `Export-CSV` met met `TypeInformation` geïmporteerd met `ConvertFrom-Csv` niet de type-informatie. Met deze wijziging worden de type gegevens aan het `PSTypeNames` lid toegevoegd als deze beschikbaar zijn vanuit het CSV-bestand.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a>`-NoTypeInformation` moet standaard zijn op `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

Deze wijziging is aangebracht om de feedback van klanten te verhelpen over het standaard gedrag van `Export-CSV` om type gegevens op te nemen.

Voorheen voert de cmdlet een opmerking uit als de eerste regel met de type naam van het object. De wijziging is het onderdrukken van deze standaard instelling, omdat deze niet wordt begrepen door de meeste hulpprogram ma's. Gebruiken `-IncludeTypeInformation` om het vorige gedrag te bewaren.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a>Web-cmdlets moeten worden gewaarschuwd wanneer `-Credential` wordt verzonden via niet-versleutelde verbindingen [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

Wanneer u HTTP gebruikt, worden inhoud, inclusief wacht woorden, verzonden als ongecodeerde tekst. Deze wijziging is het is niet toegestaan dit standaard te voor komen en een fout te retour neren als de referenties op een onveilige manier worden door gegeven. Gebruikers kunnen dit omzeilen door gebruik te maken van de `-AllowUnencryptedAuthentication` Switch.

## <a name="api-changes"></a>API-wijzigingen

### <a name="remove-addtypecommandbase-class-5407"></a>`AddTypeCommandBase` [#5407](https://github.com/PowerShell/PowerShell/issues/5407) klasse verwijderen

De `AddTypeCommandBase` klasse is verwijderd uit `Add-Type` om de prestaties te verbeteren. Deze klasse wordt alleen gebruikt door de cmdlet Add-type en mag geen invloed hebben op gebruikers.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a>De cmdlets worden samen met para meters `-Encoding` van het type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

De `-Encoding` waarde `Byte` is verwijderd uit de-cmdlets van het bestands systeem provider. Er wordt nu een nieuwe para meter `-AsByteStream` gebruikt om op te geven dat een byte stroom als invoer is vereist of dat de uitvoer een stroom van bytes is.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a>Een beter fout bericht toevoegen voor lege en null- `-UFormat` para meter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

Wanneer een lege indelings teken reeks wordt door gegeven aan `-UFormat` , zou er een onhelp-fout bericht worden weer gegeven. Er is een meer beschrijvende fout toegevoegd.

### <a name="clean-up-console-code-4995"></a>Console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995) opschonen

De volgende functies zijn verwijderd omdat ze niet worden ondersteund in Power shell core en er zijn geen plannen om ondersteuning toe te voegen, aangezien deze bestaan voor verouderde redenen voor Windows Power shell: `-psconsolefile` Switch en code, `-importsystemmodules` Switch en code, en letter type wijzigen van code.

### <a name="removed-runspaceconfiguration-support-4942"></a>`RunspaceConfiguration`Ondersteunings [#4942](https://github.com/PowerShell/PowerShell/issues/4942) verwijderd

Voorheen, wanneer u een Power shell-runs Pace programmatisch maakt met behulp van de API, kunt u de verouderde [`RunspaceConfiguration`][runspaceconfig] of de nieuwere versie gebruiken [`InitialSessionState`][iss] . Deze wijziging heeft ondersteuning voor `RunspaceConfiguration` en alleen ondersteund `InitialSessionState` .

[runspaceconfig]: /dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: /dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a>`CommandInvocationIntrinsics.InvokeScript` argumenten binden aan `$input` in plaats van `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

Een onjuiste positie van een para meter resulteerde in de argumenten die zijn door gegeven als invoer in plaats van als argumenten.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a>Niet-ondersteunde `-showwindow` Switch verwijderen van `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` is afhankelijk van WPF. dit wordt niet ondersteund in CoreCLR.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a>Toestaan dat * wordt gebruikt in het registerpad voor `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

Als er eerder `-LiteralPath` een Joker teken wordt gegeven, zou dit hetzelfde zijn als `-Path` en als het Joker teken geen bestanden heeft gevonden, wordt het op de achtergrond afgesloten. Het juiste gedrag `-LiteralPath` is een letterlijke waarde, dus als het bestand niet bestaat, moet het een fout zijn. Wijziging is het behandelen van joker tekens die worden gebruikt met `-Literal` als letterlijke waarde.

### <a name="fix-set-service-failing-test-4802"></a>`Set-Service`Mislukte test [#4802](https://github.com/PowerShell/PowerShell/issues/4802) herstellen

Voorheen werd, indien `New-Service -StartupType foo` gebruikt, `foo` genegeerd en is de service gemaakt met een standaard opstart type. Deze wijziging is het expliciet genereren van een fout voor een ongeldig opstart type.

### <a name="rename-isosx-to-ismacos-4700"></a>Naam wijzigen `$IsOSX` in `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

De naamgeving in Power shell moet consistent zijn met de naamgeving en voldoen aan het gebruik van macOS in plaats van OSX. Voor de Lees baarheid en consistent wordt er echter geadviseerd dat de Pascal-behuizing.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a>Fout bericht consistent maken wanneer ongeldig script wordt door gegeven aan-bestand, betere fout bij het door geven van een dubbel zinnig argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

De afsluit codes van wijzigen in `pwsh.exe` Uitlijnen met UNIX-conventies

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a>Het verwijderen van `LocalAccount` en cmdlets uit  `Diagnostics` modules. [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

Als gevolg van niet-ondersteunde Api's, `LocalAccounts` zijn de module en de `Counter` cmdlets in de `Diagnostics` module verwijderd totdat er een betere oplossing is gevonden.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a>Het uitvoeren van een Power shell-script met de BOOL-para meter werkt niet [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

Voorheen gebruik **powershell.exe** (nu **pwsh.exe**) om een Power shell-script uit te voeren dat is `-File` ingesteld op geen enkele manier `$true` / `$false` als parameter waarden worden door gegeven. `$true` / `$false` Er is ondersteuning toegevoegd voor als geparseerde waarden voor para meters. Switch waarden worden ook ondersteund, omdat de syntaxis die momenteel wordt beschreven, niet werkt.

### <a name="remove-clrversion-property-from-psversiontable-4027"></a>`ClrVersion`Eigenschap verwijderen uit `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

De `ClrVersion` eigenschap van `$PSVersionTable` is niet nuttig met CoreCLR, eind gebruikers moeten deze waarde niet gebruiken om de compatibiliteit te bepalen.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a>Positie parameters voor wijzigen `powershell.exe` van in `-Command` `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

Schakel het shebang-gebruik van Power shell in op niet-Windows-platforms. Dit betekent dat u op UNIX gebaseerde systemen een script bestand kunt maken dat Power shell automatisch aanroept in plaats van expliciet aan te roepen `pwsh` . Dit betekent ook dat u nu dingen kunt doen zoals `powershell foo.ps1` of `powershell fooScript` zonder op te geven `-File` . Voor deze wijziging moet u echter expliciet opgeven `-c` of als u wilt `-Command` proberen om dingen te doen `powershell.exe Get-Command` .

### <a name="implement-unicode-escape-parsing-3958"></a>[#3958](https://github.com/PowerShell/PowerShell/issues/3958) voor het parseren van Unicode-escape implementeren

`` `u####`` of `` `u{####}`` wordt geconverteerd naar het bijbehorende Unicode-teken. Als u een letterlijke waarde wilt uitvoeren, sluit u `` `u`` de apostroffen: ``` ``u``` .

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a>Wijzig de `New-ModuleManifest` code ring in `UTF8NoBOM` op niet-Windows-platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

Voorheen `New-ModuleManifest` maakt psd1-manifesten in UTF-16 met stuk lijst, waardoor er een probleem is met Linux-hulpprogram ma's. Door deze wijziging wordt de code ring van `New-ModuleManifest` als UTF (geen bom) gewijzigd in niet-Windows-platforms.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a>Geen `Get-ChildItem` herhaling in symlinks (#1875). [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

Deze wijziging brengt `Get-ChildItem` meer in overeenstemming met de `ls -r` systeem eigen UNIX-en Windows- `dir /s` opdrachten. Net als de vermelde opdrachten worden met de cmdlet symbolische koppelingen weer gegeven naar directory's die tijdens recursie zijn gevonden, maar worden ze niet herhaald.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a>Corrigeer `Get-Content -Delimiter` het scheidings teken niet in de geretourneerde regels [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

Voorheen was de uitvoer tijdens het gebruik `Get-Content -Delimiter` inconsistent en onhandig geworden toen verdere verwerking van de gegevens werd vereist om het scheidings teken te verwijderen. Met deze wijziging verwijdert u het scheidings teken in geretourneerde regels.

### <a name="implement-format-hex-in-c-3320"></a>Indeling-hex in C#- [#3320](https://github.com/PowerShell/PowerShell/issues/3320) implementeren

De `-Raw` para meter is nu een ' Nee-op ' (in dat geval gebeurt er niets). Alle uitvoer wordt weer gegeven met een echte representatie van getallen die alle bytes voor het type bevat (waarvoor de `-Raw` para meter formeel werd uitgevoerd vóór deze wijziging).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a>Power shell werkt als standaard shell niet met script opdracht [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

In UNIX is het een Conventie voor shells om `-i` een interactieve shell te accepteren en veel hulpprogram ma's verwachten dit gedrag ( `script` bijvoorbeeld wanneer Power shell als de standaard shell wordt ingesteld) en wordt de shell aangeroepen met de `-i` Switch. Deze wijziging is opgesplitst in die `-i` eerder als korte hand kan worden gebruikt `-inputformat` , wat nu moet worden gevonden `-in` .

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a>Type correctie in Get-ComputerInfo eigenschap name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` is verkeerd gespeld `BiosSeralNumber` en is gewijzigd in de juiste spelling.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a>`Get-StringHash`#3024 toevoegen en `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

Deze wijziging is dat sommige hash-algoritmen niet worden ondersteund door CoreFX, dus zijn ze niet meer beschikbaar:

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a>Validatie toevoegen voor `Get-*` cmdlets waarbij het door geven van $Null alle objecten retourneert in plaats van fout [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

Door door `$null` te geven aan een van de volgende fouten wordt een fout gegenereerd:

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

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a>Uitgebreide W3C-indeling van logboek bestand in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482) toevoegen

Voorheen kan de `Import-Csv` cmdlet niet worden gebruikt voor het rechtstreeks importeren van de logboek bestanden in de uitgebreide W3C-logboek indeling en is er extra actie vereist. Met deze wijziging wordt de uitgebreide W3C-logboek indeling ondersteund.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a>Fout bij het binden van de para meter met `ValueFromRemainingArguments` in PS-functies [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` retourneert nu de waarden als een matrix in plaats van een enkele waarde die zelf een matrix is.

### <a name="buildversion-is-removed-from-psversiontable-1415"></a>`BuildVersion` is verwijderd uit `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

Verwijder de `BuildVersion` eigenschap van `$PSVersionTable` . Deze eigenschap is gekoppeld aan de Windows-build-versie. In plaats daarvan raden we u `GitCommitId` aan gebruik te maken van om de exacte build-versie van Power shell Core op te halen.

### <a name="changes-to-web-cmdlets"></a>Wijzigingen in Web-cmdlets

De onderliggende .NET API van de Web-cmdlets is gewijzigd in `System.Net.Http.HttpClient` . Deze wijziging biedt veel voor delen. Deze wijziging in combi natie met een gebrek aan interoperabiliteit met Internet Explorer heeft tot gevolg dat er verschillende belang rijke wijzigingen zijn aangebracht in `Invoke-WebRequest` en `Invoke-RestMethod` .

- `Invoke-WebRequest` ondersteunt nu alleen eenvoudige HTML-parsering. `Invoke-WebRequest` retourneert altijd een- `BasicHtmlWebResponseObject` object. De `ParsedHtml` `Forms` Eigenschappen en zijn verwijderd.
- `BasicHtmlWebResponseObject.Headers` de waarden zijn nu `String[]` in plaats van `String` .
- `BasicHtmlWebResponseObject.BaseResponse` is nu een `System.Net.Http.HttpResponseMessage` object.
- De `Response` eigenschap van uitzonde ringen op Web-cmdlets is nu een `System.Net.Http.HttpResponseMessage` object.
- Strikte RFC-header parseren is nu standaard voor de `-Headers` `-UserAgent` para meter en. Dit kan worden omzeild met `-SkipHeaderValidation` .
- `file://` en `ftp://` URI-schema's worden niet meer ondersteund.
- `System.Net.ServicePointManager` de instellingen worden niet meer nageleefd.
- Er is momenteel geen authenticatie op basis van certificaten beschikbaar in macOS.
- Het gebruik van `-Credential` via een `http://` URI resulteert in een fout. Gebruik een `https://` URI of geef de `-AllowUnencryptedAuthentication` para meter op om de fout te onderdrukken.
- `-MaximumRedirection` produceert nu een afsluit fout wanneer de omleidings pogingen de gegeven limiet overschrijden in plaats van de resultaten van de laatste omleiding te retour neren.
- In Power shell 6,2 is een wijziging aangebracht in UTF-8-code ring voor JSON-reacties. Wanneer een charset niet wordt opgegeven voor een JSON-antwoord, moet de standaard codering UTF-8 zijn per RFC 8259.
