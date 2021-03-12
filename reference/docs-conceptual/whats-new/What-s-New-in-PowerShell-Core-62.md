---
title: Wat is er nieuw in Power shell Core 6,2
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,2
ms.date: 03/28/2019
ms.openlocfilehash: 068f345ee5174bceade2b85183646ede9ead1949
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195578"
---
# <a name="whats-new-in-powershell-core-62"></a>Wat is er nieuw in Power shell Core 6,2

De Power shell Core 6,2-release is gericht op verbeteringen in prestaties, fout oplossingen en kleinere cmdlet-en taal uitbreidingen waarmee de kwaliteit wordt verbeterd. Bekijk onze gedetailleerde [changelogs](https://github.com/PowerShell/PowerShell/releases) op github voor een volledige lijst met verbeteringen.

## <a name="experimental-features"></a>Experimentele functies

Voorheen hebben we ondersteuning voor [experimentele functies][]ingeschakeld. In de 6,2-release hebben we vier experimentele functies nodig om uit te proberen. Geef feedback zodat we verbeteringen kunnen aanbrengen en bepalen of de functie van belang is voor de status van de standaard.

Gebruik `Get-ExperimentalFeature` om een lijst met beschik bare experimentele functies op te halen. U kunt deze functies in-of uitschakelen met `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature` .

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

Een Real-World-test van `Get-Process | Sort-Object` meer dan localhost verkleint van 10-15 seconden tot 20-30 **milliseconden**. De functie moet alleen worden ingeschakeld op de client. Er zijn geen wijzigingen vereist op de server.

### <a name="temp-drive"></a>Tijdelijk station

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Als u Power shell Core gebruikt op verschillende besturings systemen, detecteert u dat de omgevings variabele voor het vinden van de tijdelijke map anders is in Windows, macOS en Linux. Met deze functie krijgt u een [PSDrive][] met `Temp:` de naam die automatisch wordt toegewezen aan de tijdelijke map voor het besturings systeem dat u gebruikt.

#### <a name="example"></a>Voorbeeld

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

Houd er rekening mee dat systeem eigen bestands opdrachten (zoals `ls` op Linux) niet op de hoogte zijn van PSDrives en dit station niet te zien `Temp:` .

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
- `Join-String -InputObject 1,2,3`Resultaat even maken als `1,2,3 | Join-String` resultaat (#8611) (bedankt @sethvs !)
- Toevoegen `-Stable` aan `Sort-Object` en verwante tests (#7862) (bedankt @KirkMunro !)
- De `Start-Sleep` cmdlet verbeteren om de Fractie seconden (#8537) te accepteren (bedankt @Prototyyppi !)
- Wijzig de hashtabel voor het gebruik `case-insensitive` van OrdinalIgnoreCase in alle cult uren (#8566)
- Herstel **LiteralPath** in `Import-Csv` om te verbinden met de `Get-ChildItem` uitvoer (#8277) (bedankt @iSazonov !)
- Slaat geen kolom zonder naam over als dubbele aanhalings tekens worden gebruikt in `Import-Csv` (#7899) (bedankt @Topping !)
- `Get-ExperimentalFeature` heeft niet langer `-ListAvailable` switches (#8318)
- De para meter debug wordt nu ingesteld `$DebugPreference` om **door te gaan** in plaats van op te **vragen** (#8195) (bedankt @KirkMunro !)
- Ga na `-OutputFormat` of het is opgegeven in een niet-interactieve, omgeleide, gecodeerde opdracht die wordt gebruikt met pwsh (#8115)
- Assembly laden vanuit module base-pad voordat u probeert te laden vanuit de GAC (#8073)
- Tilde uit Linux preview packages verwijderen (#8244)
- Verwerking van `-WorkingDirectory` vóór verwerking van profielen verplaatsen (#8079)
- Geen `PATHEXT` omgevings variabele toevoegen op UNIX (#7697) (bedankt @iSazonov !)

## <a name="known-issues"></a>Bekende problemen

- Externe toegang op Windows IOT arm-platforms heeft een probleem met het laden van modules. Zie (#8053)

## <a name="general-updates-and-fixes"></a>Algemene updates en oplossingen

- Niet-hoofdletter gevoelige tabblad voltooiing inschakelen voor bestanden en mappen op hoofdletter gevoelig bestands systeem (#8128)
- Maak PSVersionInfo. PSVersion en PSVersionInfo. PSEdition openbaar (#8054) (bedankt @KirkMunro !)
- Type in-demijner toevoegen voor `$_`  /  `$PSItem` in `catch{ }` blokken (#8020) (bedankt @vexx32 !)
- Een statische methode voor het aanroepen van het aanroep type herstellen (#8018) (bedankt @SeeminglyScience !)
- Maak een afgeleid type voor `Select-Object` , `Group-Object` , **PSObject** en **hashtabel** (#7231) (bedankt @powercode !)
- Ondersteuning voor het aanroepen van methoden met `ByRef-like` type parameters (#7721)
- De aanvraag afhandelen waarbij het pad naar de Windows Power shell-module al aanwezig is in de PSModulePath van de omgeving (#7727)
- Schakel `SecureString` cmdlets voor niet-Windows in door de tekst zonder opmaak (#9199) op te slaan
- Fout bericht op niet-Windows verbeteren bij het importeren van clixml met securestring (#7997)
- Para meter ReplyTo toevoegen aan `Send-MailMessage` (#8727) (bedankt @replicaJunction !)
- Verouderd bericht toevoegen aan `Send-MailMessage` (#9178)
- Fix `Restart-Computer` om te werken `localhost` Wanneer WinRM niet aanwezig is (#9160)
- Fout bij het afbreken van de `Start-Job` afsluiting wanneer Power shell wordt gehost (#9128)
- Voeg accelerators en achtervoegsels voor C#-stijl typen toe voor USHORT, uint, ULONG en short letterlijke tekens (#7813) (bedankt @vexx32 !)
- Nieuwe achtervoegsels toegevoegd voor numerieke letterlijke waarden-Zie [about_Numeric_Literals][] (#7901) (bedankt @vexx32 !)
- Het niveau van de impact op de juiste manier rapporteren wanneer SupportsShouldProcess niet is ingesteld op True (#8209) (bedankt @vexx32 !)
- Problemen met de aanvraag-charset in Web-cmdlets (#8742) oplossen (bedankt @markekraus !)
- Verhelp het `100-continue` probleem met Web-cmdlets (#8679) (bedankt @markekraus !)
- Problemen met het blok keren van bestanden met Web-cmdlets (#7676) oplossen (bedankt @Claustn !)
- Probleem met het parseren van code pagina in `Invoke-RestMethod` (#8694) oplossen (bedankt @markekraus !)
- Refactorion `ConvertTo-Json` om JsonObject. ConvertToJson beschikbaar te maken als een open bare API (#8682)
- Configureer bare maximale diepte toevoegen in `ConvertFrom-Json` met-Depth (#8199) (bedankt @louistio !)
- De para meter EscapeHandling toevoegen in de `ConvertTo-Json` cmdlet (#7775) (bedankt @iSazonov !)
- Toevoegen `-CustomPipeName` aan pwsh en `Enter-PSHostProcess` (#8889)
- Het maken van relatieve symbolische koppelingen in Windows inschakelen met `New-Item` (#8783)
- Toestaan dat Windows-gebruikers in de ontwikkelaars modus symlinks maken zonder uitbrei ding (#8534)
- Inschakelen `Write-Information` om te accepteren `$null` (#8774)
- Oplossing `Get-Help` voor geavanceerde functies met MAML Help-inhoud (#8353)
- `Get-Help`PSTypeName probleem met-para meter oplossen wanneer er slechts één para meter is gedeclareerd (#8754) (hartelijk dank @pougetat !)
- Correctie van token berekening voor `Get-Help` uitgevoerd op script Block voor Help bij opmerkingen. (#8238) (Bedankt @hubuk !)
- Wijzig de `Get-Help` para meter cmdlet-para meter zodat deze teken reeks matrices accepteert (#8454) (bedankt @sethvs !)
- PAGINERING omzetten als het pad spaties bevat (#8571) (bedankt @pougetat !)
- Voeg een prompt toe voor het gebruik van `less` in de functie Help om gebruikers te instrueren hoe ze moeten worden afgesloten (#7998)
- Ondersteuning voor Enum en char-typen toevoegen in de `Format-Hex` cmdlet (#8191) (bedankt @iSazonov !)
- Verwijder ShouldProcess uit `Format-Hex` (#8178)
- Nieuwe para meters voor offset en aantal toevoegen aan `Format-Hex` en refactorion de cmdlet (#7877) (bedankt @iSazonov !)
- ' Name ' toestaan als een alias sleutel voor ' label ' in `ConvertTo-Html` , staat de vermelding ' width ' toe als geheel getal (#8426) (bedankt @mklement0 !)
- Maak op script Block gebaseerde berekende eigenschappen opnieuw in `ConvertTo-Html` (#8427) (bedankt @mklement0 !)
- Cmdlet toevoegen `Join-String` voor het maken van tekst vanuit pijplijn invoer (#7660) (bedankt @powercode !)
- De `Join-String` para meter Logic van cmdlet formats (#8449) oplossen (bedankt @sethvs !)
- Ga `Clear-Host` terug naar met `$RAWUI` en wissen om te werken via externe communicatie (#8609)
- Wijzigen `Clear-Host` in simpelweg de `[console]::clear` alias wissen en verwijderen van Unix (#8603)
- Herstel LiteralPath in `Import-Csv` om te verbinden met de `Get-ChildItem` uitvoer (#8277) (bedankt @iSazonov !)
- Help-functie mag paginering niet gebruiken voor AliasHelpInfo (#8552)
- Voeg toe `-UseMinimalHeader` aan `Start-Transcript` om de transcript header (#8402) te minimaliseren (bedankt @lukexjeremy !)
- Add `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature` cmdlets (#8318)
- Alle cmdlets beschikbaar maken op basis van **PSDiagnostics** als logman.exe is (#8366)
- **Persistente** para meter verwijderen van `New-PSDrive` op `non-Windows` platform (#8291) (bedankt @lukexjeremy !)
- Voeg ondersteuning toe voor `cd +` (#7206) (bedankt @bergmeister !)
- Inschakelen `Set-Location -LiteralPath` om te werken met mappen met de naam-en + (#8089)
- `Test-Path` retourneert `$false` Wanneer een lege waarde of een `$null` pad (#8080) wordt gegeven (hartelijk dank @vexx32 !)
- De dynamische para meter mag worden geretourneerd, zelfs als het pad niet overeenkomt met een provider (#7957)
- Ondersteuning `Get-PSHostProcessInfo` en `Enter-PSHostProcess` op UNIX-platforms (#8232)
- Toewijzingen reduceren in `Get-Content` cmdlet (#8103) (bedankt @iSazonov !)
- Inschakelen `Add-Content` om Lees toegang te delen met andere hulpprogram ma's tijdens het schrijven van inhoud (#8091)
- `Get/Add-Content` genereert een verbeterde fout bij het richten op een container (#7823) (bedankt @kvprasoon !)
- Toevoegen `-Name` `-NoUserOverrides` en `-ListAvailable` para meters voor `Get-Culture` cmdlet (#7702) (bedankt @iSazonov !)
- Voeg een uniform kenmerk toe voor het volt ooien van de **coderings** parameter. (#7732) (Bedankt @ThreeFive-O !)
- Numerieke Id's en de naam van geregistreerde code pagina's in **coderings** parameters (#7636) toestaan (bedankt @iSazonov !)
- Oplossen `Rename-Item -Path` met Joker tekens (#7398) (bedankt @kwkam !)
- Wanneer u `Start-Transcript` en file exists gebruikt, is een leeg bestand in plaats van verwijderen (#8131) (bedankt @paalbra !)
- `Add-Type`Open-source bestanden maken met **FileAccess. Read** en **file share. expliciet lezen** (#7915) (bedankt @IISResetMe !)
- Herstellen `Enter-PSSession -ContainerId` voor de nieuwste versie van Windows (#7883)
- Zorg ervoor dat de eigenschap **NestedModules** wordt gevuld door `Test-ModuleManifest` (#7859)
- `%F`Case toevoegen aan `Get-Date` -UFormat (#7630) (bedankt @britishben !)
- Oplossing `Set-Service -Status Stopped` voor het stoppen van services met afhankelijkheden (#5525) (bedankt @zhenggu !)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
