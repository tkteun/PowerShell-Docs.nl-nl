---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-configuraties
ms.openlocfilehash: eeee18e6a4bd09cc22d1ac4ed5cbfaea02346170
ms.sourcegitcommit: 60f06a06c2fce63024f3f4cbd7657b1dfe7fcb1a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/03/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="f6270-103">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="f6270-103">DSC Configurations</span></span>

><span data-ttu-id="f6270-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f6270-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f6270-105">DSC-configuraties zijn PowerShell-scripts die een speciaal type van de functie definiëren.</span><span class="sxs-lookup"><span data-stu-id="f6270-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span> <span data-ttu-id="f6270-106">Als u een configuratie definieert, u het sleutelwoord PowerShell **configuratie**.</span><span class="sxs-lookup"><span data-stu-id="f6270-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="f6270-107">Sla het script als een ps1-bestand.</span><span class="sxs-lookup"><span data-stu-id="f6270-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="f6270-108">De syntaxis van de configuratie</span><span class="sxs-lookup"><span data-stu-id="f6270-108">Configuration syntax</span></span>

<span data-ttu-id="f6270-109">Een configuratiescript bestaat uit de volgende onderdelen:</span><span class="sxs-lookup"><span data-stu-id="f6270-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="f6270-110">De **configuratie** blok.</span><span class="sxs-lookup"><span data-stu-id="f6270-110">The **Configuration** block.</span></span> <span data-ttu-id="f6270-111">Dit is het buitenste scriptblok.</span><span class="sxs-lookup"><span data-stu-id="f6270-111">This is the outermost script block.</span></span> <span data-ttu-id="f6270-112">U de gegevens definiëren met behulp van de **configuratie** sleutelwoord en een naam geven.</span><span class="sxs-lookup"><span data-stu-id="f6270-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="f6270-113">In dit geval is de naam van de configuratie 'MyDscConfiguration'.</span><span class="sxs-lookup"><span data-stu-id="f6270-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="f6270-114">Een of meer **knooppunt** blokken.</span><span class="sxs-lookup"><span data-stu-id="f6270-114">One or more **Node** blocks.</span></span> <span data-ttu-id="f6270-115">Dit definieert de knooppunten (computers of virtuele machines) die u configureert.</span><span class="sxs-lookup"><span data-stu-id="f6270-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="f6270-116">In de bovenstaande configuratie, er is een **knooppunt** blok die gericht is op een computer met de naam 'TEST-PC1'.</span><span class="sxs-lookup"><span data-stu-id="f6270-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="f6270-117">Een of meer resource-blokken.</span><span class="sxs-lookup"><span data-stu-id="f6270-117">One or more resource blocks.</span></span> <span data-ttu-id="f6270-118">Dit is waar de configuratie stelt u de eigenschappen voor de resources die deze configureert.</span><span class="sxs-lookup"><span data-stu-id="f6270-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="f6270-119">In dit geval zijn er twee resource blokken, die elk de resource 'WindowsFeature' aanroepen.</span><span class="sxs-lookup"><span data-stu-id="f6270-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="f6270-120">Binnen een **configuratie** blok, kunt u alles wat u normaal gesproken in een PowerShell-functie kan doen.</span><span class="sxs-lookup"><span data-stu-id="f6270-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="f6270-121">Bijvoorbeeld in het vorige voorbeeld kan als u niet wilt harde code de naam van de doelcomputer in de configuratie u een parameter toevoegen voor de knooppuntnaam van:</span><span class="sxs-lookup"><span data-stu-id="f6270-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="f6270-122">In dit voorbeeld wordt u de naam van het knooppunt door door te geven als de **ComputerName** parameter door bij het compileren van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f6270-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="f6270-123">De naam van de standaard 'localhost'.</span><span class="sxs-lookup"><span data-stu-id="f6270-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="f6270-124">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="f6270-124">Compiling the configuration</span></span>

<span data-ttu-id="f6270-125">Voordat u een configuratie op te nemen kunt, die u moet deze worden gecompileerd tot een MOF-document.</span><span class="sxs-lookup"><span data-stu-id="f6270-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span> <span data-ttu-id="f6270-126">U doen dit door het aanroepen van de configuratie, net als een PowerShell-functie.</span><span class="sxs-lookup"><span data-stu-id="f6270-126">You do this by calling the configuration like you would a PowerShell function.</span></span>  
<span data-ttu-id="f6270-127">De laatste regel van het voorbeeld met alleen de naam van de configuratie, roept de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f6270-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="f6270-128">**Opmerking:** voor het aanroepen van een configuratie met de functie moet in het globale bereik (net als bij een andere PowerShell-functie).</span><span class="sxs-lookup"><span data-stu-id="f6270-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span> 
><span data-ttu-id="f6270-129">U kunt aanbrengen in dit geval ofwel door 'dotsourcing' het script of configuratiescript uit te voeren de met behulp van F5 of klik op de **-Script uitvoeren** knop in de ISE.</span><span class="sxs-lookup"><span data-stu-id="f6270-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span> 
><span data-ttu-id="f6270-130">Het script voor punt-bron, voert u de opdracht `. .\myConfig.ps1` waar `myConfig.ps1` is de naam van het scriptbestand dat uw configuratie bevat.</span><span class="sxs-lookup"><span data-stu-id="f6270-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="f6270-131">Bij het aanroepen van de configuratie het:</span><span class="sxs-lookup"><span data-stu-id="f6270-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="f6270-132">Alle variabelen wordt opgelost</span><span class="sxs-lookup"><span data-stu-id="f6270-132">Resolves all variables</span></span> 
- <span data-ttu-id="f6270-133">Maakt een map in de huidige map met dezelfde naam als de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f6270-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="f6270-134">Maakt een bestand met de naam _NodeName_MOF in de nieuwe map waar _NodeName_ is de naam van het doelknooppunt van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f6270-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span> 
    <span data-ttu-id="f6270-135">Als er meer dan één knooppunten, wordt een MOF-bestand gemaakt voor elk knooppunt.</span><span class="sxs-lookup"><span data-stu-id="f6270-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="f6270-136">**Opmerking**: het MOF-bestand bevat alle van de configuratiegegevens voor het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="f6270-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="f6270-137">Als gevolg hiervan is het belangrijk beveiligd blijft.</span><span class="sxs-lookup"><span data-stu-id="f6270-137">Because of this, it’s important to keep it secure.</span></span> 
><span data-ttu-id="f6270-138">Zie voor meer informatie [beveiligen van het MOF-bestand](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="f6270-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="f6270-139">Compileren van de eerste configuratie boven resultaten in de volgende mapstructuur:</span><span class="sxs-lookup"><span data-stu-id="f6270-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="f6270-140">Als de configuratie een parameter, zoals in het tweede voorbeeld moet heeft die worden opgegeven tijdens de compilatie.</span><span class="sxs-lookup"><span data-stu-id="f6270-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="f6270-141">Ga als volgt die zou als volgt uitzien:</span><span class="sxs-lookup"><span data-stu-id="f6270-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="f6270-142">Met behulp van DependsOn</span><span class="sxs-lookup"><span data-stu-id="f6270-142">Using DependsOn</span></span>

<span data-ttu-id="f6270-143">Is een nuttig DSC-sleutelwoord **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="f6270-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="f6270-144">Normaal (maar niet noodzakelijkerwijs altijd), DSC van de resources in de volgorde waarin ze worden weergegeven in de configuratie van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="f6270-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span> <span data-ttu-id="f6270-145">Echter, **DependsOn** geeft aan welk resources afhankelijk zijn van andere bronnen en de LCM zorgt ervoor dat ze worden toegepast in de juiste volgorde, ongeacht de volgorde in welke resource exemplaren worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="f6270-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span> <span data-ttu-id="f6270-146">Bijvoorbeeld: een configuratie opgeven die een exemplaar van de **gebruiker** bron is afhankelijk van de aanwezigheid van een **groep** exemplaar:</span><span class="sxs-lookup"><span data-stu-id="f6270-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="f6270-147">Met behulp van nieuwe resources in uw configuratie</span><span class="sxs-lookup"><span data-stu-id="f6270-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="f6270-148">Als u de eerdere voorbeelden hebt uitgevoerd, u mogelijk opgevallen dat zijn u gewaarschuwd dat u een resource zijn gebruiken zonder expliciet importeren.</span><span class="sxs-lookup"><span data-stu-id="f6270-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="f6270-149">Vandaag de dag DSC wordt geleverd met 12 resources als onderdeel van de module PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="f6270-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span> <span data-ttu-id="f6270-150">Andere bronnen in externe modules moeten worden geplaatst in `$env:PSModulePath` om te kunnen worden herkend door de LCM.</span><span class="sxs-lookup"><span data-stu-id="f6270-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span> <span data-ttu-id="f6270-151">Een nieuwe cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), kunnen worden gebruikt om te bepalen welke bronnen worden geïnstalleerd op het systeem en zijn beschikbaar voor gebruik door de LCM.</span><span class="sxs-lookup"><span data-stu-id="f6270-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span> <span data-ttu-id="f6270-152">Zodra deze modules zijn geplaatst `$env:PSModulePath` en correct worden herkend door [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), ze nog moeten worden geladen in uw configuratie.</span><span class="sxs-lookup"><span data-stu-id="f6270-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span> 
<span data-ttu-id="f6270-153">**Importeren DscResource** is een dynamische sleutelwoord dat alleen kan worden herkend binnen een **configuratie** blok (dat wil zeggen het is niet een cmdlet).</span><span class="sxs-lookup"><span data-stu-id="f6270-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span> 
<span data-ttu-id="f6270-154">**Importeren DscResource** ondersteunt twee parameters:</span><span class="sxs-lookup"><span data-stu-id="f6270-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="f6270-155">**Modulenaam** is de aanbevolen manier van het gebruik van **importeren DscResource**.</span><span class="sxs-lookup"><span data-stu-id="f6270-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="f6270-156">De naam van de module met de resources die worden geïmporteerd (evenals een string-matrix van modulenamen) worden geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="f6270-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span> 
- <span data-ttu-id="f6270-157">**Naam** is de naam van de resource te importeren.</span><span class="sxs-lookup"><span data-stu-id="f6270-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="f6270-158">Dit is niet de beschrijvende naam die wordt geretourneerd als 'Name' door [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), maar de naam van de klasse die wordt gebruikt wanneer definiëren van de resource-schema (geretourneerd als **ResourceType** door [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="f6270-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx)).</span></span> 

## <a name="see-also"></a><span data-ttu-id="f6270-159">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6270-159">See Also</span></span>
* [<span data-ttu-id="f6270-160">Windows PowerShell Desired State Configuration-overzicht</span><span class="sxs-lookup"><span data-stu-id="f6270-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="f6270-161">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="f6270-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="f6270-162">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="f6270-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

