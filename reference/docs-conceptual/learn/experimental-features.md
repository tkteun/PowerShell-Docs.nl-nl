---
ms.date: 04/28/2020
title: Experimentele functies gebruiken in Power shell
description: Een lijst met de momenteel beschik bare experimentele functies en hoe u deze kunt gebruiken.
ms.openlocfilehash: 72a4309d6eeede4cd2ff7c38ce8e99ce3ace30eb
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810559"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="5674c-103">Experimentele functies gebruiken in Power shell</span><span class="sxs-lookup"><span data-stu-id="5674c-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="5674c-104">De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5674c-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="5674c-105">Een experimentele functie is een onderdeel waar het ontwerp niet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="5674c-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="5674c-106">De functie is beschikbaar voor gebruikers om te testen en feedback te geven.</span><span class="sxs-lookup"><span data-stu-id="5674c-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="5674c-107">Zodra een experimentele functie is voltooid, worden de wijzigingen in het ontwerp doorgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5674c-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span>

> [!CAUTION]
> <span data-ttu-id="5674c-108">Experimentele functies zijn niet bedoeld om te worden gebruikt in productie, omdat de wijzigingen niet mogen worden opgesplitst.</span><span class="sxs-lookup"><span data-stu-id="5674c-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span> <span data-ttu-id="5674c-109">Experimentele functies worden niet officieel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5674c-109">Experimental features are not officially supported.</span></span> <span data-ttu-id="5674c-110">We waarderen echter alle feedback-en fouten rapporten.</span><span class="sxs-lookup"><span data-stu-id="5674c-110">However, we appreciate any feedback and bug reports.</span></span> <span data-ttu-id="5674c-111">U kunt problemen in de [github-bron opslagplaats](https://github.com/PowerShell/PowerShell/issues/new/choose)opslaan.</span><span class="sxs-lookup"><span data-stu-id="5674c-111">You can file issues in the [GitHub source repository](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

<span data-ttu-id="5674c-112">Zie [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)voor meer informatie over het in-of uitschakelen van deze functies.</span><span class="sxs-lookup"><span data-stu-id="5674c-112">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="5674c-113">Beschikbare functies</span><span class="sxs-lookup"><span data-stu-id="5674c-113">Available features</span></span>

<span data-ttu-id="5674c-114">In dit artikel worden de experimentele functies beschreven die beschikbaar zijn en hoe u deze functie kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5674c-114">This article describes the experimental features that are available and how to use the feature.</span></span>

|                            <span data-ttu-id="5674c-115">Naam</span><span class="sxs-lookup"><span data-stu-id="5674c-115">Name</span></span>                            |   <span data-ttu-id="5674c-116">6.2</span><span class="sxs-lookup"><span data-stu-id="5674c-116">6.2</span></span>   |   <span data-ttu-id="5674c-117">7.0</span><span class="sxs-lookup"><span data-stu-id="5674c-117">7.0</span></span>   | <span data-ttu-id="5674c-118">7,1 (preview-versie)</span><span class="sxs-lookup"><span data-stu-id="5674c-118">7.1 (preview)</span></span> |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| <span data-ttu-id="5674c-119">PSTempDrive (mainstream in PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="5674c-119">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |               |
| <span data-ttu-id="5674c-120">PSUseAbbreviationExpansion (mainstream in PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="5674c-120">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |               |
| <span data-ttu-id="5674c-121">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="5674c-121">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; |    &check;    |
| <span data-ttu-id="5674c-122">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="5674c-122">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; |    &check;    |
| <span data-ttu-id="5674c-123">Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="5674c-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; |    &check;    |
| <span data-ttu-id="5674c-124">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="5674c-124">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; |    &check;    |
| <span data-ttu-id="5674c-125">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="5674c-125">PSNullConditionalOperators</span></span>                                 |         | &check; |    &check;    |
| <span data-ttu-id="5674c-126">PSUnixFileStat (niet-Windows)</span><span class="sxs-lookup"><span data-stu-id="5674c-126">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; |    &check;    |
| <span data-ttu-id="5674c-127">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="5674c-127">PSNativePSPathResolution</span></span>                                   |         |         |    &check;    |
| <span data-ttu-id="5674c-128">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="5674c-128">PSCultureInvariantReplaceOperator</span></span>                          |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="5674c-129">Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="5674c-129">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="5674c-130">Hiermee schakelt u de para meter **BreakAll** in op de `Debug-Runspace` `Debug-Job` cmdlets, zodat gebruikers kunnen bepalen of ze Power shell direct op de huidige locatie moeten afkraken wanneer ze een debugger koppelen.</span><span class="sxs-lookup"><span data-stu-id="5674c-130">Enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="5674c-131">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="5674c-131">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="5674c-132">Raadt potentiële opdrachten aan op basis van zoek acties op fuzzy na een **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="5674c-132">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="5674c-133">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="5674c-133">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="5674c-134">Wanneer de linkeroperand in een `-replace` operator instructie geen teken reeks is, wordt die operand geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="5674c-134">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="5674c-135">Als deze functie is uitgeschakeld, `-replace` heeft de operator een cultuur gevoelige teken reeks conversie.</span><span class="sxs-lookup"><span data-stu-id="5674c-135">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="5674c-136">Als uw cultuur bijvoorbeeld is ingesteld op Frans (FR), wordt de waarde `1.2` geconverteerd naar de teken reeks `1,2` .</span><span class="sxs-lookup"><span data-stu-id="5674c-136">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="5674c-137">Als de functie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="5674c-137">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="5674c-138">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="5674c-138">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="5674c-139">Hiermee wordt de compilatie op MOF op niet-Windows-systemen ingeschakeld en wordt het gebruik van `Invoke-DSCResource` zonder LCM ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="5674c-139">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="5674c-140">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="5674c-140">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="5674c-141">Met deze functie wordt de in de shell getypte opdracht onderzocht. als alle opdrachten impliciet externe proxy opdrachten zijn die een eenvoudige pijp lijn vormen, worden de opdrachten in batch verzameld en aangeroepen als één externe pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="5674c-141">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="5674c-142">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5674c-142">Example:</span></span>

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

<span data-ttu-id="5674c-143">Zoals hierboven wordt weer gegeven, terwijl de batch functie is ingeschakeld, worden alle drie de impliciete externe proxy opdrachten,,,, `Get-AllProcesses` `Select-Custom` `Group-Stuff` uitgevoerd in de externe sessie en het resultaat van de pijp lijn de enige gegevens die worden geretourneerd naar de client.</span><span class="sxs-lookup"><span data-stu-id="5674c-143">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="5674c-144">Dit vermindert de hoeveelheid gegevens die wordt verzonden tussen de client en de externe sessie, en vermindert ook de hoeveelheid object-serialisatie en deserialisatie.</span><span class="sxs-lookup"><span data-stu-id="5674c-144">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="5674c-145">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="5674c-145">PSNativePSPathResolution</span></span>

<span data-ttu-id="5674c-146">Als een PSDrive-pad dat gebruikmaakt van de File System Provider wordt door gegeven aan een systeem eigen opdracht, wordt het omgezette bestandspad door gegeven aan de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="5674c-146">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="5674c-147">Dit betekent dat een opdracht zoals `code temp:/test.txt` nu werkt zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="5674c-147">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="5674c-148">Ook in Windows, als het pad begint met `~` , dat wordt omgezet naar het volledige pad en wordt door gegeven aan de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="5674c-148">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="5674c-149">In beide gevallen wordt het pad genormaliseerd naar de adres lijst scheidings tekens voor het relevante besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="5674c-149">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="5674c-150">Als het pad geen PSDrive of `~` (in Windows) is, treedt de normalisatie van het pad niet op</span><span class="sxs-lookup"><span data-stu-id="5674c-150">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="5674c-151">Als het pad zich in enkele aanhalings tekens bevindt, wordt het niet opgelost en behandeld als een letterlijke waarde</span><span class="sxs-lookup"><span data-stu-id="5674c-151">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="5674c-152">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="5674c-152">PSNullConditionalOperators</span></span>

<span data-ttu-id="5674c-153">Hierin worden nieuwe Opera tors geïntroduceerd voor de null-Opera tors voor voorwaardelijke toegang, `?.` en `?[]` .</span><span class="sxs-lookup"><span data-stu-id="5674c-153">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="5674c-154">Toegangs operatoren voor Null-leden kunnen worden gebruikt voor scalaire typen en matrix typen.</span><span class="sxs-lookup"><span data-stu-id="5674c-154">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="5674c-155">Retourneert de waarde van het geopende lid als de variabele niet null is.</span><span class="sxs-lookup"><span data-stu-id="5674c-155">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="5674c-156">Als de waarde van de variabele null is, retourneert dan Null.</span><span class="sxs-lookup"><span data-stu-id="5674c-156">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="5674c-157">De eigenschap `propname` is toegankelijk en de waarde ervan wordt alleen geretourneerd als deze `$x` niet null is.</span><span class="sxs-lookup"><span data-stu-id="5674c-157">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="5674c-158">De Indexeer functie wordt op dezelfde manier gebruikt als `$x` niet null is.</span><span class="sxs-lookup"><span data-stu-id="5674c-158">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="5674c-159">Als `$x` is null is, wordt Null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5674c-159">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="5674c-160">De `?.` `?[]` Opera tors en zijn lid van de operator toegang en staan geen ruimte tussen de naam van de variabele en de operator toe.</span><span class="sxs-lookup"><span data-stu-id="5674c-160">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="5674c-161">Omdat Power shell `?` als onderdeel van de naam van de variabele is toegestaan, is ondubbelzinnige installatie vereist wanneer de Opera tors worden gebruikt zonder ruimte tussen de naam van de variabele en de operator.</span><span class="sxs-lookup"><span data-stu-id="5674c-161">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="5674c-162">Voor dubbel zinnigheid moeten de variabelen worden gebruikt `{}` om de naam van de variabele te gebruiken, zoals: `${x?}?.propertyName` of `${y}?[0]` .</span><span class="sxs-lookup"><span data-stu-id="5674c-162">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="5674c-163">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="5674c-163">PSTempDrive</span></span>

<span data-ttu-id="5674c-164">Hiermee maakt `TEMP:` u de PSDrive die is toegewezen aan het pad naar de tijdelijke map van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="5674c-164">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="5674c-165">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="5674c-165">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="5674c-166">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="5674c-166">PSUnixFileStat</span></span>

<span data-ttu-id="5674c-167">Deze functie biedt nieuw gedrag om gegevens op te nemen uit de UNIX **stat** -API in de uitvoer van de bestandssysteem provider om een meer Unix-achtige bestands vermelding te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="5674c-167">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="5674c-168">Er wordt een nieuwe notitie-eigenschap toegevoegd aan de bestandssysteem provider met de naam **UnixStat** die een gemeen schappelijke expressie van de `stat(2)` API van het onderliggende UNIX-type systeem bevat.</span><span class="sxs-lookup"><span data-stu-id="5674c-168">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="5674c-169">De uitvoer van `Get-ChildItem` moet er ongeveer als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="5674c-169">The output from `Get-ChildItem` should look something like this:</span></span>

```powershell
PS> dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="5674c-170">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="5674c-170">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="5674c-171">Met deze functie kunt u het tabblad volt ooien van verkorte cmdlets en functies:</span><span class="sxs-lookup"><span data-stu-id="5674c-171">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="5674c-172">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="5674c-172">For example:</span></span>

- <span data-ttu-id="5674c-173">`i-psdf<tab>`retourneert `Import-PowerShellDataFile` .</span><span class="sxs-lookup"><span data-stu-id="5674c-173">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="5674c-174">`u-akvmssdr<tab>`retourneert`Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="5674c-174">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="5674c-175">Dit werkt alleen voor tabblad voltooiing (interactief gebruik), dus `i-psdf` is geen geldige cmdlet-naam in een script.</span><span class="sxs-lookup"><span data-stu-id="5674c-175">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="5674c-176">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="5674c-176">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>
