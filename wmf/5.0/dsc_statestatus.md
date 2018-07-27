---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: bed1186c10082bbdac7249503bf623678f13fccd
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267936"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="4615d-102">Uniforme en consistente status en statusweergave</span><span class="sxs-lookup"><span data-stu-id="4615d-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="4615d-103">Een reeks verbeteringen zijn aangebracht in deze release voor automatische ingebouwd LCM-status en DSC-status.</span><span class="sxs-lookup"><span data-stu-id="4615d-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="4615d-104">Uniforme en consistente status en de status verklaringen, beheerbare datetime-eigenschap van de van statusobjecten die worden geretourneerd door het gaat hierbij `Get-DscConfigurationStatus` cmdlet en verbeterde LCM staat details van de eigenschap die wordt geretourneerd door `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4615d-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="4615d-105">De weergave van LCM-status en de status van de DSC-bewerking worden herzien en geïntegreerde op basis van de volgende regels:</span><span class="sxs-lookup"><span data-stu-id="4615d-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="4615d-106">NotProcessed weer resource heeft geen invloed op LCM-status en DSC-status.</span><span class="sxs-lookup"><span data-stu-id="4615d-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="4615d-107">LCM stoppen verdere informatie verwerken zodra er een resource die opnieuw opstarten aanvragen wordt aangetroffen.</span><span class="sxs-lookup"><span data-stu-id="4615d-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="4615d-108">Een resource die opnieuw opstarten aanvragen is niet in de gewenste status totdat opnieuw opstarten daadwerkelijk gebeurt.</span><span class="sxs-lookup"><span data-stu-id="4615d-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="4615d-109">Na het vaststellen van een resource die is mislukt, houdt LCM verwerken van meer resources, zolang ze niet afhankelijk van de fout een zijn.</span><span class="sxs-lookup"><span data-stu-id="4615d-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="4615d-110">De algemene status geretourneerd door `Get-DscConfigurationStatus` cmdlet is de super set alle resources de status.</span><span class="sxs-lookup"><span data-stu-id="4615d-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="4615d-111">De status PendingReboot is een superset van PendingConfiguration staat.</span><span class="sxs-lookup"><span data-stu-id="4615d-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="4615d-112">De onderstaande tabel ziet u de resulterende status en de status eigenschappen met betrekking tot onder een aantal typische scenario's.</span><span class="sxs-lookup"><span data-stu-id="4615d-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="4615d-113">Scenario</span><span class="sxs-lookup"><span data-stu-id="4615d-113">Scenario</span></span>                        | <span data-ttu-id="4615d-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="4615d-114">LCMState</span></span>             | <span data-ttu-id="4615d-115">Status</span><span class="sxs-lookup"><span data-stu-id="4615d-115">Status</span></span>     | <span data-ttu-id="4615d-116">Opnieuw opstarten aangevraagd</span><span class="sxs-lookup"><span data-stu-id="4615d-116">Reboot Requested</span></span> | <span data-ttu-id="4615d-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="4615d-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="4615d-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="4615d-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="4615d-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="4615d-119">S**^**</span></span>                          | <span data-ttu-id="4615d-120">Actieve</span><span class="sxs-lookup"><span data-stu-id="4615d-120">Idle</span></span>                 | <span data-ttu-id="4615d-121">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="4615d-121">Success</span></span>    | <span data-ttu-id="4615d-122">$false</span><span class="sxs-lookup"><span data-stu-id="4615d-122">$false</span></span>        | <span data-ttu-id="4615d-123">S</span><span class="sxs-lookup"><span data-stu-id="4615d-123">S</span></span>                            | <span data-ttu-id="4615d-124">$null</span><span class="sxs-lookup"><span data-stu-id="4615d-124">$null</span></span>                          |
| <span data-ttu-id="4615d-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="4615d-125">F**^**</span></span>                          | <span data-ttu-id="4615d-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4615d-126">PendingConfiguration</span></span> | <span data-ttu-id="4615d-127">Mislukt</span><span class="sxs-lookup"><span data-stu-id="4615d-127">Failure</span></span>    | <span data-ttu-id="4615d-128">$false</span><span class="sxs-lookup"><span data-stu-id="4615d-128">$false</span></span>        | <span data-ttu-id="4615d-129">$null</span><span class="sxs-lookup"><span data-stu-id="4615d-129">$null</span></span>                        | <span data-ttu-id="4615d-130">F</span><span class="sxs-lookup"><span data-stu-id="4615d-130">F</span></span>                              |
| <span data-ttu-id="4615d-131">S, F</span><span class="sxs-lookup"><span data-stu-id="4615d-131">S,F</span></span>                             | <span data-ttu-id="4615d-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4615d-132">PendingConfiguration</span></span> | <span data-ttu-id="4615d-133">Mislukt</span><span class="sxs-lookup"><span data-stu-id="4615d-133">Failure</span></span>    | <span data-ttu-id="4615d-134">$false</span><span class="sxs-lookup"><span data-stu-id="4615d-134">$false</span></span>        | <span data-ttu-id="4615d-135">S</span><span class="sxs-lookup"><span data-stu-id="4615d-135">S</span></span>                            | <span data-ttu-id="4615d-136">F</span><span class="sxs-lookup"><span data-stu-id="4615d-136">F</span></span>                              |
| <span data-ttu-id="4615d-137">F, S</span><span class="sxs-lookup"><span data-stu-id="4615d-137">F,S</span></span>                             | <span data-ttu-id="4615d-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4615d-138">PendingConfiguration</span></span> | <span data-ttu-id="4615d-139">Mislukt</span><span class="sxs-lookup"><span data-stu-id="4615d-139">Failure</span></span>    | <span data-ttu-id="4615d-140">$false</span><span class="sxs-lookup"><span data-stu-id="4615d-140">$false</span></span>        | <span data-ttu-id="4615d-141">S</span><span class="sxs-lookup"><span data-stu-id="4615d-141">S</span></span>                            | <span data-ttu-id="4615d-142">F</span><span class="sxs-lookup"><span data-stu-id="4615d-142">F</span></span>                              |
| <span data-ttu-id="4615d-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="4615d-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="4615d-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4615d-144">PendingConfiguration</span></span> | <span data-ttu-id="4615d-145">Mislukt</span><span class="sxs-lookup"><span data-stu-id="4615d-145">Failure</span></span>    | <span data-ttu-id="4615d-146">$false</span><span class="sxs-lookup"><span data-stu-id="4615d-146">$false</span></span>        | <span data-ttu-id="4615d-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="4615d-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="4615d-148">F</span><span class="sxs-lookup"><span data-stu-id="4615d-148">F</span></span>                              |
| <span data-ttu-id="4615d-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="4615d-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="4615d-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4615d-150">PendingConfiguration</span></span> | <span data-ttu-id="4615d-151">Mislukt</span><span class="sxs-lookup"><span data-stu-id="4615d-151">Failure</span></span>    | <span data-ttu-id="4615d-152">$false</span><span class="sxs-lookup"><span data-stu-id="4615d-152">$false</span></span>        | <span data-ttu-id="4615d-153">S</span><span class="sxs-lookup"><span data-stu-id="4615d-153">S</span></span>                            | <span data-ttu-id="4615d-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="4615d-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="4615d-155">S, r</span><span class="sxs-lookup"><span data-stu-id="4615d-155">S, r</span></span>                            | <span data-ttu-id="4615d-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="4615d-156">PendingReboot</span></span>        | <span data-ttu-id="4615d-157">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="4615d-157">Success</span></span>    | <span data-ttu-id="4615d-158">$true</span><span class="sxs-lookup"><span data-stu-id="4615d-158">$true</span></span>         | <span data-ttu-id="4615d-159">S</span><span class="sxs-lookup"><span data-stu-id="4615d-159">S</span></span>                            | <span data-ttu-id="4615d-160">r</span><span class="sxs-lookup"><span data-stu-id="4615d-160">r</span></span>                              |
| <span data-ttu-id="4615d-161">F, r</span><span class="sxs-lookup"><span data-stu-id="4615d-161">F, r</span></span>                            | <span data-ttu-id="4615d-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="4615d-162">PendingReboot</span></span>        | <span data-ttu-id="4615d-163">Mislukt</span><span class="sxs-lookup"><span data-stu-id="4615d-163">Failure</span></span>    | <span data-ttu-id="4615d-164">$true</span><span class="sxs-lookup"><span data-stu-id="4615d-164">$true</span></span>         | <span data-ttu-id="4615d-165">$null</span><span class="sxs-lookup"><span data-stu-id="4615d-165">$null</span></span>                        | <span data-ttu-id="4615d-166">F, r</span><span class="sxs-lookup"><span data-stu-id="4615d-166">F, r</span></span>                           |
| <span data-ttu-id="4615d-167">r, S</span><span class="sxs-lookup"><span data-stu-id="4615d-167">r, S</span></span>                            | <span data-ttu-id="4615d-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="4615d-168">PendingReboot</span></span>        | <span data-ttu-id="4615d-169">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="4615d-169">Success</span></span>    | <span data-ttu-id="4615d-170">$true</span><span class="sxs-lookup"><span data-stu-id="4615d-170">$true</span></span>         | <span data-ttu-id="4615d-171">$null</span><span class="sxs-lookup"><span data-stu-id="4615d-171">$null</span></span>                        | <span data-ttu-id="4615d-172">r</span><span class="sxs-lookup"><span data-stu-id="4615d-172">r</span></span>                              |
| <span data-ttu-id="4615d-173">r, F</span><span class="sxs-lookup"><span data-stu-id="4615d-173">r, F</span></span>                            | <span data-ttu-id="4615d-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="4615d-174">PendingReboot</span></span>        | <span data-ttu-id="4615d-175">Geslaagd</span><span class="sxs-lookup"><span data-stu-id="4615d-175">Success</span></span>    | <span data-ttu-id="4615d-176">$true</span><span class="sxs-lookup"><span data-stu-id="4615d-176">$true</span></span>         | <span data-ttu-id="4615d-177">$null</span><span class="sxs-lookup"><span data-stu-id="4615d-177">$null</span></span>                        | <span data-ttu-id="4615d-178">r</span><span class="sxs-lookup"><span data-stu-id="4615d-178">r</span></span>                              |

- <span data-ttu-id="4615d-179">S<sub>ik</sub>: een reeks resources die is toegepast</span><span class="sxs-lookup"><span data-stu-id="4615d-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="4615d-180">F<sub>ik</sub>: een reeks resources die zonder succes toegepast</span><span class="sxs-lookup"><span data-stu-id="4615d-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="4615d-181">r: een resource die is vereist opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="4615d-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="4615d-182">Uitbreiding in de cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="4615d-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="4615d-183">Er zijn enkele verbeteringen zijn aangebracht aan `Get-DscConfigurationStatus` cmdlet in deze release.</span><span class="sxs-lookup"><span data-stu-id="4615d-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="4615d-184">De eigenschap StartDate van objecten die worden geretourneerd door de cmdlet is eerder, van het type tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="4615d-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="4615d-185">Het is nu, van het type Datetime, waarmee complexe selecteren en filteren eenvoudiger op basis van de ingebouwde eigenschappen van een datum/tijd-object.</span><span class="sxs-lookup"><span data-stu-id="4615d-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="4615d-186">Het volgende voorbeeld retourneert alle records van DSC-bewerking die hebben plaatsgevonden op dezelfde dag van week als de huidige dag.</span><span class="sxs-lookup"><span data-stu-id="4615d-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="4615d-187">Records van bewerkingen die geen wijzigingen in van het knooppunt configuratie aanbrengen mag (dat wil zeggen alleen bewerkingen lezen) worden geëlimineerd.</span><span class="sxs-lookup"><span data-stu-id="4615d-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="4615d-188">Daarom `Test-DscConfiguration`, `Get-DscConfiguration` bewerkingen zijn niet meer in de geretourneerde objecten uit verontreinigde `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4615d-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="4615d-189">Records van meta-configuratie-instelling bewerking wordt toegevoegd aan het rendement van `Get-DscConfigurationStatus` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4615d-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="4615d-190">Hieronder volgt een voorbeeld van resultaat geretourneerd vanuit `Get-DscConfigurationStatus –All` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4615d-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="4615d-191">Uitbreiding in de cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4615d-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="4615d-192">Een nieuw veld van LCMStateDetail wordt toegevoegd aan het object dat wordt geretourneerd vanaf `Get-DscLocalConfigurationManager` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4615d-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="4615d-193">Dit veld wordt gevuld wanneer LCMState is 'Bezet'.</span><span class="sxs-lookup"><span data-stu-id="4615d-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="4615d-194">Het kan worden opgehaald door de volgende cmdlet:</span><span class="sxs-lookup"><span data-stu-id="4615d-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="4615d-195">Hieronder volgt een voorbeeld van uitvoer van een doorlopende bewaking van een configuratie waarvoor twee keer opnieuw opstarten op een externe knooppunt.</span><span class="sxs-lookup"><span data-stu-id="4615d-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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