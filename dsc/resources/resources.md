---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC-Resources
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686066"
---
# <a name="dsc-resources"></a><span data-ttu-id="87c29-103">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="87c29-103">DSC Resources</span></span>

><span data-ttu-id="87c29-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="87c29-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="87c29-105">Desired State Configuration (DSC) bronnen vindt u de bouwstenen voor een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="87c29-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="87c29-106">Een resource beschrijft de eigenschappen die kunnen worden geconfigureerd (schema) en bevat de PowerShell-script-functies die de lokale Configuration Manager (LCM) zodat de "," aanroept.</span><span class="sxs-lookup"><span data-stu-id="87c29-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="87c29-107">Een resource kan iets als algemene als een bestand of de instelling van een IIS-server zo specifiek model.</span><span class="sxs-lookup"><span data-stu-id="87c29-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="87c29-108">Groepen, zoals resources worden gecombineerd in naar een DSC-Module, waarbij alle vereiste bestanden in een structuur die draagbare en is voorzien van metagegevens voor het identificeren van hoe de resources zijn bedoeld om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="87c29-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="87c29-109">Elke resource heeft een \* schema waarmee wordt bepaald van de syntaxis van de benodigde voor het gebruik van de resource in een [configuratie](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="87c29-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="87c29-110">Schema van een resource kan worden gedefinieerd in de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="87c29-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="87c29-111">**'Schema.Mof'** file: De meeste resources definiëren hun *schema* in een 'schema.mof'-bestand, met behulp van [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="87c29-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="87c29-112">**'\<Resourcenaam\>. schema.psm1'** bestand: [Samengestelde Resources](../configurations/compositeConfigs.md) definiëren hun *schema* in een '<ResourceName>. schema.psm1' met behulp van het bestand een [parameterblok](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="87c29-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="87c29-113">**'\<Resourcenaam\>.psm1'** bestand: Klasse van DSC-resources definiëren hun *schema* in het klassendefinitie van de.</span><span class="sxs-lookup"><span data-stu-id="87c29-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="87c29-114">Syntaxis van de items worden aangeduid als de klasse-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="87c29-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="87c29-115">Zie voor meer informatie, [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="87c29-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="87c29-116">Als u wilt ophalen van de syntaxis voor een DSC-resource, gebruikt u de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet met de `-Syntax` parameter.</span><span class="sxs-lookup"><span data-stu-id="87c29-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="87c29-117">Dit gebruik is vergelijkbaar met [Get-Command](/powershell/module/microsoft.powershell.core/get-command) met de `-Syntax` parameter om op te halen van de cmdlet-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="87c29-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="87c29-118">De uitvoer u ziet ziet de sjabloon die wordt gebruikt voor de blokkering van een resource voor de resource die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="87c29-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="87c29-119">De uitvoer u ziet zijn vergelijkbaar met de uitvoer hieronder, hoewel de syntaxis van deze resource in de toekomst kan veranderen.</span><span class="sxs-lookup"><span data-stu-id="87c29-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="87c29-120">Syntaxis van de cmdlet, zoals de *sleutels* weergegeven tussen vierkante haken, zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="87c29-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="87c29-121">De typen Geef het type gegevens die elke sleutel wordt verwacht.</span><span class="sxs-lookup"><span data-stu-id="87c29-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="87c29-122">De **Zorg ervoor dat** sleutel is optioneel, omdat deze standaard ingesteld op 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="87c29-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

<span data-ttu-id="87c29-123">In een configuratie met een **Service** resource blok kan er als volgt aan **Zorg ervoor dat** die de Spooler-service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="87c29-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="87c29-124">Voordat u een resource in een configuratie gebruikt, moet u importeren met behulp van [sleutelwoorden Import-dscresource bieden](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="87c29-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="87c29-125">Configuraties kunnen meerdere exemplaren van hetzelfde resourcetype bevatten.</span><span class="sxs-lookup"><span data-stu-id="87c29-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="87c29-126">Elk exemplaar moet een unieke naam hebben.</span><span class="sxs-lookup"><span data-stu-id="87c29-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="87c29-127">In het volgende voorbeeld wordt een tweede **Service** resource blok wordt toegevoegd aan de 'DHCP'-service configureren.</span><span class="sxs-lookup"><span data-stu-id="87c29-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="87c29-128">Begin in PowerShell 5.0, is intellisense toegevoegd voor DSC.</span><span class="sxs-lookup"><span data-stu-id="87c29-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="87c29-129">Deze nieuwe functie kunt u gebruikmaken van \<tabblad\> en \<Ctrl + spatie\> naar sleutelnamen automatisch aanvullen.</span><span class="sxs-lookup"><span data-stu-id="87c29-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Tab-aanvulling van resource](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="87c29-131">Ingebouwde resources</span><span class="sxs-lookup"><span data-stu-id="87c29-131">Built-in resources</span></span>

<span data-ttu-id="87c29-132">Naast de bronnen van de community zijn er ingebouwde resources voor Windows, resources voor Linux en resources voor de afhankelijkheid van meerdere knooppunten.</span><span class="sxs-lookup"><span data-stu-id="87c29-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="87c29-133">U kunt de bovenstaande stappen gebruiken om te bepalen van de syntaxis van deze resources en het gebruik ervan.</span><span class="sxs-lookup"><span data-stu-id="87c29-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="87c29-134">De pagina's die u beschikbaar deze resources maakt zijn gearchiveerd onder **verwijzing**.</span><span class="sxs-lookup"><span data-stu-id="87c29-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="87c29-135">Ingebouwde Windows-resources</span><span class="sxs-lookup"><span data-stu-id="87c29-135">Windows built-in resources</span></span>

* [<span data-ttu-id="87c29-136">Archiefresource</span><span class="sxs-lookup"><span data-stu-id="87c29-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="87c29-137">Omgevingsresource</span><span class="sxs-lookup"><span data-stu-id="87c29-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="87c29-138">Bestandsresource</span><span class="sxs-lookup"><span data-stu-id="87c29-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="87c29-139">Groepsresource</span><span class="sxs-lookup"><span data-stu-id="87c29-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="87c29-140">GroupSet-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="87c29-141">Logboekresource</span><span class="sxs-lookup"><span data-stu-id="87c29-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="87c29-142">Pakketresource</span><span class="sxs-lookup"><span data-stu-id="87c29-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="87c29-143">ProcessSet-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="87c29-144">Registerresource</span><span class="sxs-lookup"><span data-stu-id="87c29-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="87c29-145">Scriptresource</span><span class="sxs-lookup"><span data-stu-id="87c29-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="87c29-146">Serviceresource</span><span class="sxs-lookup"><span data-stu-id="87c29-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="87c29-147">ServiceSet-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="87c29-148">Gebruikersresource</span><span class="sxs-lookup"><span data-stu-id="87c29-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="87c29-149">WindowsFeature-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="87c29-150">WindowsFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="87c29-151">WindowsOptionalFeature-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="87c29-152">WindowsOptionalFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="87c29-153">WindowsPackageCabResource Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="87c29-154">WindowsProcess-resource</span><span class="sxs-lookup"><span data-stu-id="87c29-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="87c29-155">[Afhankelijkheid van meerdere knooppunten](../configurations/crossNodeDependencies.md) resources</span><span class="sxs-lookup"><span data-stu-id="87c29-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="87c29-156">WaitForAll Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="87c29-157">WaitForSome Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="87c29-158">WaitForAny Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="87c29-159">Package Management-resources</span><span class="sxs-lookup"><span data-stu-id="87c29-159">Package Management resources</span></span>

* [<span data-ttu-id="87c29-160">PackageManagement Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="87c29-161">PackageManagementSource Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="87c29-162">Linux-resources</span><span class="sxs-lookup"><span data-stu-id="87c29-162">Linux resources</span></span>

* [<span data-ttu-id="87c29-163">Linux-Archiefresource</span><span class="sxs-lookup"><span data-stu-id="87c29-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="87c29-164">Linux-Omgevingsresource</span><span class="sxs-lookup"><span data-stu-id="87c29-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="87c29-165">Linux FileLine Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="87c29-166">Linux-bestand voor Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="87c29-167">Linux-groep-Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="87c29-168">Linux-Pakketresource</span><span class="sxs-lookup"><span data-stu-id="87c29-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="87c29-169">Linux Script Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="87c29-170">Linux Service Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="87c29-171">Linux SshAuthorizedKeys Resource</span><span class="sxs-lookup"><span data-stu-id="87c29-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="87c29-172">Linux-gebruikersbron</span><span class="sxs-lookup"><span data-stu-id="87c29-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
