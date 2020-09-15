---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen
ms.openlocfilehash: 203a2e3d0e118b86ae1fe959cc3508b6ed2733a8
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217573"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="18ba6-103">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="18ba6-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="18ba6-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="18ba6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="18ba6-105">Windows Power shell desired state Configuration (DSC) heeft ingebouwde resources die u kunt gebruiken voor het configureren van uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="18ba6-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="18ba6-106">In dit onderwerp vindt u een overzicht van het ontwikkelen van resources en koppelingen naar onderwerpen met specifieke informatie en voor beelden.</span><span class="sxs-lookup"><span data-stu-id="18ba6-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="18ba6-107">DSC-resource onderdelen</span><span class="sxs-lookup"><span data-stu-id="18ba6-107">DSC resource components</span></span>

<span data-ttu-id="18ba6-108">Een DSC-resource is een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="18ba6-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="18ba6-109">De module bevat zowel het schema (de definitie van de Configureer bare eigenschappen) als de implementatie (de code die het werkelijke werk opgeeft dat is opgegeven door een configuratie) voor de resource.</span><span class="sxs-lookup"><span data-stu-id="18ba6-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="18ba6-110">Een DSC-resource schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een script module.</span><span class="sxs-lookup"><span data-stu-id="18ba6-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="18ba6-111">Vanaf de ondersteuning van Power shell-klassen in versie 5 kunnen het schema en de implementatie worden gedefinieerd in een-klasse.</span><span class="sxs-lookup"><span data-stu-id="18ba6-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="18ba6-112">In de volgende onderwerpen vindt u meer informatie over het maken van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="18ba6-112">The following topics describe in more detail how to create DSC resources.</span></span>

- [<span data-ttu-id="18ba6-113">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="18ba6-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="18ba6-114">Een DSC-resource implementeren in C #</span><span class="sxs-lookup"><span data-stu-id="18ba6-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
- [<span data-ttu-id="18ba6-115">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="18ba6-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="18ba6-116">Samengestelde resources: het gebruik van een DSC-configuratie als een resource</span><span class="sxs-lookup"><span data-stu-id="18ba6-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
- [<span data-ttu-id="18ba6-117">Het hulp programma resource Designer gebruiken</span><span class="sxs-lookup"><span data-stu-id="18ba6-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
