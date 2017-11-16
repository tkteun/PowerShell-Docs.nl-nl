---
ms.date: 2017-06-09
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptanceScript
ms.openlocfilehash: 7092fb2e63b9e2b1eca59cd418317631bff8b172
ms.sourcegitcommit: cd66d4f49ea762a31887af2c72d087b219ddbe10
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/11/2017
---
# <a name="requiring-license-acceptance-for-scripts"></a><span data-ttu-id="546fa-103">Het vereisen van instemming van de licentie voor Scripts</span><span class="sxs-lookup"><span data-stu-id="546fa-103">Requiring License Acceptance for Scripts</span></span>

<span data-ttu-id="546fa-104">Acceptatie van de licentie wordt niet ondersteund voor scripts.</span><span class="sxs-lookup"><span data-stu-id="546fa-104">License Acceptance is not supported for scripts.</span></span> <span data-ttu-id="546fa-105">Het scenario waarbij een script is afhankelijk van een module die vereist dat de acceptatie van de licentie wordt echter ondersteund.</span><span class="sxs-lookup"><span data-stu-id="546fa-105">However, the scenario where a script depends on a module that requires license acceptance is supported.</span></span>

<span data-ttu-id="546fa-106">Script commands(Install-Script/Save-Script/Update-Script) ondersteunen een nieuwe parameter - AcceptLicense dat zich gedraagt alsof de gebruiker de licentievoorwaarden hebt gezien.</span><span class="sxs-lookup"><span data-stu-id="546fa-106">Script commands(Install-Script/Save-Script/Update-Script) support a new parameter -AcceptLicense that behaves as though user saw the license.</span></span> <span data-ttu-id="546fa-107">Als niet - AcceptLicense is opgegeven; de gebruiker wordt license.txt voor afhankelijke module weergegeven en wordt gevraagd of u de licentievoorwaarden accepteert.</span><span class="sxs-lookup"><span data-stu-id="546fa-107">If -AcceptLicense is not specified; the user will be shown license.txt for dependent module and prompted to accept the license.</span></span>

## <a name="examples"></a><span data-ttu-id="546fa-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="546fa-108">EXAMPLES</span></span>

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="546fa-109">Voorbeeld 1: Installatiescript met afhankelijkheden vereisen van instemming met licentie</span><span class="sxs-lookup"><span data-stu-id="546fa-109">Example 1: Install Script with dependencies requiring license acceptance</span></span>
<span data-ttu-id="546fa-110">Script 'ScriptRequireLicenseAcceptance', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="546fa-110">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="546fa-111">Gebruiker wordt gevraagd om een licentie accepteren.</span><span class="sxs-lookup"><span data-stu-id="546fa-111">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="546fa-112">Voorbeeld 2: Installatiescript met afhankelijkheden licentie acceptatie en -AcceptLicense vereisen</span><span class="sxs-lookup"><span data-stu-id="546fa-112">Example 2: Install Script with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="546fa-113">Script 'ScriptRequireLicenseAcceptance', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="546fa-113">Script 'ScriptRequireLicenseAcceptance' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="546fa-114">Gebruiker niet gevraagd licentie accepteren omdat - AcceptLicense is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="546fa-114">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a><span data-ttu-id="546fa-115">meer informatie</span><span class="sxs-lookup"><span data-stu-id="546fa-115">More details</span></span>
### <a name="require-license-acceptance-support-for-modulesmodulerequirelicenseacceptancemd"></a>[<span data-ttu-id="546fa-116">Acceptatie van de licentie-ondersteuning vereist voor Modules</span><span class="sxs-lookup"><span data-stu-id="546fa-116">Require License Acceptance support for Modules</span></span>](../module/RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="546fa-117">Acceptatie van de licentie-ondersteuning op PowerShellGallery vereist</span><span class="sxs-lookup"><span data-stu-id="546fa-117">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="546fa-118">Vereisen dat gebruikers van de licentie op implementeren in Azure Automation</span><span class="sxs-lookup"><span data-stu-id="546fa-118">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)
