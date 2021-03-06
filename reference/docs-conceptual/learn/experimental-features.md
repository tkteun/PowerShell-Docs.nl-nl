---
ms.date: 04/19/2021
title: Experimentele functies gebruiken in PowerShell
description: Geeft een lijst weer van de momenteel beschikbare experimentele functies en hoe u deze kunt gebruiken.
ms.openlocfilehash: a91dd633f2f61d53a78ec02df0515dd72f282f04
ms.sourcegitcommit: 2ad76cd528338f8c2cc10a84c5c56c0e25b93436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/19/2021
ms.locfileid: "107729881"
---
# <a name="using-experimental-features-in-powershell"></a>Experimentele functies gebruiken in PowerShell

De ondersteuning voor experimentele functies in PowerShell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in PowerShell- of PowerShell-modules kunnen worden gebruikt.

Een experimentele functie is een functie waarbij het ontwerp niet is afgerond. De functie is beschikbaar voor gebruikers om te testen en feedback te geven. Zodra een experimentele functie is afgerond, worden de ontwerpwijzigingen belangrijke wijzigingen.

> [!CAUTION]
> Experimentele functies zijn niet bedoeld om te worden gebruikt in productie, omdat de wijzigingen mogen worden doorgevoerd. Experimentele functies worden niet officieel ondersteund. We stellen feedback en foutrapporten echter zeer op prijs. U kunt problemen in de [GitHub-bronopslagplaats indienen.](https://github.com/PowerShell/PowerShell/issues/new/choose)

Zie voor meer informatie over het in- of uitschakelen van [deze functies about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).

## <a name="available-features"></a>Beschikbare functies

In dit artikel worden de experimentele functies beschreven die beschikbaar zijn en hoe u de functie gebruikt.

|                            Name                            |   6,2   |   7.0   |   7.1   |   7.2   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| PSTempDrive (standaard in PS 7.0+)                        | &check; |         |         |         |
| PSUseAbbreviationExpansion (mainstream in PS 7.0+)         | &check; |         |         |         |
| PSNullConditionalOperators (standaard in PS 7.1+)         |         | &check; |         |         |
| PSUnixFileStat (alleen niet-Windows- gangbaar in PS 7.1+)  |         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; | &check; |
| Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace |         | &check; | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; | &check; |
| PSNativePSPathResolution                                   |         |         | &check; | &check; |
| PSAtriceeInvariantReplaceOperator                          |         |         | &check; | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; | &check; |
| PSSubsystemPluginModel                                     |         |         | &check; | &check; |
| PSAnsiProgress                                             |         |         |         | &check; |
| PSAnsiRendering                                            |         |         |         | &check; |
| PSNativeCommandArgumentPassing                             |         |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace

In PowerShell 7.0 schakelt het experiment de parameter **BreakAll** in op de cmdlets en om gebruikers in staat te stellen te bepalen of ze willen dat PowerShell direct wordt beschadigd op de huidige locatie wanneer ze een `Debug-Runspace` `Debug-Job` debugger koppelen.

In PowerShell 7.1 voegt dit experiment ook de parameter **Runspace** toe aan de `*-PSBreakpoint` cmdlets.

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

De **Runspace** parameter geeft u een **Runspace-object** om te communiceren met onderbrekingspunten in de opgegeven runspace.

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

In dit voorbeeld wordt een taak gestart en wordt een onderbrekingspunt ingesteld op break wanneer `Set-PSBreakPoint` de wordt uitgevoerd. De runspace wordt opgeslagen in een variabele en doorgegeven aan de `Get-PSBreakPoint` opdracht met de parameter **Runspace.** Vervolgens kunt u het onderbrekingspunt in de variabele `$breakpoint` inspecteren.

## <a name="psansirendering"></a>PSAnsiRendering

Dit experiment is toegevoegd in PowerShell 7.2. Met de functie kunt u wijzigen hoe de PowerShell-engine tekst uitvoert en de automatische variabele toevoegen `$PSStyle` om de ANSI-rendering van tekenreeksuitvoer te bepalen.

```powershell
PS> $PSStyle | Get-Member

   TypeName: System.Management.Automation.PSStyle

Name             MemberType Definition
----             ---------- ----------
Equals           Method     bool Equals(System.Object obj)
FormatHyperlink  Method     string FormatHyperlink(string text, uri link)
GetHashCode      Method     int GetHashCode()
GetType          Method     type GetType()
ToString         Method     string ToString()
Background       Property   System.Management.Automation.PSStyle+BackgroundColor Background {get;}
Blink            Property   string Blink {get;}
BlinkOff         Property   string BlinkOff {get;}
Bold             Property   string Bold {get;}
BoldOff          Property   string BoldOff {get;}
Foreground       Property   System.Management.Automation.PSStyle+ForegroundColor Foreground {get;}
Formatting       Property   System.Management.Automation.PSStyle+FormattingData Formatting {get;}
Hidden           Property   string Hidden {get;}
HiddenOff        Property   string HiddenOff {get;}
Italic           Property   string Italic {get;}
ItalicOff        Property   string ItalicOff {get;}
OutputRendering  Property   System.Management.Automation.OutputRendering OutputRendering {get;set;}
Progress         Property   System.Management.Automation.PSStyle+ProgressConfiguration Progress {get;}
Reset            Property   string Reset {get;}
Reverse          Property   string Reverse {get;}
ReverseOff       Property   string ReverseOff {get;}
Strikethrough    Property   string Strikethrough {get;}
StrikethroughOff Property   string StrikethroughOff {get;}
Underline        Property   string Underline {get;}
UnderlineOff     Property   string UnderlineOff {get;}
```

De basisleden retourneren tekenreeksen van ANSI-escapereeksen die aan hun namen zijn toe te geven. De waarden kunnen worden ingesteld om aanpassingen toe te staan.

Zie voor meer informatie [about_Automatic_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

> [!NOTE]
> Voor C#-ontwikkelaars hebt u toegang `PSStyle` als een singleton. Het gebruik ziet er als volgende uit:
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> `PSStyle` bestaat in de naamruimte System.Management.Automation.

Naast de toegang tot `$PSStyle` introduceert dit wijzigingen in de PowerShell-engine. Het PowerShell-opmaaksysteem wordt bijgewerkt om te `$PSStyle.OutputRendering` respecteren.

- `StringDecorated` type wordt toegevoegd om ANSI-tekenreeksen met escape-tekenreeksen te verwerken.
- `string IsDecorated` Booleaanse eigenschap wordt toegevoegd om te retourneren als de tekenreeks ANSI-escapereeksen bevat op basis van of de tekenreeks ESC of C1 CSI bevat.
- De `Length` eigenschap retourneert _alleen_ de lengte voor de tekst zonder de ANSI-escapereeksen.
- `StringDecorated Substring(int contentLength)` methode retourneert een subtekenreeks vanaf index 0 tot de inhoudslengte die geen deel uitmaakt van ANSI-escapereeksen. Dit is nodig voor tabelopmaak om tekenreeksen af tekapen en ANSI-escapereeksen te behouden die geen afdrukbare tekenruimte in beslag nemen.
- `string ToString()` methode blijft hetzelfde en retourneert de plaintext-versie van de tekenreeks.
- `string ToString(bool Ansi)` methode retourneert de onbewerkte ingesloten ANSI-tekenreeks als de `Ansi` parameter true is. Anders wordt een platte-tekstversie met ANSI-escapereeksen verwijderd.

De `FormatHyperlink(string text, uri link)` retourneert een tekenreeks met een ANSI-escapereeks die wordt gebruikt voor het inrichten van hyperlinks. Sommige terminalhosts, zoals [de Windows Terminal,](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701)ondersteunen deze markering, waardoor de weergegeven tekst in de terminal kan worden geklikt.

Ondersteuning voor ANSI-escapereeksen kan worden uitgeschakeld met behulp van de **TERM** of **NO_COLOR** omgevingsvariabelen.

De volgende waarden van `$env:TERM` wijzigen het gedrag als volgt:

- `dumb` - instellen `$Host.UI.SupportsVirtualTerminal = $false`
- `xterm-mono` - instellen `$PSStyle.OutputRendering = PlainText`
- `xtermm` - instellen `$PSStyle.OutputRendering = PlainText`

Als `$env:NO_COLOR` bestaat, stelt u `$PSStyle.OutputRendering = PlainText` in. Zie [https://no-color.org/](https://no-color.org/) voor meer informatie.

## <a name="psansiprogress"></a>PSAnsiProgress

Dit experiment is toegevoegd in PowerShell 7.2. Met de functie wordt het `$PSStyle.Progress` lid toegevoegd en kunt u de weergavebalk voor voortgangsweergaven bepalen.

- `$PSStyle.Progress.Style` - Een ANSI-tekenreeks die de renderingstijl instelt.
- `$PSStyle.Progress.MaxWidth` - Hiermee stelt u de maximale breedte van de weergave in. Stel in op `0` voor consolebreedte.
  De standaardwaarde is `120`
- `$PSStyle.Progress.View` - Een enum met waarden en `Minimal` `Classic` . `Classic` is de bestaande rendering zonder wijzigingen. `Minimal` is ????n regel minimale rendering. `Minimal` is de standaardwaarde.

> [!NOTE]
> Als de host geen ondersteuning biedt voor Virtual Terminal, `$PSStyle.Progress.View` wordt automatisch ingesteld op `Classic` .

In het volgende voorbeeld wordt de renderingstijl bijgewerkt naar een minimale voortgangsbalk.

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> U moet de experimentele **functie PSAnsiRendering** hebben ingeschakeld om deze functie te kunnen gebruiken.

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

Raadt potenti??le opdrachten aan op basis van fuzzy zoekopdrachten na **een CommandNotFoundException.**

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

## <a name="pscultureinvariantreplaceoperator"></a>PSAtriceeInvariantReplaceOperator

Wanneer de linkeropeen in een operator-instructie geen tekenreeks is, wordt die `-replace` operand geconverteerd naar een tekenreeks.

Wanneer deze functie is uitgeschakeld, wordt met `-replace` de operator een cultuurgevoelige tekenreeksconversie gemaakt.
Als uw cultuur bijvoorbeeld is ingesteld op Frans (fr), wordt de `1.2` waarde geconverteerd naar de tekenreeks `1,2` .

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

Met de functie ingeschakeld:

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

Hiermee schakelt u compilatie naar MOF op niet-Windows-systemen in en maakt u het gebruik `Invoke-DSCResource` van zonder een LCM mogelijk.

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

Deze functie onderzoekt de opdracht die in de shell is getypt. Als alle opdrachten impliciet proxyopdrachten voor externe toegang zijn die een eenvoudige pijplijn vormen, worden de opdrachten in batche bij elkaar gezet en aangeroepen als ????n externe pijplijn.

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

Zoals hierboven is te zien, worden met de batchfunctie ingeschakeld alle drie impliciete proxyopdrachten voor externe toegang, , , uitgevoerd in de externe sessie. Het resultaat van de pijplijn is de enige gegevens die worden geretourneerd naar de `Get-AllProcesses` `Select-Custom` `Group-Stuff` client. Dit vermindert de hoeveelheid gegevens die tussen client en externe sessie heen en weer worden verzonden, en vermindert ook de hoeveelheid objectser serialisatie en deseralisatie.

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

Als een PSDrive-pad dat gebruikmaakt van de FileSystem-provider wordt doorgegeven aan een systeemeigen opdracht, wordt het om opgeloste bestandspad doorgegeven aan de systeemeigen opdracht. Dit betekent dat een opdracht zoals `code temp:/test.txt` nu werkt zoals verwacht.

Als in Windows het pad begint met , wordt dat ook opgelost naar het volledige pad en `~` doorgegeven aan de native opdracht. In beide gevallen wordt het pad genormaliseerd naar de mapscheidingstekens voor het relevante besturingssysteem.

- Als het pad geen PSDrive of `~` (in Windows) is, wordt padnormalisatie niet uitgevoerd
- Als het pad tussen enkele aanhalingstekens staat, wordt het niet opgelost en behandeld als letterlijke

## <a name="psnotapplyerroractiontostderr"></a>PSNotApplyErrorActionToStderr

Wanneer deze experimentele functie is ingeschakeld, worden foutrecords die worden omgeleid vanuit native opdrachten, zoals bij het gebruik van omleidingsoperators ( ), niet naar de variabele geschreven en heeft de voorkeursvariabele geen invloed op de `2>&1` `$Error` omgeleide `$ErrorActionPreference` uitvoer.

Veel native opdrachten schrijven naar `stderr` als een alternatieve stroom voor aanvullende informatie. Dit gedrag kan verwarring veroorzaken bij het zoeken naar fouten of de aanvullende uitvoergegevens kunnen verloren gaan voor de gebruiker als is ingesteld op een status die `$ErrorActionPreference` de uitvoer dempt.

Wanneer een native opdracht een afsluitende code heeft die niet nul `$?` is, wordt ingesteld op `$false` . Als de afsluitende code nul is, `$?` wordt ingesteld op `$true` .

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

Introduceert nieuwe operators voor operators voor voorwaardelijke toegang tot null-leden - `?.` en `?[]` . Null-operatoren voor lidtoegang kunnen worden gebruikt voor scalaire typen en matrixtypen. Retourneert de waarde van het toegangslid als de variabele niet null is. Als de waarde van de variabele null is, retourneert u null.

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

De eigenschap `propname` wordt gebruikt en de waarde wordt alleen geretourneerd als niet null `$x` is. Op dezelfde manier wordt de indexer alleen gebruikt als `$x` niet null is. Als `$x` null is, wordt null geretourneerd.

De operators en zijn operators voor lidtoegang en staan geen spatie toe tussen de naam van de `?.` `?[]` variabele en de operator.

Aangezien PowerShell het mogelijk maakt als onderdeel van de naam van de variabele, is ondubbelzinnigheid vereist wanneer de operators worden gebruikt zonder een spatie tussen de naam van de variabele `?` en de operator. Om ondubbelzinnig te zijn, moeten de variabelen rond de `{}` variabelenaam gebruiken, zoals `${x?}?.propertyName` of `${y}?[0]` .

> [!NOTE]
> Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7.1 en hoger.

## <a name="pstempdrive"></a>PSTempDrive

Hiermee maakt u `TEMP:` de PSDrive die is toe te staan aan het tijdelijke directorypad van de gebruiker.

> [!NOTE]
> Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7 en hoger.

## <a name="psunixfilestat"></a>PSUnixFileStat

Deze functie biedt nieuw gedrag om gegevens uit de Unix **stat** API op te nemen in de uitvoer van de bestandssysteemprovider om een meer Unix-achtige bestandsvermelding mogelijk te maken. Er wordt een nieuwe notitie-eigenschap toegevoegd in de bestandssysteemprovider met de naam **UnixStat** die een algemene expressie van de API van het `stat(2)` onderliggende Unix-typesysteem bevat.

De uitvoer van `Get-ChildItem` moet er als de volgende uitzien:

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
> Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7.1 en hoger.

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

Met deze functie kunnen afgekorte cmdlets en functies op tabs worden voltooid:

Bijvoorbeeld:

- `i-psdf<tab>` retourneert `Import-PowerShellDataFile` .
- `u-akvmssdr<tab>` Retourneert `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`

Dit werkt alleen voor tab-aanvulling (interactief gebruik), dus is geen geldige `i-psdf` cmdlet-naam in een script.

> [!NOTE]
> Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7 en hoger.

## <a name="pssubsystempluginmodel"></a>PSSubsystemPluginModel

Met deze functie schakelt u het invoegmodel van het subsysteem in PowerShell in. De functie maakt het mogelijk om onderdelen van te `System.Management.Automation.dll` scheiden in afzonderlijke subsystemen die zich in hun eigen assembly bevinden. Door deze scheiding wordt de schijfvoetafdruk van de PowerShell-kernentafdruk verkleind en kunnen deze onderdelen optionele functies worden voor een minimale PowerShell-installatie.

Momenteel wordt alleen **het subsysteem CommandPredictor** ondersteund. Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste voorspellingsinvoegingen te bieden. In de toekomst **kunnen Taak,** **CommandCompleter,** **Externe** externe installatie en andere onderdelen worden gescheiden in subsysteemassemblage buiten `System.Management.Automation.dll` .

De experimentele functie bevat een nieuwe cmdlet, [Get-PSSubsystem.](xref:Microsoft.PowerShell.Core.Get-PSSubsystem) Deze cmdlet is alleen beschikbaar wanneer de functie is ingeschakeld. Deze cmdlet retourneert informatie over de subsystemen die beschikbaar zijn op het systeem.

## <a name="psnativecommandargumentpassing"></a>PSNativeCommandArgumentPassing

Wanneer deze experimentele functie is ingeschakeld, gebruikt PowerShell de eigenschap van het object in plaats van ons huidige mechanisme voor het reconstrueren van een tekenreeks bij het aanroepen van een `ArgumentList` `StartProcessInfo` systeemeigen uitvoerbaar bestand.

Met deze functie wordt een nieuwe automatische variabele `$PSNativeCommandArgumentPassing` toegevoegd waarmee u het gedrag tijdens runtime kunt selecteren. De geldige waarden zijn `Legacy` en `Standard` . `Legacy` is het historische gedrag. De standaardwaarde wanneer de experimentele functie is ingeschakeld, is het nieuwe `Standard` gedrag.

> [!CAUTION]
> Het nieuwe gedrag is een **wijziging die het huidige** gedrag verbreekt. Dit kan leiden tot problemen met scripts en automatisering die de verschillende problemen bij het aanroepen van native toepassingen oplossen. In het verleden moeten aanhalingstekens worden voorzien van een escape-escape en is het niet mogelijk om lege argumenten op te geven voor een native toepassing.

Nieuwe gedragingen die beschikbaar zijn gemaakt door deze wijziging:

- Letterlijke of uitbreidbare tekenreeksen met ingesloten aanhalingstekens blijven nu behouden:

  ```powershell
  PS > $a = 'a" "b'
  PS > $PSNativeCommandArgumentPassing = "Legacy"
  PS > testexe -echoargs $a 'a" "b' a" "b
  Arg 0 is <a b>
  Arg 1 is <a b>
  Arg 2 is <a b>
  PS > $PSNativeCommandArgumentPassing = "Standard"
  PS > testexe -echoargs $a 'a" "b' a" "b
  Arg 0 is <a" "b>
  Arg 1 is <a" "b>
  Arg 2 is <a b>
  ```

- Lege tekenreeksen als argumenten blijven nu behouden:

  ```powershell
  PS>  $PSNativeCommandArgumentPassing = "Legacy"
  PS> testexe -echoargs '' a b ''
  Arg 0 is <a>
  Arg 1 is <b>
  PS> $PSNativeCommandArgumentPassing = "Standard"
  PS> testexe -echoargs '' a b ''
  Arg 0 is <>
  Arg 1 is <a>
  Arg 2 is <b>
  Arg 3 is <>
  ```

Het nieuwe gedrag verandert geen aanroepen die er als de volgende uitzien:

```powershell
PS> $PSNativeCommandArgumentPassing = "Legacy"
PS> testexe -echoargs -k com:port=\\devbox\pipe\debug,pipe,resets=0,reconnect
Arg 0 is <-k>
Arg 1 is <com:port=\\devbox\pipe\debug,pipe,resets=0,reconnect>
PS> $PSNativeCommandArgumentPassing = "Standard"
PS> testexe -echoargs -k com:port=\\devbox\pipe\debug,pipe,resets=0,reconnect
Arg 0 is <-k>
Arg 1 is <com:port=\\devbox\pipe\debug,pipe,resets=0,reconnect>
```

Daarnaast wordt parametertracing nu verstrekt, zodat nuttige `Trace-Command` informatie biedt voor het opsporen van gegevens.

```powershell
PS> $PSNativeCommandArgumentPassing = "Legacy"
PS> trace-command -PSHOST -Name ParameterBinding { testexe -echoargs $a 'a" "b' a" "b }
DEBUG: 2021-02-01 17:19:53.6438 ParameterBinding Information: 0 : BIND NAMED native application line args [/Users/james/src/github/forks/jameswtruher/PowerShell-1/test/tools/TestExe/bin/testexe]
DEBUG: 2021-02-01 17:19:53.6440 ParameterBinding Information: 0 :     BIND argument [-echoargs a" "b a" "b "a b"]
DEBUG: 2021-02-01 17:19:53.6522 ParameterBinding Information: 0 : CALLING BeginProcessing
Arg 0 is <a b>
Arg 1 is <a b>
Arg 2 is <a b>
PS> $PSNativeCommandArgumentPassing = "Standard"
PS> trace-command -PSHOST -Name ParameterBinding { testexe -echoargs $a 'a" "b' a" "b }
DEBUG: 2021-02-01 17:20:01.9829 ParameterBinding Information: 0 : BIND NAMED native application line args [/Users/james/src/github/forks/jameswtruher/PowerShell-1/test/tools/TestExe/bin/testexe]
DEBUG: 2021-02-01 17:20:01.9829 ParameterBinding Information: 0 :     BIND cmd line arg [-echoargs] to position [0]
DEBUG: 2021-02-01 17:20:01.9830 ParameterBinding Information: 0 :     BIND cmd line arg [a" "b] to position [1]
DEBUG: 2021-02-01 17:20:01.9830 ParameterBinding Information: 0 :     BIND cmd line arg [a" "b] to position [2]
DEBUG: 2021-02-01 17:20:01.9831 ParameterBinding Information: 0 :     BIND cmd line arg [a b] to position [3]
DEBUG: 2021-02-01 17:20:01.9908 ParameterBinding Information: 0 : CALLING BeginProcessing
Arg 0 is <a" "b>
Arg 1 is <a" "b>
Arg 2 is <a b>
```
