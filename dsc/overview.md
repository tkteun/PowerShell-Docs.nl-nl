---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Windows PowerShell Desired State Configuration-overzicht
ms.openlocfilehash: 1d6ba0b2fdb514e703ddad11adf4cdace5c001a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="616a9-103">Windows PowerShell Desired State Configuration-overzicht</span><span class="sxs-lookup"><span data-stu-id="616a9-103">Windows PowerShell Desired State Configuration Overview</span></span> 

> <span data-ttu-id="616a9-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="616a9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="616a9-105">DSC is een beheerplatform in PowerShell waarmee u voor het beheren van uw IT-afdeling en ontwikkeling infrastructuur met configuratie als de code.</span><span class="sxs-lookup"><span data-stu-id="616a9-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="616a9-106">Zie voor een overzicht van de zakelijke voordelen van het gebruik van DSC [Desired Configuration overzicht voor besluitvormers](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="616a9-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="616a9-107">Zie voor een overzicht van de technische voordelen van het gebruik van DSC [Desired Configuration overzicht voor Engineers](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="616a9-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="616a9-108">Zie het gebruik van DSC snel starten [DSC snel starten](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="616a9-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="616a9-109">Belangrijkste concepten</span><span class="sxs-lookup"><span data-stu-id="616a9-109">Key Concepts</span></span>

<span data-ttu-id="616a9-110">DSC is een declaratieve platform gebruikt voor de configuratie, implementatie en beheer van systemen.</span><span class="sxs-lookup"><span data-stu-id="616a9-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="616a9-111">Deze bestaat uit drie primaire onderdelen:</span><span class="sxs-lookup"><span data-stu-id="616a9-111">It consists of three primary components:</span></span>

- <span data-ttu-id="616a9-112">[Configuraties](configurations.md) zijn declaratieve PowerShell-scripts die definiëren en configureren van exemplaren van resources.</span><span class="sxs-lookup"><span data-stu-id="616a9-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="616a9-113">Bij het uitvoeren van de configuratie, DSC (en de resources die wordt aangeroepen door de configuratie) wordt gewoon 'zodat het geval', ervoor zorgen dat het systeem in de status van de lay bestaat-out van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="616a9-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span> 
    <span data-ttu-id="616a9-114">DSC-configuraties zijn ook idempotent: de lokale Configuration Manager (LCM) blijven om ervoor te zorgen dat machines zijn geconfigureerd in de gewenste status van de configuratie wordt gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="616a9-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="616a9-115">[Resources](resources.md) de 'kunt u dus' deel uitmaken van DSC.</span><span class="sxs-lookup"><span data-stu-id="616a9-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="616a9-116">Ze bevatten de code die geplaatst en het doel van een configuratie in de opgegeven status houden.</span><span class="sxs-lookup"><span data-stu-id="616a9-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span> 
    <span data-ttu-id="616a9-117">Bronnen bevinden zich in de PowerShell-modules en kunnen worden geschreven als model voor iets als algemeen als een bestand of een Windows-proces is, of zo specifiek een IIS-server of een virtuele machine in Azure wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="616a9-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="616a9-118">De [lokale Configuration Manager (LCM)](metaConfig.md) is de engine waarmee DSC de interactie tussen resources en configuraties vereenvoudigt.</span><span class="sxs-lookup"><span data-stu-id="616a9-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span> 
    <span data-ttu-id="616a9-119">De LCM controleert regelmatig of het systeem met de Controlestroom geïmplementeerd door resources om ervoor te zorgen dat de status is gedefinieerd door een configuratie behouden blijft.</span><span class="sxs-lookup"><span data-stu-id="616a9-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span> 
    <span data-ttu-id="616a9-120">Als het systeem onvoldoende status heeft, maakt de LCM aanroepen naar de code in resources zodat ' dit ' volgens de configuratie.</span><span class="sxs-lookup"><span data-stu-id="616a9-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span> 

## <a name="see-also"></a><span data-ttu-id="616a9-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="616a9-121">See Also</span></span>

- [<span data-ttu-id="616a9-122">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="616a9-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="616a9-123">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="616a9-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="616a9-124">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="616a9-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

