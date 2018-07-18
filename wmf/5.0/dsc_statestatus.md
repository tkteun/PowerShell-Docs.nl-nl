---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: b279d388754c5ee42215f21317f7b3d8089b7608
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093878"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="211fe-102">Uniforme en consistente status en statusweergave</span><span class="sxs-lookup"><span data-stu-id="211fe-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="211fe-103">Een reeks verbeteringen zijn aangebracht in deze release voor automatische ingebouwd LCM-status en DSC-status.</span><span class="sxs-lookup"><span data-stu-id="211fe-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="211fe-104">Uniforme en consistente status en de status verklaringen, beheerbare datetime-eigenschap van de van statusobjecten die worden geretourneerd door het gaat hierbij `Get-DscConfigurationStatus` cmdlet en verbeterde LCM staat details van de eigenschap die wordt geretourneerd door `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="211fe-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="211fe-105">De weergave van LCM-status en de status van de DSC-bewerking worden herzien en geïntegreerde op basis van de volgende regels:</span><span class="sxs-lookup"><span data-stu-id="211fe-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="211fe-106">NotProcessed weer resource heeft geen invloed op LCM-status en DSC-status.</span><span class="sxs-lookup"><span data-stu-id="211fe-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
1. <span data-ttu-id="211fe-107">LCM stoppen verdere informatie verwerken zodra er een resource die opnieuw opstarten aanvragen wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="211fe-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
1. <span data-ttu-id="211fe-108">Een resource die opnieuw opstarten aanvragen is niet in de gewenste status totdat opnieuw opstarten daadwerkelijk gebeurt.</span><span class="sxs-lookup"><span data-stu-id="211fe-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
1. <span data-ttu-id="211fe-109">Na het vaststellen van een resource die is mislukt, houdt LCM verwerken van meer resources, zolang ze niet afhankelijk van de fout een zijn.</span><span class="sxs-lookup"><span data-stu-id="211fe-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
1. <span data-ttu-id="211fe-110">De algemene status geretourneerd door `Get-DscConfigurationStatus` cmdlet is de super set alle resources de status.</span><span class="sxs-lookup"><span data-stu-id="211fe-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
1. <span data-ttu-id="211fe-111">De status PendingReboot is een superset van PendingConfiguration staat.</span><span class="sxs-lookup"><span data-stu-id="211fe-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="211fe-112">De onderstaande tabel ziet u de resulterende status en de status eigenschappen met betrekking tot onder een aantal typische scenario's.</span><span class="sxs-lookup"><span data-stu-id="211fe-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="211fe-113">Scenario</span><span class="sxs-lookup"><span data-stu-id="211fe-113">Scenario</span></span>                    | <span data-ttu-id="211fe-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="211fe-114">LCMState</span></span>       | <span data-ttu-id="211fe-115">Status</span><span class="sxs-lookup"><span data-stu-id="211fe-115">Status</span></span> | <span data-ttu-id="211fe-116">Opnieuw opstarten aangevraagd</span><span class="sxs-lookup"><span data-stu-id="211fe-116">Reboot Requested</span></span>  | <span data-ttu-id="211fe-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="211fe-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="211fe-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="211fe-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="211fe-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="211fe-119">S**^**</span></span>                          | <span data-ttu-id="211fe-120">Actieve</span><span class="sxs-lookup"><span data-stu-id="211fe-120">Idle</span></span>                 | <span data-ttu-id="211fe-121">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="211fe-121">Success</span></span>    | <span data-ttu-id="211fe-122">$false</span><span class="sxs-lookup"><span data-stu-id="211fe-122">$false</span></span>        | <span data-ttu-id="211fe-123">S</span><span class="sxs-lookup"><span data-stu-id="211fe-123">S</span></span>                            | <span data-ttu-id="211fe-124">$null</span><span class="sxs-lookup"><span data-stu-id="211fe-124">$null</span></span>                          |
   | <span data-ttu-id="211fe-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="211fe-125">F**^**</span></span>                          | <span data-ttu-id="211fe-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="211fe-126">PendingConfiguration</span></span> | <span data-ttu-id="211fe-127">Mislukt</span><span class="sxs-lookup"><span data-stu-id="211fe-127">Failure</span></span>    | <span data-ttu-id="211fe-128">$false</span><span class="sxs-lookup"><span data-stu-id="211fe-128">$false</span></span>        | <span data-ttu-id="211fe-129">$null</span><span class="sxs-lookup"><span data-stu-id="211fe-129">$null</span></span>                        | <span data-ttu-id="211fe-130">F</span><span class="sxs-lookup"><span data-stu-id="211fe-130">F</span></span>                              |
   | <span data-ttu-id="211fe-131">S, F</span><span class="sxs-lookup"><span data-stu-id="211fe-131">S,F</span></span>                             | <span data-ttu-id="211fe-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="211fe-132">PendingConfiguration</span></span> | <span data-ttu-id="211fe-133">Mislukt</span><span class="sxs-lookup"><span data-stu-id="211fe-133">Failure</span></span>    | <span data-ttu-id="211fe-134">$false</span><span class="sxs-lookup"><span data-stu-id="211fe-134">$false</span></span>        | <span data-ttu-id="211fe-135">S</span><span class="sxs-lookup"><span data-stu-id="211fe-135">S</span></span>                            | <span data-ttu-id="211fe-136">F</span><span class="sxs-lookup"><span data-stu-id="211fe-136">F</span></span>                              |
   | <span data-ttu-id="211fe-137">F, S</span><span class="sxs-lookup"><span data-stu-id="211fe-137">F,S</span></span>                             | <span data-ttu-id="211fe-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="211fe-138">PendingConfiguration</span></span> | <span data-ttu-id="211fe-139">Mislukt</span><span class="sxs-lookup"><span data-stu-id="211fe-139">Failure</span></span>    | <span data-ttu-id="211fe-140">$false</span><span class="sxs-lookup"><span data-stu-id="211fe-140">$false</span></span>        | <span data-ttu-id="211fe-141">S</span><span class="sxs-lookup"><span data-stu-id="211fe-141">S</span></span>                            | <span data-ttu-id="211fe-142">F</span><span class="sxs-lookup"><span data-stu-id="211fe-142">F</span></span>                              |
   | <span data-ttu-id="211fe-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="211fe-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="211fe-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="211fe-144">PendingConfiguration</span></span> | <span data-ttu-id="211fe-145">Mislukt</span><span class="sxs-lookup"><span data-stu-id="211fe-145">Failure</span></span>    | <span data-ttu-id="211fe-146">$false</span><span class="sxs-lookup"><span data-stu-id="211fe-146">$false</span></span>        | <span data-ttu-id="211fe-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="211fe-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="211fe-148">F</span><span class="sxs-lookup"><span data-stu-id="211fe-148">F</span></span>                              |
   | <span data-ttu-id="211fe-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="211fe-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="211fe-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="211fe-150">PendingConfiguration</span></span> | <span data-ttu-id="211fe-151">Mislukt</span><span class="sxs-lookup"><span data-stu-id="211fe-151">Failure</span></span>    | <span data-ttu-id="211fe-152">$false</span><span class="sxs-lookup"><span data-stu-id="211fe-152">$false</span></span>        | <span data-ttu-id="211fe-153">S</span><span class="sxs-lookup"><span data-stu-id="211fe-153">S</span></span>                            | <span data-ttu-id="211fe-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="211fe-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="211fe-155">S, r</span><span class="sxs-lookup"><span data-stu-id="211fe-155">S, r</span></span>                            | <span data-ttu-id="211fe-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="211fe-156">PendingReboot</span></span>        | <span data-ttu-id="211fe-157">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="211fe-157">Success</span></span>    | <span data-ttu-id="211fe-158">$true</span><span class="sxs-lookup"><span data-stu-id="211fe-158">$true</span></span>         | <span data-ttu-id="211fe-159">S</span><span class="sxs-lookup"><span data-stu-id="211fe-159">S</span></span>                            | <span data-ttu-id="211fe-160">r</span><span class="sxs-lookup"><span data-stu-id="211fe-160">r</span></span>                              |
   | <span data-ttu-id="211fe-161">F, r</span><span class="sxs-lookup"><span data-stu-id="211fe-161">F, r</span></span>                            | <span data-ttu-id="211fe-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="211fe-162">PendingReboot</span></span>        | <span data-ttu-id="211fe-163">Mislukt</span><span class="sxs-lookup"><span data-stu-id="211fe-163">Failure</span></span>    | <span data-ttu-id="211fe-164">$true</span><span class="sxs-lookup"><span data-stu-id="211fe-164">$true</span></span>         | <span data-ttu-id="211fe-165">$null</span><span class="sxs-lookup"><span data-stu-id="211fe-165">$null</span></span>                        | <span data-ttu-id="211fe-166">F, r</span><span class="sxs-lookup"><span data-stu-id="211fe-166">F, r</span></span>                           |
   | <span data-ttu-id="211fe-167">r, S</span><span class="sxs-lookup"><span data-stu-id="211fe-167">r, S</span></span>                            | <span data-ttu-id="211fe-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="211fe-168">PendingReboot</span></span>        | <span data-ttu-id="211fe-169">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="211fe-169">Success</span></span>    | <span data-ttu-id="211fe-170">$true</span><span class="sxs-lookup"><span data-stu-id="211fe-170">$true</span></span>         | <span data-ttu-id="211fe-171">$null</span><span class="sxs-lookup"><span data-stu-id="211fe-171">$null</span></span>                        | <span data-ttu-id="211fe-172">r</span><span class="sxs-lookup"><span data-stu-id="211fe-172">r</span></span>                              |
   | <span data-ttu-id="211fe-173">r, F</span><span class="sxs-lookup"><span data-stu-id="211fe-173">r, F</span></span>                            | <span data-ttu-id="211fe-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="211fe-174">PendingReboot</span></span>        | <span data-ttu-id="211fe-175">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="211fe-175">Success</span></span>    | <span data-ttu-id="211fe-176">$true</span><span class="sxs-lookup"><span data-stu-id="211fe-176">$true</span></span>         | <span data-ttu-id="211fe-177">$null</span><span class="sxs-lookup"><span data-stu-id="211fe-177">$null</span></span>                        | <span data-ttu-id="211fe-178">r</span><span class="sxs-lookup"><span data-stu-id="211fe-178">r</span></span>                              |

   <span data-ttu-id="211fe-179">^
   S<sub>ik</sub>: een reeks resources die is toegepast, F<sub>ik</sub>: een reeks resources die toegepast zonder succes r: A resource waarvoor opnieuw opstarten \*</span><span class="sxs-lookup"><span data-stu-id="211fe-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="211fe-180">Uitbreiding in de cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="211fe-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="211fe-181">Er zijn enkele verbeteringen zijn aangebracht aan `Get-DscConfigurationStatus` cmdlet in deze release.</span><span class="sxs-lookup"><span data-stu-id="211fe-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="211fe-182">De eigenschap StartDate van objecten die worden geretourneerd door de cmdlet is eerder, van het type tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="211fe-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="211fe-183">Het is nu, van het type Datetime, waarmee complexe selecteren en filteren eenvoudiger op basis van de ingebouwde eigenschappen van een datum/tijd-object.</span><span class="sxs-lookup"><span data-stu-id="211fe-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="211fe-184">Hieronder volgt een voorbeeld waarin retourneert dat alle records voor DSC-bewerking op dezelfde dag van week vandaag is er gebeurd.</span><span class="sxs-lookup"><span data-stu-id="211fe-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="211fe-185">Records van bewerkingen die geen wijzigingen in van het knooppunt configuratie aanbrengen mag (dat wil zeggen alleen bewerkingen lezen) worden geëlimineerd.</span><span class="sxs-lookup"><span data-stu-id="211fe-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="211fe-186">Daarom `Test-DscConfiguration`, `Get-DscConfiguration` bewerkingen zijn niet meer in de geretourneerde objecten uit verontreinigde `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="211fe-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="211fe-187">Records van meta-configuratie-instelling bewerking wordt toegevoegd aan het rendement van `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="211fe-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="211fe-188">Hieronder volgt een voorbeeld van resultaat geretourneerd vanuit `Get-DscConfigurationStatus` – alle cmdlet.</span><span class="sxs-lookup"><span data-stu-id="211fe-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="211fe-189">Uitbreiding in de cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="211fe-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="211fe-190">Een nieuw veld van LCMStateDetail wordt toegevoegd aan het object dat wordt geretourneerd vanaf `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="211fe-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="211fe-191">Dit veld wordt gevuld wanneer LCMState is 'Bezet'.</span><span class="sxs-lookup"><span data-stu-id="211fe-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="211fe-192">Het kan worden opgehaald door de volgende cmdlet:</span><span class="sxs-lookup"><span data-stu-id="211fe-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="211fe-193">Hieronder volgt een voorbeeld van uitvoer van een doorlopende bewaking van een configuratie waarvoor twee keer opnieuw opstarten op een externe knooppunt.</span><span class="sxs-lookup"><span data-stu-id="211fe-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```