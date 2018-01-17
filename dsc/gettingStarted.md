---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Aan de slag met PowerShell Desired State Configuration
ms.openlocfilehash: 856528f1e52eafa8b2c93b825a60376a0d64cab2
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="getting-started-with-powershell-desired-state-configuration"></a><span data-ttu-id="2c3a0-103">Aan de slag met PowerShell Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="2c3a0-103">Getting Started with PowerShell Desired State Configuration</span></span> #

<span data-ttu-id="2c3a0-104">Deze handleiding wordt beschreven hoe u begint met het maken van PowerShell Desired State Configuration documenten en toegepast op computers.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-104">This guide describes how to begin creating PowerShell Desired State Configuration documents and apply them to machines.</span></span> <span data-ttu-id="2c3a0-105">Er wordt vanuit gegaan enigszins bekend bent met PowerShell-cmdlets, modules en -functies.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-105">It assumes basic familiarity with PowerShell cmdlets, modules, and functions.</span></span> 


## <a name="create-a-configuration"></a><span data-ttu-id="2c3a0-106">Een configuratie maken</span><span class="sxs-lookup"><span data-stu-id="2c3a0-106">Create a Configuration</span></span> ##

<span data-ttu-id="2c3a0-107">[**Configuraties** ](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) zijn documenten die worden beschreven van een omgeving.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-107">[**Configurations**](https://msdn.microsoft.com/en-us/powershell/dsc/configurations) are documents that describe an environment.</span></span> <span data-ttu-id="2c3a0-108">Omgevingen bestaan uit '**knooppunten**', die meestal worden virtuele of fysieke machines.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-108">Environments consist of "**nodes**", which are commonly virtual or physical machines.</span></span> 

<span data-ttu-id="2c3a0-109">Configuraties kunnen worden geleverd in verschillende vormen.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-109">Configurations can come in a variety of forms.</span></span> <span data-ttu-id="2c3a0-110">De eenvoudigste manier om te maken van een nieuwe configuratie is een ps1-bestand (PowerShell-script) te maken.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-110">The easiest way to create a new configuration is to create a .ps1 (PowerShell script) file.</span></span> <span data-ttu-id="2c3a0-111">U doet dit door uw keuze-editor te openen.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-111">To do this, open your editor of choice.</span></span> <span data-ttu-id="2c3a0-112">De PowerShell ISE is een goede keuze, omdat deze DSC systeemeigen begrijpt.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-112">The PowerShell ISE is a good choice, since it understands DSC natively.</span></span> <span data-ttu-id="2c3a0-113">De volgende opslaan als een PS1:</span><span class="sxs-lookup"><span data-stu-id="2c3a0-113">Save the following as a PS1:</span></span>

```powershell
configuration MyFirstConfiguration
{
    Import-DscResource -Name WindowsFeature

    Node localhost
    {
        WindowsFeature IIS
        {
            Name = "IIS"

        }
        
    }

}
```
## <a name="parts-of-a-configuration"></a><span data-ttu-id="2c3a0-114">Onderdelen van een configuratie</span><span class="sxs-lookup"><span data-stu-id="2c3a0-114">Parts of a Configuration</span></span> ##
<span data-ttu-id="2c3a0-115">**Configuratie** is een sleutelwoord die is toegevoegd aan PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-115">**Configuration** is a keyword that has been added to PowerShell 4.0.</span></span> <span data-ttu-id="2c3a0-116">Dit geeft aan dat een speciaal type van de PowerShell-functie die wordt gebruikt door Desired State Configuration.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-116">It signifies a special kind of PowerShell function used by Desired State Configuration.</span></span> <span data-ttu-id="2c3a0-117">In dit voorbeeld is de functie myFirstConfiguration naam.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-117">In this example, the function is named myFirstConfiguration.</span></span> 

<span data-ttu-id="2c3a0-118">De volgende regel wordt een importinstructie, vergelijkbaar met het importeren van een module.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-118">The next line is an import statement, similar to importing a module.</span></span> <span data-ttu-id="2c3a0-119">Dit zal later worden besproken.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-119">It will be discussed later on.</span></span>

<span data-ttu-id="2c3a0-120">'Knooppunt' definieert de naam van de machine die deze configuratie wordt toegepast.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-120">"Node" defines the machine name this configuration will act on.</span></span> <span data-ttu-id="2c3a0-121">Hoewel deze configuratie lokaal bewerkt wordt, kunnen configuraties externe knooppunten bereiken en configureren.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-121">Although this configuration is edited locally, configurations can reach out to remote nodes and configure them.</span></span> 

<span data-ttu-id="2c3a0-122">Knooppunten kunnen namen voor machines of IP-adressen zijn.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-122">Nodes can be machine names or IP addresses.</span></span> <span data-ttu-id="2c3a0-123">U kunt meerdere knooppunten in een configuratie voor één document hebben.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-123">You can have multiple nodes in a single configuration document.</span></span> <span data-ttu-id="2c3a0-124">Met behulp van [configuratiegegevens](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), u kunt ook van toepassing op meerdere knooppunten dezelfde configuratie hebben.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-124">Using [configuration data](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), you can also have the same configuration apply to multiple nodes.</span></span> <span data-ttu-id="2c3a0-125">Het knooppunt is in dit geval 'localhost' - wat betekent de lokale computer dat.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-125">In this case, the node is "localhost" - which means the local computer.</span></span> 

<span data-ttu-id="2c3a0-126">Het volgende item is een [ **resource**](https://msdn.microsoft.com/en-us/powershell/dsc/resources).</span><span class="sxs-lookup"><span data-stu-id="2c3a0-126">The next item is a [**resource**](https://msdn.microsoft.com/en-us/powershell/dsc/resources).</span></span> <span data-ttu-id="2c3a0-127">Resources zijn de bouwstenen van configuraties.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-127">Resources are building blocks of configurations.</span></span> <span data-ttu-id="2c3a0-128">Elke bron is een module die de logica van de implementatie van een enkele aspect van een machine definieert.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-128">Each resource is a module that defines the implementation logic of a single aspect of a machine.</span></span> <span data-ttu-id="2c3a0-129">U kunt elke resource weergeven op uw computer door te voeren **Get-DscResource** in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-129">You can view every resource on your machine by running **Get-DscResource** in PowerShell.</span></span> <span data-ttu-id="2c3a0-130">Resources moet aanwezig zijn op de lokale computer en geïmporteerd voordat ze kunnen worden gebruikt in een configuratie met **importeren DscResource** die zich op de tweede regel met deze configuratie.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-130">Resources must be present on the local machine and imported before they can be used in a configuration with **Import-DscResource** which is on the second line of this configuration.</span></span> 

<span data-ttu-id="2c3a0-131">**Een configuratie vast te stellen**</span><span class="sxs-lookup"><span data-stu-id="2c3a0-131">**Enacting a Configuration**</span></span>

<span data-ttu-id="2c3a0-132">Als het bovenstaande script is opgeslagen en worden uitgevoerd, wordt geen uitvoer geproduceerd.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-132">If the script above is saved and run, no output will be produced.</span></span> <span data-ttu-id="2c3a0-133">Dit is omdat een configuratie alleen een functie is en het bovenstaande script heeft de functie gedefinieerd, maar nog niet uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-133">This is because a configuration is just a function, and the script above has defined the function but not yet run it.</span></span> <span data-ttu-id="2c3a0-134">Nadat de functie is gedefinieerd, moet worden aangeroepen:</span><span class="sxs-lookup"><span data-stu-id="2c3a0-134">After the function is defined, it must be invoked:</span></span>
```powershell
myFirstConfiguration
```

<span data-ttu-id="2c3a0-135">Tijdens de uitvoering van functies van de configuratie van de configuratie valideren is geldig.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-135">When executed, configuration functions validate the configuration is valid.</span></span> <span data-ttu-id="2c3a0-136">Er is geen syntaxisfouten, resources moet alle verplichte parameters gedefinieerd en alle resources moeten worden geïmporteerd voordat wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-136">It should have no syntax errors, resources should have all mandatory parameters defined, and all resources should be imported before execution.</span></span>

<span data-ttu-id="2c3a0-137">Zodra de configuratie wordt uitgevoerd, wordt een map gemaakt met de naam van de configuratie die een **. MOF-bestand** voor elk knooppunt in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-137">Once the configuration is executed, it creates a folder with the name of the configuration containing a **.MOF file** for every node in the configuration.</span></span> <span data-ttu-id="2c3a0-138">De. MOF-bestand is een op standaarden gebaseerde management-indeling die wordt gebruikt door PowerShell DSC om te communiceren via het netwerk.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-138">The .MOF file is a standards-based management format which is used by PowerShell DSC to communicate over the network.</span></span>

<span data-ttu-id="2c3a0-139">Op te nemen in de configuratie:</span><span class="sxs-lookup"><span data-stu-id="2c3a0-139">To enact the configuration:</span></span>
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration
```
<span data-ttu-id="2c3a0-140">Hiermee maakt u een PowerShell-taak die gezocht naar de knooppunten in de configuratie en configureert u deze.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-140">This creates a PowerShell job that reaches out to the nodes in the configuration and configures them.</span></span> <span data-ttu-id="2c3a0-141">Als de uitvoer van de taak wilt weergeven, gebruikt - wachttijd.</span><span class="sxs-lookup"><span data-stu-id="2c3a0-141">To see the output of the job, use -Wait.</span></span> 
```powershell
Start-DscConfiguration -Path ./myFirstConfiguration -Wait
```

