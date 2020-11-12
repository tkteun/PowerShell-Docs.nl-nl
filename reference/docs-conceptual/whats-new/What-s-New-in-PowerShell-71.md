---
title: Wat is er nieuw in Power shell 7,1
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell 7,1
ms.date: 11/11/2020
ms.openlocfilehash: 720fd3eae3e79ee5ab82b7b35d83b6c9b054617b
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/12/2020
ms.locfileid: "94531805"
---
# <a name="whats-new-in-powershell-71"></a>Wat is er nieuw in Power shell 7,1

Power shell 7,1 is een open-source, platformoverschrijdende versie van het platform (Windows, macOS en Linux) van Power shell, gebouwd voor het beheren van heterogene omgevingen en hybride Cloud.

Voortbouwend op de basis die is vastgesteld in Power shell 7,0, onze inspanningen gericht op problemen van de community en bevatten een aantal verbeteringen en oplossingen. We streven ernaar om ervoor te zorgen dat Power shell een stabiel en het beste platform blijft.

## <a name="where-can-i-install-powershell"></a>Waar kan ik Power Shell installeren?

Power shell 7,1 ondersteunt momenteel de volgende besturings systemen op x64, waaronder:

- Windows 8,1 en 10
- Windows Server 2012 R2, 2016 en 2019
- macOS 10.13 +
- Red Hat Enterprise Linux (RHEL)/CentOS 7 en 8
- Debian 9 en 10
- Ubuntu 18,04 en 20,04
- Alpine Linux 3,10 en 3.11 +

Zie de [Power shell-ondersteunings levenscyclus](/powershell/scripting/powershell-support-lifecycle) voor meer actuele informatie over de ondersteunde besturings systemen en de levens cyclus van de ondersteuning.

Power shell 7,1 is gepubliceerd op de Microsoft Store. U kunt de Power shell-release vinden op de [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website of in de Store-toepassing in Windows.

Voor delen van het Microsoft Store-pakket:

- Automatische updates zijn direct in Windows 10 ingebouwd
- Kan worden geïntegreerd met andere software distributie mechanismen, zoals intune en SCCM

> [!NOTE]
> Alle configuratie-instellingen op systeem niveau die zijn opgeslagen in, `$PSHOME` kunnen niet worden gewijzigd. Dit omvat de WSMAN-configuratie. Hiermee voor komt u dat externe sessies verbinding maken met op opslag gebaseerde installaties van Power shell. Configuraties op gebruikers niveau en externe SSH-communicatie worden ondersteund.

Controleer de installatie-instructies voor uw voorkeurs besturings systeem:

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [MacOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

Daarnaast ondersteunt Power shell 7,1 ARM32-en ARM64-smaakten van Debian, Ubuntu en ARM64 Alpine Linux.

Hoewel niet officieel wordt ondersteund, heeft de community ook pakketten voor [Arch](https://aur.archlinux.org/packages/powershell/) en Kali Linux verschaft.

> [!NOTE]
> Debian 10 +, CentOS 8 +, Ubuntu 20,04, alpine en arm bieden momenteel geen ondersteuning voor externe toegang via WinRM. Zie voor meer informatie over het instellen van op SSH gebaseerde externe communicatie [Power shell voor externe toegang via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

## <a name="running-powershell-71"></a>Power shell 7,1 wordt uitgevoerd

Power shell 7,1 wordt geïnstalleerd in een nieuwe map en kan naast Windows Power shell 5,1 worden uitgevoerd.
Power shell 7,1 is een in-place upgrade waarmee Power shell 6. x wordt vervangen. of Power shell 7,0.

- Power shell 7,1 is geïnstalleerd voor `%programfiles%\PowerShell\7`
- De `%programfiles%\PowerShell\7` map wordt toegevoegd aan `$env:PATH`

De Power shell 7,1 Installer-pakketten upgraden vorige versies van Power shell Core 6. x:

- Power shell Core 6. x op Windows: `%programfiles%\PowerShell\6` wordt vervangen door `%programfiles%\PowerShell\7`
- Linux: `/opt/microsoft/powershell/6` is vervangen door `/opt/microsoft/powershell/7`
- macOS: `/usr/local/microsoft/powershell/6` wordt vervangen door `/usr/local/microsoft/powershell/7`

> [!NOTE]
> In Windows Power shell heet het uitvoer bare bestand voor het starten van Power shell `powershell.exe` . In versie 6 en hoger wordt het uitvoer bare bestand gewijzigd om gelijktijdige uitvoering te ondersteunen. Het nieuwe uitvoer bare bestand voor het starten van Power shell 7,1 is `pwsh.exe` . Preview-builds blijven in-place, net als in `pwsh-preview` `pwsh` de map 7-Preview.

## <a name="breaking-changes-and-improvements"></a>Wijzigingen en verbeteringen te verbreken

Zie de [wijzigingen logboek](https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG) in de GitHub-opslag plaats voor de meest recente informatie over wijzigingen en verbeteringen.

### <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

<!-- TODO: Add descriptions for each breaking change  -->

- Oplossing `$?` niet wanneer een `$false` systeem eigen opdracht schrijft naar `stderr` (#13395)
- Wijzig de naam in `-FromUnixTime` `-UnixTimeSeconds` `Get-Date` om Unix-tijd invoer (#13084) toe te staan (bedankt @aetos382 !)
- `$ErrorActionPreference`Geen invloed hebben op de `stderr` uitvoer van systeem eigen opdrachten (#13361)
- Een expliciet opgegeven benoemde para meter mag vervangen door de naam van de hashtabel splatting (#13162)
- De para meter voor de switch parameter `-Qualifier` niet positioneel instellen `Split-Path` (#12960) (bedankt @yecril71pl !)
- De werkmap omzetten als letterlijk pad voor `Start-Process` wanneer deze niet is opgegeven (#11946) (bedankt @NoMoreFood !)
- Stel de `-OutFile` para meter in Web-cmdlets als volgt `-LiteralPath` (#11701) (bedankt @iSazonov !)
- Teken reeks parameter binding voor `BigInteger` numerieke letterlijke waarden (#11634) oplossen (bedankt @vexx32 !)
- In Windows `Start-Process` maakt een proces omgeving met alle omgevings variabelen uit de huidige sessie, met behulp van `-UseNewEnvironment` een nieuwe standaard proces omgeving (#10830) (bedankt @iSazonov !)
- Geen omloop retour resultaat bij het `PSObject` converteren van script Block naar Delegate (#10619)
- Gebruik de conversie van de invariante cultuur-teken reeks voor `-replace` operator (#10954) (bedankt @iSazonov !)

### <a name="experimental-features"></a>Experimentele functies

<!-- TODO: note which features are now mainstream  -->

- `-Runspace`Para meter toevoegen aan alle `*-PSBreakpoint` cmdlets (#10492) (bedankt @KirkMunro !)
- Ondersteuning bij het door geven van `PSPath` systeem eigen opdrachten (#12386)
- Gebruik de conversie van de invariante cultuur-teken reeks voor `-replace` operator (#10954) (bedankt @iSazonov !)

### <a name="general-cmdlet-updates-and-fixes"></a>Algemene cmdlet-updates en-oplossingen

- Waarschuwing verzenden als `ConvertTo-Json` overschrijdt `-Depth` waarde (#13692)
- Herstellen wanneer uitzonderings bericht zich alleen ``"`n"`` in Windows (#13684) bevinden
- `CONOUT$`Namen en `CONIN$` gereserveerde apparaatnamen (#13508) herkennen (bedankt @davidreis97 !)
- Fix `ConciseView` voor interactieve geavanceerde functie bij het schrijven van fouten (#13623)
- Voeg ondersteuning toe voor `TLS` 1,3 in Web-cmdlets (#13409) (bedankt @iSazonov !)
- Voeg een null-controle toe voor `args` in `CommandLineParser` (#13451) (bedankt @iSazonov !)
- Reparsepunten voor Microsoft Store toepassingen (#13481) verwerken (bedankt @iSazonov !)
- De `PSNullConditionalOperators` functie van experimentele (#13529) verplaatsen
- De `PSNativePSPathResolution` functie van experimentele (#13522) verplaatsen
- Gebruik Field als er geen eigenschap bestaat voor `ObRoot` het gebruik van Power shell direct naar container (#13375) (bedankt @hemisphera !)
- `UTF-7`Verouderde waarschuwingen onderdrukken (#13484)
- Vermijd meerdere inventarisaties van een `IEnumerable<Expression>` instantie in `Compiler.cs` (#13491)
- Wijziging `Add-Type -OutputType` in geen ondersteuning `ConsoleApplication` en `WindowsApplication` (#13440)
- Waarschuwingen maken wanneer `UTF-7` is opgegeven als een code ring (#13430)
- Fout bericht oplossen van nieuwe symbolische koppeling ontbrekend doel (#13085) (bedankt @yecril71pl !)
- De para meter mag `args` niet null zijn in de open bare `ConsoleHost` api's (#13429)
- Ontbrekende afstoten voor `CancellationTokenSource` (#13420) toevoegen (bedankt @Youssef1313 !)
- Voeg de para meter toe `-Paged` aan `Get-Help` om paginering te ondersteunen (#13374)
- De oplossing wordt `Get-Help` niet correct weer gegeven als de para meter joker tekens ondersteunt (#13353) (bedankt @ThomasNieto !)
- `pwsh`Help-informatie bijwerken voor `-InputFormat` para meter (#13355) (bedankt @sethvs !)
- De MIT-licentie voor bestanden die zijn gekopieerd van Roslyn (#13305) declareren (bedankt @xtqqczze !)
- `BigInteger`Casting Behaviors (#12629) verbeteren (bedankt @vexx32 !)
- `Get-Acl -LiteralPath "HKLM:Software\Classes\*"`Gedrag oplossen (#13107) (bedankt @Shriram0908 !)
- `DefaultVisit`Methode toevoegen aan de interface en klasse van de bezoeker (#13258)
- Oplossen van conflicterende steno schakelaar `-s` (sta) voor `pwsh` (#13262) (bedankt @iSazonov !)
- Wijziging `Read-Host -MaskInput` in het gebruik van een bestaand `SecureString` pad, maar retour neren als tekst zonder opmaak (#13256)
- Verwijderen `ComEnumerator` als COM-objecten met `IEnumerator` wordt nu ondersteund in .net 5,0 (#13259)
- Tijdelijk persoonlijk pad gebruiken tijdens het opstarten van runs Pace als de omgevings variabele HOME niet is gedefinieerd (#13239)
- Oplossing `Invoke-Command` voor het detecteren van een recursieve aanroep van hetzelfde geschiedenis item (#13197)
- Het `pwsh` voor voegsel van een uitvoerbaar bestand wijzigen `-inputformat` `-in` in `-inp` om conflicten op te lossen met `-interactive` (#13205) (bedankt @iSazonov !)
- Het pad naar het WSL-bestands systeem verwerken tijdens het analyseren van de beveiligings zone van een bestand (#13120)
- Andere para meters verplicht maken in `Split-Path` (#13150) (bedankt @kvprasoon !)
- Nieuw pictogram voor Fluent-ontwerp voor Power shell 7 (#13100) (bedankt @sarthakmalik !)
- Oplossing `Move-Item` voor het ondersteunen van cross-Mount-verplaatsingen op UNIX (#13044)
- Fix `NullReferenceException` in `CommandSearcher.GetNextCmdlet` (#12659) (bedankt @powercode !)
- Voor komen `NullReferenceException` in UNIX-computer-cmdlets met test hooks Active (#12651) (bedankt @vexx32 !)
- Los het probleem op `Select-Object` waarbij `Hashtable` leden (bijvoorbeeld `Keys` ) niet kunnen worden gebruikt in combi natie met `-Property` of `-ExpandProperty` (#11097) (bedankt @vexx32 !)
- Oplossen van conflicterende steno schakelaar `-w` voor pwsh (#12945)
- Wijzig de naam van het `CimCmdlet` bron bestand (#12955) (bedankt @iSazonov !)
- Gebruik van `Test-Path` in `ConciseView` (#12778) verwijderen
- `default`Component voor waarde van de instructie switch voor vlag als sleutel woord (#10487) (bedankt @msftrncs !)
- Para meter toevoegen `SchemaFile` aan `Test-Json` cmdlet (#11934) (bedankt @beatcracker !)
- De para meters van de certificaat provider (#10622) terugbrengen (bedankt @iSazonov !)
- Oplossing `New-Item` voor het maken van een symbolische koppeling naar een relatief doelpad (#12797) (bedankt @iSazonov !)
- `CommandLine`Eigenschap toevoegen aan proces (#12288) (bedankt @iSazonov !)
- `-MaskInput`Para meter toevoegen aan `Read-Host` (#10908) (bedankt @davinci26 !)
- Wijzigen `CimCmdlets` in gebruik `AliasAttribute` (#12617) (bedankt @thlac !)
- Corrigeer de onjuiste index in een indelings teken reeks in ParameterBinderBase (#12630) (bedankt @powercode !)
- De `CommandInfo` eigenschap in `Command.Clone()` (#12301) kopiëren (bedankt @TylerLeonhardt !)
- Toep assen `-IncludeEqual` in `Compa-Object` When `-ExcludeDifferent` is opgegeven (#12317) (bedankt @davidseibel !)
- Wijziging van `Get-FileHash` Bestands ingangen sluiten voordat uitvoer wordt geschreven (#12474) (bedankt @HumanEquivalentUnit !)
- Inconsistent uitzonderings bericht oplossen in `-replace` operator (#12388) (bedankt @jackdcasey !)
- `WinCompat`Module laden herstellen om Power shell 7-modules met een hogere prioriteit (#12269) te behandelen
- `ForEach-Object -Parallel`Opnieuw gebruiken van runs Pace (#12122) implementeren
- Oplossing `Get-Service` om verzameling niet te wijzigen tijdens het opsommen (#11851) (bedankt @NextTurn !)
- De IPC-named pipe op Power Shell-afsluiten opschonen (#12187)
- De `<img />` regex-detectie in Web-cmdlets (#12099) oplossen (bedankt @vexx32 !)
- Kortere ondertekende Hex-tekens met toepasselijke type achtervoegsels toestaan (#11844) (bedankt @vexx32 !)
- Het bijwerken `UseNewEnvironment` van het parameter gedrag van de `Start-Process` cmdlet op Windows (#10830) (bedankt @iSazonov !)
- `-Shuffle`Schakel over naar de `Get-Random` opdracht (#11093) (bedankt @eugenesmlv !)
- Maak `GetWindowsPowerShellModulePath` compatibel met meerdere PS-installaties (#12280)
- Oplossen `Start-Job` om te werken op systemen waarop Windows Power shell niet is geregistreerd als standaard shell (#12296)
- Het opgeven van een alias en `-Syntax` `Get-Command` het retour neren van de syntaxis van opdrachten met alias (#10784) (bedankt @ChrisLGardner !)
- Maak CSV-cmdlets mogelijk wanneer u gebruikt `-AsNeeded` en er sprake is van een onvolledige rij (#12281) (bedankt @iSazonov !)
- In lokale aanroepen zijn niet vereist `-PowerShellVersion 5.1` voor `Get-FormatData` het weer geven van alle indelings gegevens. (#11270) (Bedankt @mklement0 !)
- Er is ondersteuning toegevoegd voor big endian `UTF-32` (#11947) (bedankt @NoMoreFood !)
- Mogelijke problemen oplossen die het Power shell-object uitstoten `ForEach-Object -Parallel` (#12227)
- Toevoegen `-FromUnixTime` aan `Get-Date` om Unix-tijd invoer toe te staan (#12179) (bedankt @jackdcasey !)
- Wijzig de voor-en achtergrond kleuren van de standaard voortgang zodat het contrast wordt verbeterd (#11455) (hartelijk dank @rkeithhill !)
- Oplossen `foreach -parallel` wanneer het huidige station niet beschikbaar is (#12197)
- Geen terugloop resultaat bij het `PSObject` converteren `ScriptBlock` naar `delegate` (#10619)
- Geen DNS-omzettings fouten op `Test-Connection -Quiet` (#12204) schrijven (bedankt @vexx32 !)
- Gebruik toegewezen threads voor het lezen van de omgeleide uitvoer en fout stromen van het onderliggende proces voor out-of-proc-taken (#11713)
- Een voor keur voor de volg orde van de operator oplossen in een binder-code (#12075) (bedankt @DamirAinullin !)
- Oplossen `NullReferenceException` bij het binden van algemene para meters van het type `ActionPreference` (#12124)
- Standaard opmaak voor gedeserialiseerd `MatchInfo` (#11728) corrigeren (bedankt @iSazonov !)
- Gebruik asynchrone streams in `Invoke-RestMethod` (#11095) (bedankt @iSazonov !)
- UTF-8-detectie in `Get-Content -Tail` (#11899) adresseren (bedankt @NoMoreFood !)
- De `IOException` in `Get-FileHash` (#11944) afhandelen (bedankt @iSazonov !)
- Wijzig `PowerShell Core` `PowerShell` in een resource teken reeks (#11928) (bedankt @alexandair !)
- Terug `MainWindowTitle` in `PSHostProcessInfo` (#11885) (bedankt @iSazonov !)
- Diverse kleine updates voor Windows-compatibiliteit (#11980)
- Oplossing `ConciseView` om te splitsen `PositionMessage` met `[Environment]::NewLine` (#12010)
- Beperking voor netwerk-hop verwijderen voor interactieve sessies (#11920)
- Fix `NullReferenceException` in `SuspendStoppingPipeline()` en `RestoreStoppingPipeline()` (#11870) (bedankt @iSazonov !)
- GUID genereren voor `FormatViewDefinition` `InstanceId` indien niet meegeleverd (#11896)
- Los op `ConciseView` dat het fout bericht breder is dan de venster breedte en geen witruimte heeft (#11880)
- Meerdere platforms `CAPI-compatible` externe sleutel uitwisseling (#11185) toestaan (hartelijk dank @silijon !)
- Fout bericht oplossen (#11862) (bedankt @NextTurn !)
- Correctie `ConciseView` voor het afhandelen van de situatie waarbij er geen console is om de breedte te verkrijgen (#11784)
- Update `CmsCommands` voor het gebruik van Store VS Certificate provider (#11643) (bedankt @mikeTWC1984 !)
- Inschakelen `pwsh` om te werken op Windows-systemen waar `mpr.dll` en niet beschikbaar is (#11748)
- Refactorion en implementeren `Restart-Computer` voor `Un*x` en macOS (#11319)
- Een implementatie van `Stop-Computer` voor Linux en macOS toevoegen (#11151)
- De `help` functie Fix om te controleren of deze `less` beschikbaar is voordat u (#11737) gebruikt
- Update `PSPath` in `certificate_format_ps1.xml` (#11603) (bedankt @xtqqczze !)
- Wijzig de reguliere expressie zodat deze overeenkomt met relatie typen zonder aanhalings tekens in de kop van de koppeling (#11711) (bedankt @Marusyk !)
- Fout bericht oplossen tijdens het verwijderen van een symbolische koppeling (#11331)
- Voeg `Selected.*` het aangepaste type `PSCustomObject` `Select-Object` slechts eenmaal toe (#11548) (hartelijk dank @iSazonov !)
- Toevoegen `-AsUTC` aan de `Get-Date` cmdlet (#11611)
- Groeps gedrag met Booleaanse waarden in `Format-Hex` (#11587) oplossen (bedankt @vexx32 !)
- `Test-Connection`Gebruik altijd de standaard synchronisatie context voor het verzenden van ping-aanvragen (#11517)
- Juiste opstart fout berichten (#11473) (bedankt @iSazonov !)
- Kopteksten met Null-waarden negeren in Web-cmdlets (#11424) (bedankt @iSazonov !)
- Controleer het verwijderen van de `Invoke-Command` taak opnieuw. (#11388)
- De functie voor het bijwerken van een nieuwe regel wordt hersteld als de inhoud leeg is (#11193) (#11342) (bedankt @iSazonov !)
- `CompleteInput`Het retour neren van resultaten van `ArgumentCompleter` When `AST` of script heeft overeenkomstige functie definitie (#10574) (hartelijk dank @M1kep !)
- Update formatter om nieuwe regels niet te schrijven als de inhoud leeg is (#11193)

<!-- TODO: add more general contributor thank you listing -->
