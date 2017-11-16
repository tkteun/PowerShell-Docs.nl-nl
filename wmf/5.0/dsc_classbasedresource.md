---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="0d3cd-102">Op basis van een klasse DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="0d3cd-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="0d3cd-103">DSC-resources met klassen definiëren</span><span class="sxs-lookup"><span data-stu-id="0d3cd-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="0d3cd-104">Op basis van feedback, hebben we aangebracht ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="0d3cd-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="0d3cd-105">De belangrijkste verschillen tussen een klasse gebaseerde DSC-resource en een cmdlet DSC-resourceprovider zijn:</span><span class="sxs-lookup"><span data-stu-id="0d3cd-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="0d3cd-106">Een MOF-bestand voor het schema is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="0d3cd-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="0d3cd-107">Een **DSCResource** submap in de modulemap is niet vereist.</span><span class="sxs-lookup"><span data-stu-id="0d3cd-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="0d3cd-108">Een PowerShell-module-bestand kan meerdere DSC-resource klassen bevatten.</span><span class="sxs-lookup"><span data-stu-id="0d3cd-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="0d3cd-109">Zie voor meer informatie [schrijven van een aangepaste DSC-resource met PowerShell klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="0d3cd-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

