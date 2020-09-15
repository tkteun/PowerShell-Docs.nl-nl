---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Controlelijst voor het ontwerpen van resource
ms.openlocfilehash: f21e2e8563880e0c10cf50b044e9c56ca09fe0fa
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217641"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="ce024-103">Controlelijst voor het ontwerpen van resource</span><span class="sxs-lookup"><span data-stu-id="ce024-103">Resource authoring checklist</span></span>

<span data-ttu-id="ce024-104">Deze controle lijst bevat de aanbevolen procedures voor het ontwerpen van een nieuwe DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="ce024-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="ce024-105">De resource module bevat het. psd1-bestand en het schema. MOF voor elke resource</span><span class="sxs-lookup"><span data-stu-id="ce024-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="ce024-106">Controleer of de resource de juiste structuur heeft en alle vereiste bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="ce024-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="ce024-107">Elke resource module moet een. psd1-bestand bevatten en elke niet-samengestelde resource moet het bestand schema. MOF hebben.</span><span class="sxs-lookup"><span data-stu-id="ce024-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span>
<span data-ttu-id="ce024-108">Resources die geen schema bevatten, worden niet weer gegeven door `Get-DscResource` en gebruikers kunnen de IntelliSense niet gebruiken bij het schrijven van code voor die modules in ISE.</span><span class="sxs-lookup"><span data-stu-id="ce024-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span> <span data-ttu-id="ce024-109">De directory-structuur voor de resource xRemoteFile, die deel uitmaakt van de [xPSDesiredStateConfiguration-resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="ce024-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

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

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="ce024-110">De resource en het schema zijn juist</span><span class="sxs-lookup"><span data-stu-id="ce024-110">Resource and schema are correct</span></span>

<span data-ttu-id="ce024-111">Controleer het resource schema `*.schema.mof` bestand ().</span><span class="sxs-lookup"><span data-stu-id="ce024-111">Verify the resource schema (`*.schema.mof`) file.</span></span> <span data-ttu-id="ce024-112">U kunt de [DSC resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) gebruiken om uw schema te ontwikkelen en te testen.</span><span class="sxs-lookup"><span data-stu-id="ce024-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span> <span data-ttu-id="ce024-113">Zorg voor het volgende:</span><span class="sxs-lookup"><span data-stu-id="ce024-113">Make sure that:</span></span>

- <span data-ttu-id="ce024-114">Eigenschaps typen zijn juist (bijvoorbeeld: geen teken reeks gebruiken voor eigenschappen die numerieke waarden accepteren, moet u in plaats daarvan UInt32 of andere numerieke typen gebruiken)</span><span class="sxs-lookup"><span data-stu-id="ce024-114">Property types are correct (e.g. don't use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="ce024-115">Eigenschaps kenmerken zijn correct opgegeven als: ([sleutel], [vereist], [schrijven], [lezen])</span><span class="sxs-lookup"><span data-stu-id="ce024-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="ce024-116">Ten minste één para meter in het schema moet worden gemarkeerd als [sleutel]</span><span class="sxs-lookup"><span data-stu-id="ce024-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="ce024-117">de eigenschap [Read] bestaat niet samen met een van de volgende waarden: [vereist], [sleutel], [schrijven]</span><span class="sxs-lookup"><span data-stu-id="ce024-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="ce024-118">Als er meerdere kwalificaties zijn opgegeven, behalve [lezen], heeft [sleutel] prioriteit</span><span class="sxs-lookup"><span data-stu-id="ce024-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="ce024-119">Als [write] en [required] zijn opgegeven, is [required] prioriteit</span><span class="sxs-lookup"><span data-stu-id="ce024-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="ce024-120">ValueMap wordt opgegeven, waar van toepassing voor beeld:</span><span class="sxs-lookup"><span data-stu-id="ce024-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="ce024-121">Beschrijvende naam is opgegeven en wordt bevestigd aan DSC-naamgevings regels</span><span class="sxs-lookup"><span data-stu-id="ce024-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="ce024-122">Voorbeeld: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="ce024-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="ce024-123">Elk veld heeft een zinvolle beschrijving.</span><span class="sxs-lookup"><span data-stu-id="ce024-123">Every field has meaningful description.</span></span> <span data-ttu-id="ce024-124">De Power shell GitHub-opslag plaats heeft goede voor beelden, zoals het [. schema. MOF voor xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="ce024-124">The PowerShell GitHub repository has good examples, such as the [.schema.mof for xRemoteFile](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/DSCResources/DSC_xRemoteFile/DSC_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="ce024-125">Daarnaast moet u `Test-xDscResource` `Test-xDscSchema` cmdlets van [DSC resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) gebruiken om automatisch de resource en het schema te controleren:</span><span class="sxs-lookup"><span data-stu-id="ce024-125">Additionally, you should use `Test-xDscResource` and `Test-xDscSchema` cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="ce024-126">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ce024-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="ce024-127">Resource belasting zonder fouten</span><span class="sxs-lookup"><span data-stu-id="ce024-127">Resource loads without errors</span></span>

<span data-ttu-id="ce024-128">Controleer of de resource module kan worden geladen.</span><span class="sxs-lookup"><span data-stu-id="ce024-128">Check whether the resource module can be successfully loaded.</span></span> <span data-ttu-id="ce024-129">Dit kan hand matig worden bereikt door uit `Import-Module <resource_module> -force` te voeren en te bevestigen dat er geen fouten zijn opgetreden of door test Automation te schrijven.</span><span class="sxs-lookup"><span data-stu-id="ce024-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="ce024-130">In het geval van de laatste kunt u deze structuur in uw test case volgen:</span><span class="sxs-lookup"><span data-stu-id="ce024-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw "Module was not imported correctly. Errors returned: $error"
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="ce024-131">De resource is in het positieve geval idempotent</span><span class="sxs-lookup"><span data-stu-id="ce024-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="ce024-132">Een van de fundamentele kenmerken van DSC-resources is idempotence.</span><span class="sxs-lookup"><span data-stu-id="ce024-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="ce024-133">Het betekent dat het Toep assen van een DSC-configuratie met die resource meerdere keren altijd hetzelfde resultaat oplevert.</span><span class="sxs-lookup"><span data-stu-id="ce024-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="ce024-134">Als we bijvoorbeeld een configuratie maken die de volgende bestands resource bevat:</span><span class="sxs-lookup"><span data-stu-id="ce024-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="ce024-135">Nadat de toepassing voor de eerste keer is toegepast, moet de bestands test.txt worden weer gegeven in de `C:\test` map.</span><span class="sxs-lookup"><span data-stu-id="ce024-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="ce024-136">Volgende uitvoeringen van dezelfde configuratie mogen echter niet de status van de machine wijzigen (bijvoorbeeld, er moeten geen kopieën van het `test.txt` bestand worden gemaakt).</span><span class="sxs-lookup"><span data-stu-id="ce024-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span> <span data-ttu-id="ce024-137">Om ervoor te zorgen dat een resource idempotent is, kunt u herhaaldelijk aanroepen `Set-TargetResource` Wanneer u de resource rechtstreeks test of `Start-DscConfiguration` meerdere keren aanroept wanneer u de test beëindigt.</span><span class="sxs-lookup"><span data-stu-id="ce024-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="ce024-138">Het resultaat moet hetzelfde zijn na elke uitvoering.</span><span class="sxs-lookup"><span data-stu-id="ce024-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="ce024-139">Scenario voor het aanpassen van gebruikers testen</span><span class="sxs-lookup"><span data-stu-id="ce024-139">Test user modification scenario</span></span>

<span data-ttu-id="ce024-140">Door de status van de machine te wijzigen en DSC opnieuw uit te voeren, kunt u controleren of `Set-TargetResource` en `Test-TargetResource` goed functioneren.</span><span class="sxs-lookup"><span data-stu-id="ce024-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="ce024-141">Hier volgen de stappen die u moet uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="ce024-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="ce024-142">Begin met de resource en niet de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="ce024-142">Start with the resource not in the desired state.</span></span>
1. <span data-ttu-id="ce024-143">Configuratie uitvoeren met uw resource</span><span class="sxs-lookup"><span data-stu-id="ce024-143">Run configuration with your resource</span></span>
1. <span data-ttu-id="ce024-144">Verify `Test-DscConfiguration` retourneert True</span><span class="sxs-lookup"><span data-stu-id="ce024-144">Verify `Test-DscConfiguration` returns True</span></span>
1. <span data-ttu-id="ce024-145">Wijzig het geconfigureerde item in de gewenste status</span><span class="sxs-lookup"><span data-stu-id="ce024-145">Modify the configured item to be out of the desired state</span></span>
1. <span data-ttu-id="ce024-146">Verify `Test-DscConfiguration` retourneert False</span><span class="sxs-lookup"><span data-stu-id="ce024-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="ce024-147">Hier volgt een meer concrete voor beeld van het gebruik van een register resource:</span><span class="sxs-lookup"><span data-stu-id="ce024-147">Here's a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="ce024-148">Beginnen met de register sleutel heeft niet de gewenste status</span><span class="sxs-lookup"><span data-stu-id="ce024-148">Start with registry key not in the desired state</span></span>
1. <span data-ttu-id="ce024-149">Voer uit `Start-DscConfiguration` met een configuratie om deze in de gewenste staat te zetten en controleer of deze wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="ce024-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
1. <span data-ttu-id="ce024-150">Uitvoeren `Test-DscConfiguration` en controleren of het resultaat True retourneert</span><span class="sxs-lookup"><span data-stu-id="ce024-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
1. <span data-ttu-id="ce024-151">Wijzig de waarde van de sleutel zodat deze niet de gewenste status heeft</span><span class="sxs-lookup"><span data-stu-id="ce024-151">Modify the value of the key so that it is not in the desired state</span></span>
1. <span data-ttu-id="ce024-152">Uitvoeren `Test-DscConfiguration` en controleren of retourneert False</span><span class="sxs-lookup"><span data-stu-id="ce024-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
1. <span data-ttu-id="ce024-153">`Get-TargetResource` de functionaliteit is geverifieerd met `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="ce024-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="ce024-154">`Get-TargetResource` de details van de huidige status van de resource moeten worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ce024-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="ce024-155">Zorg ervoor dat u deze test door aan te roepen `Get-DscConfiguration` nadat u de configuratie hebt toegepast en controleer of de uitvoer correct overeenkomt met de huidige status van de machine.</span><span class="sxs-lookup"><span data-stu-id="ce024-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="ce024-156">Het is belang rijk om deze afzonderlijk te testen, omdat eventuele problemen in dit gebied niet worden weer gegeven wanneer u aanroept `Start-DscConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ce024-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="ce024-157">**Get/set/test-TargetResource-** functies rechtstreeks aanroepen</span><span class="sxs-lookup"><span data-stu-id="ce024-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="ce024-158">Zorg ervoor dat u de `Get/Set/Test-TargetResource` functies in uw Resource test door deze rechtstreeks aan te roepen en te controleren of ze werken zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="ce024-158">Make sure you test the `Get/Set/Test-TargetResource` functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="ce024-159">End-to-end controleren met start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="ce024-159">Verify End to End using Start-DscConfiguration</span></span>

<span data-ttu-id="ce024-160">`Get/Set/Test-TargetResource`Het is belang rijk om functies te testen door ze rechtstreeks aan te roepen, maar niet alle problemen worden op deze manier gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="ce024-160">Testing `Get/Set/Test-TargetResource` functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="ce024-161">Het is belang rijk dat u zich richt op `Start-DscConfiguration` het gebruik of de pull-server.</span><span class="sxs-lookup"><span data-stu-id="ce024-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="ce024-162">Dit is in feite hoe gebruikers de resource gaan gebruiken, dus te laag inschatten de significantie van dit type tests niet op.</span><span class="sxs-lookup"><span data-stu-id="ce024-162">In fact, this is how users will use the resource, so don't underestimate the significance of this type of tests.</span></span> <span data-ttu-id="ce024-163">Mogelijke typen problemen:</span><span class="sxs-lookup"><span data-stu-id="ce024-163">Possible types of issues:</span></span>

- <span data-ttu-id="ce024-164">Referentie/sessie kan anders werken omdat de DSC-agent wordt uitgevoerd als een service.</span><span class="sxs-lookup"><span data-stu-id="ce024-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span> <span data-ttu-id="ce024-165">Zorg ervoor dat u alle functies hier kunt testen.</span><span class="sxs-lookup"><span data-stu-id="ce024-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="ce024-166">Het resultaat van `Start-DscConfiguration` de uitvoer door kan afwijken van de fouten die worden weer gegeven wanneer u de `Set-TargetResource` functie rechtstreeks aanroept.</span><span class="sxs-lookup"><span data-stu-id="ce024-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatibility-on-all-dsc-supported-platforms"></a><span data-ttu-id="ce024-167">Test compatibiliteit op alle door DSC ondersteunde platforms</span><span class="sxs-lookup"><span data-stu-id="ce024-167">Test compatibility on all DSC supported platforms</span></span>

<span data-ttu-id="ce024-168">De resource moet werken op alle door DSC ondersteunde platforms (Windows Server 2008 R2 en nieuwer).</span><span class="sxs-lookup"><span data-stu-id="ce024-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="ce024-169">Installeer de meest recente WMF (Windows Management Framework) in uw besturings systeem om de meest recente versie van DSC op te halen.</span><span class="sxs-lookup"><span data-stu-id="ce024-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="ce024-170">Als uw resource niet op een aantal van deze platformen werkt, is het mogelijk dat er een specifiek fout bericht wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ce024-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="ce024-171">Zorg er ook voor dat uw resource controleert of cmdlets die u aanroept, aanwezig zijn op een bepaalde computer.</span><span class="sxs-lookup"><span data-stu-id="ce024-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="ce024-172">Windows Server 2012 heeft een groot aantal nieuwe cmdlets toegevoegd die niet beschikbaar zijn in Windows Server 2008R2, zelfs niet als WMF is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ce024-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="ce024-173">Controleren op Windows-client (indien van toepassing)</span><span class="sxs-lookup"><span data-stu-id="ce024-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="ce024-174">Een zeer veelvoorkomende test hiaat is het verifiëren van de bron alleen op Server versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="ce024-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="ce024-175">Veel resources zijn ook ontworpen om te werken met client-Sku's, dus als dat in uw geval waar is, vergeet dan niet om deze ook op deze platforms te testen.</span><span class="sxs-lookup"><span data-stu-id="ce024-175">Many resources are also designed to work on Client SKUs, so if that's true in your case, don't forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="ce024-176">Get-Dscresource bieden geeft de resource weer</span><span class="sxs-lookup"><span data-stu-id="ce024-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="ce024-177">Nadat u de module hebt geïmplementeerd, `Get-DscResource` moet u de resource onder andere aanroepen als gevolg van een lijst.</span><span class="sxs-lookup"><span data-stu-id="ce024-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="ce024-178">Als u uw resource niet kunt vinden in de lijst, moet u ervoor zorgen dat het schema. MOF-bestand voor die bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="ce024-178">If you can't find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="ce024-179">Resource module bevat voor beelden</span><span class="sxs-lookup"><span data-stu-id="ce024-179">Resource module contains examples</span></span>

<span data-ttu-id="ce024-180">Het maken van kwaliteits voorbeelden waarmee anderen inzicht krijgen in hoe u deze kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ce024-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="ce024-181">Dit is cruciaal, vooral omdat veel gebruikers voorbeeld code behandelen als documentatie.</span><span class="sxs-lookup"><span data-stu-id="ce024-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="ce024-182">Eerst moet u de voor beelden bepalen die in de module worden opgenomen. u moet mini maal de meest belang rijke use cases voor uw resource best rijken:</span><span class="sxs-lookup"><span data-stu-id="ce024-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="ce024-183">Als uw module verschillende resources bevat die moeten samen werken voor een end-to-end-scenario, zou het Basic-end-to-end-voor beeld het eerst in het ideale geval moeten zijn.</span><span class="sxs-lookup"><span data-stu-id="ce024-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="ce024-184">De eerste voor beelden zijn heel eenvoudig: hoe u aan de slag kunt gaan met uw resources in kleine, beheersbare segmenten (bijvoorbeeld het maken van een nieuwe VHD)</span><span class="sxs-lookup"><span data-stu-id="ce024-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="ce024-185">De volgende voor beelden moeten worden gebouwd op basis van deze voor beelden (bijvoorbeeld het maken van een VM van een VHD, het verwijderen van de VM, het wijzigen van de virtuele machine) en het weer geven van geavanceerde functionaliteit (bijvoorbeeld het maken van een virtuele machine met dynamisch geheugen)</span><span class="sxs-lookup"><span data-stu-id="ce024-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="ce024-186">Voorbeeld configuraties moeten worden para meters (alle waarden moeten worden door gegeven aan de configuratie als para meters en er mogen geen hardcoded waarden zijn):</span><span class="sxs-lookup"><span data-stu-id="ce024-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

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

- <span data-ttu-id="ce024-187">Het is een goed idee om een voor beeld van een invoeging van de configuratie met de werkelijke waarden aan het einde van het voorbeeld script uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="ce024-187">It's a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span> <span data-ttu-id="ce024-188">Zo is in de configuratie hierboven niet nood zakelijk duidelijk dat de beste manier om agents op te geven:</span><span class="sxs-lookup"><span data-stu-id="ce024-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="ce024-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In dat geval kan een opmerking de beoogde uitvoering van de configuratie verduidelijken:</span><span class="sxs-lookup"><span data-stu-id="ce024-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

```powershell
<#
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>
```

- <span data-ttu-id="ce024-190">Voor elk voor beeld moet u een korte beschrijving schrijven waarin wordt uitgelegd wat het doet en wat de betekenis van de para meters zijn.</span><span class="sxs-lookup"><span data-stu-id="ce024-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="ce024-191">Zorg ervoor dat de voor beelden de meeste belang rijke scenario's voor uw resource dekken. als er niets mis gaat, controleert u of ze alle computers in de gewenste status uitvoeren en plaatsen.</span><span class="sxs-lookup"><span data-stu-id="ce024-191">Make sure examples cover most the important scenarios for your resource and if there's nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="ce024-192">Fout berichten zijn eenvoudig te begrijpen en helpen gebruikers problemen op te lossen</span><span class="sxs-lookup"><span data-stu-id="ce024-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="ce024-193">Goede fout berichten moeten zijn:</span><span class="sxs-lookup"><span data-stu-id="ce024-193">Good error messages should be:</span></span>

- <span data-ttu-id="ce024-194">Er is sprake van het grootste probleem met fout berichten dat ze vaak niet bestaan, dus zorg ervoor dat ze daar zijn.</span><span class="sxs-lookup"><span data-stu-id="ce024-194">There: The biggest problem with error messages is that they often don't exist, so make sure they are there.</span></span>
- <span data-ttu-id="ce024-195">Eenvoudig te begrijpen: menselijk leesbaar, geen onduidelijke fout codes</span><span class="sxs-lookup"><span data-stu-id="ce024-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="ce024-196">Nauw keurig: beschrijven wat het probleem precies is</span><span class="sxs-lookup"><span data-stu-id="ce024-196">Precise: Describe what's exactly the problem</span></span>
- <span data-ttu-id="ce024-197">Feitelijke: advies over het oplossen van het probleem</span><span class="sxs-lookup"><span data-stu-id="ce024-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="ce024-198">Vermoeden: liggen niet op de gebruiker of zorg ervoor dat ze slecht zijn</span><span class="sxs-lookup"><span data-stu-id="ce024-198">Polite: Don't blame user or make them feel bad</span></span>

<span data-ttu-id="ce024-199">Controleer of u fouten in end-to-end-scenario's controleert (met `Start-DscConfiguration` ), omdat deze kunnen verschillen van de waarden die worden geretourneerd bij het rechtstreeks uitvoeren van resource functies.</span><span class="sxs-lookup"><span data-stu-id="ce024-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="ce024-200">Logboek berichten zijn eenvoudig te begrijpen en info (inclusief – uitgebreid, fouten opsporen en ETW-Logboeken)</span><span class="sxs-lookup"><span data-stu-id="ce024-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="ce024-201">Zorg ervoor dat de logboeken die zijn gegenereerd door de resource eenvoudig te begrijpen zijn en waarde aan de gebruiker kunnen geven.</span><span class="sxs-lookup"><span data-stu-id="ce024-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span>
<span data-ttu-id="ce024-202">Resources moeten alle informatie uitvoeren die nuttig kan zijn voor de gebruiker, maar meer logboeken zijn niet altijd beter.</span><span class="sxs-lookup"><span data-stu-id="ce024-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="ce024-203">Vermijd het gebruik van redundantie en het uitvoeren van gegevens die geen extra waarde bieden: laat iemand niet meer dan honderden logboek vermeldingen bezoeken om te vinden wat ze zoeken.</span><span class="sxs-lookup"><span data-stu-id="ce024-203">You should avoid redundancy and outputting data which does not provide additional value – don't make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="ce024-204">Uiteraard is er geen logboeken die een geschikte oplossing voor dit probleem zijn.</span><span class="sxs-lookup"><span data-stu-id="ce024-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="ce024-205">Bij het testen moet u ook uitgebreide logboeken en fouten opsporen analyseren (door op de juiste wijze uit te voeren `Start-DscConfiguration` `–Verbose` en te `–Debug` scha kelen), evenals etw-Logboeken.</span><span class="sxs-lookup"><span data-stu-id="ce024-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="ce024-206">Als u DSC ETW-logboeken wilt weer geven, gaat u naar Logboeken en opent u de volgende map: toepassingen en services-micro soft-Windows-desired state Configuration.</span><span class="sxs-lookup"><span data-stu-id="ce024-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span> <span data-ttu-id="ce024-207">Standaard zal er een operationeel kanaal zijn, maar zorg ervoor dat u analytische en probleemoplossings kanalen inschakelt voordat u de configuratie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ce024-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span> <span data-ttu-id="ce024-208">Als u kanalen voor analyse en fout opsporing wilt inschakelen, kunt u hieronder een script uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="ce024-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="ce024-209">De resource-implementatie bevat geen hardcoded paden</span><span class="sxs-lookup"><span data-stu-id="ce024-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="ce024-210">Zorg ervoor dat er geen hardcoded paden aanwezig zijn in de resource-implementatie, met name als er een taal (en-US) wordt gebruikt, of als er systeem variabelen zijn die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="ce024-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span> <span data-ttu-id="ce024-211">Als uw resource toegang moet hebben tot specifieke paden, gebruikt u omgevings variabelen in plaats van hardcoding het pad, omdat het mogelijk op andere computers kan verschillen.</span><span class="sxs-lookup"><span data-stu-id="ce024-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="ce024-212">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="ce024-212">Example:</span></span>

<span data-ttu-id="ce024-213">In plaats van:</span><span class="sxs-lookup"><span data-stu-id="ce024-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="ce024-214">U kunt schrijven:</span><span class="sxs-lookup"><span data-stu-id="ce024-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="ce024-215">De resource-implementatie bevat geen gebruikers gegevens</span><span class="sxs-lookup"><span data-stu-id="ce024-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="ce024-216">Zorg ervoor dat er geen e-mail namen, account gegevens of namen van personen in de code zijn.</span><span class="sxs-lookup"><span data-stu-id="ce024-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="ce024-217">De resource is getest met geldige/ongeldige referenties</span><span class="sxs-lookup"><span data-stu-id="ce024-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="ce024-218">Als de resource een referentie als para meter heeft:</span><span class="sxs-lookup"><span data-stu-id="ce024-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="ce024-219">Controleer of de resource werkt wanneer het lokale systeem (of het computer account voor externe bronnen) geen toegang heeft.</span><span class="sxs-lookup"><span data-stu-id="ce024-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="ce024-220">Controleren of de resource werkt met een referentie die is opgegeven voor Get, set en test</span><span class="sxs-lookup"><span data-stu-id="ce024-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="ce024-221">Als uw resource toegang heeft tot shares, test u alle varianten die u nodig hebt om te ondersteunen, zoals:</span><span class="sxs-lookup"><span data-stu-id="ce024-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="ce024-222">Standaard Windows-shares.</span><span class="sxs-lookup"><span data-stu-id="ce024-222">Standard windows shares.</span></span>
  - <span data-ttu-id="ce024-223">DFS-shares.</span><span class="sxs-lookup"><span data-stu-id="ce024-223">DFS shares.</span></span>
  - <span data-ttu-id="ce024-224">SAMBA-shares (als u Linux wilt ondersteunen.)</span><span class="sxs-lookup"><span data-stu-id="ce024-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="ce024-225">Voor de resource is geen interactieve invoer vereist</span><span class="sxs-lookup"><span data-stu-id="ce024-225">Resource does not require interactive input</span></span>

<span data-ttu-id="ce024-226">`Get/Set/Test-TargetResource` functies moeten automatisch worden uitgevoerd en moeten niet wachten op invoer van de gebruiker tijdens een wille keurige fase (bijvoorbeeld omdat u niet `Get-Credential` in deze functies moet worden gebruikt).</span><span class="sxs-lookup"><span data-stu-id="ce024-226">`Get/Set/Test-TargetResource` functions should be executed automatically and must not wait for user's input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="ce024-227">Als u de invoer van de gebruiker moet opgeven, moet u deze door geven aan de configuratie als para meter tijdens de compilatie fase.</span><span class="sxs-lookup"><span data-stu-id="ce024-227">If you need to provide user's input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="ce024-228">De resource functionaliteit is uitgebreid getest</span><span class="sxs-lookup"><span data-stu-id="ce024-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="ce024-229">Deze controle lijst bevat items die belang rijk zijn om te worden getest en/of vaak ontbreekt.</span><span class="sxs-lookup"><span data-stu-id="ce024-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="ce024-230">Er is een aantal tests, voornamelijk functionele functies die specifiek zijn voor de resource die u wilt testen en die hier niet worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="ce024-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="ce024-231">Vergeet niet om te zien wat negatieve test cases zijn.</span><span class="sxs-lookup"><span data-stu-id="ce024-231">Don't forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="ce024-232">Best practice: de resource module bevat de map tests met ResourceDesignerTests.ps1 script</span><span class="sxs-lookup"><span data-stu-id="ce024-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="ce024-233">Het is een goed idee om de map ' tests ' te maken in de resource module, het bestand te maken `ResourceDesignerTests.ps1` en tests toe te voegen met `Test-xDscResource` en `Test-xDscSchema` voor alle resources in de betreffende module.</span><span class="sxs-lookup"><span data-stu-id="ce024-233">It's a good practice to create folder "Tests" inside resource module, create `ResourceDesignerTests.ps1` file and add tests using `Test-xDscResource` and `Test-xDscSchema` for all resources in given module.</span></span> <span data-ttu-id="ce024-234">Op deze manier kunt u snel schema's valideren van alle resources uit de opgegeven modules en een Sanity controleren voordat u publiceert.</span><span class="sxs-lookup"><span data-stu-id="ce024-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span> <span data-ttu-id="ce024-235">Voor xRemoteFile `ResourceTests.ps1` kan het er zo eenvoudig uitzien als:</span><span class="sxs-lookup"><span data-stu-id="ce024-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="ce024-236">Aanbevolen procedure: Resource ondersteunt-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ce024-236">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="ce024-237">Als uw resource ' gevaarlijk ' bewerkingen uitvoert, is het een goed idee om functionaliteit te implementeren `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ce024-237">If your resource is performing "dangerous" operations, it's a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="ce024-238">Nadat de bewerking is uitgevoerd, moet u ervoor zorgen dat uitvoer op de `-WhatIf` juiste wijze bewerkingen beschrijft die zouden gebeuren als de opdracht zonder switch is voltooid `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="ce024-238">After it's done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span> <span data-ttu-id="ce024-239">Controleer ook of de bewerkingen niet worden uitgevoerd (er worden geen wijzigingen aangebracht in de status van het knoop punt) wanneer `–WhatIf` Switch aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="ce024-239">Also, verify that operations does not execute (no changes to the node's state are made) when `–WhatIf` switch is present.</span></span> <span data-ttu-id="ce024-240">Stel dat we de bestands resource testen.</span><span class="sxs-lookup"><span data-stu-id="ce024-240">For example, let's assume we are testing File resource.</span></span> <span data-ttu-id="ce024-241">Hieronder vindt u eenvoudige configuratie waarmee bestanden `test.txt` met de inhoud ' test ' worden gemaakt:</span><span class="sxs-lookup"><span data-stu-id="ce024-241">Below is simple configuration which creates file `test.txt` with contents "test":</span></span>

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

<span data-ttu-id="ce024-242">Als we de configuratie met de switch compileren en vervolgens uitvoeren `-WhatIf` , vertelt de uitvoer precies wat er zou gebeuren wanneer de configuratie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="ce024-242">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="ce024-243">De configuratie zelf is echter niet uitgevoerd (het `test.txt` bestand is niet gemaakt).</span><span class="sxs-lookup"><span data-stu-id="ce024-243">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

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

<span data-ttu-id="ce024-244">Deze lijst is niet volledig, maar hierin worden veel belang rijke problemen besproken die kunnen optreden tijdens het ontwerpen, ontwikkelen en testen van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="ce024-244">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
