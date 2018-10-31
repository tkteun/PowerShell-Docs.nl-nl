---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Modules die instemming met licentie vereisen
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002664"
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="657c2-103">Modules die instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="657c2-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="657c2-104">SYNOPSIS</span></span>

<span data-ttu-id="657c2-105">Juridische afdelingen voor sommige uitgevers van module vereisen dat klanten de licentie expliciet accepteren moeten voordat u de module installeert vanuit PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="657c2-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="657c2-106">Als een gebruiker wordt geïnstalleerd, bijgewerkt of een module met behulp van PowerShellGet, rechtstreeks of als een afhankelijkheid voor een ander pakket worden opgeslagen en die module moet de gebruiker akkoord gaat met een licentie, wordt de gebruiker moet geven ze de gebruiksrechtovereenkomst accepteren of de bewerking is mislukt.</span><span class="sxs-lookup"><span data-stu-id="657c2-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another package, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="657c2-107">Vereisten voor Modules publiceren</span><span class="sxs-lookup"><span data-stu-id="657c2-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="657c2-108">Modules die u dat wilt gebruikers om licentie te accepteren, moeten de volgende vereisten voldoen:</span><span class="sxs-lookup"><span data-stu-id="657c2-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="657c2-109">PSData-sectie van de module-manifest moet zijn opgenomen RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="657c2-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="657c2-110">Module moet license.txt-bestand in de hoofdmap bevatten.</span><span class="sxs-lookup"><span data-stu-id="657c2-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="657c2-111">Module-manifest moet licentie Uri bevatten.</span><span class="sxs-lookup"><span data-stu-id="657c2-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="657c2-112">Module moet worden gepubliceerd met PowerShellGet indeling versie 2.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="657c2-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="657c2-113">Gevolgen voor de installatie/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="657c2-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="657c2-114">Installeer/Save/Update cmdlets biedt ondersteuning voor een nieuwe parameter – AcceptLicense die gedraagt zich alsof de gebruiker de licentie hebt gezien.</span><span class="sxs-lookup"><span data-stu-id="657c2-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="657c2-115">Als RequiredLicenseAcceptance ingesteld op True is en – AcceptLicense niet is opgegeven, de gebruiker wordt weergegeven de license.txt, en u wordt gevraagd met: &quot;gaat u akkoord met deze licentievoorwaarden (Ja/Nee/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="657c2-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="657c2-116">Als de licentie wordt geaccepteerd</span><span class="sxs-lookup"><span data-stu-id="657c2-116">If the license is accepted</span></span>
    - <span data-ttu-id="657c2-117">**Save-Module:** de module wordt gekopieerd naar de gebruiker&#39;s system</span><span class="sxs-lookup"><span data-stu-id="657c2-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="657c2-118">**Install-Module:** de module wordt gekopieerd naar de gebruiker&#39;s systeem naar de juiste map (op basis van bereik)</span><span class="sxs-lookup"><span data-stu-id="657c2-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="657c2-119">**Update-Module:** de module wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="657c2-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="657c2-120">Als de licentie is afgewezen.</span><span class="sxs-lookup"><span data-stu-id="657c2-120">If the license is declined.</span></span>
    - <span data-ttu-id="657c2-121">Kan de bewerking wordt geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="657c2-121">Operation will be cancelled.</span></span>
    - <span data-ttu-id="657c2-122">Alle cmdlets wordt gecontroleerd voor de metagegevens (requireLicenseAcceptance en versie-indeling) waarmee wordt aangegeven dat een acceptatie van de licentie is vereist</span><span class="sxs-lookup"><span data-stu-id="657c2-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
    - <span data-ttu-id="657c2-123">Als de versie van client ouder is dan 2.0, wordt de bewerking mislukt en de vraag de gebruiker om de client te werken.</span><span class="sxs-lookup"><span data-stu-id="657c2-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
    - <span data-ttu-id="657c2-124">Als de module is gepubliceerd met versie ouder is dan 2.0, worden requireLicenseAcceptance vlag genegeerd.</span><span class="sxs-lookup"><span data-stu-id="657c2-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>

## <a name="module-dependencies"></a><span data-ttu-id="657c2-125">Module-afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="657c2-125">Module Dependencies</span></span>

- <span data-ttu-id="657c2-126">Tijdens de installatie/Save/Update is-bewerking, als een afhankelijke-module (iets anders afhankelijk is van de module) is vereist voor acceptatie van de licentie en het gedrag van licentie acceptatie (hierboven) vereist.</span><span class="sxs-lookup"><span data-stu-id="657c2-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="657c2-127">Als de versie van de module al in de lokale catalogus opgenomen is als het wordt geïnstalleerd op het systeem, zouden we negeren controleren van de licentie.</span><span class="sxs-lookup"><span data-stu-id="657c2-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="657c2-128">Tijdens de installatie/Save/Update-bewerking, als een afhankelijke module een licentie moet en de acceptatie van de licentie niet wordt uitgevoerd, wordt de bewerking niet voldoen aan en volgt normale processen voor het pakket kan niet installeren/save/bijwerken.</span><span class="sxs-lookup"><span data-stu-id="657c2-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the package failed to install/save/update.</span></span>

## <a name="impact-on--force"></a><span data-ttu-id="657c2-129">Gevolgen voor de - Force</span><span class="sxs-lookup"><span data-stu-id="657c2-129">Impact on -Force</span></span>

<span data-ttu-id="657c2-130">Op te geven `–Force` is niet voldoende is om een licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-130">Specifying `–Force` is NOT sufficient to accept a license.</span></span> <span data-ttu-id="657c2-131">`–AcceptLicense` is vereist voor de machtiging om te installeren.</span><span class="sxs-lookup"><span data-stu-id="657c2-131">`–AcceptLicense` is required for permission to install.</span></span> <span data-ttu-id="657c2-132">Als `–Force` is opgegeven, RequiredLicenseAcceptance is ingesteld op True, en `–AcceptLicense` niet is opgegeven, mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="657c2-132">If `–Force` is specified, RequiredLicenseAcceptance is True, and `–AcceptLicense` is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="657c2-133">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="657c2-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="657c2-134">Voorbeeld 1: Update-Module Manifest om te vereisen van instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-134">Example 1: Update Module Manifest to require license acceptance</span></span>

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

<span data-ttu-id="657c2-135">Met deze opdracht werkt het manifestbestand en wordt de RequireLicenseAcceptance-vlag ingesteld op true.</span><span class="sxs-lookup"><span data-stu-id="657c2-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>

### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="657c2-136">Voorbeeld 2: Install Module waarvoor instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-136">Example 2: Install Module requiring license acceptance</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="657c2-137">Met deze opdracht ziet u de licentie van license.txt bestand en vraagt de gebruiker om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="657c2-138">Voorbeeld 3: Install Module waarvoor instemming met licentie vereisen bij - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="657c2-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="657c2-139">Module is geïnstalleerd zonder een prompt om licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="657c2-140">Voorbeeld 4: Install Module waarvoor instemming met licentie vereisen bij - Force</span><span class="sxs-lookup"><span data-stu-id="657c2-140">Example 4: Install Module requiring license acceptance with -Force</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -Force
```

```output
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="657c2-141">Voorbeeld 5: Install-Module met afhankelijkheden die instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>

<span data-ttu-id="657c2-142">Module 'ModuleWithDependency', is afhankelijk van module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="657c2-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="657c2-143">Gebruiker wordt gevraagd naar licentie accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-143">User is prompted to Accept License.</span></span>

```powershell
Install-Module -Name ModuleWithDependency
```

```output
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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="657c2-144">Voorbeeld 6: Install-Module met afhankelijkheden die instemming met licentie vereisen en -AcceptLicense vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>

<span data-ttu-id="657c2-145">Module 'ModuleWithDependency', is afhankelijk van module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="657c2-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="657c2-146">Gebruiker niet gevraagd om te accepteren van licentie - AcceptLicense is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="657c2-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="657c2-147">Voorbeeld 7: Die instemming met licentie vereisen op een client die ouder zijn dan PSGetFormatVersion 2.0-module installeren</span><span class="sxs-lookup"><span data-stu-id="657c2-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="657c2-148">Voorbeeld 8: Sla Module die instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-148">Example 8: Save Module requiring license acceptance</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved
```

```output
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

<span data-ttu-id="657c2-149">Met deze opdracht ziet u de licentie van license.txt bestand en vraagt de gebruiker om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="657c2-150">Voorbeeld 9: Module die instemming met licentie vereisen bij - AcceptLicense opslaan</span><span class="sxs-lookup"><span data-stu-id="657c2-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

<span data-ttu-id="657c2-151">Module is opgeslagen zonder een prompt om licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="657c2-152">Voorbeeld 10: Update-Module waarvoor instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-152">Example 10: Update Module requiring license acceptance</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance
```

```output
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

<span data-ttu-id="657c2-153">Met deze opdracht ziet u de licentie van license.txt bestand en vraagt de gebruiker om de licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="657c2-154">Voorbeeld 11: Update-Module waarvoor instemming met licentie vereisen bij - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="657c2-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

<span data-ttu-id="657c2-155">Module wordt bijgewerkt zonder een prompt om licentie te accepteren.</span><span class="sxs-lookup"><span data-stu-id="657c2-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="657c2-156">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="657c2-156">More details</span></span>

[<span data-ttu-id="657c2-157">Acceptatie van de licentie vereisen voor scripts</span><span class="sxs-lookup"><span data-stu-id="657c2-157">Require License Acceptance for Scripts</span></span>](./script-license-acceptance.md)

[<span data-ttu-id="657c2-158">Ondersteuning voor acceptatie van de licentie op PowerShellGallery vereisen</span><span class="sxs-lookup"><span data-stu-id="657c2-158">Require License Acceptance support on PowerShellGallery</span></span>](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[<span data-ttu-id="657c2-159">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="657c2-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../how-to/working-with-packages/deploy-to-azure-automation.md)
