---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: DSC-resources
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942151"
---
# <a name="dsc-resources"></a><span data-ttu-id="64e33-103">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="64e33-103">DSC Resources</span></span>

><span data-ttu-id="64e33-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="64e33-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="64e33-105">Resources voor desired state Configuration (DSC) bieden de bouw stenen voor een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="64e33-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="64e33-106">Een resource kan eigenschappen weer geven die kunnen worden geconfigureerd (schema) en de Power shell-script functies bevat die de lokale Configuration Manager (LCM) aanroept om het te maken.</span><span class="sxs-lookup"><span data-stu-id="64e33-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="64e33-107">Een resource kan een model als algemeen hebben als een bestand of als een IIS-server instelling.</span><span class="sxs-lookup"><span data-stu-id="64e33-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="64e33-108">Groepen van like-resources worden gecombineerd in naar een DSC-module, waarmee alle vereiste bestanden in worden ingedeeld in een geportablee structuur en die meta gegevens bevat om te bepalen hoe de resources zijn bedoeld om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="64e33-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="64e33-109">Elke resource heeft een \*-schema dat bepaalt de syntaxis die nodig is voor het gebruik van de bron in een [configuratie](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="64e33-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="64e33-110">Het schema van een resource kan op de volgende manieren worden gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="64e33-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="64e33-111">Bestand van het **schema. MOF** : De meeste resources definiëren hun *schema* in een ' schema. mof '-bestand met behulp van [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="64e33-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="64e33-112">**' \<Resource naam @ no__t-2. schema. psm1 '** bestand: [Samengestelde resources](../configurations/compositeConfigs.md) definiëren hun *schema* in een ' @no__t -2. schema. psm1-bestand met behulp van een [parameter blok](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="64e33-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="64e33-113">**' \<Resource naam @ no__t-2. psm1 '** bestand: DSC-resources op basis van klassen definiëren hun *schema* in de klassedefinitie.</span><span class="sxs-lookup"><span data-stu-id="64e33-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="64e33-114">Syntaxis items worden aangeduid als klasse-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="64e33-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="64e33-115">Zie [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="64e33-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="64e33-116">Als u de syntaxis voor een DSC-resource wilt ophalen, gebruikt u de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) met de para meter `-Syntax`.</span><span class="sxs-lookup"><span data-stu-id="64e33-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="64e33-117">Dit gebruik is vergelijkbaar met het gebruik van [Get-opdracht](/powershell/module/microsoft.powershell.core/get-command) met de para meter `-Syntax` om de syntaxis van de cmdlet op te halen.</span><span class="sxs-lookup"><span data-stu-id="64e33-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="64e33-118">De uitvoer die wordt weer gegeven, toont de sjabloon die wordt gebruikt voor een resource blok voor de resource die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="64e33-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="64e33-119">De uitvoer die u ziet, moet vergelijkbaar zijn met de onderstaande uitvoer, hoewel de syntaxis van deze resource in de toekomst kan veranderen.</span><span class="sxs-lookup"><span data-stu-id="64e33-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="64e33-120">Net als de syntaxis van de cmdlet zijn de *sleutels* in vier Kante haken optioneel.</span><span class="sxs-lookup"><span data-stu-id="64e33-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="64e33-121">De typen geven het type gegevens op dat elke sleutel verwacht.</span><span class="sxs-lookup"><span data-stu-id="64e33-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="64e33-122">De sleutel **controleren** is optioneel omdat deze standaard is ingesteld op pres.</span><span class="sxs-lookup"><span data-stu-id="64e33-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="64e33-123">Binnen een configuratie kan een **service** bron blok er als volgt uitzien, om **ervoor te zorgen** dat de Spooler-service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="64e33-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="64e33-124">Voordat u een resource in een configuratie gaat gebruiken, moet u deze importeren met [import-dscresource bieden](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="64e33-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="64e33-125">Configuraties kunnen meerdere exemplaren van hetzelfde bron type bevatten.</span><span class="sxs-lookup"><span data-stu-id="64e33-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="64e33-126">Elk exemplaar moet een unieke naam hebben.</span><span class="sxs-lookup"><span data-stu-id="64e33-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="64e33-127">In het volgende voor beeld wordt een tweede **service** resource blok toegevoegd voor het configureren van de DHCP-service.</span><span class="sxs-lookup"><span data-stu-id="64e33-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="64e33-128">Vanaf Power shell 5,0 is IntelliSense toegevoegd voor DSC.</span><span class="sxs-lookup"><span data-stu-id="64e33-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="64e33-129">Met deze nieuwe functie kunt u \<TAB @ no__t-1 en \<Ctrl + Space @ no__t-3 gebruiken om sleutel namen automatisch te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="64e33-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Voltooiing van resource tabblad](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a><span data-ttu-id="64e33-131">Ingebouwde resources</span><span class="sxs-lookup"><span data-stu-id="64e33-131">Built-in resources</span></span>

<span data-ttu-id="64e33-132">Naast de community-bronnen zijn er ingebouwde resources voor Windows, resources voor Linux en bronnen voor afhankelijkheid tussen knoop punten.</span><span class="sxs-lookup"><span data-stu-id="64e33-132">In addition to community resources, there are built-in resources for Windows, resources for Linux, and resources for cross-node dependency.</span></span> <span data-ttu-id="64e33-133">U kunt de bovenstaande stappen gebruiken om de syntaxis van deze resources te bepalen en hoe u deze gebruikt.</span><span class="sxs-lookup"><span data-stu-id="64e33-133">You can use the steps above to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="64e33-134">De pagina's van deze resources zijn onder **verwijzing**gearchiveerd.</span><span class="sxs-lookup"><span data-stu-id="64e33-134">The pages that serve these resources have been archived under **Reference**.</span></span>

<span data-ttu-id="64e33-135">Ingebouwde Windows-resources</span><span class="sxs-lookup"><span data-stu-id="64e33-135">Windows built-in resources</span></span>

* [<span data-ttu-id="64e33-136">Archiefresource</span><span class="sxs-lookup"><span data-stu-id="64e33-136">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
* [<span data-ttu-id="64e33-137">Omgevingsresource</span><span class="sxs-lookup"><span data-stu-id="64e33-137">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
* [<span data-ttu-id="64e33-138">Bestandsresource</span><span class="sxs-lookup"><span data-stu-id="64e33-138">File Resource</span></span>](../reference/resources/windows/fileResource.md)
* [<span data-ttu-id="64e33-139">Groepsresource</span><span class="sxs-lookup"><span data-stu-id="64e33-139">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
* [<span data-ttu-id="64e33-140">GroupSet-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-140">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
* [<span data-ttu-id="64e33-141">Logboekresource</span><span class="sxs-lookup"><span data-stu-id="64e33-141">Log Resource</span></span>](../reference/resources/windows/logResource.md)
* [<span data-ttu-id="64e33-142">Pakketresource</span><span class="sxs-lookup"><span data-stu-id="64e33-142">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
* [<span data-ttu-id="64e33-143">ProcessSet-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-143">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
* [<span data-ttu-id="64e33-144">Registerresource</span><span class="sxs-lookup"><span data-stu-id="64e33-144">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
* [<span data-ttu-id="64e33-145">Scriptresource</span><span class="sxs-lookup"><span data-stu-id="64e33-145">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
* [<span data-ttu-id="64e33-146">Serviceresource</span><span class="sxs-lookup"><span data-stu-id="64e33-146">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
* [<span data-ttu-id="64e33-147">ServiceSet-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-147">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
* [<span data-ttu-id="64e33-148">Gebruikersresource</span><span class="sxs-lookup"><span data-stu-id="64e33-148">User Resource</span></span>](../reference/resources/windows/userResource.md)
* [<span data-ttu-id="64e33-149">WindowsFeature-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-149">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
* [<span data-ttu-id="64e33-150">WindowsFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-150">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
* [<span data-ttu-id="64e33-151">WindowsOptionalFeature-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-151">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [<span data-ttu-id="64e33-152">WindowsOptionalFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-152">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [<span data-ttu-id="64e33-153">WindowsPackageCabResource-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-153">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
* [<span data-ttu-id="64e33-154">WindowsProcess-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-154">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

<span data-ttu-id="64e33-155">[Afhankelijkheids bronnen voor meerdere knoop punten](../configurations/crossNodeDependencies.md)</span><span class="sxs-lookup"><span data-stu-id="64e33-155">[Cross-Node dependency](../configurations/crossNodeDependencies.md) resources</span></span>

* [<span data-ttu-id="64e33-156">WaitForAll-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-156">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
* [<span data-ttu-id="64e33-157">WaitForSome-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-157">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
* [<span data-ttu-id="64e33-158">WaitForAny-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-158">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

<span data-ttu-id="64e33-159">Pakket beheer resources</span><span class="sxs-lookup"><span data-stu-id="64e33-159">Package Management resources</span></span>

* [<span data-ttu-id="64e33-160">Package Management-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-160">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [<span data-ttu-id="64e33-161">PackageManagementSource-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-161">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

<span data-ttu-id="64e33-162">Linux-Resources</span><span class="sxs-lookup"><span data-stu-id="64e33-162">Linux resources</span></span>

* [<span data-ttu-id="64e33-163">Resource voor Linux-archief</span><span class="sxs-lookup"><span data-stu-id="64e33-163">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
* [<span data-ttu-id="64e33-164">Resource van Linux-omgeving</span><span class="sxs-lookup"><span data-stu-id="64e33-164">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
* [<span data-ttu-id="64e33-165">Linux FileLine-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-165">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
* [<span data-ttu-id="64e33-166">Linux-bestands resource</span><span class="sxs-lookup"><span data-stu-id="64e33-166">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
* [<span data-ttu-id="64e33-167">Resource van Linux-groep</span><span class="sxs-lookup"><span data-stu-id="64e33-167">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
* [<span data-ttu-id="64e33-168">Linux-pakket resource</span><span class="sxs-lookup"><span data-stu-id="64e33-168">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
* [<span data-ttu-id="64e33-169">Linux-script bron</span><span class="sxs-lookup"><span data-stu-id="64e33-169">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
* [<span data-ttu-id="64e33-170">Resource van Linux-service</span><span class="sxs-lookup"><span data-stu-id="64e33-170">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
* [<span data-ttu-id="64e33-171">Linux SshAuthorizedKeys-resource</span><span class="sxs-lookup"><span data-stu-id="64e33-171">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [<span data-ttu-id="64e33-172">Linux-gebruikers resource</span><span class="sxs-lookup"><span data-stu-id="64e33-172">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
