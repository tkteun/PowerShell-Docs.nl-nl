---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: Met behulp van de sleutelwoorden Import-dscresource bieden
ms.openlocfilehash: 6bc3c1aa1d34a05e3188666da825322235c0672e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404033"
---
# <a name="using-import-dscresource"></a><span data-ttu-id="ced12-103">Met behulp van de sleutelwoorden Import-dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="ced12-103">Using Import-DSCResource</span></span>

<span data-ttu-id="ced12-104">`Import-DScResource` is een dynamische sleutelwoord, die alleen kan worden gebruikt in een configuratie-scriptblok.</span><span class="sxs-lookup"><span data-stu-id="ced12-104">`Import-DScResource` is a dynamic keyword, which can only be used inside a Configuration script block.</span></span> <span data-ttu-id="ced12-105">De `Import-DSCResource` trefwoord dat u wilt importeren van alle resources die nodig zijn in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="ced12-105">The `Import-DSCResource` keyword to import any resources needed in your Configuration.</span></span> <span data-ttu-id="ced12-106">Resources onder `$phsome` automatisch worden geïmporteerd, maar het is nog steeds beschouwd als aanbevolen procedure voor het expliciet importeren van alle resources die worden gebruikt uw [configuratie](Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="ced12-106">Resources under `$phsome` are imported automatically, but it is still considered best practice to explicitly import all resources used in your [Configuration](Configurations.md).</span></span>

<span data-ttu-id="ced12-107">De syntaxis voor `Import-DSCResource` wordt hieronder weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ced12-107">The syntax for `Import-DSCResource` is shown below.</span></span>

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>]
```

|<span data-ttu-id="ced12-108">Parameter</span><span class="sxs-lookup"><span data-stu-id="ced12-108">Parameter</span></span>  |<span data-ttu-id="ced12-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ced12-109">Description</span></span>  |
|---------|---------|
|`-Name`|<span data-ttu-id="ced12-110">De namen van de DSC-resource die u moet importeren.</span><span class="sxs-lookup"><span data-stu-id="ced12-110">The DSC resource name(s) that you must import.</span></span> <span data-ttu-id="ced12-111">Als de naam van de module is opgegeven, de opdracht wordt gezocht naar deze DSC-resources binnen deze module. de opdracht zoekt anders de DSC-resources in alle paden voor DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="ced12-111">If the module name is specified, the command searches for these DSC resources within this module; otherwise the command searches the DSC resources in all DSC resource paths.</span></span> <span data-ttu-id="ced12-112">Jokertekens worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ced12-112">Wildcards are supported.</span></span>|
|`-ModuleName`|<span data-ttu-id="ced12-113">De namen van container-module, of de module specification(s).</span><span class="sxs-lookup"><span data-stu-id="ced12-113">The container module name(s), or module specification(s).</span></span>  <span data-ttu-id="ced12-114">Als u resources te importeren vanuit een module opgeeft, wordt de opdracht wordt geprobeerd enkel de resources te importeren.</span><span class="sxs-lookup"><span data-stu-id="ced12-114">If you specify resources to import from a module, the command will try to import only those resources.</span></span> <span data-ttu-id="ced12-115">Als u de module alleen opgeeft, wordt met de opdracht de DSC-resources in de module geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="ced12-115">If you specify the module only, the command imports all the DSC resources in the module.</span></span>|

<span data-ttu-id="ced12-116">U kunt jokertekens met de `-Name` parameter bij het gebruik van `Import-DSCResource`.</span><span class="sxs-lookup"><span data-stu-id="ced12-116">You can use wildcards with the `-Name` parameter when using `Import-DSCResource`.</span></span>

```powershell
Import-DscResource -Name * -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a><span data-ttu-id="ced12-117">Voorbeeld: Sleutelwoorden Import-dscresource bieden in een configuratie gebruiken</span><span class="sxs-lookup"><span data-stu-id="ced12-117">Example: Use Import-DSCResource within a configuration</span></span>

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName MS_DSC1 -name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    Import-DSCResource -Name File, TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
...
```

> [!NOTE]
> <span data-ttu-id="ced12-118">Meerdere waarden voor de namen van de Resource en modules in dezelfde opdracht op te geven, worden niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ced12-118">Specifying multiple values for Resource names and modules names in same command are not supported.</span></span> <span data-ttu-id="ced12-119">Het kan gedrag van niet-deterministisch over welke resource moet worden geladen vanaf welke module in het geval dezelfde resource in meerdere modules bestaat hebben.</span><span class="sxs-lookup"><span data-stu-id="ced12-119">It can have non-deterministic behavior about which resource to load from which module in case same resource exists in multiple modules.</span></span> <span data-ttu-id="ced12-120">Onderstaande opdracht resulteert in fout tijdens de compilatie.</span><span class="sxs-lookup"><span data-stu-id="ced12-120">Below command will result in error during compilation.</span></span>
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

<span data-ttu-id="ced12-121">Dingen om te overwegen bij het gebruik van alleen de parameter Name:</span><span class="sxs-lookup"><span data-stu-id="ced12-121">Things to consider when using only the Name parameter:</span></span>

- <span data-ttu-id="ced12-122">Dit is een resource-intensieve bewerking afhankelijk van het aantal modules die zijn geïnstalleerd op de machine.</span><span class="sxs-lookup"><span data-stu-id="ced12-122">It is a resource-intensive operation depending on the number of modules installed on machine.</span></span>
- <span data-ttu-id="ced12-123">Het wordt geladen door de eerste resource gevonden met de opgegeven naam.</span><span class="sxs-lookup"><span data-stu-id="ced12-123">It will load the first resource found with the given name.</span></span> <span data-ttu-id="ced12-124">In het geval wanneer er meer dan één resource met dezelfde naam geïnstalleerd is, de juiste resource kan worden geladen.</span><span class="sxs-lookup"><span data-stu-id="ced12-124">In the case where there is more than one resource with same name installed, it could load the wrong resource.</span></span>

<span data-ttu-id="ced12-125">De aanbevolen methode is om op te geven `–ModuleName` met de `-Name` parameter, zoals hieronder wordt beschreven.</span><span class="sxs-lookup"><span data-stu-id="ced12-125">The recommended usage is to specify `–ModuleName` with the `-Name` parameter, as described below.</span></span>

<span data-ttu-id="ced12-126">Dit gebruik heeft de volgende voordelen:</span><span class="sxs-lookup"><span data-stu-id="ced12-126">This usage has the following benefits:</span></span>

- <span data-ttu-id="ced12-127">Dit vermindert de prestatiegevolgen door het beperken van het zoekbereik voor de opgegeven resource.</span><span class="sxs-lookup"><span data-stu-id="ced12-127">It reduces the performance impact by limiting the search scope for the specified resource.</span></span>
- <span data-ttu-id="ced12-128">Hiermee worden de module definiëren van de resource, ervoor te zorgen dat de juiste resource wordt geladen expliciet gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="ced12-128">It explicitly defines the module defining the resource, ensuring the correct resource is loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="ced12-129">In PowerShell 5.0, DSC-resources kunnen er meerdere versies en versies kunnen worden geïnstalleerd op een computer side-by-side.</span><span class="sxs-lookup"><span data-stu-id="ced12-129">In PowerShell 5.0, DSC resources can have multiple versions, and versions can be installed on a computer side-by-side.</span></span> <span data-ttu-id="ced12-130">Dit is geïmplementeerd door meerdere versies van een resource-module die zijn opgenomen in de modulemap met dezelfde.</span><span class="sxs-lookup"><span data-stu-id="ced12-130">This is implemented by having multiple versions of a resource module that are contained in the same module folder.</span></span>
> <span data-ttu-id="ced12-131">Zie voor meer informatie, [resources met meerdere versies gebruiken](sxsresource.md).</span><span class="sxs-lookup"><span data-stu-id="ced12-131">For more information, see [Using resources with multiple versions](sxsresource.md).</span></span>

## <a name="intellisense-with-import-dscresource"></a><span data-ttu-id="ced12-132">IntelliSense met sleutelwoorden Import-dscresource bieden</span><span class="sxs-lookup"><span data-stu-id="ced12-132">Intellisense with Import-DSCResource</span></span>

<span data-ttu-id="ced12-133">Bij het ontwerpen van de DSC-configuratie in ISE biedt PowerShell IntelliSence voor resources en resource-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="ced12-133">When authoring the DSC configuration in ISE, PowerShell provides IntelliSence for resources and resource properties.</span></span> <span data-ttu-id="ced12-134">Resourcedefinities onder de `$pshome` modulepad worden automatisch geladen.</span><span class="sxs-lookup"><span data-stu-id="ced12-134">Resource definitions under the `$pshome` module path are loaded automatically.</span></span> <span data-ttu-id="ced12-135">Wanneer het importeren van resources met behulp van de `Import-DSCResource` trefwoord, de opgegeven resource-definities zijn toegevoegd en Intellisense om op te nemen van de geïmporteerde resource-schema is uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="ced12-135">When you import resources using the `Import-DSCResource` keyword, the specified resource definitions are added and Intellisense is expanded to include the imported resource's schema.</span></span>

![Resource-Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> <span data-ttu-id="ced12-137">Begin in PowerShell 5.0, is tab-Aanvulling toegevoegd aan de ISE voor DSC-resources en hun eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="ced12-137">Beginning in PowerShell 5.0, tab completion was added to the ISE for DSC resources and their properties.</span></span> <span data-ttu-id="ced12-138">Zie voor meer informatie, [Resources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="ced12-138">For more information, see [Resources](../resources/resources.md).</span></span>

<span data-ttu-id="ced12-139">Bij het compileren van de configuratie van de PowerShell maakt gebruik van de geïmporteerde resourcedefinities alle resource blokken in de configuratie valideren.</span><span class="sxs-lookup"><span data-stu-id="ced12-139">When compiling the Configuration, PowerShell uses the imported resource definitions to validate all resource blocks in the configuration.</span></span>
<span data-ttu-id="ced12-140">Elk blok van de resource is gevalideerd, met behulp van de resource-schemadefinitie, voor de volgende regels.</span><span class="sxs-lookup"><span data-stu-id="ced12-140">Each resource block is validated, using the resource's schema definition, for the following rules.</span></span>

- <span data-ttu-id="ced12-141">Alleen de eigenschappen die zijn gedefinieerd in het schema worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ced12-141">Only properties defined in schema are used.</span></span>
- <span data-ttu-id="ced12-142">De gegevenstypen voor elke eigenschap zijn correct.</span><span class="sxs-lookup"><span data-stu-id="ced12-142">The data types for each property are correct.</span></span>
- <span data-ttu-id="ced12-143">Eigenschappen van de sleutels worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="ced12-143">Keys properties are specified.</span></span>
- <span data-ttu-id="ced12-144">Er is geen alleen-lezen eigenschap wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ced12-144">No read-only property is used.</span></span>
- <span data-ttu-id="ced12-145">Validatie van waarde toegewezen typen.</span><span class="sxs-lookup"><span data-stu-id="ced12-145">Validation on value maps types.</span></span>

<span data-ttu-id="ced12-146">Houd rekening met de volgende configuratie:</span><span class="sxs-lookup"><span data-stu-id="ced12-146">Consider the following configuration:</span></span>

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

<span data-ttu-id="ced12-147">Compileren van deze configuratie leidt tot een fout.</span><span class="sxs-lookup"><span data-stu-id="ced12-147">Compiling this Configuration results in an error.</span></span>

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

<span data-ttu-id="ced12-148">Validatie van IntelliSense en het schema kunt u meer runbookauteur fouten worden gedetecteerd tijdens het parseren en compilatie tijd complicaties vermijden tijdens de uitvoering.</span><span class="sxs-lookup"><span data-stu-id="ced12-148">Intellisense and schema validation allow you to catch more errors during parse and compilation time, avoiding complications at run time.</span></span>

> [!NOTE]
> <span data-ttu-id="ced12-149">Elke DSC-resource kan hebben een naam en een **FriendlyName** gedefinieerd door de resource-schema.</span><span class="sxs-lookup"><span data-stu-id="ced12-149">Each DSC resource can have a name, and a **FriendlyName** defined by the resource's schema.</span></span> <span data-ttu-id="ced12-150">Hieronder vindt u de eerste twee regels van 'MSFT_ServiceResource.shema.mof'.</span><span class="sxs-lookup"><span data-stu-id="ced12-150">Below are the first two lines of "MSFT_ServiceResource.shema.mof".</span></span>
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> <span data-ttu-id="ced12-151">Wanneer u deze resource in een configuratie gebruikt, kunt u **MSFT_ServiceResource** of **Service**.</span><span class="sxs-lookup"><span data-stu-id="ced12-151">When using this resource in a Configuration, you can specify **MSFT_ServiceResource** or **Service**.</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="ced12-152">Verschillen in PowerShell v4 en versie 5</span><span class="sxs-lookup"><span data-stu-id="ced12-152">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="ced12-153">Er zijn meerdere verschillen u ziet bij het ontwerpen van configuraties in PowerShell 4.0 Visual Studio. PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="ced12-153">There are multiple differences you see when authoring Configurations in PowerShell 4.0 vs. PowerShell 5.0 and later.</span></span> <span data-ttu-id="ced12-154">In deze sectie worden de verschillen die u ziet dat relevant is voor dit artikel.</span><span class="sxs-lookup"><span data-stu-id="ced12-154">This section will highlight the differences that you see relevant to this article.</span></span>

### <a name="multiple-resource-versions"></a><span data-ttu-id="ced12-155">Meerdere versies van de Resource</span><span class="sxs-lookup"><span data-stu-id="ced12-155">Multiple Resource Versions</span></span>

<span data-ttu-id="ced12-156">Installeren en gebruiken van meerdere versies van resources naast elkaar wordt niet ondersteund in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="ced12-156">Installing and using multiple versions of resources side by side was not supported in PowerShell 4.0.</span></span> <span data-ttu-id="ced12-157">Als u problemen met het importeren van resources in uw configuratie ziet, zorg ervoor dat u slechts één versie van de resource geïnstalleerd hebben.</span><span class="sxs-lookup"><span data-stu-id="ced12-157">If you notice issues importing resources into your Configuration, ensure that you only have one version of the resource installed.</span></span>

<span data-ttu-id="ced12-158">In de afbeelding hieronder, twee versies van de **xPSDesiredStateConfiguration** module zijn geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="ced12-158">In the image below, two versions of the **xPSDesiredStateConfiguration** module are installed.</span></span>

![Meerdere Resource-versies opgelost](/media/multiple-resource-versions-broken.md)

<span data-ttu-id="ced12-160">Kopieer de inhoud van uw moduleversie van de gewenste naar het hoogste niveau van de modulemap.</span><span class="sxs-lookup"><span data-stu-id="ced12-160">Copy the contents of your desired module version to the top level of the module directory.</span></span>

![Meerdere Resource-versies opgelost](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a><span data-ttu-id="ced12-162">Resourcelocatie</span><span class="sxs-lookup"><span data-stu-id="ced12-162">Resource location</span></span>

<span data-ttu-id="ced12-163">Bij het ontwerpen en -configuraties compileren, uw resources kunnen worden opgeslagen in een map die is opgegeven door uw [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span><span class="sxs-lookup"><span data-stu-id="ced12-163">When authoring and compiling Configurations, your resources can be stored in any directory specified by your [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path).</span></span> <span data-ttu-id="ced12-164">In PowerShell 4.0, vereist de LCM alle DSC-resource-modules worden opgeslagen onder 'Programma Files\WindowsPowerShell\Modules' of `$pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="ced12-164">In PowerShell 4.0, the LCM requires all DSC resource modules to be stored under "Program Files\WindowsPowerShell\Modules" or `$pshome\Modules`.</span></span> <span data-ttu-id="ced12-165">Begin in PowerShell 5.0, deze vereiste is verwijderd en resource-modules kunnen worden opgeslagen in een map die is opgegeven door `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="ced12-165">Beginning in PowerShell 5.0, this requirement was removed, and resource modules can be stored in any directory specified by `PSModulePath`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ced12-166">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ced12-166">See also</span></span>

- [<span data-ttu-id="ced12-167">Resources</span><span class="sxs-lookup"><span data-stu-id="ced12-167">Resources</span></span>](../resources/resources.md)
