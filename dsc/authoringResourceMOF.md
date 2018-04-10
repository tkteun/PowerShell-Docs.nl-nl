---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Schrijven van een aangepaste DSC-resource met MOF
ms.openlocfilehash: 4e336e837d2153fecab8325cb8714ffed85a6175
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="e51d7-103">Schrijven van een aangepaste DSC-resource met MOF</span><span class="sxs-lookup"><span data-stu-id="e51d7-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="e51d7-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e51d7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="e51d7-105">In dit onderwerp wordt het schema voor de aangepaste resource van een Windows PowerShell Desired State Configuration (DSC) definiëren in een MOF-bestand, en implementeren van de resource in een Windows PowerShell-scriptbestand.</span><span class="sxs-lookup"><span data-stu-id="e51d7-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="e51d7-106">Deze aangepaste resource wordt voor het maken en onderhouden van een website.</span><span class="sxs-lookup"><span data-stu-id="e51d7-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="e51d7-107">Maken van het MOF-schema</span><span class="sxs-lookup"><span data-stu-id="e51d7-107">Creating the MOF schema</span></span>

<span data-ttu-id="e51d7-108">Het schema definieert de eigenschappen van de bron die kunnen worden geconfigureerd door een DSC-configuratiescript.</span><span class="sxs-lookup"><span data-stu-id="e51d7-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="e51d7-109">Mapstructuur voor een MOF-bron</span><span class="sxs-lookup"><span data-stu-id="e51d7-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="e51d7-110">Voor het implementeren van een aangepaste DSC-resource met een MOF-schema, maken de volgende mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="e51d7-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="e51d7-111">Het MOF-schema is gedefinieerd in het bestand Demo_IISWebsite.schema.mof en het resource-script is gedefinieerd in Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="e51d7-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="e51d7-112">U kunt desgewenst een module-manifest (psd1)-bestand maken.</span><span class="sxs-lookup"><span data-stu-id="e51d7-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="e51d7-113">Houd er rekening mee dat het nodig zijn voor het maken van een map met de naam DSCResources onder de hoofdmap is en dat de map voor elke resource moet dezelfde naam als de bron.</span><span class="sxs-lookup"><span data-stu-id="e51d7-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="e51d7-114">De inhoud van het MOF-bestand</span><span class="sxs-lookup"><span data-stu-id="e51d7-114">The contents of the MOF file</span></span>

<span data-ttu-id="e51d7-115">Hier volgt een voorbeeld van de MOF-bestand dat kan worden gebruikt voor de bron van een aangepaste website.</span><span class="sxs-lookup"><span data-stu-id="e51d7-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="e51d7-116">Wilt u dit voorbeeld, dit schema opslaan in een bestand en het bestand *Demo_IISWebsite.schema.mof*.</span><span class="sxs-lookup"><span data-stu-id="e51d7-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("Website")]
class Demo_IISWebsite : OMI_BaseResource
{
  [Key] string Name;
  [Required] string PhysicalPath;
  [write,ValueMap{"Present", "Absent"},Values{"Present", "Absent"}] string Ensure;
  [write,ValueMap{"Started","Stopped"},Values{"Started", "Stopped"}] string State;
  [write] string Protocol[];
  [write] string BindingInfo[];
  [write] string ApplicationPool;
  [read] string ID;
};
```

<span data-ttu-id="e51d7-117">Houd rekening met de volgende met betrekking tot de vorige code:</span><span class="sxs-lookup"><span data-stu-id="e51d7-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="e51d7-118">`FriendlyName` definieert de naam die u gebruiken kunt om te verwijzen naar deze aangepaste resource in scripts voor DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="e51d7-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="e51d7-119">In dit voorbeeld `Website` komt overeen met de beschrijvende naam `Archive` voor de ingebouwde archief-resource.</span><span class="sxs-lookup"><span data-stu-id="e51d7-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="e51d7-120">De klasse die u definieert voor de aangepaste resource moet worden afgeleid van `OMI_BaseResource`.</span><span class="sxs-lookup"><span data-stu-id="e51d7-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="e51d7-121">De kwalificatie type `[Key]`op een eigenschap aangeeft dat deze eigenschap een unieke identificatie van de resource-instantie.</span><span class="sxs-lookup"><span data-stu-id="e51d7-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="e51d7-122">Ten minste één `[Key]` eigenschap is vereist.</span><span class="sxs-lookup"><span data-stu-id="e51d7-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="e51d7-123">De `[Required]` kwalificatie geeft aan dat de eigenschap vereist is (er moet een waarde worden opgegeven in een configuratiescript dat gebruikmaakt van deze bron).</span><span class="sxs-lookup"><span data-stu-id="e51d7-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="e51d7-124">De `[write]` kwalificatie geeft aan dat deze eigenschap optioneel is bij het gebruik van de aangepaste resource in een configuratiescript.</span><span class="sxs-lookup"><span data-stu-id="e51d7-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="e51d7-125">De `[read]` kwalificatie geeft aan dat een eigenschap kan niet worden ingesteld door een configuratie en is alleen voor rapportagedoeleinden.</span><span class="sxs-lookup"><span data-stu-id="e51d7-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="e51d7-126">`Values` Hiermee beperkt u de waarden die kunnen worden toegewezen aan de eigenschap aan de lijst met waarden die zijn gedefinieerd in `ValueMap`.</span><span class="sxs-lookup"><span data-stu-id="e51d7-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="e51d7-127">Zie voor meer informatie [ValueMap en waarde-kwalificaties bevat](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span><span class="sxs-lookup"><span data-stu-id="e51d7-127">For more information, see [ValueMap and Value Qualifiers](https://msdn.microsoft.com/library/windows/desktop/aa393965.aspx).</span></span>
* <span data-ttu-id="e51d7-128">Met inbegrip van een eigenschap genaamd `Ensure` met waarden `Present` en `Absent` in de bron, wordt aanbevolen als een manier om een consistente stijl met ingebouwde DSC-resources te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="e51d7-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="e51d7-129">Naam van het schemabestand voor uw aangepaste resource als volgt: `classname.schema.mof`, waarbij `classname` is de id die volgt de `class` -sleutelwoord in de schemadefinitie van de.</span><span class="sxs-lookup"><span data-stu-id="e51d7-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="e51d7-130">De resource-script schrijven</span><span class="sxs-lookup"><span data-stu-id="e51d7-130">Writing the resource script</span></span>

<span data-ttu-id="e51d7-131">Het script resource implementeert de logica van de resource.</span><span class="sxs-lookup"><span data-stu-id="e51d7-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="e51d7-132">U moet drie functies aangeroepen opnemen in deze module **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="e51d7-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="e51d7-133">Alle drie functies moeten rekening houden met een parameterset die identiek is aan de set eigenschappen die zijn gedefinieerd in het MOF-schema dat u hebt gemaakt voor uw resource.</span><span class="sxs-lookup"><span data-stu-id="e51d7-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="e51d7-134">In dit document, wordt deze reeks eigenschappen aangeduid als de "broneigenschappen'.</span><span class="sxs-lookup"><span data-stu-id="e51d7-134">In this document, this set of properties is referred to as the “resource properties.”</span></span> <span data-ttu-id="e51d7-135">Deze drie functies in een bestand genaamd Store <ResourceName>.psm1.</span><span class="sxs-lookup"><span data-stu-id="e51d7-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="e51d7-136">In het volgende voorbeeld worden de functies worden opgeslagen in een bestand met de naam Demo_IISWebsite.psm1.</span><span class="sxs-lookup"><span data-stu-id="e51d7-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> <span data-ttu-id="e51d7-137">**Opmerking**: wanneer u de dezelfde configuratiescript op uw resource meer dan één keer uitvoeren, u geen fouten ontvangt en de bron in dezelfde staat blijven moet als het eenmaal uitvoeren van het script.</span><span class="sxs-lookup"><span data-stu-id="e51d7-137">**Note**: When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="e51d7-138">U doet dit door ervoor te zorgen dat uw **Get-TargetResource** en **Test TargetResource** functies laat de bron niet worden gewijzigd en dat aanroepen van de **Set-TargetResource**werken meer dan één keer in een reeks met dezelfde parameter waarden is altijd gelijk is aan één keer aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e51d7-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="e51d7-139">In de **Get-TargetResource** implementatie werkt, de belangrijkste bron eigenschapswaarden die beschikbaar zijn als parameters gebruiken om te controleren van de status van het exemplaar van de opgegeven bron.</span><span class="sxs-lookup"><span data-stu-id="e51d7-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="e51d7-140">Deze functie moet een hashtabel waarin de broneigenschappen als sleutels en de werkelijke waarden van deze eigenschappen als de bijbehorende waarden retourneren.</span><span class="sxs-lookup"><span data-stu-id="e51d7-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="e51d7-141">De volgende code geeft een voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="e51d7-141">The following code provides an example.</span></span>

```powershell
# DSC uses the Get-TargetResource function to fetch the status of the resource instance specified in the parameters for the target machine
function Get-TargetResource
{
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

        $getTargetResourceResult = $null;

        <# Insert logic that uses the mandatory parameter values to get the website and assign it to a variable called $Website #>
        <# Set $ensureResult to "Present" if the requested website exists and to "Absent" otherwise #>

        # Add all Website properties to the hash table
        # This simple example assumes that $Website is not null
        $getTargetResourceResult = @{
                                      Name = $Website.Name;
                                        Ensure = $ensureResult;
                                        PhysicalPath = $Website.physicalPath;
                                        State = $Website.state;
                                        ID = $Website.id;
                                        ApplicationPool = $Website.applicationPool;
                                        Protocol = $Website.bindings.Collection.protocol;
                                        Binding = $Website.bindings.Collection.bindingInformation;
                                    }

        $getTargetResourceResult;
}
```

<span data-ttu-id="e51d7-142">Afhankelijk van de waarden die zijn opgegeven voor de resource-eigenschappen in het configuratiescript de **Set TargetResource** moet een van de volgende dingen doen:</span><span class="sxs-lookup"><span data-stu-id="e51d7-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="e51d7-143">Een nieuwe website maken</span><span class="sxs-lookup"><span data-stu-id="e51d7-143">Create a new website</span></span>
* <span data-ttu-id="e51d7-144">Bijwerken van een bestaande website</span><span class="sxs-lookup"><span data-stu-id="e51d7-144">Update an existing website</span></span>
* <span data-ttu-id="e51d7-145">Verwijderen van een bestaande website</span><span class="sxs-lookup"><span data-stu-id="e51d7-145">Delete an existing website</span></span>

<span data-ttu-id="e51d7-146">Het volgende voorbeeld ziet u dit.</span><span class="sxs-lookup"><span data-stu-id="e51d7-146">The following example illustrates this.</span></span>

```powershell
# The Set-TargetResource function is used to create, delete or configure a website on the target machine.
function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [ValidateSet("Present", "Absent")]
        [string]$Ensure = "Present",

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$Name,

        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [string]$PhysicalPath,

        [ValidateSet("Started", "Stopped")]
        [string]$State = "Started",

        [string]$ApplicationPool,

        [string[]]$BindingInfo,

        [string[]]$Protocol
    )

    <# If Ensure is set to "Present" and the website specified in the mandatory input parameters does not exist, then create it using the specified parameter values #>
    <# Else, if Ensure is set to "Present" and the website does exist, then update its properties to match the values provided in the non-mandatory parameter values #>
    <# Else, if Ensure is set to "Absent" and the website does not exist, then do nothing #>
    <# Else, if Ensure is set to "Absent" and the website does exist, then delete the website #>
}
```

<span data-ttu-id="e51d7-147">Ten slotte de **Test TargetResource** functie moet rekening houden met dezelfde parameterset als **Get-TargetResource** en **Set TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="e51d7-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="e51d7-148">Bij de implementatie van **Test TargetResource**, Controleer de status van de resource-instantie die is opgegeven in de belangrijkste parameters.</span><span class="sxs-lookup"><span data-stu-id="e51d7-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="e51d7-149">Als de huidige status van het exemplaar van de resource komt niet overeen met de opgegeven waarden in de parameterset, geretourneerd **$false**.</span><span class="sxs-lookup"><span data-stu-id="e51d7-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="e51d7-150">Anders retourneren **$true**.</span><span class="sxs-lookup"><span data-stu-id="e51d7-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="e51d7-151">De volgende code implementeert de **Test TargetResource** functie.</span><span class="sxs-lookup"><span data-stu-id="e51d7-151">The following code implements the **Test-TargetResource** function.</span></span>

```powershell
function Test-TargetResource
{
[CmdletBinding()]
[OutputType([System.Boolean])]
param
(
[ValidateSet("Present","Absent")]
[System.String]
$Ensure,

[parameter(Mandatory = $true)]
[System.String]
$Name,

[parameter(Mandatory = $true)]
[System.String]
$PhysicalPath,

[ValidateSet("Started","Stopped")]
[System.String]
$State,

[System.String[]]
$Protocol,

[System.String[]]
$BindingData,

[System.String]
$ApplicationPool
)

#Write-Verbose "Use this cmdlet to deliver information about command processing."

#Write-Debug "Use this cmdlet to write debug information while troubleshooting."


#Include logic to
$result = [System.Boolean]
#Add logic to test whether the website is present and its status mathes the supplied parameter values. If it does, return true. If it does not, return false.
$result
}
```

<span data-ttu-id="e51d7-152">**Opmerking**: voor gemakkelijker foutopsporing, gebruikt u de **Write-Verbose** cmdlet in uw implementatie van de vorige drie functies.</span><span class="sxs-lookup"><span data-stu-id="e51d7-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="e51d7-153">Deze cmdlet schrijft tekst naar de uitgebreide berichtenstroom.</span><span class="sxs-lookup"><span data-stu-id="e51d7-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="e51d7-154">Standaard de uitgebreide berichtenstroom niet wordt weergegeven, maar kunt u deze weergeven door het wijzigen van de waarde van de **$VerbosePreference** variabele of met behulp van de **uitgebreid** parameter in de DSC-cmdlets = new.</span><span class="sxs-lookup"><span data-stu-id="e51d7-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="e51d7-155">Maken van de module-manifest</span><span class="sxs-lookup"><span data-stu-id="e51d7-155">Creating the module manifest</span></span>

<span data-ttu-id="e51d7-156">Gebruik tot slot de **nieuw ModuleManifest** cmdlet voor het definiëren van een <ResourceName>.psd1-bestand voor uw aangepaste resource-module.</span><span class="sxs-lookup"><span data-stu-id="e51d7-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="e51d7-157">Als u deze cmdlet aanroept, verwijzen naar het scriptbestand voor module (.psm1) die worden beschreven in de vorige sectie.</span><span class="sxs-lookup"><span data-stu-id="e51d7-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="e51d7-158">Omvatten **Get-TargetResource**, **Set TargetResource**, en **Test TargetResource** in de lijst met functies om te exporteren.</span><span class="sxs-lookup"><span data-stu-id="e51d7-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="e51d7-159">Hier volgt een voorbeeld-manifestbestand.</span><span class="sxs-lookup"><span data-stu-id="e51d7-159">Following is an example manifest file.</span></span>

```powershell
# Module manifest for module 'Demo.IIS.Website'
#
# Generated on: 1/10/2013
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '6AB5ED33-E923-41d8-A3A4-5ADDA2B301DE'

# Author of this module
Author = 'Contoso'

# Company or vendor of this module
CompanyName = 'Contoso'

# Copyright statement for this module
Copyright = 'Contoso. All rights reserved.'

# Description of the functionality provided by this module
Description = 'This Module is used to support the creation and configuration of IIS Websites through Get, Set and Test API on the DSC managed nodes.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '4.0'

# Minimum version of the common language runtime (CLR) required by this module
CLRVersion = '4.0'

# Modules that must be imported into the global environment prior to importing this module
RequiredModules = @("WebAdministration")

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
NestedModules = @("Demo_IISWebsite.psm1")

# Functions to export from this module
FunctionsToExport = @("Get-TargetResource", "Set-TargetResource", "Test-TargetResource")

# Cmdlets to export from this module
#CmdletsToExport = '*'

# HelpInfo URI of this module
# HelpInfoURI = ''
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="e51d7-160">Ondersteunende PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e51d7-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="e51d7-161">**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="e51d7-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="e51d7-162">De **PsDscRunAsCredential** eigenschap kan worden gebruikt [DSC-configuraties](configurations.md) resource blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="e51d7-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="e51d7-163">Zie voor meer informatie [DSC uitgevoerd met gebruikersreferenties](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="e51d7-163">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="e51d7-164">Voor toegang tot de gebruikerscontext van binnen een aangepaste bron, kunt u de automatische variabele `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="e51d7-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="e51d7-165">De volgende code zou bijvoorbeeld de gebruikerscontext waaronder de bron wordt uitgevoerd naar de uitgebreide uitvoerstroom schrijven:</span><span class="sxs-lookup"><span data-stu-id="e51d7-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```