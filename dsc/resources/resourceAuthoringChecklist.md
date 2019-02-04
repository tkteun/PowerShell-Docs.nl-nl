---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Controlelijst voor het ontwerpen van resource
ms.openlocfilehash: 7b1a096bba1b729c096b6689178ee022e12e4634
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683959"
---
# <a name="resource-authoring-checklist"></a><span data-ttu-id="619c5-103">Controlelijst voor het ontwerpen van resource</span><span class="sxs-lookup"><span data-stu-id="619c5-103">Resource authoring checklist</span></span>

<span data-ttu-id="619c5-104">Deze controlelijst is een lijst met aanbevolen procedures bij het ontwerpen van een nieuwe DSC-Resource.</span><span class="sxs-lookup"><span data-stu-id="619c5-104">This checklist is a list of best practices when authoring a new DSC Resource.</span></span>

## <a name="resource-module-contains-psd1-file-and-schemamof-for-every-resource"></a><span data-ttu-id="619c5-105">Resource-module bevat .psd1-bestand en schema.mof voor elke resource</span><span class="sxs-lookup"><span data-stu-id="619c5-105">Resource module contains .psd1 file and schema.mof for every resource</span></span>

<span data-ttu-id="619c5-106">Controleer of de bron de juiste structuur heeft en alle vereiste bestanden bevat.</span><span class="sxs-lookup"><span data-stu-id="619c5-106">Check that your resource has correct structure and contains all required files.</span></span> <span data-ttu-id="619c5-107">Elke resource-module een .psd1-bestand moet bevatten en elke niet-samengestelde resource schema.mof bestand moet hebben.</span><span class="sxs-lookup"><span data-stu-id="619c5-107">Every resource module should contain a .psd1 file and every non-composite resource should have schema.mof file.</span></span> <span data-ttu-id="619c5-108">Resources die geen schema bevatten, niet worden weergegeven door `Get-DscResource` en gebruikers niet mogelijk de intellisense gebruiken bij het schrijven van code op basis van deze modules in ISE.</span><span class="sxs-lookup"><span data-stu-id="619c5-108">Resources that do not contain schema will not be listed by `Get-DscResource` and users will not be able to use the intellisense when writing code against those modules in ISE.</span></span>
<span data-ttu-id="619c5-109">De mapstructuur voor xRemoteFile resource, die deel uitmaakt van de [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="619c5-109">The directory structure for xRemoteFile resource, which is part of the [xPSDesiredStateConfiguration resource module](https://github.com/PowerShell/xPSDesiredStateConfiguration), looks as follows:</span></span>

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

## <a name="resource-and-schema-are-correct"></a><span data-ttu-id="619c5-110">Bron en het schema zijn juist</span><span class="sxs-lookup"><span data-stu-id="619c5-110">Resource and schema are correct</span></span>

<span data-ttu-id="619c5-111">Controleer of de resource-schema (\*. schema.mof) bestand.</span><span class="sxs-lookup"><span data-stu-id="619c5-111">Verify the resource schema (\*.schema.mof) file.</span></span> <span data-ttu-id="619c5-112">U kunt de [Designer voor DSC-Resource](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) voor het ontwikkelen en testen van uw schema.</span><span class="sxs-lookup"><span data-stu-id="619c5-112">You can use the [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to help develop and test your schema.</span></span>
<span data-ttu-id="619c5-113">Zorg ervoor dat:</span><span class="sxs-lookup"><span data-stu-id="619c5-113">Make sure that:</span></span>

- <span data-ttu-id="619c5-114">Typen eigenschappen voor correct zijn (bijvoorbeeld tekenreeks niet gebruiken voor eigenschappen die numerieke waarden accepteert, moet u UInt32 of andere numerieke typen in plaats daarvan)</span><span class="sxs-lookup"><span data-stu-id="619c5-114">Property types are correct (e.g. don’t use String for properties which accept numeric values, you should use UInt32 or other numeric types instead)</span></span>
- <span data-ttu-id="619c5-115">Eigenschapskenmerken correct zijn opgegeven als: ([-toets], [vereist], [schrijven], [lezen])</span><span class="sxs-lookup"><span data-stu-id="619c5-115">Property attributes are specified correctly as: ([key], [required], [write], [read])</span></span>
- <span data-ttu-id="619c5-116">Ten minste één parameter in het schema moet worden gemarkeerd als [-toets]</span><span class="sxs-lookup"><span data-stu-id="619c5-116">At least one parameter in the schema has to be marked as [key]</span></span>
- <span data-ttu-id="619c5-117">[meer] eigenschap niet samen voorkomen, samen met een van: (vereist), [key], [schrijven]</span><span class="sxs-lookup"><span data-stu-id="619c5-117">[read] property does not coexist together with any of: [required], [key], [write]</span></span>
- <span data-ttu-id="619c5-118">Als meerdere kwalificaties zijn opgegeven, met uitzondering [lezen], klikt u vervolgens prioriteit]</span><span class="sxs-lookup"><span data-stu-id="619c5-118">If multiple qualifiers are specified except [read], then [key] takes precedence</span></span>
- <span data-ttu-id="619c5-119">Als [schrijven] en [vereist] zijn opgegeven, wordt heeft een hogere prioriteit (vereist)</span><span class="sxs-lookup"><span data-stu-id="619c5-119">If [write] and [required] are specified, then [required] takes precedence</span></span>
- <span data-ttu-id="619c5-120">ValueMap is opgegeven voorbeeld indien van toepassing:</span><span class="sxs-lookup"><span data-stu-id="619c5-120">ValueMap is specified where appropriate Example:</span></span>

  ```
  [Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
  ```

- <span data-ttu-id="619c5-121">Beschrijvende naam is opgegeven en wordt bevestigd dat aan de naamgevingsconventies DSC</span><span class="sxs-lookup"><span data-stu-id="619c5-121">Friendly name is specified and confirms to DSC naming conventions</span></span>

  <span data-ttu-id="619c5-122">Voorbeeld: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span><span class="sxs-lookup"><span data-stu-id="619c5-122">Example: `[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]`</span></span>

- <span data-ttu-id="619c5-123">Elk veld heeft een duidelijke beschrijving.</span><span class="sxs-lookup"><span data-stu-id="619c5-123">Every field has meaningful description.</span></span> <span data-ttu-id="619c5-124">De PowerShell-GitHub-opslagplaats is een goede voorbeelden zoals [de. schema.mof voor xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span><span class="sxs-lookup"><span data-stu-id="619c5-124">The PowerShell GitHub repository has good examples, such as [the .schema.mof for xRemoteFile](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)</span></span>

<span data-ttu-id="619c5-125">Bovendien moet u **Test xDscResource** en **Test xDscSchema** -cmdlets van [Designer voor DSC-Resource](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) automatisch te controleren of de bron en het schema:</span><span class="sxs-lookup"><span data-stu-id="619c5-125">Additionally, you should use **Test-xDscResource** and **Test-xDscSchema** cmdlets from [DSC Resource Designer](https://www.powershellgallery.com/packages/xDSCResourceDesigner/1.12.0.0) to automatically verify the resource and schema:</span></span>

```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```

<span data-ttu-id="619c5-126">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="619c5-126">For example:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="resource-loads-without-errors"></a><span data-ttu-id="619c5-127">Resource zonder fouten wordt geladen</span><span class="sxs-lookup"><span data-stu-id="619c5-127">Resource loads without errors</span></span>

<span data-ttu-id="619c5-128">Controleer of de resource-module is kan worden geladen.</span><span class="sxs-lookup"><span data-stu-id="619c5-128">Check whether the resource module can be successfully loaded.</span></span>
<span data-ttu-id="619c5-129">Dit kan handmatig worden bereikt door het uitvoeren van `Import-Module <resource_module> -force` en bevestigen dat er geen fouten zijn opgetreden, of door schrijven test automation.</span><span class="sxs-lookup"><span data-stu-id="619c5-129">This can be achieved manually, by running `Import-Module <resource_module> -force` and confirming that no errors occurred, or by writing test automation.</span></span> <span data-ttu-id="619c5-130">U kunt deze structuur in uw testscenario volgen in het geval van de laatste:</span><span class="sxs-lookup"><span data-stu-id="619c5-130">In case of the latter, you can follow this structure in your test case:</span></span>

```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```

## <a name="resource-is-idempotent-in-the-positive-case"></a><span data-ttu-id="619c5-131">Resource is idempotent zijn in het geval is positief</span><span class="sxs-lookup"><span data-stu-id="619c5-131">Resource is idempotent in the positive case</span></span>

<span data-ttu-id="619c5-132">Een van de basiskenmerken van DSC-resources is idempotence.</span><span class="sxs-lookup"><span data-stu-id="619c5-132">One of the fundamental characteristics of DSC resources is idempotence.</span></span> <span data-ttu-id="619c5-133">Dit betekent dat het toepassen van een DSC-configuratie met die bron meerdere keren wordt altijd hetzelfde resultaat bereiken.</span><span class="sxs-lookup"><span data-stu-id="619c5-133">It means that applying a DSC configuration containing that resource multiple times will always achieve the same result.</span></span> <span data-ttu-id="619c5-134">Bijvoorbeeld, als we een configuratie waarin de resource van het volgende bestand maken:</span><span class="sxs-lookup"><span data-stu-id="619c5-134">For example, if we create a configuration which contains the following File resource:</span></span>

```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
}
```

<span data-ttu-id="619c5-135">Na het toepassen van deze voor de eerste keer, bestand test.txt, moet worden weergegeven in `C:\test` map.</span><span class="sxs-lookup"><span data-stu-id="619c5-135">After applying it for the first time, file test.txt should appear in `C:\test` folder.</span></span> <span data-ttu-id="619c5-136">Volgende uitvoeringen van dezelfde configuratie moeten echter niet wijzigen de status van de machine (bijvoorbeeld geen kopieën van de `test.txt` -bestand moet worden gemaakt).</span><span class="sxs-lookup"><span data-stu-id="619c5-136">However, subsequent runs of the same configuration should not change the state of the machine (e.g. no copies of the `test.txt` file should be created).</span></span>
<span data-ttu-id="619c5-137">Om te controleren of een resource is idempotent zijn, kunt u herhaaldelijk aanroepen `Set-TargetResource` bij het testen van de resource direct of bel `Start-DscConfiguration` meerdere keren bij het maken van end-to-end-testen.</span><span class="sxs-lookup"><span data-stu-id="619c5-137">To ensure a resource is idempotent you can repeatedly call `Set-TargetResource` when testing the resource directly, or call `Start-DscConfiguration` multiple times when doing end to end testing.</span></span> <span data-ttu-id="619c5-138">Het resultaat moet hetzelfde na elke uitvoering.</span><span class="sxs-lookup"><span data-stu-id="619c5-138">The result should be the same after every run.</span></span>

## <a name="test-user-modification-scenario"></a><span data-ttu-id="619c5-139">Testscenario gebruiker wijzigen</span><span class="sxs-lookup"><span data-stu-id="619c5-139">Test user modification scenario</span></span>

<span data-ttu-id="619c5-140">Door het wijzigen van de status van de machine en vervolgens opnieuw uit te voeren DSC, kunt u controleren of `Set-TargetResource` en `Test-TargetResource` laten functioneren.</span><span class="sxs-lookup"><span data-stu-id="619c5-140">By changing the state of the machine and then rerunning DSC, you can verify that `Set-TargetResource` and `Test-TargetResource` function properly.</span></span> <span data-ttu-id="619c5-141">Hier vindt u stappen die u moet uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="619c5-141">Here are steps you should take:</span></span>

1. <span data-ttu-id="619c5-142">Beginnen met de resource niet in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="619c5-142">Start with the resource not in the desired state.</span></span>
2. <span data-ttu-id="619c5-143">Configuratie uitvoeren met de resource</span><span class="sxs-lookup"><span data-stu-id="619c5-143">Run configuration with your resource</span></span>
3. <span data-ttu-id="619c5-144">Controleer of `Test-DscConfiguration` resulteert in waar</span><span class="sxs-lookup"><span data-stu-id="619c5-144">Verify `Test-DscConfiguration` returns True</span></span>
4. <span data-ttu-id="619c5-145">Wijzigen van de geconfigureerde item om te worden uit de gewenste status</span><span class="sxs-lookup"><span data-stu-id="619c5-145">Modify the configured item to be out of the desired state</span></span>
5. <span data-ttu-id="619c5-146">Controleer of `Test-DscConfiguration` retourneert ' false '</span><span class="sxs-lookup"><span data-stu-id="619c5-146">Verify `Test-DscConfiguration` returns false</span></span>

<span data-ttu-id="619c5-147">Hier volgt een meer concrete voorbeeld met behulp van registerresource:</span><span class="sxs-lookup"><span data-stu-id="619c5-147">Here’s a more concrete example using Registry resource:</span></span>

1. <span data-ttu-id="619c5-148">Beginnen met de registersleutel niet in de gewenste status</span><span class="sxs-lookup"><span data-stu-id="619c5-148">Start with registry key not in the desired state</span></span>
2. <span data-ttu-id="619c5-149">Voer `Start-DscConfiguration` met een configuratie plaatst deze in de gewenste status en controleer of deze is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="619c5-149">Run `Start-DscConfiguration` with a configuration to put it in the desired state and verify it passes.</span></span>
3. <span data-ttu-id="619c5-150">Voer `Test-DscConfiguration` en controleer of deze retourneert ' True '</span><span class="sxs-lookup"><span data-stu-id="619c5-150">Run `Test-DscConfiguration` and verify it returns true</span></span>
4. <span data-ttu-id="619c5-151">De waarde van de sleutel wijzigen zodat deze zich niet in de gewenste status</span><span class="sxs-lookup"><span data-stu-id="619c5-151">Modify the value of the key so that it is not in the desired state</span></span>
5. <span data-ttu-id="619c5-152">Voer `Test-DscConfiguration` en controleer of het resultaat false</span><span class="sxs-lookup"><span data-stu-id="619c5-152">Run `Test-DscConfiguration` and verify it returns false</span></span>
6. <span data-ttu-id="619c5-153">`Get-TargetResource` functionaliteit is geverifieerd met behulp van `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="619c5-153">`Get-TargetResource` functionality was verified using `Get-DscConfiguration`</span></span>

<span data-ttu-id="619c5-154">`Get-TargetResource` details van de huidige status van de resource moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="619c5-154">`Get-TargetResource` should return details of the current state of the resource.</span></span> <span data-ttu-id="619c5-155">Zorg ervoor dat u deze testen door het aanroepen van `Get-DscConfiguration` nadat u de configuratie toepassen en verifiëren die correct uitvoer de huidige status van de machine geeft.</span><span class="sxs-lookup"><span data-stu-id="619c5-155">Make sure to test it by calling `Get-DscConfiguration` after you apply the configuration and verifying that output correctly reflects the current state of the machine.</span></span> <span data-ttu-id="619c5-156">Het is belangrijk dat de afzonderlijk testen omdat eventuele problemen op dit gebied wordt niet weergegeven bij het aanroepen van `Start-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="619c5-156">It's important to test it separately, since any issues in this area won't appear when calling `Start-DscConfiguration`.</span></span>

## <a name="call-getsettest-targetresource-functions-directly"></a><span data-ttu-id="619c5-157">Bel **Get/Set/Test-TargetResource** rechtstreeks functies</span><span class="sxs-lookup"><span data-stu-id="619c5-157">Call **Get/Set/Test-TargetResource** functions directly</span></span>

<span data-ttu-id="619c5-158">Zorg ervoor dat u test de **Get/Set/Test-TargetResource** functies die zijn geïmplementeerd in uw resource door ze voor het rechtstreeks aanroepen en verifiëren dat ze werken zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="619c5-158">Make sure you test the **Get/Set/Test-TargetResource** functions implemented in your resource by calling them directly and verifying that they work as expected.</span></span>

## <a name="verify-end-to-end-using-start-dscconfiguration"></a><span data-ttu-id="619c5-159">Controleer of met behulp van End-to-End **Start-DscConfiguration**</span><span class="sxs-lookup"><span data-stu-id="619c5-159">Verify End to End using **Start-DscConfiguration**</span></span>

<span data-ttu-id="619c5-160">Testen **Get/Set/Test-TargetResource** functies door ze rechtstreeks aan te roepen is belangrijk, maar niet alle problemen op deze manier worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="619c5-160">Testing **Get/Set/Test-TargetResource** functions by calling them directly is important, but not all issues will be discovered this way.</span></span> <span data-ttu-id="619c5-161">U moet erop zijn gericht aanzienlijk deel van de controle over het gebruik van `Start-DscConfiguration` of de pull-server.</span><span class="sxs-lookup"><span data-stu-id="619c5-161">You should focus significant part of your testing on using `Start-DscConfiguration` or the pull server.</span></span> <span data-ttu-id="619c5-162">Dit is in feite hoe gebruikers de resource, zodat de betekenis van dit type tests Onderschat niet wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="619c5-162">In fact, this is how users will use the resource, so don’t underestimate the significance of this type of tests.</span></span>
<span data-ttu-id="619c5-163">Mogelijke typen problemen:</span><span class="sxs-lookup"><span data-stu-id="619c5-163">Possible types of issues:</span></span>

- <span data-ttu-id="619c5-164">Referentie/sessie mogelijk anders werken omdat de DSC-agent wordt uitgevoerd als een service.</span><span class="sxs-lookup"><span data-stu-id="619c5-164">Credential/Session may behave differently because the DSC agent runs as a service.</span></span>  <span data-ttu-id="619c5-165">Zorg ervoor dat testen functies hier end-to-end.</span><span class="sxs-lookup"><span data-stu-id="619c5-165">Be sure to test any features here end to end.</span></span>
- <span data-ttu-id="619c5-166">Fouten uitvoeren door `Start-DscConfiguration` mogelijk anders dan die worden weergegeven bij het aanroepen van de `Set-TargetResource` rechtstreeks werken.</span><span class="sxs-lookup"><span data-stu-id="619c5-166">Errors output by `Start-DscConfiguration` may be different than those displayed when calling the `Set-TargetResource` function directly.</span></span>

## <a name="test-compatability-on-all-dsc-supported-platforms"></a><span data-ttu-id="619c5-167">Ondersteunde platforms voor test-compatibiliteit op alle DSC</span><span class="sxs-lookup"><span data-stu-id="619c5-167">Test compatability on all DSC supported platforms</span></span>

<span data-ttu-id="619c5-168">Resource moet werken op alle DSC ondersteunde platforms (Windows Server 2008 R2 en hoger).</span><span class="sxs-lookup"><span data-stu-id="619c5-168">Resource should work on all DSC supported platforms (Windows Server 2008 R2 and newer).</span></span> <span data-ttu-id="619c5-169">Installeer de meest recente WMF (Windows Management Framework) van het besturingssysteem naar de meest recente versie van DSC.</span><span class="sxs-lookup"><span data-stu-id="619c5-169">Install the latest WMF (Windows Management Framework) on your OS to get the latest version of DSC.</span></span> <span data-ttu-id="619c5-170">Als uw resource standaard niet op sommige van deze platformen werkt, kan een specifiek foutbericht moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="619c5-170">If your resource does not work on some of these platforms by design, a specific error message should be returned.</span></span> <span data-ttu-id="619c5-171">Zorg er ook dat uw resource controleert of de cmdlets die u aanroept op bepaalde machine aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="619c5-171">Also, make sure your resource checks whether cmdlets you are calling are present on particular machine.</span></span> <span data-ttu-id="619c5-172">Windows Server 2012 toegevoegd een groot aantal nieuwe cmdlets die niet beschikbaar op Windows Server 2008R2, zelfs met WMF is geïnstalleerd zijn.</span><span class="sxs-lookup"><span data-stu-id="619c5-172">Windows Server 2012 added a large number of new cmdlets that are not available on Windows Server 2008R2, even with WMF installed.</span></span>

## <a name="verify-on-windows-client-if-applicable"></a><span data-ttu-id="619c5-173">Controleer of op Windows-Client (indien van toepassing)</span><span class="sxs-lookup"><span data-stu-id="619c5-173">Verify on Windows Client (if applicable)</span></span>

<span data-ttu-id="619c5-174">Een heel normaal test tussenruimte met het controleren van de resource alleen op server-versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="619c5-174">One very common test gap is verifying the resource only on server versions of Windows.</span></span> <span data-ttu-id="619c5-175">Veel resources ook zijn ontworpen om te werken op Client-SKU's, dus als dat is waar in uw geval, vergeet dan niet om dit te testen op deze platforms ook.</span><span class="sxs-lookup"><span data-stu-id="619c5-175">Many resources are also designed to work on Client SKUs, so if that’s true in your case, don’t forget to test it on those platforms as well.</span></span>

## <a name="get-dscresource-lists-the-resource"></a><span data-ttu-id="619c5-176">Sleutelwoorden Get-dscresource bieden geeft een lijst van de resource</span><span class="sxs-lookup"><span data-stu-id="619c5-176">Get-DSCResource lists the resource</span></span>

<span data-ttu-id="619c5-177">Na de implementatie van de module aanroepen `Get-DscResource` uw resource onder andere als gevolg hiervan moet weergeven.</span><span class="sxs-lookup"><span data-stu-id="619c5-177">After deploying the module, calling `Get-DscResource` should list your resource among others as a result.</span></span> <span data-ttu-id="619c5-178">Als u de resource niet in de lijst vinden, ervoor zorgen dat bestand schema.mof voor die bron bestaat.</span><span class="sxs-lookup"><span data-stu-id="619c5-178">If you can’t find your resource in the list, make sure that schema.mof file for that resource exists.</span></span>

## <a name="resource-module-contains-examples"></a><span data-ttu-id="619c5-179">Resource-module bevat voorbeelden</span><span class="sxs-lookup"><span data-stu-id="619c5-179">Resource module contains examples</span></span>

<span data-ttu-id="619c5-180">Het maken van het kwaliteitsvoorbeelden waarmee anderen te begrijpen hoe u deze.</span><span class="sxs-lookup"><span data-stu-id="619c5-180">Creating quality examples which will help others understand how to use it.</span></span> <span data-ttu-id="619c5-181">Dit is essentieel, met name omdat veel gebruikers voorbeeldcode als documentatie behandelen.</span><span class="sxs-lookup"><span data-stu-id="619c5-181">This is crucial, especially since many users treat sample code as documentation.</span></span>

- <span data-ttu-id="619c5-182">Eerst moet u de voorbeelden die wordt opgenomen met de module: ten minste bepalen, moet u belangrijkste use-cases dekking voor uw resource:</span><span class="sxs-lookup"><span data-stu-id="619c5-182">First, you should determine the examples that will be included with the module – at minimum, you should cover most important use cases for your resource:</span></span>
- <span data-ttu-id="619c5-183">Als uw module verschillende bronnen die nodig is om samen te werken voor een end-to-end-scenario bevat, zou de eenvoudige end-to-end-voorbeeld in het ideale geval eerste.</span><span class="sxs-lookup"><span data-stu-id="619c5-183">If your module contains several resources that need to work together for an end-to-end scenario, the basic end-to-end example would ideally be first.</span></span>
- <span data-ttu-id="619c5-184">De eerste voorbeelden zeer eenvoudig--moeten zijn aan de slag met uw resources in kleine beheerbare segmenten (bijvoorbeeld het maken van een nieuwe VHD)</span><span class="sxs-lookup"><span data-stu-id="619c5-184">The initial examples should be very simple -- how to get started with your resources in small manageable chunks (e.g. creating a new VHD)</span></span>
- <span data-ttu-id="619c5-185">Opeenvolgende voorbeelden te bouwen op deze voorbeelden (bijvoorbeeld een virtuele machine maken vanaf een VHD, VM, het wijzigen van de virtuele machine verwijderen) en geavanceerde functionaliteit (bijvoorbeeld een virtuele machine maken met het dynamisch geheugen)</span><span class="sxs-lookup"><span data-stu-id="619c5-185">Subsequent examples should build on those examples (e.g. creating a VM from a VHD, removing VM, modifying VM), and show advanced functionality (e.g. creating a VM with dynamic memory)</span></span>
- <span data-ttu-id="619c5-186">Van de voorbeeldconfiguraties als parameters moeten worden gebruikt (alle waarden moeten worden doorgegeven aan de configuratie als parameters en er mag geen waarden vastgelegd):</span><span class="sxs-lookup"><span data-stu-id="619c5-186">Example configurations should be parameterized (all values should be passed to the configuration as parameters and there should be no hardcoded values):</span></span>

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

- <span data-ttu-id="619c5-187">Het is raadzaam om op te nemen (opmerkingen van) voorbeeld van hoe u de configuratie met de werkelijke waarden aan het einde van de voorbeeld-script aanroept.</span><span class="sxs-lookup"><span data-stu-id="619c5-187">It’s a good practice to include (commented out) example of how to call the configuration with the actual values at the end of the example script.</span></span>
  <span data-ttu-id="619c5-188">Bijvoorbeeld, in de bovenstaande configuratie is niet altijd duidelijk dat de beste manier om op te geven van de UserAgent is:</span><span class="sxs-lookup"><span data-stu-id="619c5-188">For example, in the configuration above it isn't necessarily obvious that the best way to specify UserAgent is:</span></span>

  <span data-ttu-id="619c5-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` Een opmerking kunt in dat geval de beoogde uitvoering van de configuratie te verduidelijken:</span><span class="sxs-lookup"><span data-stu-id="619c5-189">`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer` In which case a comment can clarify the intended execution of the configuration:</span></span>

  ```powershell
  <#
  Sample use (parameter values need to be changed according to your scenario):

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

  Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
  -userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
  #>
  ```

- <span data-ttu-id="619c5-190">Voor elk voorbeeld een korte beschrijving waarin wordt uitgelegd wat het doet en de betekenis van de parameters te schrijven.</span><span class="sxs-lookup"><span data-stu-id="619c5-190">For each example, write a short description which explains what it does, and the meaning of the parameters.</span></span>
- <span data-ttu-id="619c5-191">Zorg ervoor dat de voorbeelden voor de meeste belangrijke scenario's voor uw resource en als er niets ontbreekt, Controleer of ze al worden uitgevoerd en machine in de gewenste status geplaatst.</span><span class="sxs-lookup"><span data-stu-id="619c5-191">Make sure examples cover most the important scenarios for your resource and if there’s nothing missing, verify that they all execute and put machine in the desired state.</span></span>

## <a name="error-messages-are-easy-to-understand-and-help-users-solve-problems"></a><span data-ttu-id="619c5-192">Foutberichten zijn eenvoudig te begrijpen en oplossen van problemen met gebruikers helpen</span><span class="sxs-lookup"><span data-stu-id="619c5-192">Error messages are easy to understand and help users solve problems</span></span>

<span data-ttu-id="619c5-193">Goede foutberichten moeten worden:</span><span class="sxs-lookup"><span data-stu-id="619c5-193">Good error messages should be:</span></span>

- <span data-ttu-id="619c5-194">Er zijn: Het grootste probleem met foutberichten is dat ze vaak niet bestaan, dus zorg ervoor dat ze zijn er.</span><span class="sxs-lookup"><span data-stu-id="619c5-194">There: The biggest problem with error messages is that they often don’t exist, so make sure they are there.</span></span>
- <span data-ttu-id="619c5-195">Gemakkelijk te begrijpen: Mens leesbaar, niet verborgen foutcodes</span><span class="sxs-lookup"><span data-stu-id="619c5-195">Easy to understand: Human readable, no obscure error codes</span></span>
- <span data-ttu-id="619c5-196">Nauwkeurige: Wat is er precies het probleem beschrijven</span><span class="sxs-lookup"><span data-stu-id="619c5-196">Precise: Describe what’s exactly the problem</span></span>
- <span data-ttu-id="619c5-197">Feitelijke: Advies over het oplossen van het probleem</span><span class="sxs-lookup"><span data-stu-id="619c5-197">Constructive: Advice how to fix the issue</span></span>
- <span data-ttu-id="619c5-198">Beleefd: Geen gebruiker zal of zodat ze ongeldige denkt</span><span class="sxs-lookup"><span data-stu-id="619c5-198">Polite: Don’t blame user or make them feel bad</span></span>

<span data-ttu-id="619c5-199">Zorg ervoor dat u fouten in de End-to-End scenario's controleren (met behulp van `Start-DscConfiguration`), omdat ze van die afwijken kunnen bij het uitvoeren van functies van resource rechtstreeks geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="619c5-199">Make sure you verify errors in End to End scenarios (using `Start-DscConfiguration`), because they may differ from those returned when running resource functions directly.</span></span>

## <a name="log-messages-are-easy-to-understand-and-informative-including-verbose-debug-and-etw-logs"></a><span data-ttu-id="619c5-200">Logboekberichten zijn gemakkelijk te begrijpen en informatieve (inclusief-verbose,-foutopsporing en ETW-Logboeken)</span><span class="sxs-lookup"><span data-stu-id="619c5-200">Log messages are easy to understand and informative (including –verbose, –debug and ETW logs)</span></span>

<span data-ttu-id="619c5-201">Zorg ervoor dat logboeken gegenereerd door de resource die eenvoudig te begrijpen en geef de waarde voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="619c5-201">Ensure that logs outputted by the resource are easy to understand and provide value to the user.</span></span> <span data-ttu-id="619c5-202">Resources moeten alle informatie die nuttig voor de gebruiker zijn kan uitvoeren, maar meer logboeken is niet altijd beter.</span><span class="sxs-lookup"><span data-stu-id="619c5-202">Resources should output all information which might be helpful to the user, but more logs is not always better.</span></span> <span data-ttu-id="619c5-203">U moet voorkomen van redundantie en gegevens die niet worden uitgevoerd bieden een extra waarde: iemand anders gaat u door de honderden logboekvermeldingen om te zoeken wat ze zoekt niet maken.</span><span class="sxs-lookup"><span data-stu-id="619c5-203">You should avoid redundancy and outputting data which does not provide additional value – don’t make someone go through hundreds of log entries in order to find what they're looking for.</span></span> <span data-ttu-id="619c5-204">Er zijn geen logboeken is natuurlijk niet een aanvaardbare oplossing voor dit probleem ofwel.</span><span class="sxs-lookup"><span data-stu-id="619c5-204">Of course, no logs is not an acceptable solution for this problem either.</span></span>

<span data-ttu-id="619c5-205">Wanneer u test, u moet ook uitgebreide analyseren en fouten opsporen in Logboeken (door het uitvoeren van `Start-DscConfiguration` met `–Verbose` en `–Debug` op de juiste wijze verandert), ook als ETW-Logboeken.</span><span class="sxs-lookup"><span data-stu-id="619c5-205">When testing, you should also analyze verbose and debug logs (by running `Start-DscConfiguration` with `–Verbose` and `–Debug` switches appropriately), as well as ETW logs.</span></span> <span data-ttu-id="619c5-206">DSC-ETW-logboeken bekijken, gaat u naar Logboeken en opent u de volgende map: Applications and Services- Microsoft - Windows - Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="619c5-206">To see DSC ETW logs, go to Event Viewer and open the following folder: Applications and Services- Microsoft - Windows - Desired State Configuration.</span></span>  <span data-ttu-id="619c5-207">Er standaard worden operationele kanaal, maar zorg ervoor dat u inschakelt analytische en foutopsporing van kanalen voordat de configuratie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="619c5-207">By default there will be Operational channel, but make sure you enable Analytic and Debug channels before running the configuration.</span></span>
<span data-ttu-id="619c5-208">Om in te schakelen analytische/Debug kanalen, kunt u onderstaande script uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="619c5-208">To enable Analytic/Debug channels, you can execute script below:</span></span>

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

## <a name="resource-implementation-does-not-contain-hardcoded-paths"></a><span data-ttu-id="619c5-209">Resource-implementatie bevat geen vastgelegd paden</span><span class="sxs-lookup"><span data-stu-id="619c5-209">Resource implementation does not contain hardcoded paths</span></span>

<span data-ttu-id="619c5-210">Zorg ervoor dat er zijn geen paden vastgelegd in de resource-implementatie, met name als ze gaan ervan uit taal (en-us), of wanneer er systeemvariabelen die kunnen worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="619c5-210">Ensure there are no hardcoded paths in the resource implementation, particularly if they assume language (en-us), or when there are system variables that can be used.</span></span>
<span data-ttu-id="619c5-211">Als de bron nodig hebt voor toegang tot specifieke paden, omgevingsvariabelen gebruiken in plaats van hardcoderen het pad, omdat dit anders op andere computers zijn kan.</span><span class="sxs-lookup"><span data-stu-id="619c5-211">If your resource need to access specific paths, use environment variables instead of hardcoding the path, as it may differ on other machines.</span></span>

<span data-ttu-id="619c5-212">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="619c5-212">Example:</span></span>

<span data-ttu-id="619c5-213">In plaats van:</span><span class="sxs-lookup"><span data-stu-id="619c5-213">Instead of:</span></span>

```powershell
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
```

<span data-ttu-id="619c5-214">U kunt schrijven:</span><span class="sxs-lookup"><span data-stu-id="619c5-214">You can write:</span></span>

```powershell
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)}
```

## <a name="resource-implementation-does-not-contain-user-information"></a><span data-ttu-id="619c5-215">Resource-implementatie bevatten geen gebruikersgegevens</span><span class="sxs-lookup"><span data-stu-id="619c5-215">Resource implementation does not contain user information</span></span>

<span data-ttu-id="619c5-216">Zorg ervoor dat er zijn geen e-namen, accountgegevens of namen van personen in de code.</span><span class="sxs-lookup"><span data-stu-id="619c5-216">Make sure there are no email names, account information, or names of people in the code.</span></span>

## <a name="resource-was-tested-with-validinvalid-credentials"></a><span data-ttu-id="619c5-217">Resource is getest met de referenties geldig/ongeldig</span><span class="sxs-lookup"><span data-stu-id="619c5-217">Resource was tested with valid/invalid credentials</span></span>

<span data-ttu-id="619c5-218">Als de resource een referentie als parameter:</span><span class="sxs-lookup"><span data-stu-id="619c5-218">If your resource takes a credential as parameter:</span></span>

- <span data-ttu-id="619c5-219">Controleer of de resource-werkt als lokaal systeem (of het computeraccount voor de externe bronnen) heeft geen toegang.</span><span class="sxs-lookup"><span data-stu-id="619c5-219">Verify the resource works when Local System (or the computer account for remote resources) does not have access.</span></span>
- <span data-ttu-id="619c5-220">Controleer of de resource werkt met een referentie opgegeven voor ophalen, instellen en testen</span><span class="sxs-lookup"><span data-stu-id="619c5-220">Verify the resource works with a credential specified for Get, Set and Test</span></span>
- <span data-ttu-id="619c5-221">Als uw resource toegang heeft tot de shares, test u alle varianten die u ondersteunen wilt, zoals:</span><span class="sxs-lookup"><span data-stu-id="619c5-221">If your resource accesses shares, test all the variants you need to support, such as:</span></span>
  - <span data-ttu-id="619c5-222">Standaard windows-shares.</span><span class="sxs-lookup"><span data-stu-id="619c5-222">Standard windows shares.</span></span>
  - <span data-ttu-id="619c5-223">DFS-shares.</span><span class="sxs-lookup"><span data-stu-id="619c5-223">DFS shares.</span></span>
  - <span data-ttu-id="619c5-224">SAMBA-shares (als u ondersteuning voor Linux.)</span><span class="sxs-lookup"><span data-stu-id="619c5-224">SAMBA shares (if you want to support Linux.)</span></span>

## <a name="resource-does-not-require-interactive-input"></a><span data-ttu-id="619c5-225">Resource is niet vereist voor interactieve invoer</span><span class="sxs-lookup"><span data-stu-id="619c5-225">Resource does not require interactive input</span></span>

<span data-ttu-id="619c5-226">**Get/Set/Test-TargetResource** functies automatisch moet worden uitgevoerd en moet u niet wachten voor de invoer van gebruiker tijdens elke fase van de uitvoering (bijv. Gebruik geen `Get-Credential` binnen deze functies).</span><span class="sxs-lookup"><span data-stu-id="619c5-226">**Get/Set/Test-TargetResource** functions should be executed automatically and must not wait for user’s input at any stage of execution (e.g. you should not use `Get-Credential` inside these functions).</span></span> <span data-ttu-id="619c5-227">Als u nodig hebt voor de invoer van gebruiker, moet u deze doorgeven aan de configuratie als parameter tijdens de compilatie-fase.</span><span class="sxs-lookup"><span data-stu-id="619c5-227">If you need to provide user’s input, you should pass it to the configuration as parameter during the compilation phase.</span></span>

## <a name="resource-functionality-was-thoroughly-tested"></a><span data-ttu-id="619c5-228">Resourcefunctionaliteit is uitgebreid getest.</span><span class="sxs-lookup"><span data-stu-id="619c5-228">Resource functionality was thoroughly tested</span></span>

<span data-ttu-id="619c5-229">Deze controlelijst bevat de items die zijn belangrijk om te worden getest en/of vaak zijn gemist.</span><span class="sxs-lookup"><span data-stu-id="619c5-229">This checklist contains items which are important to be tested and/or are often missed.</span></span> <span data-ttu-id="619c5-230">Er is aantal tests, voornamelijk functionele labels die specifiek zijn voor de resource die u wilt testen en niet hier worden vermeld.</span><span class="sxs-lookup"><span data-stu-id="619c5-230">There will be bunch of tests, mainly functional ones which will be specific to the resource you are testing and are not mentioned here.</span></span> <span data-ttu-id="619c5-231">Vergeet niet over negatieve Testscenario's.</span><span class="sxs-lookup"><span data-stu-id="619c5-231">Don’t forget about negative test cases.</span></span>

## <a name="best-practice-resource-module-contains-tests-folder-with-resourcedesignertestsps1-script"></a><span data-ttu-id="619c5-232">Aanbevolen: Resource-module bevat de map Tests met ResourceDesignerTests.ps1 script</span><span class="sxs-lookup"><span data-stu-id="619c5-232">Best practice: Resource module contains Tests folder with ResourceDesignerTests.ps1 script</span></span>

<span data-ttu-id="619c5-233">Het is raadzaam om te maken van de map 'Test' in resource-module, maken `ResourceDesignerTests.ps1` bestand en voeg toe met behulp van tests **Test xDscResource** en **Test xDscSchema** voor alle resources in bepaalde module.</span><span class="sxs-lookup"><span data-stu-id="619c5-233">It’s a good practice to create folder “Tests” inside resource module, create `ResourceDesignerTests.ps1` file and add tests using **Test-xDscResource** and **Test-xDscSchema** for all resources in given module.</span></span>
<span data-ttu-id="619c5-234">Op deze manier kunt u snel schema's van alle resources uit het opgegeven modules en voert u een sanity controleren voordat u publiceert valideren.</span><span class="sxs-lookup"><span data-stu-id="619c5-234">This way you can quickly validate schemas of all resources from the given modules and do a sanity check before publishing.</span></span>
<span data-ttu-id="619c5-235">Voor xRemoteFile, `ResourceTests.ps1` kan net zo eenvoudig als zoeken:</span><span class="sxs-lookup"><span data-stu-id="619c5-235">For xRemoteFile, `ResourceTests.ps1` could look as simple as:</span></span>

```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## <a name="best-practice-resource-folder-contains-resource-designer-script-for-generating-schema"></a><span data-ttu-id="619c5-236">Aanbevolen: Resource-map bevat de ontwerperscript resource voor het genereren van schema</span><span class="sxs-lookup"><span data-stu-id="619c5-236">Best practice: Resource folder contains resource designer script for generating schema</span></span>

<span data-ttu-id="619c5-237">Elke bron moet een resource designer script een mof-schema van de resource genereert bevatten.</span><span class="sxs-lookup"><span data-stu-id="619c5-237">Each resource should contain a resource designer script which generates a mof schema of the resource.</span></span> <span data-ttu-id="619c5-238">Dit bestand moet worden geplaatst `<ResourceName>\ResourceDesignerScripts` en de naam genereren `<ResourceName>Schema.ps1` voor xRemoteFile resource dit bestand kan worden aangeroepen `GenerateXRemoteFileSchema.ps1` en bevatten:</span><span class="sxs-lookup"><span data-stu-id="619c5-238">This file should be placed in `<ResourceName>\ResourceDesignerScripts` and be named Generate `<ResourceName>Schema.ps1` For xRemoteFile resource this file would be called `GenerateXRemoteFileSchema.ps1` and contain:</span></span>

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

## <a name="best-practice-resource-supports--whatif"></a><span data-ttu-id="619c5-239">Aanbevolen: Resource ondersteunt - WhatIf</span><span class="sxs-lookup"><span data-stu-id="619c5-239">Best practice: Resource supports -WhatIf</span></span>

<span data-ttu-id="619c5-240">Als uw resource 'gevaarlijke' bewerkingen uitvoert, is het raadzaam om te implementeren `-WhatIf` functionaliteit.</span><span class="sxs-lookup"><span data-stu-id="619c5-240">If your resource is performing “dangerous” operations, it’s a good practice to implement `-WhatIf` functionality.</span></span> <span data-ttu-id="619c5-241">Nadat dit voltooid, controleert u of `-WhatIf` uitvoer beschrijft correct bewerkingen die er gebeuren zou als de opdracht is uitgevoerd zonder `-WhatIf` overschakelen.</span><span class="sxs-lookup"><span data-stu-id="619c5-241">After it’s done, make sure that `-WhatIf` output correctly describes operations which would happen if command was executed without `-WhatIf` switch.</span></span>
<span data-ttu-id="619c5-242">Controleer ook of bewerkingen wordt niet uitgevoerd (de status van het knooppunt worden niet gewijzigd) als `–WhatIf` switch aanwezig is.</span><span class="sxs-lookup"><span data-stu-id="619c5-242">Also, verify that operations does not execute (no changes to the node’s state are made) when `–WhatIf` switch is present.</span></span>
<span data-ttu-id="619c5-243">Bijvoorbeeld, Stel dat we bestandsresource test.</span><span class="sxs-lookup"><span data-stu-id="619c5-243">For example, let’s assume we are testing File resource.</span></span> <span data-ttu-id="619c5-244">Hieronder vindt u eenvoudige configuratie die zorgt voor bestand `test.txt` met inhoud van 'test':</span><span class="sxs-lookup"><span data-stu-id="619c5-244">Below is simple configuration which creates file `test.txt` with contents “test”:</span></span>

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

<span data-ttu-id="619c5-245">Als we compileren en uitvoeren van de configuratie met de `-WhatIf` switch, de uitvoer is laat ons weten dat precies wat gebeurt er wanneer we de configuratie uitvoert.</span><span class="sxs-lookup"><span data-stu-id="619c5-245">If we compile and then execute the configuration with the `-WhatIf` switch, the output is telling us exactly what would happen when we run the configuration.</span></span> <span data-ttu-id="619c5-246">Tot wel is niet worden uitgevoerd door de configuratie zelf (`test.txt` bestand is niet gemaakt).</span><span class="sxs-lookup"><span data-stu-id="619c5-246">The configuration itself however was not executed (`test.txt` file was not created).</span></span>

```powershell
Start-DscConfiguration -Path .\config -ComputerName localhost -Wait -Verbose -WhatIf
```

```output
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

<span data-ttu-id="619c5-247">Deze lijst is niet volledig, maar het geeft veel belangrijke problemen die kunnen worden aangetroffen tijdens het ontwerpen, ontwikkelen en testen van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="619c5-247">This list is not exhaustive, but it covers many important issues which can be encountered while designing, developing and testing DSC resources.</span></span>
