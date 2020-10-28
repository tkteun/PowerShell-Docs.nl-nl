---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Import-DSCResource gebruiken
description: Import-DSCResource is een dynamisch sleutel woord dat alleen kan worden gebruikt binnen een configuratie script blok. Het wordt gebruikt voor het importeren van de resource modules die nodig zijn in uw configuratie.
ms.openlocfilehash: f6dcad2c56848ec25eb79332c96fe6b0d438fe95
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658508"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="09ce5-105">Import-DSCResource gebruiken</span><span class="sxs-lookup"><span data-stu-id="09ce5-105">Using Import-DSCResource</span></span>

<span data-ttu-id="09ce5-106">`Import-DSCResource` is een dynamisch sleutel woord dat alleen kan worden gebruikt binnen een configuratie script blok om alle resources te importeren die nodig zijn in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="09ce5-106">`Import-DSCResource` is a dynamic keyword, which can only be used inside a Configuration script block to import any resources needed in your Configuration.</span></span> <span data-ttu-id="09ce5-107">Resources onder `$PSHOME` worden automatisch geïmporteerd, maar worden nog steeds beschouwd als best practice voor het expliciet importeren van alle resources die worden gebruikt in uw [configuratie](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="09ce5-107">Resources under `$PSHOME` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="09ce5-108">De syntaxis voor `Import-DSCResource` wordt hieronder weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="09ce5-108">The syntax for `Import-DSCResource` is shown below.</span></span> <span data-ttu-id="09ce5-109">Wanneer u modules op naam opgeeft, is het een vereiste om elk op een nieuwe regel te vermelden.</span><span class="sxs-lookup"><span data-stu-id="09ce5-109">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|    <span data-ttu-id="09ce5-110">Parameter</span><span class="sxs-lookup"><span data-stu-id="09ce5-110">Parameter</span></span>     |                                                                                                                      <span data-ttu-id="09ce5-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="09ce5-111">Description</span></span>                                                                                                                      |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-Name`          | <span data-ttu-id="09ce5-112">De DSC-resource naam (s) die u moet importeren.</span><span class="sxs-lookup"><span data-stu-id="09ce5-112">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="09ce5-113">Als de module naam is opgegeven, zoekt de opdracht naar deze DSC-resources in deze module; anders wordt met de opdracht gezocht in de DSC-resources in alle DSC-resource paden.</span><span class="sxs-lookup"><span data-stu-id="09ce5-113">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="09ce5-114">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="09ce5-114">Wildcards are supported.</span></span> |
| `-ModuleName`    | <span data-ttu-id="09ce5-115">De module naam of module specificatie.</span><span class="sxs-lookup"><span data-stu-id="09ce5-115">The module name, or module specification.</span></span>  <span data-ttu-id="09ce5-116">Als u resources opgeeft om te importeren uit een module, probeert de opdracht alleen die resources te importeren.</span><span class="sxs-lookup"><span data-stu-id="09ce5-116">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="09ce5-117">Als u alleen de module opgeeft, worden alle DSC-resources in de module geïmporteerd met de opdracht.</span><span class="sxs-lookup"><span data-stu-id="09ce5-117">If you specify the module only, the command imports all the DSC resources in the module.</span></span>            |
| `-ModuleVersion` | <span data-ttu-id="09ce5-118">Vanaf Power shell 5,0 kunt u opgeven welke versie van een module een configuratie moet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="09ce5-118">Beginning in PowerShell 5.0, you can specify which version of a module a configuration should use.</span></span> <span data-ttu-id="09ce5-119">Zie [een specifieke versie van een geïnstalleerde resource importeren](sxsresource.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="09ce5-119">For more information, see [Import a specific version of an installed resource](sxsresource.md).</span></span>                                                    |

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="09ce5-120">Voor beeld: Import-DSCResource gebruiken in een configuratie</span><span class="sxs-lookup"><span data-stu-id="09ce5-120">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> <span data-ttu-id="09ce5-121">Het opgeven van meerdere waarden voor de namen van resource namen en modules in dezelfde opdracht wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="09ce5-121">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span>
> <span data-ttu-id="09ce5-122">Het kan een niet-deterministisch gedrag hebben over welke resource moet worden geladen, voor het geval dezelfde resource in meerdere modules bestaat.</span><span class="sxs-lookup"><span data-stu-id="09ce5-122">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="09ce5-123">De onderstaande opdracht resulteert in een fout tijdens de compilatie.</span><span class="sxs-lookup"><span data-stu-id="09ce5-123">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="09ce5-124">Overwegingen bij het gebruik van alleen de para meter name:</span><span class="sxs-lookup"><span data-stu-id="09ce5-124">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="09ce5-125">Het is een resource-intensieve bewerking, afhankelijk van het aantal modules dat op de computer is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="09ce5-125">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="09ce5-126">Hiermee wordt de eerste resource geladen die met de opgegeven naam is gevonden.</span><span class="sxs-lookup"><span data-stu-id="09ce5-126">It will load the first resource found with the given name.</span></span> <span data-ttu-id="09ce5-127">Als er meer dan één resource met dezelfde naam is geïnstalleerd, kan de verkeerde resource worden geladen.</span><span class="sxs-lookup"><span data-stu-id="09ce5-127">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="09ce5-128">Het aanbevolen gebruik moet worden opgegeven `–ModuleName` met de `-Name` para meter, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="09ce5-128">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="09ce5-129">Dit gebruik heeft de volgende voor delen:</span><span class="sxs-lookup"><span data-stu-id="09ce5-129">This usage has the following benefits:</span></span>

- <span data-ttu-id="09ce5-130">Het vermindert de invloed op de prestaties doordat het zoek bereik voor de opgegeven resource wordt beperkt.</span><span class="sxs-lookup"><span data-stu-id="09ce5-130">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="09ce5-131">Hiermee wordt expliciet de module gedefinieerd waarmee de resource wordt gedefinieerd, zodat de juiste resource wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="09ce5-131">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="09ce5-132">In Power shell 5,0 kunnen DSC-resources meerdere versies hebben en kunnen versies worden geïnstalleerd op een computer naast elkaar.</span><span class="sxs-lookup"><span data-stu-id="09ce5-132">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="09ce5-133">Dit wordt geïmplementeerd door meerdere versies van een resource module te hebben die zich in dezelfde module map bevinden.</span><span class="sxs-lookup"><span data-stu-id="09ce5-133">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span> <span data-ttu-id="09ce5-134">Zie [resources met meerdere versies gebruiken](sxsresource.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="09ce5-134">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="09ce5-135">IntelliSense met Import-DSCResource</span><span class="sxs-lookup"><span data-stu-id="09ce5-135">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="09ce5-136">Bij het ontwerpen van de DSC-configuratie in ISE biedt Power shell IntelliSence voor resources en resource-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="09ce5-136">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="09ce5-137">Bron definities onder het `$pshome` pad naar de module worden automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="09ce5-137">Resource definitions under the `$pshome` module path are loaded automatically.</span></span>
<span data-ttu-id="09ce5-138">Wanneer u resources importeert met behulp van het `Import-DSCResource` tref woord, worden de opgegeven resource definities toegevoegd en wordt IntelliSense uitgebreid met het schema van de geïmporteerde resource.</span><span class="sxs-lookup"><span data-stu-id="09ce5-138">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![IntelliSense in het ISE voor een DSC-resource](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="09ce5-140">Vanaf Power shell 5,0 is het tabblad voltooiings punt toegevoegd aan de ISE voor DSC-resources en de bijbehorende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="09ce5-140">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="09ce5-141">Zie [resources](../resources/resources.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="09ce5-141">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="09ce5-142">Bij het compileren van de configuratie gebruikt Power shell de geïmporteerde resource definities om alle resource blokken in de configuratie te valideren.</span><span class="sxs-lookup"><span data-stu-id="09ce5-142">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span> <span data-ttu-id="09ce5-143">Elk resource blok wordt gevalideerd, met behulp van de schema definitie van de resource, voor de volgende regels.</span><span class="sxs-lookup"><span data-stu-id="09ce5-143">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="09ce5-144">Alleen de eigenschappen die in het schema zijn gedefinieerd, worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="09ce5-144">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="09ce5-145">De gegevens typen voor elke eigenschap zijn juist.</span><span class="sxs-lookup"><span data-stu-id="09ce5-145">The data types for each property are correct.</span></span>
- <span data-ttu-id="09ce5-146">De eigenschappen van de sleutels zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="09ce5-146">Keys properties are specified.</span></span>
- <span data-ttu-id="09ce5-147">Er wordt geen alleen-lezen-eigenschap gebruikt.</span><span class="sxs-lookup"><span data-stu-id="09ce5-147">No read-only property is used.</span></span>
- <span data-ttu-id="09ce5-148">Validatie van typen van de waarde-toewijzingen.</span><span class="sxs-lookup"><span data-stu-id="09ce5-148">Validation on value maps types.</span></span>

<span data-ttu-id="09ce5-149">Houd rekening met de volgende configuratie:</span><span class="sxs-lookup"><span data-stu-id="09ce5-149">Consider the following configuration:</span></span>

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

<span data-ttu-id="09ce5-150">Het compileren van deze configuratie resulteert in een fout.</span><span class="sxs-lookup"><span data-stu-id="09ce5-150">Compiling this Configuration results in an error.</span></span>

```Output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or
valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values:
Present, Absent.
```

<span data-ttu-id="09ce5-151">Met IntelliSense en schema validatie kunt u meer fouten tijdens de parsering-en compilatie tijd ondervangen, waardoor complicaties tijdens de uitvoering worden voor komen.</span><span class="sxs-lookup"><span data-stu-id="09ce5-151">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="09ce5-152">Elke DSC-resource kan een naam hebben en een **FriendlyName** die is gedefinieerd in het schema van de resource.</span><span class="sxs-lookup"><span data-stu-id="09ce5-152">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="09ce5-153">Hieronder ziet u de eerste twee regels van ' MSFT_ServiceResource. Shema. mof '.</span><span class="sxs-lookup"><span data-stu-id="09ce5-153">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
>
> <span data-ttu-id="09ce5-154">Wanneer u deze bron in een configuratie gebruikt, kunt u **MSFT_ServiceResource** of **service** opgeven.</span><span class="sxs-lookup"><span data-stu-id="09ce5-154">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service** .</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="09ce5-155">Verschillen Power shell v4 en V5</span><span class="sxs-lookup"><span data-stu-id="09ce5-155">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="09ce5-156">Er zijn meerdere verschillen die u ziet bij het ontwerpen van configuraties in Power Shell 4,0 versus Power shell 5,0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="09ce5-156">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="09ce5-157">In deze sectie worden de verschillen gemarkeerd die relevant zijn voor dit artikel.</span><span class="sxs-lookup"><span data-stu-id="09ce5-157">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="09ce5-158">Meerdere resource versies</span><span class="sxs-lookup"><span data-stu-id="09ce5-158">Multiple Resource Versions</span></span>

<span data-ttu-id="09ce5-159">Het installeren en gebruiken van meerdere versies van resources naast elkaar werd niet ondersteund in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="09ce5-159">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="09ce5-160">Als u problemen ondervindt bij het importeren van resources in uw configuratie, moet u ervoor zorgen dat er slechts één versie van de bron is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="09ce5-160">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="09ce5-161">In de onderstaande afbeelding zijn twee versies van de module **xPSDesiredStateConfiguration** geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="09ce5-161">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Er zijn meerdere resource versies geïnstalleerd in de map](media/import-dscresource/multiple-resource-versions-broken.png)

<span data-ttu-id="09ce5-163">Kopieer de inhoud van de gewenste module versie naar het hoogste niveau van de module directory.</span><span class="sxs-lookup"><span data-stu-id="09ce5-163">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Kopieer de gewenste versie naar de map op het hoogste niveau van de module](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="09ce5-165">Resourcelocatie</span><span class="sxs-lookup"><span data-stu-id="09ce5-165">Resource location</span></span>

<span data-ttu-id="09ce5-166">Bij het ontwerpen en compileren van configuraties kunnen uw resources worden opgeslagen in een map die is opgegeven door uw [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="09ce5-166">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path).</span></span>
<span data-ttu-id="09ce5-167">In Power Shell 4,0 moeten alle DSC-resource modules zijn opgeslagen onder Program Files\WindowsPowerShell\Modules of `$pshome\Modules` .</span><span class="sxs-lookup"><span data-stu-id="09ce5-167">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="09ce5-168">Vanaf Power shell 5,0 is deze vereiste verwijderd en kunnen resource modules worden opgeslagen in een map die is opgegeven door `PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="09ce5-168">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

### <a name="moduleversion-added"></a><span data-ttu-id="09ce5-169">ModuleVersion toegevoegd</span><span class="sxs-lookup"><span data-stu-id="09ce5-169">ModuleVersion added</span></span>

<span data-ttu-id="09ce5-170">Vanaf Power shell 5,0 `-ModuleVersion` kunt u met de para meter opgeven welke versie van een module moet worden gebruikt in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="09ce5-170">Beginning in PowerShell 5.0, the `-ModuleVersion` parameter allows you to specify which version of a module to use within your configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="09ce5-171">Zie ook</span><span class="sxs-lookup"><span data-stu-id="09ce5-171">See also</span></span>

- [<span data-ttu-id="09ce5-172">Bronnen</span><span class="sxs-lookup"><span data-stu-id="09ce5-172">Resources</span></span>](../resources/resources.md)
