---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Aangepaste Windows PowerShell Desired State Configuration Resources bouwen
ms.openlocfilehash: 7da4741a773d40da75c6ef667c35f86e1bae74bf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="2c7a0-103">Aangepaste Windows PowerShell Desired State Configuration Resources bouwen</span><span class="sxs-lookup"><span data-stu-id="2c7a0-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="2c7a0-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2c7a0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="2c7a0-105">Windows PowerShell Desired State Configuration (DSC) met de ingebouwde resources die u gebruiken kunt om uw omgeving te configureren.</span><span class="sxs-lookup"><span data-stu-id="2c7a0-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="2c7a0-106">(Zie voor meer informatie [ingebouwde Windows PowerShell Desired status configuratie-bronnen](builtInResource.md).) In dit onderwerp biedt een overzicht van het ontwikkelen van resources en koppelingen naar onderwerpen met specifieke informatie over en voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="2c7a0-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="2c7a0-107">Onderdelen van DSC-resource</span><span class="sxs-lookup"><span data-stu-id="2c7a0-107">DSC resource components</span></span>

<span data-ttu-id="2c7a0-108">Een DSC-resource is een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="2c7a0-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="2c7a0-109">De module bevat zowel het schema (de definitie van de configureerbare eigenschappen) en de implementatie (de code die het echte werk verricht dat door een opgegeven) voor de resource.</span><span class="sxs-lookup"><span data-stu-id="2c7a0-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="2c7a0-110">Een DSC-resource schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een scriptmodule.</span><span class="sxs-lookup"><span data-stu-id="2c7a0-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="2c7a0-111">U begint met de ondersteuning van PowerShell-klassen in versie 5, kunnen het schema en de implementatie zowel worden gedefinieerd in een klasse.</span><span class="sxs-lookup"><span data-stu-id="2c7a0-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="2c7a0-112">De volgende onderwerpen wordt beschreven in meer detail DSC-resources te maken.</span><span class="sxs-lookup"><span data-stu-id="2c7a0-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="2c7a0-113">Schrijven van een aangepaste DSC-resource met MOF</span><span class="sxs-lookup"><span data-stu-id="2c7a0-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="2c7a0-114">Implementatie van een DSC-resource in C#</span><span class="sxs-lookup"><span data-stu-id="2c7a0-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="2c7a0-115">Schrijven van een aangepaste DSC-resource met PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="2c7a0-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="2c7a0-116">Samengestelde bronnen: met een DSC-configuratie als een bron</span><span class="sxs-lookup"><span data-stu-id="2c7a0-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="2c7a0-117">Het hulpprogramma voor het Resource-Designer</span><span class="sxs-lookup"><span data-stu-id="2c7a0-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)