---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058111"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="0d40a-102">DSC-resources op basis van een klasse</span><span class="sxs-lookup"><span data-stu-id="0d40a-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="0d40a-103">DSC-resources met klassen definiëren</span><span class="sxs-lookup"><span data-stu-id="0d40a-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="0d40a-104">Op basis van feedback, hebben we ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="0d40a-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="0d40a-105">De belangrijkste verschillen tussen een klasse op basis van DSC-resource en een cmdlet DSC-resourceprovider zijn:</span><span class="sxs-lookup"><span data-stu-id="0d40a-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="0d40a-106">Een MOF-bestand voor het schema is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="0d40a-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="0d40a-107">Een **sleutelwoorden dscresource bieden** submap in de modulemap is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="0d40a-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="0d40a-108">Een PowerShell-module-bestand kan meerdere DSC-resource-klassen bevatten.</span><span class="sxs-lookup"><span data-stu-id="0d40a-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="0d40a-109">Zie voor meer informatie, [schrijven van een aangepaste DSC-resource met de PowerShell-klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="0d40a-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
