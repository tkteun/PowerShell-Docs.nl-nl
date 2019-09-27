---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Import-DSCResource gebruiken
ms.openlocfilehash: 735b2c2b4ae5101ded333768f00b46cb54d541b0
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323015"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="9c25e-103">Import-DSCResource gebruiken</span><span class="sxs-lookup"><span data-stu-id="9c25e-103">Using Import-DSCResource</span></span>

<span data-ttu-id="9c25e-104">`Import-DScResource`is een dynamisch sleutel woord dat alleen kan worden gebruikt binnen een configuratie script blok.</span><span class="sxs-lookup"><span data-stu-id="9c25e-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="9c25e-105">Het `Import-DSCResource` sleutel woord voor het importeren van alle resources die nodig zijn in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="9c25e-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="9c25e-106">Resources onder `$pshome` worden automatisch geïmporteerd, maar worden nog steeds beschouwd als best practice voor het expliciet importeren van alle resources die worden gebruikt in uw [configuratie](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="9c25e-106">Resources under `$pshome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="9c25e-107">De syntaxis voor `Import-DSCResource` wordt hieronder weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9c25e-107">The syntax for `Import-DSCResource` is shown below.</span></span>  <span data-ttu-id="9c25e-108">Wanneer u modules op naam opgeeft, is het een vereiste om elk op een nieuwe regel te vermelden.</span><span class="sxs-lookup"><span data-stu-id="9c25e-108">When specifying modules by name, it is a requirement to list each on a new line.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|<span data-ttu-id="9c25e-109">Parameter</span><span class="sxs-lookup"><span data-stu-id="9c25e-109">Parameter</span></span>  |<span data-ttu-id="9c25e-110">Description</span><span class="sxs-lookup"><span data-stu-id="9c25e-110">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="9c25e-111">De DSC-resource naam (s) die u moet importeren.</span><span class="sxs-lookup"><span data-stu-id="9c25e-111">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="9c25e-112">Als de module naam is opgegeven, zoekt de opdracht naar deze DSC-resources in deze module; anders wordt met de opdracht gezocht in de DSC-resources in alle DSC-resource paden.</span><span class="sxs-lookup"><span data-stu-id="9c25e-112">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="9c25e-113">Joker tekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9c25e-113">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="9c25e-114">De module naam of module specificatie.</span><span class="sxs-lookup"><span data-stu-id="9c25e-114">The module name, or module specification.</span></span>  <span data-ttu-id="9c25e-115">Als u resources opgeeft om te importeren uit een module, probeert de opdracht alleen die resources te importeren.</span><span class="sxs-lookup"><span data-stu-id="9c25e-115">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="9c25e-116">Als u alleen de module opgeeft, worden alle DSC-resources in de module geïmporteerd met de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9c25e-116">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="9c25e-117">Voorbeeld: Import-Dscresource bieden binnen een configuratie gebruiken</span><span class="sxs-lookup"><span data-stu-id="9c25e-117">Example: Use Import-DSCResource within a configuration</span></span>

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> <span data-ttu-id="9c25e-118">Het opgeven van meerdere waarden voor de namen van resource namen en modules in dezelfde opdracht wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9c25e-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="9c25e-119">Het kan een niet-deterministisch gedrag hebben over welke resource moet worden geladen, voor het geval dezelfde resource in meerdere modules bestaat.</span><span class="sxs-lookup"><span data-stu-id="9c25e-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="9c25e-120">De onderstaande opdracht resulteert in een fout tijdens de compilatie.</span><span class="sxs-lookup"><span data-stu-id="9c25e-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="9c25e-121">Overwegingen bij het gebruik van alleen de para meter name:</span><span class="sxs-lookup"><span data-stu-id="9c25e-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="9c25e-122">Het is een resource-intensieve bewerking, afhankelijk van het aantal modules dat op de computer is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9c25e-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="9c25e-123">Hiermee wordt de eerste resource geladen die met de opgegeven naam is gevonden.</span><span class="sxs-lookup"><span data-stu-id="9c25e-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="9c25e-124">Als er meer dan één resource met dezelfde naam is geïnstalleerd, kan de verkeerde resource worden geladen.</span><span class="sxs-lookup"><span data-stu-id="9c25e-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="9c25e-125">Het aanbevolen gebruik moet worden opgegeven `–ModuleName` met de `-Name` para meter, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="9c25e-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="9c25e-126">Dit gebruik heeft de volgende voor delen:</span><span class="sxs-lookup"><span data-stu-id="9c25e-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="9c25e-127">Het vermindert de invloed op de prestaties doordat het zoek bereik voor de opgegeven resource wordt beperkt.</span><span class="sxs-lookup"><span data-stu-id="9c25e-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="9c25e-128">Hiermee wordt expliciet de module gedefinieerd waarmee de resource wordt gedefinieerd, zodat de juiste resource wordt geladen.</span><span class="sxs-lookup"><span data-stu-id="9c25e-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="9c25e-129">In Power shell 5,0 kunnen DSC-resources meerdere versies hebben en kunnen versies worden geïnstalleerd op een computer naast elkaar.</span><span class="sxs-lookup"><span data-stu-id="9c25e-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="9c25e-130">Dit wordt geïmplementeerd door meerdere versies van een resource module te hebben die zich in dezelfde module map bevinden.</span><span class="sxs-lookup"><span data-stu-id="9c25e-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="9c25e-131">Zie [resources met meerdere versies gebruiken](sxsresource.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c25e-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="9c25e-132">IntelliSense met import-Dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="9c25e-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="9c25e-133">Bij het ontwerpen van de DSC-configuratie in ISE biedt Power shell IntelliSence voor resources en resource-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="9c25e-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="9c25e-134">Bron definities onder het `$pshome` pad naar de module worden automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="9c25e-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="9c25e-135">Wanneer u resources importeert met behulp van het `Import-DSCResource` tref woord, worden de opgegeven resource definities toegevoegd en wordt IntelliSense uitgebreid met het schema van de geïmporteerde resource.</span><span class="sxs-lookup"><span data-stu-id="9c25e-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Resource IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="9c25e-137">Vanaf Power shell 5,0 is het tabblad voltooiings punt toegevoegd aan de ISE voor DSC-resources en de bijbehorende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="9c25e-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="9c25e-138">Zie [resources](../resources/resources.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c25e-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="9c25e-139">Bij het compileren van de configuratie gebruikt Power shell de geïmporteerde resource definities om alle resource blokken in de configuratie te valideren.</span><span class="sxs-lookup"><span data-stu-id="9c25e-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="9c25e-140">Elk resource blok wordt gevalideerd, met behulp van de schema definitie van de resource, voor de volgende regels.</span><span class="sxs-lookup"><span data-stu-id="9c25e-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="9c25e-141">Alleen de eigenschappen die in het schema zijn gedefinieerd, worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9c25e-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="9c25e-142">De gegevens typen voor elke eigenschap zijn juist.</span><span class="sxs-lookup"><span data-stu-id="9c25e-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="9c25e-143">De eigenschappen van de sleutels zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9c25e-143">Keys properties are specified.</span></span>
- <span data-ttu-id="9c25e-144">Er wordt geen alleen-lezen-eigenschap gebruikt.</span><span class="sxs-lookup"><span data-stu-id="9c25e-144">No read-only property is used.</span></span>
- <span data-ttu-id="9c25e-145">Validatie van typen van de waarde-toewijzingen.</span><span class="sxs-lookup"><span data-stu-id="9c25e-145">Validation on value maps types.</span></span>

<span data-ttu-id="9c25e-146">Houd rekening met de volgende configuratie:</span><span class="sxs-lookup"><span data-stu-id="9c25e-146">Consider the following configuration:</span></span>

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

<span data-ttu-id="9c25e-147">Het compileren van deze configuratie resulteert in een fout.</span><span class="sxs-lookup"><span data-stu-id="9c25e-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="9c25e-148">Met IntelliSense en schema validatie kunt u meer fouten tijdens de parsering-en compilatie tijd ondervangen, waardoor complicaties tijdens de uitvoering worden voor komen.</span><span class="sxs-lookup"><span data-stu-id="9c25e-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="9c25e-149">Elke DSC-resource kan een naam hebben en een **FriendlyName** die is gedefinieerd in het schema van de resource.</span><span class="sxs-lookup"><span data-stu-id="9c25e-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="9c25e-150">Hieronder vindt u de eerste twee regels van ' MSFT_ServiceResource. Shema. mof '.</span><span class="sxs-lookup"><span data-stu-id="9c25e-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="9c25e-151">Wanneer u deze bron in een configuratie gebruikt, kunt u **MSFT_ServiceResource** of **service**opgeven.</span><span class="sxs-lookup"><span data-stu-id="9c25e-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="9c25e-152">Verschillen Power shell v4 en V5</span><span class="sxs-lookup"><span data-stu-id="9c25e-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="9c25e-153">Er zijn meerdere verschillen die u ziet tijdens het ontwerpen van configuraties in Power Shell 4,0 vs. Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="9c25e-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="9c25e-154">In deze sectie worden de verschillen gemarkeerd die relevant zijn voor dit artikel.</span><span class="sxs-lookup"><span data-stu-id="9c25e-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="9c25e-155">Meerdere resource versies</span><span class="sxs-lookup"><span data-stu-id="9c25e-155">Multiple Resource Versions</span></span>

<span data-ttu-id="9c25e-156">Het installeren en gebruiken van meerdere versies van resources naast elkaar werd niet ondersteund in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="9c25e-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="9c25e-157">Als u problemen ondervindt bij het importeren van resources in uw configuratie, moet u ervoor zorgen dat er slechts één versie van de bron is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9c25e-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="9c25e-158">In de onderstaande afbeelding zijn twee versies van de module **xPSDesiredStateConfiguration** geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="9c25e-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Er zijn meerdere resource versies opgelost](../media/multiple-resource-versions-broken.png)

<span data-ttu-id="9c25e-160">Kopieer de inhoud van de gewenste module versie naar het hoogste niveau van de module directory.</span><span class="sxs-lookup"><span data-stu-id="9c25e-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Er zijn meerdere resource versies opgelost](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a><span data-ttu-id="9c25e-162">Resource locatie</span><span class="sxs-lookup"><span data-stu-id="9c25e-162">Resource location</span></span>

<span data-ttu-id="9c25e-163">Bij het ontwerpen en compileren van configuraties kunnen uw resources worden opgeslagen in een map die is opgegeven door uw [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="9c25e-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="9c25e-164">In Power Shell 4,0 moeten alle DSC-resource modules zijn opgeslagen onder Program Files\WindowsPowerShell\Modules of `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="9c25e-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="9c25e-165">Vanaf Power shell 5,0 is deze vereiste verwijderd en kunnen resource modules worden opgeslagen in een map die is opgegeven door `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="9c25e-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c25e-166">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9c25e-166">See also</span></span>

- [<span data-ttu-id="9c25e-167">Resources</span><span class="sxs-lookup"><span data-stu-id="9c25e-167">Resources</span></span>](../resources/resources.md)
