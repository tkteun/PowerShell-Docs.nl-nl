---
ms.date: 12/14/2020
title: Experimentele functies gebruiken in Power shell
description: Een lijst met de momenteel beschik bare experimentele functies en hoe u deze kunt gebruiken.
ms.openlocfilehash: be02829c27ff5d8babaf173d2ee7ebbfc7614773
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879351"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="7eb42-103">Experimentele functies gebruiken in Power shell</span><span class="sxs-lookup"><span data-stu-id="7eb42-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="7eb42-104">De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7eb42-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="7eb42-105">Een experimentele functie is een onderdeel waar het ontwerp niet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="7eb42-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="7eb42-106">De functie is beschikbaar voor gebruikers om te testen en feedback te geven.</span><span class="sxs-lookup"><span data-stu-id="7eb42-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="7eb42-107">Zodra een experimentele functie is voltooid, worden de wijzigingen in het ontwerp doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7eb42-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="7eb42-108">Experimentele functies zijn niet bedoeld om te worden gebruikt in productie, omdat de wijzigingen niet mogen worden opgesplitst.</span><span class="sxs-lookup"><span data-stu-id="7eb42-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="7eb42-109">Experimentele functies worden niet officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7eb42-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="7eb42-110">We waarderen echter alle feedback-en fouten rapporten.</span><span class="sxs-lookup"><span data-stu-id="7eb42-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="7eb42-111">U kunt problemen in de [github-bron opslagplaats](https://github.com/PowerShell/PowerShell/issues/new/choose)opslaan.</span><span class="sxs-lookup"><span data-stu-id="7eb42-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="7eb42-112">Zie [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)voor meer informatie over het in-of uitschakelen van deze functies.</span><span class="sxs-lookup"><span data-stu-id="7eb42-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="7eb42-113">Beschikbare functies</span><span class="sxs-lookup"><span data-stu-id="7eb42-113">Available features</span></span>

<span data-ttu-id="7eb42-114">In dit artikel worden de experimentele functies beschreven die beschikbaar zijn en hoe u deze functie kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="7eb42-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="7eb42-115">Name</span><span class="sxs-lookup"><span data-stu-id="7eb42-115">Name</span></span>                            |   <span data-ttu-id="7eb42-116">6,2</span><span class="sxs-lookup"><span data-stu-id="7eb42-116">6.2</span></span>   |   <span data-ttu-id="7eb42-117">7.0</span><span class="sxs-lookup"><span data-stu-id="7eb42-117">7.0</span></span>   |   <span data-ttu-id="7eb42-118">7.1</span><span class="sxs-lookup"><span data-stu-id="7eb42-118">7.1</span></span>   |   <span data-ttu-id="7eb42-119">7.2</span><span class="sxs-lookup"><span data-stu-id="7eb42-119">7.2</span></span>   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| <span data-ttu-id="7eb42-120">PSTempDrive (mainstream in PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="7eb42-120">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |         |         |
| <span data-ttu-id="7eb42-121">PSUseAbbreviationExpansion (mainstream in PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="7eb42-121">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |         |         |
| <span data-ttu-id="7eb42-122">PSNullConditionalOperators (mainstream in PS 7.1 +)</span><span class="sxs-lookup"><span data-stu-id="7eb42-122">PSNullConditionalOperators (mainstream in PS 7.1+)</span></span>         |         | &check; |         |         |
| <span data-ttu-id="7eb42-123">PSUnixFileStat (alleen niet-Windows-mainstream in PS 7.1 +)</span><span class="sxs-lookup"><span data-stu-id="7eb42-123">PSUnixFileStat (non-Windows only - mainstream in PS 7.1+)</span></span>  |         | &check; |         |         |
| <span data-ttu-id="7eb42-124">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="7eb42-124">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; | &check; | &check; |
| <span data-ttu-id="7eb42-125">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="7eb42-125">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; | &check; | &check; |
| <span data-ttu-id="7eb42-126">Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="7eb42-126">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; | &check; | &check; |
| <span data-ttu-id="7eb42-127">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="7eb42-127">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; | &check; | &check; |
| <span data-ttu-id="7eb42-128">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="7eb42-128">PSNativePSPathResolution</span></span>                                   |         |         | &check; | &check; |
| <span data-ttu-id="7eb42-129">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="7eb42-129">PSCultureInvariantReplaceOperator</span></span>                          |         |         | &check; | &check; |
| <span data-ttu-id="7eb42-130">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="7eb42-130">PSNotApplyErrorActionToStderr</span></span>                              |         |         | &check; | &check; |
| <span data-ttu-id="7eb42-131">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="7eb42-131">PSSubsystemPluginModel</span></span>                                     |         |         | &check; | &check; |
| <span data-ttu-id="7eb42-132">PSAnsiRendering</span><span class="sxs-lookup"><span data-stu-id="7eb42-132">PSAnsiRendering</span></span>                                            |         |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="7eb42-133">Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="7eb42-133">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="7eb42-134">In Power shell 7,0 stelt het experiment de para meter **BreakAll** in op de `Debug-Runspace` `Debug-Job` cmdlets, zodat gebruikers kunnen bepalen of ze Power shell onmiddellijk op de huidige locatie moeten afkraken wanneer ze een debugger koppelen.</span><span class="sxs-lookup"><span data-stu-id="7eb42-134">In PowerShell 7.0, the experiment enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

<span data-ttu-id="7eb42-135">In Power shell 7,1 voegt dit experiment ook de **runs Pace** -para meter toe aan de `*-PSBreakpoint` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="7eb42-135">In PowerShell 7.1, this experiment also adds the **Runspace** parameter to the `*-PSBreakpoint` cmdlets.</span></span>

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

<span data-ttu-id="7eb42-136">De para meter **runs Pace** geeft een **runs Pace** -object op om te communiceren met onderbrekings punten in de opgegeven runs Pace.</span><span class="sxs-lookup"><span data-stu-id="7eb42-136">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

<span data-ttu-id="7eb42-137">In dit voor beeld wordt een taak gestart en wordt een onderbrekings punt ingesteld op break wanneer de `Set-PSBreakPoint` wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7eb42-137">In this example, a job is started and a breakpoint is set to break when the `Set-PSBreakPoint` is run.</span></span> <span data-ttu-id="7eb42-138">De runs Pace wordt opgeslagen in een variabele en door gegeven aan de `Get-PSBreakPoint` opdracht met de para meter **runs Pace** .</span><span class="sxs-lookup"><span data-stu-id="7eb42-138">The runspace is stored in a variable and passed to the `Get-PSBreakPoint` command with the **Runspace** parameter.</span></span> <span data-ttu-id="7eb42-139">U kunt vervolgens het onderbrekings punt in de variabele inspecteren `$breakpoint` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-139">You can then inspect the breakpoint in the `$breakpoint` variable.</span></span>

## <a name="psansirendering"></a><span data-ttu-id="7eb42-140">PSAnsiRendering</span><span class="sxs-lookup"><span data-stu-id="7eb42-140">PSAnsiRendering</span></span>

<span data-ttu-id="7eb42-141">Dit experiment is toegevoegd aan Power shell 7,2.</span><span class="sxs-lookup"><span data-stu-id="7eb42-141">This experiment was added in PowerShell 7.2.</span></span> <span data-ttu-id="7eb42-142">Met de functie kunt u wijzigingen aanbrengen in de manier waarop de Power shell-engine tekst uitvoer en de `$PSStyle` Automatische variabele toevoegen om de ANSI-rendering van teken reeks uitvoer te beheren.</span><span class="sxs-lookup"><span data-stu-id="7eb42-142">The feature enables changes how the PowerShell engine outputs text and add the `$PSStyle` automatic variable to control ANSI rendering of string output.</span></span>

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

<span data-ttu-id="7eb42-143">De basis leden retour neren teken reeksen van ANSI-escape reeksen die zijn toegewezen aan hun namen.</span><span class="sxs-lookup"><span data-stu-id="7eb42-143">The base members return strings of ANSI escape sequences mapped to their names.</span></span> <span data-ttu-id="7eb42-144">De waarden kunnen worden ingesteld om aanpassing mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="7eb42-144">The values are settable to allow customization.</span></span>

<span data-ttu-id="7eb42-145">Zie [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="7eb42-145">For more information, see [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)</span></span>

> [!NOTE]
> <span data-ttu-id="7eb42-146">Voor C#-ontwikkel aars kunt u `PSStyle` als Singleton toegang krijgen.</span><span class="sxs-lookup"><span data-stu-id="7eb42-146">For C# developers, you can access `PSStyle` as a singleton.</span></span> <span data-ttu-id="7eb42-147">Gebruik ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="7eb42-147">Usage will look like this:</span></span>
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> <span data-ttu-id="7eb42-148">`PSStyle` bestaat in de naam ruimte System. Management. Automation.</span><span class="sxs-lookup"><span data-stu-id="7eb42-148">`PSStyle` exists in the System.Management.Automation namespace.</span></span>

<span data-ttu-id="7eb42-149">Naast de toegang tot `$PSStyle` , worden er wijzigingen aangebracht in de Power shell-engine.</span><span class="sxs-lookup"><span data-stu-id="7eb42-149">Along with access to `$PSStyle`, this introduces changes to the PowerShell engine.</span></span> <span data-ttu-id="7eb42-150">Het Power shell-opmaak systeem is bijgewerkt met betrekking tot `$PSStyle.OutputRendering` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-150">The PowerShell formatting system is updated to respect `$PSStyle.OutputRendering`.</span></span>

- <span data-ttu-id="7eb42-151">`StringDecorated` type wordt toegevoegd voor het verwerken van teken reeksen met ANSI-Escapes.</span><span class="sxs-lookup"><span data-stu-id="7eb42-151">`StringDecorated` type is added to handle ANSI escaped strings.</span></span>
- <span data-ttu-id="7eb42-152">`string IsDecorated` Er wordt een Boole-eigenschap toegevoegd om te retour neren als de teken reeks ANSI-escape reeksen bevat op basis van als de teken reeks ESC of C1 CSI bevat.</span><span class="sxs-lookup"><span data-stu-id="7eb42-152">`string IsDecorated` boolean property is added to return if the string contains ANSI escape sequences based on if the string contains ESC or C1 CSI.</span></span>
- <span data-ttu-id="7eb42-153">De `Length` eigenschap retourneert _alleen_ de lengte van de tekst zonder de ANSI-escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="7eb42-153">The `Length` property returns _only_ the length for the text without the ANSI escape sequences.</span></span>
- <span data-ttu-id="7eb42-154">`StringDecorated Substring(int contentLength)` methode retourneert een subtekenreeks die begint bij index 0 tot aan de lengte van de inhoud die geen deel uitmaakt van ANSI-escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="7eb42-154">`StringDecorated Substring(int contentLength)` method returns a substring starting at index 0 up to the content length that is not a part of ANSI escape sequences.</span></span> <span data-ttu-id="7eb42-155">Dit is nodig voor het afkappen van teken reeksen en het behouden van ANSI-escape reeksen die geen afdruk bare teken ruimte innemen.</span><span class="sxs-lookup"><span data-stu-id="7eb42-155">This is needed for table formatting to truncate strings and preserve ANSI escape sequences that don't take up printable character space.</span></span>
- <span data-ttu-id="7eb42-156">`string ToString()` de methode blijft hetzelfde en retourneert de ongecodeerde versie van de teken reeks.</span><span class="sxs-lookup"><span data-stu-id="7eb42-156">`string ToString()` method stays the same and returns the plaintext version of the string.</span></span>
- <span data-ttu-id="7eb42-157">`string ToString(bool Ansi)` methode retourneert de onbewerkte ANSI-teken reeks als de `Ansi` para meter waar is.</span><span class="sxs-lookup"><span data-stu-id="7eb42-157">`string ToString(bool Ansi)` method returns the raw ANSI embedded string if the `Ansi` parameter is true.</span></span> <span data-ttu-id="7eb42-158">Anders wordt een niet-gecodeerde versie met ANSI-escape reeksen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7eb42-158">Otherwise, a plaintext version with ANSI escape sequences removed is returned.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="7eb42-159">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="7eb42-159">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="7eb42-160">Raadt potentiële opdrachten aan op basis van zoek acties op fuzzy na een **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="7eb42-160">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="7eb42-161">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="7eb42-161">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="7eb42-162">Wanneer de linkeroperand in een `-replace` operator instructie geen teken reeks is, wordt die operand geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="7eb42-162">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="7eb42-163">Als deze functie is uitgeschakeld, `-replace` heeft de operator een cultuur gevoelige teken reeks conversie.</span><span class="sxs-lookup"><span data-stu-id="7eb42-163">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="7eb42-164">Als uw cultuur bijvoorbeeld is ingesteld op Frans (FR), wordt de waarde `1.2` geconverteerd naar de teken reeks `1,2` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-164">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="7eb42-165">Als de functie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="7eb42-165">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="7eb42-166">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="7eb42-166">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="7eb42-167">Hiermee wordt de compilatie op MOF op niet-Windows-systemen ingeschakeld en wordt het gebruik van `Invoke-DSCResource` zonder LCM ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb42-167">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="7eb42-168">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="7eb42-168">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="7eb42-169">Met deze functie wordt de in de shell getypte opdracht onderzocht. als alle opdrachten impliciet externe proxy opdrachten zijn die een eenvoudige pijp lijn vormen, worden de opdrachten in batch verzameld en aangeroepen als één externe pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="7eb42-169">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="7eb42-170">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7eb42-170">Example:</span></span>

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

<span data-ttu-id="7eb42-171">Zoals hierboven wordt weer gegeven, terwijl de batch functie is ingeschakeld, worden alle drie de impliciete externe proxy opdrachten,,,, `Get-AllProcesses` `Select-Custom` `Group-Stuff` uitgevoerd in de externe sessie en het resultaat van de pijp lijn de enige gegevens die worden geretourneerd naar de client.</span><span class="sxs-lookup"><span data-stu-id="7eb42-171">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="7eb42-172">Dit vermindert de hoeveelheid gegevens die wordt verzonden tussen de client en de externe sessie, en vermindert ook de hoeveelheid object-serialisatie en deserialisatie.</span><span class="sxs-lookup"><span data-stu-id="7eb42-172">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="7eb42-173">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="7eb42-173">PSNativePSPathResolution</span></span>

<span data-ttu-id="7eb42-174">Als een PSDrive-pad dat gebruikmaakt van de File System Provider wordt door gegeven aan een systeem eigen opdracht, wordt het omgezette bestandspad door gegeven aan de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="7eb42-174">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="7eb42-175">Dit betekent dat een opdracht zoals `code temp:/test.txt` nu werkt zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="7eb42-175">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="7eb42-176">Ook in Windows, als het pad begint met `~` , dat wordt omgezet naar het volledige pad en wordt door gegeven aan de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="7eb42-176">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="7eb42-177">In beide gevallen wordt het pad genormaliseerd naar de adres lijst scheidings tekens voor het relevante besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="7eb42-177">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="7eb42-178">Als het pad geen PSDrive of `~` (in Windows) is, treedt de normalisatie van het pad niet op</span><span class="sxs-lookup"><span data-stu-id="7eb42-178">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="7eb42-179">Als het pad zich in enkele aanhalings tekens bevindt, wordt het niet opgelost en behandeld als een letterlijke waarde</span><span class="sxs-lookup"><span data-stu-id="7eb42-179">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnotapplyerroractiontostderr"></a><span data-ttu-id="7eb42-180">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="7eb42-180">PSNotApplyErrorActionToStderr</span></span>

<span data-ttu-id="7eb42-181">Wanneer deze experimentele functie is ingeschakeld, worden fout records die worden omgeleid van systeem eigen opdrachten, zoals het gebruik van omleidings operatoren ( `2>&1` ), niet naar de `$Error` variabele geschreven en is de voorkeurs variabele niet van `$ErrorActionPreference` invloed op de omgeleide uitvoer.</span><span class="sxs-lookup"><span data-stu-id="7eb42-181">When this experimental feature is enabled, error records redirected from native commands, like when using redirection operators (`2>&1`), are not written to the `$Error` variable and the preference variable `$ErrorActionPreference` does not affect the redirected output.</span></span>

<span data-ttu-id="7eb42-182">Veel systeem eigen opdrachten schrijven naar `stderr` als alternatieve stroom voor aanvullende informatie.</span><span class="sxs-lookup"><span data-stu-id="7eb42-182">Many native commands write to `stderr` as an alternative stream for additional information.</span></span> <span data-ttu-id="7eb42-183">Dit gedrag kan leiden tot Verwar ring bij het opzoeken van fouten of de aanvullende uitvoer gegevens kunnen verloren gaan voor de gebruiker als deze `$ErrorActionPreference` is ingesteld op een status die de uitvoer dempt.</span><span class="sxs-lookup"><span data-stu-id="7eb42-183">This behavior can cause confusion when looking through errors or the additional output information can be lost to the user if `$ErrorActionPreference` is set to a state that mutes the output.</span></span>

<span data-ttu-id="7eb42-184">Wanneer een systeem eigen opdracht een afsluit code heeft die niet gelijk is aan nul, `$?` wordt ingesteld op `$false` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-184">When a native command has a non-zero exit code, `$?` is set to `$false`.</span></span> <span data-ttu-id="7eb42-185">Als de afsluit code nul is, `$?` wordt ingesteld op `$true` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-185">If the exit code is zero, `$?` is set to `$true`.</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="7eb42-186">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="7eb42-186">PSNullConditionalOperators</span></span>

<span data-ttu-id="7eb42-187">Hierin worden nieuwe Opera tors geïntroduceerd voor de null-Opera tors voor voorwaardelijke toegang, `?.` en `?[]` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-187">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="7eb42-188">Toegangs operatoren voor Null-leden kunnen worden gebruikt voor scalaire typen en matrix typen.</span><span class="sxs-lookup"><span data-stu-id="7eb42-188">Null member access operators can be used on scalar types and array types.</span></span> <span data-ttu-id="7eb42-189">Retourneert de waarde van het geopende lid als de variabele niet null is.</span><span class="sxs-lookup"><span data-stu-id="7eb42-189">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="7eb42-190">Als de waarde van de variabele null is, retourneert dan Null.</span><span class="sxs-lookup"><span data-stu-id="7eb42-190">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="7eb42-191">De eigenschap `propname` is toegankelijk en de waarde ervan wordt alleen geretourneerd als deze `$x` niet null is.</span><span class="sxs-lookup"><span data-stu-id="7eb42-191">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="7eb42-192">De Indexeer functie wordt op dezelfde manier gebruikt als `$x` niet null is.</span><span class="sxs-lookup"><span data-stu-id="7eb42-192">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="7eb42-193">Als `$x` is null is, wordt Null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7eb42-193">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="7eb42-194">De `?.` `?[]` Opera tors en zijn lid van de operator toegang en staan geen ruimte tussen de naam van de variabele en de operator toe.</span><span class="sxs-lookup"><span data-stu-id="7eb42-194">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="7eb42-195">Omdat Power shell `?` als onderdeel van de naam van de variabele is toegestaan, is ondubbelzinnige installatie vereist wanneer de Opera tors worden gebruikt zonder ruimte tussen de naam van de variabele en de operator.</span><span class="sxs-lookup"><span data-stu-id="7eb42-195">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="7eb42-196">Voor dubbel zinnigheid moeten de variabelen worden gebruikt `{}` om de naam van de variabele te gebruiken, zoals: `${x?}?.propertyName` of `${y}?[0]` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-196">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

> [!NOTE]
> <span data-ttu-id="7eb42-197">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="7eb42-197">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="7eb42-198">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="7eb42-198">PSTempDrive</span></span>

<span data-ttu-id="7eb42-199">Hiermee maakt `TEMP:` u de PSDrive die is toegewezen aan het pad naar de tijdelijke map van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="7eb42-199">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="7eb42-200">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="7eb42-200">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="7eb42-201">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="7eb42-201">PSUnixFileStat</span></span>

<span data-ttu-id="7eb42-202">Deze functie biedt nieuw gedrag om gegevens op te nemen uit de UNIX **stat** -API in de uitvoer van de bestandssysteem provider om een meer Unix-achtige bestands vermelding te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="7eb42-202">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="7eb42-203">Er wordt een nieuwe notitie-eigenschap toegevoegd aan de bestandssysteem provider met de naam **UnixStat** die een gemeen schappelijke expressie van de `stat(2)` API van het onderliggende UNIX-type systeem bevat.</span><span class="sxs-lookup"><span data-stu-id="7eb42-203">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="7eb42-204">De uitvoer van `Get-ChildItem` moet er ongeveer als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="7eb42-204">The output from `Get-ChildItem` should look something like this:</span></span>

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
> <span data-ttu-id="7eb42-205">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7,1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="7eb42-205">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="7eb42-206">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="7eb42-206">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="7eb42-207">Met deze functie kunt u het tabblad volt ooien van verkorte cmdlets en functies:</span><span class="sxs-lookup"><span data-stu-id="7eb42-207">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="7eb42-208">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="7eb42-208">For example:</span></span>

- <span data-ttu-id="7eb42-209">`i-psdf<tab>` retourneert `Import-PowerShellDataFile` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-209">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="7eb42-210">`u-akvmssdr<tab>` retourneert `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="7eb42-210">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="7eb42-211">Dit werkt alleen voor tabblad voltooiing (interactief gebruik), dus `i-psdf` is geen geldige cmdlet-naam in een script.</span><span class="sxs-lookup"><span data-stu-id="7eb42-211">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="7eb42-212">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="7eb42-212">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="pssubsystempluginmodel"></a><span data-ttu-id="7eb42-213">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="7eb42-213">PSSubsystemPluginModel</span></span>

<span data-ttu-id="7eb42-214">Met deze functie wordt het subsysteem voor de invoeg toepassing in Power shell ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb42-214">This feature enables the subsystem plugin model in PowerShell.</span></span> <span data-ttu-id="7eb42-215">De functie maakt het mogelijk om onderdelen van te scheiden `System.Management.Automation.dll` in afzonderlijke subsystemen die zich in hun eigen assembly bevinden.</span><span class="sxs-lookup"><span data-stu-id="7eb42-215">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="7eb42-216">Deze schei ding vermindert het schijf gebruik van de kern-Power shell-engine en maakt het mogelijk dat deze onderdelen optionele functies worden voor een minimale Power shell-installatie.</span><span class="sxs-lookup"><span data-stu-id="7eb42-216">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="7eb42-217">Op dit moment wordt alleen het subsysteem **CommandPredictor** ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7eb42-217">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="7eb42-218">Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste Voorspellings-invoeg toepassingen te bieden.</span><span class="sxs-lookup"><span data-stu-id="7eb42-218">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="7eb42-219">In de toekomst kunnen **Job**, **CommandCompleter**, **Remoting** en andere onderdelen worden gescheiden in subsysteem-assembly's buiten `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="7eb42-219">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

<span data-ttu-id="7eb42-220">Het experimentele onderdeel bevat een nieuwe cmdlet [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span><span class="sxs-lookup"><span data-stu-id="7eb42-220">The experimental feature includes a new cmdlet, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span></span> <span data-ttu-id="7eb42-221">Deze cmdlet is alleen beschikbaar wanneer de functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="7eb42-221">This cmdlet is only available when the feature is enabled.</span></span> <span data-ttu-id="7eb42-222">Deze cmdlet retourneert informatie over de subsystemen die beschikbaar zijn op het systeem.</span><span class="sxs-lookup"><span data-stu-id="7eb42-222">This cmdlet returns information about the subsystems that are available on the system.</span></span>
