---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC-configuraties
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684288"
---
# <a name="dsc-configurations"></a><span data-ttu-id="eb2ee-103">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="eb2ee-103">DSC Configurations</span></span>

> <span data-ttu-id="eb2ee-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="eb2ee-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="eb2ee-105">DSC-configuraties zijn PowerShell-scripts die een speciaal type functie definiëren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="eb2ee-106">Voor het definiëren van een configuratie die u gebruikt het sleutelwoord PowerShell **configuratie**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="eb2ee-107">Sla het script als een `.ps1` bestand.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="eb2ee-108">Syntaxis van de configuratie</span><span class="sxs-lookup"><span data-stu-id="eb2ee-108">Configuration syntax</span></span>

<span data-ttu-id="eb2ee-109">Een configuratiescript bestaat uit de volgende onderdelen:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="eb2ee-110">De **configuratie** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-110">The **Configuration** block.</span></span> <span data-ttu-id="eb2ee-111">Dit is het buitenste scriptblok.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-111">This is the outermost script block.</span></span> <span data-ttu-id="eb2ee-112">U de gegevens definiëren met behulp van de **configuratie** trefwoord en een naam geven.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="eb2ee-113">In dit geval is de naam van de configuratie 'MyDscConfiguration'.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="eb2ee-114">Een of meer **knooppunt** blokken.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-114">One or more **Node** blocks.</span></span> <span data-ttu-id="eb2ee-115">Dit definieert de knooppunten (computers of virtuele machines) die u wilt configureren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="eb2ee-116">In de bovenstaande configuratie, er is een **knooppunt** blokkeren die gericht is op een computer met de naam 'TEST-PC1'.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="eb2ee-117">Het knooppunt blok kan meerdere computernamen accepteren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="eb2ee-118">Een of meer resource-blokken.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-118">One or more resource blocks.</span></span> <span data-ttu-id="eb2ee-119">Dit is waar de eigenschappen voor de resources waarmee deze wordt geconfigureerd in de configuratie wordt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="eb2ee-120">In dit geval zijn er twee blokken van de resource, die elk de resource "WindowsFeature" aanroepen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="eb2ee-121">Binnen een **configuratie** blokkeren, kunt u alles wat u normaal gesproken in een PowerShell-functie kan doen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="eb2ee-122">Bijvoorbeeld, in het vorige voorbeeld, kan als u niet wilt harde code de naam van de doelcomputer in de configuratie u toevoegen een parameter voor de naam van het knooppunt:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="eb2ee-123">In dit voorbeeld, geeft u de naam van het knooppunt door door te geven als de **ComputerName** parameter wanneer u de configuratie compileren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="eb2ee-124">De naam van de standaardwaarde is "localhost".</span><span class="sxs-lookup"><span data-stu-id="eb2ee-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="eb2ee-125">De **knooppunt** blok kunt ook meerdere computernamen accepteren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="eb2ee-126">In het bovenstaande voorbeeld kunt u ofwel de `-ComputerName` parameter of pass een door komma's gescheiden lijst met computers rechtstreeks naar de **knooppunt** blokkeren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="eb2ee-127">Bij het opgeven van een lijst van computers aan de **knooppunt** blok, uit in een configuratie, moet u matrix-notatie gebruiken.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="eb2ee-128">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="eb2ee-128">Compiling the configuration</span></span>

<span data-ttu-id="eb2ee-129">Voordat u kunt een configuratie gerapporteerd, moet u tijdens het compileren in een MOF-document.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="eb2ee-130">U doen dit door het aanroepen van de configuratie, zoals u zou een PowerShell-functie aanroepen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="eb2ee-131">De laatste regel van het voorbeeld met alleen de naam van de configuratie, roept de configuratie.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="eb2ee-132">Voor het aanroepen van een configuratie, moet de functie in het globale bereik (net als bij een andere PowerShell-functie).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="eb2ee-133">Kunt u dit laten gebeuren ofwel door "dotsourcing" het script, of door het uitvoeren van het configuratiescript met F5 of door te klikken op de **-Script uitvoeren** knop in de ISE.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="eb2ee-134">Het script dot-bron, voert u de opdracht `. .\myConfig.ps1` waar `myConfig.ps1` is de naam van het scriptbestand waarmee de configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="eb2ee-135">Bij het aanroepen van de configuratie, het:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="eb2ee-136">Oplossing voor alle variabelen</span><span class="sxs-lookup"><span data-stu-id="eb2ee-136">Resolves all variables</span></span>
- <span data-ttu-id="eb2ee-137">Hiermee maakt een map in de huidige map met dezelfde naam als de configuratie.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="eb2ee-138">Hiermee maakt u een bestand met de naam _knooppuntnaam_.mof in de nieuwe map waar _knooppuntnaam_ is de naam van het doelknooppunt van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="eb2ee-139">Als er meer dan één knooppunt, wordt een MOF-bestand worden gemaakt voor elk knooppunt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="eb2ee-140">Het MOF-bestand bevat alle van de configuratie-informatie voor het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="eb2ee-141">Als gevolg hiervan is het belangrijk om veilig te houden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="eb2ee-142">Zie voor meer informatie, [beveiligen van het MOF-bestand](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="eb2ee-143">Compileren van de eerste configuratie boven resultaten in de volgende mapstructuur:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="eb2ee-144">Als de configuratie heeft een parameter, zoals in het tweede voorbeeld nodig heeft om te worden opgegeven bij het compileren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="eb2ee-145">Hier ziet u dat zou als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="eb2ee-146">Met behulp van nieuwe resources in uw configuratie</span><span class="sxs-lookup"><span data-stu-id="eb2ee-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="eb2ee-147">Als u de vorige voorbeelden hebt uitgevoerd, u mogelijk opgevallen dat u zijn gewaarschuwd dat u een resource zonder expliciet importeren gebruikten.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="eb2ee-148">DSC wordt nu geleverd met 12 resources als onderdeel van de module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="eb2ee-149">De cmdlet [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), kan worden gebruikt om te bepalen welke resources zijn geïnstalleerd op het systeem en beschikbaar zijn voor gebruik door de LCM.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="eb2ee-150">Zodra deze modules zijn geplaatst `$env:PSModulePath` en goed worden herkend door [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ze nog steeds nodig om te worden geladen in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="eb2ee-151">**Sleutelwoorden import-dscresource bieden** is een dynamische trefwoord dat alleen kan worden herkend binnen een **configuratie** blok, het is niet een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="eb2ee-152">**Sleutelwoorden import-dscresource bieden** ondersteunt twee parameters:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="eb2ee-153">**ModuleName** is de aanbevolen manier voor het gebruik van **sleutelwoorden Import-dscresource bieden**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="eb2ee-154">De naam van de module met de resources die worden geïmporteerd (evenals een string-matrix van modulenamen) worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="eb2ee-155">**Naam** is de naam van de resource te importeren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="eb2ee-156">Dit is niet de beschrijvende naam die wordt geretourneerd als "Naam" door [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), maar de naam van de klasse die wordt gebruikt wanneer de resource-schema definiëren (geretourneerd als **ResourceType** door [Get-sleutelwoorden dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="eb2ee-157">Voor meer informatie over het gebruik van `Import-DSCResource`, Zie [met behulp van importeren sleutelwoorden-dscresource bieden](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="eb2ee-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="eb2ee-158">Verschillen in PowerShell v4 en versie 5</span><span class="sxs-lookup"><span data-stu-id="eb2ee-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="eb2ee-159">Er zijn verschillen in waar DSC-resources moeten worden opgeslagen in PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="eb2ee-160">Zie voor meer informatie, [Resourcelocatie](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb2ee-161">Zie ook</span><span class="sxs-lookup"><span data-stu-id="eb2ee-161">See Also</span></span>

- [<span data-ttu-id="eb2ee-162">Windows PowerShell Desired State Configuration-overzicht</span><span class="sxs-lookup"><span data-stu-id="eb2ee-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="eb2ee-163">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="eb2ee-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="eb2ee-164">De Local Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="eb2ee-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
