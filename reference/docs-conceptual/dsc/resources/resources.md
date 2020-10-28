---
ms.date: 07/23/2020
keywords: DSC, Power shell, configuratie, installatie
title: DSC-resources
description: DSC-resources bieden de bouw stenen voor een DSC-configuratie. Een resource beschrijft eigenschappen die kunnen worden geconfigureerd (schema) en bevat de Power shell-script functies die door de LCM worden gebruikt om de configuratie toe te passen.
ms.openlocfilehash: 1634db84deff8de3b33c941ad738dc21cf3017ac
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658443"
---
# <a name="dsc-resources"></a><span data-ttu-id="00a68-105">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="00a68-105">DSC Resources</span></span>

> <span data-ttu-id="00a68-106">Is van toepassing op Windows Power Shell 4,0 en up.</span><span class="sxs-lookup"><span data-stu-id="00a68-106">Applies to Windows PowerShell 4.0 and up.</span></span>

## <a name="overview"></a><span data-ttu-id="00a68-107">Overzicht</span><span class="sxs-lookup"><span data-stu-id="00a68-107">Overview</span></span>

<span data-ttu-id="00a68-108">Resources voor desired state Configuration (DSC) bieden de bouw stenen voor een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="00a68-108">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="00a68-109">Een resource kan eigenschappen weer geven die kunnen worden geconfigureerd (schema) en de Power shell-script functies bevat die de lokale Configuration Manager (LCM) aanroept om het te maken.</span><span class="sxs-lookup"><span data-stu-id="00a68-109">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="00a68-110">Een resource kan een model als algemeen hebben als een bestand of als een IIS-server instelling.</span><span class="sxs-lookup"><span data-stu-id="00a68-110">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="00a68-111">Groepen van like-resources worden gecombineerd in naar een DSC-module, waarmee alle vereiste bestanden in worden ingedeeld in een geportablee structuur en die meta gegevens bevat om te bepalen hoe de resources zijn bedoeld om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00a68-111">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="00a68-112">Elke resource heeft een \*-schema dat bepaalt de syntaxis die nodig is voor het gebruik van de bron in een [configuratie](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="00a68-112">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="00a68-113">Het schema van een resource kan op de volgende manieren worden gedefinieerd:</span><span class="sxs-lookup"><span data-stu-id="00a68-113">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="00a68-114">`Schema.Mof` bestand: de meeste resources definiëren hun _schema_ in een `schema.mof` bestand met behulp van [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="00a68-114">`Schema.Mof` file: Most resources define their _schema_ in a `schema.mof` file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="00a68-115">`<Resource Name>.schema.psm1` bestand: [samengestelde resources](../configurations/compositeConfigs.md) definiëren hun _schema_ in een `<ResourceName>.schema.psm1` bestand met behulp van een [parameter blok](/powershell/module/microsoft.powershell.core/about/about_functions#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="00a68-115">`<Resource Name>.schema.psm1` file: [Composite Resources](../configurations/compositeConfigs.md) define their _schema_ in a `<ResourceName>.schema.psm1` file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions#functions-with-parameters).</span></span>
- <span data-ttu-id="00a68-116">`<Resource Name>.psm1` bestand: DSC-resources op basis van klassen definiëren hun _schema_ in de klassedefinitie.</span><span class="sxs-lookup"><span data-stu-id="00a68-116">`<Resource Name>.psm1` file: Class based DSC resources define their _schema_ in the class definition.</span></span> <span data-ttu-id="00a68-117">Syntaxis items worden aangeduid als klasse-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="00a68-117">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="00a68-118">Zie [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="00a68-118">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="00a68-119">Als u de syntaxis voor een DSC-resource wilt ophalen, gebruikt u de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) met de para meter **syntax** .</span><span class="sxs-lookup"><span data-stu-id="00a68-119">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the **Syntax** parameter.</span></span> <span data-ttu-id="00a68-120">Dit gebruik is vergelijkbaar met het gebruik van [Get-opdracht](/powershell/module/microsoft.powershell.core/get-command) met de **syntaxis** parameter om de syntaxis van de cmdlet op te halen.</span><span class="sxs-lookup"><span data-stu-id="00a68-120">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the **Syntax** parameter to get cmdlet syntax.</span></span> <span data-ttu-id="00a68-121">De uitvoer die wordt weer gegeven, toont de sjabloon die wordt gebruikt voor een resource blok voor de resource die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="00a68-121">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="00a68-122">De uitvoer die u ziet, moet vergelijkbaar zijn met de onderstaande uitvoer, hoewel de syntaxis van deze resource in de toekomst kan veranderen.</span><span class="sxs-lookup"><span data-stu-id="00a68-122">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="00a68-123">Net als de syntaxis van de cmdlet zijn de _sleutels_ in vier Kante haken optioneel.</span><span class="sxs-lookup"><span data-stu-id="00a68-123">Like cmdlet syntax, the _keys_ seen in square brackets, are optional.</span></span> <span data-ttu-id="00a68-124">De typen geven het type gegevens op dat elke sleutel verwacht.</span><span class="sxs-lookup"><span data-stu-id="00a68-124">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="00a68-125">De sleutel **controleren** is optioneel omdat deze standaard is ingesteld op pres.</span><span class="sxs-lookup"><span data-stu-id="00a68-125">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

> [!NOTE]
> <span data-ttu-id="00a68-126">In Power shell-versies onder 7,0 worden `Get-DscResource` op klassen gebaseerde DSC-resources niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="00a68-126">In PowerShell versions below 7.0, `Get-DscResource` does not find Class based DSC resources.</span></span>

<span data-ttu-id="00a68-127">Binnen een configuratie kan een **service** bron blok er als volgt uitzien, om **ervoor te zorgen** dat de Spooler-service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="00a68-127">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="00a68-128">Voordat u een resource in een configuratie gaat gebruiken, moet u deze importeren met [import-dscresource bieden](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="00a68-128">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the
    # resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as l
        # ong as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

<span data-ttu-id="00a68-129">Configuraties kunnen meerdere exemplaren van hetzelfde bron type bevatten.</span><span class="sxs-lookup"><span data-stu-id="00a68-129">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="00a68-130">Elk exemplaar moet een unieke naam hebben.</span><span class="sxs-lookup"><span data-stu-id="00a68-130">Each instance must be uniquely named.</span></span> <span data-ttu-id="00a68-131">In het volgende voor beeld wordt een tweede **service** resource blok toegevoegd voor het configureren van de DHCP-service.</span><span class="sxs-lookup"><span data-stu-id="00a68-131">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the
    # resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as
        # long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service
        # resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="00a68-132">Vanaf Power shell 5,0 is IntelliSense toegevoegd voor DSC.</span><span class="sxs-lookup"><span data-stu-id="00a68-132">Beginning in PowerShell 5.0, IntelliSense was added for DSC.</span></span> <span data-ttu-id="00a68-133">Met deze nieuwe functie kunt u de <kbd>Tab</kbd> - <kbd>en</kbd> + <kbd>plaatsings ruimte</kbd> gebruiken om sleutel namen automatisch te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="00a68-133">This new feature allows you to use <kbd>TAB</kbd> and <kbd>Ctr</kbd>+<kbd>Space</kbd> to auto-complete key names.</span></span>

![Resource IntelliSense met Tab-aanvulling](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a><span data-ttu-id="00a68-135">Typen resources</span><span class="sxs-lookup"><span data-stu-id="00a68-135">Types of resources</span></span>

<span data-ttu-id="00a68-136">Windows wordt geleverd met ingebouwde resources en Linux heeft specifieke resources voor het besturings systeem.</span><span class="sxs-lookup"><span data-stu-id="00a68-136">Windows comes with built in resources and Linux has OS specific resources.</span></span> <span data-ttu-id="00a68-137">Er zijn resources voor [afhankelijkheden tussen knoop punten](../configurations/crossNodeDependencies.md), resources voor pakket beheer en[resources die eigendom](https://github.com/dsccommunity)zijn van de community.</span><span class="sxs-lookup"><span data-stu-id="00a68-137">There are resources for [cross-node dependencies](../configurations/crossNodeDependencies.md), package management resources, as well as[community owned and maintained resources](https://github.com/dsccommunity).</span></span> <span data-ttu-id="00a68-138">U kunt de bovenstaande stappen gebruiken om de syntaxis van deze resources te bepalen en hoe u deze gebruikt.</span><span class="sxs-lookup"><span data-stu-id="00a68-138">You can use the above steps to determine the syntax of these resources and how to use them.</span></span> <span data-ttu-id="00a68-139">De pagina's van deze resources zijn onder **verwijzing** gearchiveerd.</span><span class="sxs-lookup"><span data-stu-id="00a68-139">The pages that serve these resources have been archived under **Reference** .</span></span>

### <a name="windows-built-in-resources"></a><span data-ttu-id="00a68-140">Ingebouwde Windows-resources</span><span class="sxs-lookup"><span data-stu-id="00a68-140">Windows built-in resources</span></span>

- [<span data-ttu-id="00a68-141">Archiefresource</span><span class="sxs-lookup"><span data-stu-id="00a68-141">Archive Resource</span></span>](../reference/resources/windows/archiveResource.md)
- [<span data-ttu-id="00a68-142">Omgevingsresource</span><span class="sxs-lookup"><span data-stu-id="00a68-142">Environment Resource</span></span>](../reference/resources/windows/environmentResource.md)
- [<span data-ttu-id="00a68-143">Bestandsresource</span><span class="sxs-lookup"><span data-stu-id="00a68-143">File Resource</span></span>](../reference/resources/windows/fileResource.md)
- [<span data-ttu-id="00a68-144">Groepsresource</span><span class="sxs-lookup"><span data-stu-id="00a68-144">Group Resource</span></span>](../reference/resources/windows/groupResource.md)
- [<span data-ttu-id="00a68-145">GroupSet-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-145">GroupSet Resource</span></span>](../reference/resources/windows/groupSetResource.md)
- [<span data-ttu-id="00a68-146">Logboekresource</span><span class="sxs-lookup"><span data-stu-id="00a68-146">Log Resource</span></span>](../reference/resources/windows/logResource.md)
- [<span data-ttu-id="00a68-147">Pakketresource</span><span class="sxs-lookup"><span data-stu-id="00a68-147">Package Resource</span></span>](../reference/resources/windows/packageResource.md)
- [<span data-ttu-id="00a68-148">ProcessSet-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-148">ProcessSet Resource</span></span>](../reference/resources/windows/ProcessSetResource.md)
- [<span data-ttu-id="00a68-149">Registerresource</span><span class="sxs-lookup"><span data-stu-id="00a68-149">Registry Resource</span></span>](../reference/resources/windows/registryResource.md)
- [<span data-ttu-id="00a68-150">Scriptresource</span><span class="sxs-lookup"><span data-stu-id="00a68-150">Script Resource</span></span>](../reference/resources/windows/scriptResource.md)
- [<span data-ttu-id="00a68-151">Serviceresource</span><span class="sxs-lookup"><span data-stu-id="00a68-151">Service Resource</span></span>](../reference/resources/windows/serviceResource.md)
- [<span data-ttu-id="00a68-152">ServiceSet-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-152">ServiceSet Resource</span></span>](../reference/resources/windows/serviceSetResource.md)
- [<span data-ttu-id="00a68-153">Gebruikersresource</span><span class="sxs-lookup"><span data-stu-id="00a68-153">User Resource</span></span>](../reference/resources/windows/userResource.md)
- [<span data-ttu-id="00a68-154">WindowsFeature-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-154">WindowsFeature Resource</span></span>](../reference/resources/windows/windowsFeatureResource.md)
- [<span data-ttu-id="00a68-155">WindowsFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-155">WindowsFeatureSet Resource</span></span>](../reference/resources/windows/windowsFeatureSetResource.md)
- [<span data-ttu-id="00a68-156">WindowsOptionalFeature-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-156">WindowsOptionalFeature Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [<span data-ttu-id="00a68-157">WindowsOptionalFeatureSet-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-157">WindowsOptionalFeatureSet Resource</span></span>](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [<span data-ttu-id="00a68-158">WindowsPackageCabResource-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-158">WindowsPackageCabResource Resource</span></span>](../reference/resources/windows/windowsPackageCabResource.md)
- [<span data-ttu-id="00a68-159">WindowsProcess-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-159">WindowsProcess Resource</span></span>](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a><span data-ttu-id="00a68-160">Afhankelijkheids bronnen voor meerdere knoop punten</span><span class="sxs-lookup"><span data-stu-id="00a68-160">Cross-Node dependency resources</span></span>

- [<span data-ttu-id="00a68-161">WaitForAll-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-161">WaitForAll Resource</span></span>](../reference/resources/windows/waitForAllResource.md)
- [<span data-ttu-id="00a68-162">WaitForSome-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-162">WaitForSome Resource</span></span>](../reference/resources/windows/waitForSomeResource.md)
- [<span data-ttu-id="00a68-163">WaitForAny-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-163">WaitForAny Resource</span></span>](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a><span data-ttu-id="00a68-164">Pakket beheer resources</span><span class="sxs-lookup"><span data-stu-id="00a68-164">Package Management resources</span></span>

- [<span data-ttu-id="00a68-165">Package Management-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-165">PackageManagement Resource</span></span>](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [<span data-ttu-id="00a68-166">PackageManagementSource-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-166">PackageManagementSource Resource</span></span>](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a><span data-ttu-id="00a68-167">Linux-Resources</span><span class="sxs-lookup"><span data-stu-id="00a68-167">Linux resources</span></span>

- [<span data-ttu-id="00a68-168">Resource voor Linux-archief</span><span class="sxs-lookup"><span data-stu-id="00a68-168">Linux Archive Resource</span></span>](../reference/resources/linux/lnxArchiveResource.md)
- [<span data-ttu-id="00a68-169">Resource van Linux-omgeving</span><span class="sxs-lookup"><span data-stu-id="00a68-169">Linux Environment Resource</span></span>](../reference/resources/linux/lnxEnvironmentResource.md)
- [<span data-ttu-id="00a68-170">Linux FileLine-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-170">Linux FileLine Resource</span></span>](../reference/resources/linux/lnxFileLineResource.md)
- [<span data-ttu-id="00a68-171">Linux-bestands resource</span><span class="sxs-lookup"><span data-stu-id="00a68-171">Linux File Resource</span></span>](../reference/resources/linux/lnxFileResource.md)
- [<span data-ttu-id="00a68-172">Resource van Linux-groep</span><span class="sxs-lookup"><span data-stu-id="00a68-172">Linux Group Resource</span></span>](../reference/resources/linux/lnxGroupResource.md)
- [<span data-ttu-id="00a68-173">Linux-pakket resource</span><span class="sxs-lookup"><span data-stu-id="00a68-173">Linux Package Resource</span></span>](../reference/resources/linux/lnxPackageResource.md)
- [<span data-ttu-id="00a68-174">Linux-script bron</span><span class="sxs-lookup"><span data-stu-id="00a68-174">Linux Script Resource</span></span>](../reference/resources/linux/lnxScriptResource.md)
- [<span data-ttu-id="00a68-175">Resource van Linux-service</span><span class="sxs-lookup"><span data-stu-id="00a68-175">Linux Service Resource</span></span>](../reference/resources/linux/lnxServiceResource.md)
- [<span data-ttu-id="00a68-176">Linux SshAuthorizedKeys-resource</span><span class="sxs-lookup"><span data-stu-id="00a68-176">Linux SshAuthorizedKeys Resource</span></span>](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [<span data-ttu-id="00a68-177">Linux-gebruikers resource</span><span class="sxs-lookup"><span data-stu-id="00a68-177">Linux User Resource</span></span>](../reference/resources/linux/lnxUserResource.md)
