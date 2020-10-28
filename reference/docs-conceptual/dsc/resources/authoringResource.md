---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen
description: Dit artikel bevat een overzicht van het ontwikkelen van resources en koppelingen naar artikelen met specifieke informatie en voor beelden.
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656408"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="9381a-104">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="9381a-104">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="9381a-105">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="9381a-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9381a-106">Windows Power shell desired state Configuration (DSC) heeft ingebouwde resources die u kunt gebruiken voor het configureren van uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="9381a-106">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="9381a-107">Dit artikel bevat een overzicht van het ontwikkelen van resources en koppelingen naar artikelen met specifieke informatie en voor beelden.</span><span class="sxs-lookup"><span data-stu-id="9381a-107">This article provides an overview of developing resources and links to articles with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="9381a-108">DSC-resource onderdelen</span><span class="sxs-lookup"><span data-stu-id="9381a-108">DSC resource components</span></span>

<span data-ttu-id="9381a-109">Een DSC-resource is een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="9381a-109">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="9381a-110">De module bevat zowel het schema (de definitie van de Configureer bare eigenschappen) als de implementatie (de code die het werkelijke werk opgeeft dat is opgegeven door een configuratie) voor de resource.</span><span class="sxs-lookup"><span data-stu-id="9381a-110">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="9381a-111">Een DSC-resource schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een script module.</span><span class="sxs-lookup"><span data-stu-id="9381a-111">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="9381a-112">Vanaf de ondersteuning van Power shell-klassen in versie 5 kunnen het schema en de implementatie worden gedefinieerd in een-klasse.</span><span class="sxs-lookup"><span data-stu-id="9381a-112">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="9381a-113">In de volgende artikelen vindt u meer informatie over het maken van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="9381a-113">The following articles describe in more detail how to create DSC resources.</span></span>

- [<span data-ttu-id="9381a-114">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="9381a-114">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="9381a-115">Een DSC-resource implementeren in C #</span><span class="sxs-lookup"><span data-stu-id="9381a-115">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
- [<span data-ttu-id="9381a-116">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="9381a-116">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="9381a-117">Samengestelde resources: het gebruik van een DSC-configuratie als een resource</span><span class="sxs-lookup"><span data-stu-id="9381a-117">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
- [<span data-ttu-id="9381a-118">Het hulp programma resource Designer gebruiken</span><span class="sxs-lookup"><span data-stu-id="9381a-118">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
