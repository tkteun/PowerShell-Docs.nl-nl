---
ms.date: 12/14/2020
title: Experimentele functies gebruiken in Power shell
description: Een lijst met de momenteel beschik bare experimentele functies en hoe u deze kunt gebruiken.
ms.openlocfilehash: 556ae8d877b670b119b7b5b958a52488aad16241
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500120"
---
# <a name="using-experimental-features-in-powershell"></a>Experimentele functies gebruiken in Power shell

De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.

Een experimentele functie is een onderdeel waar het ontwerp niet is voltooid. De functie is beschikbaar voor gebruikers om te testen en feedback te geven. Zodra een experimentele functie is voltooid, worden de wijzigingen in het ontwerp doorgevoerd.

> [!CAUTION]
> Experimentele functies zijn niet bedoeld om te worden gebruikt in productie, omdat de wijzigingen niet mogen worden opgesplitst. Experimentele functies worden niet officieel ondersteund. We waarderen echter alle feedback-en fouten rapporten. U kunt problemen in de [github-bron opslagplaats](https://github.com/PowerShell/PowerShell/issues/new/choose)opslaan.

Zie [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)voor meer informatie over het in-of uitschakelen van deze functies.

## <a name="available-features"></a>Beschikbare functies

In dit artikel worden de experimentele functies beschreven die beschikbaar zijn en hoe u deze functie kunt gebruiken.

|                            Name                            |   6,2   |   7.0   |   7.1   |   7.2   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| PSTempDrive (mainstream in PS 7.0 +)                        | &check; |         |         |         |
| PSUseAbbreviationExpansion (mainstream in PS 7.0 +)         | &check; |         |         |         |
| PSNullConditionalOperators (mainstream in PS 7.1 +)         |         | &check; |         |         |
| PSUnixFileStat (alleen niet-Windows-mainstream in PS 7.1 +)  |         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; | &check; |
| Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace |         | &check; | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; | &check; |
| PSNativePSPathResolution                                   |         |         | &check; | &check; |
| PSCultureInvariantReplaceOperator                          |         |         | &check; | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; | &check; |
| PSSubsystemPluginModel                                     |         |         | &check; | &check; |
| PSAnsiProgress                                             |         |         |         | &check; |
| PSAnsiRendering                                            |         |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace

In Power shell 7,0 stelt het experiment de para meter **BreakAll** in op de `Debug-Runspace` `Debug-Job` cmdlets, zodat gebruikers kunnen bepalen of ze Power shell onmiddellijk op de huidige locatie moeten afkraken wanneer ze een debugger koppelen.

In Power shell 7,1 voegt dit experiment ook de **runs Pace** -para meter toe aan de `*-PSBreakpoint` cmdlets.

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

De para meter **runs Pace** geeft een **runs Pace** -object op om te communiceren met onderbrekings punten in de opgegeven runs Pace.

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

In dit voor beeld wordt een taak gestart en wordt een onderbrekings punt ingesteld op break wanneer de `Set-PSBreakPoint` wordt uitgevoerd. De runs Pace wordt opgeslagen in een variabele en door gegeven aan de `Get-PSBreakPoint` opdracht met de para meter **runs Pace** . U kunt vervolgens het onderbrekings punt in de variabele inspecteren `$breakpoint` .

## <a name="psansirendering"></a>PSAnsiRendering

Dit experiment is toegevoegd aan Power shell 7,2. Met de functie kunt u wijzigingen aanbrengen in de manier waarop de Power shell-engine tekst uitvoer en de `$PSStyle` Automatische variabele toevoegen om de ANSI-rendering van teken reeks uitvoer te beheren.

```powershell
PS> $PSStyle

Name            MemberType Definition
----            ---------- ----------
Reset           Property   string AttributesOff {get;set;}
Background      Property   System.Management.Automation.PSStyle+BackgroundColor Background {get;set;}
Blink           Property   string Blink {get;set;}
BlinkOff        Property   string BlinkOff {get;set;}
Bold            Property   string Bold {get;set;}
BoldOff         Property   string BoldOff {get;set;}
Foreground      Property   System.Management.Automation.PSStyle+ForegroundColor Foreground {get;set;}
Formatting      Property   System.Management.Automation.PSStyle+FormattingData Formatting {get;set;}
Hidden          Property   string Hidden {get;set;}
HiddenOff       Property   string HiddenOff {get;set;}
OutputRendering Property   System.Management.Automation.OutputRendering OutputRendering {get;set;}
Reverse         Property   string Reverse {get;set;}
ReverseOff      Property   string ReverseOff {get;set;}
Italic          Property   string Standout {get;set;}
ItalicOff       Property   string StandoutOff {get;set;}
Underline       Property   string Underlined {get;set;}
Underline Off   Property   string UnderlinedOff {get;set;}
```

De basis leden retour neren teken reeksen van ANSI-escape reeksen die zijn toegewezen aan hun namen. De waarden kunnen worden ingesteld om aanpassing mogelijk te maken.

Zie [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) voor meer informatie.

> [!NOTE]
> Voor C#-ontwikkel aars kunt u `PSStyle` als Singleton toegang krijgen. Gebruik ziet er als volgt uit:
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> `PSStyle` bestaat in de naam ruimte System. Management. Automation.

Naast de toegang tot `$PSStyle` , worden er wijzigingen aangebracht in de Power shell-engine. Het Power shell-opmaak systeem is bijgewerkt met betrekking tot `$PSStyle.OutputRendering` .

- `StringDecorated` type wordt toegevoegd voor het verwerken van teken reeksen met ANSI-Escapes.
- `string IsDecorated` Er wordt een Boole-eigenschap toegevoegd om te retour neren als de teken reeks ANSI-escape reeksen bevat op basis van als de teken reeks ESC of C1 CSI bevat.
- De `Length` eigenschap retourneert _alleen_ de lengte van de tekst zonder de ANSI-escape reeksen.
- `StringDecorated Substring(int contentLength)` methode retourneert een subtekenreeks die begint bij index 0 tot aan de lengte van de inhoud die geen deel uitmaakt van ANSI-escape reeksen. Dit is nodig voor het afkappen van teken reeksen en het behouden van ANSI-escape reeksen die geen afdruk bare teken ruimte innemen.
- `string ToString()` de methode blijft hetzelfde en retourneert de ongecodeerde versie van de teken reeks.
- `string ToString(bool Ansi)` methode retourneert de onbewerkte ANSI-teken reeks als de `Ansi` para meter waar is. Anders wordt een niet-gecodeerde versie met ANSI-escape reeksen verwijderd.

## <a name="psansiprogress"></a>PSAnsiProgress

Dit experiment is toegevoegd aan Power shell 7,2. De functie voegt het `$PSStyle.Progress` lid toe en stelt u in staat om de weer gave van de voortgangs weergave te beheren.

- `$PSStyle.Progress.Style` -Een ANSI-teken reeks die de weergave stijl instelt.
- `$PSStyle.Progress.MaxWidth` : Hiermee stelt u de maximale breedte van de weer gave. Stel in `0` voor de breedte van de console.
  Wordt standaard ingesteld op `120`
- `$PSStyle.Progress.View` -Een enum met waarden `Minimal` en `Classic` . `Classic` is de bestaande rendering zonder wijzigingen. `Minimal` is een minimale rendering van één regel. `Minimal` is de standaardwaarde.

In het volgende voor beeld wordt de stijl rendering bijgewerkt naar een minimale voortgangs balk.

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> U kunt deze functie alleen gebruiken als u de experimentele functie **PSAnsiRendering** hebt ingeschakeld.

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

Raadt potentiële opdrachten aan op basis van zoek acties op fuzzy na een **CommandNotFoundException**.

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a>PSCultureInvariantReplaceOperator

Wanneer de linkeroperand in een `-replace` operator instructie geen teken reeks is, wordt die operand geconverteerd naar een teken reeks.

Als deze functie is uitgeschakeld, `-replace` heeft de operator een cultuur gevoelige teken reeks conversie.
Als uw cultuur bijvoorbeeld is ingesteld op Frans (FR), wordt de waarde `1.2` geconverteerd naar de teken reeks `1,2` .

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

Als de functie is ingeschakeld:

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

Hiermee wordt de compilatie op MOF op niet-Windows-systemen ingeschakeld en wordt het gebruik van `Invoke-DSCResource` zonder LCM ingeschakeld.

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

Met deze functie wordt de in de shell getypte opdracht onderzocht. als alle opdrachten impliciet externe proxy opdrachten zijn die een eenvoudige pijp lijn vormen, worden de opdrachten in batch verzameld en aangeroepen als één externe pijp lijn.

Voorbeeld:

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

Zoals hierboven wordt weer gegeven, terwijl de batch functie is ingeschakeld, worden alle drie de impliciete externe proxy opdrachten,,,, `Get-AllProcesses` `Select-Custom` `Group-Stuff` uitgevoerd in de externe sessie en het resultaat van de pijp lijn de enige gegevens die worden geretourneerd naar de client. Dit vermindert de hoeveelheid gegevens die wordt verzonden tussen de client en de externe sessie, en vermindert ook de hoeveelheid object-serialisatie en deserialisatie.

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

Als een PSDrive-pad dat gebruikmaakt van de File System Provider wordt door gegeven aan een systeem eigen opdracht, wordt het omgezette bestandspad door gegeven aan de systeem eigen opdracht. Dit betekent dat een opdracht zoals `code temp:/test.txt` nu werkt zoals verwacht.

Ook in Windows, als het pad begint met `~` , dat wordt omgezet naar het volledige pad en wordt door gegeven aan de systeem eigen opdracht. In beide gevallen wordt het pad genormaliseerd naar de adres lijst scheidings tekens voor het relevante besturings systeem.

- Als het pad geen PSDrive of `~` (in Windows) is, treedt de normalisatie van het pad niet op
- Als het pad zich in enkele aanhalings tekens bevindt, wordt het niet opgelost en behandeld als een letterlijke waarde

## <a name="psnotapplyerroractiontostderr"></a>PSNotApplyErrorActionToStderr

Wanneer deze experimentele functie is ingeschakeld, worden fout records die worden omgeleid van systeem eigen opdrachten, zoals het gebruik van omleidings operatoren ( `2>&1` ), niet naar de `$Error` variabele geschreven en is de voorkeurs variabele niet van `$ErrorActionPreference` invloed op de omgeleide uitvoer.

Veel systeem eigen opdrachten schrijven naar `stderr` als alternatieve stroom voor aanvullende informatie. Dit gedrag kan leiden tot Verwar ring bij het opzoeken van fouten of de aanvullende uitvoer gegevens kunnen verloren gaan voor de gebruiker als deze `$ErrorActionPreference` is ingesteld op een status die de uitvoer dempt.

Wanneer een systeem eigen opdracht een afsluit code heeft die niet gelijk is aan nul, `$?` wordt ingesteld op `$false` . Als de afsluit code nul is, `$?` wordt ingesteld op `$true` .

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

Hierin worden nieuwe Opera tors geïntroduceerd voor de null-Opera tors voor voorwaardelijke toegang, `?.` en `?[]` . Toegangs operatoren voor Null-leden kunnen worden gebruikt voor scalaire typen en matrix typen. Retourneert de waarde van het geopende lid als de variabele niet null is. Als de waarde van de variabele null is, retourneert dan Null.

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

De eigenschap `propname` is toegankelijk en de waarde ervan wordt alleen geretourneerd als deze `$x` niet null is. De Indexeer functie wordt op dezelfde manier gebruikt als `$x` niet null is. Als `$x` is null is, wordt Null geretourneerd.

De `?.` `?[]` Opera tors en zijn lid van de operator toegang en staan geen ruimte tussen de naam van de variabele en de operator toe.

Omdat Power shell `?` als onderdeel van de naam van de variabele is toegestaan, is ondubbelzinnige installatie vereist wanneer de Opera tors worden gebruikt zonder ruimte tussen de naam van de variabele en de operator. Voor dubbel zinnigheid moeten de variabelen worden gebruikt `{}` om de naam van de variabele te gebruiken, zoals: `${x?}?.propertyName` of `${y}?[0]` .

> [!NOTE]
> Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7,1 en hoger.

## <a name="pstempdrive"></a>PSTempDrive

Hiermee maakt `TEMP:` u de PSDrive die is toegewezen aan het pad naar de tijdelijke map van de gebruiker.

> [!NOTE]
> Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.

## <a name="psunixfilestat"></a>PSUnixFileStat

Deze functie biedt nieuw gedrag om gegevens op te nemen uit de UNIX **stat** -API in de uitvoer van de bestandssysteem provider om een meer Unix-achtige bestands vermelding te vergemakkelijken. Er wordt een nieuwe notitie-eigenschap toegevoegd aan de bestandssysteem provider met de naam **UnixStat** die een gemeen schappelijke expressie van de `stat(2)` API van het onderliggende UNIX-type systeem bevat.

De uitvoer van `Get-ChildItem` moet er ongeveer als volgt uitzien:

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

> [!NOTE]
> Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7,1 en hoger.

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

Met deze functie kunt u het tabblad volt ooien van verkorte cmdlets en functies:

Bijvoorbeeld:

- `i-psdf<tab>` retourneert `Import-PowerShellDataFile` .
- `u-akvmssdr<tab>` retourneert `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`

Dit werkt alleen voor tabblad voltooiing (interactief gebruik), dus `i-psdf` is geen geldige cmdlet-naam in een script.

> [!NOTE]
> Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.

## <a name="pssubsystempluginmodel"></a>PSSubsystemPluginModel

Met deze functie wordt het subsysteem voor de invoeg toepassing in Power shell ingeschakeld. De functie maakt het mogelijk om onderdelen van te scheiden `System.Management.Automation.dll` in afzonderlijke subsystemen die zich in hun eigen assembly bevinden. Deze schei ding vermindert het schijf gebruik van de kern-Power shell-engine en maakt het mogelijk dat deze onderdelen optionele functies worden voor een minimale Power shell-installatie.

Op dit moment wordt alleen het subsysteem **CommandPredictor** ondersteund. Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste Voorspellings-invoeg toepassingen te bieden. In de toekomst kunnen **Job**, **CommandCompleter**, **Remoting** en andere onderdelen worden gescheiden in subsysteem-assembly's buiten `System.Management.Automation.dll` .

Het experimentele onderdeel bevat een nieuwe cmdlet [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem). Deze cmdlet is alleen beschikbaar wanneer de functie is ingeschakeld. Deze cmdlet retourneert informatie over de subsystemen die beschikbaar zijn op het systeem.
