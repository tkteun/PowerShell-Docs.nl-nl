---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een aangepaste DSC-resource schrijven met MOF
ms.openlocfilehash: 24e9d15bcbe1eddd297daeb04e0713c443e52c38
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941206"
---
# <a name="writing-a-custom-dsc-resource-with-mof"></a><span data-ttu-id="c131d-103">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="c131d-103">Writing a custom DSC resource with MOF</span></span>

> <span data-ttu-id="c131d-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="c131d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c131d-105">In dit onderwerp definiëren we het schema voor een aangepaste Windows Power shell-resource voor desired state Configuration (DSC) in een MOF-bestand en implementeert u de bron in een Windows Power shell-script bestand.</span><span class="sxs-lookup"><span data-stu-id="c131d-105">In this topic, we will define the schema for a Windows PowerShell Desired State Configuration (DSC) custom resource in a MOF file, and implement the resource in a Windows PowerShell script file.</span></span> <span data-ttu-id="c131d-106">Deze aangepaste resource is voor het maken en onderhouden van een website.</span><span class="sxs-lookup"><span data-stu-id="c131d-106">This custom resource is for creating and maintaining a web site.</span></span>

## <a name="creating-the-mof-schema"></a><span data-ttu-id="c131d-107">Het MOF-schema maken</span><span class="sxs-lookup"><span data-stu-id="c131d-107">Creating the MOF schema</span></span>

<span data-ttu-id="c131d-108">Het schema definieert de eigenschappen van uw resource die kunnen worden geconfigureerd met een DSC-configuratie script.</span><span class="sxs-lookup"><span data-stu-id="c131d-108">The schema defines the properties of your resource that can be configured by a DSC configuration script.</span></span>

### <a name="folder-structure-for-a-mof-resource"></a><span data-ttu-id="c131d-109">Mapstructuur voor een MOF-bron</span><span class="sxs-lookup"><span data-stu-id="c131d-109">Folder structure for a MOF resource</span></span>

<span data-ttu-id="c131d-110">Als u een aangepaste DSC-resource met een MOF-schema wilt implementeren, maakt u de volgende mapstructuur.</span><span class="sxs-lookup"><span data-stu-id="c131d-110">To implement a DSC custom resource with a MOF schema, create the following folder structure.</span></span> <span data-ttu-id="c131d-111">Het MOF-schema wordt gedefinieerd in het bestand Demo_IISWebsite. schema. mof en het bron script is gedefinieerd in Demo_IISWebsite. psm1.</span><span class="sxs-lookup"><span data-stu-id="c131d-111">The MOF schema is defined in the file Demo_IISWebsite.schema.mof, and the resource script is defined in Demo_IISWebsite.psm1.</span></span> <span data-ttu-id="c131d-112">U kunt desgewenst een psd1-bestand (module manifest) maken.</span><span class="sxs-lookup"><span data-stu-id="c131d-112">Optionally, you can create a module manifest (psd1) file.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- Demo_IISWebsite (folder)
                |- Demo_IISWebsite.psd1 (file, optional)
                |- Demo_IISWebsite.psm1 (file, required)
                |- Demo_IISWebsite.schema.mof (file, required)
```

<span data-ttu-id="c131d-113">Houd er rekening mee dat u een map met de naam DSCResources maakt in de map op het hoogste niveau en dat de map voor elke resource dezelfde naam moet hebben als de resource.</span><span class="sxs-lookup"><span data-stu-id="c131d-113">Note that it is necessary to create a folder named DSCResources under the top-level folder, and that the folder for each resource must have the same name as the resource.</span></span>

### <a name="the-contents-of-the-mof-file"></a><span data-ttu-id="c131d-114">De inhoud van het MOF-bestand</span><span class="sxs-lookup"><span data-stu-id="c131d-114">The contents of the MOF file</span></span>

<span data-ttu-id="c131d-115">Hier volgt een voor beeld van een MOF-bestand dat kan worden gebruikt voor een aangepaste website bron.</span><span class="sxs-lookup"><span data-stu-id="c131d-115">Following is an example MOF file that can be used for a custom website resource.</span></span> <span data-ttu-id="c131d-116">Als u dit voor beeld wilt volgen, slaat u dit schema op in een bestand en roept u het bestand *Demo_IISWebsite. schema. MOF*.</span><span class="sxs-lookup"><span data-stu-id="c131d-116">To follow this example, save this schema to a file, and call the file *Demo_IISWebsite.schema.mof*.</span></span>

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

<span data-ttu-id="c131d-117">Let op het volgende voor gaande code:</span><span class="sxs-lookup"><span data-stu-id="c131d-117">Note the following about the previous code:</span></span>

* <span data-ttu-id="c131d-118">`FriendlyName`Hiermee definieert u de naam die u kunt gebruiken om te verwijzen naar deze aangepaste resource in de DSC-configuratie scripts.</span><span class="sxs-lookup"><span data-stu-id="c131d-118">`FriendlyName` defines the name you can use to refer to this custom resource in DSC configuration scripts.</span></span> <span data-ttu-id="c131d-119">In dit voor beeld `Website` is gelijk aan de beschrijvende naam `Archive` voor de ingebouwde archief bron.</span><span class="sxs-lookup"><span data-stu-id="c131d-119">In this example, `Website` is equivalent to the friendly name `Archive` for the built-in Archive resource.</span></span>
* <span data-ttu-id="c131d-120">De klasse die u definieert voor uw aangepaste resource moet zijn afgeleid `OMI_BaseResource`van.</span><span class="sxs-lookup"><span data-stu-id="c131d-120">The class you define for your custom resource must derive from `OMI_BaseResource`.</span></span>
* <span data-ttu-id="c131d-121">De type kwalificatie, `[Key]`, op een eigenschap geeft aan dat deze eigenschap het bron exemplaar uniek identificeert.</span><span class="sxs-lookup"><span data-stu-id="c131d-121">The type qualifier, `[Key]`, on a property indicates that this property will uniquely identify the resource instance.</span></span> <span data-ttu-id="c131d-122">Er is ten `[Key]` minste één eigenschap vereist.</span><span class="sxs-lookup"><span data-stu-id="c131d-122">At least one `[Key]` property is required.</span></span>
* <span data-ttu-id="c131d-123">De `[Required]` kwalificatie geeft aan dat de eigenschap vereist is (er moet een waarde worden opgegeven in een configuratie script dat gebruikmaakt van deze bron).</span><span class="sxs-lookup"><span data-stu-id="c131d-123">The `[Required]` qualifier indicates that the property is required (a value must be specified in any configuration script that uses this resource).</span></span>
* <span data-ttu-id="c131d-124">De `[write]` kwalificatie geeft aan dat deze eigenschap optioneel is wanneer u de aangepaste resource in een configuratie script gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c131d-124">The `[write]` qualifier indicates that this property is optional when using the custom resource in a configuration script.</span></span> <span data-ttu-id="c131d-125">De `[read]` kwalificatie geeft aan dat een eigenschap niet kan worden ingesteld met een configuratie en alleen voor rapportage doeleinden.</span><span class="sxs-lookup"><span data-stu-id="c131d-125">The `[read]` qualifier indicates that a property cannot be set by a configuration, and is for reporting purposes only.</span></span>
* <span data-ttu-id="c131d-126">`Values`Hiermee worden de waarden die kunnen worden toegewezen aan de eigenschap, beperkt tot de lijst met waarden die `ValueMap`zijn gedefinieerd in.</span><span class="sxs-lookup"><span data-stu-id="c131d-126">`Values` restricts the values that can be assigned to the property to the list of values defined in `ValueMap`.</span></span> <span data-ttu-id="c131d-127">Zie voor meer informatie [ValueMap en waarde-kwalificaties](/windows/desktop/WmiSdk/value-map).</span><span class="sxs-lookup"><span data-stu-id="c131d-127">For more information, see [ValueMap and Value Qualifiers](/windows/desktop/WmiSdk/value-map).</span></span>
* <span data-ttu-id="c131d-128">Het toevoegen van een `Ensure` eigenschap met `Present` de `Absent` naam waarden en in uw resource wordt aanbevolen als een manier om een consistente stijl met ingebouwde DSC-resources te onderhouden.</span><span class="sxs-lookup"><span data-stu-id="c131d-128">Including a property called `Ensure` with values `Present` and `Absent` in your resource is recommended as a way to maintain a consistent style with built-in DSC resources.</span></span>
* <span data-ttu-id="c131d-129">Noem het schema bestand voor uw aangepaste resource als volgt: `classname.schema.mof`, waarbij `classname` de id is gevolgd door het `class` sleutel woord in uw schema definitie.</span><span class="sxs-lookup"><span data-stu-id="c131d-129">Name the schema file for your custom resource as follows: `classname.schema.mof`, where `classname` is the identifier that follows the `class` keyword in your schema definition.</span></span>

### <a name="writing-the-resource-script"></a><span data-ttu-id="c131d-130">Het resource script wordt geschreven</span><span class="sxs-lookup"><span data-stu-id="c131d-130">Writing the resource script</span></span>

<span data-ttu-id="c131d-131">Het bron script implementeert de logica van de resource.</span><span class="sxs-lookup"><span data-stu-id="c131d-131">The resource script implements the logic of the resource.</span></span> <span data-ttu-id="c131d-132">In deze module moet u drie functies gebruiken met de naam **Get-TargetResource**, **set-TargetResource**en **test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="c131d-132">In this module, you must include three functions called **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource**.</span></span> <span data-ttu-id="c131d-133">Alle drie de functies moeten een parameterset hebben die identiek is aan de set eigenschappen die zijn gedefinieerd in het MOF-schema dat u voor uw resource hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c131d-133">All three functions must take a parameter set that is identical to the set of properties defined in the MOF schema that you created for your resource.</span></span> <span data-ttu-id="c131d-134">In dit document wordt deze set eigenschappen aangeduid als de ' resource-eigenschappen '.</span><span class="sxs-lookup"><span data-stu-id="c131d-134">In this document, this set of properties is referred to as the "resource properties."</span></span> <span data-ttu-id="c131d-135">Sla deze drie functies op in een bestand <ResourceName>met de naam. psm1.</span><span class="sxs-lookup"><span data-stu-id="c131d-135">Store these three functions in a file called <ResourceName>.psm1.</span></span> <span data-ttu-id="c131d-136">In het volgende voor beeld worden de functies opgeslagen in een bestand met de naam Demo_IISWebsite. psm1.</span><span class="sxs-lookup"><span data-stu-id="c131d-136">In the following example, the functions are stored in a file called Demo_IISWebsite.psm1.</span></span>

> [!NOTE]
> <span data-ttu-id="c131d-137">Wanneer u hetzelfde configuratie script voor uw resource meer dan één keer uitvoert, worden er geen fouten weer gegeven en moet de resource dezelfde status blijven als het script eenmaal uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c131d-137">When you run the same configuration script on your resource more than once, you should receive no errors and the resource should remain in the same state as running the script once.</span></span> <span data-ttu-id="c131d-138">Om dit te bewerkstelligen, moet u ervoor zorgen dat de functies **Get-TargetResource** en **test-TargetResource** de resource ongewijzigd laten en dat de functie **set-TargetResource** meerdere keren wordt aangeroepen in een reeks met dezelfde parameter waarden.</span><span class="sxs-lookup"><span data-stu-id="c131d-138">To accomplish this, ensure that your **Get-TargetResource** and **Test-TargetResource** functions leave the resource unchanged, and that invoking the **Set-TargetResource** function more than once in a sequence with the same parameter values is always equivalent to invoking it once.</span></span>

<span data-ttu-id="c131d-139">Gebruik in de implementatie **Get-TargetResource** functie de belangrijkste eigenschaps waarden van de bron die zijn opgegeven als para meters om de status van het opgegeven bron exemplaar te controleren.</span><span class="sxs-lookup"><span data-stu-id="c131d-139">In the **Get-TargetResource** function implementation, use the key resource property values that are provided as parameters to check the status of the specified resource instance.</span></span> <span data-ttu-id="c131d-140">Deze functie moet een hash-tabel retour neren met een lijst van alle bron eigenschappen als sleutels en de werkelijke waarden van deze eigenschappen als de bijbehorende waarden.</span><span class="sxs-lookup"><span data-stu-id="c131d-140">This function must return a hash table that lists all the resource properties as keys and the actual values of these properties as the corresponding values.</span></span> <span data-ttu-id="c131d-141">De volgende code bevat een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="c131d-141">The following code provides an example.</span></span>

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

<span data-ttu-id="c131d-142">Afhankelijk van de waarden die zijn opgegeven voor de bron eigenschappen in het configuratie script, moet de **set-TargetResource** een van de volgende handelingen uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="c131d-142">Depending on the values that are specified for the resource properties in the configuration script, the **Set-TargetResource** must do one of the following:</span></span>

* <span data-ttu-id="c131d-143">Een nieuwe website maken</span><span class="sxs-lookup"><span data-stu-id="c131d-143">Create a new website</span></span>
* <span data-ttu-id="c131d-144">Een bestaande website bijwerken</span><span class="sxs-lookup"><span data-stu-id="c131d-144">Update an existing website</span></span>
* <span data-ttu-id="c131d-145">Een bestaande website verwijderen</span><span class="sxs-lookup"><span data-stu-id="c131d-145">Delete an existing website</span></span>

<span data-ttu-id="c131d-146">In het volgende voor beeld ziet u dit.</span><span class="sxs-lookup"><span data-stu-id="c131d-146">The following example illustrates this.</span></span>

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

<span data-ttu-id="c131d-147">Ten slotte moet de functie **test-TargetResource** dezelfde para meter instellen als **Get-TargetResource** en **set-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="c131d-147">Finally, the **Test-TargetResource** function must take the same parameter set as **Get-TargetResource** and **Set-TargetResource**.</span></span> <span data-ttu-id="c131d-148">Controleer in uw implementatie van **test-TargetResource**de status van het bron exemplaar dat is opgegeven in de sleutel parameters.</span><span class="sxs-lookup"><span data-stu-id="c131d-148">In your implementation of **Test-TargetResource**, check the status of the resource instance that is specified in the key parameters.</span></span> <span data-ttu-id="c131d-149">Als de werkelijke status van het bron exemplaar niet overeenkomt met de waarden die zijn opgegeven in de parameterset, retourneert **$False**.</span><span class="sxs-lookup"><span data-stu-id="c131d-149">If the actual status of the resource instance does not match the values specified in the parameter set, return **$false**.</span></span> <span data-ttu-id="c131d-150">Als dat niet het geval is, retourneert u **$True**.</span><span class="sxs-lookup"><span data-stu-id="c131d-150">Otherwise, return **$true**.</span></span>

<span data-ttu-id="c131d-151">Met de volgende code wordt de functie **test-TargetResource** geïmplementeerd.</span><span class="sxs-lookup"><span data-stu-id="c131d-151">The following code implements the **Test-TargetResource** function.</span></span>

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

<span data-ttu-id="c131d-152">**Opmerking**: voor eenvoudiger fout opsporing gebruikt u de cmdlet **Write-verbose** in uw implementatie van de vorige drie functies.</span><span class="sxs-lookup"><span data-stu-id="c131d-152">**Note**: For easier debugging, use the **Write-Verbose** cmdlet in your implementation of the previous three functions.</span></span>
><span data-ttu-id="c131d-153">Met deze cmdlet wordt tekst naar de uitgebreide berichten stroom geschreven.</span><span class="sxs-lookup"><span data-stu-id="c131d-153">This cmdlet writes text to the verbose message stream.</span></span>
><span data-ttu-id="c131d-154">De uitgebreide berichten stroom wordt standaard niet weer gegeven, maar u kunt deze weer geven door de waarde van de **$VerbosePreference** variabele te wijzigen of door de **uitgebreide** para meter in de DSC-cmdlets = New te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c131d-154">By default, the verbose message stream is not displayed, but you can display it by changing the value of the **$VerbosePreference** variable or by using the **Verbose** parameter in the DSC cmdlets = new.</span></span>

### <a name="creating-the-module-manifest"></a><span data-ttu-id="c131d-155">Het module manifest maken</span><span class="sxs-lookup"><span data-stu-id="c131d-155">Creating the module manifest</span></span>

<span data-ttu-id="c131d-156">Gebruik ten slotte de cmdlet **New-ModuleManifest** om een <ResourceName>psd1-bestand voor uw aangepaste resource module te definiëren.</span><span class="sxs-lookup"><span data-stu-id="c131d-156">Finally, use the **New-ModuleManifest** cmdlet to define a <ResourceName>.psd1 file for your custom resource module.</span></span> <span data-ttu-id="c131d-157">Wanneer u deze cmdlet aanroept, verwijst u naar het script module bestand (. psm1) dat wordt beschreven in de vorige sectie.</span><span class="sxs-lookup"><span data-stu-id="c131d-157">When you invoke this cmdlet, reference the script module (.psm1) file described in the previous section.</span></span> <span data-ttu-id="c131d-158">Neem **Get-TargetResource**, **set-TargetResource**en **test-TargetResource** op in de lijst met functies die moeten worden geëxporteerd.</span><span class="sxs-lookup"><span data-stu-id="c131d-158">Include **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** in the list of functions to export.</span></span> <span data-ttu-id="c131d-159">Hier volgt een voor beeld van een manifest bestand.</span><span class="sxs-lookup"><span data-stu-id="c131d-159">Following is an example manifest file.</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="c131d-160">PsDscRunAsCredential ondersteunen</span><span class="sxs-lookup"><span data-stu-id="c131d-160">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="c131d-161">**Opmerking:** **PsDscRunAsCredential** wordt ondersteund in Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c131d-161">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="c131d-162">De eigenschap **PsDscRunAsCredential** kan worden gebruikt in [DSC-configuratie](../configurations/configurations.md) bron blok om op te geven dat de resource moet worden uitgevoerd onder een opgegeven set referenties.</span><span class="sxs-lookup"><span data-stu-id="c131d-162">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="c131d-163">Zie [DSC uitvoeren met gebruikers referenties](../configurations/runAsUser.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c131d-163">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

<span data-ttu-id="c131d-164">Voor toegang tot de gebruikers context vanuit een aangepaste resource kunt u de automatische variabele `$PsDscContext`gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c131d-164">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="c131d-165">Met de volgende code wordt bijvoorbeeld de gebruikers context geschreven waarmee de resource wordt uitgevoerd naar de uitgebreide uitvoer stroom:</span><span class="sxs-lookup"><span data-stu-id="c131d-165">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="rebooting-the-node"></a><span data-ttu-id="c131d-166">Het knoop punt opnieuw opstarten</span><span class="sxs-lookup"><span data-stu-id="c131d-166">Rebooting the Node</span></span>

<span data-ttu-id="c131d-167">Als voor de acties die in `Set-TargetResource` de functie worden uitgevoerd, opnieuw moet worden opgestart, kunt u een globale vlag gebruiken om te geven dat de LCM het knoop punt opnieuw moet opstarten.</span><span class="sxs-lookup"><span data-stu-id="c131d-167">If the actions taken in your `Set-TargetResource` function require a reboot, you can use a global flag to tell the LCM to reboot the Node.</span></span> <span data-ttu-id="c131d-168">Het opnieuw opstarten vindt direct nadat `Set-TargetResource` de functie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="c131d-168">This reboot occurs directly after the `Set-TargetResource` function completes.</span></span>

<span data-ttu-id="c131d-169">Voeg in `Set-TargetResource` de functie de volgende regel code toe.</span><span class="sxs-lookup"><span data-stu-id="c131d-169">Inside your `Set-TargetResource` function, add the following line of code.</span></span>

```powershell
# Include this line if the resource requires a system reboot.
$global:DSCMachineStatus = 1
```

<span data-ttu-id="c131d-170">Om het knoop punt opnieuw op te starten, moet de **RebootNodeIfNeeded** -vlag worden ingesteld op `$true`.</span><span class="sxs-lookup"><span data-stu-id="c131d-170">In order for the LCM to reboot the Node, the **RebootNodeIfNeeded** flag needs to be set to `$true`.</span></span> <span data-ttu-id="c131d-171">De **ActionAfterReboot** -instelling moet ook worden ingesteld op **ContinueConfiguration**. Dit is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="c131d-171">The **ActionAfterReboot** setting should also be set to **ContinueConfiguration**, which is the default.</span></span> <span data-ttu-id="c131d-172">Zie [de lokale Configuration Manager configureren](../managing-nodes/metaConfig.md)of [de lokale Configuration Manager configureren (v4)](../managing-nodes/metaConfig4.md)voor meer informatie over het configureren van de LCM.</span><span class="sxs-lookup"><span data-stu-id="c131d-172">For more information on configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configuring the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>
