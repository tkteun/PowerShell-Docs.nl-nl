---
title: Wat is er nieuw in Power shell Core 6,2
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,2
ms.date: 03/28/2019
ms.openlocfilehash: 2f5f5d11ba46d53966093c5e3ed6d0c7d47308d0
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737131"
---
# <a name="whats-new-in-powershell-core-62"></a>Wat is er nieuw in Power shell Core 6,2

De Power shell Core 6,2-release is gericht op verbeteringen in prestaties, fout oplossingen en kleinere cmdlet-en taal uitbreidingen waarmee de kwaliteit wordt verbeterd. Bekijk onze gedetailleerde [changelogs](https://github.com/PowerShell/PowerShell/releases) op github voor een volledige lijst met verbeteringen.

## <a name="experimental-features"></a>Experimentele functies

Voorheen hebben we ondersteuning voor [experimentele functies][]ingeschakeld. In de 6,2-release hebben we vier experimentele functies nodig om uit te proberen. Geef feedback zodat we verbeteringen kunnen aanbrengen en bepalen of de functie van belang is voor de status van de standaard.

Gebruik `Get-ExperimentalFeature` om een lijst met beschik bare experimentele functies op te halen. U kunt deze functies in-of uitschakelen met `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature`.

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

Met deze functie analyseert Power shell de pijp lijn om te bepalen of de opdracht veilig kan worden uitgevoerd en op het doel systeem. Als deze eigenschap waar is, wordt de volledige pijp lijn op afstand uitgevoerd en worden alleen de resultaten van de client `de-serializes`.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Een praktijk test van `Get-Process | Sort-Object` over localhost neemt af van 10-15 seconden tot 20-30 **milliseconden**. De functie moet alleen worden ingeschakeld op de client. Er zijn geen wijzigingen vereist op de server.

### <a name="temp-drive"></a>Tijdelijk station

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Als u Power shell Core gebruikt op verschillende besturings systemen, detecteert u dat de omgevings variabele voor het vinden van de tijdelijke map anders is in Windows, macOS en Linux. Met deze functie krijgt u een [PSDrive][] met de naam `Temp:` die automatisch wordt toegewezen aan de tijdelijke map voor het besturings systeem dat u gebruikt.

#### <a name="example"></a>Voorbeeld

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

Houd er rekening mee dat systeem eigen bestands opdrachten (zoals `ls` op Linux) niet op de hoogte zijn van PSDrives en dit `Temp:` station niet te zien.

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

- Herstel `-NoEnumerate` gedrag in `Write-Output` consistent te zijn met Windows Power shell. (#9069)
- `Join-String -InputObject 1,2,3` resultaat gelijk maken aan `1,2,3 | Join-String` resultaat (#8611) (Bedankt @sethvs!)
- `-Stable` toevoegen aan `Sort-Object` en gerelateerde tests (#7862) (Bedankt @KirkMunro!)
- `Start-Sleep`-cmdlet verbeteren om breuk seconden (#8537) te accepteren (Bedankt @Prototyyppi!)
- Wijzig de hashtabel zodanig dat OrdinalIgnoreCase wordt gebruikt voor de `case-insensitive` in alle cult uren (#8566)
- Herstel **LiteralPath** in `Import-Csv` om verbinding te maken met `Get-ChildItem`-uitvoer (#8277) (Bedankt @iSazonov!)
- Slaat geen kolom zonder naam over als dubbele aanhalings tekens worden gebruikt in `Import-Csv` (#7899) (Bedankt @Topping!)
- `Get-ExperimentalFeature` heeft niet langer `-ListAvailable` switch (#8318)
- Met de para meter debug wordt nu `$DebugPreference` ingesteld om **door te gaan** in plaats van op te **vragen** (#8195) (Bedankt @KirkMunro!)
- Respect `-OutputFormat` indien opgegeven in niet-interactieve, omgeleide, gecodeerde opdracht die wordt gebruikt met pwsh (#8115)
- Assembly laden vanuit module base-pad voordat u probeert te laden vanuit de GAC (#8073)
- Tilde uit Linux preview packages verwijderen (#8244)
- Verwerking van `-WorkingDirectory` vóór het verwerken van profielen verplaatsen (#8079)
- Voeg `PATHEXT` omgevings variabele niet toe op UNIX (#7697) (Bedankt @iSazonov!)

## <a name="known-issues"></a>Bekende problemen

- Externe toegang op Windows IOT ARM-platforms heeft een probleem met het laden van modules. Zie (#8053)

## <a name="general-updates-and-fixes"></a>Algemene updates en oplossingen

- Niet-hoofdletter gevoelige tabblad voltooiing inschakelen voor bestanden en mappen op hoofdletter gevoelig bestands systeem (#8128)
- Maak PSVersionInfo. PSVersion en PSVersionInfo. PSEdition openbaar (#8054) (Bedankt @KirkMunro!)
- Type demijner voor `$_` / `$PSItem` in `catch{ }` blokken (#8020) toevoegen (Bedankt @vexx32!)
- Een statische methode voor het aanroepen van het aanroep type herstellen (#8018) (Bedankt @SeeminglyScience!)
- Maak een afgeleid type voor `Select-Object`, `Group-Object`, **PSObject** en **hashtabel** (#7231) (Bedankt @powercode!)
- Ondersteuning voor het aanroepen van methoden met `ByRef-like` type para meters (#7721)
- De aanvraag afhandelen waarbij het pad naar de Windows Power shell-module al aanwezig is in de PSModulePath van de omgeving (#7727)
- `SecureString`-cmdlets voor niet-Windows inschakelen door het onbewerkte tekst (#9199) op te slaan
- Fout bericht op niet-Windows verbeteren bij het importeren van clixml met securestring (#7997)
- Para meter ReplyTo toevoegen aan `Send-MailMessage` (#8727) (Bedankt @replicaJunction!)
- Verouderd bericht toevoegen aan `Send-MailMessage` (#9178)
- `Restart-Computer` oplossen om te werken aan `localhost` wanneer WinRM niet aanwezig is (#9160)
- Fout bij het beëindigen van `Start-Job` genereren wanneer Power shell wordt gehost (#9128)
- Stijl C# typen accelerators en achtervoegsels voor USHORT, uint, ULONG en short letterlijke tekens (#7813) toevoegen (Bedankt @vexx32!)
- Nieuwe achtervoegsels toegevoegd voor numerieke letterlijke waarden-Zie [about_Numeric_Literals][] (#7901) (Bedankt @vexx32!)
- Het niveau van de impact op de juiste manier rapporteren wanneer SupportsShouldProcess niet is ingesteld op True (#8209) (Bedankt @vexx32!)
- Problemen met de aanvraag-charset oplossen in Web-cmdlets (#8742) (Bedankt @markekraus!)
- Voor de oplossing wordt een probleem `100-continue` met Web-cmdlets (#8679) (Bedankt @markekraus!)
- Problemen met het blok keren van bestanden met Web-cmdlets (#7676) oplossen (Bedankt @Claustn!)
- Het parseren van de code pagina in `Invoke-RestMethod` (#8694) oplossen (Bedankt @markekraus!)
- Refactory `ConvertTo-Json` om JsonObject. ConvertToJson beschikbaar te maken als een open bare API (#8682)
- Configureer bare maximale diepte toevoegen in `ConvertFrom-Json` met-Depth (#8199) (Bedankt @louistio!)
- De para meter EscapeHandling toevoegen in `ConvertTo-Json`-cmdlet (#7775) (Bedankt @iSazonov!)
- `-CustomPipeName` toevoegen aan pwsh en `Enter-PSHostProcess` (#8889)
- Het maken van relatieve symbolische koppelingen in Windows inschakelen met `New-Item` (#8783)
- Toestaan dat Windows-gebruikers in de ontwikkelaars modus symlinks maken zonder uitbrei ding (#8534)
- `Write-Information` accepteren `$null` (#8774)
- `Get-Help` herstellen voor geavanceerde functies met MAML Help-inhoud (#8353)
- Herstel `Get-Help` PSTypeName-probleem met-para meter wanneer er slechts één para meter is gedeclareerd (#8754) (hartelijk dank @pougetat!)
- Correctie van token berekening voor `Get-Help` uitgevoerd op script Block voor opmerkings hulp. (#8238) (Bedankt @hubuk!)
- Wijzig `Get-Help` cmdlet para meter parameter zodat deze teken reeks matrices (#8454) accepteert (Bedankt @sethvs!)
- PAGINERING omzetten als het pad spaties bevat (#8571) (Bedankt @pougetat!)
- Voeg een prompt toe voor het gebruik van `less` in de functie Help om gebruikers te instrueren hoe ze moeten worden afgesloten (#7998)
- Voeg ondersteuning toe voor Enum en char-typen in `Format-Hex`-cmdlet (#8191) (Bedankt @iSazonov!)
- ShouldProcess verwijderen uit `Format-Hex` (#8178)
- Voeg nieuwe para meters voor offset en aantal toe aan `Format-Hex` en refactorion de cmdlet (#7877) (hartelijk dank @iSazonov!)
- ' Name ' toestaan als een alias sleutel voor ' label ' in `ConvertTo-Html`, de vermelding ' width ' toestaan als geheel getal (#8426) (Bedankt @mklement0!)
- Zorg dat berekende eigenschappen op basis van script Block opnieuw werken in `ConvertTo-Html` (#8427) (Bedankt @mklement0!)
- `Join-String` cmdlet toevoegen voor het maken van tekst van pijplijn invoer (#7660) (Bedankt @powercode!)
- `Join-String`-cmdlets parameter Logic (#8449) herstellen (Bedankt @sethvs!)
- `Clear-Host` opnieuw instellen op het gebruik van `$RAWUI` en wissen om te werken via externe toegang (#8609)
- Wijzig `Clear-Host` in simpelweg de naam `[console]::clear` en verwijder de duidelijke alias van UNIX (#8603)
- Herstel LiteralPath in `Import-Csv` om verbinding te maken met `Get-ChildItem`-uitvoer (#8277) (Bedankt @iSazonov!)
- Help-functie mag paginering niet gebruiken voor AliasHelpInfo (#8552)
- Voeg `-UseMinimalHeader` toe aan `Start-Transcript` om de transcript header (#8402) te minimaliseren (Bedankt @lukexjeremy!)
- `Enable-ExperimentalFeature`-en `Disable-ExperimentalFeature`-cmdlets toevoegen (#8318)
- Alle cmdlets weer geven vanuit **PSDiagnostics** als logman. exe beschikbaar is (#8366)
- Verwijder de **persistente** para meter uit `New-PSDrive` op `non-Windows` platform (#8291) (Bedankt @lukexjeremy!)
- Voeg ondersteuning toe voor `cd +` (#7206) (Bedankt @bergmeister!)
- Schakel `Set-Location -LiteralPath` in om te werken met mappen met de naam-en + (#8089)
- `Test-Path` retourneert `$false` wanneer het een lege waarde of een `$null` padwaarde (#8080) heeft gegeven (Bedankt @vexx32!)
- De dynamische para meter mag worden geretourneerd, zelfs als het pad niet overeenkomt met een provider (#7957)
- Ondersteuning voor `Get-PSHostProcessInfo` en `Enter-PSHostProcess` op UNIX-platforms (#8232)
- Verlaag toewijzingen in `Get-Content`-cmdlet (#8103) (Bedankt @iSazonov!)
- Inschakelen dat `Add-Content` Lees toegang met andere hulpprogram ma's kunt delen tijdens het schrijven van inhoud (#8091)
- `Get/Add-Content` genereert een verbeterde fout bij het richten op een container (#7823) (hartelijk dank @kvprasoon!)
- `-Name`-, `-NoUserOverrides`-en `-ListAvailable`-para meters toevoegen aan `Get-Culture`-cmdlet (#7702) (Bedankt @iSazonov!)
- Voeg een uniform kenmerk toe voor het volt ooien van de **coderings** parameter. (#7732) (Bedankt @ThreeFive-O!)
- Numerieke Id's en de naam van geregistreerde code pagina's toestaan in **coderings** parameters (#7636) (Bedankt @iSazonov!)
- Herstel `Rename-Item -Path` met Joker teken (#7398) (Bedankt @kwkam!)
- Wanneer u `Start-Transcript` en het bestand exists gebruikt, is dit een leeg bestand in plaats van het verwijderen (#8131) (Bedankt @paalbra!)
- `Add-Type` open source-bestanden maken met **FileAccess. Read** en **file share. expliciet lezen** (#7915) (Bedankt @IISResetMe!)
- `Enter-PSSession -ContainerId` voor de nieuwste versie van Windows (#7883) herstellen
- Zorg ervoor dat de eigenschap **NestedModules** wordt gevuld door `Test-ModuleManifest` (#7859)
- Voeg `%F` Case toe aan `Get-Date`-UFormat (#7630) (Bedankt @britishben!)
- Herstel `Set-Service -Status Stopped` om services te stoppen met afhankelijkheden (#5525) (Bedankt @zhenggu!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
