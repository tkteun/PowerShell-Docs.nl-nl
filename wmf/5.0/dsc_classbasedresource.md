---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="b01e4-102">DSC-resources op basis van een klasse</span><span class="sxs-lookup"><span data-stu-id="b01e4-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="b01e4-103">DSC-resources met klassen definiëren</span><span class="sxs-lookup"><span data-stu-id="b01e4-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="b01e4-104">Op basis van feedback, hebben we aangebracht ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="b01e4-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="b01e4-105">De belangrijkste verschillen tussen een klasse gebaseerde DSC-resource en een cmdlet DSC-resourceprovider zijn:</span><span class="sxs-lookup"><span data-stu-id="b01e4-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="b01e4-106">Een MOF-bestand voor het schema is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="b01e4-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="b01e4-107">Een **DSCResource** submap in de modulemap is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="b01e4-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="b01e4-108">Een PowerShell-module-bestand kan meerdere DSC-resource klassen bevatten.</span><span class="sxs-lookup"><span data-stu-id="b01e4-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="b01e4-109">Zie voor meer informatie [schrijven van een aangepaste DSC-resource met PowerShell klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="b01e4-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>