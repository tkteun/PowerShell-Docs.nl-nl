---
title: Activiteitsparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e4e0cf6-19e0-44b8-8b40-d6f6075276cf
caps.latest.revision: 5
ms.openlocfilehash: 32e2b8acf33bc733c5e4cab94a721076ff46225d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849089"
---
# <a name="activity-parameters"></a><span data-ttu-id="6d154-102">Activiteitsparameters</span><span class="sxs-lookup"><span data-stu-id="6d154-102">Activity Parameters</span></span>

<span data-ttu-id="6d154-103">De volgende tabel bevat de aanbevolen namen en de functionaliteit voor de activiteitsparameters.</span><span class="sxs-lookup"><span data-stu-id="6d154-103">The following table lists the recommended names and functionality for activity parameters.</span></span>

<span data-ttu-id="6d154-104">Gegevens van het type toevoegen: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-104">Append Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-105">Implementeer deze parameter zodat de gebruikers inhoud aan het einde van een resource toevoegen kunnen als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-105">Implement this parameter so that the user can add content to the end of a resource when the parameter is specified.</span></span>

<span data-ttu-id="6d154-106">CaseSensitive-gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-106">CaseSensitive Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-107">Deze parameter implementeren, zodat de gebruiker hoofdlettergevoeligheid vereisen kunt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-107">Implement this parameter so the user can require case sensitivity when the parameter is specified.</span></span>

<span data-ttu-id="6d154-108">Opdracht-gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6d154-108">Command Data type: String</span></span>

<span data-ttu-id="6d154-109">Deze parameter implementeren, zodat de gebruiker een opdrachttekenreeks om uit te voeren kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-109">Implement this parameter so the user can specify a command string to run.</span></span>

<span data-ttu-id="6d154-110">CompatibleVersion gegevenstype: System.Version object</span><span class="sxs-lookup"><span data-stu-id="6d154-110">CompatibleVersion Data type: System.Version object</span></span>

<span data-ttu-id="6d154-111">Deze parameter implementeren, zodat de gebruiker de semantiek voor dat de cmdlet compatibel met voor compatibiliteit met eerdere versies zijn moet kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-111">Implement this parameter so the user can specify the semantics that the cmdlet must be compatible with for compatibility with previous versions.</span></span>

<span data-ttu-id="6d154-112">Comprimeren van gegevens van het type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-112">Compress Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-113">Implementeer deze parameter zodat de compressie van gegevens wordt gebruikt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-113">Implement this parameter so that data compression is used when the parameter is specified.</span></span>

<span data-ttu-id="6d154-114">Comprimeren van gegevens van het type: Trefwoord</span><span class="sxs-lookup"><span data-stu-id="6d154-114">Compress Data type: Keyword</span></span>

<span data-ttu-id="6d154-115">Deze parameter implementeren zodat de gebruiker het algoritme moet worden gebruikt voor de compressie van gegevens kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-115">Implement this parameter so that the user can specify the algorithm to use for data compression.</span></span>

<span data-ttu-id="6d154-116">Continue gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-116">Continuous Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-117">Implementeer deze parameter zodat de gegevens worden verwerkt totdat de gebruiker de cmdlet wordt gesloten wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-117">Implement this parameter so that data is processed until the user terminates the cmdlet when the parameter is specified.</span></span> <span data-ttu-id="6d154-118">Als de parameter niet opgegeven is, wordt de cmdlet verwerkt een vooraf gedefinieerde hoeveelheid gegevens en vervolgens de bewerking beëindigd.</span><span class="sxs-lookup"><span data-stu-id="6d154-118">If the parameter is not specified, the cmdlet processes a predefined amount of data and then terminates the operation.</span></span>

<span data-ttu-id="6d154-119">Gegevenstype maken: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-119">Create Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-120">Implementeer deze parameter om aan te geven dat een resource wordt gemaakt als deze niet al bestaat als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-120">Implement this parameter to indicate that a resource is created if one does not already exist when the parameter is specified.</span></span>

<span data-ttu-id="6d154-121">Verwijder het gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-121">Delete Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-122">Implementeer deze parameter zodat resources worden verwijderd wanneer de cmdlet kan de bewerking is voltooid wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-122">Implement this parameter so that resources are deleted when the cmdlet has completed its operation when the parameter is specified.</span></span>

<span data-ttu-id="6d154-123">Leegmaken gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-123">Drain Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-124">Implementeer deze parameter om aan te geven dat er een uitstaande werkitems worden verwerkt voordat nieuwe gegevens in de cmdlet worden verwerkt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-124">Implement this parameter to indicate that outstanding work items are processed before the cmdlet processes new data when the parameter is specified.</span></span> <span data-ttu-id="6d154-125">Als de parameter niet opgegeven is, worden de werkitems onmiddellijk verwerkt.</span><span class="sxs-lookup"><span data-stu-id="6d154-125">If the parameter is not specified, the work items are processed immediately.</span></span>

<span data-ttu-id="6d154-126">Wissen van gegevens van het type: Int32</span><span class="sxs-lookup"><span data-stu-id="6d154-126">Erase Data type: Int32</span></span>

<span data-ttu-id="6d154-127">Deze parameter implementeren zodat de gebruiker het aantal keren dat die een resource worden gewist opgeven kan voordat deze wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="6d154-127">Implement this parameter so that the user can specify the number of times a resource is erased before it is deleted.</span></span>

<span data-ttu-id="6d154-128">ErrorLevel gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="6d154-128">ErrorLevel Data type: Int32</span></span>

<span data-ttu-id="6d154-129">Implementeer deze parameter zodat de gebruiker kan het niveau van fouten naar het rapport opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-129">Implement this parameter so that the user can specify the level of errors to report.</span></span>

<span data-ttu-id="6d154-130">Gegevens van het type uitsluiten: String[]</span><span class="sxs-lookup"><span data-stu-id="6d154-130">Exclude Data type: String[]</span></span>

<span data-ttu-id="6d154-131">Implementeer deze parameter zodat de gebruiker iets van een activiteit uitsluiten kunt.</span><span class="sxs-lookup"><span data-stu-id="6d154-131">Implement this parameter so that the user can exclude something from an activity.</span></span> <span data-ttu-id="6d154-132">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6d154-132">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="6d154-133">Filteren van gegevens van het type: Trefwoord</span><span class="sxs-lookup"><span data-stu-id="6d154-133">Filter Data type: Keyword</span></span>

<span data-ttu-id="6d154-134">Deze parameter implementeren zodat de gebruiker kan een filter dat de resources waarop de actie van de cmdlet uit te voeren selecteert opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-134">Implement this parameter so that the user can specify a filter that selects the resources upon which to perform the cmdlet action.</span></span> <span data-ttu-id="6d154-135">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6d154-135">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="6d154-136">Voer de gegevens van het type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-136">Follow Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-137">Implementeer deze parameter zodat de voortgang wordt bijgehouden wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-137">Implement this parameter so that progress is tracked when the parameter is specified.</span></span>

<span data-ttu-id="6d154-138">Afdwingen dat het gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-138">Force Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-139">Implementeer deze parameter om aan te geven dat de gebruiker een actie uitvoeren kan, zelfs als er beperkingen optreden als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-139">Implement this parameter to indicate that the user can perform an action even if restrictions are encountered when the parameter is specified.</span></span> <span data-ttu-id="6d154-140">De beveiliging is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="6d154-140">The parameter does not allow security to be compromised.</span></span> <span data-ttu-id="6d154-141">Deze parameter kunt bijvoorbeeld een gebruiker een alleen-lezenbestand overschrijven.</span><span class="sxs-lookup"><span data-stu-id="6d154-141">For example, this parameter lets a user overwrite a read-only file.</span></span>

<span data-ttu-id="6d154-142">Gegevenstype bevatten: String[]</span><span class="sxs-lookup"><span data-stu-id="6d154-142">Include Data type: String[]</span></span>

<span data-ttu-id="6d154-143">Implementeer deze parameter zodat de gebruiker iets in een activiteit opnemen kunt.</span><span class="sxs-lookup"><span data-stu-id="6d154-143">Implement this parameter so that the user can include something in an activity.</span></span> <span data-ttu-id="6d154-144">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6d154-144">For more information about how to use input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="6d154-145">Incrementele gegevens typt u: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-145">Incremental Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-146">Implementeer deze parameter om aan te geven dat de verwerking stapsgewijs wordt uitgevoerd wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-146">Implement this parameter to indicate that processing is performed incrementally when the parameter is specified.</span></span> <span data-ttu-id="6d154-147">Met deze parameter kunt bijvoorbeeld het uitvoeren van incrementele back-ups die back-up van bestanden alleen sinds de laatste back-up van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="6d154-147">For example, this parameter lets a user perform incremental backups that back up files only since the last backup.</span></span>

<span data-ttu-id="6d154-148">InputObject gegevenstype: Object</span><span class="sxs-lookup"><span data-stu-id="6d154-148">InputObject Data type: Object</span></span>

<span data-ttu-id="6d154-149">Deze parameter implementeren wanneer de cmdlet wordt de invoer uit andere cmdlets.</span><span class="sxs-lookup"><span data-stu-id="6d154-149">Implement this parameter when the cmdlet takes input from other cmdlets.</span></span> <span data-ttu-id="6d154-150">Als u definieert een `InputObject` parameter altijd opgeven om de `ValueFromPipeline` sleutelwoord wanneer u declareert de **Parameter** kenmerk.</span><span class="sxs-lookup"><span data-stu-id="6d154-150">When you define an `InputObject` parameter, always specify the `ValueFromPipeline` keyword when you declare the **Parameter** attribute.</span></span> <span data-ttu-id="6d154-151">Zie voor meer informatie over het gebruik van invoer filters [invoerparameters Filter](./input-filter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6d154-151">For more information about using input filters, see [Input Filter Parameters](./input-filter-parameters.md).</span></span>

<span data-ttu-id="6d154-152">Voeg de gegevens van het type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-152">Insert Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-153">Implementeer deze parameter zodat de cmdlet wordt een item ingevoegd als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-153">Implement this parameter so that the cmdlet inserts an item when the parameter is specified.</span></span>

<span data-ttu-id="6d154-154">Interactieve gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-154">Interactive Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-155">Implementeer deze parameter zodat de cmdlet interactief met de gebruiker werkt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-155">Implement this parameter so that the cmdlet works interactively with the user when the parameter is specified.</span></span>

<span data-ttu-id="6d154-156">Intervaltype van gegevens: Hash-tabel</span><span class="sxs-lookup"><span data-stu-id="6d154-156">Interval Data type: HashTable</span></span>

<span data-ttu-id="6d154-157">Implementeer deze parameter zodat de gebruiker kan een hash-tabel met trefwoorden die de waarden bevat opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-157">Implement this parameter so that the user can specify a hash table of keywords that contains the values.</span></span> <span data-ttu-id="6d154-158">Het volgende voorbeeld toont voorbeeldwaarden voor de `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.</span><span class="sxs-lookup"><span data-stu-id="6d154-158">The following example shows sample values for the `Interval` parameter: `-interval @{ResumeScan=15; Retry=3}`.</span></span>

<span data-ttu-id="6d154-159">Logboekgegevens, typt u: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-159">Log Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-160">Implementeer de controle voor deze parameter de acties van de cmdlet wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-160">Implement this parameter audit the actions of the cmdlet when the parameter is specified.</span></span>

<span data-ttu-id="6d154-161">NoClobber gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-161">NoClobber Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-162">Implementeer deze parameter zodat de bron niet worden overschreven wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-162">Implement this parameter so that the resource will not be overwritten when the parameter is specified.</span></span> <span data-ttu-id="6d154-163">Deze parameter is algemeen van toepassing op de cmdlets die nieuwe objecten maken, zodat ze kunnen worden voorkomen van het overschrijven van bestaande objecten met dezelfde naam.</span><span class="sxs-lookup"><span data-stu-id="6d154-163">This parameter generally applies to cmdlets that create new objects so that they can be prevented from overwriting existing objects with the same name.</span></span>

<span data-ttu-id="6d154-164">Op de hoogte stellen gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-164">Notify Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-165">Implementeer deze parameter zodat de gebruiker ontvangt een melding dat de activiteit voltooid is wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-165">Implement this parameter so that the user will be notified that the activity is complete when the parameter is specified.</span></span>

<span data-ttu-id="6d154-166">NotifyAddress gegevenstype: E-mailadres</span><span class="sxs-lookup"><span data-stu-id="6d154-166">NotifyAddress Data type: E-mail address</span></span>

<span data-ttu-id="6d154-167">Deze parameter implementeren zodat de gebruiker kan het e-mailadres te gebruiken voor het verzenden van een melding opgeven wanneer de `Notify` parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-167">Implement this parameter so that the user can specify the e-mail address to use to send a notification when the `Notify` parameter is specified.</span></span>

<span data-ttu-id="6d154-168">Gegevens van het type overschrijven: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-168">Overwrite Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-169">Implementeer deze parameter zodat de cmdlet worden alle bestaande gegevens overschreven wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-169">Implement this parameter so that the cmdlet overwrites any existing data when the parameter is specified.</span></span>

<span data-ttu-id="6d154-170">Gegevens van het type vragen: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6d154-170">Prompt Data type: String</span></span>

<span data-ttu-id="6d154-171">Deze parameter implementeren zodat de gebruiker kan een prompt voor de cmdlet opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-171">Implement this parameter so that the user can specify a prompt for the cmdlet.</span></span>

<span data-ttu-id="6d154-172">Stille gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-172">Quiet Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-173">Implementeer deze parameter zodat de cmdlet feedback van gebruikers tijdens de acties onderdrukt als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-173">Implement this parameter so that the cmdlet suppresses user feedback during its actions when the parameter is specified.</span></span>

<span data-ttu-id="6d154-174">Recurse gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-174">Recurse Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-175">Implementeer deze parameter zodat de recursief cmdlet worden de acties uitgevoerd op resources als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-175">Implement this parameter so that the cmdlet recursively performs its actions on resources when the parameter is specified.</span></span>

<span data-ttu-id="6d154-176">Herstellen van gegevens van het type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-176">Repair Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-177">Implementeer deze parameter zodat de cmdlet probeert op te lossen iets uit een beschadigde status als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-177">Implement this parameter so that the cmdlet will attempt to correct something from a broken state when the parameter is specified.</span></span>

<span data-ttu-id="6d154-178">RepairString gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6d154-178">RepairString Data type: String</span></span>

<span data-ttu-id="6d154-179">Deze parameter implementeren zodat de gebruiker van een tekenreeks opgeven kan voor het gebruik van wanneer de `Repair` parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-179">Implement this parameter so that the user can specify a string to use when the `Repair` parameter is specified.</span></span>

<span data-ttu-id="6d154-180">Het gegevenstype voor opnieuw proberen: Int32</span><span class="sxs-lookup"><span data-stu-id="6d154-180">Retry Data type: Int32</span></span>

<span data-ttu-id="6d154-181">Deze parameter implementeren, zodat de gebruiker kan het aantal keren dat de cmdlet een actie probeert opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-181">Implement this parameter so the user can specify the number of times the cmdlet will attempt an action.</span></span>

<span data-ttu-id="6d154-182">Selecteer het gegevenstype: Sleutelwoord matrix</span><span class="sxs-lookup"><span data-stu-id="6d154-182">Select Data type: Keyword array</span></span>

<span data-ttu-id="6d154-183">Implementeer deze parameter zodat de gebruiker kan een matrix van de typen objecten opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-183">Implement this parameter so that the user can specify an array of the types of items.</span></span>

<span data-ttu-id="6d154-184">Stream-gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-184">Stream Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-185">Deze parameter implementeren, zodat de gebruiker meerdere uitvoer objecten via de pijplijn streamen kan wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-185">Implement this parameter so the user can stream multiple output objects through the pipeline when the parameter is specified.</span></span>

<span data-ttu-id="6d154-186">Strikte gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-186">Strict Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-187">Implementeer deze parameter zodat alle fouten worden verwerkt als fouten wordt beëindigd wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-187">Implement this parameter so that all errors are handled as terminating errors when the parameter is specified.</span></span>

<span data-ttu-id="6d154-188">TempLocation gegevenstype: Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6d154-188">TempLocation Data type: String</span></span>

<span data-ttu-id="6d154-189">Deze parameter implementeren, zodat de gebruiker de locatie van tijdelijke gegevens die worden gebruikt tijdens de bewerking van de cmdlet kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-189">Implement this parameter so the user can specify the location of temporary data that is used during the operation of the cmdlet.</span></span>

<span data-ttu-id="6d154-190">Time-out voor het gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="6d154-190">Timeout Data type: Int32</span></span>

<span data-ttu-id="6d154-191">Implementeer deze parameter zodat de gebruiker kan de time-outinterval (in milliseconden) opgeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-191">Implement this parameter so that the user can specify the timeout interval (in milliseconds).</span></span>

<span data-ttu-id="6d154-192">Het gegevenstype worden afgekapt: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-192">Truncate Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-193">Implementeer deze parameter zodat de cmdlet worden de acties worden afgekapt wanneer de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-193">Implement this parameter so that the cmdlet will truncate its actions when the parameter is specified.</span></span> <span data-ttu-id="6d154-194">Als de parameter niet opgegeven is, wordt door de cmdlet een andere actie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="6d154-194">If the parameter is not specified, the cmdlet performs another action.</span></span>

<span data-ttu-id="6d154-195">Controleer of het gegevenstype: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-195">Verify Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-196">Implementeer deze parameter zodat de cmdlet test om te bepalen of een actie is opgetreden bij de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-196">Implement this parameter so that the cmdlet will test to determine whether an action has occurred when the parameter is specified.</span></span>

<span data-ttu-id="6d154-197">Wachten op gegevens van het type: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="6d154-197">Wait Data type: SwitchParameter</span></span>

<span data-ttu-id="6d154-198">Implementeer deze parameter zodat de cmdlet op invoer van de gebruiker wacht voordat u doorgaat als de parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-198">Implement this parameter so that the cmdlet will wait for user input before continuing when the parameter is specified.</span></span>

<span data-ttu-id="6d154-199">Wachttijd gegevenstype: Int32</span><span class="sxs-lookup"><span data-stu-id="6d154-199">WaitTime Data type: Int32</span></span>

<span data-ttu-id="6d154-200">Deze parameter implementeren zodat de gebruiker kan de duur (in seconden) opgeven dat de cmdlet wordt gewacht op gebruiker invoer wanneer de `Wait` parameter is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6d154-200">Implement this parameter so that the user can specify the duration (in seconds) that the cmdlet will wait for user input when the `Wait` parameter is specified.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d154-201">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6d154-201">See Also</span></span>

[<span data-ttu-id="6d154-202">Cmdlet-Parameters</span><span class="sxs-lookup"><span data-stu-id="6d154-202">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="6d154-203">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6d154-203">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="6d154-204">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6d154-204">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
