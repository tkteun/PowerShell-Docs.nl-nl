---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Controlelijst voor het ontwerpen van resource
description: Dit artikel bevat een controle lijst met aanbevolen procedures die moeten worden gebruikt bij het ontwerpen van een nieuwe DSC-resource.
ms.openlocfilehash: 5b618511f730c80104620c84e693c13ae4f536ac
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656340"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="ea149-104">Controlelijst voor het ontwerpen van resource</span><span class="sxs-lookup"><span data-stu-id="ea149-104">Resource authoring checklist</span></span>

<span data-ttu-id="ea149-105">Deze controle lijst bevat de aanbevolen procedures voor het ontwerpen van een nieuwe DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="ea149-105">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="ea149-106">De resource module bevat het. psd1-bestand en het schema. MOF voor elke resource</span><span class="sxs-lookup"><span data-stu-id="ea149-106">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="ea149-107">Controleer of de resource de juiste structuur heeft en alle vereiste bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="ea149-107">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="ea149-108">Elke resource module moet een. psd1-bestand bevatten en elke niet-samengestelde resource moet het bestand schema. MOF hebben.</span><span class="sxs-lookup"><span data-stu-id="ea149-108">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span>
<span data-ttu-id="ea149-109">Resources die geen schema bevatten, worden niet weer gegeven door `Get-DscResource` en gebruikers kunnen de IntelliSense niet gebruiken bij het schrijven van code voor die modules in ISE.</span><span class="sxs-lookup"><span data-stu-id="ea149-109">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the IntelliSense when writing code against those modules in ISE.</span></span> <span data-ttu-id="ea149-110">De directory-structuur voor de resource xRemoteFile, die deel uitmaakt van de [xPSDesiredStateConfiguration-resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="ea149-110">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

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

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="ea149-111">De resource en het schema zijn juist</span><span class="sxs-lookup"><span data-stu-id="ea149-111">Resource and schema are correct</span></span>

<span data-ttu-id="ea149-112">Controleer het resource schema `*.schema.mof` bestand ().</span><span class="sxs-lookup"><span data-stu-id="ea149-112">Verify the resource schema (`*.schema.mof`) file.</span></span> <span data-ttu-id="ea149-113">U kunt de [DSC resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) gebruiken om uw schema te ontwikkelen en te testen.</span><span class="sxs-lookup"><span data-stu-id="ea149-113">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span> <span data-ttu-id="ea149-114">Zorg voor het volgende:</span><span class="sxs-lookup"><span data-stu-id="ea149-114">Make sure that:</span></span>

- <span data-ttu-id="ea149-115">Eigenschaps typen zijn juist (bijvoorbeeld: geen teken reeks gebruiken voor eigenschappen die numerieke waarden accepteren, moet u in plaats daarvan UInt32 of andere numerieke typen gebruiken)</span><span class="sxs-lookup"><span data-stu-id="ea149-115">Property types are correct (e.g. don't use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="ea149-116">Eigenschaps kenmerken zijn correct opgegeven als: ([sleutel], [vereist], [schrijven], [lezen])</span><span class="sxs-lookup"><span data-stu-id="ea149-116">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="ea149-117">Ten minste één para meter in het schema moet worden gemarkeerd als [sleutel]</span><span class="sxs-lookup"><span data-stu-id="ea149-117">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="ea149-118">de eigenschap [Read] bestaat niet samen met een van de volgende waarden: [vereist], [sleutel], [schrijven]</span><span class="sxs-lookup"><span data-stu-id="ea149-118">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="ea149-119">Als er meerdere kwalificaties zijn opgegeven, behalve [lezen], heeft [sleutel] prioriteit</span><span class="sxs-lookup"><span data-stu-id="ea149-119">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="ea149-120">Als [write] en [required] zijn opgegeven, is [required] prioriteit</span><span class="sxs-lookup"><span data-stu-id="ea149-120">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="ea149-121">ValueMap wordt opgegeven, waar van toepassing voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ea149-121">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="ea149-122">Beschrijvende naam is opgegeven en wordt bevestigd aan DSC-naamgevings regels</span><span class="sxs-lookup"><span data-stu-id="ea149-122">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="ea149-123">Voorbeeld: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="ea149-123">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="ea149-124">Elk veld heeft een zinvolle beschrijving.</span><span class="sxs-lookup"><span data-stu-id="ea149-124">Every field has meaningful description.</span></span> <span data-ttu-id="ea149-125">De Power shell GitHub-opslag plaats heeft goede voor beelden, zoals het [. schema. MOF voor xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="ea149-125">The PowerShell GitHub repository has good examples, such as the [.schema.mof for xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="ea149-126">Daarnaast moet u `Test-xDscResource` `Test-xDscSchema` cmdlets van [DSC resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) gebruiken om automatisch de resource en het schema te controleren:</span><span class="sxs-lookup"><span data-stu-id="ea149-126">Additionally, you should use `Test-xDscResource` and `Test-xDscSchema` cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="ea149-127">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ea149-127">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="ea149-128">Resource belasting zonder fouten</span><span class="sxs-lookup"><span data-stu-id="ea149-128">Resource loads without errors</span></span>

<span data-ttu-id="ea149-129">Controleer of de resource module kan worden geladen.</span><span class="sxs-lookup"><span data-stu-id="ea149-129">Check whether the resource module can be successfully loaded.</span></span> <span data-ttu-id="ea149-130">Dit kan hand matig worden bereikt door uit `Import-Module <resource_module> -force` te voeren en te bevestigen dat er geen fouten zijn opgetreden of door test Automation te schrijven.</span><span class="sxs-lookup"><span data-stu-id="ea149-130">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="ea149-131">In het geval van de laatste kunt u deze structuur in uw test case volgen:</span><span class="sxs-lookup"><span data-stu-id="ea149-131">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="ea149-132">De resource is in het positieve geval idempotent</span><span class="sxs-lookup"><span data-stu-id="ea149-132">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="ea149-133">Een van de fundamentele kenmerken van DSC-resources is idempotence.</span><span class="sxs-lookup"><span data-stu-id="ea149-133">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="ea149-134">Het betekent dat het Toep assen van een DSC-configuratie met die resource meerdere keren altijd hetzelfde resultaat oplevert.</span><span class="sxs-lookup"><span data-stu-id="ea149-134">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="ea149-135">Als we bijvoorbeeld een configuratie maken die de volgende bestands resource bevat:</span><span class="sxs-lookup"><span data-stu-id="ea149-135">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="ea149-136">Nadat de toepassing voor de eerste keer is toegepast, moet de bestands test.txt worden weer gegeven in de `C:\test` map.</span><span class="sxs-lookup"><span data-stu-id="ea149-136">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="ea149-137">Volgende uitvoeringen van dezelfde configuratie mogen echter niet de status van de machine wijzigen (bijvoorbeeld, er moeten geen kopieën van het `test.txt` bestand worden gemaakt).</span><span class="sxs-lookup"><span data-stu-id="ea149-137">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span> <span data-ttu-id="ea149-138">Om ervoor te zorgen dat een resource idempotent is, kunt u herhaaldelijk aanroepen `Set-TargetResource` Wanneer u de resource rechtstreeks test of `Start-DscConfiguration` meerdere keren aanroept wanneer u de test beëindigt.</span><span class="sxs-lookup"><span data-stu-id="ea149-138">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="ea149-139">Het resultaat moet hetzelfde zijn na elke uitvoering.</span><span class="sxs-lookup"><span data-stu-id="ea149-139">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="ea149-140">Scenario voor het aanpassen van gebruikers testen</span><span class="sxs-lookup"><span data-stu-id="ea149-140">Test user modification scenario</span></span>

<span data-ttu-id="ea149-141">Door de status van de machine te wijzigen en DSC opnieuw uit te voeren, kunt u controleren of `Set-TargetResource` en `Test-TargetResource` goed functioneren.</span><span class="sxs-lookup"><span data-stu-id="ea149-141">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="ea149-142">Hier volgen de stappen die u moet uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="ea149-142">Here are steps you should take:</span></span>

1. <span data-ttu-id="ea149-143">Begin met de resource en niet de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="ea149-143">Start with the resource not in the desired state.</span></span>
1. <span data-ttu-id="ea149-144">Configuratie uitvoeren met uw resource</span><span class="sxs-lookup"><span data-stu-id="ea149-144">Run configuration with your resource</span></span>
1. <span data-ttu-id="ea149-145">Verify `Test-DscConfiguration` retourneert True</span><span class="sxs-lookup"><span data-stu-id="ea149-145">Verify `Test-DscConfiguration` returns True</span></span>
1. <span data-ttu-id="ea149-146">Wijzig het geconfigureerde item in de gewenste status</span><span class="sxs-lookup"><span data-stu-id="ea149-146">Modify the configured item to be out of the desired state</span></span>
1. <span data-ttu-id="ea149-147">Verify `Test-DscConfiguration` retourneert False</span><span class="sxs-lookup"><span data-stu-id="ea149-147">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="ea149-148">Hier volgt een meer concrete voor beeld van het gebruik van een register resource:</span><span class="sxs-lookup"><span data-stu-id="ea149-148">Here's a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="ea149-149">Beginnen met de register sleutel heeft niet de gewenste status</span><span class="sxs-lookup"><span data-stu-id="ea149-149">Start with registry key not in the desired state</span></span>
1. <span data-ttu-id="ea149-150">Voer uit `Start-DscConfiguration` met een configuratie om deze in de gewenste staat te zetten en controleer of deze wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="ea149-150">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
1. <span data-ttu-id="ea149-151">Uitvoeren `Test-DscConfiguration` en controleren of het resultaat True retourneert</span><span class="sxs-lookup"><span data-stu-id="ea149-151">Run `Test-DscConfiguration` and verify it returns true</span></span>
1. <span data-ttu-id="ea149-152">Wijzig de waarde van de sleutel zodat deze niet de gewenste status heeft</span><span class="sxs-lookup"><span data-stu-id="ea149-152">Modify the value of the key so that it is not in the desired state</span></span>
1. <span data-ttu-id="ea149-153">Uitvoeren `Test-DscConfiguration` en controleren of retourneert False</span><span class="sxs-lookup"><span data-stu-id="ea149-153">Run `Test-DscConfiguration` and verify it returns false</span></span>
1. <span data-ttu-id="ea149-154">`Get-TargetResource` de functionaliteit is geverifieerd met `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="ea149-154">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="ea149-155">`Get-TargetResource` de details van de huidige status van de resource moeten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ea149-155">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="ea149-156">Zorg ervoor dat u deze test door aan te roepen `Get-DscConfiguration` nadat u de configuratie hebt toegepast en controleer of de uitvoer correct overeenkomt met de huidige status van de machine.</span><span class="sxs-lookup"><span data-stu-id="ea149-156">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="ea149-157">Het is belang rijk om deze afzonderlijk te testen, omdat eventuele problemen in dit gebied niet worden weer gegeven wanneer u aanroept `Start-DscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ea149-157">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="ea149-158">**Get/set/test-TargetResource-** functies rechtstreeks aanroepen</span><span class="sxs-lookup"><span data-stu-id="ea149-158">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="ea149-159">Zorg ervoor dat u de `Get/Set/Test-TargetResource` functies in uw Resource test door deze rechtstreeks aan te roepen en te controleren of ze werken zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="ea149-159">Make sure you test the `Get/Set/Test-TargetResource` functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="ea149-160">End-to-end controleren met behulp van Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ea149-160">Verify End to End using Start-DscConfiguration</span></span>

<span data-ttu-id="ea149-161">`Get/Set/Test-TargetResource`Het is belang rijk om functies te testen door ze rechtstreeks aan te roepen, maar niet alle problemen worden op deze manier gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="ea149-161">Testing `Get/Set/Test-TargetResource` functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="ea149-162">Het is belang rijk dat u zich richt op `Start-DscConfiguration` het gebruik of de pull-server.</span><span class="sxs-lookup"><span data-stu-id="ea149-162">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="ea149-163">Dit is in feite hoe gebruikers de resource gaan gebruiken, dus te laag inschatten de significantie van dit type tests niet op.</span><span class="sxs-lookup"><span data-stu-id="ea149-163">In fact, this is how users will use the resource, so don't underestimate the significance of this type of tests.</span></span> <span data-ttu-id="ea149-164">Mogelijke typen problemen:</span><span class="sxs-lookup"><span data-stu-id="ea149-164">Possible types of issues:</span></span>

- <span data-ttu-id="ea149-165">Referentie/sessie kan anders werken omdat de DSC-agent wordt uitgevoerd als een service.</span><span class="sxs-lookup"><span data-stu-id="ea149-165">Credential/Session may behave differently because the DSC agent runs as a service.</span></span> <span data-ttu-id="ea149-166">Zorg ervoor dat u alle functies hier kunt testen.</span><span class="sxs-lookup"><span data-stu-id="ea149-166">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="ea149-167">Het resultaat van `Start-DscConfiguration` de uitvoer door kan afwijken van de fouten die worden weer gegeven wanneer u de `Set-TargetResource` functie rechtstreeks aanroept.</span><span class="sxs-lookup"><span data-stu-id="ea149-167">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a><span data-ttu-id="ea149-168">Test compatibiliteit op alle door DSC ondersteunde platforms</span><span class="sxs-lookup"><span data-stu-id="ea149-168">Test compatibility on all DSC supported platforms</span></span>

<span data-ttu-id="ea149-169">De resource moet werken op alle door DSC ondersteunde platforms (Windows Server 2008 R2 en nieuwer).</span><span class="sxs-lookup"><span data-stu-id="ea149-169">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="ea149-170">Installeer de meest recente WMF (Windows Management Framework) in uw besturings systeem om de meest recente versie van DSC op te halen.</span><span class="sxs-lookup"><span data-stu-id="ea149-170">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="ea149-171">Als uw resource niet op een aantal van deze platformen werkt, is het mogelijk dat er een specifiek fout bericht wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ea149-171">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="ea149-172">Zorg er ook voor dat uw resource controleert of cmdlets die u aanroept, aanwezig zijn op een bepaalde computer.</span><span class="sxs-lookup"><span data-stu-id="ea149-172">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="ea149-173">Windows Server 2012 heeft een groot aantal nieuwe cmdlets toegevoegd die niet beschikbaar zijn in Windows Server 2008R2, zelfs niet als WMF is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ea149-173">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="ea149-174">Controleren op Windows-client (indien van toepassing)</span><span class="sxs-lookup"><span data-stu-id="ea149-174">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="ea149-175">Een zeer veelvoorkomende test hiaat is het verifiëren van de bron alleen op Server versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="ea149-175">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="ea149-176">Veel resources zijn ook ontworpen om te werken met client-Sku's, dus als dat in uw geval waar is, vergeet dan niet om deze ook op deze platforms te testen.</span><span class="sxs-lookup"><span data-stu-id="ea149-176">Many resources are also designed to work on Client SKUs, so if that's true in your case, don't forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="ea149-177">Get-DSCResource bevat de resource</span><span class="sxs-lookup"><span data-stu-id="ea149-177">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="ea149-178">Nadat u de module hebt geïmplementeerd, `Get-DscResource` moet u de resource onder andere aanroepen als gevolg van een lijst.</span><span class="sxs-lookup"><span data-stu-id="ea149-178">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="ea149-179">Als u uw resource niet kunt vinden in de lijst, moet u ervoor zorgen dat het schema. MOF-bestand voor die bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="ea149-179">If you can't find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="ea149-180">Resource module bevat voor beelden</span><span class="sxs-lookup"><span data-stu-id="ea149-180">Resource module contains examples</span></span>

<span data-ttu-id="ea149-181">Het maken van kwaliteits voorbeelden waarmee anderen inzicht krijgen in hoe u deze kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ea149-181">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="ea149-182">Dit is cruciaal, vooral omdat veel gebruikers voorbeeld code behandelen als documentatie.</span><span class="sxs-lookup"><span data-stu-id="ea149-182">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="ea149-183">Eerst moet u de voor beelden bepalen die in de module worden opgenomen. u moet mini maal de meest belang rijke use cases voor uw resource best rijken:</span><span class="sxs-lookup"><span data-stu-id="ea149-183">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="ea149-184">Als uw module verschillende resources bevat die moeten samen werken voor een end-to-end-scenario, zou het Basic-end-to-end-voor beeld het eerst in het ideale geval moeten zijn.</span><span class="sxs-lookup"><span data-stu-id="ea149-184">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="ea149-185">De eerste voor beelden zijn heel eenvoudig: hoe u aan de slag kunt gaan met uw resources in kleine, beheersbare segmenten (bijvoorbeeld het maken van een nieuwe VHD)</span><span class="sxs-lookup"><span data-stu-id="ea149-185">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="ea149-186">De volgende voor beelden moeten worden gebouwd op basis van deze voor beelden (bijvoorbeeld het maken van een VM van een VHD, het verwijderen van de VM, het wijzigen van de virtuele machine) en het weer geven van geavanceerde functionaliteit (bijvoorbeeld het maken van een virtuele machine met dynamisch geheugen)</span><span class="sxs-lookup"><span data-stu-id="ea149-186">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="ea149-187">Voorbeeld configuraties moeten worden para meters (alle waarden moeten worden door gegeven aan de configuratie als para meters en er mogen geen hardcoded waarden zijn):</span><span class="sxs-lookup"><span data-stu-id="ea149-187">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

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

- <span data-ttu-id="ea149-188">Het is een goed idee om een voor beeld van een invoeging van de configuratie met de werkelijke waarden aan het einde van het voorbeeld script uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ea149-188">It's a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span> <span data-ttu-id="ea149-189">Zo is in de configuratie hierboven niet nood zakelijk duidelijk dat de beste manier om agents op te geven:</span><span class="sxs-lookup"><span data-stu-id="ea149-189">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="ea149-190">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In dat geval kan een opmerking de beoogde uitvoering van de configuratie verduidelijken:</span><span class="sxs-lookup"><span data-stu-id="ea149-190">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

```powershell
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```

- <span data-ttu-id="ea149-191">Voor elk voor beeld moet u een korte beschrijving schrijven waarin wordt uitgelegd wat het doet en wat de betekenis van de para meters zijn.</span><span class="sxs-lookup"><span data-stu-id="ea149-191">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="ea149-192">Zorg ervoor dat de voor beelden de meeste belang rijke scenario's voor uw resource dekken. als er niets mis gaat, controleert u of ze alle computers in de gewenste status uitvoeren en plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ea149-192">Make sure examples cover most the important scenarios for your resource and if there's nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="ea149-193">Fout berichten zijn eenvoudig te begrijpen en helpen gebruikers problemen op te lossen</span><span class="sxs-lookup"><span data-stu-id="ea149-193">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="ea149-194">Goede fout berichten moeten zijn:</span><span class="sxs-lookup"><span data-stu-id="ea149-194">Good error messages should be:</span></span>

- <span data-ttu-id="ea149-195">Er is sprake van het grootste probleem met fout berichten dat ze vaak niet bestaan, dus zorg ervoor dat ze daar zijn.</span><span class="sxs-lookup"><span data-stu-id="ea149-195">There: The biggest problem with error messages is that they often don't exist, so make sure they are there.</span></span>
- <span data-ttu-id="ea149-196">Eenvoudig te begrijpen: menselijk leesbaar, geen onduidelijke fout codes</span><span class="sxs-lookup"><span data-stu-id="ea149-196">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="ea149-197">Nauw keurig: beschrijven wat het probleem precies is</span><span class="sxs-lookup"><span data-stu-id="ea149-197">Precise: Describe what's exactly the problem</span></span>
- <span data-ttu-id="ea149-198">Feitelijke: advies over het oplossen van het probleem</span><span class="sxs-lookup"><span data-stu-id="ea149-198">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="ea149-199">Vermoeden: liggen niet op de gebruiker of zorg ervoor dat ze slecht zijn</span><span class="sxs-lookup"><span data-stu-id="ea149-199">Polite: Don't blame user or make them feel bad</span></span>

<span data-ttu-id="ea149-200">Controleer of u fouten in end-to-end-scenario's controleert (met `Start-DscConfiguration` ), omdat deze kunnen verschillen van de waarden die worden geretourneerd bij het rechtstreeks uitvoeren van resource functies.</span><span class="sxs-lookup"><span data-stu-id="ea149-200">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="ea149-201">Logboek berichten zijn eenvoudig te begrijpen en info (inclusief – uitgebreid, fouten opsporen en ETW-Logboeken)</span><span class="sxs-lookup"><span data-stu-id="ea149-201">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="ea149-202">Zorg ervoor dat de logboeken die zijn gegenereerd door de resource eenvoudig te begrijpen zijn en waarde aan de gebruiker kunnen geven.</span><span class="sxs-lookup"><span data-stu-id="ea149-202">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span>
<span data-ttu-id="ea149-203">Resources moeten alle informatie uitvoeren die nuttig kan zijn voor de gebruiker, maar meer logboeken zijn niet altijd beter.</span><span class="sxs-lookup"><span data-stu-id="ea149-203">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="ea149-204">Vermijd het gebruik van redundantie en het uitvoeren van gegevens die geen extra waarde bieden: laat iemand niet meer dan honderden logboek vermeldingen bezoeken om te vinden wat ze zoeken.</span><span class="sxs-lookup"><span data-stu-id="ea149-204">You should avoid redundancy and outputting data which does not provide additional value – don't make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="ea149-205">Uiteraard is er geen logboeken die een geschikte oplossing voor dit probleem zijn.</span><span class="sxs-lookup"><span data-stu-id="ea149-205">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="ea149-206">Bij het testen moet u ook uitgebreide logboeken en fouten opsporen analyseren (door op de juiste wijze uit te voeren `Start-DscConfiguration` `–Verbose` en te `–Debug` scha kelen), evenals etw-Logboeken.</span><span class="sxs-lookup"><span data-stu-id="ea149-206">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="ea149-207">Als u DSC ETW-logboeken wilt weer geven, gaat u naar Logboeken en opent u de volgende map: toepassingen en services-micro soft-Windows-desired state Configuration.</span><span class="sxs-lookup"><span data-stu-id="ea149-207">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span> <span data-ttu-id="ea149-208">Standaard zal er een operationeel kanaal zijn, maar zorg ervoor dat u analytische en probleemoplossings kanalen inschakelt voordat u de configuratie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ea149-208">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span> <span data-ttu-id="ea149-209">Als u kanalen voor analyse en fout opsporing wilt inschakelen, kunt u hieronder een script uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="ea149-209">To enable Analytic/Debug channels, you can execute script below:</span></span>

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="ea149-210">De resource-implementatie bevat geen hardcoded paden</span><span class="sxs-lookup"><span data-stu-id="ea149-210">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="ea149-211">Zorg ervoor dat er geen hardcoded paden aanwezig zijn in de resource-implementatie, met name als er een taal (en-US) wordt gebruikt, of als er systeem variabelen zijn die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ea149-211">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span> <span data-ttu-id="ea149-212">Als uw resource toegang moet hebben tot specifieke paden, gebruikt u omgevings variabelen in plaats van hardcoding het pad, omdat het mogelijk op andere computers kan verschillen.</span><span class="sxs-lookup"><span data-stu-id="ea149-212">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="ea149-213">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ea149-213">Example:</span></span>

<span data-ttu-id="ea149-214">In plaats van:</span><span class="sxs-lookup"><span data-stu-id="ea149-214">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="ea149-215">U kunt schrijven:</span><span class="sxs-lookup"><span data-stu-id="ea149-215">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="ea149-216">De resource-implementatie bevat geen gebruikers gegevens</span><span class="sxs-lookup"><span data-stu-id="ea149-216">Resource implementation does not contain user information</span></span>

<span data-ttu-id="ea149-217">Zorg ervoor dat er geen e-mail namen, account gegevens of namen van personen in de code zijn.</span><span class="sxs-lookup"><span data-stu-id="ea149-217">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="ea149-218">De resource is getest met geldige/ongeldige referenties</span><span class="sxs-lookup"><span data-stu-id="ea149-218">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="ea149-219">Als de resource een referentie als para meter heeft:</span><span class="sxs-lookup"><span data-stu-id="ea149-219">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="ea149-220">Controleer of de resource werkt wanneer het lokale systeem (of het computer account voor externe bronnen) geen toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="ea149-220">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="ea149-221">Controleren of de resource werkt met een referentie die is opgegeven voor Get, set en test</span><span class="sxs-lookup"><span data-stu-id="ea149-221">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="ea149-222">Als uw resource toegang heeft tot shares, test u alle varianten die u nodig hebt om te ondersteunen, zoals:</span><span class="sxs-lookup"><span data-stu-id="ea149-222">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="ea149-223">Standaard Windows-shares.</span><span class="sxs-lookup"><span data-stu-id="ea149-223">Standard windows shares.</span></span>
  - <span data-ttu-id="ea149-224">DFS-shares.</span><span class="sxs-lookup"><span data-stu-id="ea149-224">DFS shares.</span></span>
  - <span data-ttu-id="ea149-225">SAMBA-shares (als u Linux wilt ondersteunen.)</span><span class="sxs-lookup"><span data-stu-id="ea149-225">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="ea149-226">Voor de resource is geen interactieve invoer vereist</span><span class="sxs-lookup"><span data-stu-id="ea149-226">Resource does not require interactive input</span></span>

<span data-ttu-id="ea149-227">`Get/Set/Test-TargetResource` functies moeten automatisch worden uitgevoerd en moeten niet wachten op invoer van de gebruiker tijdens een wille keurige fase (bijvoorbeeld omdat u niet `Get-Credential` in deze functies moet worden gebruikt).</span><span class="sxs-lookup"><span data-stu-id="ea149-227">`Get/Set/Test-TargetResource` functions should be executed automatically and must not wait for user's input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="ea149-228">Als u de invoer van de gebruiker moet opgeven, moet u deze door geven aan de configuratie als para meter tijdens de compilatie fase.</span><span class="sxs-lookup"><span data-stu-id="ea149-228">If you need to provide user's input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="ea149-229">De resource functionaliteit is uitgebreid getest</span><span class="sxs-lookup"><span data-stu-id="ea149-229">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="ea149-230">Deze controle lijst bevat items die belang rijk zijn om te worden getest en/of vaak ontbreekt.</span><span class="sxs-lookup"><span data-stu-id="ea149-230">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="ea149-231">Er is een aantal tests, voornamelijk functionele functies die specifiek zijn voor de resource die u wilt testen en die hier niet worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="ea149-231">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="ea149-232">Vergeet niet om te zien wat negatieve test cases zijn.</span><span class="sxs-lookup"><span data-stu-id="ea149-232">Don't forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="ea149-233">Best practice: de resource module bevat de map tests met ResourceDesignerTests.ps1 script</span><span class="sxs-lookup"><span data-stu-id="ea149-233">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="ea149-234">Het is een goed idee om de map ' tests ' te maken in de resource module, het bestand te maken `ResourceDesignerTests.ps1` en tests toe te voegen met `Test-xDscResource` en `Test-xDscSchema` voor alle resources in de betreffende module.</span><span class="sxs-lookup"><span data-stu-id="ea149-234">It's a good practice to create folder "Tests" inside resource module, create `ResourceDesignerTests.ps1` file and add tests using `Test-xDscResource` and `Test-xDscSchema` for all resources in given module.</span></span> <span data-ttu-id="ea149-235">Op deze manier kunt u snel schema's valideren van alle resources uit de opgegeven modules en een Sanity controleren voordat u publiceert.</span><span class="sxs-lookup"><span data-stu-id="ea149-235">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span> <span data-ttu-id="ea149-236">Voor xRemoteFile `ResourceTests.ps1` kan het er zo eenvoudig uitzien als:</span><span class="sxs-lookup"><span data-stu-id="ea149-236">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="ea149-237">Aanbevolen procedure: Resource ondersteunt-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ea149-237">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="ea149-238">Als uw resource ' gevaarlijk ' bewerkingen uitvoert, is het een goed idee om functionaliteit te implementeren `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ea149-238">If your resource is performing "dangerous" operations, it's a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="ea149-239">Nadat de bewerking is uitgevoerd, moet u ervoor zorgen dat uitvoer op de `-WhatIf` juiste wijze bewerkingen beschrijft die zouden gebeuren als de opdracht zonder switch is voltooid `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ea149-239">After it's done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span> <span data-ttu-id="ea149-240">Controleer ook of de bewerkingen niet worden uitgevoerd (er worden geen wijzigingen aangebracht in de status van het knoop punt) wanneer `–WhatIf` Switch aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="ea149-240">Also, verify that operations does not execute (no changes to the node's state are made) when `–WhatIf` switch is present.</span></span> <span data-ttu-id="ea149-241">Stel dat we de bestands resource testen.</span><span class="sxs-lookup"><span data-stu-id="ea149-241">For example, let's assume we are testing File resource.</span></span> <span data-ttu-id="ea149-242">Hieronder vindt u eenvoudige configuratie waarmee bestanden `test.txt` met de inhoud ' test ' worden gemaakt:</span><span class="sxs-lookup"><span data-stu-id="ea149-242">Below is simple configuration which creates file `test.txt` with contents "test":</span></span>

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

<span data-ttu-id="ea149-243">Als we de configuratie met de switch compileren en vervolgens uitvoeren `-WhatIf` , vertelt de uitvoer precies wat er zou gebeuren wanneer de configuratie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ea149-243">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="ea149-244">De configuratie zelf is echter niet uitgevoerd (het `test.txt` bestand is niet gemaakt).</span><span class="sxs-lookup"><span data-stu-id="ea149-244">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```Output
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

<span data-ttu-id="ea149-245">Deze lijst is niet volledig, maar hierin worden veel belang rijke problemen besproken die kunnen optreden tijdens het ontwerpen, ontwikkelen en testen van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="ea149-245">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
