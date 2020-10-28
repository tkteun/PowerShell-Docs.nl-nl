---
ms.date: 06/09/2017
title: Modules die instemming met licentie vereisen
description: In het artikel wordt uitgelegd hoe u kunt werken met modules die zijn gepubliceerd in de PowerShell Gallery waarvoor een gebruiksrecht overeenkomst moet worden geaccepteerd.
ms.openlocfilehash: a9486e10b10569ce8bcde47d5c8acf0796a93851
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656120"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="2ab12-103">Modules die instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="2ab12-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="2ab12-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="2ab12-104">SYNOPSIS</span></span>

<span data-ttu-id="2ab12-105">Voor sommige uitgevers van modules moeten klanten expliciet de licentie accepteren voordat ze hun module van PowerShell Gallery kunnen installeren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="2ab12-106">Als een gebruiker een module installeert, bijwerkt of opslaat met behulp van PowerShellGet, of dit nu rechtstreeks of als afhankelijkheid voor een ander pakket is, en die module vereist dat de gebruiker akkoord gaat met een licentie, dan moet de gebruiker aangeven dat ze de licentie accepteren of mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="2ab12-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="2ab12-107">Publicatie vereisten voor modules</span><span class="sxs-lookup"><span data-stu-id="2ab12-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="2ab12-108">Aan de volgende vereisten moet worden voldaan aan de modules die gebruikers nodig hebben om de licentie te accepteren:</span><span class="sxs-lookup"><span data-stu-id="2ab12-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="2ab12-109">De sectie PSData van module manifest moet RequireLicenseAcceptance = $True bevatten.</span><span class="sxs-lookup"><span data-stu-id="2ab12-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="2ab12-110">De module moet license.txt-bestand in de hoofdmap bevatten.</span><span class="sxs-lookup"><span data-stu-id="2ab12-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="2ab12-111">Module manifest moet licentie-URI bevatten.</span><span class="sxs-lookup"><span data-stu-id="2ab12-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="2ab12-112">De module moet worden gepubliceerd met PowerShellGet-indeling versie 2,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="2ab12-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="2ab12-113">Gevolgen voor installeren/opslaan/bijwerken-module</span><span class="sxs-lookup"><span data-stu-id="2ab12-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="2ab12-114">Installeren/opslaan/bijwerken cmdlets ondersteunen een nieuwe para meter **AcceptLicense** die zich gedraagt alsof de gebruiker de licentie heeft gezien.</span><span class="sxs-lookup"><span data-stu-id="2ab12-114">Install/Save/Update cmdlets support a new parameter **AcceptLicense** that behaves as though the user saw the license.</span></span>
- <span data-ttu-id="2ab12-115">Als **RequiredLicenseAcceptance** is ingesteld op True en **AcceptLicense** niet is opgegeven, wordt de gebruiker weer gegeven `license.txt` en wordt u gevraagd om: `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)` .</span><span class="sxs-lookup"><span data-stu-id="2ab12-115">If **RequiredLicenseAcceptance** is True and **AcceptLicense** is not specified, the user is shown the `license.txt`, and prompted with: `Do you accept these license terms
  (Yes/No/YesToAll/NoToAll)`.</span></span>
  - <span data-ttu-id="2ab12-116">Als de licentie is geaccepteerd</span><span class="sxs-lookup"><span data-stu-id="2ab12-116">If the license is accepted</span></span>
    - <span data-ttu-id="2ab12-117">**Save-module:** de module wordt gekopieerd naar het systeem van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="2ab12-117">**Save-Module:** the module is copied to the user's system</span></span>
    - <span data-ttu-id="2ab12-118">**Installatie-module:** de module wordt naar het systeem van de gebruiker gekopieerd naar de juiste map (op basis van het bereik)</span><span class="sxs-lookup"><span data-stu-id="2ab12-118">**Install-Module:** the module is copied to the user's system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="2ab12-119">**Update-module:** de module is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="2ab12-119">**Update-Module:** the module is updated.</span></span>
  - <span data-ttu-id="2ab12-120">Als de licentie wordt afgewezen.</span><span class="sxs-lookup"><span data-stu-id="2ab12-120">If the license is declined.</span></span>
    - <span data-ttu-id="2ab12-121">De bewerking is geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="2ab12-121">Operation is canceled.</span></span>
    - <span data-ttu-id="2ab12-122">Alle cmdlets controleren de meta gegevens ( **requireLicenseAcceptance** en indelings versie) met de melding dat een acceptatie van de licentie is vereist</span><span class="sxs-lookup"><span data-stu-id="2ab12-122">All cmdlets check for the metadata ( **requireLicenseAcceptance** and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="2ab12-123">Als de indelings versie van de client ouder is dan 2,0, mislukt de bewerking en wordt de gebruiker gevraagd om de client bij te werken.</span><span class="sxs-lookup"><span data-stu-id="2ab12-123">If format version of client is older than 2.0, operation fails and asks the user to update the client.</span></span>
    - <span data-ttu-id="2ab12-124">Als de module is gepubliceerd met een indelings versie ouder dan 2,0, wordt de vlag requireLicenseAcceptance genegeerd.</span><span class="sxs-lookup"><span data-stu-id="2ab12-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag is ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="2ab12-125">Module-afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="2ab12-125">Module Dependencies</span></span>

- <span data-ttu-id="2ab12-126">Als in een afhankelijke module (iets anders is afhankelijk van de module) tijdens de installatie/het opslaan/bijwerken van de acceptatie van de licentie vereist is, is het acceptatie gedrag van de licentie (hierboven) vereist.</span><span class="sxs-lookup"><span data-stu-id="2ab12-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) is required.</span></span>
- <span data-ttu-id="2ab12-127">Als de module versie al in de lokale catalogus wordt weer gegeven als op het systeem wordt geïnstalleerd, wordt de licentie controle omzeild.</span><span class="sxs-lookup"><span data-stu-id="2ab12-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="2ab12-128">Als er tijdens het installeren/opslaan/bijwerken van een afhankelijke module een licentie is vereist en de licentie acceptatie niet plaatsvindt, mislukt de bewerking en volgen de normale processen voor het pakket niet installeren/opslaan/bijwerken.</span><span class="sxs-lookup"><span data-stu-id="2ab12-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation fails and follows normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="2ab12-129">Impact op Force</span><span class="sxs-lookup"><span data-stu-id="2ab12-129">Impact on -Force</span></span>

<span data-ttu-id="2ab12-130">Opgeven `–Force` is niet voldoende om een licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="2ab12-131">`–AcceptLicense` is vereist voor de installatie van.</span><span class="sxs-lookup"><span data-stu-id="2ab12-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="2ab12-132">Als `–Force` is opgegeven, RequiredLicenseAcceptance de waarde True heeft en `–AcceptLicense` niet is opgegeven, mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="2ab12-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation fails.</span></span>

## <a name="examples"></a><span data-ttu-id="2ab12-133">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="2ab12-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="2ab12-134">Voor beeld 1: module manifest bijwerken zodat acceptatie van de licentie is vereist</span><span class="sxs-lookup"><span data-stu-id="2ab12-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="2ab12-135">Met deze opdracht wordt het manifest bestand bijgewerkt en wordt de RequireLicenseAcceptance-vlag ingesteld op True.</span><span class="sxs-lookup"><span data-stu-id="2ab12-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="2ab12-136">Voor beeld 2: module installeren waarvoor licentie acceptatie is vereist</span><span class="sxs-lookup"><span data-stu-id="2ab12-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="2ab12-137">Met deze opdracht wordt de licentie uit het bestand weer gegeven `license.txt` en wordt de gebruiker gevraagd om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-137">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="2ab12-138">Voor beeld 3: een module installeren waarvoor een licentie moet worden geaccepteerd met-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2ab12-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="2ab12-139">De module wordt geïnstalleerd zonder dat u wordt gevraagd om een licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="2ab12-140">Voor beeld 4: module installeren waarvoor licentie acceptatie is vereist</span><span class="sxs-lookup"><span data-stu-id="2ab12-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```Output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="2ab12-141">Voor beeld 5: module installeren met afhankelijkheden waarvoor acceptatie van licenties is vereist</span><span class="sxs-lookup"><span data-stu-id="2ab12-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="2ab12-142">Module **ModuleWithDependency** is afhankelijk van module **ModuleRequireLicenseAcceptance** .</span><span class="sxs-lookup"><span data-stu-id="2ab12-142">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance** .</span></span> <span data-ttu-id="2ab12-143">De gebruiker wordt gevraagd de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-143">User is prompted to accept license.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```Output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="2ab12-144">Voor beeld 6: module installeren met afhankelijkheden waarvoor acceptatie van licenties is vereist en-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2ab12-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="2ab12-145">Module **ModuleWithDependency** is afhankelijk van module **ModuleRequireLicenseAcceptance** .</span><span class="sxs-lookup"><span data-stu-id="2ab12-145">Module **ModuleWithDependency** depends on module **ModuleRequireLicenseAcceptance** .</span></span> <span data-ttu-id="2ab12-146">De gebruiker wordt niet gevraagd om de licentie te accepteren als **AcceptLicense** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2ab12-146">User is not prompted to accept license as **AcceptLicense** is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="2ab12-147">Voor beeld 7: installatie module waarvoor licentie acceptatie is vereist voor een client die ouder is dan PSGetFormatVersion 2,0</span><span class="sxs-lookup"><span data-stu-id="2ab12-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```Output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion
'2.0' is not supported by the current version of PowerShellGet. Get the latest version of the
PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="2ab12-148">Voor beeld 8: module opslaan waarvoor licentie acceptatie is vereist</span><span class="sxs-lookup"><span data-stu-id="2ab12-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="2ab12-149">Met deze opdracht wordt de licentie uit het bestand weer gegeven `license.txt` en wordt de gebruiker gevraagd om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-149">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="2ab12-150">Voor beeld 9: een module opslaan waarvoor een licentie wordt geaccepteerd met-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2ab12-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="2ab12-151">De module wordt opgeslagen zonder dat u wordt gevraagd om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="2ab12-152">Voor beeld 10: een update module waarvoor licentie acceptatie is vereist</span><span class="sxs-lookup"><span data-stu-id="2ab12-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```Output
License Acceptance

License 2.0
Copyright (c) 2016 PowerShell Team
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software.

Do you accept the license terms for module 'ModuleRequireLicenseAcceptance'.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

<span data-ttu-id="2ab12-153">Met deze opdracht wordt de licentie uit het bestand weer gegeven `license.txt` en wordt de gebruiker gevraagd om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-153">This command shows the license from `license.txt` file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="2ab12-154">Voor beeld 11: Update-module waarvoor licentie acceptatie is vereist met-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2ab12-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="2ab12-155">De module wordt bijgewerkt zonder dat u wordt gevraagd om een licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="2ab12-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="2ab12-156">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="2ab12-156">More details</span></span>

[<span data-ttu-id="2ab12-157">Acceptatie van de licentie vereisen voor scripts</span><span class="sxs-lookup"><span data-stu-id="2ab12-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="2ab12-158">Ondersteuning voor acceptatie van licenties vereisen op PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="2ab12-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="2ab12-159">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="2ab12-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
