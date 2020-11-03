---
description: In Windows Power shell wordt een Windows-gebeurtenis logboek gemaakt met de naam Windows Power shell om Windows Power shell-gebeurtenissen vast te leggen. U kunt dit logboek weer geven in Logboeken of met behulp van cmdlets die gebeurtenissen ophalen, zoals de `Get-EventLog` cmdlet. Standaard worden de gebeurtenissen van de Windows Power shell-engine en provider vastgelegd in het gebeurtenis logboek, maar u kunt de voorkeurs variabelen voor gebeurtenis Logboeken gebruiken om het gebeurtenis logboek aan te passen. U kunt bijvoorbeeld gebeurtenissen over Windows Power shell-opdrachten toevoegen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_eventlogs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Eventlogs
ms.openlocfilehash: eb92333c6a6e220e287dcbec1441d2d05aa9275b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252806"
---
# <a name="about-eventlogs"></a><span data-ttu-id="dc958-107">Over gebeurtenis logboeken</span><span class="sxs-lookup"><span data-stu-id="dc958-107">About Eventlogs</span></span>

## <a name="short-description"></a><span data-ttu-id="dc958-108">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc958-108">Short Description</span></span>

<span data-ttu-id="dc958-109">In Windows Power shell wordt een Windows-gebeurtenis logboek gemaakt met de naam Windows Power shell om Windows Power shell-gebeurtenissen vast te leggen.</span><span class="sxs-lookup"><span data-stu-id="dc958-109">Windows PowerShell creates a Windows event log that is named "Windows PowerShell" to record Windows PowerShell events.</span></span> <span data-ttu-id="dc958-110">U kunt dit logboek weer geven in Logboeken of met behulp van cmdlets die gebeurtenissen ophalen, zoals de `Get-EventLog` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc958-110">You can view this log in Event Viewer or by using cmdlets that get events, such as the `Get-EventLog` cmdlet.</span></span> <span data-ttu-id="dc958-111">Standaard worden de gebeurtenissen van de Windows Power shell-engine en provider vastgelegd in het gebeurtenis logboek, maar u kunt de voorkeurs variabelen voor gebeurtenis Logboeken gebruiken om het gebeurtenis logboek aan te passen.</span><span class="sxs-lookup"><span data-stu-id="dc958-111">By default, Windows PowerShell engine and provider events are recorded in the event log, but you can use the event log preference variables to customize the event log.</span></span> <span data-ttu-id="dc958-112">U kunt bijvoorbeeld gebeurtenissen over Windows Power shell-opdrachten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="dc958-112">For example, you can add events about Windows PowerShell commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="dc958-113">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc958-113">Long Description</span></span>

<span data-ttu-id="dc958-114">In het gebeurtenis logboek van Windows Power shell worden gegevens van Windows Power shell-bewerkingen vastgelegd, zoals het starten en stoppen van de programma-engine en het starten en stoppen van de Windows Power shell-providers.</span><span class="sxs-lookup"><span data-stu-id="dc958-114">The Windows PowerShell event log records details of Windows PowerShell operations, such as starting and stopping the program engine and starting and stopping the Windows PowerShell providers.</span></span> <span data-ttu-id="dc958-115">U kunt ook informatie over Windows Power shell-opdrachten vastleggen in een logboek.</span><span class="sxs-lookup"><span data-stu-id="dc958-115">You can also log details about Windows PowerShell commands.</span></span>

<span data-ttu-id="dc958-116">Het gebeurtenis logboek van Windows Power Shell bevindt zich in de groep toepassings-en service Logboeken.</span><span class="sxs-lookup"><span data-stu-id="dc958-116">The Windows PowerShell event log is in the Application and Services Logs group.</span></span> <span data-ttu-id="dc958-117">Het Windows Power shell-logboek is een klassiek gebeurtenis logboek dat geen gebruik maakt van de Windows eventing-technologie.</span><span class="sxs-lookup"><span data-stu-id="dc958-117">The Windows PowerShell log is a classic event log that does not use the Windows Eventing technology.</span></span> <span data-ttu-id="dc958-118">Als u het logboek wilt weer geven, gebruikt u de cmdlets die zijn ontworpen voor klassieke gebeurtenis logboeken, zoals `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="dc958-118">To view the log, use the cmdlets designed for classic event logs, such as `Get-EventLog`.</span></span>

## <a name="viewing-the-windows-powershell-event-log"></a><span data-ttu-id="dc958-119">Het gebeurtenis logboek van Windows Power shell weer geven</span><span class="sxs-lookup"><span data-stu-id="dc958-119">Viewing the Windows PowerShell Event Log</span></span>

<span data-ttu-id="dc958-120">U kunt het Windows Power shell-gebeurtenis logboek weer geven in Logboeken of met behulp van de- `Get-EventLog` en- `Get-WmiObject` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="dc958-120">You can view the Windows PowerShell event log in Event Viewer or by using the `Get-EventLog` and `Get-WmiObject` cmdlets.</span></span> <span data-ttu-id="dc958-121">Als u de inhoud van het Windows Power shell-logboek wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="dc958-121">To view the contents of the Windows PowerShell log, type:</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell"
```

<span data-ttu-id="dc958-122">Als u de gebeurtenissen en hun eigenschappen wilt bekijken, gebruikt u de `Sort-Object` cmdlet, de `Group-Object` cmdlet en de cmdlets die de `Format` opdracht (de `Format` cmdlets) bevatten.</span><span class="sxs-lookup"><span data-stu-id="dc958-122">To examine the events and their properties, use the `Sort-Object` cmdlet, the `Group-Object` cmdlet, and the cmdlets that contain the `Format` verb (the `Format` cmdlets).</span></span>

<span data-ttu-id="dc958-123">Als u bijvoorbeeld de gebeurtenissen in het logboek wilt weer geven, gegroepeerd op gebeurtenis-ID, typt u:</span><span class="sxs-lookup"><span data-stu-id="dc958-123">For example, to view the events in the log grouped by the event ID, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" | Format-Table -GroupBy EventID
```

<span data-ttu-id="dc958-124">Of typ:</span><span class="sxs-lookup"><span data-stu-id="dc958-124">Or, type:</span></span>

```powershell
Get-EventLog "Windows PowerShell" |
  Sort-Object EventID |
  Group-Object EventID
```

<span data-ttu-id="dc958-125">Als u alle klassieke gebeurtenis logboeken wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="dc958-125">To view all the classic event logs, type:</span></span>

```powershell
Get-EventLog -List
```

<span data-ttu-id="dc958-126">U kunt de cmdlet ook gebruiken `Get-WmiObject` om de WMI-klassen (gebeurtenis-gerelateerde Windows Management Instrumentation) te gebruiken om het gebeurtenis logboek te onderzoeken.</span><span class="sxs-lookup"><span data-stu-id="dc958-126">You can also use the `Get-WmiObject` cmdlet to use the event-related Windows Management Instrumentation (WMI) classes to examine the event log.</span></span> <span data-ttu-id="dc958-127">Als u bijvoorbeeld alle eigenschappen van het gebeurtenis logboek bestand wilt weer geven, typt u:</span><span class="sxs-lookup"><span data-stu-id="dc958-127">For example, to view all the properties of the event log file, type:</span></span>

```powershell
Get-WmiObject Win32_NTEventlogFile |
  where LogFileName -EQ "Windows PowerShell" |
  Format-List -Property *
```

<span data-ttu-id="dc958-128">Als u de WMI-klassen wilt vinden die aan Win32-gebeurtenissen zijn gerelateerd, typt u:</span><span class="sxs-lookup"><span data-stu-id="dc958-128">To find the Win32 event-related WMI classes, type:</span></span>

```powershell
Get-WmiObject -List | where Name -Like "win32*event*"
```

<span data-ttu-id="dc958-129">Typ "Get-Help Get-EventLog" en "Get-Help Get-WmiObject" voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc958-129">For more information, type "Get-Help Get-EventLog" and "Get-Help Get-WmiObject".</span></span>

## <a name="selecting-events-for-the-windows-powershell-event-log"></a><span data-ttu-id="dc958-130">Gebeurtenissen selecteren voor het gebeurtenis logboek van Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="dc958-130">Selecting Events for the Windows PowerShell Event Log</span></span>

<span data-ttu-id="dc958-131">U kunt de voorkeurs variabelen van gebeurtenis Logboeken gebruiken om te bepalen welke gebeurtenissen worden vastgelegd in het gebeurtenis logboek van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="dc958-131">You can use the event log preference variables to determine which events are recorded in the Windows PowerShell event log.</span></span>

<span data-ttu-id="dc958-132">Er zijn zes voorkeurs variabelen voor gebeurtenis Logboeken. twee variabelen voor elk van de drie logboek registratie-onderdelen: de engine (het Windows Power shell-programma), de providers en de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="dc958-132">There are six event log preference variables; two variables for each of the three logging components: the engine (the Windows PowerShell program), the providers, and the commands.</span></span> <span data-ttu-id="dc958-133">De LifeCycleEvent-variabelen registreren normaal starten en stoppen van gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="dc958-133">The LifeCycleEvent variables log normal starting and stopping events.</span></span> <span data-ttu-id="dc958-134">De status variabelen registreren fout gebeurtenissen.</span><span class="sxs-lookup"><span data-stu-id="dc958-134">The Health variables log error events.</span></span>

<span data-ttu-id="dc958-135">De volgende tabel bevat de voorkeurs variabelen van gebeurtenis Logboeken.</span><span class="sxs-lookup"><span data-stu-id="dc958-135">The following table lists the event log preference variables.</span></span>

|<span data-ttu-id="dc958-136">Variabele</span><span class="sxs-lookup"><span data-stu-id="dc958-136">Variable</span></span>                  |<span data-ttu-id="dc958-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="dc958-137">Description</span></span>                                    |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="dc958-138">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-138">$LogEngineLifeCycleEvent</span></span>  |<span data-ttu-id="dc958-139">Registreert het starten en stoppen van Power shell</span><span class="sxs-lookup"><span data-stu-id="dc958-139">Logs the start and stop of PowerShell</span></span>          |
|<span data-ttu-id="dc958-140">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-140">$LogEngineHealthEvent</span></span>     |<span data-ttu-id="dc958-141">Logboeken van Power shell-programma fouten</span><span class="sxs-lookup"><span data-stu-id="dc958-141">Logs PowerShell program errors</span></span>                 |
|<span data-ttu-id="dc958-142">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-142">$LogProviderLifeCycleEvent</span></span>|<span data-ttu-id="dc958-143">Registreert het starten en stoppen van Power shell-providers</span><span class="sxs-lookup"><span data-stu-id="dc958-143">Logs the start and stop of PowerShell providers</span></span>|
|<span data-ttu-id="dc958-144">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-144">$LogProviderHealthEvent</span></span>   |<span data-ttu-id="dc958-145">Logboeken van Power shell-provider fouten</span><span class="sxs-lookup"><span data-stu-id="dc958-145">Logs PowerShell provider errors</span></span>                |
|<span data-ttu-id="dc958-146">$LogCommandLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-146">$LogCommandLifeCycleEvent</span></span> |<span data-ttu-id="dc958-147">Hiermee wordt het starten en volt ooien van opdrachten geregistreerd</span><span class="sxs-lookup"><span data-stu-id="dc958-147">Logs the starting and completion of commands</span></span>   |
|<span data-ttu-id="dc958-148">$LogCommandHealthEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-148">$LogCommandHealthEvent</span></span>    |<span data-ttu-id="dc958-149">Registreert opdracht fouten</span><span class="sxs-lookup"><span data-stu-id="dc958-149">Logs command errors</span></span>                            |

<span data-ttu-id="dc958-150">(Zie [about_Providers](about_Providers.md)voor meer informatie over Windows Power shell-providers.)</span><span class="sxs-lookup"><span data-stu-id="dc958-150">(For information about Windows PowerShell providers, see [about_Providers](about_Providers.md).)</span></span>

<span data-ttu-id="dc958-151">Standaard worden alleen de volgende gebeurtenis typen ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="dc958-151">By default, only the following event types are enabled:</span></span>

* <span data-ttu-id="dc958-152">$LogEngineLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-152">$LogEngineLifeCycleEvent</span></span>
* <span data-ttu-id="dc958-153">$LogEngineHealthEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-153">$LogEngineHealthEvent</span></span>
* <span data-ttu-id="dc958-154">$LogProviderLifeCycleEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-154">$LogProviderLifeCycleEvent</span></span>
* <span data-ttu-id="dc958-155">$LogProviderHealthEvent</span><span class="sxs-lookup"><span data-stu-id="dc958-155">$LogProviderHealthEvent</span></span>

<span data-ttu-id="dc958-156">Als u een gebeurtenis type wilt inschakelen, stelt u de voorkeurs variabele voor dat gebeurtenis type in op $true.</span><span class="sxs-lookup"><span data-stu-id="dc958-156">To enable an event type, set the preference variable for that event type to $true.</span></span> <span data-ttu-id="dc958-157">Als u bijvoorbeeld gebeurtenissen voor levens cyclus van opdrachten wilt inschakelen, typt u:</span><span class="sxs-lookup"><span data-stu-id="dc958-157">For example, to enable command life-cycle events, type:</span></span>

```powershell
$LogCommandLifeCycleEvent
```

<span data-ttu-id="dc958-158">Of typ:</span><span class="sxs-lookup"><span data-stu-id="dc958-158">Or, type:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="dc958-159">Als u een gebeurtenis type wilt uitschakelen, stelt u de voorkeurs variabele voor dat gebeurtenis type in op $false.</span><span class="sxs-lookup"><span data-stu-id="dc958-159">To disable an event type, set the preference variable for that event type to $false.</span></span> <span data-ttu-id="dc958-160">Als u bijvoorbeeld de opdracht levens cyclus gebeurtenissen wilt uitschakelen, typt u:</span><span class="sxs-lookup"><span data-stu-id="dc958-160">For example, to disable command life-cycle events, type:</span></span>

```powershell
$LogProviderLifeCycleEvent = $false
```

<span data-ttu-id="dc958-161">U kunt elke gebeurtenis uitschakelen, met uitzonde ring van de gebeurtenissen die aangeven dat de Windows Power shell-engine en de kern providers worden gestart.</span><span class="sxs-lookup"><span data-stu-id="dc958-161">You can disable any event, except for the events that indicate that the Windows PowerShell engine and the core providers are started.</span></span> <span data-ttu-id="dc958-162">Deze gebeurtenissen worden gegenereerd voordat de Windows Power shell-profielen worden uitgevoerd en voordat het hostprogramma gereed is om opdrachten te accepteren.</span><span class="sxs-lookup"><span data-stu-id="dc958-162">These events are generated before the Windows PowerShell profiles are run and before the host program is ready to accept commands.</span></span>

<span data-ttu-id="dc958-163">De instellingen van de variabele zijn alleen van toepassing op de huidige Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="dc958-163">The variable settings apply only for the current Windows PowerShell session.</span></span>
<span data-ttu-id="dc958-164">Als u deze wilt Toep assen op alle Windows Power shell-sessies, voegt u deze toe aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="dc958-164">To apply them to all Windows PowerShell sessions, add them to your Windows PowerShell profile.</span></span>

## <a name="logging-module-events"></a><span data-ttu-id="dc958-165">Logboek registratie module gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="dc958-165">Logging Module Events</span></span>

<span data-ttu-id="dc958-166">Vanaf Windows Power Shell 3,0 kunt u uitvoerings gebeurtenissen vastleggen voor de cmdlets en functies in Windows Power shell-modules en-modules door de eigenschap LogPipelineExecutionDetails van modules en modules in te stellen op TRUE.</span><span class="sxs-lookup"><span data-stu-id="dc958-166">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets and functions in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="dc958-167">In Windows Power Shell 2,0 is deze functie alleen beschikbaar voor modules.</span><span class="sxs-lookup"><span data-stu-id="dc958-167">In Windows PowerShell 2.0, this feature is available only for snap-ins.</span></span>

<span data-ttu-id="dc958-168">Wanneer de waarde van de eigenschap LogPipelineExecutionDetails TRUE ( `$true` ) is, schrijft Windows Power shell cmdlet-en Function Execution-gebeurtenissen in de sessie naar de Windows Power shell-aanmeld Logboeken.</span><span class="sxs-lookup"><span data-stu-id="dc958-168">When the LogPipelineExecutionDetails property value is TRUE (`$true`), Windows PowerShell writes cmdlet and function execution events in the session to the Windows PowerShell log in Event Viewer.</span></span> <span data-ttu-id="dc958-169">De instelling is alleen effectief in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="dc958-169">The setting is effective only in the current session.</span></span>

<span data-ttu-id="dc958-170">Als u logboek registratie van uitvoerings gebeurtenissen van cmdlets en functies in een module wilt inschakelen, gebruikt u de volgende opdracht reeks.</span><span class="sxs-lookup"><span data-stu-id="dc958-170">To enable logging of execution events of cmdlets and functions in a module, use the following command sequence.</span></span>

```powershell
Import-Module <ModuleName>
$m = Get-Module <ModuleName>
$m.LogPipelineExecutionDetails = $true
```

<span data-ttu-id="dc958-171">Als u logboek registratie van uitvoerings gebeurtenissen van cmdlets in een module wilt inschakelen, gebruikt u de volgende opdracht reeks.</span><span class="sxs-lookup"><span data-stu-id="dc958-171">To enable logging of execution events of cmdlets in a snap-in, use the following command sequence.</span></span>

```powershell
$m = Get-PSSnapin <SnapInName> [-Registered]
$m.LogPipelineExecutionDetails = $True
```

<span data-ttu-id="dc958-172">Als u logboek registratie wilt uitschakelen, gebruikt u dezelfde opdracht reeks om de eigenschaps waarde in te stellen op FALSE ( `$false` ).</span><span class="sxs-lookup"><span data-stu-id="dc958-172">To disable logging, use the same command sequence to set the property value to FALSE (`$false`).</span></span>

<span data-ttu-id="dc958-173">U kunt ook de instelling ' module logboek registratie inschakelen ' groepsbeleid gebruiken om module-en module logboek registratie in te scha kelen en uit te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="dc958-173">You can also use the "Turn on Module Logging" Group Policy setting to enable and disable module and snap-in logging.</span></span> <span data-ttu-id="dc958-174">De beleids waarde bevat een lijst van module-en module namen.</span><span class="sxs-lookup"><span data-stu-id="dc958-174">The policy value includes a list of module and snap-in names.</span></span> <span data-ttu-id="dc958-175">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="dc958-175">Wildcards are supported.</span></span>

<span data-ttu-id="dc958-176">Wanneer het inschakelen van module logboek registratie is ingesteld voor een module, is de waarde van de eigenschap LogPipelineExecutionDetails van de module in alle sessies waar en kan niet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="dc958-176">When "Turn on Module Logging" is set for a module, the value of the LogPipelineExecutionDetails property of the module is TRUE in all sessions and it cannot be changed.</span></span>

<span data-ttu-id="dc958-177">De groeps beleids instelling voor het inschakelen van module logboek registratie bevindt zich in de volgende groepsbeleid paden:</span><span class="sxs-lookup"><span data-stu-id="dc958-177">The Turn On Module Logging group policy setting is located in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
     Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="dc958-178">Het gebruikers configuratie beleid heeft voor rang op het computer configuratie beleid en beide beleids regels hebben voor keur boven de waarde van de eigenschap LogPipelineExecutionDetails van modules en modules.</span><span class="sxs-lookup"><span data-stu-id="dc958-178">The User Configuration policy takes precedence over the Computer Configuration policy, and both policies take preference over the value of the LogPipelineExecutionDetails property of modules and snap-ins.</span></span>

<span data-ttu-id="dc958-179">Zie [about_Group_Policy_Settings](about_Group_Policy_Settings.md)voor meer informatie over deze Groepsbeleid instelling.</span><span class="sxs-lookup"><span data-stu-id="dc958-179">For more information about this Group Policy setting, see [about_Group_Policy_Settings](about_Group_Policy_Settings.md).</span></span>

## <a name="security-and-auditing"></a><span data-ttu-id="dc958-180">Beveiliging en controle</span><span class="sxs-lookup"><span data-stu-id="dc958-180">Security and Auditing</span></span>

<span data-ttu-id="dc958-181">Het gebeurtenis logboek van Windows Power shell is ontworpen om activiteiten aan te duiden en operationele details te bieden voor het oplossen van problemen.</span><span class="sxs-lookup"><span data-stu-id="dc958-181">The Windows PowerShell event log is designed to indicate activity and to provide operational details for troubleshooting.</span></span>

<span data-ttu-id="dc958-182">Net als de meeste Windows-logboeken voor toepassings gebeurtenissen is het Windows Power shell-gebeurtenis logboek echter niet ontworpen om beveiligd te zijn.</span><span class="sxs-lookup"><span data-stu-id="dc958-182">However, like most Windows-based application event logs, the Windows PowerShell event log is not designed to be secure.</span></span> <span data-ttu-id="dc958-183">Het mag niet worden gebruikt om de beveiliging te controleren of om vertrouwelijke of eigendoms gegevens vast te leggen.</span><span class="sxs-lookup"><span data-stu-id="dc958-183">It should not be used to audit security or to record confidential or proprietary information.</span></span>

<span data-ttu-id="dc958-184">Gebeurtenis logboeken zijn bedoeld om te worden gelezen en begrepen door gebruikers.</span><span class="sxs-lookup"><span data-stu-id="dc958-184">Event logs are designed to be read and understood by users.</span></span> <span data-ttu-id="dc958-185">Gebruikers kunnen lezen uit en schrijven naar het logboek.</span><span class="sxs-lookup"><span data-stu-id="dc958-185">Users can read from and write to the log.</span></span> <span data-ttu-id="dc958-186">Een kwaadwillende gebruiker kan een gebeurtenis logboek op een lokale of externe computer lezen, onwaare gegevens opnemen en vervolgens voor komen dat hun activiteiten worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="dc958-186">A malicious user could read an event log on a local or remote computer, record false data, and then prevent the logging of their activities.</span></span>

## <a name="notes"></a><span data-ttu-id="dc958-187">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="dc958-187">Notes</span></span>

<span data-ttu-id="dc958-188">Auteurs van module ontwerpers kunnen logboek functies toevoegen aan hun modules.</span><span class="sxs-lookup"><span data-stu-id="dc958-188">Authors of module authors can add logging features to their modules.</span></span> <span data-ttu-id="dc958-189">Zie [een Windows Power shell-module schrijven](/powershell/scripting/developer/module/writing-a-windows-powershell-module)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="dc958-189">For more information, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

## <a name="see-also"></a><span data-ttu-id="dc958-190">Zie ook</span><span class="sxs-lookup"><span data-stu-id="dc958-190">See Also</span></span>

[<span data-ttu-id="dc958-191">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="dc958-191">Get-EventLog</span></span>](xref:Microsoft.PowerShell.Management.Get-EventLog)

[<span data-ttu-id="dc958-192">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="dc958-192">Get-WmiObject</span></span>](xref:Microsoft.PowerShell.Management.Get-WmiObject)

[<span data-ttu-id="dc958-193">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="dc958-193">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="dc958-194">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="dc958-194">about_Preference_Variables</span></span>](about_Preference_Variables.md)
