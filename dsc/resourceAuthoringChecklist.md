---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Controlelijst voor het ontwerpen van resource
ms.openlocfilehash: 39f652b458702dc7e815ab4b2f965e6728fa1b51
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="da715-103">Controlelijst voor het ontwerpen van resource</span><span class="sxs-lookup"><span data-stu-id="da715-103">Resource authoring checklist</span></span>
<span data-ttu-id="da715-104">Deze controlelijst is een lijst met aanbevolen procedures bij het ontwerpen van een nieuwe DSC-Resource.</span><span class="sxs-lookup"><span data-stu-id="da715-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>
## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="da715-105">Resource-module bevat .psd1 bestands- en schema.mof voor elke resource</span><span class="sxs-lookup"><span data-stu-id="da715-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>
<span data-ttu-id="da715-106">Controleer of de resource heeft de juiste structuur en alle vereiste bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="da715-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="da715-107">Elke resource-module een .psd1-bestand moet bevatten en elke resource niet-samengestelde schema.mof bestand moet hebben.</span><span class="sxs-lookup"><span data-stu-id="da715-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="da715-108">Resources die geen schema bevatten worden niet weergegeven door **Get-DscResource** en gebruikers zich niet intellisense gebruiken bij het schrijven van code voor deze modules in ISE.</span><span class="sxs-lookup"><span data-stu-id="da715-108">Resources that do not contain schema will not be listed by **Get-DscResource** and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="da715-109">De mapstructuur voor xRemoteFile resource die deel uitmaakt van de [xPSDesiredStateConfiguration bronmodule](https://github.com/PowerShell/xPSDesiredStateConfiguration), ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="da715-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="da715-110">Bron en het schema kloppen ##</span><span class="sxs-lookup"><span data-stu-id="da715-110">Resource and schema are correct##</span></span>
<span data-ttu-id="da715-111">Controleer het schema van de resource (\*. schema.mof) bestand.</span><span class="sxs-lookup"><span data-stu-id="da715-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="da715-112">U kunt de [DSC-Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) te ontwikkelen en testen van uw schema.</span><span class="sxs-lookup"><span data-stu-id="da715-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to help develop and test your schema.</span></span>
<span data-ttu-id="da715-113">Zorg ervoor dat:</span><span class="sxs-lookup"><span data-stu-id="da715-113">Make sure that:</span></span>
- <span data-ttu-id="da715-114">Typen eigenschappen juist zijn (bijvoorbeeld tekenreeks niet gebruiken voor eigenschappen die numerieke waarden accepteert, moet u UInt32 of andere numerieke typen in plaats daarvan)</span><span class="sxs-lookup"><span data-stu-id="da715-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="da715-115">Eigenschapskenmerken juist zijn opgegeven als: ([key], [vereist], [schrijven], [lezen])</span><span class="sxs-lookup"><span data-stu-id="da715-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="da715-116">Ten minste één parameter in het schema heeft zijn gemarkeerd als [sleutel]</span><span class="sxs-lookup"><span data-stu-id="da715-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="da715-117">[lezen] eigenschap niet naast elkaar worden gebruikt samen met een van: [vereist], [key], [schrijven]</span><span class="sxs-lookup"><span data-stu-id="da715-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="da715-118">Als meerdere kwalificaties zijn opgegeven, behalve [lezen], klikt u vervolgens prioriteit]</span><span class="sxs-lookup"><span data-stu-id="da715-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="da715-119">Als [schrijven] en [vereist] zijn opgegeven, wordt de [vereist] heeft een hogere prioriteit</span><span class="sxs-lookup"><span data-stu-id="da715-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="da715-120">ValueMap is opgegeven, indien van toepassing</span><span class="sxs-lookup"><span data-stu-id="da715-120">ValueMap is specified where appropriate</span></span>

<span data-ttu-id="da715-121">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="da715-121">Example:</span></span>
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- <span data-ttu-id="da715-122">Beschrijvende naam is opgegeven en bevestigt aan de naamgeving DSC</span><span class="sxs-lookup"><span data-stu-id="da715-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

<span data-ttu-id="da715-123">Voorbeeld: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span><span class="sxs-lookup"><span data-stu-id="da715-123">Example: ```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```</span></span>

- <span data-ttu-id="da715-124">Elk veld heeft een duidelijke beschrijving.</span><span class="sxs-lookup"><span data-stu-id="da715-124">Every field has meaningful description.</span></span> <span data-ttu-id="da715-125">De PowerShell-GitHub-opslagplaats is een goede voorbeelden zoals [de. schema.mof voor xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="da715-125">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="da715-126">Bovendien moet u **Test xDscResource** en **Test xDscSchema** cmdlets uit [DSC-Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) automatisch te controleren of de bron en het schema:</span><span class="sxs-lookup"><span data-stu-id="da715-126">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/) to automatically verify the resource and schema:</span></span>
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
<span data-ttu-id="da715-127">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="da715-127">For example:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="da715-128">Resource wordt geladen zonder fouten</span><span class="sxs-lookup"><span data-stu-id="da715-128">Resource loads without errors</span></span> ##
<span data-ttu-id="da715-129">Controleer of de module resources kan worden geladen.</span><span class="sxs-lookup"><span data-stu-id="da715-129">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="da715-130">Dit kan handmatig worden gerealiseerd door het uitvoeren van `Import-Module <resource_module> -force ` en bevestigt dat geen fouten zijn opgetreden, of door schrijven test automation.</span><span class="sxs-lookup"><span data-stu-id="da715-130">This can be achieved manually, by running `Import-Module <resource_module> -force ` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="da715-131">In geval van de laatste kunt u deze structuur te volgen in uw testscenario:</span><span class="sxs-lookup"><span data-stu-id="da715-131">In case of the latter, you can follow this structure in your test case:</span></span>
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="da715-132">Bron is idempotent in het geval is positief</span><span class="sxs-lookup"><span data-stu-id="da715-132">Resource is idempotent in the positive case</span></span>
<span data-ttu-id="da715-133">Een van de fundamentele kenmerken van DSC-resources is idempotence worden.</span><span class="sxs-lookup"><span data-stu-id="da715-133">One of the fundamental characteristics of DSC resources is be idempotence.</span></span> <span data-ttu-id="da715-134">Dit betekent dat het toepassen van een DSC-configuratie die resource met meerdere keren wordt altijd hetzelfde resultaat bereiken.</span><span class="sxs-lookup"><span data-stu-id="da715-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="da715-135">Bijvoorbeeld, als we een configuratie met de volgende bestandsbron maken:</span><span class="sxs-lookup"><span data-stu-id="da715-135">For example, if we create a configuration which contains the following File resource:</span></span>
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```
<span data-ttu-id="da715-136">Bestand test.txt worden na het toepassen van voor het eerst wordt weergegeven in de map C:\test.</span><span class="sxs-lookup"><span data-stu-id="da715-136">After applying it for the first time, file test.txt should appear in C:\test folder.</span></span> <span data-ttu-id="da715-137">Latere uitvoeringen van dezelfde configuratie moeten echter niet wijzigen voor de status van de machine (bijvoorbeeld geen kopieën van het bestand test.txt moeten worden gemaakt).</span><span class="sxs-lookup"><span data-stu-id="da715-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the test.txt file should be created).</span></span>
<span data-ttu-id="da715-138">Om te controleren of een resource idempotent kunt u meerdere keren aanroepen **Set TargetResource** bij het testen van de resource direct of bel **Start DscConfiguration** meerdere keren bij het uitvoeren van end-to-end testen.</span><span class="sxs-lookup"><span data-stu-id="da715-138">To ensure a resource is idempotent you can repeatedly call **Set-TargetResource** when testing the resource directly, or call **Start-DscConfiguration** multiple times when doing end to end testing.</span></span> <span data-ttu-id="da715-139">Het resultaat moet hetzelfde na elke uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="da715-139">The result should be the same after every run.</span></span>


## <a name="test-user-modification-scenario"></a><span data-ttu-id="da715-140">Testscenario gebruiker wijziging</span><span class="sxs-lookup"><span data-stu-id="da715-140">Test user modification scenario</span></span> ##
<span data-ttu-id="da715-141">Door het wijzigen van de status van de machine en vervolgens opnieuw uit te voeren DSC, kunt u controleren of **Set TargetResource** en **Test TargetResource** naar behoren.</span><span class="sxs-lookup"><span data-stu-id="da715-141">By changing the state of the machine and then rerunning DSC, you can verify that **Set-TargetResource** and **Test-TargetResource** function properly.</span></span> <span data-ttu-id="da715-142">Hier vindt u stappen die u moet uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="da715-142">Here are steps you should take:</span></span>
1.  <span data-ttu-id="da715-143">Beginnen met de resource niet in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="da715-143">Start with the resource not in the desired state.</span></span>
2.  <span data-ttu-id="da715-144">Configuratie uitvoeren met de bron</span><span class="sxs-lookup"><span data-stu-id="da715-144">Run configuration with your resource</span></span>
3.  <span data-ttu-id="da715-145">Controleer of **Test DscConfiguration** retourneert True</span><span class="sxs-lookup"><span data-stu-id="da715-145">Verify **Test-DscConfiguration** returns True</span></span>
4.  <span data-ttu-id="da715-146">Het geconfigureerde item om te worden uit de gewenste status wijzigen</span><span class="sxs-lookup"><span data-stu-id="da715-146">Modify the configured item to be out of the desired state</span></span>
5.  <span data-ttu-id="da715-147">Controleer of **Test DscConfiguration** retourneert onwaar Hier volgt een voorbeeld van een concrete Resourcegebruik register:</span><span class="sxs-lookup"><span data-stu-id="da715-147">Verify **Test-DscConfiguration** returns false Here’s a more concrete example using Registry resource:</span></span>
1.  <span data-ttu-id="da715-148">Beginnen met de registersleutel niet in de gewenste status</span><span class="sxs-lookup"><span data-stu-id="da715-148">Start with registry key not in the desired state</span></span>
2.  <span data-ttu-id="da715-149">Voer **Start DscConfiguration** met een configuratie wilt plaatsen in de gewenste status en controleer of deze is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="da715-149">Run **Start-DscConfiguration** with a configuration to put it in the desired state and verify it passes.</span></span>
3.  <span data-ttu-id="da715-150">Voer **Test DscConfiguration** en controleer of wordt true geretourneerd</span><span class="sxs-lookup"><span data-stu-id="da715-150">Run **Test-DscConfiguration** and verify it returns true</span></span>
4.  <span data-ttu-id="da715-151">De waarde van de sleutel wijzigen zodat deze zich niet in de gewenste status</span><span class="sxs-lookup"><span data-stu-id="da715-151">Modify the value of the key so that it is not in the desired state</span></span>
5.  <span data-ttu-id="da715-152">Voer **Test DscConfiguration** en controleer of het resultaat is false</span><span class="sxs-lookup"><span data-stu-id="da715-152">Run **Test-DscConfiguration** and verify it returns false</span></span>
6.  <span data-ttu-id="da715-153">Get-TargetResource functionaliteit is geverifieerd met behulp van Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="da715-153">Get-TargetResource functionality was verified using Get-DscConfiguration</span></span>

<span data-ttu-id="da715-154">Details van de huidige status van de resource moet worden geretourneerd door Get-TargetResource.</span><span class="sxs-lookup"><span data-stu-id="da715-154">Get-TargetResource should return details of the current state of the resource.</span></span> <span data-ttu-id="da715-155">Zorg ervoor dat deze te testen op aanroepen van Get-DscConfiguration na het toepassen van de configuratie en te verifiëren dat uitvoer correct de huidige status van de machine weerspiegelt.</span><span class="sxs-lookup"><span data-stu-id="da715-155">Make sure to test it by calling Get-DscConfiguration after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="da715-156">Het is belangrijk afzonderlijk testen omdat eventuele problemen op dit gebied wordt niet weergegeven bij het aanroepen van Start DscConfiguration.</span><span class="sxs-lookup"><span data-stu-id="da715-156">It's important to test it separately, since any issues in this area won't appear when calling Start-DscConfiguration.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="da715-157">Roep **Get/Set/Test-TargetResource** rechtstreeks fungeert</span><span class="sxs-lookup"><span data-stu-id="da715-157">Call **Get/Set/Test-TargetResource** functions directly</span></span> ##

<span data-ttu-id="da715-158">Zorg ervoor dat u testen de **Get/Set/Test-TargetResource** functies die zijn geïmplementeerd in de bron door ze rechtstreeks aanroepen en verifiëren dat ze werken zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="da715-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="da715-159">Controleren of de complete **Start DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="da715-159">Verify End to End using **Start-DscConfiguration**</span></span> ##

<span data-ttu-id="da715-160">Testen **Get/Set/Test-TargetResource** functies door het aanroepen van deze rechtstreeks is belangrijk, maar niet alle problemen op deze manier worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="da715-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="da715-161">U moet zich richten aanzienlijk deel van uw tests over het gebruik van **Start DscConfiguration** of de pull-server.</span><span class="sxs-lookup"><span data-stu-id="da715-161">You should focus significant part of your testing on using **Start-DscConfiguration** or the pull server.</span></span> <span data-ttu-id="da715-162">Dit is in feite hoe gebruikers de resource, zodat de betekenis van dit type tests Onderschat niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da715-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="da715-163">Mogelijke typen problemen:</span><span class="sxs-lookup"><span data-stu-id="da715-163">Possible types of issues:</span></span>
- <span data-ttu-id="da715-164">Referentie/sessie mogelijk anders werken omdat de DSC-agent wordt uitgevoerd als een service.</span><span class="sxs-lookup"><span data-stu-id="da715-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="da715-165">Zorg ervoor dat alle functies hier complete testen.</span><span class="sxs-lookup"><span data-stu-id="da715-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="da715-166">Fouten uitvoeren door **Start DscConfiguration** mogelijk anders uit dan bij het aanroepen van de **Set TargetResource** rechtstreeks werken.</span><span class="sxs-lookup"><span data-stu-id="da715-166">Errors output by **Start-DscConfiguration** may be different than those displayed when calling the **Set-TargetResource** function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="da715-167">Ondersteunde platforms voor test-compatibiliteit van alle DSC</span><span class="sxs-lookup"><span data-stu-id="da715-167">Test compatability on all DSC supported platforms</span></span> ##
<span data-ttu-id="da715-168">Resource moet werken op alle platforms van DSC ondersteund (Windows Server 2008 R2 en nieuwer).</span><span class="sxs-lookup"><span data-stu-id="da715-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="da715-169">De meest recente WMF (Windows Management Framework) installeren op uw besturingssysteem naar de nieuwste versie van DSC.</span><span class="sxs-lookup"><span data-stu-id="da715-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="da715-170">Als de bron aan het ontwerp niet op sommige van deze platformen werkt, kan een specifiek foutbericht moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="da715-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="da715-171">Controleer ook of dat de resource controleert of u verbinding maakt met cmdlets aanwezig op bepaalde machine zijn.</span><span class="sxs-lookup"><span data-stu-id="da715-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="da715-172">Windows Server 2012 toegevoegd een groot aantal nieuwe cmdlets die niet beschikbaar op Windows Server 2008 R2, zelfs met WMF is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="da715-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="da715-173">Controleer of op Windows-Client (indien van toepassing)</span><span class="sxs-lookup"><span data-stu-id="da715-173">Verify on Windows Client (if applicable)</span></span> ##
<span data-ttu-id="da715-174">Een zeer gangbaar gat in de test controleert de resource alleen op serverversies van Windows.</span><span class="sxs-lookup"><span data-stu-id="da715-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="da715-175">Veel resources ook zijn ontworpen om te werken op Client-SKU's, zodat als die true in het geval is, vergeet niet om deze te testen op deze platforms ook.</span><span class="sxs-lookup"><span data-stu-id="da715-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>
## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="da715-176">Get-DSCResource geeft een lijst van de resource</span><span class="sxs-lookup"><span data-stu-id="da715-176">Get-DSCResource lists the resource</span></span> ##
<span data-ttu-id="da715-177">Na implementatie van de module, moet aanroepen van Get-DscResource aanbieden uw resource onder andere als gevolg hiervan.</span><span class="sxs-lookup"><span data-stu-id="da715-177">After deploying the module, calling Get-DscResource should list your resource among others as a result.</span></span> <span data-ttu-id="da715-178">Als u uw resource in de lijst vinden kunt, controleert u dat bestand schema.mof voor die bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="da715-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>
## <a name="resource-module-contains-examples"></a><span data-ttu-id="da715-179">Resource-module bevat voorbeelden</span><span class="sxs-lookup"><span data-stu-id="da715-179">Resource module contains examples</span></span> ##
<span data-ttu-id="da715-180">Maken kwaliteitsvoorbeelden waarmee anderen te begrijpen hoe deze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="da715-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="da715-181">Dit is essentieel, vooral omdat voorbeeldcode als documentatie worden beschouwd door veel gebruikers.</span><span class="sxs-lookup"><span data-stu-id="da715-181">This is crucial, especially since many users treat sample code as documentation.</span></span>
- <span data-ttu-id="da715-182">Eerst moet u de voorbeelden die opgenomen met de module – minimaal worden bepalen, dient u belangrijkste gebruiksvoorbeelden omvatten voor uw resource:</span><span class="sxs-lookup"><span data-stu-id="da715-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="da715-183">Als uw module verschillende bronnen die nodig is om samen te werken voor een end-to-end-scenario bevat, is de elementaire end-to-end-voorbeeld in het ideale geval eerste.</span><span class="sxs-lookup"><span data-stu-id="da715-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="da715-184">De eerste voorbeelden moet zeer eenvoudig--het aan de slag met uw resources in kleine beheerbare segmenten (bijvoorbeeld een nieuwe VHD maken)</span><span class="sxs-lookup"><span data-stu-id="da715-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="da715-185">Opeenvolgende voorbeelden moeten bouwen in deze voorbeelden (bijvoorbeeld een virtuele machine maken vanaf een VHD, verwijderen van de virtuele machine, VM wijzigen) en weergeven van geavanceerde functionaliteit (bv. maken van een virtuele machine met dynamisch geheugen)</span><span class="sxs-lookup"><span data-stu-id="da715-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="da715-186">Voorbeeldconfiguraties parameters moeten worden gebruikt (alle waarden als parameters voor de configuratie moeten worden doorgegeven en er mag geen waarden hardcoded):</span><span class="sxs-lookup"><span data-stu-id="da715-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
}
```
- <span data-ttu-id="da715-187">Het is raadzaam om op te nemen (opmerkingen uitgaand) voorbeeld van hoe u de configuratie met de werkelijke waarden aan het einde van het voorbeeldscript niet aanroepen.</span><span class="sxs-lookup"><span data-stu-id="da715-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
<span data-ttu-id="da715-188">Bijvoorbeeld, in de bovenstaande configuratie is het niet altijd duidelijk dat de beste manier om op te geven UserAgent is:</span><span class="sxs-lookup"><span data-stu-id="da715-188">For example, in the configuration above it isn't neccessarily obvious that the best way to specify UserAgent is:</span></span>

<span data-ttu-id="da715-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Een opmerking kan in dat geval verduidelijken dat de beoogde uitvoering van de configuratie:</span><span class="sxs-lookup"><span data-stu-id="da715-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>
```
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```
- <span data-ttu-id="da715-190">Elke bijvoorbeeld, een korte beschrijving waarin wordt uitgelegd wat het doet en de betekenis van de parameters te schrijven.</span><span class="sxs-lookup"><span data-stu-id="da715-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="da715-191">Zorg ervoor dat voorbeelden hebben betrekking op de meeste belangrijke scenario's voor uw resource en als er niets ontbreekt, Controleer of ze alle uitvoeren machine in de gewenste status geplaatst.</span><span class="sxs-lookup"><span data-stu-id="da715-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="da715-192">Foutberichten zijn gemakkelijk te begrijpen en oplossen van problemen met gebruikers helpen</span><span class="sxs-lookup"><span data-stu-id="da715-192">Error messages are easy to understand and help users solve problems</span></span> ##
<span data-ttu-id="da715-193">Goede foutberichten worden:</span><span class="sxs-lookup"><span data-stu-id="da715-193">Good error messages should be:</span></span>
- <span data-ttu-id="da715-194">: Het grootste probleem met de foutberichten bestaat dat ze vaak niet bestaan, zorg er dus dat er zijn.</span><span class="sxs-lookup"><span data-stu-id="da715-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="da715-195">Gemakkelijker te begrijpen: menselijke leesbare, niet verborgen foutcodes</span><span class="sxs-lookup"><span data-stu-id="da715-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="da715-196">Nauwkeurig: Is beschreven wat er precies het probleem</span><span class="sxs-lookup"><span data-stu-id="da715-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="da715-197">Feitelijke: Advies hoe het probleem op te lossen</span><span class="sxs-lookup"><span data-stu-id="da715-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="da715-198">Beleefd: Niet schuldig gebruiker of maken ze van mening bent dat ongeldige Zorg ervoor dat u fouten in de complete scenario's controleren (met behulp van **Start DscConfiguration**), omdat ze van die afwijken kunnen bij het uitvoeren van functies van de resource direct geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="da715-198">Polite: Don’t blame user or make them feel bad Make sure you verify errors in End to End scenarios (using **Start-DscConfiguration**), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="da715-199">Berichten in het logboek zijn gemakkelijker te begrijpen en informatieve (inclusief-verbose,-ETW-logboeken en foutopsporing)</span><span class="sxs-lookup"><span data-stu-id="da715-199">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span> ##
<span data-ttu-id="da715-200">Zorg ervoor dat Logboeken die zijn gegenereerd door de resource gemakkelijk zijn te begrijpen en geef een waarde voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="da715-200">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="da715-201">Resources moeten uitvoer alle informatie die nuttig voor de gebruiker zijn kan, maar meer logboeken is niet altijd beter.</span><span class="sxs-lookup"><span data-stu-id="da715-201">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="da715-202">U moet voorkomen van redundantie en gegevens die niet worden uitgevoerd bieden aanvullende waarde – Maak iemand honderden logboekvermeldingen doorlopen om te kunnen vinden wat ze zoekt niet.</span><span class="sxs-lookup"><span data-stu-id="da715-202">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="da715-203">Er worden geen logboeken is natuurlijk niet een aanvaardbare oplossing voor dit probleem ofwel.</span><span class="sxs-lookup"><span data-stu-id="da715-203">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="da715-204">Bij het testen, moet u ook uitgebreide analyseren en foutopsporing van Logboeken (door het uitvoeren van **Start DscConfiguration** met-verbose en -switches op de juiste wijze voor foutopsporing), ook als ETW-Logboeken.</span><span class="sxs-lookup"><span data-stu-id="da715-204">When testing, you should also analyze verbose and debug logs (by running **Start-DscConfiguration** with –verbose and –debug switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="da715-205">Als u DSC ETW-Logboeken, gaat u naar Logboeken en open de volgende map: toepassingen en Services van Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="da715-205">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="da715-206">Er standaard worden operationele kanaal, maar zorg ervoor dat het inschakelen van analyse en foutopsporing kanalen voordat de configuratie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="da715-206">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="da715-207">U kunt de onderstaande script uitvoeren zodat analysen/Debug kanalen:</span><span class="sxs-lookup"><span data-stu-id="da715-207">To enable Analytic/Debug channels, you can execute script below:</span></span>
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug"
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}
Invoke-Expression $commandToExecute
```
## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="da715-208">Resource-implementatie bevat geen hardcoded paden</span><span class="sxs-lookup"><span data-stu-id="da715-208">Resource implementation does not contain hardcoded paths</span></span> ##
<span data-ttu-id="da715-209">Zorg ervoor dat er zijn geen paden vastgelegd in de resource-implementatie, met name als ze taal wordt ervan uitgegaan dat (en-us), of wanneer er systeemvariabelen die kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="da715-209">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="da715-210">Als de bron moet toegang tot bepaalde paden, omgevingsvariabelen gebruiken in plaats van hardcoderen wordt het pad, zoals deze afwijken op andere computers.</span><span class="sxs-lookup"><span data-stu-id="da715-210">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="da715-211">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="da715-211">Example:</span></span>

<span data-ttu-id="da715-212">In plaats van:</span><span class="sxs-lookup"><span data-stu-id="da715-212">Instead of:</span></span>
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
<span data-ttu-id="da715-213">U kunt schrijven:</span><span class="sxs-lookup"><span data-stu-id="da715-213">You can write:</span></span>
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```
## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="da715-214">Implementatie van resource bevatten geen gebruikersgegevens</span><span class="sxs-lookup"><span data-stu-id="da715-214">Resource implementation does not contain user information</span></span> ##
<span data-ttu-id="da715-215">Zorg ervoor dat er zijn geen e-namen, accountgegevens of namen van mensen in de code.</span><span class="sxs-lookup"><span data-stu-id="da715-215">Make sure there are no email names, account information, or names of people in the code.</span></span>
## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="da715-216">Resource is getest met de referenties geldig/ongeldig</span><span class="sxs-lookup"><span data-stu-id="da715-216">Resource was tested with valid/invalid credentials</span></span> ##
<span data-ttu-id="da715-217">Als de resource een referentie als parameter:</span><span class="sxs-lookup"><span data-stu-id="da715-217">If your resource takes a credential as parameter:</span></span>
- <span data-ttu-id="da715-218">Controleer of de resource-werkt als lokaal systeem (of het computeraccount voor de externe bronnen) geen toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="da715-218">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="da715-219">Controleer of de resource werkt met een referentie die is opgegeven voor u, ingesteld en testen</span><span class="sxs-lookup"><span data-stu-id="da715-219">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="da715-220">Als de bron naar shares, test u alle varianten die u ondersteunen wilt, zoals:</span><span class="sxs-lookup"><span data-stu-id="da715-220">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="da715-221">Standaard windows-bestandsshares.</span><span class="sxs-lookup"><span data-stu-id="da715-221">Standard windows shares.</span></span>
  - <span data-ttu-id="da715-222">DFS-shares.</span><span class="sxs-lookup"><span data-stu-id="da715-222">DFS shares.</span></span>
  - <span data-ttu-id="da715-223">SAMBA-shares (als u ondersteuning voor Linux.)</span><span class="sxs-lookup"><span data-stu-id="da715-223">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="da715-224">Resource vereist geen interactieve invoer</span><span class="sxs-lookup"><span data-stu-id="da715-224">Resource does not require interactive input</span></span> ##
<span data-ttu-id="da715-225">**Get/Set/Test-TargetResource** functies automatisch moet worden uitgevoerd en voor gebruikers in elk stadium van de uitvoering van de invoer niet opgeschort (bv. Gebruik geen **Get-Credential** binnen deze functies).</span><span class="sxs-lookup"><span data-stu-id="da715-225">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use **Get-Credential** inside these functions).</span></span> <span data-ttu-id="da715-226">Als u leveren de invoer van gebruiker wilt, moet u deze doorgeven aan de configuratie als parameter tijdens de compilatiefase.</span><span class="sxs-lookup"><span data-stu-id="da715-226">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>
## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="da715-227">Resourcefunctionaliteit is uitgebreid getest.</span><span class="sxs-lookup"><span data-stu-id="da715-227">Resource functionality was thoroughly tested</span></span> ##
<span data-ttu-id="da715-228">Deze controlelijst bevat de items die zijn belangrijk om te worden getest en/of vaak zijn gemist.</span><span class="sxs-lookup"><span data-stu-id="da715-228">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="da715-229">Er zijn bunch van tests, hoofdzakelijk functionele die zijn die specifiek zijn voor de resource die u wilt testen en niet hier worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="da715-229">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="da715-230">Vergeet niet over negatieve testcases.</span><span class="sxs-lookup"><span data-stu-id="da715-230">Don’t forget about negative test cases.</span></span>
## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="da715-231">Kunt u beter: Resource-module bevat de map Tests met ResourceDesignerTests.ps1 script</span><span class="sxs-lookup"><span data-stu-id="da715-231">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span> ##
<span data-ttu-id="da715-232">Het is raadzaam map 'Tests' create binnen bronmodule, ResourceDesignerTests.ps1-bestand maken en toevoegen van testen met behulp van **Test xDscResource** en **Test xDscSchema** voor alle resources in bepaalde module.</span><span class="sxs-lookup"><span data-stu-id="da715-232">It’s a good practice to create folder “Tests” inside resource module, create ResourceDesignerTests.ps1 file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="da715-233">Op deze manier kunt u snel schema's van alle resources uit het opgegeven modules en voert u een sanity controleren voordat u publiceert valideren.</span><span class="sxs-lookup"><span data-stu-id="da715-233">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="da715-234">XRemoteFile, kan ResourceTests.ps1 Zoek net zo eenvoudig als:</span><span class="sxs-lookup"><span data-stu-id="da715-234">For xRemoteFile, ResourceTests.ps1 could look as simple as:</span></span>
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```
##<a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="da715-235">Kunt u beter: resourcemap resource designer script voor het genereren van schema ## bevat</span><span class="sxs-lookup"><span data-stu-id="da715-235">Best practice: Resource folder contains resource designer script for generating schema##</span></span>
<span data-ttu-id="da715-236">Elke bron moet een resource designer script een mof-schema van de resource genereert bevatten.</span><span class="sxs-lookup"><span data-stu-id="da715-236">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="da715-237">Dit bestand moet worden geplaatst <ResourceName>\ResourceDesignerScripts en de naam genereren<ResourceName>Schema.ps1 voor xRemoteFile resource dit bestand GenerateXRemoteFileSchema.ps1 zou worden aangeroepen en bevat:</span><span class="sxs-lookup"><span data-stu-id="da715-237">This file should be placed in <ResourceName>\ResourceDesignerScripts and be named Generate<ResourceName>Schema.ps1 For xRemoteFile resource this file would be called GenerateXRemoteFileSchema.ps1 and contain:</span></span>
```powershell
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.'
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile
```
## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="da715-238">Kunt u beter: bron - whatif wordt ondersteund</span><span class="sxs-lookup"><span data-stu-id="da715-238">Best practice: Resource supports -whatif</span></span> ##
<span data-ttu-id="da715-239">Als uw resource 'gevaarlijke' bewerkingen uitvoert, is het raadzaam om - whatif-functionaliteit te implementeren.</span><span class="sxs-lookup"><span data-stu-id="da715-239">If your resource is performing “dangerous” operations, it’s a good practice to implement -whatif functionality.</span></span> <span data-ttu-id="da715-240">Nadat deze voltooid, zorg er dan voor dat bewerkingen waarvoor er gebeuren zou als de opdracht is uitgevoerd zonder whatif switch hierin wordt beschreven whatif uitvoer.</span><span class="sxs-lookup"><span data-stu-id="da715-240">After it’s done, make sure that whatif output correctly describes operations which would happen if command was executed without whatif switch.</span></span>
<span data-ttu-id="da715-241">Controleer ook of bewerkingen wordt niet uitgevoerd (de status van het knooppunt worden niet gewijzigd) wanneer-whatif switch aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="da715-241">Also, verify that operations does not execute (no changes to the node’s state are made) when –whatif switch is present.</span></span>
<span data-ttu-id="da715-242">Bijvoorbeeld, Stel dat we bestandsbron wilt testen.</span><span class="sxs-lookup"><span data-stu-id="da715-242">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="da715-243">Hieronder vindt u eenvoudige configuratie gemaakt van bestand 'test.txt' met inhoud 'test':</span><span class="sxs-lookup"><span data-stu-id="da715-243">Below is simple configuration which creates file “test.txt” with contents “test”:</span></span>
```powershell
configuration config
{
    node localhost
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config
```
<span data-ttu-id="da715-244">Als wij compileren en vervolgens de configuratie met de schakeloptie-whatif wordt uitgevoerd, is de uitvoer vertellen ons precies wat er gebeurt wanneer we de configuratie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="da715-244">If we compile and then execute the configuration with the –whatif switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="da715-245">Tot maar is niet worden uitgevoerd door de configuratie zelf (test.txt bestand is niet gemaakt).</span><span class="sxs-lookup"><span data-stu-id="da715-245">The configuration itself however was not executed (test.txt file was not created).</span></span>
```powershell
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

<span data-ttu-id="da715-246">Deze lijst is niet volledig, maar deze bevat veel belangrijke problemen die kunnen worden aangetroffen tijdens het ontwerpen, ontwikkelen en testen van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="da715-246">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>