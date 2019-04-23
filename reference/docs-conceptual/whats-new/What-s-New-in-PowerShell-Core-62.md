---
title: Wat is er nieuw in PowerShell Core 6.2
description: Nieuwe functies en wijzigingen die zijn uitgebracht in PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 6a0da8a410e602ae3963e0bc7bace745317d7d4b
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984490"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="67b37-103">Wat is er nieuw in PowerShell Core 6.2</span><span class="sxs-lookup"><span data-stu-id="67b37-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="67b37-104">De PowerShell Core 6.2-versie gericht op verbeteringen in queryprestaties, oplossingen voor problemen en kleinere-cmdlet en taal-uitbreidingen ter verbetering van de kwaliteit.</span><span class="sxs-lookup"><span data-stu-id="67b37-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="67b37-105">Een volledige lijst van de verbeteringen wilt bekijken, Bekijk onze gedetailleerde [changelogs](https://github.com/PowerShell/PowerShell/releases) op GitHub.</span><span class="sxs-lookup"><span data-stu-id="67b37-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="67b37-106">Experimentele functies</span><span class="sxs-lookup"><span data-stu-id="67b37-106">Experimental Features</span></span>

<span data-ttu-id="67b37-107">Eerder moesten we ondersteuning voor ingeschakeld [experimentele functies][].</span><span class="sxs-lookup"><span data-stu-id="67b37-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="67b37-108">In de 6.2 release hebben we vier experimentele functies om uit te proberen. Geef feedback, zodat we verbeteringen kunnen maken en om te bepalen of de functie is waard is om bevordering van de algemene status.</span><span class="sxs-lookup"><span data-stu-id="67b37-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="67b37-109">Gebruik `Get-ExperimentalFeature` voor een lijst van beschikbare experimentele functies.</span><span class="sxs-lookup"><span data-stu-id="67b37-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="67b37-110">U kunt inschakelen of uitschakelen van deze functies met `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="67b37-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="67b37-111">Kan de opdracht niet vinden suggesties</span><span class="sxs-lookup"><span data-stu-id="67b37-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="67b37-112">Deze functie maakt gebruik van zoeken bij benadering suggesties voor opdrachten of -cmdlets die u hebt misschien vinden.</span><span class="sxs-lookup"><span data-stu-id="67b37-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="67b37-113">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="67b37-113">Example</span></span>

<span data-ttu-id="67b37-114">In dit voorbeeld wordt is de verkeerd gespelde cmdlet-naam fuzzy enkele suggesties overeenkomende van waarschijnlijk minste waarschijnlijk.</span><span class="sxs-lookup"><span data-stu-id="67b37-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="67b37-115">Impliciete externe communicatie via batchverwerking uitvoeren</span><span class="sxs-lookup"><span data-stu-id="67b37-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="67b37-116">Bij het gebruik van [impliciete externe communicatie](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in een pijplijn, behandelt PowerShell elke opdracht in de pijplijn onafhankelijk van elkaar.</span><span class="sxs-lookup"><span data-stu-id="67b37-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="67b37-117">Objecten herhaaldelijk worden geserialiseerd en `de-serialized` tussen de client en het externe systeem over de uitvoering van de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="67b37-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="67b37-118">Met deze functie analyseert PowerShell de pijplijn om te bepalen van de opdracht is veilig om te worden uitgevoerd als deze bestaat op het doelsysteem.</span><span class="sxs-lookup"><span data-stu-id="67b37-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="67b37-119">Indien waar, PowerShell, de hele pijplijn op afstand wordt uitgevoerd en alleen serialiseert en `de-serializes` de resultaten terug naar de client.</span><span class="sxs-lookup"><span data-stu-id="67b37-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="67b37-120">Een test op echte `Get-Process | Sort-Object` via localhost afneemt van 10-15 seconden naar 20-30 **milliseconden**.</span><span class="sxs-lookup"><span data-stu-id="67b37-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="67b37-121">De functie moet alleen worden ingeschakeld op de client.</span><span class="sxs-lookup"><span data-stu-id="67b37-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="67b37-122">Er zijn geen wijzigingen zijn vereist op de server.</span><span class="sxs-lookup"><span data-stu-id="67b37-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="67b37-123">Temp Drive</span><span class="sxs-lookup"><span data-stu-id="67b37-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="67b37-124">Als u PowerShell Core op verschillende besturingssystemen, zult u ontdekken dat de omgevingsvariabele voor het vinden van de tijdelijke map anders in Windows, macOS en Linux is!</span><span class="sxs-lookup"><span data-stu-id="67b37-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="67b37-125">Met deze functie krijgt u een [PSDrive][] met de naam `Temp:` die automatisch is toegewezen aan de tijdelijke map voor het besturingssysteem die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="67b37-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="67b37-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="67b37-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> `Get-Content` Temp:/hello.txt
Hello World!
```

<span data-ttu-id="67b37-127">Houd er rekening mee dat opdrachten in het oorspronkelijke bestand (zoals `ls` op Linux) zijn niet op de hoogte van PSDrives en ziet deze niet `Temp:` station.</span><span class="sxs-lookup"><span data-stu-id="67b37-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="67b37-128">Afkorting-uitbreiding</span><span class="sxs-lookup"><span data-stu-id="67b37-128">Abbreviation Expansion</span></span>

<span data-ttu-id="67b37-129">PowerShell-cmdlets worden verwacht beschrijvende woorden.</span><span class="sxs-lookup"><span data-stu-id="67b37-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="67b37-130">Dit resulteert in lange namen die moeilijker zijn te typen.</span><span class="sxs-lookup"><span data-stu-id="67b37-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="67b37-131">Deze functie kunt u alleen de hoofdletters van de cmdlet typt en tab-aanvulling gebruiken om een overeenkomst te vinden.</span><span class="sxs-lookup"><span data-stu-id="67b37-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="67b37-132">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="67b37-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="67b37-133">Als u druk op tab en de Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module zijn geïnstalleerd, wordt automatisch aanvullen voor:</span><span class="sxs-lookup"><span data-stu-id="67b37-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="67b37-134">Deze functie is bedoeld voor interactief.</span><span class="sxs-lookup"><span data-stu-id="67b37-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="67b37-135">Verkorte vorm van cmdlets kunnen niet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="67b37-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="67b37-136">Deze functie is geen vervanging voor aliassen.</span><span class="sxs-lookup"><span data-stu-id="67b37-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="67b37-137">Wijzigingen die fouten veroorzaken</span><span class="sxs-lookup"><span data-stu-id="67b37-137">Breaking Changes</span></span>

- <span data-ttu-id="67b37-138">Los `-NoEnumerate` gedrag in `Write-Output` moet consistent zijn met Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="67b37-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="67b37-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="67b37-139">(#9069)</span></span>
- <span data-ttu-id="67b37-140">Controleer `Join-String -InputObject 1,2,3` resultaat gelijk is aan `1,2,3 | Join-String` leiden tot (#8611) (Bedankt @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="67b37-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="67b37-141">Toevoegen `-Stable` naar `Sort-Object` en gerelateerde tests (#7862) (Bedankt @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="67b37-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="67b37-142">Verbeteren `Start-Sleep` cmdlet precisiewaarde accepteren (#8537) (Bedankt @Prototyyppi!)</span><span class="sxs-lookup"><span data-stu-id="67b37-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="67b37-143">Wijzigen van de hashtabel OrdinalIgnoreCase gebruiken om u te worden `case-insensitive` in alle culturen (#8566)</span><span class="sxs-lookup"><span data-stu-id="67b37-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="67b37-144">Los **LiteralPath** in `Import-Csv` binden aan `Get-ChildItem` uitvoer (#8277) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-145">Een kolom zonder naam niet meer wordt overgeslagen als dubbel aanhalingsteken scheidingsteken wordt gebruikt in `Import-Csv` (#7899) (Bedankt @Topping!)</span><span class="sxs-lookup"><span data-stu-id="67b37-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="67b37-146">`Get-ExperimentalFeature` heeft niet langer `-ListAvailable` overschakelen (#8318)</span><span class="sxs-lookup"><span data-stu-id="67b37-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="67b37-147">Fouten opsporen in nu parametersets `$DebugPreference` naar **doorgaan** in plaats van **opvragen** (#8195) (Bedankt @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="67b37-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="67b37-148">Honor `-OutputFormat` als opgegeven in niet-interactieve, omgeleide, gecodeerde opdracht die wordt gebruikt met pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="67b37-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="67b37-149">Laden van assembly uit module basispad voordat u probeert te laden vanuit de GAC (#8073)</span><span class="sxs-lookup"><span data-stu-id="67b37-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="67b37-150">Tilde verwijderen uit Linux preview-pakketten (#8244)</span><span class="sxs-lookup"><span data-stu-id="67b37-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="67b37-151">Verplaats verwerkingstaken van `-WorkingDirectory` voorafgaand aan de verwerking van profielen (#8079)</span><span class="sxs-lookup"><span data-stu-id="67b37-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="67b37-152">Voeg geen `PATHEXT` omgevingsvariabele op Unix (#7697) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="67b37-153">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="67b37-153">Known Issues</span></span>

- <span data-ttu-id="67b37-154">Op ARM voor Windows-IOT-platformen voor externe toegang is een probleem dat het laden van modules.</span><span class="sxs-lookup"><span data-stu-id="67b37-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="67b37-155">Zie (#8053)</span><span class="sxs-lookup"><span data-stu-id="67b37-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="67b37-156">Algemene Updates en oplossingen</span><span class="sxs-lookup"><span data-stu-id="67b37-156">General Updates and Fixes</span></span>

- <span data-ttu-id="67b37-157">Niet-hoofdlettergevoelige tab-aanvulling voor bestanden en mappen op hoofdlettergevoelig bestandssysteem inschakelen (#8128)</span><span class="sxs-lookup"><span data-stu-id="67b37-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="67b37-158">PSVersionInfo.PSVersion en PSVersionInfo.PSEdition openbaar maken (#8054) (Bedankt @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="67b37-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="67b37-159">Toevoegen van Type Deductie voor `$_`  /  `$PSItem` in `catch{ }` (#8020) blokkeert (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="67b37-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="67b37-160">Statische methode aanroepen type Deductie oplossen (#8018) (Bedankt @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="67b37-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="67b37-161">Maken van afgeleide typen voor `Select-Object`, `Group-Object`, **PSObject** en **hashtabel** (#7231) (Bedankt @powercode!)</span><span class="sxs-lookup"><span data-stu-id="67b37-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="67b37-162">Ondersteuning voor de aanroepende methode met `ByRef-like` Typ parameters (#7721)</span><span class="sxs-lookup"><span data-stu-id="67b37-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="67b37-163">Wanneer het pad van Windows PowerShell-module is al in de omgeving PSModulePath verwerken (#7727)</span><span class="sxs-lookup"><span data-stu-id="67b37-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="67b37-164">Schakel `SecureString` -cmdlets voor Windows door op te slaan van de tekst zonder opmaak (#9199)</span><span class="sxs-lookup"><span data-stu-id="67b37-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="67b37-165">Foutbericht bij niet-Windows verbeteren bij het importeren van clixml met securestring (#7997)</span><span class="sxs-lookup"><span data-stu-id="67b37-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="67b37-166">Parameter ReplyTo toe te voegen aan `Send-MailMessage` (#8727) (Bedankt @replicaJunction!)</span><span class="sxs-lookup"><span data-stu-id="67b37-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="67b37-167">Verouderd bericht toevoegen `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="67b37-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="67b37-168">Los `Restart-Computer` om te werken op `localhost` wanneer WinRM is niet aanwezig (#9160)</span><span class="sxs-lookup"><span data-stu-id="67b37-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="67b37-169">Controleer `Start-Job` throw afsluitfout wanneer PowerShell wordt gehost (#9128)</span><span class="sxs-lookup"><span data-stu-id="67b37-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="67b37-170">Voeg C# style type accelerators en achtervoegsels voor ushort, uint, ulong en korte letterlijke waarden (#7813) (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="67b37-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="67b37-171">Toegevoegde nieuwe achtervoegsels voor numerieke letterlijke waarden - Zie [about_Numeric_Literals][] (#7901) (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="67b37-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="67b37-172">Niveau van impact correct rapporteren wanneer SupportsShouldProcess niet is ingesteld op 'true' (#8209) (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="67b37-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="67b37-173">Aanvraag tekenset problemen oplossen in Web-Cmdlets (#8742) (Bedankt @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="67b37-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="67b37-174">Los Expect `100-continue` probleem met Web-Cmdlets (#8679) (Bedankt @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="67b37-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="67b37-175">Bestand blokkerend probleem herstellen met de web-cmdlets (#7676) (Bedankt @Claustn!)</span><span class="sxs-lookup"><span data-stu-id="67b37-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="67b37-176">Codepagina bij het parseren van het probleem in herstellen `Invoke-RestMethod` (#8694) (Bedankt @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="67b37-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="67b37-177">Herstructureren `ConvertTo-Json` blootstellen JsonObject.ConvertToJson als een openbare API (#8682)</span><span class="sxs-lookup"><span data-stu-id="67b37-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="67b37-178">Configureerbare maximale diepte in toe te voegen `ConvertFrom-Json` met - diepte (#8199) (Bedankt @louistio!)</span><span class="sxs-lookup"><span data-stu-id="67b37-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="67b37-179">Toevoegen van de parameter EscapeHandling in `ConvertTo-Json` cmdlet (#7775) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-180">Voeg `-CustomPipeName` naar pwsh en `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="67b37-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="67b37-181">Inschakelen op Windows met het maken van relatieve symbolische koppelingen `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="67b37-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="67b37-182">Toestaan dat gebruikers van Windows in de modus voor ontwikkelaars symlinks zonder misbruik te maken (#8534)</span><span class="sxs-lookup"><span data-stu-id="67b37-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="67b37-183">Schakel `Write-Information` accepteren `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="67b37-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="67b37-184">Los `Get-Help` voor geavanceerde functies met MAML help-inhoud (#8353)</span><span class="sxs-lookup"><span data-stu-id="67b37-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="67b37-185">Los `Get-Help` PSTypeName probleem met de - Parameter wanneer slechts één parameter wordt gedefinieerd (#8754) (Bedankt @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="67b37-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="67b37-186">Token berekening correctie voor `Get-Help` uitgevoerd op ScriptBlock voor meer informatie over opmerking.</span><span class="sxs-lookup"><span data-stu-id="67b37-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="67b37-187">(#8238) (Bedankt @hubuk!)</span><span class="sxs-lookup"><span data-stu-id="67b37-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="67b37-188">Wijziging `Get-Help` cmdlet-Parameter parameter, zodat deze tekenreeks accepteert matrices (#8454) (Bedankt @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="67b37-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="67b37-189">Los PAGER als het pad bevat spaties (#8571) (Bedankt @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="67b37-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="67b37-190">Vragen toevoegen aan het gebruik van `less` in de functie 'help' voor de registratie door de gebruikers (#7998) afsluiten</span><span class="sxs-lookup"><span data-stu-id="67b37-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="67b37-191">Toevoegen van ondersteuning voor enum en char typen in `Format-Hex` cmdlet (#8191) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-192">Verwijderen van shouldprocess wordt overgeslagen van `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="67b37-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="67b37-193">Toevoegen van nieuwe Offset en aantal parameters voor `Format-Hex` en herstructureren van de cmdlet (#7877) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-194">Toestaan dat 'name' als een alias-sleutel voor 'label' in `ConvertTo-Html`, toestaan dat de vermelding 'breedte' moet een geheel getal (#8426) (Bedankt @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="67b37-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="67b37-195">Controleer scriptblock op basis van berekende eigenschappen weer werkt `ConvertTo-Html` (#8427) (Bedankt @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="67b37-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="67b37-196">Cmdlet toegevoegd `Join-String` voor het maken van de tekst van de pijplijn (#7660) invoeren (Bedankt @powercode!)</span><span class="sxs-lookup"><span data-stu-id="67b37-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="67b37-197">Los `Join-String` cmdlet FormatString parameter logica (#8449) (Bedankt @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="67b37-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="67b37-198">Wijziging `Clear-Host` terug op het gebruik `$RAWUI` en wissen om te werken via externe toegang (#8609)</span><span class="sxs-lookup"><span data-stu-id="67b37-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="67b37-199">Wijziging `Clear-Host` gewoon aangeroepen `[console]::clear` en duidelijke alias verwijderen van Unix (#8603)</span><span class="sxs-lookup"><span data-stu-id="67b37-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="67b37-200">Los LiteralPath in `Import-Csv` binden aan `Get-ChildItem` uitvoer (#8277) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-201">Help-functie pager voor AliasHelpInfo al dan niet mogen gebruiken (#8552)</span><span class="sxs-lookup"><span data-stu-id="67b37-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="67b37-202">Toevoegen `-UseMinimalHeader` naar `Start-Transcript` transcript header minimaliseren (#8402) (Bedankt @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="67b37-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="67b37-203">Voeg `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature` cmdlets (#8318)</span><span class="sxs-lookup"><span data-stu-id="67b37-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="67b37-204">Alle cmdlets van blootstellen **PSDiagnostics** als logman.exe beschikbaar (#8366)</span><span class="sxs-lookup"><span data-stu-id="67b37-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="67b37-205">Verwijder **Persist** parameter van `New-PSDrive` op `non-Windows` platform (#8291) (Bedankt @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="67b37-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="67b37-206">Voeg ondersteuning toe voor `cd +` (#7206) (Bedankt @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="67b37-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="67b37-207">Schakel `Set-Location -LiteralPath` om te werken met mappen met de naam - en + (#8089)</span><span class="sxs-lookup"><span data-stu-id="67b37-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="67b37-208">`Test-Path` retourneert `$false` bij een lege of `$null` pad waarde (#8080) (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="67b37-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="67b37-209">Dynamische parameter moet worden geretourneerd, zelfs als het pad komt niet overeen met alle elke provider toestaan (#7957)</span><span class="sxs-lookup"><span data-stu-id="67b37-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="67b37-210">Ondersteuning voor `Get-PSHostProcessInfo` en `Enter-PSHostProcess` op Unix-platforms (#8232)</span><span class="sxs-lookup"><span data-stu-id="67b37-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="67b37-211">Toewijzingen in verminderen `Get-Content` cmdlet (#8103) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-212">Schakel `Add-Content` leestoegang delen met andere hulpprogramma's tijdens het schrijven van inhoud (#8091)</span><span class="sxs-lookup"><span data-stu-id="67b37-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="67b37-213">`Get/Add-Content` Verbeterde fout genereert wanneer die gericht is op een container (#7823) (Bedankt @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="67b37-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="67b37-214">Voeg `-Name`, `-NoUserOverrides` en `-ListAvailable` parameters `Get-Culture` cmdlet (#7702) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-215">Geïntegreerde kenmerk voor de voltooiing voor toevoegen **Encoding** parameter.</span><span class="sxs-lookup"><span data-stu-id="67b37-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="67b37-216">(#7732) (Bedankt @ThreeFive-O!)</span><span class="sxs-lookup"><span data-stu-id="67b37-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="67b37-217">Toestaan dat de numerieke id's en de naam van de geregistreerde codetabellen in **Encoding** parameters (#7636) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="67b37-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="67b37-218">Los `Rename-Item -Path` met jokertekens char (#7398) (Bedankt @kwkam!)</span><span class="sxs-lookup"><span data-stu-id="67b37-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="67b37-219">Bij het gebruik van `Start-Transcript` en bestand aanwezig is, leeg bestand in plaats daarvan zijn dan (#8131) verwijderen (Bedankt @paalbra!)</span><span class="sxs-lookup"><span data-stu-id="67b37-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="67b37-220">Controleer `Add-Type` open source-bestanden met **FileAccess.Read** en **FileShare.Read** expliciet (#7915) (Bedankt @IISResetMe!)</span><span class="sxs-lookup"><span data-stu-id="67b37-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="67b37-221">Los `Enter-PSSession -ContainerId` voor de meest recente Windows (#7883)</span><span class="sxs-lookup"><span data-stu-id="67b37-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="67b37-222">Zorg ervoor dat **NestedModules** eigenschap wordt gevuld door `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="67b37-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="67b37-223">Voeg `%F` case te `Get-Date` - UFormat (#7630) (Bedankt @britishben!)</span><span class="sxs-lookup"><span data-stu-id="67b37-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="67b37-224">Los `Set-Service -Status Stopped` met afhankelijkheden-services stoppen (#5525) (Bedankt @zhenggu!)</span><span class="sxs-lookup"><span data-stu-id="67b37-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
