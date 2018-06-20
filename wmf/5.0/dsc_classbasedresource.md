---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221847"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="bd942-102">DSC-resources op basis van een klasse</span><span class="sxs-lookup"><span data-stu-id="bd942-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="bd942-103">DSC-resources met klassen definiëren</span><span class="sxs-lookup"><span data-stu-id="bd942-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="bd942-104">Op basis van feedback, hebben we aangebracht ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="bd942-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="bd942-105">De belangrijkste verschillen tussen een klasse gebaseerde DSC-resource en een cmdlet DSC-resourceprovider zijn:</span><span class="sxs-lookup"><span data-stu-id="bd942-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="bd942-106">Een MOF-bestand voor het schema is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="bd942-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="bd942-107">Een **DSCResource** submap in de modulemap is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="bd942-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="bd942-108">Een PowerShell-module-bestand kan meerdere DSC-resource klassen bevatten.</span><span class="sxs-lookup"><span data-stu-id="bd942-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="bd942-109">Zie voor meer informatie [schrijven van een aangepaste DSC-resource met PowerShell klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="bd942-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
