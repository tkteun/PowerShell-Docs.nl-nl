---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Overzicht van desired state Configuration voor Windows Power shell
ms.openlocfilehash: 5c4853cb059ca0cf063a9450f97230732bc56b10
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941724"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="962e4-103">Overzicht van desired state Configuration voor Windows Power shell</span><span class="sxs-lookup"><span data-stu-id="962e4-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="962e4-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="962e4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="962e4-105">DSC is een beheer platform in Power shell waarmee u uw IT-en ontwikkelings infrastructuur met configuratie als code kunt beheren.</span><span class="sxs-lookup"><span data-stu-id="962e4-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="962e4-106">Voor een overzicht van de zakelijke voor delen van het gebruik van DSC raadpleegt u [overzicht van desired state Configuration voor besluit vormers](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="962e4-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="962e4-107">Voor een overzicht van de technische voor delen van het gebruik van DSC, Zie [desired state Configuration-overzicht voor technici](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="962e4-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="962e4-108">Zie [DSC Quick Start](../quickstarts/website-quickstart.md)om DSC snel te gaan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="962e4-108">To start using DSC quickly, see [DSC quick start](../quickstarts/website-quickstart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="962e4-109">Hoofdconcepten</span><span class="sxs-lookup"><span data-stu-id="962e4-109">Key Concepts</span></span>

<span data-ttu-id="962e4-110">DSC is een declaratief platform dat wordt gebruikt voor de configuratie, implementatie en het beheer van systemen.</span><span class="sxs-lookup"><span data-stu-id="962e4-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="962e4-111">Het bestaat uit drie primaire onderdelen:</span><span class="sxs-lookup"><span data-stu-id="962e4-111">It consists of three primary components:</span></span>

- <span data-ttu-id="962e4-112">[Configuraties](../configurations/configurations.md) zijn declaratieve Power shell-scripts waarmee instanties van resources worden gedefinieerd en geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="962e4-112">[Configurations](../configurations/configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="962e4-113">Bij het uitvoeren van de configuratie zal DSC (en de bronnen die worden aangeroepen door de configuratie) het ' zo maken ' dat het systeem bestaat in de status die is opgenomen in de configuratie.</span><span class="sxs-lookup"><span data-stu-id="962e4-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply "make it so", ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="962e4-114">DSC-configuraties zijn ook idempotent: de lokale Configuration Manager (LCM) blijft ervoor zorgen dat machines worden geconfigureerd in welke staat de configuratie declareert.</span><span class="sxs-lookup"><span data-stu-id="962e4-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="962e4-115">[Resources](../resources/resources.md) zijn het deel van DSC.</span><span class="sxs-lookup"><span data-stu-id="962e4-115">[Resources](../resources/resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="962e4-116">Ze bevatten de code die het doel van een configuratie in de opgegeven status plaatst en bewaart.</span><span class="sxs-lookup"><span data-stu-id="962e4-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="962e4-117">Resources bevinden zich in Power shell-modules en kunnen worden geschreven om iets te model leren als een bestand of een Windows-proces, of als een IIS-server of een VM die wordt uitgevoerd in Azure.</span><span class="sxs-lookup"><span data-stu-id="962e4-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="962e4-118">De [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is de engine waarmee DSC de interactie tussen bronnen en configuraties vereenvoudigt.</span><span class="sxs-lookup"><span data-stu-id="962e4-118">The [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="962e4-119">De LCM pollt regel matig het systeem met behulp van de controle stroom die door resources wordt geïmplementeerd om ervoor te zorgen dat de status die is gedefinieerd door een configuratie wordt behouden.</span><span class="sxs-lookup"><span data-stu-id="962e4-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="962e4-120">Als het systeem niet in staat is, wordt de code in de bronnen door de LCM aangeroepen volgens de configuratie.</span><span class="sxs-lookup"><span data-stu-id="962e4-120">If the system is out of state, the LCM makes calls to the code in resources to "make it so" according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="962e4-121">Zie ook</span><span class="sxs-lookup"><span data-stu-id="962e4-121">See Also</span></span>

- [<span data-ttu-id="962e4-122">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="962e4-122">DSC Configurations</span></span>](../configurations/configurations.md)
- [<span data-ttu-id="962e4-123">DSC-resources</span><span class="sxs-lookup"><span data-stu-id="962e4-123">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="962e4-124">De lokale Configuration Manager configureren</span><span class="sxs-lookup"><span data-stu-id="962e4-124">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
