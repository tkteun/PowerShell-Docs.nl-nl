---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Vereisen van instemming met licentie vereisen voor scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084671"
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="1dd91-103">Vereisen van instemming met licentie vereisen voor scripts</span><span class="sxs-lookup"><span data-stu-id="1dd91-103">Requiring license acceptance for scripts</span></span>

<span data-ttu-id="1dd91-104">Acceptatie van de licentie wordt niet ondersteund voor scripts.</span><span class="sxs-lookup"><span data-stu-id="1dd91-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="1dd91-105">Het scenario waarbij een script afhankelijk is van een module die is vereist acceptatie van de licentie wordt echter ondersteund.</span><span class="sxs-lookup"><span data-stu-id="1dd91-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="1dd91-106">Script commands(Install-Script/Save-Script/Update-Script) ondersteuning voor een nieuwe parameter - AcceptLicense dat zich gedraagt alsof de gebruiker de licentie hebt gezien.</span><span class="sxs-lookup"><span data-stu-id="1dd91-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="1dd91-107">Als de - AcceptLicense is niet opgegeven. de gebruiker wordt license.txt voor afhankelijke module weergegeven en u wordt gevraagd om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="1dd91-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="1dd91-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1dd91-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="1dd91-109">Voorbeeld 1: Installatiescript met afhankelijkheden die instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="1dd91-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>

<span data-ttu-id="1dd91-110">Script 'ScriptRequireLicenseAcceptance', is afhankelijk van module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="1dd91-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1dd91-111">Gebruiker wordt gevraagd naar licentie accepteren.</span><span class="sxs-lookup"><span data-stu-id="1dd91-111">User is prompted to Accept License.</span></span>

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="1dd91-112">Voorbeeld 2: Script met afhankelijkheden vereisen van instemming met licentie vereisen en -AcceptLicense installeren</span><span class="sxs-lookup"><span data-stu-id="1dd91-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="1dd91-113">Script 'ScriptRequireLicenseAcceptance', is afhankelijk van module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="1dd91-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1dd91-114">Gebruiker niet gevraagd om te accepteren van licentie - AcceptLicense is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1dd91-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="1dd91-115">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="1dd91-115">More details</span></span>

- [<span data-ttu-id="1dd91-116">Ondersteuning voor acceptatie van de licentie vereisen voor Modules</span><span class="sxs-lookup"><span data-stu-id="1dd91-116">Require License Acceptance support for Modules</span></span>](module-license-acceptance.md)
- [<span data-ttu-id="1dd91-117">Ondersteuning voor acceptatie van de licentie op PowerShellGallery vereisen</span><span class="sxs-lookup"><span data-stu-id="1dd91-117">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [<span data-ttu-id="1dd91-118">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="1dd91-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
