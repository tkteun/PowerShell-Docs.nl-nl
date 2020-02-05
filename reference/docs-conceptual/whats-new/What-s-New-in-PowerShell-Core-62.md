---
title: Wat is er nieuw in Power shell Core 6,2
description: Nieuwe functies en wijzigingen die zijn uitgebracht in Power shell Core 6,2
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995484"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="11544-103">Wat is er nieuw in Power shell Core 6,2</span><span class="sxs-lookup"><span data-stu-id="11544-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="11544-104">De Power shell Core 6,2-release is gericht op verbeteringen in prestaties, fout oplossingen en kleinere cmdlet-en taal uitbreidingen waarmee de kwaliteit wordt verbeterd.</span><span class="sxs-lookup"><span data-stu-id="11544-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="11544-105">Bekijk onze gedetailleerde [changelogs](https://github.com/PowerShell/PowerShell/releases) op github voor een volledige lijst met verbeteringen.</span><span class="sxs-lookup"><span data-stu-id="11544-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="11544-106">Experimentele functies</span><span class="sxs-lookup"><span data-stu-id="11544-106">Experimental Features</span></span>

<span data-ttu-id="11544-107">Voorheen hebben we ondersteuning voor [experimentele functies][]ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="11544-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="11544-108">In de 6,2-release hebben we vier experimentele functies nodig om uit te proberen. Geef feedback zodat we verbeteringen kunnen aanbrengen en bepalen of de functie van belang is voor de status van de standaard.</span><span class="sxs-lookup"><span data-stu-id="11544-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="11544-109">Gebruik `Get-ExperimentalFeature` om een lijst met beschik bare experimentele functies op te halen.</span><span class="sxs-lookup"><span data-stu-id="11544-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="11544-110">U kunt deze functies in-of uitschakelen met `Enable-ExperimentalFeature` en `Disable-ExperimentalFeature`.</span><span class="sxs-lookup"><span data-stu-id="11544-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="11544-111">Suggesties van opdracht niet gevonden</span><span class="sxs-lookup"><span data-stu-id="11544-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="11544-112">Deze functie maakt gebruik van fuzzy match om suggesties te vinden voor opdrachten of cmdlets die u mogelijk hebt getypt.</span><span class="sxs-lookup"><span data-stu-id="11544-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="11544-113">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="11544-113">Example</span></span>

<span data-ttu-id="11544-114">In dit voor beeld is de onjuist gespelde naam van de cmdlet gelijk aan een aantal suggesties van de meest waarschijnlijke waarschijnlijke kans.</span><span class="sxs-lookup"><span data-stu-id="11544-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

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

### <a name="implicit-remoting-batching"></a><span data-ttu-id="11544-115">Impliciete externe batch verwerking</span><span class="sxs-lookup"><span data-stu-id="11544-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="11544-116">Wanneer u [impliciete externe toegang](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in een pijp lijn gebruikt, behandelt Power shell elke opdracht onafhankelijk van elkaar in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="11544-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="11544-117">Objecten worden herhaaldelijk geserialiseerd en `de-serialized` tussen de client en het externe systeem over de uitvoering van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="11544-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="11544-118">Met deze functie analyseert Power shell de pijp lijn om te bepalen of de opdracht veilig kan worden uitgevoerd en op het doel systeem.</span><span class="sxs-lookup"><span data-stu-id="11544-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="11544-119">Als deze eigenschap waar is, wordt de volledige pijp lijn op afstand uitgevoerd en worden alleen de resultaten van de client `de-serializes`.</span><span class="sxs-lookup"><span data-stu-id="11544-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="11544-120">Een praktijk test van `Get-Process | Sort-Object` over localhost neemt af van 10-15 seconden tot 20-30 **milliseconden**.</span><span class="sxs-lookup"><span data-stu-id="11544-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="11544-121">De functie moet alleen worden ingeschakeld op de client.</span><span class="sxs-lookup"><span data-stu-id="11544-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="11544-122">Er zijn geen wijzigingen vereist op de server.</span><span class="sxs-lookup"><span data-stu-id="11544-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="11544-123">Tijdelijk station</span><span class="sxs-lookup"><span data-stu-id="11544-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="11544-124">Als u Power shell Core gebruikt op verschillende besturings systemen, detecteert u dat de omgevings variabele voor het vinden van de tijdelijke map anders is in Windows, macOS en Linux.</span><span class="sxs-lookup"><span data-stu-id="11544-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="11544-125">Met deze functie krijgt u een [PSDrive][] met de naam `Temp:` die automatisch wordt toegewezen aan de tijdelijke map voor het besturings systeem dat u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11544-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="11544-126">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="11544-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

<span data-ttu-id="11544-127">Houd er rekening mee dat systeem eigen bestands opdrachten (zoals `ls` op Linux) niet op de hoogte zijn van PSDrives en dit `Temp:` station niet te zien.</span><span class="sxs-lookup"><span data-stu-id="11544-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="11544-128">Afkorting uitbreiden</span><span class="sxs-lookup"><span data-stu-id="11544-128">Abbreviation Expansion</span></span>

<span data-ttu-id="11544-129">Voor Power shell-cmdlets wordt verwacht dat ze beschrijvende naam woorden bevatten.</span><span class="sxs-lookup"><span data-stu-id="11544-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="11544-130">Dit resulteert in lange namen die moeilijker te typen zijn.</span><span class="sxs-lookup"><span data-stu-id="11544-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="11544-131">Met deze functie kunt u alleen de hoofd letters van de cmdlet typen en de opdracht volt ooien gebruiken om een overeenkomst te vinden.</span><span class="sxs-lookup"><span data-stu-id="11544-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="11544-132">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="11544-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="11544-133">Als u op TAB drukt en de Azure PowerShell [AZ](https://www.powershellgallery.com/packages/Az) -module hebt geïnstalleerd, wordt deze automatisch aangevuld met:</span><span class="sxs-lookup"><span data-stu-id="11544-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="11544-134">Deze functie is bedoeld om interactief te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="11544-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="11544-135">Verkorte vormen van cmdlets kunnen niet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="11544-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="11544-136">Deze functie is geen vervanging voor aliassen.</span><span class="sxs-lookup"><span data-stu-id="11544-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="11544-137">Wijzigingen die fouten veroorzaken</span><span class="sxs-lookup"><span data-stu-id="11544-137">Breaking Changes</span></span>

- <span data-ttu-id="11544-138">Herstel `-NoEnumerate` gedrag in `Write-Output` consistent te zijn met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="11544-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="11544-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="11544-139">(#9069)</span></span>
- <span data-ttu-id="11544-140">`Join-String -InputObject 1,2,3` resultaat gelijk maken aan `1,2,3 | Join-String` resultaat (#8611) (Bedankt @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="11544-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="11544-141">`-Stable` toevoegen aan `Sort-Object` en gerelateerde tests (#7862) (Bedankt @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="11544-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="11544-142">`Start-Sleep`-cmdlet verbeteren om breuk seconden (#8537) te accepteren (Bedankt @Prototyyppi!)</span><span class="sxs-lookup"><span data-stu-id="11544-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="11544-143">Wijzig de hashtabel zodanig dat OrdinalIgnoreCase wordt gebruikt voor de `case-insensitive` in alle cult uren (#8566)</span><span class="sxs-lookup"><span data-stu-id="11544-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="11544-144">Herstel **LiteralPath** in `Import-Csv` om verbinding te maken met `Get-ChildItem`-uitvoer (#8277) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-145">Slaat geen kolom zonder naam over als dubbele aanhalings tekens worden gebruikt in `Import-Csv` (#7899) (Bedankt @Topping!)</span><span class="sxs-lookup"><span data-stu-id="11544-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="11544-146">`Get-ExperimentalFeature` heeft niet langer `-ListAvailable` switch (#8318)</span><span class="sxs-lookup"><span data-stu-id="11544-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="11544-147">Met de para meter debug wordt nu `$DebugPreference` ingesteld om **door te gaan** in plaats van op te **vragen** (#8195) (Bedankt @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="11544-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="11544-148">Respect `-OutputFormat` indien opgegeven in niet-interactieve, omgeleide, gecodeerde opdracht die wordt gebruikt met pwsh (#8115)</span><span class="sxs-lookup"><span data-stu-id="11544-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="11544-149">Assembly laden vanuit module base-pad voordat u probeert te laden vanuit de GAC (#8073)</span><span class="sxs-lookup"><span data-stu-id="11544-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="11544-150">Tilde uit Linux preview packages verwijderen (#8244)</span><span class="sxs-lookup"><span data-stu-id="11544-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="11544-151">Verwerking van `-WorkingDirectory` vóór het verwerken van profielen verplaatsen (#8079)</span><span class="sxs-lookup"><span data-stu-id="11544-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="11544-152">Voeg `PATHEXT` omgevings variabele niet toe op UNIX (#7697) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="11544-153">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="11544-153">Known Issues</span></span>

- <span data-ttu-id="11544-154">Externe toegang op Windows IOT ARM-platforms heeft een probleem met het laden van modules.</span><span class="sxs-lookup"><span data-stu-id="11544-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="11544-155">Zie (#8053)</span><span class="sxs-lookup"><span data-stu-id="11544-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="11544-156">Algemene updates en oplossingen</span><span class="sxs-lookup"><span data-stu-id="11544-156">General Updates and Fixes</span></span>

- <span data-ttu-id="11544-157">Niet-hoofdletter gevoelige tabblad voltooiing inschakelen voor bestanden en mappen op hoofdletter gevoelig bestands systeem (#8128)</span><span class="sxs-lookup"><span data-stu-id="11544-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="11544-158">Maak PSVersionInfo. PSVersion en PSVersionInfo. PSEdition openbaar (#8054) (Bedankt @KirkMunro!)</span><span class="sxs-lookup"><span data-stu-id="11544-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="11544-159">Type demijner voor `$_` / `$PSItem` in `catch{ }` blokken (#8020) toevoegen (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="11544-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="11544-160">Een statische methode voor het aanroepen van het aanroep type herstellen (#8018) (Bedankt @SeeminglyScience!)</span><span class="sxs-lookup"><span data-stu-id="11544-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="11544-161">Maak een afgeleid type voor `Select-Object`, `Group-Object`, **PSObject** en **hashtabel** (#7231) (Bedankt @powercode!)</span><span class="sxs-lookup"><span data-stu-id="11544-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="11544-162">Ondersteuning voor het aanroepen van methoden met `ByRef-like` type para meters (#7721)</span><span class="sxs-lookup"><span data-stu-id="11544-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="11544-163">De aanvraag afhandelen waarbij het pad naar de Windows Power shell-module al aanwezig is in de PSModulePath van de omgeving (#7727)</span><span class="sxs-lookup"><span data-stu-id="11544-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="11544-164">`SecureString`-cmdlets voor niet-Windows inschakelen door het onbewerkte tekst (#9199) op te slaan</span><span class="sxs-lookup"><span data-stu-id="11544-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="11544-165">Fout bericht op niet-Windows verbeteren bij het importeren van clixml met securestring (#7997)</span><span class="sxs-lookup"><span data-stu-id="11544-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="11544-166">Para meter ReplyTo toevoegen aan `Send-MailMessage` (#8727) (Bedankt @replicaJunction!)</span><span class="sxs-lookup"><span data-stu-id="11544-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="11544-167">Verouderd bericht toevoegen aan `Send-MailMessage` (#9178)</span><span class="sxs-lookup"><span data-stu-id="11544-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="11544-168">`Restart-Computer` oplossen om te werken aan `localhost` wanneer WinRM niet aanwezig is (#9160)</span><span class="sxs-lookup"><span data-stu-id="11544-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="11544-169">Fout bij het beëindigen van `Start-Job` genereren wanneer Power shell wordt gehost (#9128)</span><span class="sxs-lookup"><span data-stu-id="11544-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="11544-170">Stijl C# typen accelerators en achtervoegsels voor USHORT, uint, ULONG en short letterlijke tekens (#7813) toevoegen (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="11544-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="11544-171">Nieuwe achtervoegsels toegevoegd voor numerieke letterlijke waarden-Zie [about_Numeric_Literals][] (#7901) (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="11544-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="11544-172">Het niveau van de impact op de juiste manier rapporteren wanneer SupportsShouldProcess niet is ingesteld op True (#8209) (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="11544-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="11544-173">Problemen met de aanvraag-charset oplossen in Web-cmdlets (#8742) (Bedankt @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="11544-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="11544-174">Voor de oplossing wordt een probleem `100-continue` met Web-cmdlets (#8679) (Bedankt @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="11544-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="11544-175">Problemen met het blok keren van bestanden met Web-cmdlets (#7676) oplossen (Bedankt @Claustn!)</span><span class="sxs-lookup"><span data-stu-id="11544-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="11544-176">Het parseren van de code pagina in `Invoke-RestMethod` (#8694) oplossen (Bedankt @markekraus!)</span><span class="sxs-lookup"><span data-stu-id="11544-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="11544-177">Refactory `ConvertTo-Json` om JsonObject. ConvertToJson beschikbaar te maken als een open bare API (#8682)</span><span class="sxs-lookup"><span data-stu-id="11544-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="11544-178">Configureer bare maximale diepte toevoegen in `ConvertFrom-Json` met-Depth (#8199) (Bedankt @louistio!)</span><span class="sxs-lookup"><span data-stu-id="11544-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="11544-179">De para meter EscapeHandling toevoegen in `ConvertTo-Json`-cmdlet (#7775) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-180">`-CustomPipeName` toevoegen aan pwsh en `Enter-PSHostProcess` (#8889)</span><span class="sxs-lookup"><span data-stu-id="11544-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="11544-181">Het maken van relatieve symbolische koppelingen in Windows inschakelen met `New-Item` (#8783)</span><span class="sxs-lookup"><span data-stu-id="11544-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="11544-182">Toestaan dat Windows-gebruikers in de ontwikkelaars modus symlinks maken zonder uitbrei ding (#8534)</span><span class="sxs-lookup"><span data-stu-id="11544-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="11544-183">`Write-Information` accepteren `$null` (#8774)</span><span class="sxs-lookup"><span data-stu-id="11544-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="11544-184">`Get-Help` herstellen voor geavanceerde functies met MAML Help-inhoud (#8353)</span><span class="sxs-lookup"><span data-stu-id="11544-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="11544-185">Herstel `Get-Help` PSTypeName-probleem met-para meter wanneer er slechts één para meter is gedeclareerd (#8754) (hartelijk dank @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="11544-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="11544-186">Correctie van token berekening voor `Get-Help` uitgevoerd op script Block voor opmerkings hulp.</span><span class="sxs-lookup"><span data-stu-id="11544-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="11544-187">(#8238) (Bedankt @hubuk!)</span><span class="sxs-lookup"><span data-stu-id="11544-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="11544-188">Wijzig `Get-Help` cmdlet para meter parameter zodat deze teken reeks matrices (#8454) accepteert (Bedankt @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="11544-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="11544-189">PAGINERING omzetten als het pad spaties bevat (#8571) (Bedankt @pougetat!)</span><span class="sxs-lookup"><span data-stu-id="11544-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="11544-190">Voeg een prompt toe voor het gebruik van `less` in de functie Help om gebruikers te instrueren hoe ze moeten worden afgesloten (#7998)</span><span class="sxs-lookup"><span data-stu-id="11544-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="11544-191">Voeg ondersteuning toe voor Enum en char-typen in `Format-Hex`-cmdlet (#8191) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-192">ShouldProcess verwijderen uit `Format-Hex` (#8178)</span><span class="sxs-lookup"><span data-stu-id="11544-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="11544-193">Voeg nieuwe para meters voor offset en aantal toe aan `Format-Hex` en refactorion de cmdlet (#7877) (hartelijk dank @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-194">' Name ' toestaan als een alias sleutel voor ' label ' in `ConvertTo-Html`, de vermelding ' width ' toestaan als geheel getal (#8426) (Bedankt @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="11544-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="11544-195">Zorg dat berekende eigenschappen op basis van script Block opnieuw werken in `ConvertTo-Html` (#8427) (Bedankt @mklement0!)</span><span class="sxs-lookup"><span data-stu-id="11544-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="11544-196">`Join-String` cmdlet toevoegen voor het maken van tekst van pijplijn invoer (#7660) (Bedankt @powercode!)</span><span class="sxs-lookup"><span data-stu-id="11544-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="11544-197">`Join-String`-cmdlets parameter Logic (#8449) herstellen (Bedankt @sethvs!)</span><span class="sxs-lookup"><span data-stu-id="11544-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="11544-198">`Clear-Host` opnieuw instellen op het gebruik van `$RAWUI` en wissen om te werken via externe toegang (#8609)</span><span class="sxs-lookup"><span data-stu-id="11544-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="11544-199">Wijzig `Clear-Host` in simpelweg de naam `[console]::clear` en verwijder de duidelijke alias van UNIX (#8603)</span><span class="sxs-lookup"><span data-stu-id="11544-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="11544-200">Herstel LiteralPath in `Import-Csv` om verbinding te maken met `Get-ChildItem`-uitvoer (#8277) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-201">Help-functie mag paginering niet gebruiken voor AliasHelpInfo (#8552)</span><span class="sxs-lookup"><span data-stu-id="11544-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="11544-202">Voeg `-UseMinimalHeader` toe aan `Start-Transcript` om de transcript header (#8402) te minimaliseren (Bedankt @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="11544-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="11544-203">`Enable-ExperimentalFeature`-en `Disable-ExperimentalFeature`-cmdlets toevoegen (#8318)</span><span class="sxs-lookup"><span data-stu-id="11544-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="11544-204">Alle cmdlets weer geven vanuit **PSDiagnostics** als logman. exe beschikbaar is (#8366)</span><span class="sxs-lookup"><span data-stu-id="11544-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="11544-205">Verwijder de **persistente** para meter uit `New-PSDrive` op `non-Windows` platform (#8291) (Bedankt @lukexjeremy!)</span><span class="sxs-lookup"><span data-stu-id="11544-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="11544-206">Voeg ondersteuning toe voor `cd +` (#7206) (Bedankt @bergmeister!)</span><span class="sxs-lookup"><span data-stu-id="11544-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="11544-207">Schakel `Set-Location -LiteralPath` in om te werken met mappen met de naam-en + (#8089)</span><span class="sxs-lookup"><span data-stu-id="11544-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="11544-208">`Test-Path` retourneert `$false` wanneer het een lege waarde of een `$null` padwaarde (#8080) heeft gegeven (Bedankt @vexx32!)</span><span class="sxs-lookup"><span data-stu-id="11544-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="11544-209">De dynamische para meter mag worden geretourneerd, zelfs als het pad niet overeenkomt met een provider (#7957)</span><span class="sxs-lookup"><span data-stu-id="11544-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="11544-210">Ondersteuning voor `Get-PSHostProcessInfo` en `Enter-PSHostProcess` op UNIX-platforms (#8232)</span><span class="sxs-lookup"><span data-stu-id="11544-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="11544-211">Verlaag toewijzingen in `Get-Content`-cmdlet (#8103) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-212">Inschakelen dat `Add-Content` Lees toegang met andere hulpprogram ma's kunt delen tijdens het schrijven van inhoud (#8091)</span><span class="sxs-lookup"><span data-stu-id="11544-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="11544-213">`Get/Add-Content` genereert een verbeterde fout bij het richten op een container (#7823) (hartelijk dank @kvprasoon!)</span><span class="sxs-lookup"><span data-stu-id="11544-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="11544-214">`-Name`-, `-NoUserOverrides`-en `-ListAvailable`-para meters toevoegen aan `Get-Culture`-cmdlet (#7702) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-215">Voeg een uniform kenmerk toe voor het volt ooien van de **coderings** parameter.</span><span class="sxs-lookup"><span data-stu-id="11544-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="11544-216">(#7732) (Bedankt @ThreeFive-O!)</span><span class="sxs-lookup"><span data-stu-id="11544-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="11544-217">Numerieke Id's en de naam van geregistreerde code pagina's toestaan in **coderings** parameters (#7636) (Bedankt @iSazonov!)</span><span class="sxs-lookup"><span data-stu-id="11544-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="11544-218">Herstel `Rename-Item -Path` met Joker teken (#7398) (Bedankt @kwkam!)</span><span class="sxs-lookup"><span data-stu-id="11544-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="11544-219">Wanneer u `Start-Transcript` en het bestand exists gebruikt, is dit een leeg bestand in plaats van het verwijderen (#8131) (Bedankt @paalbra!)</span><span class="sxs-lookup"><span data-stu-id="11544-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="11544-220">`Add-Type` open source-bestanden maken met **FileAccess. Read** en **file share. expliciet lezen** (#7915) (Bedankt @IISResetMe!)</span><span class="sxs-lookup"><span data-stu-id="11544-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="11544-221">`Enter-PSSession -ContainerId` voor de nieuwste versie van Windows (#7883) herstellen</span><span class="sxs-lookup"><span data-stu-id="11544-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="11544-222">Zorg ervoor dat de eigenschap **NestedModules** wordt gevuld door `Test-ModuleManifest` (#7859)</span><span class="sxs-lookup"><span data-stu-id="11544-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="11544-223">Voeg `%F` Case toe aan `Get-Date`-UFormat (#7630) (Bedankt @britishben!)</span><span class="sxs-lookup"><span data-stu-id="11544-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="11544-224">Herstel `Set-Service -Status Stopped` om services te stoppen met afhankelijkheden (#5525) (Bedankt @zhenggu!)</span><span class="sxs-lookup"><span data-stu-id="11544-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[Experimentele functies]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
