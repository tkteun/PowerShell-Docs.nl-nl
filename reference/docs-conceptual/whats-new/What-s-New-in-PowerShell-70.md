---
title: Wat is er nieuw in Power shell 7,0
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell 7,0
ms.date: 03/04/2020
ms.openlocfilehash: 84631d9fa169c8d1b4cd4dd23eb3d7c1bca120bb
ms.sourcegitcommit: b0966d61293e28ecdb929c5065be9760884e4e7d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80263132"
---
# <a name="whats-new-in-powershell-70"></a>Wat is er nieuw in Power shell 7,0

Power shell 7,0 is een open-source, platformoverschrijdende versie van het platform (Windows, macOS en Linux) van Power shell, gebouwd voor het beheren van heterogene omgevingen en hybride Cloud.

In deze release introduceren we een aantal nieuwe functies, waaronder:

- Pijplijn parallel Lise ring met `ForEach-Object -Parallel`
- Nieuwe Opera tors:
  - Ternaire operator: `a ? b : c`
  - Opera tors voor pijplijn ketens: `||` en `&&`
  - Voorwaardelijke null-Opera tors: `??` en `??=`
- Een vereenvoudigde en dynamische fout weergave en `Get-Error` cmdlet voor eenvoudiger onderzoek van fouten
- Een compatibiliteit slaag waarmee gebruikers modules kunnen importeren in een impliciete Windows Power shell-sessie
- Meldingen voor automatische nieuwe versie
- De mogelijkheid om DSC-resources rechtstreeks vanuit Power shell 7 aan te roepen (experimenteel)

Zie de [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)voor een volledige lijst met functies en oplossingen.

## <a name="where-can-i-install-powershell"></a>Waar kan ik Power Shell installeren?

Power shell 7 biedt momenteel ondersteuning voor de volgende besturings systemen op x64, waaronder:

- Windows 8,1 en 10
- Windows Server 2012, 2012 R2, 2016 en 2019
- macOS 10.13 +
- Red Hat Enterprise Linux (RHEL)/CentOS 7
- Fedora 30 +
- Debian 9
- Ubuntu LTS 16.04 +
- Alpine Linux 3.8 +

Daarnaast ondersteunt Power shell 7,0 ARM32-en ARM64-smaakten van Debian, Ubuntu en ARM64 Alpine Linux.

Controleer de installatie-instructies voor uw favoriete besturings systeem [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7)of [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7).

Hoewel niet officieel wordt ondersteund, heeft de community ook pakketten voor [Arch](https://aur.archlinux.org/packages/powershell/) en Kali Linux verschaft.

> [!NOTE]
> Debian 10 en CentOS 8 bieden momenteel geen ondersteuning voor externe toegang via WinRM. Zie voor meer informatie over het instellen van op SSH gebaseerde externe communicatie [Power shell voor externe toegang via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7).

Zie de [Power shell-ondersteunings levenscyclus](/powershell/scripting/powershell-support-lifecycle?view=powershell-7)voor meer actuele informatie over de ondersteunde besturings systemen en de levens cyclus van de ondersteuning.

## <a name="running-powershell-7"></a>Power shell 7 wordt uitgevoerd

Power shell 7 wordt geïnstalleerd in een nieuwe map en wordt naast elkaar uitgevoerd met Windows Power shell 5,1. Voor Power shell Core 6. x is Power shell 7 een in-place upgrade waarmee Power shell Core 6. x wordt verwijderd.

- Power shell 7 is geïnstalleerd op `%programfiles%\PowerShell\7`
- De map `%programfiles%\PowerShell\7` wordt toegevoegd aan `$env:PATH`

De installatie pakketten voor Power shell 7 upgraden eerdere versies van Power shell Core 6. x:

- Power shell Core 6. x op Windows: `%programfiles%\PowerShell\6` is vervangen door `%programfiles%\PowerShell\7`
- Linux: `/opt/microsoft/powershell/6` is vervangen door `/opt/microsoft/powershell/7`
- macOS: `/usr/local/microsoft/powershell/6` is vervangen door `/usr/local/microsoft/powershell/7`

> [!NOTE]
> In Windows Power shell heet het uitvoer bare bestand voor het starten van Power shell `powershell.exe`. In versie 6 en hoger wordt het uitvoer bare bestand gewijzigd om gelijktijdige uitvoering te ondersteunen. Het nieuwe uitvoer bare bestand voor het starten van Power shell 7 is `pwsh.exe`. Preview-builds blijven in-place als `pwsh-preview` in plaats van `pwsh` onder de map 7-Preview.

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>Verbeterde achterwaartse compatibiliteit met Windows Power shell

Power shell 7,0 markeert een verplaatsing van a naar .NET Core 3,1, waardoor aanzienlijk neerwaartse compatibiliteit met bestaande Windows Power shell-modules mogelijk wordt. Dit omvat veel modules op Windows waarvoor GUI-functionaliteit is vereist, zoals `Out-GridView` en `Show-Command`, evenals veel rollen beheer modules die worden geleverd als onderdeel van Windows.

Voor Windows wordt een nieuwe switch parameter **UseWindowsPowerShell** toegevoegd aan `Import-Module`. Met deze switch maakt u een proxy module in Power shell 7 die gebruikmaakt van een lokaal Windows Power Shell-proces om impliciet alle cmdlets in die module uit te voeren. Voor meer informatie over [import-module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7).

Zie de [module Compatibility Table](https://aka.ms/PSModuleCompat)voor meer informatie over welke micro soft-modules met power shell 7,0 werken.

## <a name="parallel-execution-added-to-foreach-object"></a>Parallelle uitvoering toegevoegd aan ForEach-object

De cmdlet `ForEach-Object`, waarmee items in een verzameling worden herhaald, heeft nu een ingebouwde parallelle parallelliteit met de nieuwe **parallelle** para meter.

Parallelle script blokken gebruiken standaard de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.

In dit voor beeld worden 50.000 logboek vermeldingen van 5 systeem logboeken op een lokale Windows-computer opgehaald:

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

Met de **parallelle** para meter wordt het script blok opgegeven dat parallel wordt uitgevoerd voor elke invoer logboek naam.

De nieuwe **ThrottleLimit** -para meter beperkt het aantal script blokken dat gelijktijdig wordt uitgevoerd op een bepaald moment. De standaard waarde is 5.

Gebruik de variabele `$_` om het huidige invoer object in het-script blok weer te geven. Gebruik het `$using:` bereik om variabele verwijzingen naar het uitgevoerde script blok door te geven.

Voor meer informatie over [foreach-object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7).

## <a name="ternary-operator"></a>Ternaire operator

Power shell 7,0 introduceert een ternaire operator die gedraagt zich als een vereenvoudigd `if-else`-instructie.
De ternaire operator van Power shell is nauw keurig gemodelleerd uit de syntaxis van de C# ternaire operator:

```
<condition> ? <if-true> : <if-false>
```

De voor waarde-expressie wordt altijd geëvalueerd en het resultaat wordt omgezet in een **Booleaanse** waarde om te bepalen welke vertakking vervolgens wordt geëvalueerd:

- De `<if-true>` expressie wordt uitgevoerd als de `<condition>`-expressie waar is
- De `<if-false>` expressie wordt uitgevoerd als de `<condition>`-expressie onwaar is

Bijvoorbeeld:

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

In dit voor beeld als het pad bestaat, wordt het **pad** weer gegeven. Als het pad niet bestaat, wordt het **pad niet gevonden** weer gegeven.

Voor meer informatie [over als](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7).

## <a name="pipeline-chain-operators"></a>Opera tors voor pijplijn keten

Power shell 7 implementeert de `&&`-en `||`-Opera tors om pijp lijnen voorwaardelijk te koppelen. Deze opera tors zijn bekend in Power shell als Opera tors voor pipeline-ketens en zijn vergelijkbaar met en en of lijsten in schalen zoals **bash** en **zsh**, evenals voorwaardelijke verwerkings symbolen in de Windows-opdracht shell (**cmd. exe**).

De operator `&&` voert de rechter pijp lijn uit als de pijplijn is geslaagd. Daarentegen wordt de rechter pijplijn door de `||`-operator uitgevoerd als de pijplijn is mislukt.

> [!NOTE]
> Deze opera tors gebruiken de `$?` en `$LASTEXITCODE` variabelen om te bepalen of een pijp lijn is mislukt. Hierdoor kunt u ze gebruiken met systeem eigen opdrachten en niet alleen met cmdlets of functies.

Hier is de eerste opdracht geslaagd en de tweede opdracht wordt uitgevoerd:

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

De eerste opdracht mislukt, de tweede wordt niet uitgevoerd:

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

De eerste opdracht slaagt, de tweede opdracht wordt niet uitgevoerd:

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

De eerste opdracht mislukt, dus de tweede opdracht wordt uitgevoerd:

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

Voor meer informatie [over pijplijn keten operators](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7).

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Null-samen voegen, toewijzings-en voorwaardelijke Opera tors

Power shell 7 bevat Null-samenvoegings operator `??`, voorwaardelijke toewijzing van Null-`??=`en null-Opera tors voor voorwaardelijke toegang van leden `?.` en `?[]`.

### <a name="null-coalescing-operator-"></a>Null-samenvoegings operator?

De null-samenvoegings operator `??` retourneert de waarde van de linkeroperand als deze niet null is.
Anders wordt de rechter operand geëvalueerd en wordt het resultaat geretourneerd. De `??`-operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.

```powershell
$x = $null
$x ?? 100
100
```

In het volgende voor beeld wordt de rechter operand niet geëvalueerd:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Operator voor voorwaardelijke toewijzing van Null? =

De operator voor voorwaardelijke toewijzing met Null `??=` wijst de waarde van de rechter operand alleen aan de linkeroperand toe als de linkeroperand wordt geëvalueerd als null. De `??=`-operator evalueert de rechter operand niet als de linkeroperand wordt geëvalueerd als niet-null.

```powershell
$x = $null
$x ??= 100
$x
100
```

In het volgende voor beeld wordt de rechter operand niet geëvalueerd:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Null-Opera tors voor voorwaardelijk leden?. maar? [] (Experimenteel)

> [!NOTE]
> Dit is een experimentele functie met de naam **PSNullConditionalOperators**. Meer informatie [over experimentele functies](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

Een voorwaardelijke operator met een null-waarde heeft leden toegang, `?.`, of element toegang, alleen `?[]`aan de operand als die operand resulteert in niet-Null; anders wordt Null geretourneerd.

> [!NOTE]
> Omdat Power shell toestaat dat `?` deel uitmaakt van de naam van de variabele, is formele specificatie van de naam van de variabele vereist voor het gebruik van deze opera tors. Daarom moet `{}` worden gebruikt rond de namen van variabelen, zoals `${a}` of wanneer `?` deel uitmaakt van de naam van de variabele `${a?}`.

In het volgende voor beeld wordt de waarde van **de lideigenschap geretourneerd** :

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

In het volgende voor beeld wordt Null geretourneerd zonder dat wordt geprobeerd om de **status**van de lidnaam te openen:

```powershell
$service = $Null
${Service}?.status
```

Op dezelfde manier wordt met behulp van `?[]`de waarde van het element geretourneerd:

```powershell
$a = 1..10
${a}?[0]
1
```

En als de operand null is, wordt het element niet geopend en wordt Null geretourneerd:

```powershell
$a = $null
${a}?[0]
```

[About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7)voor meer informatie.

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>Nieuwe weer gave-ConciseView en cmdlet Get-fout

De weer gave van fout berichten is verbeterd om de Lees baarheid van interactieve en script fouten te verbeteren met een nieuwe standaard weergave **ConciseView**. De weer gaven kunnen door de gebruiker worden geselecteerd via de voorkeurs variabele `$ErrorView`.

Als een fout niet is opgetreden in een script of parserfout, wordt met **ConciseView**een fout bericht met één regel weer gegeven:

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

Als de fout optreedt tijdens het uitvoeren van een script of als het een Parseerfout is, retourneert Power shell een fout bericht met meerdere regels met de fout, een wijzer en een fout bericht waarin wordt aangegeven waar de fout zich op die regel bevindt. Als de Terminal geen ANSI-escape reeksen (VT100) ondersteunt, worden er geen kleuren weer gegeven.

![Fout bij het weer geven van een script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

De standaard weergave in Power shell 7 is **ConciseView**. De vorige standaard weergave was **NormalView** en kan door de gebruiker worden geselecteerd door de voorkeurs variabele `$ErrorView`in te stellen.

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> Er wordt een nieuwe eigenschap **ErrorAccentColor** toegevoegd aan `$Host.PrivateData` ter ondersteuning van het wijzigen van de accent kleur van het fout bericht.

Een nieuwe cmdlet `Get-Error` biedt volledige gedetailleerde weer gave van de volledig gekwalificeerde fout, indien gewenst.
Standaard worden de volledige details van de cmdlet weer gegeven, met inbegrip van interne uitzonde ringen, van de laatste fout die is opgetreden.

![Weer geven bij Get-error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

De cmdlet `Get-Error` ondersteunt invoer van de pijp lijn met behulp van de ingebouwde variabele `$Error`.
`Get-Error` alle gesluisde fouten weer gegeven.

```powershell
$Error | Get-Error
```

De cmdlet `Get-Error` ondersteunt de **nieuwste** para meter, zodat u kunt opgeven hoeveel fouten van de huidige sessie u wilt weer geven.

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

Voor meer informatie over [Get-error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7).

## <a name="new-version-notification"></a>Melding voor nieuwe versie

Power shell 7 gebruikt update meldingen om gebruikers te waarschuwen dat er updates zijn voor Power shell.
Eenmaal per dag vraagt Power shell een online service aan om te bepalen of er een nieuwere versie beschikbaar is.

> [!NOTE]
> De update controle wordt uitgevoerd tijdens de eerste sessie binnen een bepaalde periode van 24 uur. Om prestatie redenen wordt de update controle drie seconden na het starten van de sessie gestart. De melding wordt alleen weer gegeven aan het begin van volgende sessies.

Power shell abonneert standaard op een van twee verschillende meldings kanalen, afhankelijk van de versie/vertakking. Ondersteunde, algemeen beschik bare (GA) versies van Power shell retour neren alleen meldingen voor bijgewerkte GA-releases. Preview en release Candi date (RC) geven een melding van updates voor preview-, RC-en GA-releases.

Het gedrag van de update melding kan worden gewijzigd met behulp van de omgevings variabele `$Env:POWERSHELL_UPDATECHECK`. De volgende waarden worden ondersteund:

- De **standaard instelling** is hetzelfde als het niet definiëren van `$Env:POWERSHELL_UPDATECHECK`
  - GA releases op de hoogte van updates voor GA releases
  - Preview/RC geeft melding van updates voor GA-en Preview-versies
- Met **uitschakelen** wordt de functie voor update meldingen uitgeschakeld
- **LTS** brengt alleen berichten op de hoogte van updates voor LTS-ga (Long-term-Servicing)

> [!NOTE]
> De omgevings variabele `$Env:POWERSHELL_UPDATECHECK` bestaat niet totdat deze voor de eerste keer is ingesteld.

Als u de versie melding alleen voor `LTS` releases wilt instellen:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

De versie melding instellen op het `Default` gedrag:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

Voor meer informatie [over meldingen over updates](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7).

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>Nieuwe ondersteuning voor DSC-resources met invoke-Dscresource bieden (experimenteel)

> [!NOTE]
> Dit is een experimentele functie met de naam **PSDesiredStateConfiguration. InvokeDscResource**. Meer informatie [over experimentele functies](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7).

Met de cmdlet `Invoke-DscResource` wordt een methode uitgevoerd van een opgegeven DSC-resource (desired state Configuration) van Power shell.

Met deze cmdlet wordt een DSC-resource rechtstreeks aangeroepen zonder dat er een configuratie document wordt gemaakt. Met deze cmdlet kunnen Configuration Management-producten Windows of Linux beheren met behulp van DSC-resources. Met deze cmdlet schakelt u ook fout opsporing van resources in wanneer de DSC-engine wordt uitgevoerd met fout opsporing ingeschakeld.

Met deze opdracht wordt de methode **set** aangeroepen van een resource met de naam log en wordt een **bericht** eigenschap opgegeven.

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

Voor meer informatie over [invoke-dscresource bieden](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7).

## <a name="breaking-changes-and-improvements"></a>Wijzigingen en verbeteringen te verbreken

### <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

- Update melding maken ondersteuning voor LTS en standaard kanalen (#11132)
- Test-verbinding bijwerken zodat deze meer werkt zoals in Windows Power shell (#10697) (Bedankt @vexx32!)
- $ Behouden? voor ParenExpression, subexpressie en ArrayExpression (#11040)
- Stel werkmap in op huidige map in start-Job (#10920) (Bedankt @iSazonov!)
- $PSCulture consistent weer geven in wijzigingen in de sessie cultuur (#10138) (Bedankt @iSazonov!)

### <a name="engine-updates-and-fixes"></a>Engine-updates en-oplossingen

- Verbeteringen in Break Point-Api's voor externe scenario's (#11312)
- Een lekkende definitie van een Power shell-klasse oplossen in een andere runs Pace (#11273)
- Een regressie in de opmaak herstellen, veroorzaakt door de FirstOrDefault-primitieve die is toegevoegd in 7.0.0-Preview1 (#11258)
- Aanvullende micro soft-modules voor het bijhouden van PS7-telemetrie (#10751)
- Goedgekeurde functies maken zonder experimentele (#11303)
- ConciseView bijwerken voor het gebruik van target object, indien van toepassing (#11075)
- NullReferenceException in CompletionCompleters Public-methoden oplossen (#11274)
- Status controle van apartment-thread op niet-Windows-platforms herstellen (#11301)
- Update-instelling PSModulePath om de variabelen process en machine Environment samen te voegen (#11276)
- Beduw .NET core naar 3.1.0 (#11260)
- Detectie van $PSHOME voor $env:P AD (#11141) oplossen
- Toestaan dat pwsh overneemt $env:P SModulePath en Power shell. exe op de juiste wijze kan worden gestart (#11057)
- Naar .NET Core 3,1 Preview 1 (#10798)
- Controles van reparse-Tags in de bestandssysteem provider (#10431) (Bedankt @iSazonov!)
- Vervang CR en New line door een 0x23CE-teken in script logging (#10616)
- Los een bron lekkage op door de registratie van de gebeurtenis-handler van AppDomain. CurrentDomain. ProcessExit (#10626) ongedaan te maken.
- Voeg ondersteuning toe aan ActionPreference. Store om in het fout opsporingsprogramma te kraken wanneer fout opsporing, fout, informatie, voortgang, uitgebreide of waarschuwings berichten worden gegenereerd (#8205) (Bedankt @KirkMunro!)
- Schakel het starten van invoeg toepassingen in het configuratie scherm in Power shell core in zonder op te geven. CPL-extensie. (#9828)
- Ondersteuning voor negatieve getallen in de Splits operator (#8960) (Bedankt @ece-jacob-scott!)

### <a name="general-cmdlet-updates-and-fixes"></a>Algemene cmdlet-updates en-oplossingen

- Oplossing voor probleem op Raspbian voor het instellen van de datum van bestands wijzigingen in de UnixStat experimentele functie (#11313)
- Add-AsPlainText voor ConvertFrom-SecureString (#11142)
- Controle van WindowsPS-versie toegevoegd voor WinCompat (#11148)
- Fout rapportage oplossen in sommige WinCompat-scenario's (#11259)
- Systeem eigen binaire resolver (#11032) toevoegen (Bedankt @iSazonov!)
- De berekening van de teken breedte bijwerken om de CJK-tekens correct te respecteren (#11262)
- Deblokkeren toevoegen-bestand voor macOS (#11137)
- Herstel regressie in Get-PSCallStack (#11210) (Bedankt @iSazonov!)
- Autoloading van de ScheduledJob-module verwijderen bij het gebruik van taak-cmdlets (#11194)
- Output type toevoegen aan de cmdlet Get-error en de oorspronkelijke TypeName (#10856) behouden
- Herstel de null-verwijzing in de eigenschap SupportsVirtualTerminal (#11105)
- Limiet controle toevoegen in Get-Wine vent (#10648) (Bedankt @iSazonov!)
- Opdracht runtime corrigeren zodat StopUpstreamCommandsException niet wordt gevuld in-ErrorVariable (#10840)
- Stel de uitvoer codering in op [console]:: OutputEncoding for native commands (#10824)
- Ondersteuning voor code blokken met meerdere regels in voor beelden (#10776) (Bedankt @Greg-Smulko!)
- Para meter Culture toevoegen aan de Select-string-cmdlet (#10943) (Bedankt @iSazonov!)
- Pad naar de werkmap van de start taak oplossen met een afsluitende back slash (#11041)
- ConvertFrom-JSON: verzamelingen standaard uitpakken (#10861) (Bedankt @danstur!)
- Gebruik een hoofdletter gevoelige hashtabel voor Group-object cmdlet with-CaseSensitive en-AsHashtable switches (#11030) (Bedankt @vexx32!)
- Uitzonde ring afhandelen wanneer het opsommen van bestanden mislukt bij het opnieuw opbouwen van het pad naar de juiste behuizing (#11014)
- Herstel ConciseView om activiteit weer te geven in plaats van myCommand (#11007)
- Web-cmdlets toestaan om HTTP-fout statussen te negeren (#10466) (Bedankt @vdamewood!)
- De installatie van meer dan één CommandInfo op Get-opdracht (#10929) herstellen
- De cmdlet Get-Counter voor Windows (#10933) toevoegen
- Maak ConvertTo-JSON behandel [AutomationNull]:: waarde en [NullString]:: waarde als $null (#10957)
- Haken verwijderen van IPv6-adres voor externe SSHing (#10968)
- Een crash herstellen als de opdracht die wordt verzonden naar pwsh, alleen witruimte is (#10977)
- Meerdere platforms Get-Klembord en set-klem bord (#10340) toegevoegd
- De instelling van het oorspronkelijke pad van het bestandssysteem object herstellen zonder extra afsluitende slash (#10959)
- Ondersteunings $null voor ConvertTo-JSON (#10947)
- Opdracht voor uitgaand-printer toevoegen in Windows (#10906)
- Start-job-variabele workingdirectory oplossen met witruimte (#10951)
- De standaard waarde Retour neren bij het ophalen van Null voor een instelling in PSConfiguration.cs (#10963) (Bedankt @iSazonov!)
- I/o-uitzonde ring afhandelen als niet-beëindigd (#10950)
- Voeg de GraphicalHost-assembly toe voor het inschakelen van out-GridView, show-Command en Get-Help-ShowWindow (#10899)
- Onderneem computer naam via pijp lijn in Get-HotFix (#10852) (Bedankt @kvprasoon!)
- De aanvulling van het tabblad voor para meters herstellen, zodat de algemene para meters als beschikbaar worden weer gegeven (#10850)
- Herstel GetCorrectCasedPath () om eerst te controleren of er systeem bestands vermeldingen worden geretourneerd voordat de eerste () (#10930) wordt aangeroepen.
- Stel werkmap in op huidige map in start-Job (#10920) (Bedankt @iSazonov!)
- Wijzig TabExpansion2 in niet vereist-CursorColumn en behandel als $InputScript. length (#10849)
- Case afhandelen waarbij host geen rijen of kolommen van het scherm mag retour neren (#10938)
- Het gebruik van accent kleuren herstellen voor hosts die deze niet ondersteunen (#10937)
- Een update toevoegen-lijst opdracht (#10922)
- FWLink-id bijwerken voor Clear-RecycleBin (#10925)
- Bij het volt ooien van het tabblad bestand overs Laan als bestands kenmerken niet kunnen worden gelezen (#10910)
- Clear-RecycleBin voor Windows toevoegen (#10909)
- `$env:__SuppressAnsiEscapeSequences` toevoegen om te bepalen of er een escape-teken reeks moet worden uitgevoerd (#10814)
- De para meter add-all voor het inkleuren van de Select-string uitvoer (#8963) (Bedankt @derek-xia!)
- De cmdlet Get-HotFix (#10740) toevoegen
- Het toevoegen van het type bruikbaar maken in toepassingen die als host optreden voor Power shell (#10587)
- Gebruik een effectievere evaluatie volgorde in LanguagePrimitives. IsNullLike () (#10781) (Bedankt @vexx32!)
- De verwerking van gepipede invoer van gemengde verzamelingen en gestreamde stromen van invoer in Format-hex (#8674) verbeteren (Bedankt @vexx32!)
- Gebruik type Conversion in SSHConnection hashtabellen wanneer de waarde niet overeenkomt met het verwachte type (#10720) (Bedankt @SeeminglyScience!)
- Herstel Get-content-ReadCount 0 Behavior wanneer-TotalCount is ingesteld (#10749) (Bedankt @eugenesmlv!)
- Het fout bericht toegang geweigerd in Get-Wine vent (#10639) (Bedankt @iSazonov!)
- Het inschakelen van het tabblad voor de toewijzing van een variabele met Enum of type beperkt (#10646)
- Ongebruikte eigenschap SourceLength Remoting verwijderen waardoor opmaak problemen ontstaan (#10765)
- De para meter add-scheidings teken voor ConvertFrom-StringData (#10665) (Bedankt @steviecoaster!)
- Positionele para meter voor script Block toevoegen bij het gebruik van invoke-opdracht met SSH (#10721) (Bedankt @machgo!)
- Regel context gegevens weer geven als er meerdere regels maar geen script naam voor ConciseView (#10746)
- Voeg ondersteuning voor \\WSL $ \-paden toe aan de File System Provider (#10674)
- Voeg de ontbrekende token tekst toe voor TokenKind. QuestionMark in parser (#10706)
- Stel de huidige werkmap van elk ForEach-object-parallel uitgevoerd script in op dezelfde locatie als het aanroepende script. (#10672)
- Vervang API-MS-Win-Core-File-L1-2 -2. dll door Kernell32. dll voor FindFirstStreamW-en FindNextStreamW-Api's (#10680) (Bedankt @iSazonov!)
- Tweak Help opmaak script om StrictMode tolerant te maken (#10563)
- Voeg de para meter-SecurityDescriptorSDDL toe aan New-Service (#10483) (Bedankt @kvprasoon!)
- De informatieve uitvoer verwijderen, het pingen van het gebruik van de test verbinding consolideren (#10478) (Bedankt @vexx32!)
- Speciale reparsepunten lezen zonder ze te openen (#10662) (Bedankt @iSazonov!)
- Direct uitgeschakelde uitvoer van de host naar Terminal (#10681) (Bedankt @iSazonov!)
- Opnieuw een nieuwe regel toevoegen met de indeling-Table en-Property (#10653)
- Verwijder [ValidateNotNullOrEmpty] uit-input object op Get-Random om lege teken reeks toe te staan (#10644)
- Niet-hoofdletter gevoelig (#10549 @iSazonov) systeem teken reeks van suggestie
- Uitzonde ring voor Null-verwijzingen herstellen in ForEach-Object-parallelle invoer verwerking (#10577)
- Definities van Power shell core-groeps beleid toevoegen (#10468)
- Update de console-host ter ondersteuning van XTPUSHSGR/XTPOPSGR VT-controle reeksen die worden gebruikt in scenario's voor het opstellen van een scenario. (#10208)
- De para meter variabele workingdirectory toevoegen aan de start-Job (#10324) (Bedankt @davinci26!)
- Verwijder de gebeurtenis-handler waardoor wijzigingen in onderbrekings punten onjuist worden gerepliceerd naar de host runs Pace Debugger (#10503) (Bedankt @KirkMunro!)
- Vervang API-MS-Win-core-job-12-1 -0. dll met Kernell32. dll in micro soft. Power shell. commands. NativeMethods P/Invoke API (#10417) (Bedankt @iSazonov!)
- Corrigeer de verkeerde uitvoer voor New-Service in variabele Assignment en-outvariable (#10444) (Bedankt @kvprasoon!)
- Algemene problemen met het hulp programma oplossen rond de afsluit code, opdracht regel parameters en pad met spaties (#10461)
- Herstel recursie in OneDrive-Change FindFirstFileEx () voor het gebruik van SafeFindHandle type (#10405)
- Het automatisch laden van PSReadLine in Windows overs Laan als de scherm lezer NVDA actief is (#10385)
- Verg root de ingebouwde module versie van Power shell naar 7.0.0.0 (#10356)
- Er is een fout opgetreden in de add-type als er al een type met dezelfde naam bestaat (#9609) (hartelijk dank @iSazonov!)

### <a name="performance"></a>Prestaties

- Vermijd het gebruik van closure in parser. saving (#11006)
- Verbeter de caching bij het maken van nieuwe regex-instanties (#10657) (Bedankt @iSazonov!)
- Verbeter de verwerking van de ingebouwde Power shell-type gegevens van types. ps1xml, typesV3. ps1xml en GetEvent. types. ps1xml (#10898)
- Werk PSConfiguration. ReadValueFromFile bij om het sneller en meer geheugen efficiënt te maken (#10839)
- Voeg kleine prestatie verbeteringen toe voor runs Pace-initialisatie (#10569) (Bedankt @iSazonov!)
- Maak ForEach-object sneller voor de meestgebruikte scenario's (#10454) en los het probleem van ForEach-object-parallel op met veel runspaces (#10455)

### <a name="code-cleanup"></a>Code opschonen

- Tekst van opmerking en element wijzigen om te voldoen aan de micro soft-normen (#11304)
- Problemen met opschonings stijl in Compiler.cs (#10368) (Bedankt @iSazonov!)
- Verwijder het niet-gebruikte type Converter voor CommaDelimitedStringCollection (#11000) (Bedankt @iSazonov!)
- Stijl opschonen in InitialSessionState.cs (#10865) (Bedankt @iSazonov!)
- Code opschonen voor PSSession-klasse (#11001)
- Verwijder de niet-werkende update uitvoeren-Help van Get-Help wanneer Get-Help wordt uitgevoerd voor de eerste functie (#10974)
- Stijl problemen oplossen (#10998) (Bedankt @iSazonov!)
- Opschonen: gebruik de ingebouwde alias (#10882) (Bedankt @iSazonov!)
- Verwijder de ongebruikte instelling sleutel ConsolePrompting en Vermijd overbodige teken reeks maken bij het uitvoeren van een query naar de ExecutionPolicy-instelling (#10985)
- Update meldings controle uitschakelen voor dagelijkse builds (#10903) (Bedankt @bergmeister!)
- Het herstellen van de API voor fout opsporing in #10338 is verloren gegaan (#10808)
- Verwijder de WorkflowJobSourceAdapter-verwijzing die niet meer wordt gebruikt (#10326) (Bedankt @KirkMunro!)
- De COM-interfaces in Jump List code opschonen door de PreserveSig-kenmerken (#9899) te corrigeren (Bedankt @weltkante!)
- Voeg een opmerking toe waarin wordt beschreven waarom-IA niet de alias voor Information Action common para meter (#10703) (Bedankt @KirkMunro!)
- Wijzig de naam van InvokeCommandCmdlet.cs in InvokeExpressionCommand.cs (#10659) (Bedankt @kilasuit!)
- Secundaire code-opschoningen gerelateerd aan update meldingen toevoegen (#10698)
- Afgeschafte werk stroom logica verwijderen uit de scripts voor externe installatie (#10320) (Bedankt @KirkMunro!)
- Help-indeling bijwerken voor het gebruik van de juiste case (#10678) (Bedankt @tnieto88!)
- Opschonen van CodeFactor stijl problemen die zich voordoen in door voeringen in de afgelopen maand (#10591) (Bedankt @iSazonov!)
- Corrigeer type fout in beschrijving van de PSTernaryOperator experimentele functie (#10586) (Bedankt @bergmeister!)
- ActionPreference omzetten in een niet-ondersteunde, gereserveerde status en de beperking voor het gebruik van ActionPreference. ignore negeren in de voorkeurs variabelen (#10317) (Bedankt @KirkMunro!)
- Vervang de array list door lijst<T> om meer Lees bare en betrouw bare code te verkrijgen zonder de functionaliteit te wijzigen (#10333) (Bedankt @iSazonov!)
- Code stijl oplossingen maken voor TestConnectionCommand (#10439) (Bedankt @vexx32!)
- AutomationEngine opschonen en extra SetSessionStateDrive-methode aanroep (#10416) verwijderen (Bedankt @iSazonov!)
- Wijzig de naam van de standaard ParameterSetName weer in scheidings teken voor ConvertTo-CSV en ConvertFrom-CSV (#10425)

### <a name="tools"></a>Hulpprogramma's

- Voeg de standaard instelling voor de eigenschap SDKToUse toe zodat deze wordt gebouwd in VS (#11085)
- Install-Powershell. ps1: para meter toevoegen voor het gebruik van MSI-installatie (#10921) (Bedankt @MJECloud!)
- Eenvoudige voor beelden voor install-PowerShell. ps1 (#10914) toevoegen (Bedankt @kilasuit!)
- Zorg ervoor dat Install-PowerShellRemoting. ps1 een lege teken reeks verwerkt in de PowerShellHome-para meter (#10526) (Bedankt @Orca88!)
- Schakel over van/etc/lsb-release naar/etc/OS-release in install-powershell.sh (#10773) (Bedankt @Himura2la!)
- Controleer pwsh. exe en pwsh in de dagelijkse versie van Windows (#10738) (Bedankt @centreboard!)
- Verwijder overbodige tikken in installpsh-osx.sh (#10752)
- Werk install-PowerShell. ps1 bij om te controleren of er al een geïnstalleerde dagelijkse build is (#10489)

### <a name="tests"></a>Getest

- Onbetrouwbare DSC-test maken in behandeling (#11131)
- Herstel de stringdata-test om sleutels van hashtabellen correct te valideren (#10810)
- Test modules (#11061) verwijderen (Bedankt @iSazonov!)
- De tijd verlengen tussen nieuwe pogingen om de test-URL te testen (#11015)
- Update tests om test acties nauw keurig te beschrijven. (#10928) (Bedankt @romero126!)
- De Flaky test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827) tijdelijk overs Laan
- De test van de gebeurtenis-handler stabiel maken (#10790)
- Synchronisatie van kapitalisatie in CI YAML (#10767) (Bedankt @RDIL!)
- Test toevoegen voor het oplossen van de gebeurtenis-handler (#10768)
- Get-Child item-test (#10507) toevoegen (Bedankt @iSazonov!)
- Vervang niet-eenduidige taal voor tests van overschakelen naar para meter voor nauw keurigheid (#10666) (Bedankt @romero126!)
- Experimentele controle toevoegen aan ForEach-Object-parallelle tests (#10354) (Bedankt @KirkMunro!)
- Tests voor alpiene validatie bijwerken (#10428)

### <a name="build-and-package-improvements"></a>Verbeteringen op het gebied van build en package

- Nuget pakket ondertekening voor gecoördineerde pakket build (#11316) oplossen
- Afhankelijkheden van PowerShell Gallery en NuGet (#11323) bijwerken
- Duw micro soft. ApplicationInsights van 2.11.0 naar 2.12.0 (#11305)
- Duw micro soft. CodeAnalysis. CSharp van 3.3.1 naar 3.4.0 (#11265)
- Update pakketten voor Debian 10 en 11 (#11236)
- Schakel alleen experimentele functies in vóór RC (#11162)
- Minimum versie van macOS bijwerken (#11163)
- Duw NJsonSchema van 10.0.27 naar 10.0.28 (#11170)
- Koppelingen in README.md en meta data. json bijwerken voor preview. 5 (#10854)
- Selecteer de bestanden voor nalevings tests die eigendom zijn van Power shell (#10837)
- Win7x86 msix-pakket mag worden gemaakt. (Interne 10515)
- Toestaan dat semantische versies worden door gegeven aan de functie NormalizeVersion (#11087)
- .NET core Framework omlaag dalen tot 3,1-Preview. 3 (#11079)
- Duw PSReadLine van 2.0.0-beta5 naar 2.0.0-beta6 in/src/Modules (#11078)
- Duw Newton soft. json van 12.0.2 naar 12.0.3 (#11037) (#11038)
- Debian-pakketten van 10, 11 en CentOS 8 toevoegen (#11028)
- Het JSON-bestand voor Build-info uploaden met het veld ReleaseDate (#10986)
- .NET core Framework omlaag dalen tot 3,1-Preview. 2 (#10993)
- Build van het x86 MSIX-pakket (#10934) inschakelen
- De URL van de DotNet SDK-installatie script bijwerken in build. psm1 (#10927)
- Duw Markdig. ondertekend van 0.17.1 naar 0.18.0 (#10887)
- Duw ThreadJob van 2.0.1 naar 2.0.2 (#10886)
- AppX-manifest en verpakkings module bijwerken om te voldoen aan de vereisten voor MS Store (#10878)
- Pakket verwijzing voor Power shell SDK bijwerken naar preview. 5 (interne 10295)
- Update ThirdPartyNotices. txt (#10834)
- Duw micro soft. Power shell. native naar 7.0.0-Preview. 3 (#10826)
- Duw micro soft. ApplicationInsights van 2.10.0 naar 2.11.0 (#10608)
- Duw NJsonSchema van 10.0.24 naar 10.0.27 (#10756)
- MacPorts-ondersteuning toevoegen aan het build-systeem (#10736) (Bedankt @Lucius-Q-User!)
- Duw package management van 1.4.4 naar 1.4.5 (#10728)
- Duw NJsonSchema van 10.0.23 naar 10.0.24 (#10635)
- Omgevings variabele toevoegen om onderscheid te maken tussen client/server-telemetrie in MSI (#10612)
- Duw PSDesiredStateConfiguration van 2.0.3 naar 2.0.4 (#10603)
- Duw micro soft. CodeAnalysis. CSharp van 3.2.1 naar 3.3.1 (#10607)
- Bijwerken naar .net Core 3,0 RTM (#10604) (Bedankt @bergmeister!)
- MSIX-verpakking bijwerken zodat de versie van Windows Store-vereisten (#10588)
- PowerShellGet-versie van 2,2 naar 2.2.1 (#10382)
- Package Management-versie van 1.4.3 naar 1.4.4 (#10383)
- README.md en meta data. json bijwerken voor 7.0.0-Preview. 4 (interne 10011)
- Voer een upgrade uit van de .net Core 3,0-versie van preview 9 naar RC1 (#10552) (Bedankt @bergmeister!)
- Genereren van ExperimentalFeature-lijst oplossen (intern 9996)
- Duw PSReadLine-versie van 2.0.0-beta4 naar 2.0.0-beta5 (#10536)
- Release build-script voor het instellen van release tag herstellen
- Update versie van micro soft. Power shell. native to 7.0.0-Preview. 2 (#10519)
- Voer een upgrade uit naar Netcoreapp 3.0 preview9 (#10484) (Bedankt @bergmeister!)
- Zorg ervoor dat de dagelijkse samen stelling kent, weet u zeker dat het een dagelijkse build is (#10464)
- Werk de gecombineerde pakket versie bij om de dagelijkse builds op te heffen (#10449)
- Verwijder de appveyor-verwijzing (#10445) (Bedankt @RDIL!)
- NJsonSchema-versie van 10.0.22 naar 10.0.23 (#10421)
- Verwijder het verwijderen van de map Linux-x64 build omdat sommige afhankelijkheden voor Alpine zijn vereist (#10407)

### <a name="documentation-and-help-content"></a>Documentatie en Help-inhoud

- Wijzigings logboeken voor refeiten in één logboek per release (#11165)
- FWLinks voor Power shell 7 online-Help-documenten (#11071) herstellen
- Update CONTRIBUTING.md (#11096) (Bedankt @mklement0!)
- Koppelingen voor installatie doc herstellen in README.md (#11083)
- Voor beelden toevoegen aan het script install-PowerShell. ps1 (#11024) (Bedankt @kilasuit!)
- Fix to select-string nadruk en import-Dscresource bieden in CHANGELOG.md (#10890)
- De verouderde koppeling verwijderen van powershell-beginners-guide.md (#10926)
- Stabiele en onderhouds logboeken voor wijzigingen samen voegen (#10527)
- Gebruikte .NET-versie bijwerken in Build docs (#10775) (Bedankt @Greg-Smulko!)
- Vervang links van MSDN naar docs.microsoft.com in powershell-beginners-guide.md (#10778) (Bedankt @iSazonov!)
- Defecte koppeling voor DSC-overzicht oplossen (#10702)
- Support_Question. MD bijwerken om te koppelen aan Stack Overflow als een andere Community-Resource (#10638) (Bedankt @mklement0!)
- De processor architectuur toevoegen aan de sjabloon voor de distributie aanvraag (#10661)
- Nieuw Power shell MoL Book toevoegen om Power shell-documenten te leren (#10602)
- README.md en meta gegevens bijwerken voor v 6.1.6-en v 6.2.3-releases (#10523)
- Een type fout corrigeren in README.md (#10465) (Bedankt @vedhasp!)
- Voeg een verwijzing naar de PSKoans-module toe aan de documentatie voor Learning resources (#10369) (Bedankt @vexx32!)
- README.md en meta data. json bijwerken voor 7.0.0-Preview. 3 (#10393)
