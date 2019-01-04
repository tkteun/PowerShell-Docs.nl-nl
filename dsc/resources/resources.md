---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC-Resources
ms.openlocfilehash: 02e1b9856942cf28e77d83dac89681a08cf6bb74
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012446"
---
# <a name="dsc-resources"></a><span data-ttu-id="a3210-103">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="a3210-103">DSC Resources</span></span>

><span data-ttu-id="a3210-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="a3210-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="a3210-105">Desired State Configuration (DSC) bronnen vindt u de bouwstenen voor een DSC-configuratie.</span><span class="sxs-lookup"><span data-stu-id="a3210-105">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="a3210-106">Een resource beschrijft de eigenschappen die kunnen worden geconfigureerd (schema) en bevat de PowerShell-script-functies die de lokale Configuration Manager (LCM) zodat de "," aanroept.</span><span class="sxs-lookup"><span data-stu-id="a3210-106">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="a3210-107">Een resource kan iets als algemene als een bestand of de instelling van een IIS-server zo specifiek model.</span><span class="sxs-lookup"><span data-stu-id="a3210-107">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span>  <span data-ttu-id="a3210-108">Groepen, zoals resources worden gecombineerd in naar een DSC-Module, waarbij alle vereiste bestanden in een structuur die draagbare en is voorzien van metagegevens voor het identificeren van hoe de resources zijn bedoeld om te worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a3210-108">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

<span data-ttu-id="a3210-109">Elke resource heeft een \* schema waarmee wordt bepaald van de syntaxis van de benodigde voor het gebruik van de resource in een [configuratie](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a3210-109">Each resource has a \*schema that determines the syntax needed to use the resource in a [Configuration](../configurations/configurations.md).</span></span> <span data-ttu-id="a3210-110">Schema van een resource kan worden gedefinieerd in de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="a3210-110">A resource's schema can be defined in the following ways:</span></span>

- <span data-ttu-id="a3210-111">**'Schema.Mof'** bestand: De meeste resources definiëren hun *schema* in een 'schema.mof'-bestand, met behulp van [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span><span class="sxs-lookup"><span data-stu-id="a3210-111">**'Schema.Mof'** file: Most resources define their *schema* in a 'schema.mof' file, using [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).</span></span>
- <span data-ttu-id="a3210-112">**'\<Resourcenaam\>. schema.psm1'** bestand: [Samengestelde Resources](../configurations/compositeConfigs.md) definiëren hun *schema* in een '<ResourceName>. schema.psm1' met behulp van het bestand een [parameterblok](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span><span class="sxs-lookup"><span data-stu-id="a3210-112">**'\<Resource Name\>.schema.psm1'** file: [Composite Resources](../configurations/compositeConfigs.md) define their *schema* in a '<ResourceName>.schema.psm1' file using a [Parameter Block](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).</span></span>
- <span data-ttu-id="a3210-113">**'\<Resourcenaam\>.psm1'** bestand: Klasse van DSC-resources definiëren hun *schema* in het klassendefinitie van de.</span><span class="sxs-lookup"><span data-stu-id="a3210-113">**'\<Resource Name\>.psm1'** file: Class based DSC resources define their *schema* in the class definition.</span></span> <span data-ttu-id="a3210-114">Syntaxis van de items worden aangeduid als de klasse-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="a3210-114">Syntax items are denoted as Class properties.</span></span> <span data-ttu-id="a3210-115">Zie voor meer informatie, [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span><span class="sxs-lookup"><span data-stu-id="a3210-115">For more information, see [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).</span></span>

<span data-ttu-id="a3210-116">Als u wilt ophalen van de syntaxis voor een DSC-resource, gebruikt u de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet met de `-Syntax` parameter.</span><span class="sxs-lookup"><span data-stu-id="a3210-116">To retrieve the syntax for a DSC resource, use the [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet with the `-Syntax` parameter.</span></span> <span data-ttu-id="a3210-117">Dit gebruik is vergelijkbaar met [Get-Command](/powershell/module/microsoft.powershell.core/get-command) met de `-Syntax` parameter om op te halen van de cmdlet-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="a3210-117">This usage is similar to using [Get-Command](/powershell/module/microsoft.powershell.core/get-command) with the `-Syntax` parameter to get cmdlet syntax.</span></span> <span data-ttu-id="a3210-118">De uitvoer u ziet ziet de sjabloon die wordt gebruikt voor de blokkering van een resource voor de resource die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="a3210-118">The output you see will show the template used for a resource block for the resource you specify.</span></span>

```powershell
Get-DscResource -Syntax Service
```

<span data-ttu-id="a3210-119">De uitvoer u ziet zijn vergelijkbaar met de uitvoer hieronder, hoewel de syntaxis van deze resource in de toekomst kan veranderen.</span><span class="sxs-lookup"><span data-stu-id="a3210-119">The output you see should be similar to the output below, though this resource's syntax could change in the future.</span></span> <span data-ttu-id="a3210-120">Syntaxis van de cmdlet, zoals de *sleutels* weergegeven tussen vierkante haken, zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="a3210-120">Like cmdlet syntax, the *keys* seen in square brackets, are optional.</span></span> <span data-ttu-id="a3210-121">De typen Geef het type gegevens die elke sleutel wordt verwacht.</span><span class="sxs-lookup"><span data-stu-id="a3210-121">The types specify the type of data each key expects.</span></span>

> [!NOTE]
> <span data-ttu-id="a3210-122">De **Zorg ervoor dat** sleutel is optioneel, omdat deze standaard ingesteld op 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="a3210-122">The **Ensure** key is optional because it defaults to "Present".</span></span>

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

<span data-ttu-id="a3210-123">In een configuratie met een **Service** resource blok kan er als volgt aan **Zorg ervoor dat** die de Spooler-service wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a3210-123">Inside a Configuration, a **Service** resource block might look like this to **Ensure** that the Spooler service is running.</span></span>

> [!NOTE]
> <span data-ttu-id="a3210-124">Voordat u een resource in een configuratie gebruikt, moet u importeren met behulp van [sleutelwoorden Import-dscresource bieden](../configurations/import-dscresource.md).</span><span class="sxs-lookup"><span data-stu-id="a3210-124">Before using a resource in a Configuration, you must import it using [Import-DSCResource](../configurations/import-dscresource.md).</span></span>

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

<span data-ttu-id="a3210-125">Configuraties kunnen meerdere exemplaren van hetzelfde resourcetype bevatten.</span><span class="sxs-lookup"><span data-stu-id="a3210-125">Configurations can contain multiple instances of the same resource type.</span></span> <span data-ttu-id="a3210-126">Elk exemplaar moet een unieke naam hebben.</span><span class="sxs-lookup"><span data-stu-id="a3210-126">Each instance must be uniquely named.</span></span> <span data-ttu-id="a3210-127">In het volgende voorbeeld wordt een tweede **Service** resource blok wordt toegevoegd aan de 'DHCP'-service configureren.</span><span class="sxs-lookup"><span data-stu-id="a3210-127">In the following example, a second **Service** resource block is added to configure the "DHCP" service.</span></span>

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
> <span data-ttu-id="a3210-128">Begin in PowerShell 5.0, is intellisense toegevoegd voor DSC.</span><span class="sxs-lookup"><span data-stu-id="a3210-128">Beginning in PowerShell 5.0, intellisense was added for DSC.</span></span> <span data-ttu-id="a3210-129">Deze nieuwe functie kunt u gebruikmaken van \<tabblad\> en \<Ctrl + spatie\> naar sleutelnamen automatisch aanvullen.</span><span class="sxs-lookup"><span data-stu-id="a3210-129">This new feature allows you to use \<TAB\> and \<Ctrl+Space\> to auto-complete key names.</span></span>

![Tab-aanvulling van resource](../media/resource-tabcompletion.png)
