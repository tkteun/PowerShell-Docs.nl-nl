---
ms.date: 12/14/2020
title: Experimentele functies gebruiken in PowerShell
description: Geeft een lijst weer van de momenteel beschikbare experimentele functies en hoe u deze kunt gebruiken.
ms.openlocfilehash: 76646a05fbdba27358fa3c8dcbeb90445bb7e675
ms.sourcegitcommit: 366304d096c1caf52f0e17962f6ed23d20f86e7b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/16/2021
ms.locfileid: "107543978"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="d2b19-103">Experimentele functies gebruiken in PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2b19-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="d2b19-104">De ondersteuning voor experimentele functies in PowerShell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in PowerShell- of PowerShell-modules kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d2b19-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="d2b19-105">Een experimentele functie is een functie waarbij het ontwerp niet is afgerond.</span><span class="sxs-lookup"><span data-stu-id="d2b19-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="d2b19-106">De functie is beschikbaar voor gebruikers om te testen en feedback te geven.</span><span class="sxs-lookup"><span data-stu-id="d2b19-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="d2b19-107">Zodra een experimentele functie is afgerond, worden de ontwerpwijzigingen belangrijke wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="d2b19-108">Experimentele functies zijn niet bedoeld om te worden gebruikt in productie, omdat de wijzigingen mogen worden doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d2b19-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="d2b19-109">Experimentele functies worden niet officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d2b19-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="d2b19-110">We stellen feedback en foutrapporten echter zeer op prijs.</span><span class="sxs-lookup"><span data-stu-id="d2b19-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="d2b19-111">U kunt problemen in de [GitHub-bronopslagplaats indienen.](https://github.com/PowerShell/PowerShell/issues/new/choose)</span><span class="sxs-lookup"><span data-stu-id="d2b19-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="d2b19-112">Zie voor meer informatie over het in- of uitschakelen van [deze functies about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span><span class="sxs-lookup"><span data-stu-id="d2b19-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="d2b19-113">Beschikbare functies</span><span class="sxs-lookup"><span data-stu-id="d2b19-113">Available features</span></span>

<span data-ttu-id="d2b19-114">In dit artikel worden de experimentele functies beschreven die beschikbaar zijn en hoe u de functie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d2b19-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="d2b19-115">Name</span><span class="sxs-lookup"><span data-stu-id="d2b19-115">Name</span></span>                            |   <span data-ttu-id="d2b19-116">6,2</span><span class="sxs-lookup"><span data-stu-id="d2b19-116">6.2</span></span>   |   <span data-ttu-id="d2b19-117">7.0</span><span class="sxs-lookup"><span data-stu-id="d2b19-117">7.0</span></span>   |   <span data-ttu-id="d2b19-118">7.1</span><span class="sxs-lookup"><span data-stu-id="d2b19-118">7.1</span></span>   |   <span data-ttu-id="d2b19-119">7.2</span><span class="sxs-lookup"><span data-stu-id="d2b19-119">7.2</span></span>   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| <span data-ttu-id="d2b19-120">PSTempDrive (standaard in PS 7.0+)</span><span class="sxs-lookup"><span data-stu-id="d2b19-120">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |         |         |
| <span data-ttu-id="d2b19-121">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span><span class="sxs-lookup"><span data-stu-id="d2b19-121">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |         |         |
| <span data-ttu-id="d2b19-122">PSNullConditionalOperators (standaard in PS 7.1+)</span><span class="sxs-lookup"><span data-stu-id="d2b19-122">PSNullConditionalOperators (mainstream in PS 7.1+)</span></span>         |         | &check; |         |         |
| <span data-ttu-id="d2b19-123">PSUnixFileStat (alleen niet-Windows - mainstream in PS 7.1+)</span><span class="sxs-lookup"><span data-stu-id="d2b19-123">PSUnixFileStat (non-Windows only - mainstream in PS 7.1+)</span></span>  |         | &check; |         |         |
| <span data-ttu-id="d2b19-124">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="d2b19-124">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; | &check; | &check; |
| <span data-ttu-id="d2b19-125">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="d2b19-125">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; | &check; | &check; |
| <span data-ttu-id="d2b19-126">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="d2b19-126">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; | &check; | &check; |
| <span data-ttu-id="d2b19-127">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="d2b19-127">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; | &check; | &check; |
| <span data-ttu-id="d2b19-128">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="d2b19-128">PSNativePSPathResolution</span></span>                                   |         |         | &check; | &check; |
| <span data-ttu-id="d2b19-129">PSAtriceeInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="d2b19-129">PSCultureInvariantReplaceOperator</span></span>                          |         |         | &check; | &check; |
| <span data-ttu-id="d2b19-130">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="d2b19-130">PSNotApplyErrorActionToStderr</span></span>                              |         |         | &check; | &check; |
| <span data-ttu-id="d2b19-131">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="d2b19-131">PSSubsystemPluginModel</span></span>                                     |         |         | &check; | &check; |
| <span data-ttu-id="d2b19-132">PSAnsiProgress</span><span class="sxs-lookup"><span data-stu-id="d2b19-132">PSAnsiProgress</span></span>                                             |         |         |         | &check; |
| <span data-ttu-id="d2b19-133">PSAnsiRendering</span><span class="sxs-lookup"><span data-stu-id="d2b19-133">PSAnsiRendering</span></span>                                            |         |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="d2b19-134">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="d2b19-134">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="d2b19-135">In PowerShell 7.0 schakelt het experiment de parameter **BreakAll** in op de cmdlets en om gebruikers in staat te stellen te bepalen of ze willen dat PowerShell direct wordt beschadigd op de huidige locatie wanneer ze een `Debug-Runspace` `Debug-Job` debugger koppelen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-135">In PowerShell 7.0, the experiment enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

<span data-ttu-id="d2b19-136">In PowerShell 7.1 voegt dit experiment ook de parameter **Runspace** toe aan de `*-PSBreakpoint` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d2b19-136">In PowerShell 7.1, this experiment also adds the **Runspace** parameter to the `*-PSBreakpoint` cmdlets.</span></span>

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

<span data-ttu-id="d2b19-137">De **Runspace** parameter geeft u een **Runspace-object** om te communiceren met onderbrekingspunten in de opgegeven runspace.</span><span class="sxs-lookup"><span data-stu-id="d2b19-137">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

<span data-ttu-id="d2b19-138">In dit voorbeeld wordt een taak gestart en wordt een onderbrekingspunt ingesteld op break wanneer `Set-PSBreakPoint` de wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d2b19-138">In this example, a job is started and a breakpoint is set to break when the `Set-PSBreakPoint` is run.</span></span> <span data-ttu-id="d2b19-139">De runspace wordt opgeslagen in een variabele en doorgegeven aan de `Get-PSBreakPoint` opdracht met de parameter **Runspace.**</span><span class="sxs-lookup"><span data-stu-id="d2b19-139">The runspace is stored in a variable and passed to the `Get-PSBreakPoint` command with the **Runspace** parameter.</span></span> <span data-ttu-id="d2b19-140">Vervolgens kunt u het onderbrekingspunt in de variabele `$breakpoint` inspecteren.</span><span class="sxs-lookup"><span data-stu-id="d2b19-140">You can then inspect the breakpoint in the `$breakpoint` variable.</span></span>

## <a name="psansirendering"></a><span data-ttu-id="d2b19-141">PSAnsiRendering</span><span class="sxs-lookup"><span data-stu-id="d2b19-141">PSAnsiRendering</span></span>

<span data-ttu-id="d2b19-142">Dit experiment is toegevoegd in PowerShell 7.2.</span><span class="sxs-lookup"><span data-stu-id="d2b19-142">This experiment was added in PowerShell 7.2.</span></span> <span data-ttu-id="d2b19-143">Met de functie kunt u wijzigen hoe de PowerShell-engine tekst uitvoert en de automatische variabele toevoegen `$PSStyle` om de ANSI-rendering van tekenreeksuitvoer te bepalen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-143">The feature enables changes how the PowerShell engine outputs text and add the `$PSStyle` automatic variable to control ANSI rendering of string output.</span></span>

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

<span data-ttu-id="d2b19-144">De basisleden retourneren tekenreeksen van ANSI-escapereeksen die aan hun namen zijn toe te geven.</span><span class="sxs-lookup"><span data-stu-id="d2b19-144">The base members return strings of ANSI escape sequences mapped to their names.</span></span> <span data-ttu-id="d2b19-145">De waarden kunnen worden ingesteld om aanpassingen toe te staan.</span><span class="sxs-lookup"><span data-stu-id="d2b19-145">The values are settable to allow customization.</span></span>

<span data-ttu-id="d2b19-146">Zie voor meer informatie [about_Automatic_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)</span><span class="sxs-lookup"><span data-stu-id="d2b19-146">For more information, see [about_Automatic_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)</span></span>

> [!NOTE]
> <span data-ttu-id="d2b19-147">Voor C#-ontwikkelaars hebt u toegang `PSStyle` als een singleton.</span><span class="sxs-lookup"><span data-stu-id="d2b19-147">For C# developers, you can access `PSStyle` as a singleton.</span></span> <span data-ttu-id="d2b19-148">Het gebruik ziet er als volgende uit:</span><span class="sxs-lookup"><span data-stu-id="d2b19-148">Usage will look like this:</span></span>
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> <span data-ttu-id="d2b19-149">`PSStyle` bestaat in de naamruimte System.Management.Automation.</span><span class="sxs-lookup"><span data-stu-id="d2b19-149">`PSStyle` exists in the System.Management.Automation namespace.</span></span>

<span data-ttu-id="d2b19-150">Naast de toegang tot `$PSStyle` introduceert dit wijzigingen in de PowerShell-engine.</span><span class="sxs-lookup"><span data-stu-id="d2b19-150">Along with access to `$PSStyle`, this introduces changes to the PowerShell engine.</span></span> <span data-ttu-id="d2b19-151">Het PowerShell-opmaaksysteem wordt bijgewerkt om te `$PSStyle.OutputRendering` respecteren.</span><span class="sxs-lookup"><span data-stu-id="d2b19-151">The PowerShell formatting system is updated to respect `$PSStyle.OutputRendering`.</span></span>

- <span data-ttu-id="d2b19-152">`StringDecorated` type wordt toegevoegd om ANSI-tekenreeksen met escape-tekenreeksen te verwerken.</span><span class="sxs-lookup"><span data-stu-id="d2b19-152">`StringDecorated` type is added to handle ANSI escaped strings.</span></span>
- <span data-ttu-id="d2b19-153">`string IsDecorated` Booleaanse eigenschap wordt toegevoegd om te retourneren als de tekenreeks ANSI-escapereeksen bevat op basis van of de tekenreeks ESC of C1 CSI bevat.</span><span class="sxs-lookup"><span data-stu-id="d2b19-153">`string IsDecorated` boolean property is added to return if the string contains ANSI escape sequences based on if the string contains ESC or C1 CSI.</span></span>
- <span data-ttu-id="d2b19-154">De `Length` eigenschap _retourneert alleen_ de lengte voor de tekst zonder de ANSI-escapereeksen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-154">The `Length` property returns _only_ the length for the text without the ANSI escape sequences.</span></span>
- <span data-ttu-id="d2b19-155">`StringDecorated Substring(int contentLength)` methode retourneert een subtekenreeks vanaf index 0 tot de inhoudslengte die geen deel uitmaakt van ANSI-escapereeksen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-155">`StringDecorated Substring(int contentLength)` method returns a substring starting at index 0 up to the content length that is not a part of ANSI escape sequences.</span></span> <span data-ttu-id="d2b19-156">Dit is nodig voor tabelopmaak om tekenreeksen af tekapen en ANSI-escapereeksen te behouden die geen afdrukbare tekenruimte in beslag nemen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-156">This is needed for table formatting to truncate strings and preserve ANSI escape sequences that don't take up printable character space.</span></span>
- <span data-ttu-id="d2b19-157">`string ToString()` methode blijft hetzelfde en retourneert de plaintext-versie van de tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d2b19-157">`string ToString()` method stays the same and returns the plaintext version of the string.</span></span>
- <span data-ttu-id="d2b19-158">`string ToString(bool Ansi)` methode retourneert de onbewerkte ingesloten ANSI-tekenreeks als de `Ansi` parameter true is.</span><span class="sxs-lookup"><span data-stu-id="d2b19-158">`string ToString(bool Ansi)` method returns the raw ANSI embedded string if the `Ansi` parameter is true.</span></span> <span data-ttu-id="d2b19-159">Anders wordt een platte-tekstversie met ANSI-escapereeksen verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d2b19-159">Otherwise, a plaintext version with ANSI escape sequences removed is returned.</span></span>

<span data-ttu-id="d2b19-160">De `FormatHyperlink(string text, uri link)` retourneert een tekenreeks met een ANSI-escapereeks die wordt gebruikt voor het inrichten van hyperlinks.</span><span class="sxs-lookup"><span data-stu-id="d2b19-160">The `FormatHyperlink(string text, uri link)` returns a string containing ANSI escape sequence used to decorate hyperlinks.</span></span> <span data-ttu-id="d2b19-161">Sommige terminalhosts, zoals [de Windows Terminal,](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701)ondersteunen deze markering, waardoor de weergegeven tekst in de terminal kan worden geklikt.</span><span class="sxs-lookup"><span data-stu-id="d2b19-161">Some terminal hosts, like the [Windows Terminal](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701), support this markup, which makes the rendered text clickable in the terminal.</span></span>

## <a name="psansiprogress"></a><span data-ttu-id="d2b19-162">PSAnsiProgress</span><span class="sxs-lookup"><span data-stu-id="d2b19-162">PSAnsiProgress</span></span>

<span data-ttu-id="d2b19-163">Dit experiment is toegevoegd in PowerShell 7.2.</span><span class="sxs-lookup"><span data-stu-id="d2b19-163">This experiment was added in PowerShell 7.2.</span></span> <span data-ttu-id="d2b19-164">Met de functie wordt het `$PSStyle.Progress` lid toegevoegd en kunt u de weergavebalk voor voortgangsweergaven bepalen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-164">The feature adds the `$PSStyle.Progress` member and allows you to control progress view bar rendering.</span></span>

- <span data-ttu-id="d2b19-165">`$PSStyle.Progress.Style` - Een ANSI-tekenreeks die de renderingstijl instelt.</span><span class="sxs-lookup"><span data-stu-id="d2b19-165">`$PSStyle.Progress.Style` - An ANSI string setting the rendering style.</span></span>
- <span data-ttu-id="d2b19-166">`$PSStyle.Progress.MaxWidth` - Hiermee stelt u de maximale breedte van de weergave in.</span><span class="sxs-lookup"><span data-stu-id="d2b19-166">`$PSStyle.Progress.MaxWidth` - Sets the max width of the view.</span></span> <span data-ttu-id="d2b19-167">Stel in op `0` voor consolebreedte.</span><span class="sxs-lookup"><span data-stu-id="d2b19-167">Set to `0` for console width.</span></span>
  <span data-ttu-id="d2b19-168">De standaardwaarde is `120`</span><span class="sxs-lookup"><span data-stu-id="d2b19-168">Defaults to `120`</span></span>
- <span data-ttu-id="d2b19-169">`$PSStyle.Progress.View` - Een enum met waarden en `Minimal` `Classic` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-169">`$PSStyle.Progress.View` - An enum with values, `Minimal` and `Classic`.</span></span> <span data-ttu-id="d2b19-170">`Classic` is de bestaande rendering zonder wijzigingen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-170">`Classic` is the existing rendering with no changes.</span></span> <span data-ttu-id="d2b19-171">`Minimal` is één regel minimale rendering.</span><span class="sxs-lookup"><span data-stu-id="d2b19-171">`Minimal` is a single line minimal rendering.</span></span> <span data-ttu-id="d2b19-172">`Minimal` is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="d2b19-172">`Minimal` is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b19-173">Als de host geen ondersteuning biedt voor Virtual Terminal, `$PSStyle.Progress.View` wordt automatisch ingesteld op `Classic` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-173">If the host doesn't support Virtual Terminal, `$PSStyle.Progress.View` is automatically set to `Classic`.</span></span>

<span data-ttu-id="d2b19-174">In het volgende voorbeeld wordt de renderingstijl bijgewerkt naar een minimale voortgangsbalk.</span><span class="sxs-lookup"><span data-stu-id="d2b19-174">The following example updates the rendering style to a minimal progress bar.</span></span>

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> <span data-ttu-id="d2b19-175">U moet de experimentele **functie PSAnsiRendering** hebben ingeschakeld om deze functie te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="d2b19-175">You must have the **PSAnsiRendering** experimental feature enabled to use this feature.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="d2b19-176">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="d2b19-176">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="d2b19-177">Raadt potentiële opdrachten aan op basis van fuzzy zoekopdrachten na **een CommandNotFoundException.**</span><span class="sxs-lookup"><span data-stu-id="d2b19-177">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="d2b19-178">PSAtriceeInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="d2b19-178">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="d2b19-179">Wanneer de linkeropeen in een operator-instructie geen tekenreeks is, wordt die `-replace` operand geconverteerd naar een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="d2b19-179">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="d2b19-180">Wanneer deze functie is uitgeschakeld, wordt met `-replace` de operator een cultuurgevoelige tekenreeksconversie gemaakt.</span><span class="sxs-lookup"><span data-stu-id="d2b19-180">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="d2b19-181">Als uw cultuur bijvoorbeeld is ingesteld op Frans (fr), wordt de `1.2` waarde geconverteerd naar de tekenreeks `1,2` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-181">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="d2b19-182">Met de functie ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="d2b19-182">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="d2b19-183">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="d2b19-183">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="d2b19-184">Hiermee wordt compilatie naar MOF op niet-Windows-systemen mogelijk en wordt het gebruik `Invoke-DSCResource` van zonder LCM mogelijk.</span><span class="sxs-lookup"><span data-stu-id="d2b19-184">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="d2b19-185">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="d2b19-185">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="d2b19-186">Deze functie onderzoekt de opdracht die in de shell is getypt. Als alle opdrachten impliciete proxyopdrachten voor externe toegang zijn die een eenvoudige pijplijn vormen, worden de opdrachten in batche bij elkaar gezet en aangeroepen als één externe pijplijn.</span><span class="sxs-lookup"><span data-stu-id="d2b19-186">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="d2b19-187">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2b19-187">Example:</span></span>

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

<span data-ttu-id="d2b19-188">Zoals hierboven is te zien, worden alle drie de impliciete proxyopdrachten voor externe toegang, , , uitgevoerd in de externe sessie en zijn het resultaat van de pijplijn de enige gegevens die worden geretourneerd naar de `Get-AllProcesses` `Select-Custom` `Group-Stuff` client.</span><span class="sxs-lookup"><span data-stu-id="d2b19-188">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="d2b19-189">Dit vermindert de hoeveelheid gegevens die tussen client en externe sessie heen en weer worden verzonden, en vermindert ook de hoeveelheid objectser serialisatie en deseralisatie.</span><span class="sxs-lookup"><span data-stu-id="d2b19-189">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="d2b19-190">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="d2b19-190">PSNativePSPathResolution</span></span>

<span data-ttu-id="d2b19-191">Als een PSDrive-pad dat gebruikmaakt van de FileSystem-provider wordt doorgegeven aan een systeemeigen opdracht, wordt het om opgeloste bestandspad doorgegeven aan de systeemeigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="d2b19-191">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="d2b19-192">Dit betekent dat een opdracht zoals `code temp:/test.txt` nu werkt zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="d2b19-192">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="d2b19-193">Als in Windows het pad begint met , wordt dat ook opgelost naar het volledige pad en `~` doorgegeven aan de native opdracht.</span><span class="sxs-lookup"><span data-stu-id="d2b19-193">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="d2b19-194">In beide gevallen wordt het pad genormaliseerd naar de mapscheidingstekens voor het relevante besturingssysteem.</span><span class="sxs-lookup"><span data-stu-id="d2b19-194">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="d2b19-195">Als het pad geen PSDrive of `~` (in Windows) is, wordt padnormalisatie niet uitgevoerd</span><span class="sxs-lookup"><span data-stu-id="d2b19-195">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="d2b19-196">Als het pad tussen enkele aanhalingstekens staat, wordt het niet opgelost en behandeld als letterlijke</span><span class="sxs-lookup"><span data-stu-id="d2b19-196">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnotapplyerroractiontostderr"></a><span data-ttu-id="d2b19-197">PSNotApplyErrorActionToStderr</span><span class="sxs-lookup"><span data-stu-id="d2b19-197">PSNotApplyErrorActionToStderr</span></span>

<span data-ttu-id="d2b19-198">Wanneer deze experimentele functie is ingeschakeld, worden foutrecords die worden omgeleid vanuit native opdrachten, zoals bij het gebruik van omleidingsoperators ( ), niet naar de variabele geschreven en heeft de voorkeursvariabele geen invloed op de `2>&1` `$Error` omgeleide `$ErrorActionPreference` uitvoer.</span><span class="sxs-lookup"><span data-stu-id="d2b19-198">When this experimental feature is enabled, error records redirected from native commands, like when using redirection operators (`2>&1`), are not written to the `$Error` variable and the preference variable `$ErrorActionPreference` does not affect the redirected output.</span></span>

<span data-ttu-id="d2b19-199">Veel native opdrachten schrijven naar `stderr` als een alternatieve stroom voor aanvullende informatie.</span><span class="sxs-lookup"><span data-stu-id="d2b19-199">Many native commands write to `stderr` as an alternative stream for additional information.</span></span> <span data-ttu-id="d2b19-200">Dit gedrag kan verwarring veroorzaken bij het zoeken door fouten of de aanvullende uitvoergegevens kunnen verloren gaan voor de gebruiker als is ingesteld op een status die `$ErrorActionPreference` de uitvoer dempt.</span><span class="sxs-lookup"><span data-stu-id="d2b19-200">This behavior can cause confusion when looking through errors or the additional output information can be lost to the user if `$ErrorActionPreference` is set to a state that mutes the output.</span></span>

<span data-ttu-id="d2b19-201">Wanneer een native opdracht een afsluitende code heeft die niet nul `$?` is, wordt ingesteld op `$false` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-201">When a native command has a non-zero exit code, `$?` is set to `$false`.</span></span> <span data-ttu-id="d2b19-202">Als de afsluitende code nul is, `$?` wordt ingesteld op `$true` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-202">If the exit code is zero, `$?` is set to `$true`.</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="d2b19-203">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="d2b19-203">PSNullConditionalOperators</span></span>

<span data-ttu-id="d2b19-204">Introduceert nieuwe operators voor operators voor voorwaardelijke toegang tot null-leden - `?.` en `?[]` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-204">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="d2b19-205">Null-operators voor lidtoegang kunnen worden gebruikt voor scalaire typen en matrixtypen.</span><span class="sxs-lookup"><span data-stu-id="d2b19-205">Null member access operators can be used on scalar types and array types.</span></span> <span data-ttu-id="d2b19-206">Retourneert de waarde van het lid dat toegang heeft als de variabele niet null is.</span><span class="sxs-lookup"><span data-stu-id="d2b19-206">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="d2b19-207">Als de waarde van de variabele null is, retourneert u null.</span><span class="sxs-lookup"><span data-stu-id="d2b19-207">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="d2b19-208">De eigenschap wordt gebruikt en de waarde wordt alleen geretourneerd `propname` als `$x` niet null is.</span><span class="sxs-lookup"><span data-stu-id="d2b19-208">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="d2b19-209">Op dezelfde manier wordt de indexer alleen gebruikt als `$x` niet null is.</span><span class="sxs-lookup"><span data-stu-id="d2b19-209">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="d2b19-210">Als `$x` null is, wordt null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d2b19-210">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="d2b19-211">De operators en zijn operators voor lidtoegang en staan geen spatie toe tussen de naam van de `?.` `?[]` variabele en de operator.</span><span class="sxs-lookup"><span data-stu-id="d2b19-211">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="d2b19-212">Aangezien PowerShell het mogelijk maakt als onderdeel van de naam van de variabele, is ondubbelzinnigheid vereist wanneer de operators worden gebruikt zonder een spatie tussen de naam van de variabele `?` en de operator.</span><span class="sxs-lookup"><span data-stu-id="d2b19-212">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="d2b19-213">Om ondubbelzinnig te zijn, moeten de variabelen rond de `{}` variabelenaam gebruiken, zoals `${x?}?.propertyName` of `${y}?[0]` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-213">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b19-214">Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7.1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d2b19-214">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="d2b19-215">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="d2b19-215">PSTempDrive</span></span>

<span data-ttu-id="d2b19-216">Hiermee maakt u `TEMP:` de PSDrive die is toe te staan aan het tijdelijke directorypad van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="d2b19-216">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b19-217">Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d2b19-217">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="d2b19-218">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="d2b19-218">PSUnixFileStat</span></span>

<span data-ttu-id="d2b19-219">Deze functie biedt nieuw gedrag om gegevens uit de Unix **stat** API op te nemen in de uitvoer van de bestandssysteemprovider om een meer Unix-achtige bestandsvermelding mogelijk te maken.</span><span class="sxs-lookup"><span data-stu-id="d2b19-219">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="d2b19-220">Er wordt een nieuwe notitie-eigenschap toegevoegd in de bestandssysteemprovider met de naam **UnixStat** die een algemene expressie van de API van het `stat(2)` onderliggende Unix-typesysteem bevat.</span><span class="sxs-lookup"><span data-stu-id="d2b19-220">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="d2b19-221">De uitvoer van `Get-ChildItem` ziet er als de volgende uit:</span><span class="sxs-lookup"><span data-stu-id="d2b19-221">The output from `Get-ChildItem` should look something like this:</span></span>

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
> <span data-ttu-id="d2b19-222">Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7.1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d2b19-222">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7.1 and higher.</span></span>

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="d2b19-223">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="d2b19-223">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="d2b19-224">Met deze functie kunt u tabs van afgekorte cmdlets en functies voltooien:</span><span class="sxs-lookup"><span data-stu-id="d2b19-224">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="d2b19-225">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d2b19-225">For example:</span></span>

- <span data-ttu-id="d2b19-226">`i-psdf<tab>` retourneert `Import-PowerShellDataFile` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-226">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="d2b19-227">`u-akvmssdr<tab>` Retourneert `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="d2b19-227">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="d2b19-228">Dit werkt alleen voor tabinvulling (interactief gebruik), dus is geen geldige `i-psdf` cmdlet-naam in een script.</span><span class="sxs-lookup"><span data-stu-id="d2b19-228">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="d2b19-229">Deze functie is uit de experimentele fase verplaatst en is een algemene functie in PowerShell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="d2b19-229">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="pssubsystempluginmodel"></a><span data-ttu-id="d2b19-230">PSSubsystemPluginModel</span><span class="sxs-lookup"><span data-stu-id="d2b19-230">PSSubsystemPluginModel</span></span>

<span data-ttu-id="d2b19-231">Met deze functie schakelt u het invoegmodel van het subsysteem in PowerShell in.</span><span class="sxs-lookup"><span data-stu-id="d2b19-231">This feature enables the subsystem plugin model in PowerShell.</span></span> <span data-ttu-id="d2b19-232">De functie maakt het mogelijk om onderdelen van te `System.Management.Automation.dll` scheiden in afzonderlijke subsystemen die zich in hun eigen assembly bevinden.</span><span class="sxs-lookup"><span data-stu-id="d2b19-232">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="d2b19-233">Door deze scheiding wordt de schijfvoetafdruk van de PowerShell-kernentafdruk verkleind en kunnen deze onderdelen optionele functies worden voor een minimale PowerShell-installatie.</span><span class="sxs-lookup"><span data-stu-id="d2b19-233">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="d2b19-234">Momenteel wordt alleen **het subsysteem CommandPredictor** ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d2b19-234">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="d2b19-235">Dit subsysteem wordt samen met de PSReadLine-module gebruikt om aangepaste voorspellingsinvoegingen te bieden.</span><span class="sxs-lookup"><span data-stu-id="d2b19-235">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="d2b19-236">In de toekomst **kunnen Taak,** **CommandCompleter,** **Externe** externe mogelijkheden en andere onderdelen worden gescheiden in subsysteemassemblage buiten `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="d2b19-236">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

<span data-ttu-id="d2b19-237">De experimentele functie bevat een nieuwe cmdlet, [Get-PSSubsystem.](xref:Microsoft.PowerShell.Core.Get-PSSubsystem)</span><span class="sxs-lookup"><span data-stu-id="d2b19-237">The experimental feature includes a new cmdlet, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem).</span></span> <span data-ttu-id="d2b19-238">Deze cmdlet is alleen beschikbaar wanneer de functie is ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="d2b19-238">This cmdlet is only available when the feature is enabled.</span></span> <span data-ttu-id="d2b19-239">Deze cmdlet retourneert informatie over de subsystemen die beschikbaar zijn op het systeem.</span><span class="sxs-lookup"><span data-stu-id="d2b19-239">This cmdlet returns information about the subsystems that are available on the system.</span></span>
