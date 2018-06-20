---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Het vereisen van instemming van de licentie voor scripts
ms.openlocfilehash: 6374c8c8536dd0c8f27580a5b8895b8db18424f9
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
ms.locfileid: "34048816"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="85904-103">Het vereisen van instemming van de licentie voor scripts</span><span class="sxs-lookup"><span data-stu-id="85904-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="85904-104">Acceptatie van de licentie wordt niet ondersteund voor scripts.</span><span class="sxs-lookup"><span data-stu-id="85904-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="85904-105">Het scenario waarbij een script is afhankelijk van een module die vereist dat de acceptatie van de licentie wordt echter ondersteund.</span><span class="sxs-lookup"><span data-stu-id="85904-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="85904-106">Script commands(Install-Script/Save-Script/Update-Script) ondersteunen een nieuwe parameter - AcceptLicense dat zich gedraagt alsof de gebruiker de licentievoorwaarden hebt gezien.</span><span class="sxs-lookup"><span data-stu-id="85904-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="85904-107">Als niet - AcceptLicense is opgegeven; de gebruiker wordt license.txt voor afhankelijke module weergegeven en wordt gevraagd of u de licentievoorwaarden accepteert.</span><span class="sxs-lookup"><span data-stu-id="85904-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="85904-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="85904-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="85904-109">Voorbeeld 1: Installatiescript met afhankelijkheden vereisen van instemming met licentie</span><span class="sxs-lookup"><span data-stu-id="85904-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="85904-110">Script 'ScriptRequireLicenseAcceptance', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="85904-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="85904-111">Gebruiker wordt gevraagd om een licentie accepteren.</span><span class="sxs-lookup"><span data-stu-id="85904-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="85904-112">Voorbeeld 2: Installatiescript met afhankelijkheden licentie acceptatie en -AcceptLicense vereisen</span><span class="sxs-lookup"><span data-stu-id="85904-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="85904-113">Script 'ScriptRequireLicenseAcceptance', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="85904-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="85904-114">Gebruiker niet gevraagd licentie accepteren omdat - AcceptLicense is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="85904-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="85904-115">meer informatie</span><span class="sxs-lookup"><span data-stu-id="85904-115">More details</span></span>

- [<span data-ttu-id="85904-116">Acceptatie van de licentie-ondersteuning vereist voor Modules</span><span class="sxs-lookup"><span data-stu-id="85904-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="85904-117">Acceptatie van de licentie-ondersteuning op PowerShellGallery vereist</span><span class="sxs-lookup"><span data-stu-id="85904-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [<span data-ttu-id="85904-118">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="85904-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-items/deploy-to-azure-automation.md)