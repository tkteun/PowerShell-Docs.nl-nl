---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Acceptatie van de licentie vereisen voor scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328894"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="b9f80-103">Acceptatie van de licentie vereisen voor scripts</span><span class="sxs-lookup"><span data-stu-id="b9f80-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="b9f80-104">Acceptatie van licenties wordt niet ondersteund voor scripts.</span><span class="sxs-lookup"><span data-stu-id="b9f80-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="b9f80-105">Het scenario waarbij een script afhankelijk is van een module waarvoor acceptatie van licenties vereist is, wordt echter wel ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b9f80-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="b9f80-106">Script opdrachten (install-script/Save-script/update-script) ondersteunen een nieuwe para meter-AcceptLicense die zich gedraagt alsof de gebruiker de licentie heeft gezien.</span><span class="sxs-lookup"><span data-stu-id="b9f80-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="b9f80-107">If-AcceptLicense is niet opgegeven. de gebruiker krijgt de licentie. txt voor de afhankelijke module te zien en u wordt gevraagd de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="b9f80-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="b9f80-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b9f80-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="b9f80-109">Voor beeld 1: script installeren met afhankelijkheden waarvoor licentie acceptatie is vereist</span><span class="sxs-lookup"><span data-stu-id="b9f80-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="b9f80-110">Het script ScriptRequireLicenseAcceptance is afhankelijk van de module ModuleRequireLicenseAcceptance.</span><span class="sxs-lookup"><span data-stu-id="b9f80-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="b9f80-111">De gebruiker wordt gevraagd de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="b9f80-111">User is prompted to Accept License.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance

License Acceptance
MIT License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="b9f80-112">Voor beeld 2: script installeren met afhankelijkheden waarvoor acceptatie van licenties is vereist en-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="b9f80-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="b9f80-113">Het script ScriptRequireLicenseAcceptance is afhankelijk van de module ModuleRequireLicenseAcceptance.</span><span class="sxs-lookup"><span data-stu-id="b9f80-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="b9f80-114">De gebruiker wordt niet gevraagd om de licentie te accepteren als-AcceptLicense is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="b9f80-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="b9f80-115">Meer details</span><span class="sxs-lookup"><span data-stu-id="b9f80-115">More details</span></span>

- [<span data-ttu-id="b9f80-116">Ondersteuning van acceptatie van licenties voor modules vereisen</span><span class="sxs-lookup"><span data-stu-id="b9f80-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="b9f80-117">Ondersteuning voor acceptatie van licenties vereisen op PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="b9f80-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="b9f80-118">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="b9f80-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
