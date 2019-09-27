---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: DSC-configuraties
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323256"
---
# <a name="dsc-configurations"></a><span data-ttu-id="b0684-103">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="b0684-103">DSC Configurations</span></span>

> <span data-ttu-id="b0684-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="b0684-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b0684-105">DSC-configuraties zijn Power shell-scripts waarmee een speciaal type functie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b0684-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="b0684-106">Voor het definiëren van een configuratie gebruikt u de **configuratie**van het Power shell-tref woord.</span><span class="sxs-lookup"><span data-stu-id="b0684-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

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

<span data-ttu-id="b0684-107">Sla het script op als `.ps1` een bestand.</span><span class="sxs-lookup"><span data-stu-id="b0684-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="b0684-108">Configuratie syntaxis</span><span class="sxs-lookup"><span data-stu-id="b0684-108">Configuration syntax</span></span>

<span data-ttu-id="b0684-109">Een configuratie script bestaat uit de volgende onderdelen:</span><span class="sxs-lookup"><span data-stu-id="b0684-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="b0684-110">Het **configuratie** blok.</span><span class="sxs-lookup"><span data-stu-id="b0684-110">The **Configuration** block.</span></span> <span data-ttu-id="b0684-111">Dit is het buitenste script blok.</span><span class="sxs-lookup"><span data-stu-id="b0684-111">This is the outermost script block.</span></span> <span data-ttu-id="b0684-112">U definieert deze met behulp van het sleutel woord **Configuration** en geeft een naam op.</span><span class="sxs-lookup"><span data-stu-id="b0684-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="b0684-113">In dit geval is de naam van de configuratie ' MyDscConfiguration '.</span><span class="sxs-lookup"><span data-stu-id="b0684-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="b0684-114">Een of meer **knooppunt** blokken.</span><span class="sxs-lookup"><span data-stu-id="b0684-114">One or more **Node** blocks.</span></span> <span data-ttu-id="b0684-115">Hier worden de knoop punten (computers of Vm's) gedefinieerd die u configureert.</span><span class="sxs-lookup"><span data-stu-id="b0684-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="b0684-116">In de bovenstaande configuratie bevindt zich één **knooppunt** blok dat gericht is op een computer met de naam ' test-PC1 '.</span><span class="sxs-lookup"><span data-stu-id="b0684-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="b0684-117">Het knooppunt blok kan meerdere computer namen accepteren.</span><span class="sxs-lookup"><span data-stu-id="b0684-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="b0684-118">Een of meer resource blokken.</span><span class="sxs-lookup"><span data-stu-id="b0684-118">One or more resource blocks.</span></span> <span data-ttu-id="b0684-119">Hier stelt de configuratie de eigenschappen in voor de resources die worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="b0684-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="b0684-120">In dit geval zijn er twee resource blokken, die elk de resource ' WindowsFeature ' aanroepen.</span><span class="sxs-lookup"><span data-stu-id="b0684-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="b0684-121">Binnen een **configuratie** blok kunt u alles doen wat u normaal gesp roken in een Power shell-functie zou kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b0684-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="b0684-122">Als u bijvoorbeeld in het vorige voor beeld niet de naam van de doel computer in de configuratie wilt coderen, kunt u een para meter voor de knooppunt naam toevoegen:</span><span class="sxs-lookup"><span data-stu-id="b0684-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="b0684-123">In dit voor beeld geeft u de naam van het knoop punt op door dit door te geven als de para meter **ComputerName** wanneer u de configuratie compileert.</span><span class="sxs-lookup"><span data-stu-id="b0684-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="b0684-124">De naam wordt standaard ingesteld op localhost.</span><span class="sxs-lookup"><span data-stu-id="b0684-124">The name defaults to "localhost".</span></span>

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

<span data-ttu-id="b0684-125">Het **knooppunt** blok kan ook meerdere computer namen accepteren.</span><span class="sxs-lookup"><span data-stu-id="b0684-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="b0684-126">In het bovenstaande voor beeld kunt u de `-ComputerName` para meter gebruiken of een door komma's gescheiden lijst met computers rechtstreeks aan het **knooppunt** blok door geven.</span><span class="sxs-lookup"><span data-stu-id="b0684-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="b0684-127">Wanneer u een lijst met computers voor het **knooppunt** blok opgeeft, moet u in een configuratie matrix-Notation gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b0684-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

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

## <a name="compiling-the-configuration"></a><span data-ttu-id="b0684-128">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="b0684-128">Compiling the configuration</span></span>

<span data-ttu-id="b0684-129">Voordat u een configuratie kunt vastleggen, moet u deze compileren in een MOF-document.</span><span class="sxs-lookup"><span data-stu-id="b0684-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="b0684-130">U doet dit door de configuratie aan te roepen, net zoals u een Power shell-functie zou aanroepen.</span><span class="sxs-lookup"><span data-stu-id="b0684-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="b0684-131">De laatste regel van het voor beeld met alleen de naam van de configuratie roept de configuratie aan.</span><span class="sxs-lookup"><span data-stu-id="b0684-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="b0684-132">Voor het aanroepen van een configuratie moet de functie zich in een globaal bereik bevinden (net als bij een andere Power shell-functie).</span><span class="sxs-lookup"><span data-stu-id="b0684-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="b0684-133">U kunt dit doen door het script of door het-configuratie script uit te voeren met F5 of door te klikken op de knop **script uitvoeren** in het ISE.</span><span class="sxs-lookup"><span data-stu-id="b0684-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="b0684-134">Als u het script wilt punt, voert u de `. .\myConfig.ps1` opdracht `myConfig.ps1` uit, waarbij de naam is van het script bestand dat uw configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="b0684-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="b0684-135">Wanneer u de configuratie aanroept, doet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="b0684-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="b0684-136">Hiermee worden alle variabelen omgezet</span><span class="sxs-lookup"><span data-stu-id="b0684-136">Resolves all variables</span></span>
- <span data-ttu-id="b0684-137">Hiermee maakt u een map in de huidige map met dezelfde naam als de configuratie.</span><span class="sxs-lookup"><span data-stu-id="b0684-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="b0684-138">Hiermee maakt u een bestand met de naam ' _nodenaam_. mof ' in de nieuwe map, waarbij _knooppuntnaam_ de naam is van het doel knooppunt van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="b0684-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="b0684-139">Als er meer dan één knoop punt is, wordt voor elk knoop punt een MOF-bestand gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b0684-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="b0684-140">Het MOF-bestand bevat alle configuratie-informatie voor het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="b0684-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="b0684-141">Daarom is het belang rijk dat u deze veilig blijft beveiligen.</span><span class="sxs-lookup"><span data-stu-id="b0684-141">Because of this, it's important to keep it secure.</span></span>
> <span data-ttu-id="b0684-142">Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0684-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="b0684-143">Het compileren van de eerste configuratie hierboven resulteert in de volgende mapstructuur:</span><span class="sxs-lookup"><span data-stu-id="b0684-143">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="b0684-144">Als voor de configuratie een para meter wordt gebruikt, zoals in het tweede voor beeld, die tijdens het compileren moet worden gegeven.</span><span class="sxs-lookup"><span data-stu-id="b0684-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="b0684-145">Dit ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="b0684-145">Here's how that would look:</span></span>

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

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="b0684-146">Nieuwe resources in uw configuratie gebruiken</span><span class="sxs-lookup"><span data-stu-id="b0684-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="b0684-147">Als u de voor gaande voor beelden hebt uitgevoerd, bent u mogelijk opgevallen dat u een resource hebt gebruikt zonder deze expliciet te importeren.</span><span class="sxs-lookup"><span data-stu-id="b0684-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="b0684-148">In de PSDesiredStateConfiguration-module van DSC worden er nu 12 resources geleverd.</span><span class="sxs-lookup"><span data-stu-id="b0684-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="b0684-149">De cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), kan worden gebruikt om te bepalen welke resources op het systeem zijn geïnstalleerd en beschikbaar zijn voor gebruik door de LCM.</span><span class="sxs-lookup"><span data-stu-id="b0684-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="b0684-150">Zodra deze modules zijn geplaatst `$env:PSModulePath` en op de juiste wijze worden herkend door [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), moeten ze nog steeds worden geladen in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="b0684-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="b0684-151">**Import-dscresource bieden** is een dynamisch tref woord dat alleen kan worden herkend binnen een **configuratie** blok en dat het geen cmdlet is.</span><span class="sxs-lookup"><span data-stu-id="b0684-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="b0684-152">**Import-dscresource bieden** ondersteunt twee para meters:</span><span class="sxs-lookup"><span data-stu-id="b0684-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="b0684-153">**Module** naam is de aanbevolen methode voor het gebruik van **import-dscresource bieden**.</span><span class="sxs-lookup"><span data-stu-id="b0684-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="b0684-154">De naam van de module die de resources bevat die moeten worden geïmporteerd (en een teken reeks matrix van module namen), wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="b0684-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="b0684-155">**Naam** is de naam van de resource die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="b0684-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="b0684-156">Dit is niet de beschrijvende naam die wordt geretourneerd als ' name ' door [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), maar de naam van de klasse die wordt gebruikt bij het definiëren van het resource schema (geretourneerd als **resource type** op [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="b0684-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="b0684-157">Zie `Import-DSCResource` [using import-dscresource bieden](import-dscresource.md) voor meer informatie over het gebruik van.</span><span class="sxs-lookup"><span data-stu-id="b0684-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="b0684-158">Verschillen Power shell v4 en V5</span><span class="sxs-lookup"><span data-stu-id="b0684-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="b0684-159">Er zijn verschillen in waar DSC-resources moeten worden opgeslagen in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="b0684-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="b0684-160">Zie [Resource Location](import-dscresource.md#resource-location)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b0684-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0684-161">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b0684-161">See Also</span></span>

- [<span data-ttu-id="b0684-162">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="b0684-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="b0684-163">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="b0684-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="b0684-164">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="b0684-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
