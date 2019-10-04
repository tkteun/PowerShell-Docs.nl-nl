---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941171"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="82a62-103">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="82a62-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="82a62-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="82a62-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="82a62-105">Windows Power shell desired state Configuration (DSC) heeft ingebouwde resources die u kunt gebruiken voor het configureren van uw omgeving.</span><span class="sxs-lookup"><span data-stu-id="82a62-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="82a62-106">In dit onderwerp vindt u een overzicht van het ontwikkelen van resources en koppelingen naar onderwerpen met specifieke informatie en voor beelden.</span><span class="sxs-lookup"><span data-stu-id="82a62-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="82a62-107">DSC-resource onderdelen</span><span class="sxs-lookup"><span data-stu-id="82a62-107">DSC resource components</span></span>

<span data-ttu-id="82a62-108">Een DSC-resource is een Windows Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="82a62-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="82a62-109">De module bevat zowel het schema (de definitie van de Configureer bare eigenschappen) als de implementatie (de code die het werkelijke werk opgeeft dat is opgegeven door een configuratie) voor de resource.</span><span class="sxs-lookup"><span data-stu-id="82a62-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="82a62-110">Een DSC-resource schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een script module.</span><span class="sxs-lookup"><span data-stu-id="82a62-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="82a62-111">Vanaf de ondersteuning van Power shell-klassen in versie 5 kunnen het schema en de implementatie worden gedefinieerd in een-klasse.</span><span class="sxs-lookup"><span data-stu-id="82a62-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="82a62-112">In de volgende onderwerpen vindt u meer informatie over het maken van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="82a62-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="82a62-113">Een aangepaste DSC-resource schrijven met MOF</span><span class="sxs-lookup"><span data-stu-id="82a62-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="82a62-114">Een DSC-resource implementeren inC#</span><span class="sxs-lookup"><span data-stu-id="82a62-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="82a62-115">Een aangepaste DSC-resource schrijven met Power shell-klassen</span><span class="sxs-lookup"><span data-stu-id="82a62-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* <span data-ttu-id="82a62-116">[Composite resources: Een DSC-configuratie gebruiken als resource @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="82a62-116">[Composite resources: Using a DSC configuration as a resource](authoringResourceComposite.md)</span></span>
* [<span data-ttu-id="82a62-117">Het hulp programma resource Designer gebruiken</span><span class="sxs-lookup"><span data-stu-id="82a62-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
