---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: DSC-configuraties
description: DSC-configuraties zijn Power shell-scripts waarmee een speciaal type functie wordt gedefinieerd.
ms.openlocfilehash: e59ad2791055ee3ff0150c342ec621d0228c4fc1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658561"
---
# <a name="dsc-configurations"></a><span data-ttu-id="55245-104">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="55245-104">DSC Configurations</span></span>

> <span data-ttu-id="55245-105">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="55245-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="55245-106">DSC-configuraties zijn Power shell-scripts waarmee een speciaal type functie wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="55245-106">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="55245-107">Voor het definiëren van een configuratie gebruikt u de **configuratie** van het Power shell-tref woord.</span><span class="sxs-lookup"><span data-stu-id="55245-107">To define a configuration, you use the PowerShell keyword **Configuration** .</span></span>

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

<span data-ttu-id="55245-108">Sla het script op als een `.ps1` bestand.</span><span class="sxs-lookup"><span data-stu-id="55245-108">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="55245-109">Configuratiesyntaxis</span><span class="sxs-lookup"><span data-stu-id="55245-109">Configuration syntax</span></span>

<span data-ttu-id="55245-110">Een configuratie script bestaat uit de volgende onderdelen:</span><span class="sxs-lookup"><span data-stu-id="55245-110">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="55245-111">Het **configuratie** blok.</span><span class="sxs-lookup"><span data-stu-id="55245-111">The **Configuration** block.</span></span> <span data-ttu-id="55245-112">Dit is het buitenste script blok.</span><span class="sxs-lookup"><span data-stu-id="55245-112">This is the outermost script block.</span></span> <span data-ttu-id="55245-113">U definieert deze met behulp van het sleutel woord **Configuration** en geeft een naam op.</span><span class="sxs-lookup"><span data-stu-id="55245-113">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="55245-114">In dit geval is de naam van de configuratie ' MyDscConfiguration '.</span><span class="sxs-lookup"><span data-stu-id="55245-114">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="55245-115">Een of meer **knooppunt** blokken.</span><span class="sxs-lookup"><span data-stu-id="55245-115">One or more **Node** blocks.</span></span> <span data-ttu-id="55245-116">Hier worden de knoop punten (computers of Vm's) gedefinieerd die u configureert.</span><span class="sxs-lookup"><span data-stu-id="55245-116">These define the nodes (computers or VMs) that you are configuring.</span></span>
  <span data-ttu-id="55245-117">In de bovenstaande configuratie bevindt zich één **knooppunt** blok dat gericht is op een computer met de naam ' test-PC1 '.</span><span class="sxs-lookup"><span data-stu-id="55245-117">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
  <span data-ttu-id="55245-118">Het knooppunt blok kan meerdere computer namen accepteren.</span><span class="sxs-lookup"><span data-stu-id="55245-118">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="55245-119">Een of meer resource blokken.</span><span class="sxs-lookup"><span data-stu-id="55245-119">One or more resource blocks.</span></span> <span data-ttu-id="55245-120">Hier stelt de configuratie de eigenschappen in voor de resources die worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="55245-120">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="55245-121">In dit geval zijn er twee resource blokken, die elk de resource ' WindowsFeature ' aanroepen.</span><span class="sxs-lookup"><span data-stu-id="55245-121">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="55245-122">Binnen een **configuratie** blok kunt u alles doen wat u normaal gesp roken in een Power shell-functie zou kunnen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="55245-122">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="55245-123">Als u bijvoorbeeld in het vorige voor beeld niet de naam van de doel computer in de configuratie wilt coderen, kunt u een para meter voor de knooppunt naam toevoegen:</span><span class="sxs-lookup"><span data-stu-id="55245-123">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="55245-124">In dit voor beeld geeft u de naam van het knoop punt op door dit door te geven als de para meter **ComputerName** wanneer u de configuratie compileert.</span><span class="sxs-lookup"><span data-stu-id="55245-124">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="55245-125">De naam wordt standaard ingesteld op localhost.</span><span class="sxs-lookup"><span data-stu-id="55245-125">The name defaults to "localhost".</span></span>

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

<span data-ttu-id="55245-126">Het **knooppunt** blok kan ook meerdere computer namen accepteren.</span><span class="sxs-lookup"><span data-stu-id="55245-126">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="55245-127">In het bovenstaande voor beeld kunt u de `-ComputerName` para meter gebruiken of een door komma's gescheiden lijst met computers rechtstreeks aan het **knooppunt** blok door geven.</span><span class="sxs-lookup"><span data-stu-id="55245-127">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="55245-128">Wanneer u een lijst met computers voor het **knooppunt** blok opgeeft, moet u in een configuratie matrix-Notation gebruiken.</span><span class="sxs-lookup"><span data-stu-id="55245-128">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

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

## <a name="compiling-the-configuration"></a><span data-ttu-id="55245-129">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="55245-129">Compiling the configuration</span></span>

<span data-ttu-id="55245-130">Voordat u een configuratie kunt vastleggen, moet u deze compileren in een MOF-document.</span><span class="sxs-lookup"><span data-stu-id="55245-130">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="55245-131">U doet dit door de configuratie aan te roepen, net zoals u een Power shell-functie zou aanroepen.</span><span class="sxs-lookup"><span data-stu-id="55245-131">You do this by calling the configuration like you would call a PowerShell function.</span></span> <span data-ttu-id="55245-132">De laatste regel van het voor beeld met alleen de naam van de configuratie roept de configuratie aan.</span><span class="sxs-lookup"><span data-stu-id="55245-132">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="55245-133">Voor het aanroepen van een configuratie moet de functie zich in een globaal bereik bevinden (net als bij een andere Power shell-functie).</span><span class="sxs-lookup"><span data-stu-id="55245-133">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> <span data-ttu-id="55245-134">U kunt dit doen door het script of door het-configuratie script uit te voeren met F5 of door te klikken op de knop **script uitvoeren** in het ISE.</span><span class="sxs-lookup"><span data-stu-id="55245-134">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> <span data-ttu-id="55245-135">Als u het script wilt punt, voert u de opdracht uit, `. .\myConfig.ps1` waarbij de `myConfig.ps1` naam is van het script bestand dat uw configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="55245-135">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="55245-136">Wanneer u de configuratie aanroept, doet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="55245-136">When you call the configuration, it:</span></span>

- <span data-ttu-id="55245-137">Hiermee worden alle variabelen omgezet</span><span class="sxs-lookup"><span data-stu-id="55245-137">Resolves all variables</span></span>
- <span data-ttu-id="55245-138">Hiermee maakt u een map in de huidige map met dezelfde naam als de configuratie.</span><span class="sxs-lookup"><span data-stu-id="55245-138">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="55245-139">Hiermee maakt u een bestand met de naam ' _nodenaam_ . mof ' in de nieuwe map, waarbij _knooppuntnaam_ de naam is van het doel knooppunt van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="55245-139">Creates a file named _NodeName_ .mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> <span data-ttu-id="55245-140">Als er meer dan één knoop punt is, wordt voor elk knoop punt een MOF-bestand gemaakt.</span><span class="sxs-lookup"><span data-stu-id="55245-140">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="55245-141">Het MOF-bestand bevat alle configuratie-informatie voor het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="55245-141">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="55245-142">Daarom is het belang rijk dat u deze veilig blijft beveiligen.</span><span class="sxs-lookup"><span data-stu-id="55245-142">Because of this, it's important to keep it secure.</span></span> <span data-ttu-id="55245-143">Zie [het MOF-bestand beveiligen](../pull-server/secureMOF.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="55245-143">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="55245-144">Het compileren van de eerste configuratie hierboven resulteert in de volgende mapstructuur:</span><span class="sxs-lookup"><span data-stu-id="55245-144">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="55245-145">Als voor de configuratie een para meter wordt gebruikt, zoals in het tweede voor beeld, die tijdens het compileren moet worden gegeven.</span><span class="sxs-lookup"><span data-stu-id="55245-145">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="55245-146">Dit ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="55245-146">Here's how that would look:</span></span>

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

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="55245-147">Nieuwe resources in uw configuratie gebruiken</span><span class="sxs-lookup"><span data-stu-id="55245-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="55245-148">Als u de voor gaande voor beelden hebt uitgevoerd, bent u mogelijk opgevallen dat u een resource hebt gebruikt zonder deze expliciet te importeren.</span><span class="sxs-lookup"><span data-stu-id="55245-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span> <span data-ttu-id="55245-149">In de PSDesiredStateConfiguration-module van DSC worden er nu 12 resources geleverd.</span><span class="sxs-lookup"><span data-stu-id="55245-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="55245-150">De cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), kan worden gebruikt om te bepalen welke resources op het systeem zijn geïnstalleerd en beschikbaar zijn voor gebruik door de LCM.</span><span class="sxs-lookup"><span data-stu-id="55245-150">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="55245-151">Zodra deze modules zijn geplaatst `$env:PSModulePath` en op de juiste wijze worden herkend door [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), moeten ze nog steeds worden geladen in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="55245-151">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="55245-152">**Import-dscresource bieden** is een dynamisch tref woord dat alleen kan worden herkend binnen een **configuratie** blok en dat het geen cmdlet is.</span><span class="sxs-lookup"><span data-stu-id="55245-152">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span> <span data-ttu-id="55245-153">**Import-dscresource bieden** ondersteunt twee para meters:</span><span class="sxs-lookup"><span data-stu-id="55245-153">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="55245-154">**Module** naam is de aanbevolen methode voor het gebruik van **import-dscresource bieden** .</span><span class="sxs-lookup"><span data-stu-id="55245-154">**ModuleName** is the recommended way of using **Import-DscResource** .</span></span> <span data-ttu-id="55245-155">De naam van de module die de resources bevat die moeten worden geïmporteerd (en een teken reeks matrix van module namen), wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="55245-155">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="55245-156">**Naam** is de naam van de resource die u wilt importeren.</span><span class="sxs-lookup"><span data-stu-id="55245-156">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="55245-157">Dit is niet de beschrijvende naam die wordt geretourneerd als ' name ' door [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), maar de naam van de klasse die wordt gebruikt bij het definiëren van het resource schema (geretourneerd als **resource type** op [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="55245-157">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="55245-158">`Import-DSCResource`Zie [using import-dscresource bieden](import-dscresource.md) voor meer informatie over het gebruik van.</span><span class="sxs-lookup"><span data-stu-id="55245-158">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="55245-159">Verschillen Power shell v4 en V5</span><span class="sxs-lookup"><span data-stu-id="55245-159">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="55245-160">Er zijn verschillen in waar DSC-resources moeten worden opgeslagen in Power Shell 4,0.</span><span class="sxs-lookup"><span data-stu-id="55245-160">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="55245-161">Zie [Resource Location](import-dscresource.md#resource-location)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="55245-161">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="55245-162">Zie ook</span><span class="sxs-lookup"><span data-stu-id="55245-162">See Also</span></span>

- [<span data-ttu-id="55245-163">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="55245-163">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="55245-164">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="55245-164">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="55245-165">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="55245-165">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
