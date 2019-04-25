---
title: Wat is er nieuw in PowerShell Core 6.2
description: Nieuwe functies en wijzigingen die zijn uitgebracht in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058094"
---
# <a name="whats-new-in-powershell-core-62"></a>Wat is er nieuw in PowerShell Core 6.2

De PowerShell Core 6.2-versie gericht op verbeteringen in queryprestaties, oplossingen voor problemen en kleinere-cmdlet en taal-uitbreidingen ter verbetering van de kwaliteit. Een volledige lijst van de verbeteringen wilt bekijken, Bekijk onze gedetailleerde [changelogs](https://github.com/PowerShell/PowerShell/releases) op GitHub.

## <a name="experimental-features"></a>Experimentele functies

Eerder moesten we ondersteuning voor ingeschakeld [experimentele functies][]. In de 6.2 release hebben we vier experimentele functies om uit te proberen. Geef feedback, zodat we verbeteringen kunnen maken en om te bepalen of de functie is waard is om bevordering van de algemene status.

Gebruik `Get-ExperimentalFeature` voor een lijst van beschikbare experimentele functies. U kunt inschakelen of uitschakelen van deze functies met `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature`.

### <a name="command-not-found-suggestions"></a>Kan de opdracht niet vinden suggesties

Deze functie maakt gebruik van zoeken bij benadering suggesties voor opdrachten of -cmdlets die u hebt misschien vinden.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>Voorbeeld

In dit voorbeeld wordt is de verkeerd gespelde cmdlet-naam fuzzy enkele suggesties overeenkomende van waarschijnlijk minste waarschijnlijk.

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

### <a name="implicit-remoting-batching"></a>Impliciete externe communicatie via batchverwerking uitvoeren

Bij het gebruik van [impliciete externe communicatie](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in een pijplijn, behandelt PowerShell elke opdracht in de pijplijn onafhankelijk van elkaar. Objecten herhaaldelijk worden geserialiseerd en `de-serialized` tussen de client en het externe systeem over de uitvoering van de pijplijn.

Met deze functie analyseert PowerShell de pijplijn om te bepalen van de opdracht is veilig om te worden uitgevoerd als deze bestaat op het doelsysteem. Indien waar, PowerShell, de hele pijplijn op afstand wordt uitgevoerd en alleen serialiseert en `de-serializes` de resultaten terug naar de client.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

Een test op echte `Get-Process | Sort-Object` via localhost afneemt van 10-15 seconden naar 20-30 **milliseconden**. De functie moet alleen worden ingeschakeld op de client. Er zijn geen wijzigingen zijn vereist op de server.

### <a name="temp-drive"></a>Temp Drive

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

Als u PowerShell Core op verschillende besturingssystemen, zult u ontdekken dat de omgevingsvariabele voor het vinden van de tijdelijke map anders in Windows, macOS en Linux is! Met deze functie krijgt u een [PSDrive][] met de naam `Temp:` die automatisch is toegewezen aan de tijdelijke map voor het besturingssysteem die u gebruikt.

#### <a name="example"></a>Voorbeeld

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

Houd er rekening mee dat opdrachten in het oorspronkelijke bestand (zoals `ls` op Linux) zijn niet op de hoogte van PSDrives en ziet deze niet `Temp:` station.

### <a name="abbreviation-expansion"></a>Afkorting-uitbreiding

PowerShell-cmdlets worden verwacht beschrijvende woorden. Dit resulteert in lange namen die moeilijker zijn te typen. Deze functie kunt u alleen de hoofdletters van de cmdlet typt en tab-aanvulling gebruiken om een overeenkomst te vinden.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>Voorbeeld

```powershell
PS> i-arsavsf
```

Als u druk op tab en de Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module zijn geïnstalleerd, wordt automatisch aanvullen voor:

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> Deze functie is bedoeld voor interactief. Verkorte vorm van cmdlets kunnen niet worden uitgevoerd.
> Deze functie is geen vervanging voor aliassen.

## <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

- Los `-NoEnumerate` gedrag in `Write-Output` moet consistent zijn met Windows PowerShell. (#9069)
- Controleer `Join-String -InputObject 1,2,3` resultaat gelijk is aan `1,2,3 | Join-String` leiden tot (#8611) (Bedankt @sethvs!)
- Toevoegen `-Stable` naar `Sort-Object` en gerelateerde tests (#7862) (Bedankt @KirkMunro!)
- Verbeteren `Start-Sleep` cmdlet precisiewaarde accepteren (#8537) (Bedankt @Prototyyppi!)
- Wijzigen van de hashtabel OrdinalIgnoreCase gebruiken om u te worden `case-insensitive` in alle culturen (#8566)
- Los **LiteralPath** in `Import-Csv` binden aan `Get-ChildItem` uitvoer (#8277) (Bedankt @iSazonov!)
- Een kolom zonder naam niet meer wordt overgeslagen als dubbel aanhalingsteken scheidingsteken wordt gebruikt in `Import-Csv` (#7899) (Bedankt @Topping!)
- `Get-ExperimentalFeature` heeft niet langer `-ListAvailable` overschakelen (#8318)
- Fouten opsporen in nu parametersets `$DebugPreference` naar **doorgaan** in plaats van **opvragen** (#8195) (Bedankt @KirkMunro!)
- Honor `-OutputFormat` als opgegeven in niet-interactieve, omgeleide, gecodeerde opdracht die wordt gebruikt met pwsh (#8115)
- Laden van assembly uit module basispad voordat u probeert te laden vanuit de GAC (#8073)
- Tilde verwijderen uit Linux preview-pakketten (#8244)
- Verplaats verwerkingstaken van `-WorkingDirectory` voorafgaand aan de verwerking van profielen (#8079)
- Voeg geen `PATHEXT` omgevingsvariabele op Unix (#7697) (Bedankt @iSazonov!)

## <a name="known-issues"></a>Bekende problemen

- Op ARM voor Windows-IOT-platformen voor externe toegang is een probleem dat het laden van modules. Zie (#8053)

## <a name="general-updates-and-fixes"></a>Algemene Updates en oplossingen

- Niet-hoofdlettergevoelige tab-aanvulling voor bestanden en mappen op hoofdlettergevoelig bestandssysteem inschakelen (#8128)
- PSVersionInfo.PSVersion en PSVersionInfo.PSEdition openbaar maken (#8054) (Bedankt @KirkMunro!)
- Toevoegen van Type Deductie voor `$_`  /  `$PSItem` in `catch{ }` (#8020) blokkeert (Bedankt @vexx32!)
- Statische methode aanroepen type Deductie oplossen (#8018) (Bedankt @SeeminglyScience!)
- Maken van afgeleide typen voor `Select-Object`, `Group-Object`, **PSObject** en **hashtabel** (#7231) (Bedankt @powercode!)
- Ondersteuning voor de aanroepende methode met `ByRef-like` Typ parameters (#7721)
- Wanneer het pad van Windows PowerShell-module is al in de omgeving PSModulePath verwerken (#7727)
- Schakel `SecureString` -cmdlets voor Windows door op te slaan van de tekst zonder opmaak (#9199)
- Foutbericht bij niet-Windows verbeteren bij het importeren van clixml met securestring (#7997)
- Parameter ReplyTo toe te voegen aan `Send-MailMessage` (#8727) (Bedankt @replicaJunction!)
- Verouderd bericht toevoegen `Send-MailMessage` (#9178)
- Los `Restart-Computer` om te werken op `localhost` wanneer WinRM is niet aanwezig (#9160)
- Controleer `Start-Job` throw afsluitfout wanneer PowerShell wordt gehost (#9128)
- Voeg C# style type accelerators en achtervoegsels voor ushort, uint, ulong en korte letterlijke waarden (#7813) (Bedankt @vexx32!)
- Toegevoegde nieuwe achtervoegsels voor numerieke letterlijke waarden - Zie [about_Numeric_Literals][] (#7901) (Bedankt @vexx32!)
- Niveau van impact correct rapporteren wanneer SupportsShouldProcess niet is ingesteld op 'true' (#8209) (Bedankt @vexx32!)
- Aanvraag tekenset problemen oplossen in Web-Cmdlets (#8742) (Bedankt @markekraus!)
- Los Expect `100-continue` probleem met Web-Cmdlets (#8679) (Bedankt @markekraus!)
- Bestand blokkerend probleem herstellen met de web-cmdlets (#7676) (Bedankt @Claustn!)
- Codepagina bij het parseren van het probleem in herstellen `Invoke-RestMethod` (#8694) (Bedankt @markekraus!)
- Herstructureren `ConvertTo-Json` blootstellen JsonObject.ConvertToJson als een openbare API (#8682)
- Configureerbare maximale diepte in toe te voegen `ConvertFrom-Json` met - diepte (#8199) (Bedankt @louistio!)
- Toevoegen van de parameter EscapeHandling in `ConvertTo-Json` cmdlet (#7775) (Bedankt @iSazonov!)
- Voeg `-CustomPipeName` naar pwsh en `Enter-PSHostProcess` (#8889)
- Inschakelen op Windows met het maken van relatieve symbolische koppelingen `New-Item` (#8783)
- Toestaan dat gebruikers van Windows in de modus voor ontwikkelaars symlinks zonder misbruik te maken (#8534)
- Schakel `Write-Information` accepteren `$null` (#8774)
- Los `Get-Help` voor geavanceerde functies met MAML help-inhoud (#8353)
- Los `Get-Help` PSTypeName probleem met de - Parameter wanneer slechts één parameter wordt gedefinieerd (#8754) (Bedankt @pougetat!)
- Token berekening correctie voor `Get-Help` uitgevoerd op ScriptBlock voor meer informatie over opmerking. (#8238) (Bedankt @hubuk!)
- Wijziging `Get-Help` cmdlet-Parameter parameter, zodat deze tekenreeks accepteert matrices (#8454) (Bedankt @sethvs!)
- Los PAGER als het pad bevat spaties (#8571) (Bedankt @pougetat!)
- Vragen toevoegen aan het gebruik van `less` in de functie 'help' voor de registratie door de gebruikers (#7998) afsluiten
- Toevoegen van ondersteuning voor enum en char typen in `Format-Hex` cmdlet (#8191) (Bedankt @iSazonov!)
- Verwijderen van shouldprocess wordt overgeslagen van `Format-Hex` (#8178)
- Toevoegen van nieuwe Offset en aantal parameters voor `Format-Hex` en herstructureren van de cmdlet (#7877) (Bedankt @iSazonov!)
- Toestaan dat 'name' als een alias-sleutel voor 'label' in `ConvertTo-Html`, toestaan dat de vermelding 'breedte' moet een geheel getal (#8426) (Bedankt @mklement0!)
- Controleer scriptblock op basis van berekende eigenschappen weer werkt `ConvertTo-Html` (#8427) (Bedankt @mklement0!)
- Cmdlet toegevoegd `Join-String` voor het maken van de tekst van de pijplijn (#7660) invoeren (Bedankt @powercode!)
- Los `Join-String` cmdlet FormatString parameter logica (#8449) (Bedankt @sethvs!)
- Wijziging `Clear-Host` terug op het gebruik `$RAWUI` en wissen om te werken via externe toegang (#8609)
- Wijziging `Clear-Host` gewoon aangeroepen `[console]::clear` en duidelijke alias verwijderen van Unix (#8603)
- Los LiteralPath in `Import-Csv` binden aan `Get-ChildItem` uitvoer (#8277) (Bedankt @iSazonov!)
- Help-functie pager voor AliasHelpInfo al dan niet mogen gebruiken (#8552)
- Toevoegen `-UseMinimalHeader` naar `Start-Transcript` transcript header minimaliseren (#8402) (Bedankt @lukexjeremy!)
- Voeg `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature` cmdlets (#8318)
- Alle cmdlets van blootstellen **PSDiagnostics** als logman.exe beschikbaar (#8366)
- Verwijder **Persist** parameter van `New-PSDrive` op `non-Windows` platform (#8291) (Bedankt @lukexjeremy!)
- Voeg ondersteuning toe voor `cd +` (#7206) (Bedankt @bergmeister!)
- Schakel `Set-Location -LiteralPath` om te werken met mappen met de naam - en + (#8089)
- `Test-Path` retourneert `$false` bij een lege of `$null` pad waarde (#8080) (Bedankt @vexx32!)
- Dynamische parameter moet worden geretourneerd, zelfs als het pad komt niet overeen met alle elke provider toestaan (#7957)
- Ondersteuning voor `Get-PSHostProcessInfo` en `Enter-PSHostProcess` op Unix-platforms (#8232)
- Toewijzingen in verminderen `Get-Content` cmdlet (#8103) (Bedankt @iSazonov!)
- Schakel `Add-Content` leestoegang delen met andere hulpprogramma's tijdens het schrijven van inhoud (#8091)
- `Get/Add-Content` Verbeterde fout genereert wanneer die gericht is op een container (#7823) (Bedankt @kvprasoon!)
- Voeg `-Name`, `-NoUserOverrides` en `-ListAvailable` parameters `Get-Culture` cmdlet (#7702) (Bedankt @iSazonov!)
- Geïntegreerde kenmerk voor de voltooiing voor toevoegen **Encoding** parameter. (#7732) (Bedankt @ThreeFive-O!)
- Toestaan dat de numerieke id's en de naam van de geregistreerde codetabellen in **Encoding** parameters (#7636) (Bedankt @iSazonov!)
- Los `Rename-Item -Path` met jokertekens char (#7398) (Bedankt @kwkam!)
- Bij het gebruik van `Start-Transcript` en bestand aanwezig is, leeg bestand in plaats daarvan zijn dan (#8131) verwijderen (Bedankt @paalbra!)
- Controleer `Add-Type` open source-bestanden met **FileAccess.Read** en **FileShare.Read** expliciet (#7915) (Bedankt @IISResetMe!)
- Los `Enter-PSSession -ContainerId` voor de meest recente Windows (#7883)
- Zorg ervoor dat **NestedModules** eigenschap wordt gevuld door `Test-ModuleManifest` (#7859)
- Voeg `%F` case te `Get-Date` - UFormat (#7630) (Bedankt @britishben!)
- Los `Set-Service -Status Stopped` met afhankelijkheden-services stoppen (#5525) (Bedankt @zhenggu!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
