---
title: Wat is er nieuw in PowerShell 7.0
description: Nieuwe functies en wijzigingen uitgebracht in PowerShell 7.0
ms.date: 03/04/2020
ms.openlocfilehash: c858cf46d264ec1c29625eb08e30f71336f4e736
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729950"
---
# <a name="whats-new-in-powershell-70"></a>Wat is er nieuw in PowerShell 7.0

PowerShell 7.0 is een opensource-, platformoverschrijdende (Windows-, macOS- en Linux)-editie van PowerShell, gebouwd om heterogene omgevingen en hybride cloud te beheren.

In deze release introduceren we een aantal nieuwe functies, waaronder:

- Pijplijn-parallellisatie met `ForEach-Object -Parallel`
- Nieuwe operators:
  - Ternaire operator: `a ? b : c`
  - Pijplijnketenoperators: `||` en `&&`
  - Voorwaardelijke null-operators: `??` en `??=`
- Een vereenvoudigde en dynamische foutweergave en `Get-Error` cmdlet voor eenvoudiger onderzoek van fouten
- Een compatibiliteitslaag waarmee gebruikers modules kunnen importeren in een impliciete Windows PowerShell sessie
- Automatische meldingen van nieuwe versies
- De mogelijkheid om DSC-resources rechtstreeks vanuit PowerShell 7 aan te roepen (experimenteel)

Zie de [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)voor een volledige lijst met functies en oplossingen.

## <a name="where-can-i-install-powershell"></a>Waar kan ik PowerShell installeren?

PowerShell 7 ondersteunt momenteel de volgende besturingssystemen op x64, waaronder:

- Windows 8.1 en 10
- Windows Server 2012, 2012 R2, 2016 en 2019
- macOS 10.13+
- Red Hat Enterprise Linux (RHEL) / CentOS 7
- Fedora 30+
- Debian 9
- Ubuntu LTS 16.04+
- Alpine Linux 3.8+

Daarnaast biedt PowerShell 7.0 ondersteuning voor ARM32- en ARM64-varianten van Debian, Ubuntu en ARM64 Alpine Linux.

Controleer de installatie-instructies voor het besturingssysteem van [uw voorkeur: Windows,](/powershell/scripting/install/installing-powershell-core-on-windows) [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)of [Linux.](/powershell/scripting/install/installing-powershell-core-on-linux)

Hoewel dit niet officieel wordt ondersteund, biedt de community ook pakketten voor [Arch](https://aur.archlinux.org/packages/powershell/) en Kali Linux.

> [!NOTE]
> Debian 10 en CentOS 8 bieden momenteel geen ondersteuning voor remoting van WinRM. Zie Voor meer informatie over het instellen van op SSH gebaseerde remoting [PowerShell Remoting via SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

Zie De levenscyclus van [PowerShell-ondersteuning](/powershell/scripting/powershell-support-lifecycle)voor meer actuele informatie over ondersteunde besturingssystemen en de levenscyclus van ondersteuning.

## <a name="running-powershell-7"></a>PowerShell 7 uitvoeren

PowerShell 7 wordt in een map geïnstalleerd, gescheiden van Windows PowerShell.
Hiermee kunt u PowerShell 7 naast elkaar uitvoeren met Windows PowerShell 5.1. Voor PowerShell Core 6.x is PowerShell 7 een in-place upgrade die PowerShell Core 6.x verwijdert.

- PowerShell 7 is geïnstalleerd op `%programfiles%\PowerShell\7`
- De `%programfiles%\PowerShell\7` map wordt toegevoegd aan `$env:PATH`

Met het PowerShell 7-installatiepakket worden eerdere versies van PowerShell Core 6.x:

- PowerShell Core 6.x in Windows: `%programfiles%\PowerShell\6` is vervangen door `%programfiles%\PowerShell\7`
- Linux: `/opt/microsoft/powershell/6` wordt vervangen door `/opt/microsoft/powershell/7`
- macOS: `/usr/local/microsoft/powershell/6` is vervangen door `/usr/local/microsoft/powershell/7`

> [!NOTE]
> In Windows PowerShell heeft het uitvoerbare bestand om PowerShell te starten de naam `powershell.exe` . In versie 6 en hoger wordt de naam van het uitvoerbare bestand gewijzigd om uitvoering naast elkaar te ondersteunen. De nieuwe naam van het uitvoerbare bestand om PowerShell 7 te starten is `pwsh.exe` . Preview-builds blijven in-place als `pwsh-preview` in plaats van onder de map `pwsh` 7-preview.

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>Verbeterde compatibiliteit met eerdere Windows PowerShell

PowerShell 7.0 markeert een overstap naar .NET Core 3.1, waardoor de compatibiliteit met bestaande Windows PowerShell-modules aanzienlijk Windows PowerShell is. Dit omvat veel modules in Windows waarvoor GUI-functionaliteit is vereist, zoals en , evenals veel rolbeheermodules die worden aangeboden `Out-GridView` `Show-Command` als onderdeel van Windows.

Voor Windows wordt een nieuwe switchparameter **UseWindowsPowerShell** toegevoegd aan `Import-Module` . Met deze switch maakt u een proxymodule in PowerShell 7 die gebruikmaakt van een lokaal Windows PowerShell om impliciet cmdlets uit te voeren die in die module zijn opgenomen. Voor meer informatie over [Import-Module.](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true)

Zie de modulecompatibiliteitstabel voor meer informatie over [](https://aka.ms/PSModuleCompat)welke Microsoft-modules werken met PowerShell 7.0.

## <a name="parallel-execution-added-to-foreach-object"></a>Parallelle uitvoering toegevoegd aan ForEach-Object

De cmdlet, waarmee items in een verzameling worden itereerd, heeft nu `ForEach-Object` ingebouwde parallellisme met de nieuwe parameter **Parallel.**

Parallelle scriptblokken gebruiken standaard de huidige werkmap van de aanroeper die de parallelle taken heeft gestart.

In dit voorbeeld worden 50.000 logboekgegevens opgehaald uit 5 systeemlogboeken op een lokale Windows-computer:

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

De **parameter Parallel** geeft het scriptblok aan dat parallel wordt uitgevoerd voor elke naam van het invoerlogboek.

De nieuwe **parameter ThrottleLimit** beperkt het aantal scriptblokken dat parallel op een bepaald moment wordt uitgevoerd. De standaardwaarde is 5.

Gebruik de variabele om het huidige invoerobject in het `$_` scriptblok weer te geven. Gebruik het `$using:` bereik om variabeleverwijzingen door te geven aan het lopende scriptblok.

Voor meer informatie over [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7&preserve-view=true).

## <a name="ternary-operator"></a>Ternaire operator

PowerShell 7.0 introduceert een ternaire operator die zich gedraagt als een vereenvoudigde `if-else` instructie.
De ternaire operator van PowerShell is nauw gemodelleerd op de syntaxis van de ternaire C#-operator:

```
<condition> ? <if-true> : <if-false>
```

De condition-expression wordt altijd geëvalueerd en het resultaat ervan wordt geconverteerd naar een **Booleaanse** waarde om te bepalen welke vertakking vervolgens wordt geëvalueerd:

- De `<if-true>` expressie wordt uitgevoerd als de expressie waar `<condition>` is
- De `<if-false>` expressie wordt uitgevoerd als de expressie `<condition>` onwaar is

Bijvoorbeeld:

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

Als het pad in dit voorbeeld bestaat, wordt **Pad** bestaat weergegeven. Als het pad niet bestaat, wordt **Pad niet gevonden** weergegeven.

Voor meer informatie [over If](/powershell/module/microsoft.powershell.core/about/about_if).

## <a name="pipeline-chain-operators"></a>Pijplijnketenoperators

PowerShell 7 implementeert de `&&` operators en `||` om pijplijnen voorwaardelijk te ketenen. Deze operators worden in PowerShell 'pijplijnketenoperators' genoemd en zijn vergelijkbaar met AND- en OR-lijsten in shells zoals **Bash** en **Zsh,** evenals voorwaardelijke verwerkingssymbolen in de Windows Command Shell **(cmd.exe).**

De `&&` operator voert de rechterpijplijn uit als de pijplijn aan de linkerkant is geslaagd. De operator voert `||` daarentegen de rechterpijplijn uit als de pijplijn aan de linkerkant is mislukt.

> [!NOTE]
> Deze operators gebruiken de `$?` variabelen en om te bepalen of een `$LASTEXITCODE` pijplijn is mislukt. Hiermee kunt u ze gebruiken met systeemeigen opdrachten en niet alleen met cmdlets of functies.

Hier slaagt de eerste opdracht en wordt de tweede opdracht uitgevoerd:

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

Hier mislukt de eerste opdracht en wordt de tweede niet uitgevoerd:

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

Hier slaagt de eerste opdracht, de tweede opdracht wordt niet uitgevoerd:

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

Hier mislukt de eerste opdracht, zodat de tweede opdracht wordt uitgevoerd:

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

Voor meer informatie over [pijplijnketenoperators.](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7&preserve-view=true)

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Null-sameneten, toewijzing en voorwaardelijke operators

PowerShell 7 bevat null-samen te schalen operator `??` , Null voorwaardelijke toewijzing `??=` en Null voorwaardelijke lidtoegangsoperators `?.` en `?[]` .

### <a name="null-coalescing-operator-"></a>Null-samen te sluiten Operator ?

De operator null-coalescing retourneert de waarde van de linkerope `??` operand als deze niet null is.
Anders wordt de rechterope operand geëvalueerd en wordt het resultaat ervan retourneert. De `??` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.

```powershell
$x = $null
$x ?? 100
100
```

In het volgende voorbeeld wordt de rechteropeenvolger niet geëvalueerd:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Null-operator voor voorwaardelijke toewijzing? =

De operator voor voorwaardelijke toewijzing van null wijst de waarde van de rechteropend alleen toe aan de linkeropend als de operand aan de linkerkant als null `??=` wordt geëvalueerd. De `??=` operator evalueert de rechterope operand niet als de linkeropeen is geëvalueerd als niet-null.

```powershell
$x = $null
$x ??= 100
$x
100
```

In het volgende voorbeeld wordt de rechterope operand niet geëvalueerd:

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Null operators voor voorwaardelijke lidtoegang ? . En? [] (experimenteel)

> [!NOTE]
> Dit is een experimentele functie met de **naam PSNullConditionalOperators.** Zie Experimentele functies gebruiken [voor meer informatie.](/powershell/scripting/learn/experimental-features)

Een voorwaardelijke operator null staat alleen toegang tot leden, , of elementtoegang tot de operand toe als die operand als niet-null wordt geëvalueerd; anders wordt `?.` `?[]` null geretourneerd.

> [!NOTE]
> Omdat PowerShell deel mag uitmaken van de naam van de variabele, is een formele specificatie van de naam van de variabele `?` vereist voor het gebruik van deze operators. Het is dus vereist om te gebruiken `{}` rond de namen van variabelen, zoals of wanneer deel uitmaakt van de `${a}` `?` variabelenaam `${a?}` .

In het volgende voorbeeld wordt de waarde van de eigenschap Status van het **lid** geretourneerd:

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

In het volgende voorbeeld wordt null geretourneerd, zonder toegang te krijgen tot de **lidnaam Status:**

```powershell
$service = $Null
${Service}?.status
```

Op dezelfde manier wordt met `?[]` behulp van de waarde van het element geretourneerd:

```powershell
$a = 1..10
${a}?[0]
1
```

En wanneer de operand null is, wordt het element niet toegankelijk en wordt null geretourneerd:

```powershell
$a = $null
${a}?[0]
```

Voor meer informatie [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7&preserve-view=true).

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>Nieuwe weergave: ConciseView en cmdlet Get-Error

PowerShell 7.0 verbetert de weergave van foutberichten om de leesbaarheid van interactieve en scriptfouten te verbeteren met een nieuwe standaardweergave **ConciseView**. De weergaven kunnen door de gebruiker worden geselecteerd via de voorkeursvariabele `$ErrorView` .

Als **een fout niet** afkomstig is van een script- of parserfout, is dit een foutbericht met één regel:

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

Als de fout optreedt tijdens het uitvoeren van het script of een parseringsfout is, retourneert PowerShell een foutbericht met meerdere lijnen dat de fout bevat, een aanwijzer en een foutbericht dat laat zien waar de fout zich op die regel voordoet. Als de terminal geen ondersteuning biedt voor ANSI-kleuren escapereeksen (VT100), worden er geen kleuren weergegeven.

![Fout bij het weergeven van een script](./media/What-s-New-in-PowerShell-70/myscript-error.png)

De standaardweergave in PowerShell 7 is **ConciseView.** De vorige standaardweergave was **NormalView en** u kunt dit selecteren door de voorkeursvariabele in te `$ErrorView` stellen.

```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> Er wordt een nieuwe eigenschap **ErrorAccentColor** toegevoegd aan ter `$Host.PrivateData` ondersteuning van het wijzigen van de accentkleur van het foutbericht.

Een nieuwe cmdlet biedt desgewenst een volledige gedetailleerde weergave van de volledig `Get-Error` gekwalificeerde fout.
Standaard geeft de cmdlet de volledige details weer, inclusief interne uitzonderingen, van de laatste fout die is opgetreden.

![Weergeven vanuit Get-Error](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

De `Get-Error` cmdlet ondersteunt invoer van de pijplijn met behulp van de ingebouwde variabele `$Error` .
`Get-Error` geeft alle doorspijpfouten weer.

```powershell
$Error | Get-Error
```

De `Get-Error` cmdlet ondersteunt de parameter **Nieuwste,** zodat u kunt opgeven hoeveel fouten van de huidige sessie u wilt weergeven.

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

Voor meer informatie over [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7&preserve-view=true).

## <a name="new-version-notification"></a>Melding over nieuwe versie

PowerShell 7 maakt gebruik van updatemeldingen om gebruikers te waarschuwen dat er updates voor PowerShell bestaan.
Eenmaal per dag vraagt PowerShell een query uit op een onlineservice om te bepalen of er een nieuwere versie beschikbaar is.

> [!NOTE]
> De updatecontrole vindt plaats tijdens de eerste sessie in een bepaalde periode van 24 uur. Uit prestatieoverwegingen wordt de updatecontrole 3 seconden na het begin van de sessie gestart. De melding wordt alleen weergegeven aan het begin van volgende sessies.

PowerShell abonneert zich standaard op een van twee verschillende meldingskanalen, afhankelijk van de versie/vertakking. Ondersteunde, algemeen beschikbare (GA)-versies van PowerShell retourneren alleen meldingen voor bijgewerkte ga-releases. Preview- en RELEASE Candidate-releases (RC) melden updates voor preview-, RC- en GA-releases.

Het gedrag voor updatemeldingen kan worden gewijzigd met behulp van de `$Env:POWERSHELL_UPDATECHECK` omgevingsvariabele. De volgende waarden worden ondersteund:

- **De** standaardwaarde is hetzelfde als het niet definiëren van `$Env:POWERSHELL_UPDATECHECK`
  - GA-releases melden updates voor GA-releases
  - Preview-/RC-releases melden updates voor ga- en preview-releases
- **Met Uitschakelen** wordt de functie voor updatemeldingen uitgeschakeld
- **LTS** waarschuwt alleen updates voor LTS-releases (long-term-servicing)

> [!NOTE]
> De `$Env:POWERSHELL_UPDATECHECK` omgevingsvariabele bestaat pas als deze voor de eerste keer is ingesteld.

De versiemelding voor alleen `LTS` releases instellen:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

De versiemelding instellen op het `Default` gedrag:

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

Voor meer informatie [over updatemeldingen.](/powershell/module/microsoft.powershell.core/about/about_update_notifications)

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>Nieuwe ondersteuning voor DSC-resources met Invoke-DSCResource (experimenteel)

> [!NOTE]
> Dit is een experimentele functie met **de naam PSDesiredStateConfiguration.InvokeDscResource.** Zie Experimentele functies gebruiken [voor meer informatie.](/powershell/scripting/learn/experimental-features)

Met `Invoke-DscResource` de cmdlet wordt een methode van een opgegeven PowerShell Desired State Configuration -resource (DSC) uitgevoerd.

Met deze cmdlet wordt een DSC-resource rechtstreeks aanroepen, zonder een configuratiedocument te maken. Met deze cmdlet kunnen configuratiebeheerproducten Windows of Linux beheren met behulp van DSC-resources. Met deze cmdlet kunt u ook debuggen van resources wanneer de DSC-engine wordt uitgevoerd met debugging ingeschakeld.

Met deze opdracht wordt de **set-methode** van een resource met de naam **WindowsProcess** aanroepen en worden de verplichte eigenschappen **Pad** en **Argumenten** opgegeven om het opgegeven Windows-proces te starten.

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

Voor meer informatie over [Invoke-DSCResource.](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&preserve-view=true)

## <a name="breaking-changes-and-improvements"></a>Belangrijke wijzigingen en verbeteringen

### <a name="breaking-changes"></a>Wijzigingen die fouten veroorzaken

- Updatemeldingen ondersteunen LTS en standaardkanalen (#11132)
- Werk Test-Connection zo bij dat het meer werkt zoals in Windows PowerShell (#10697) (Bedankt @vexx32 !)
- $? voor ParenExpression, SubExpression en ArrayExpression (#11040)
- Stel de working directory in op current directory in Start-Job (#10920) (Bedankt @iSazonov !)
- Zorg $PSCulture consistent wijzigingen in de sessiecultuur (#10138) (Bedankt @iSazonov !)

### <a name="engine-updates-and-fixes"></a>Engine-updates en -oplossingen

- Verbeteringen in onderbrekingspunt-API's voor externe scenario's (#11312)
- Probleem opgelost met het lekken van PowerShell-klassedefinitie in een andere Runspace (#11273)
- Regressie in opmaak opgelost die wordt veroorzaakt door de firstordefault-primitieve die is toegevoegd in 7.0.0-Preview1 (#11258)
- Aanvullende Microsoft-modules om bij te houden in PS7-telemetrie (#10751)
- Goedgekeurde functies niet-experimenteel maken (#11303)
- Werk ConciseView bij om TargetObject te gebruiken, indien van toepassing (#11075)
- NullReferenceException opgelost in Openbare methoden van CompletionCompleters (#11274)
- Controle van de threadtoestand van een thread op niet-Windows-platformen (#11301)
- Instelling PSModulePath bijgewerkt voor het samenvoegen van de proces- en machineomgevingsvariabelen (#11276)
- .NET Core naar 3.1.0 (#11260)
- Detectie van $PSHOME vóór $env:PATH (#11141)
- Pwsh toestaan om $env:PSModulePath over te nemen en ervoor te zorgen powershell.exe correct wordt #11057)
- Over naar .NET Core 3.1 preview 1 (#10798)
- Controles van reparsetags in de bestandssysteemprovider (#10431) (bedankt @iSazonov !)
- VERVANG CR en de nieuwe regel door een 0x23CE in scriptlogboekregistratie (#10616)
- Los een resourcelek op door de registratie van de gebeurtenis-handler van AppDomain.CurrentDomain.ProcessExit (#10626)
- Voeg ondersteuning toe aan ActionPreference.Break om op te breken in het foutopsporingssysteem wanneer er foutopsporings-, fout-, informatie-, voortgangs-, uitgebreide of waarschuwingsberichten worden gegenereerd (#8205) (bedankt @KirkMunro !)
- Schakel invoegingen van het configuratiescherm in PowerShell Core zonder op te geven. CPL-extensie. (#9828)
- Ondersteuning voor negatieve getallen in de operator -split (#8960) (bedankt @ece-jacob-scott !)

### <a name="general-cmdlet-updates-and-fixes"></a>Algemene updates en oplossingen voor cmdlet

- Oplossing voor probleem met Raspbian voor het instellen van de datum van bestandswijzigingen in de experimentele functie UnixStat (#11313)
- -AsPlainText toevoegen aan ConvertFrom-SecureString (#11142)
- WindowsPS-versiecontrole toegevoegd voor WinCompat (#11148)
- Foutrapportage in sommige WinCompat-scenario's (#11259)
- Systeemeigen binaire resolver (#11032) toevoegen (bedankt @iSazonov !)
- De berekening van de breedte van de char bijwerken om CJK-chars correct te #11262)
- Een Unblock-File voor macOS (#11137)
- Regressie in Get-PSCallStack (#11210) opgelost (bedankt @iSazonov !)
- Automatisch laden van de module ScheduledJob verwijderen bij het gebruik van taak-cmdlets (#11194)
- Voeg OutputType toe aan Get-Error cmdlet en behoud de oorspronkelijke typenamen (#10856)
- Probleem opgelost met null-verwijzing in eigenschap SupportsVirtualTerminal (#11105)
- Limietcontrole toevoegen in Get-WinEvent (#10648) (Bedankt @iSazonov !)
- Probleem met opdrachtruntime opgelost, zodat StopUpstreamCommandsException niet wordt ingevuld in -ErrorVariable (#10840)
- Stel de uitvoercodeer in op [Console]::OutputEncoding voor systeemeigen opdrachten (#10824)
- Ondersteuning voor codeblokken met meerdere regels in voorbeelden (#10776) (Bedankt @Greg-Smulko !)
- Voeg de parameter Culture toe Select-String cmdlet (#10943) (Bedankt @iSazonov !)
- Probleem Start-Job van een werkmap met een backslash (#11041)
- ConvertFrom-Json: verzamelingen standaard uitpakken (#10861) (bedankt @danstur !)
- Gebruik de casegevoelige hashtabel voor Group-Object cmdlet met -CaseSensitive en -AsHashtable-switches (#11030) (Bedankt @vexx32 !)
- Af te handelen uitzondering als het opsnoemen van bestanden mislukt bij het herbouwen van het pad met de juiste casing (#11014)
- Fix ConciseView to show Activity instead of myCommand (#11007) (Beknopte #11007)
- Web-cmdlets toestaan http-foutstatussen (#10466) te negeren (bedankt @vdamewood !)
- Het doorspijpen van meer dan één CommandInfo naar Get-Command (#10929)
- Back-Get-Counter cmdlet voor Windows (#10933)
- Zorg ConvertTo-Json [AutomationNull]::Value en [NullString]::Value behandelen als $null (#10957)
- Haakjes verwijderen van ipv6-adres voor SSH-remoting (#10968)
- Crash oplossen als de opdracht die naar pwsh wordt verzonden alleen witruimte is (#10977)
- Platformoverschrijdende Get-Clipboard en Set-Clipboard (#10340)
- Probleem opgelost bij het instellen van het oorspronkelijke pad van het bestandssysteemobject om geen extra schuine streep (#10959)
- Ondersteuning$ $null voor ConvertTo-Json (#10947)
- Back-Out-Printer toevoegen in Windows (#10906)
- Oplossing Start-Job -WorkingDirectory met witruimte (#10951)
- Retourneert de standaardwaarde wanneer null wordt geretourneerd voor een instelling in PSConfiguration.cs (#10963) (Bedankt @iSazonov !)
- I/O-uitzondering verwerken als niet-#10950)
- Voeg een GraphicalHost-assembly toe om Out-GridView, Show-Command en Get-Help -ShowWindow (#10899)
- Neem ComputerName via pijplijn in Get-HotFix (#10852) (bedankt @kvprasoon !)
- Tab-voltooiing voor parameters opgelost, zodat algemene parameters als beschikbaar worden weergegeven (#10850)
- Probleem opgelost met GetCorrectCasedPath() om eerst te controleren of er vermeldingen in het systeembestand worden geretourneerd voordat u First() (#10930)
- Stel working directory in op current directory in Start-Job (#10920) (Bedankt @iSazonov !)
- Wijzig TabExpansion2 om -CursorColumn niet te vereisen en te behandelen als $InputScript.Length (#10849)
- Handle case where Host may not return Rows or Columns of screen (#10938)
- Probleem opgelost met het gebruik van accentkleuren voor hosts die deze niet ondersteunen (#10937)
- Back-Update-List (#10922)
- FWLink-id bijwerken voor Clear-RecycleBin (#10925)
- Sla het bestand tijdens het voltooien van het tabblad over als bestandskenmerken niet kunnen worden gelezen (#10910)
- Back-Clear-RecycleBin voor Windows (#10909)
- Toevoegen `$env:__SuppressAnsiEscapeSequences` om te bepalen of de VT-escapereeks moet worden uitgevoerd (#10814)
- Parameter -NoEmphasize toevoegen om de uitvoer Select-String kleuren (#8963) (bedankt @derek-xia !)
- Back-Get-HotFix cmdlet (#10740)
- Maak Add-Type bruikbaar in toepassingen die PowerShell hosten (#10587)
- Gebruik een effectievere evaluatie volgorde in LanguagePrimitives.IsNullLike() (#10781) (Bedankt @vexx32 !)
- De verwerking verbeteren van invoer met gemengde verzamelingspijpen en doorspijpstromen van invoer in Format-Hex (#8674) (Bedankt @vexx32 !)
- Gebruik typeconversie in hashtabels van SSHConnection wanneer de waarde niet overeen komt met het verwachte type (#10720) (Bedankt @SeeminglyScience !)
- Probleem Get-Content -ReadCount 0 opgelost wanneer -TotalCount is ingesteld (#10749) (Bedankt @eugenesmlv !)
- Foutbericht toegang geweigerd in Get-WinEvent (#10639) (Bedankt @iSazonov !)
- Tab-voltooiing inschakelen voor variabeletoewijzing die beperkt is of van het type is beperkt (#10646)
- Verwijder ongebruikte eigenschap voor het buiten gebruik hebben van SourceLength, wat opmaakproblemen veroorzaakt (#10765)
- Parameter -Delimiter toevoegen aan ConvertFrom-StringData (#10665) (Bedankt @steviecoaster !)
- Positionele parameter voor ScriptBlock toevoegen bij gebruik van Invoke-Command met SSH (#10721) (Bedankt @machgo !)
- Informatie over regelcontext tonen als er meerdere regels zijn, maar geen scriptnaam voor ConciseView (#10746)
- Ondersteuning toegevoegd voor \\ wsl$\-paden naar bestandssysteemprovider (#10674)
- De ontbrekende tokentekst voor TokenKind.QuestionMark toevoegen aan parser (#10706)
- Stel de huidige werkmap van elke ForEach-Object -Parallel uitvoerend script in op dezelfde locatie als het aanroepend script. (#10672)
- Vervang api-ms-win-core-file-l1-2-2.dll door Kernell32.dll findfirstStreamW en FindNextStreamW-API's (#10680) (bedankt @iSazonov !)
- Help-opmaakscript aanpassen om StrictMode toleranter (#10563)
- Parameter -SecurityDescriptorSDDL toevoegen aan New-Service (#10483) (bedankt @kvprasoon !)
- Gegevensuitvoer verwijderen, pinggebruik consolideren in Test-Connection (#10478) (Bedankt @vexx32 !)
- Lees speciale reparsepunten zonder ze te openen (#10662) (bedankt @iSazonov !)
- Direct Clear-Host output to terminal (#10681) (Bedankt @iSazonov !)
- Nieuwe lijn toevoegen voor groeperen met Format-Table en -Eigenschap (#10653)
- Verwijder [ValidateNotNullOrEmpty] uit -InputObject op Get-Random lege tekenreeks toe te staan (#10644)
- Maak het algoritme voor de tekenreeksafstand van het suggestiesysteem niet-#10549 (bedankt @iSazonov !)
- Probleem met null-verwijzing opgelost in ForEach-Object - Parallelle invoerverwerking (#10577)
- Definities PowerShell Core groepsbeleid toevoegen (#10468)
- Werk de consolehost bij voor de ondersteuning van XTPUSHSGR/XTPOPSGR VT-besturingsreeksen die worden gebruikt in scenario's met opstellen. (#10208)
- Parameter WorkingDirectory toevoegen aan Start-Job (#10324) (Bedankt @davinci26 !)
- Verwijder de gebeurtenis-handler waardoor onderbrekingspuntwijzigingen ten onrechte zijn gerepliceerd naar het foutopsporingspunt van de hostrunspace (#10503) (bedankt @KirkMunro !)
- Vervang api-ms-win-core-job-12-1-0.dll door Kernell32.dll in Microsoft.PowerShell.Commands.NativeMethods P/Invoke API(#10417) (bedankt @iSazonov !)
- Foute uitvoer voor New-Service in variabele toewijzing en -OutVariable (#10444) (bedankt @kvprasoon !)
- Problemen met globale hulpprogramma's met betrekking tot de afsluitende code, opdrachtregelparameters en het pad met spaties (#10461)
- Recursie in OneDrive herstellen: wijzig FindFirstFileEx() in safeFindHandle-type (#10405)
- Het automatisch laden van PSReadLine in Windows overslaan als de NVDA-schermlezer actief is (#10385)
- Ingebouwde met PowerShell-moduleversies verhogen naar 7.0.0.0 (#10356)
- Voeg een foutmelding toe aan Add-Type als er al een type met dezelfde naam bestaat (#9609) (Bedankt @iSazonov !)

### <a name="performance"></a>Prestaties

- Vermijd het gebruik van sluiting in Parser.SaveError (#11006)
- De caching verbeteren bij het maken van nieuwe Regex-exemplaren (#10657) (Bedankt @iSazonov !)
- De verwerking van de ingebouwde PowerShell-typegegevens van types.ps1xml, typesV3.ps1xml en GetEvent.types.ps1xml (#10898) verbeteren
- WERK PSConfiguration.ReadValueFromFile bij om het sneller en efficiënter te maken (#10839)
- Kleine prestatieverbeteringen toevoegen voor runspace-initialisatie (#10569) (Bedankt @iSazonov !)
- Maak ForEach-Object sneller voor de veelgebruikte scenario's (#10454) en los ForEach-Object -Parallel-prestatieprobleem op met veel runspaces (#10455)

### <a name="code-cleanup"></a>Code opschonen

- Opmerking en elementtekst wijzigen om te voldoen aan microsoft-standaarden (#11304)
- Problemen met opschoningsstijl in Compiler.cs (#10368) (Bedankt @iSazonov !)
- Verwijder de niet-gebruikte typeconverter voor CommaDelimitedStringCollection (#11000) (Bedankt @iSazonov !)
- Opschoningsstijl in InitialSessionState.cs (#10865) (bedankt @iSazonov !)
- Code ops schonen voor pssession-klasse (#11001)
- Verwijder de niet-werkende functie 'run Update-Help uit Get-Help wanneer Get-Help voor het eerst wordt uitgevoerd' (#10974)
- Stijlproblemen oplossen (#10998) (Bedankt @iSazonov !)
- Opschonen: gebruik de ingebouwde typealias (#10882) (Bedankt @iSazonov !)
- Verwijder de niet-gebruikte instellingssleutel ConsolePrompting en vermijd onnodig maken van tekenreeksen bij het uitvoeren van query's op executionpolicy-instelling (#10985)
- Controle van updatemeldingen uitschakelen voor dagelijkse builds (#10903) (bedankt @bergmeister !)
- De API voor het herstellen van debuggen in #10338 (#10808)
- Verwijder de referentie WorkflowJobSourceAdapter die niet meer wordt gebruikt (#10326) (Bedankt @KirkMunro !)
- COM-interfaces in jumplist-code opschonen door PreserveSig-kenmerken (#9899) op te schonen (bedankt @weltkante !)
- Voeg een opmerking toe waarin wordt beschreven waarom -ia niet de alias is voor de algemene parameter -InformationAction (#10703) (Bedankt @KirkMunro !)
- Wijzig de naam invokeCommandCmdlet.cs in InvokeExpressionCommand.cs (#10659) (bedankt @kilasuit !)
- Kleine code-opschoningen toevoegen met betrekking tot updatemeldingen (#10698)
- Afgeschafte werkstroomlogica verwijderen uit de installatiescripts voor remoting (#10320) (Bedankt @KirkMunro !)
- Help-indeling bijwerken voor het gebruik van de juiste case (#10678) (Bedankt @tnieto88 !)
- Problemen met de CodeFactor-stijl opseen die in de afgelopen maand zijn #10591 (bedankt @iSazonov !)
- Typfout in beschrijving van experimentele functie PSTernaryOperator (#10586) opgelost (bedankt @bergmeister !)
- Convert ActionPreference.Suspend enumeration value into a non-supported, reserved state, and remove restriction on using ActionPreference.Ignore in preference variables (#10317) (Bedankt @KirkMunro !)
- Vervang ArrayList door List om beter leesbare en betrouwbare code te krijgen zonder de functionaliteit \<T> (#10333) te wijzigen (bedankt @iSazonov !)
- Maak codestijlfixes voor TestConnectionCommand (#10439) (bedankt @vexx32 !)
- AutomationEngine opschonen en extra methode-aanroep setSessionStateDrive (#10416) verwijderen (bedankt @iSazonov !)
- Wijzig de naam van de standaardParameterSetName weer in Scheidingsteken voor ConvertTo-Csv en ConvertFrom-Csv (#10425)

### <a name="tools"></a>Hulpprogramma's

- Voeg de standaardinstelling toe voor de eigenschap SDKToUse, zodat deze wordt opgebouwd in VS (#11085)
- Install-Powershell.ps1: Parameter toevoegen voor het gebruik van MSI-installatie (#10921) (Bedankt @MJECloud !)
- Eenvoudige voorbeelden toevoegen voor install-powershell.ps1 (#10914) (bedankt @kilasuit !)
- Maak Install-PowerShellRemoting.ps1 lege tekenreeks in de parameter PowerShellHome (#10526) (Bedankt @Orca88 !)
- Schakel over van /etc/lsb-release naar /etc/os-release in install-powershell.sh (#10773) (Bedankt @Himura2la !)
- Controleer pwsh.exe en pwsh in de dagelijkse versie in Windows (#10738) (Bedankt @centreboard !)
- Verwijder onnodig tikken in installpsh-osx.sh (#10752)
- Werk install-powershell.ps1 bij om te controleren of de dagelijkse build al is geïnstalleerd (#10489)

### <a name="tests"></a>Testen

- Onbetrouwbare DSC-test in behandeling maken (#11131)
- Probleem met stringdata-test opgelost om sleutels van hashtabels correct te valideren (#10810)
- Testmodules (#11061) uit het geheugen verwijderd (bedankt @iSazonov !)
- Tijd tussen nieuwe test-URL's (#11015)
- Werk tests bij om testacties nauwkeurig te beschrijven. (#10928) (Bedankt @romero126 !)
- Sla de test TestAppDomainProcessExitEvenHandlerNotLeaking (#10827) tijdelijk over
- De gebeurtenis-handler stabiel laten lekken (#10790)
- Synchronisatie-hoofdletters in CI YAML (#10767) (Bedankt @RDIL !)
- Test toevoegen voor het lekken van de gebeurtenis-handler (#10768)
- Een Get-ChildItem test (#10507) toevoegen (bedankt @iSazonov !)
- Vervang ambigue taal voor tests van overschakelen naar parameter voor nauwkeurigheid (#10666) (Bedankt @romero126 !)
- Experimentele controle toevoegen aan ForEach-Object -Parallelle tests (#10354) (Bedankt @KirkMunro !)
- Updatetests voor Alpine-validatie (#10428)

### <a name="build-and-package-improvements"></a>Verbeteringen in de build en het pakket

- Probleem opgelost met nuget-pakket-ondertekening voor Coordinated Package build (#11316)
- Afhankelijkheden van PowerShell Gallery en NuGet (#11323)
- Microsoft.ApplicationInsights van 2.11.0 naar 2.12.0 (#11305)
- Microsoft.CodeAnalysis.CSharp van 3.3.1 naar 3.4.0 (#11265)
- Updates-pakketten voor Debian 10 en 11 (#11236)
- Schakel experimentele functies alleen in vóór RC (#11162)
- Minimale macOS-versie bijwerken (#11163)
- Bump NJsonSchema van 10.0.27 naar 10.0.28 (#11170)
- Koppelingen bijwerken in README.md en metadata.jspreview.5 (#10854)
- Selecteer de bestanden voor nalevingstests die eigendom zijn van PowerShell (#10837)
- Sta toe dat het win7x86 msix-pakket wordt gebouwd. (Intern 10515)
- Toestaan dat semantische versies worden doorgegeven aan de functie NormalizeVersion (#11087)
- Bump .NET Core Framework naar 3.1-preview.3 (#11079)
- Bump PSReadLine van 2.0.0-beta5 naar 2.0.0-beta6 in /src/Modules (#11078)
- Bump Newtonsoft.Jsvan 12.0.2 tot 12.0.3 (#11037) (#11038)
- Debian 10-, 11- en CentOS 8-pakketten (#11028)
- Upload Build-Info Json-bestand met het veld ReleaseDate (#10986)
- Bump .NET Core Framework naar 3.1-preview.2 (#10993)
- Build van x86 MSIX-pakket inschakelen (#10934)
- Werk de url voor het dotnet-SDK-installatiescript bij in build.psm1 (#10927)
- Bump Markdig.Signed van 0.17.1 tot 0.18.0 (#10887)
- Bump ThreadJob van 2.0.1 tot 2.0.2 (#10886)
- Module AppX-manifest en -verpakking bijwerken om te voldoen aan de MS Store-vereisten (#10878)
- Update package reference for PowerShell SDK to preview.5 (Internal 10295) (Pakketverwijzing voor PowerShell SDK bijwerken naar preview.5 (Internal 10295)
- Update ThirdPartyNotices.txt (#10834)
- Bump Microsoft.PowerShell.Native naar 7.0.0-preview.3 (#10826)
- Microsoft.ApplicationInsights van 2.10.0 naar 2.11.0 (#10608)
- Bump NJsonSchema van 10.0.24 naar 10.0.27 (#10756)
- MacPorts-ondersteuning toevoegen aan het buildsysteem (#10736) (Bedankt @Lucius-Q-User !)
- Bump PackageManagement van 1.4.4 tot 1.4.5 (#10728)
- Bump NJsonSchema van 10.0.23 naar 10.0.24 (#10635)
- Omgevingsvariabele toevoegen om onderscheid te maken tussen client-/server-telemetrie in MSI (#10612)
- Bump PSDesiredStateConfiguration van 2.0.3 naar 2.0.4 (#10603)
- Bump Microsoft.CodeAnalysis.CSharp van 3.2.1 naar 3.3.1 (#10607)
- Bijwerken naar .Net Core 3.0 RTM (#10604) (bedankt @bergmeister !)
- MSIX-verpakking bijwerken zodat de versie voldoet aan de Windows Store-vereisten (#10588)
- Bump PowerShellGet-versie van 2.2 naar 2.2.1 (#10382)
- Bump PackageManagement versie van 1.4.3 tot 1.4.4 (#10383)
- Update README.md and metadata.json for 7.0.0-preview.4 (Internal 10011)
- .Net Core 3.0-versie upgraden van Preview 9 naar RC1 (#10552) (bedankt @bergmeister !)
- ExperimentalFeature-lijstgeneratie opgelost (interne 9996)
- Bump PSReadLine-versie van 2.0.0-beta4 naar 2.0.0-beta5 (#10536)
- Buildscript van release opgelost om releasetag in te stellen
- Versie van Microsoft.PowerShell.Native bijgewerkt naar 7.0.0-preview.2 (#10519)
- Upgrade naar Netcoreapp3.0 preview9 (#10484) (bedankt @bergmeister !)
- Zorg ervoor dat de dagelijkse gecoördineerde build weet dat het een dagelijkse build is (#10464)
- Werk de gecombineerde pakket-build bij om de dagelijkse builds (#10449)
- Verwijzing appveyor (#10445) verwijderen (bedankt @RDIL !)
- Bump NJsonSchema-versie van 10.0.22 tot 10.0.23 (#10421)
- Verwijder de verwijdering van de buildmap linux-x64 omdat sommige afhankelijkheden voor Alpine deze nodig hebben (#10407)

### <a name="documentation-and-help-content"></a>Documentatie en Help-inhoud

- Wijzigingslogboeken herfactoren in één logboek per release (#11165)
- Probleem opgelost met online Help-documenten voor FWLinks voor PowerShell 7 (#11071)
- Werk CONTRIBUTING.md (#11096) bij (bedankt @mklement0 !)
- Koppelingen naar installatie docs in README.md (#11083)
- Voegt voorbeelden toe aan install-powershell.ps1 script (#11024) (bedankt @kilasuit !)
- Oplossing voor Select-String nadruk en Import-DscResource in CHANGELOG.md (#10890)
- Verwijder de verouderde koppeling uit powershell-beginners-guide.md (#10926)
- Stabiele wijzigingslogboeken en onderhoudswijzigingslogboeken samenvoegen (#10527)
- Gebruikte .NET-versie bijgewerkt in build docs (#10775) (Bedankt @Greg-Smulko !)
- Koppelingen van MSDN vervangen docs.microsoft.com in powershell-beginners-guide.md (#10778) (Bedankt @iSazonov !)
- Verbroken DSC-overzichtskoppeling (#10702)
- Werk Support_Question.md bij om een koppeling naar Stack Overflow te maken als een andere communityresource (#10638) (Bedankt @mklement0 !)
- Processorarchitectuur toevoegen aan distributieaanvraagsjabloon (#10661)
- Nieuw PowerShell MoL-boek toevoegen om PowerShell-documenten (#10602)
- De README.md en metagegevens bijwerken voor versies van v6.1.6 en v6.2.3 (#10523)
- Typfout in README.md (#10465) opgelost (bedankt @vedhasp !)
- Voeg een verwijzing naar de PSKoans-module toe aan de documentatie over Learning Resources (#10369) (Bedankt @vexx32 !)
- Update README.md and metadata.json for 7.0.0-preview.3 (#10393)
