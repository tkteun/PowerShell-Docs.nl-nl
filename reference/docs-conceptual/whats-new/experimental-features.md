---
ms.date: 04/28/2020
title: Experimentele functies gebruiken in Power shell
description: Een lijst met de momenteel beschik bare experimentele functies en hoe u deze kunt gebruiken.
ms.openlocfilehash: e2c9f30cb1d4ec7b89596cebd1e5df27968626cc
ms.sourcegitcommit: a5e945e0889d0635b7af767d80d6a13bc5526269
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82587391"
---
# <a name="using-experimental-features-in-powershell"></a><span data-ttu-id="1b0a5-103">Experimentele functies gebruiken in Power shell</span><span class="sxs-lookup"><span data-stu-id="1b0a5-103">Using Experimental Features in PowerShell</span></span>

<span data-ttu-id="1b0a5-104">De experimentele functies ondersteuning in Power shell biedt een mechanisme voor experimentele functies die naast bestaande stabiele functies in Power shell-of Power shell-modules kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="1b0a5-105">In dit artikel worden de experimentele functies beschreven die beschikbaar zijn en hoe u deze functie kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-105">This article describes the experimental features that are available and how to use the feature.</span></span> <span data-ttu-id="1b0a5-106">Zie [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features)voor meer informatie over het in-of uitschakelen van deze functies.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-106">For more information about enabling or disabling these features, see [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).</span></span>

## <a name="available-features"></a><span data-ttu-id="1b0a5-107">Beschikbare functies</span><span class="sxs-lookup"><span data-stu-id="1b0a5-107">Available features</span></span>

<span data-ttu-id="1b0a5-108">De volgende tabel geeft een lijst van de functies die beschikbaar zijn in verschillende versies van Power shell.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-108">The following table lists the feature that are available in various versions of PowerShell.</span></span>

|                            <span data-ttu-id="1b0a5-109">Naam</span><span class="sxs-lookup"><span data-stu-id="1b0a5-109">Name</span></span>                            |   <span data-ttu-id="1b0a5-110">6.2</span><span class="sxs-lookup"><span data-stu-id="1b0a5-110">6.2</span></span>   |   <span data-ttu-id="1b0a5-111">7.0</span><span class="sxs-lookup"><span data-stu-id="1b0a5-111">7.0</span></span>   | <span data-ttu-id="1b0a5-112">7,1 (preview-versie)</span><span class="sxs-lookup"><span data-stu-id="1b0a5-112">7.1 (preview)</span></span> |
| ---------------------------------------------------------- | :-----: | :-----: | :-----------: |
| <span data-ttu-id="1b0a5-113">PSTempDrive (mainstream in PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="1b0a5-113">PSTempDrive (mainstream in PS 7.0+)</span></span>                        | &check; |         |               |
| <span data-ttu-id="1b0a5-114">PSUseAbbreviationExpansion (mainstream in PS 7.0 +)</span><span class="sxs-lookup"><span data-stu-id="1b0a5-114">PSUseAbbreviationExpansion (mainstream in PS 7.0+)</span></span>         | &check; |         |               |
| <span data-ttu-id="1b0a5-115">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="1b0a5-115">PSCommandNotFoundSuggestion</span></span>                                | &check; | &check; |    &check;    |
| <span data-ttu-id="1b0a5-116">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="1b0a5-116">PSImplicitRemotingBatching</span></span>                                 | &check; | &check; |    &check;    |
| <span data-ttu-id="1b0a5-117">Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="1b0a5-117">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span> |         | &check; |    &check;    |
| <span data-ttu-id="1b0a5-118">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="1b0a5-118">PSDesiredStateConfiguration.InvokeDscResource</span></span>              |         | &check; |    &check;    |
| <span data-ttu-id="1b0a5-119">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="1b0a5-119">PSNullConditionalOperators</span></span>                                 |         | &check; |    &check;    |
| <span data-ttu-id="1b0a5-120">PSUnixFileStat (niet-Windows)</span><span class="sxs-lookup"><span data-stu-id="1b0a5-120">PSUnixFileStat (non-Windows only)</span></span>                          |         | &check; |    &check;    |
| <span data-ttu-id="1b0a5-121">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="1b0a5-121">PSNativePSPathResolution</span></span>                                   |         |         |    &check;    |
| <span data-ttu-id="1b0a5-122">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="1b0a5-122">PSCultureInvariantReplaceOperator</span></span>                          |         |         |    &check;    |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a><span data-ttu-id="1b0a5-123">Micro soft. Power shell. Utility. PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="1b0a5-123">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>

<span data-ttu-id="1b0a5-124">Hiermee schakelt **BreakAll** u de para meter `Debug-Runspace` BreakAll `Debug-Job` in op de cmdlets, zodat gebruikers kunnen bepalen of ze Power shell direct op de huidige locatie moeten afkraken wanneer ze een debugger koppelen.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-124">Enables the **BreakAll** parameter on the `Debug-Runspace` and `Debug-Job` cmdlets to allow users to decide if they want PowerShell to break immediately in the current location when they attach a debugger.</span></span>

## <a name="pscommandnotfoundsuggestion"></a><span data-ttu-id="1b0a5-125">PSCommandNotFoundSuggestion</span><span class="sxs-lookup"><span data-stu-id="1b0a5-125">PSCommandNotFoundSuggestion</span></span>

<span data-ttu-id="1b0a5-126">Raadt potentiële opdrachten aan op basis van zoek acties op fuzzy na een **CommandNotFoundException**.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-126">Recommends potential commands based on fuzzy matching search after a **CommandNotFoundException**.</span></span>

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

## <a name="pscultureinvariantreplaceoperator"></a><span data-ttu-id="1b0a5-127">PSCultureInvariantReplaceOperator</span><span class="sxs-lookup"><span data-stu-id="1b0a5-127">PSCultureInvariantReplaceOperator</span></span>

<span data-ttu-id="1b0a5-128">Wanneer de linkeroperand in een `-replace` operator instructie geen teken reeks is, wordt die operand geconverteerd naar een teken reeks.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-128">When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span>

<span data-ttu-id="1b0a5-129">Als deze functie is uitgeschakeld, heeft `-replace` de operator een cultuur gevoelige teken reeks conversie.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-129">When this feature is disabled, the `-replace` operator does a culture-sensitive string conversion.</span></span>
<span data-ttu-id="1b0a5-130">Als uw cultuur bijvoorbeeld is ingesteld op Frans (FR), wordt de waarde `1.2` geconverteerd naar de teken reeks. `1,2`</span><span class="sxs-lookup"><span data-stu-id="1b0a5-130">For example, if your culture is set to French (fr), the value `1.2` is converted to the string `1,2`.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

<span data-ttu-id="1b0a5-131">Als de functie is ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="1b0a5-131">With the feature enabled:</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a><span data-ttu-id="1b0a5-132">PSDesiredStateConfiguration.InvokeDscResource</span><span class="sxs-lookup"><span data-stu-id="1b0a5-132">PSDesiredStateConfiguration.InvokeDscResource</span></span>

<span data-ttu-id="1b0a5-133">Hiermee wordt de compilatie op MOF op niet-Windows-systemen ingeschakeld en `Invoke-DSCResource` wordt het gebruik van zonder LCM ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-133">Enables compilation to MOF on non-Windows systems and enables the use of `Invoke-DSCResource` without an LCM.</span></span>

## <a name="psimplicitremotingbatching"></a><span data-ttu-id="1b0a5-134">PSImplicitRemotingBatching</span><span class="sxs-lookup"><span data-stu-id="1b0a5-134">PSImplicitRemotingBatching</span></span>

<span data-ttu-id="1b0a5-135">Met deze functie wordt de in de shell getypte opdracht onderzocht. als alle opdrachten impliciet externe proxy opdrachten zijn die een eenvoudige pijp lijn vormen, worden de opdrachten in batch verzameld en aangeroepen als één externe pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-135">This feature examines the command typed in the shell, and if all the commands are implicit remoting proxy commands that form a simple pipeline, then the commands are batched together and invoked as a single remote pipeline.</span></span>

<span data-ttu-id="1b0a5-136">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1b0a5-136">Example:</span></span>

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

<span data-ttu-id="1b0a5-137">Zoals hierboven wordt weer gegeven, terwijl de batch functie is ingeschakeld, worden alle drie de impliciete `Get-AllProcesses`externe `Select-Custom`proxy `Group-Stuff`opdrachten,,,, uitgevoerd in de externe sessie en het resultaat van de pijp lijn de enige gegevens die worden geretourneerd naar de client.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-137">As seen above, with the batching feature enabled, all three implicit remoting proxy commands, `Get-AllProcesses`, `Select-Custom`, `Group-Stuff`, run in the remote session and the result from the pipeline is the only data returned to the client.</span></span> <span data-ttu-id="1b0a5-138">Dit vermindert de hoeveelheid gegevens die wordt verzonden tussen de client en de externe sessie, en vermindert ook de hoeveelheid object-serialisatie en deserialisatie.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-138">This decreases the amount of data sent back and forth between client and remote session, and also reduces the amount of object serialization and de-serialization.</span></span>

## <a name="psnativepspathresolution"></a><span data-ttu-id="1b0a5-139">PSNativePSPathResolution</span><span class="sxs-lookup"><span data-stu-id="1b0a5-139">PSNativePSPathResolution</span></span>

<span data-ttu-id="1b0a5-140">Als een PSDrive-pad dat gebruikmaakt van de File System Provider wordt door gegeven aan een systeem eigen opdracht, wordt het omgezette bestandspad door gegeven aan de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-140">If a PSDrive path that uses the FileSystem provider is passed to a native command, the resolved file path is passed to the native command.</span></span> <span data-ttu-id="1b0a5-141">Dit betekent dat een opdracht `code temp:/test.txt` zoals nu werkt zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-141">This means a command like `code temp:/test.txt` now works as expected.</span></span>

<span data-ttu-id="1b0a5-142">Ook in Windows, als het pad begint met `~`, dat wordt omgezet naar het volledige pad en wordt door gegeven aan de systeem eigen opdracht.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-142">Also, on Windows, if the path starts with `~`, that is resolved to the full path and passed to the native command.</span></span> <span data-ttu-id="1b0a5-143">In beide gevallen wordt het pad genormaliseerd naar de adres lijst scheidings tekens voor het relevante besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-143">In both cases, the path is normalized to the directory separators for the relevant operating system.</span></span>

- <span data-ttu-id="1b0a5-144">Als het pad geen PSDrive of `~` (in Windows) is, treedt de normalisatie van het pad niet op</span><span class="sxs-lookup"><span data-stu-id="1b0a5-144">If the path is not a PSDrive or `~` (on Windows), then path normalization doesn't occur</span></span>
- <span data-ttu-id="1b0a5-145">Als het pad zich in enkele aanhalings tekens bevindt, wordt het niet opgelost en behandeld als een letterlijke waarde</span><span class="sxs-lookup"><span data-stu-id="1b0a5-145">If the path is in single quotes, then it's not resolved and treated as literal</span></span>

## <a name="psnullconditionaloperators"></a><span data-ttu-id="1b0a5-146">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="1b0a5-146">PSNullConditionalOperators</span></span>

<span data-ttu-id="1b0a5-147">Hierin worden nieuwe Opera tors geïntroduceerd voor de null- `?.` Opera `?[]`tors voor voorwaardelijke toegang, en.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-147">Introduces new operators for Null conditional member access operators - `?.` and `?[]`.</span></span> <span data-ttu-id="1b0a5-148">Toegangs operatoren voor Null-leden kunnen worden gebruikt voor scalaire typen en matrix typen.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-148">Null member access operators can used on scalar types and array types.</span></span> <span data-ttu-id="1b0a5-149">Retourneert de waarde van het geopende lid als de variabele niet null is.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-149">Return the value of the accessed member if the variable is not null.</span></span> <span data-ttu-id="1b0a5-150">Als de waarde van de variabele null is, retourneert dan Null.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-150">If the value of the variable is null, then return null.</span></span>

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

<span data-ttu-id="1b0a5-151">De eigenschap `propname` is toegankelijk en de waarde ervan wordt alleen geretourneerd als `$x` deze niet null is.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-151">The property `propname` is accessed and it's value is returned only if `$x` is not null.</span></span> <span data-ttu-id="1b0a5-152">De Indexeer functie wordt op dezelfde manier gebruikt als `$x` niet null is.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-152">Similarly, the indexer is used only if `$x` is not null.</span></span> <span data-ttu-id="1b0a5-153">Als `$x` is null is, wordt Null geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-153">If `$x` is null, then null is returned.</span></span>

<span data-ttu-id="1b0a5-154">De `?.` Opera `?[]` tors en zijn lid van de operator toegang en staan geen ruimte tussen de naam van de variabele en de operator toe.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-154">The `?.` and `?[]` operators are member access operators and do not allow a space in between the variable name and the operator.</span></span>

<span data-ttu-id="1b0a5-155">Omdat Power shell `?` als onderdeel van de naam van de variabele is toegestaan, is ondubbelzinnige installatie vereist wanneer de Opera tors worden gebruikt zonder ruimte tussen de naam van de variabele en de operator.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-155">Since PowerShell allows `?` as part of the variable name, disambiguation is required when the operators are used without a space between the variable name and the operator.</span></span> <span data-ttu-id="1b0a5-156">Voor dubbel zinnigheid moeten de variabelen worden gebruikt `{}` om de naam van de variabele `${x?}?.propertyName` te `${y}?[0]`gebruiken, zoals: of.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-156">To disambiguate, the variables must use `{}` around the variable name like: `${x?}?.propertyName` or `${y}?[0]`.</span></span>

## <a name="pstempdrive"></a><span data-ttu-id="1b0a5-157">PSTempDrive</span><span class="sxs-lookup"><span data-stu-id="1b0a5-157">PSTempDrive</span></span>

<span data-ttu-id="1b0a5-158">Hiermee maakt `TEMP:` u de PSDrive die is toegewezen aan het pad naar de tijdelijke map van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-158">Creates the `TEMP:` PSDrive mapped to user's temporary directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="1b0a5-159">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-159">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>

## <a name="psunixfilestat"></a><span data-ttu-id="1b0a5-160">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="1b0a5-160">PSUnixFileStat</span></span>

<span data-ttu-id="1b0a5-161">Deze functie biedt nieuw gedrag om gegevens op te nemen uit de UNIX **stat** -API in de uitvoer van de bestandssysteem provider om een meer Unix-achtige bestands vermelding te vergemakkelijken.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-161">This feature provides new behavior to include data from the Unix **stat** API in the output of the file system provider to facilitate a more Unix-like file listing.</span></span> <span data-ttu-id="1b0a5-162">Er wordt een nieuwe notitie-eigenschap toegevoegd aan de bestandssysteem provider met de naam **UnixStat** die een `stat(2)` gemeen schappelijke expressie van de API van het onderliggende UNIX-type systeem bevat.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-162">It adds a new note property in the filesystem provider named **UnixStat** that includes a common expression of the `stat(2)` API from the underlying Unix type system.</span></span>

<span data-ttu-id="1b0a5-163">De uitvoer van `Get-ChildItem` moet er ongeveer als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="1b0a5-163">The output from `Get-ChildItem` should look something like this:</span></span>

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

## <a name="psuseabbreviationexpansion"></a><span data-ttu-id="1b0a5-164">PSUseAbbreviationExpansion</span><span class="sxs-lookup"><span data-stu-id="1b0a5-164">PSUseAbbreviationExpansion</span></span>

<span data-ttu-id="1b0a5-165">Met deze functie kunt u het tabblad volt ooien van verkorte cmdlets en functies:</span><span class="sxs-lookup"><span data-stu-id="1b0a5-165">This feature enables tab-completion of abbreviated cmdlets and functions:</span></span>

<span data-ttu-id="1b0a5-166">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1b0a5-166">For example:</span></span>

- <span data-ttu-id="1b0a5-167">`i-psdf<tab>`retourneert `Import-PowerShellDataFile`.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-167">`i-psdf<tab>` returns `Import-PowerShellDataFile`.</span></span>
- <span data-ttu-id="1b0a5-168">`u-akvmssdr<tab>`retourneert`Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span><span class="sxs-lookup"><span data-stu-id="1b0a5-168">`u-akvmssdr<tab>` returns `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`</span></span>

<span data-ttu-id="1b0a5-169">Dit werkt alleen voor tabblad voltooiing (interactief gebruik), dus `i-psdf` is geen geldige cmdlet-naam in een script.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-169">This only works for tab completion (interactive use), so `i-psdf` is not a valid cmdlet name in a script.</span></span>

> [!NOTE]
> <span data-ttu-id="1b0a5-170">Deze functie is uit de experimentele fase verplaatst en is een mainstream functie in Power shell 7 en hoger.</span><span class="sxs-lookup"><span data-stu-id="1b0a5-170">This feature has moved out of the experimental phase and is a mainstream feature in PowerShell 7 and higher.</span></span>
