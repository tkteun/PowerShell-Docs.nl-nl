---
title: Wat is er nieuw in Power shell Core 6,2
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,2
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "76995484"
---
# <a name="whats-new-in-powershell-core-62"></a>Wat is er nieuw in Power shell Core 6,2

De Power shell Core 6,2-release is gericht op verbeteringen in prestaties, fout oplossingen en kleinere cmdlet-en taal uitbreidingen waarmee de kwaliteit wordt verbeterd. Bekijk onze gedetailleerde [changelogs](https://github.com/PowerShell/PowerShell/releases) op github voor een volledige lijst met verbeteringen.

## <a name="experimental-features"></a>Experimentele functies

Voorheen hebben we ondersteuning voor [experimentele functies][]ingeschakeld. In de 6,2-release hebben we vier experimentele functies nodig om uit te proberen. Geef feedback zodat we verbeteringen kunnen aanbrengen en bepalen of de functie van belang is voor de status van de standaard.

Gebruik `Get-ExperimentalFeature` om een lijst met beschik bare experimentele functies op te halen. U kunt deze functies in-of uitschakelen `Enable-ExperimentalFeature` met `Disable-ExperimentalFeature`en.

### <a name="command-not-found-suggestions"></a>Suggesties van opdracht niet gevonden

Deze functie maakt gebruik van fuzzy match om suggesties te vinden voor opdrachten of cmdlets die u mogelijk hebt getypt.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Voorbeeld

In dit voor beeld is de onjuist gespelde naam van de cmdlet gelijk aan een aantal suggesties van de meest waarschijnlijke waarschijnlijke kans.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>Impliciete externe batch verwerking

Wanneer u [impliciete externe toegang](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in een pijp lijn gebruikt, behandelt Power shell elke opdracht onafhankelijk van elkaar in de pijp lijn. Objecten worden herhaaldelijk geserialiseerd en `de-serialized` tussen de client en het externe systeem over de uitvoering van de pijp lijn.

Met deze functie analyseert Power shell de pijp lijn om te bepalen of de opdracht veilig kan worden uitgevoerd en op het doel systeem. Indien true, voert Power shell de volledige pijp lijn op afstand uit en worden alleen `de-serializes` de resultaten naar de client geretourneerd.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Een Real-World-test `Get-Process | Sort-Object` van meer dan localhost verkleint van 10-15 seconden tot 20-30 **milliseconden**. De functie moet alleen worden ingeschakeld op de client. Er zijn geen wijzigingen vereist op de server.

### <a name="temp-drive"></a>Tijdelijk station

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Als u Power shell Core gebruikt op verschillende besturings systemen, detecteert u dat de omgevings variabele voor het vinden van de tijdelijke map anders is in Windows, macOS en Linux. Met deze functie krijgt u een [PSDrive][] met de `Temp:` naam die automatisch wordt toegewezen aan de tijdelijke map voor het besturings systeem dat u gebruikt.

#### <a name="example"></a>Voorbeeld

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

Houd er rekening mee dat systeem eigen bestands `ls` opdrachten (zoals op Linux) niet op de hoogte zijn van `Temp:` PSDrives en dit station niet te zien.

### <a name="abbreviation-expansion"></a>Afkorting uitbreiden

Voor Power shell-cmdlets wordt verwacht dat ze beschrijvende naam woorden bevatten. Dit resulteert in lange namen die moeilijker te typen zijn. Met deze functie kunt u alleen de hoofd letters van de cmdlet typen en de opdracht volt ooien gebruiken om een overeenkomst te vinden.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Voorbeeld

```powershell
PS> i-arsavsf
```

Als u op TAB drukt en de Azure PowerShell [AZ](https://www.powershellgallery.com/packages/Az) -module hebt geïnstalleerd, wordt deze automatisch aangevuld met:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Deze functie is bedoeld om interactief te worden gebruikt. Verkorte vormen van cmdlets kunnen niet worden uitgevoerd.
> Deze functie is geen vervanging voor aliassen.

## <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

- Herstel `-NoEnumerate` gedrag in `Write-Output` om consistent te zijn met Windows Power shell. (#9069)
- Resultaat `Join-String -InputObject 1,2,3` even maken als `1,2,3 | Join-String` resultaat (#8611) (bedankt @sethvs!)
- Toevoegen `-Stable` aan `Sort-Object` en verwante tests (#7862) (bedankt @KirkMunro!)
- De `Start-Sleep` cmdlet verbeteren om de Fractie seconden (#8537) te accepteren @Prototyyppi(bedankt!)
- Wijzig de hashtabel voor het gebruik `case-insensitive` van OrdinalIgnoreCase in alle cult uren (#8566)
- Herstel **LiteralPath** in `Import-Csv` om te verbinden `Get-ChildItem` met de uitvoer (#8277) @iSazonov(bedankt!)
- Slaat geen kolom zonder naam over als dubbele aanhalings tekens worden gebruikt in `Import-Csv` (#7899) (bedankt @Topping!)
- `Get-ExperimentalFeature`heeft `-ListAvailable` niet langer switches (#8318)
- De para meter Debug `$DebugPreference` wordt nu ingesteld om **door te gaan** in plaats van op @KirkMunrote **vragen** (#8195) (bedankt!)
- Ga `-OutputFormat` na of het is opgegeven in een niet-interactieve, omgeleide, gecodeerde opdracht die wordt gebruikt met pwsh (#8115)
- Assembly laden vanuit module base-pad voordat u probeert te laden vanuit de GAC (#8073)
- Tilde uit Linux preview packages verwijderen (#8244)
- Verwerking van `-WorkingDirectory` vóór verwerking van profielen verplaatsen (#8079)
- Geen omgevings `PATHEXT` variabele toevoegen op Unix (#7697) (bedankt @iSazonov!)

## <a name="known-issues"></a>Bekende problemen

- Externe toegang op Windows IOT ARM-platforms heeft een probleem met het laden van modules. Zie (#8053)

## <a name="general-updates-and-fixes"></a>Algemene updates en oplossingen

- Niet-hoofdletter gevoelige tabblad voltooiing inschakelen voor bestanden en mappen op hoofdletter gevoelig bestands systeem (#8128)
- Maak PSVersionInfo. PSVersion en PSVersionInfo. PSEdition openbaar (#8054) (bedankt @KirkMunro!)
- Type in-demijner `$_`  /  `$PSItem` toevoegen `catch{ }` voor in blokken (#8020) @vexx32(bedankt!)
- Een statische methode voor het aanroepen van het aanroep type herstellen (#8018 @SeeminglyScience) (bedankt!)
- Maak een afgeleid type `Select-Object`voor, `Group-Object`, **PSObject** en **hashtabel** (#7231) (bedankt @powercode!)
- Ondersteuning voor het aanroepen van methoden met `ByRef-like` type parameters (#7721)
- De aanvraag afhandelen waarbij het pad naar de Windows Power shell-module al aanwezig is in de PSModulePath van de omgeving (#7727)
- Schakel `SecureString` cmdlets voor niet-Windows in door de tekst zonder opmaak (#9199) op te slaan
- Fout bericht op niet-Windows verbeteren bij het importeren van clixml met securestring (#7997)
- Para meter ReplyTo toevoegen `Send-MailMessage` aan (#8727) ( @replicaJunctionBedankt!)
- Verouderd bericht toevoegen `Send-MailMessage` aan (#9178)
- Fix `Restart-Computer` om te werken `localhost` wanneer WinRM niet aanwezig is (#9160)
- `Start-Job` Fout bij het afbreken van de afsluiting wanneer Power shell wordt gehost (#9128)
- Voeg accelerators en achtervoegsels voor C#-stijl typen toe voor USHORT, uint, ULONG en short letterlijke tekens (#7813) @vexx32(bedankt!)
- Nieuwe achtervoegsels toegevoegd voor numerieke letterlijke waarden-Zie [about_Numeric_Literals][] (#7901) ( @vexx32Bedankt!)
- Het niveau van de impact op de juiste manier rapporteren wanneer SupportsShouldProcess niet is ingesteld op True ( @vexx32#8209) (bedankt!)
- Problemen met de aanvraag-charset in Web-cmdlets ( @markekraus#8742) oplossen (bedankt!)
- Verhelp `100-continue` het probleem met Web-cmdlets (#8679) @markekraus(bedankt!)
- Problemen met het blok keren van bestanden met Web-cmdlets ( @Claustn#7676) oplossen (bedankt!)
- Probleem met het parseren van `Invoke-RestMethod` code pagina in (#8694 @markekraus) oplossen (bedankt!)
- Refactorion `ConvertTo-Json` om JsonObject. ConvertToJson beschikbaar te maken als een open bare API (#8682)
- Configureer bare maximale diepte toevoegen in `ConvertFrom-Json` met-depth (#8199) (bedankt @louistio!)
- De para meter EscapeHandling `ConvertTo-Json` toevoegen in de cmdlet (#7775 @iSazonov) (bedankt!)
- Toevoegen `-CustomPipeName` aan pwsh en `Enter-PSHostProcess` (#8889)
- Het maken van relatieve symbolische koppelingen in `New-Item` Windows inschakelen met (#8783)
- Toestaan dat Windows-gebruikers in de ontwikkelaars modus symlinks maken zonder uitbrei ding (#8534)
- Inschakelen `Write-Information` om te `$null` accepteren (#8774)
- Oplossing `Get-Help` voor geavanceerde functies met MAML Help-inhoud (#8353)
- PSTypeName `Get-Help` probleem met-para meter oplossen wanneer er slechts één para meter is gedeclareerd (#8754 @pougetat) (hartelijk dank!)
- Correctie van token berekening `Get-Help` voor uitgevoerd op script Block voor Help bij opmerkingen. (#8238) (Bedankt @hubuk!)
- Wijzig `Get-Help` de para meter cmdlet-para meter zodat deze teken reeks matrices accepteert (#8454 @sethvs) (bedankt!)
- PAGINERING omzetten als het pad spaties bevat (#8571) (bedankt @pougetat!)
- Voeg een prompt toe voor het `less` gebruik van in de functie Help om gebruikers te instrueren hoe ze moeten worden afgesloten (#7998)
- Ondersteuning voor Enum en char-typen `Format-Hex` toevoegen in de cmdlet (#8191 @iSazonov) (bedankt!)
- Verwijder ShouldProcess uit `Format-Hex` (#8178)
- Nieuwe para meters voor offset en `Format-Hex` aantal toevoegen aan en refactorion de cmdlet (#7877 @iSazonov) (bedankt!)
- ' Name ' toestaan als een alias sleutel voor ' label ' in `ConvertTo-Html`, staat de vermelding ' width ' toe als geheel getal (#8426) (bedankt @mklement0!)
- Maak op script Block gebaseerde berekende eigenschappen opnieuw in `ConvertTo-Html` (#8427) (bedankt @mklement0!)
- Cmdlet `Join-String` toevoegen voor het maken van tekst vanuit pijplijn invoer (#7660) ( @powercodeBedankt!)
- De `Join-String` para meter Logic van cmdlet formats (#8449 @sethvs) oplossen (bedankt!)
- Ga `Clear-Host` terug naar met `$RAWUI` en wissen om te werken via externe communicatie (#8609)
- Wijzigen `Clear-Host` in simpelweg de `[console]::clear` alias wissen en verwijderen van UNIX (#8603)
- Herstel LiteralPath in `Import-Csv` om te verbinden `Get-ChildItem` met de uitvoer (#8277) @iSazonov(bedankt!)
- Help-functie mag paginering niet gebruiken voor AliasHelpInfo (#8552)
- Voeg `-UseMinimalHeader` toe `Start-Transcript` aan om de transcript header (#8402) te @lukexjeremyminimaliseren (bedankt!)
- Add `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature` cmdlets (#8318)
- Alle cmdlets weer geven vanuit **PSDiagnostics** als logman. exe beschikbaar is (#8366)
- **Persistente** para meter `New-PSDrive` verwijderen `non-Windows` van op platform (#8291) @lukexjeremy(bedankt!)
- Voeg ondersteuning toe `cd +` voor (#7206) ( @bergmeisterBedankt!)
- Inschakelen `Set-Location -LiteralPath` om te werken met mappen met de naam-en + (#8089)
- `Test-Path`retourneert `$false` wanneer een lege waarde of `$null` een pad (#8080) wordt gegeven @vexx32(hartelijk dank!)
- De dynamische para meter mag worden geretourneerd, zelfs als het pad niet overeenkomt met een provider (#7957)
- Ondersteuning `Get-PSHostProcessInfo` en `Enter-PSHostProcess` op Unix-platforms (#8232)
- Toewijzingen reduceren in `Get-Content` cmdlet (#8103) (bedankt @iSazonov!)
- Inschakelen `Add-Content` om Lees toegang te delen met andere hulpprogram ma's tijdens het schrijven van inhoud (#8091)
- `Get/Add-Content`genereert een verbeterde fout bij het richten op een container (#7823) ( @kvprasoonBedankt!)
- Toevoegen `-Name` `-NoUserOverrides` en `-ListAvailable` para meters `Get-Culture` voor cmdlet (#7702) ( @iSazonovBedankt!)
- Voeg een uniform kenmerk toe voor het volt ooien van de **coderings** parameter. (#7732) (Bedankt @ThreeFive-O!)
- Numerieke Id's en de naam van geregistreerde code pagina's in **coderings** parameters (#7636) @iSazonovtoestaan (bedankt!)
- Oplossen `Rename-Item -Path` met Joker tekens (#7398) (bedankt @kwkam!)
- Wanneer u `Start-Transcript` en file exists gebruikt, is een leeg bestand in plaats van verwijderen @paalbra(#8131) (bedankt!)
- Open `Add-Type` -source bestanden maken met **FileAccess. Read** en **file share. expliciet lezen** (#7915) @IISResetMe(bedankt!)
- Herstellen `Enter-PSSession -ContainerId` voor de nieuwste versie van Windows (#7883)
- Zorg ervoor dat de eigenschap **NestedModules** wordt `Test-ModuleManifest` gevuld door (#7859)
- Case `%F` toevoegen aan `Get-Date` -UFormat (#7630) (bedankt @britishben!)
- Oplossing `Set-Service -Status Stopped` voor het stoppen van services met afhankelijkheden (#5525 @zhenggu) (bedankt!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
