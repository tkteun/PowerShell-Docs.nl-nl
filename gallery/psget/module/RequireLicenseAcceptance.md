---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: RequireLicenseAcceptance
ms.openlocfilehash: d78f8cb7f84869880e9a88a0f0407d18dc5c64cb
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="modules-requiring-license-acceptance"></a><span data-ttu-id="1ba4c-103">Modules die instemming met licentie vereisen</span><span class="sxs-lookup"><span data-stu-id="1ba4c-103">Modules Requiring License Acceptance</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ba4c-104">SYNOPSIS</span><span class="sxs-lookup"><span data-stu-id="1ba4c-104">SYNOPSIS</span></span>
<span data-ttu-id="1ba4c-105">Juridische afdelingen voor sommige uitgevers van de module vereist dat klanten expliciet de licentievoorwaarden accepteren voordat hun-module installeren vanuit PowerShell-galerie.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-105">Legal departments for some module publishers require that customers must explicitly accept the license before installing their module from PowerShell Gallery.</span></span> <span data-ttu-id="1ba4c-106">Als een gebruiker wordt geïnstalleerd, bijgewerkt of een module met behulp van PowerShellGet, rechtstreeks of als een afhankelijkheid voor een ander item wordt opgeslagen en die module moet de gebruiker akkoord gaat met een licentie, moet de gebruiker aan ze de licentievoorwaarden accepteren of dat de bewerking is mislukt.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-106">If a user installs, updates, or saves a module using PowerShellGet, whether directly or as a dependency for another item, and that module requires the user to agree to a license, the user must indicate they accept the license or the operation fails.</span></span>

## <a name="publish-requirements-for-modules"></a><span data-ttu-id="1ba4c-107">Vereisten voor Modules publiceren</span><span class="sxs-lookup"><span data-stu-id="1ba4c-107">Publish Requirements for Modules</span></span>

<span data-ttu-id="1ba4c-108">Modules die u dat wilt gebruikers moeten akkoord gaan met licentievoorwaarden moeten volgende vereisten voldoen:</span><span class="sxs-lookup"><span data-stu-id="1ba4c-108">Modules that would like to require users to accept license should fulfill following requirements:</span></span>

- <span data-ttu-id="1ba4c-109">PSData sectie van de module-manifest bevatten RequireLicenseAcceptance = $True.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-109">PSData section of module manifest should include RequireLicenseAcceptance = $True.</span></span>
- <span data-ttu-id="1ba4c-110">Module moet license.txt bestand in de hoofdmap bevatten.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-110">Module should contain license.txt file in root directory.</span></span>
- <span data-ttu-id="1ba4c-111">Module-manifest moet licentie Uri bevatten.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-111">Module manifest should contain License Uri.</span></span>
- <span data-ttu-id="1ba4c-112">Module moet worden gepubliceerd met PowerShellGet indeling versie 2.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-112">Module should be published with PowerShellGet Format Version 2.0 and above.</span></span>

## <a name="impact-on-installsaveupdate-module"></a><span data-ttu-id="1ba4c-113">Gevolgen voor de installatie/Save/Update-Module</span><span class="sxs-lookup"><span data-stu-id="1ba4c-113">Impact on Install/Save/Update-Module</span></span>

- <span data-ttu-id="1ba4c-114">Cmdlets opslaan-installatie-Update wordt ondersteuning voor een nieuwe parameter – het AcceptLicense gedraagt zich alsof de gebruiker de licentievoorwaarden hebt gezien.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-114">Install/Save/Update cmdlets will support a new parameter –AcceptLicense that will behave as though the user saw the license.</span></span>
- <span data-ttu-id="1ba4c-115">Als RequiredLicenseAcceptance ingesteld op True is en – AcceptLicense niet is opgegeven, de gebruiker worden weergegeven de license.txt, en met gevraagd: &quot;gaat u akkoord met deze licentievoorwaarden (Ja/Nee/YesToAll/NoToAll)&quot;.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-115">If RequiredLicenseAcceptance is True and –AcceptLicense is not specified, the user will be shown the license.txt, and prompted with: &quot;Do you accept these license terms (Yes/No/YesToAll/NoToAll)&quot;.</span></span>
  - <span data-ttu-id="1ba4c-116">Als de licentie is geaccepteerd</span><span class="sxs-lookup"><span data-stu-id="1ba4c-116">If the license is accepted</span></span>
    - <span data-ttu-id="1ba4c-117">**Opslaan-Module:** de module wordt gekopieerd naar de gebruiker&#39;s systeem</span><span class="sxs-lookup"><span data-stu-id="1ba4c-117">**Save-Module:** the module will be copied to the user&#39;s system</span></span>
    - <span data-ttu-id="1ba4c-118">**Installatie-Module:** de module wordt gekopieerd naar de gebruiker&#39;s systeem naar de juiste map (op basis van bereik)</span><span class="sxs-lookup"><span data-stu-id="1ba4c-118">**Install-Module:** the module will be copied to the user&#39;s system to the proper folder (based on scope)</span></span>
    - <span data-ttu-id="1ba4c-119">**Update-Module:** de module wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-119">**Update-Module:** the module will be updated.</span></span>
  - <span data-ttu-id="1ba4c-120">Als de licentie is geweigerd.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-120">If the license is declined.</span></span>
    - <span data-ttu-id="1ba4c-121">Bewerking wordt geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-121">Operation will be cancelled.</span></span>
- <span data-ttu-id="1ba4c-122">Alle cmdlets wordt voor de metagegevens (requireLicenseAcceptance en versie-indeling) waarin staat dat de acceptatie van een licentie is vereist dat gecontroleerd</span><span class="sxs-lookup"><span data-stu-id="1ba4c-122">All cmdlets will check for the metadata(requireLicenseAcceptance and Format Version) that says a license acceptance is required</span></span>
  - <span data-ttu-id="1ba4c-123">Als de versie van de indeling van de client is ouder dan 2.0, bewerking mislukken en vraag de gebruiker naar de client bijwerken.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-123">If format version of client is older than 2.0, operation will fail and ask the user to update the client.</span></span>
  - <span data-ttu-id="1ba4c-124">Als de module is gepubliceerd met versie ouder is dan 2.0-indeling, worden requireLicenseAcceptance vlag genegeerd.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-124">If module was published with format version older than 2.0, requireLicenseAcceptance flag will be ignored.</span></span>


 ## <a name="module-dependencies"></a><span data-ttu-id="1ba4c-125">Module-afhankelijkheden</span><span class="sxs-lookup"><span data-stu-id="1ba4c-125">Module Dependencies</span></span>
- <span data-ttu-id="1ba4c-126">Tijdens het opslaan-installatie-Update is-bewerking, als een afhankelijke module (iets anders is afhankelijk van de module) licentie acceptatie en vervolgens het gedrag van licentie acceptatie (boven vereist) vereist.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-126">During Install/Save/Update operation, if a dependent module(something else depends on the module) requires license acceptance, then the license acceptance behavior (above) will be required.</span></span>
- <span data-ttu-id="1ba4c-127">Als de moduleversie al wordt vermeld in de lokale catalogus als het wordt geïnstalleerd op het systeem, zouden we omzeilen licentie moet worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-127">If the module version is already listed in the local catalog as being installed on the system, we would bypass the license checking.</span></span>
- <span data-ttu-id="1ba4c-128">Tijdens de bewerking opslaan-installatie-Update, als een afhankelijke module een licentie moet en de acceptatie van de licentie niet wordt uitgevoerd, zal de bewerking mislukken en volg normale processen voor het item kan niet opslaan-installatie-update.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-128">During Install/Save/Update operation, if a dependent module requires a license, and the license acceptance does not occur, the operation will fail and follow normal processes for the item failed to install/save/update.</span></span>

 ## <a name="impact-on--force"></a><span data-ttu-id="1ba4c-129">Gevolgen voor de - Force</span><span class="sxs-lookup"><span data-stu-id="1ba4c-129">Impact on -Force</span></span>

<span data-ttu-id="1ba4c-130">Geven – Force is niet voldoende zijn voor het accepteren van een licentie.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-130">Specifying –Force is NOT sufficient to accept a license.</span></span> <span data-ttu-id="1ba4c-131">– AcceptLicense is vereist voor de machtiging om te installeren.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-131">–AcceptLicense is required for permission to install.</span></span> <span data-ttu-id="1ba4c-132">Als – Force is opgegeven, RequiredLicenseAcceptance is ingesteld op True, en – AcceptLicense niet is opgegeven, mislukt de bewerking.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-132">If –Force is specified, RequiredLicenseAcceptance is True, and –AcceptLicense is NOT specified, the operation will fail.</span></span>

## <a name="examples"></a><span data-ttu-id="1ba4c-133">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="1ba4c-133">EXAMPLES</span></span>

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a><span data-ttu-id="1ba4c-134">Voorbeeld 1: Update Module Manifest licentie acceptatie vereisen</span><span class="sxs-lookup"><span data-stu-id="1ba4c-134">Example 1: Update Module Manifest to require license acceptance</span></span>
```PowerShell
PS C:\> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```
<span data-ttu-id="1ba4c-135">Deze opdracht werkt het manifestbestand en wordt de RequireLicenseAcceptance-vlag ingesteld op true.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-135">This command updates the manifest file and sets the RequireLicenseAcceptance flag to true.</span></span>
### <a name="example-2-install-module-requiring-license-acceptance"></a><span data-ttu-id="1ba4c-136">Voorbeeld 2: Installeer Module vereisen licentie acceptatie</span><span class="sxs-lookup"><span data-stu-id="1ba4c-136">Example 2: Install Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance

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
<span data-ttu-id="1ba4c-137">Deze opdracht geeft de licentie van license.txt bestand en vraagt de gebruiker de licentievoorwaarden accepteren.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-137">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="1ba4c-138">Voorbeeld 3: Installatie Module vereisen licentie instemming met - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="1ba4c-138">Example 3: Install Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="1ba4c-139">Module is zonder een prompt te accepteren van de licentie geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-139">Module is installed without any prompt to accept license.</span></span>

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a><span data-ttu-id="1ba4c-140">Voorbeeld 4: Installatie Module vereisen licentie instemming met - Force</span><span class="sxs-lookup"><span data-stu-id="1ba4c-140">Example 4: Install Module requiring license acceptance with -Force</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a><span data-ttu-id="1ba4c-141">Voorbeeld 5: Installatie Module met afhankelijkheden vereisen van instemming met licentie</span><span class="sxs-lookup"><span data-stu-id="1ba4c-141">Example 5: Install Module with dependencies requiring license acceptance</span></span>
<span data-ttu-id="1ba4c-142">Module 'ModuleWithDependency', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-142">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1ba4c-143">Gebruiker wordt gevraagd om een licentie accepteren.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-143">User is prompted to Accept License.</span></span>
```PowerShell
PS C:\> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a><span data-ttu-id="1ba4c-144">Voorbeeld 6: Installatie Module met afhankelijkheden licentie acceptatie en -AcceptLicense vereisen</span><span class="sxs-lookup"><span data-stu-id="1ba4c-144">Example 6: Install Module with dependencies requiring license acceptance and -AcceptLicense</span></span>
<span data-ttu-id="1ba4c-145">Module 'ModuleWithDependency', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-145">Module 'ModuleWithDependency' depends on module 'ModuleRequireLicenseAcceptance'.</span></span> <span data-ttu-id="1ba4c-146">Gebruiker niet gevraagd licentie accepteren omdat - AcceptLicense is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-146">User is not prompted to accept license as -AcceptLicense is specified.</span></span>
```PowerShell
PS C:\>  Install-Module -Name ModuleWithDependency -AcceptLicense
```
### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a><span data-ttu-id="1ba4c-147">Voorbeeld 7: Vereisen van instemming van de licentie op een client die ouder zijn dan PSGetFormatVersion 2.0-module installeren</span><span class="sxs-lookup"><span data-stu-id="1ba4c-147">Example 7: Install module requiring license acceptance on a client older than PSGetFormatVersion 2.0</span></span>
```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```
### <a name="example-8-save-module-requiring-license-acceptance"></a><span data-ttu-id="1ba4c-148">Voorbeeld 8: Sla Module vereisen van instemming met licentie</span><span class="sxs-lookup"><span data-stu-id="1ba4c-148">Example 8: Save Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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
<span data-ttu-id="1ba4c-149">Deze opdracht geeft de licentie van license.txt bestand en vraagt de gebruiker de licentievoorwaarden accepteren.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-149">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="1ba4c-150">Voorbeeld 9: Sla Module vereisen van instemming met AcceptLicense - licentie</span><span class="sxs-lookup"><span data-stu-id="1ba4c-150">Example 9: Save Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```
<span data-ttu-id="1ba4c-151">Module is zonder een prompt te accepteren van de licentie opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-151">Module is saved without any prompt to accept license.</span></span>

### <a name="example-10-update-module-requiring-license-acceptance"></a><span data-ttu-id="1ba4c-152">Voorbeeld 10: Update Module vereisen licentie acceptatie</span><span class="sxs-lookup"><span data-stu-id="1ba4c-152">Example 10: Update Module requiring license acceptance</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance

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
<span data-ttu-id="1ba4c-153">Deze opdracht geeft de licentie van license.txt bestand en vraagt de gebruiker de licentievoorwaarden accepteren.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-153">This command shows the license from license.txt file and prompts the user to accept the license.</span></span>

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a><span data-ttu-id="1ba4c-154">Voorbeeld 11: Module Update vereisen licentie instemming met - AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="1ba4c-154">Example 11: Update Module requiring license acceptance with -AcceptLicense</span></span>
```PowerShell
PS C:\> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```
<span data-ttu-id="1ba4c-155">Module bijgewerkt zonder een prompt licentie accepteren.</span><span class="sxs-lookup"><span data-stu-id="1ba4c-155">Module is updated without any prompt to accept license.</span></span>

## <a name="more-details"></a><span data-ttu-id="1ba4c-156">meer informatie</span><span class="sxs-lookup"><span data-stu-id="1ba4c-156">More details</span></span>
### <a name="require-license-acceptance-for-scriptsscriptscriptrequirelicenseacceptancemd"></a>[<span data-ttu-id="1ba4c-157">Acceptatie van de licentie vereisen voor scripts</span><span class="sxs-lookup"><span data-stu-id="1ba4c-157">Require License Acceptance for Scripts</span></span>](../script/script_RequireLicenseAcceptance.md)

### <a name="require-license-acceptance-support-on-powershellgallerypsgallerypsgalleryrequireslicenseacceptancemd"></a>[<span data-ttu-id="1ba4c-158">Acceptatie van de licentie-ondersteuning op PowerShellGallery vereist</span><span class="sxs-lookup"><span data-stu-id="1ba4c-158">Require License Acceptance support on PowerShellGallery</span></span>](../../psgallery/psgallery_requires_license_acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationpsgallerypsgallerydeploytoazureautomationrequirelicenseacceptancemd"></a>[<span data-ttu-id="1ba4c-159">Acceptatie van de licentie vereisen bij implementeren naar Azure Automation</span><span class="sxs-lookup"><span data-stu-id="1ba4c-159">Require License Acceptance on Deploy to Azure Automation</span></span>](../../psgallery/psgallery_deploy_to_azure_automation_requireLicenseAcceptance.md)