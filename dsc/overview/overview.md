---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Windows PowerShell Desired State Configuration-overzicht
ms.openlocfilehash: 3e4f0afa17ab60bfa98f1b86b9830462a7c8e1cf
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404390"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="f24d5-103">Windows PowerShell Desired State Configuration-overzicht</span><span class="sxs-lookup"><span data-stu-id="f24d5-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="f24d5-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f24d5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f24d5-105">DSC is een beheerplatform in PowerShell waarmee u voor het beheren van uw IT-afdeling en infrastructuur voor ontwikkeling met configuratie als code.</span><span class="sxs-lookup"><span data-stu-id="f24d5-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="f24d5-106">Zie voor een overzicht van de zakelijke voordelen van het gebruik van DSC, [overzicht van Desired State Configuration voor besluitvormers](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="f24d5-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="f24d5-107">Zie voor een overzicht van de technische voordelen van het gebruik van DSC [overzicht van Desired State Configuration voor technici](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="f24d5-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="f24d5-108">Als u wilt gaan met behulp van DSC snel, Zie [snel starten met DSC](../quickstarts/website-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="f24d5-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="f24d5-109">Belangrijkste concepten</span><span class="sxs-lookup"><span data-stu-id="f24d5-109">Key Concepts</span></span>

<span data-ttu-id="f24d5-110">DSC is een declaratieve platform dat wordt gebruikt voor configuratie, implementatie en beheer van systemen.</span><span class="sxs-lookup"><span data-stu-id="f24d5-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="f24d5-111">Deze bestaat uit drie primaire onderdelen:</span><span class="sxs-lookup"><span data-stu-id="f24d5-111">It consists of three primary components:</span></span>

- <span data-ttu-id="f24d5-112">[Configuraties](../configurations/configurations.md) declaratieve PowerShell-scripts die definiëren en configureren van exemplaren van resources.</span><span class="sxs-lookup"><span data-stu-id="f24d5-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="f24d5-113">Bij het uitvoeren van de configuratie, DSC (en de resources die wordt aangeroepen met de configuratie) wordt gewoon 'Maak het dus', ervoor zorgen dat het systeem in de status van de lay bestaat-out van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f24d5-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="f24d5-114">DSC-configuraties zijn ook idempotent: de lokale Configuration Manager (LCM) blijven om ervoor te zorgen dat machines zijn geconfigureerd in de configuratie van de status wordt gedeclareerd.</span><span class="sxs-lookup"><span data-stu-id="f24d5-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="f24d5-115">[Resources](../resources/resources.md) zijn het onderdeel 'Maak het dus' van DSC.</span><span class="sxs-lookup"><span data-stu-id="f24d5-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="f24d5-116">Ze bevatten de code die plaats en sla het doel van een configuratie in de opgegeven status.</span><span class="sxs-lookup"><span data-stu-id="f24d5-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="f24d5-117">Resources zich bevinden in de PowerShell-modules en kunnen worden geschreven naar iets als algemene als een bestand of een Windows-proces of een IIS-server of een virtuele machine die wordt uitgevoerd in Azure zo specifiek model.</span><span class="sxs-lookup"><span data-stu-id="f24d5-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="f24d5-118">De [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is de engine waarmee DSC vereenvoudigt het uitvoeren van de interactie tussen resources en configuraties.</span><span class="sxs-lookup"><span data-stu-id="f24d5-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="f24d5-119">De LCM controleert regelmatig of het systeem met behulp van de Controlestroom door resources worden geïmplementeerd om ervoor te zorgen dat de status die is gedefinieerd door een configuratie wordt bijgehouden.</span><span class="sxs-lookup"><span data-stu-id="f24d5-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="f24d5-120">Als het systeem onvoldoende staat heeft, wordt de LCM in aanroepen naar de code in resources zodat "," op basis van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f24d5-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="f24d5-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f24d5-121">See Also</span></span>

- [<span data-ttu-id="f24d5-122">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="f24d5-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="f24d5-123">DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="f24d5-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="f24d5-124">De Local Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="f24d5-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
