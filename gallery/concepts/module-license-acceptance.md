---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Modules die instemming met licentie vereisen
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075219"
---
# <a name="modules-requiring-license-acceptance"></a>Modules die instemming met licentie vereisen

## <a name="synopsis"></a>SYNOPSIS

Juridische afdelingen voor sommige uitgevers van module vereisen dat klanten de licentie expliciet accepteren moeten voordat u de module installeert vanuit PowerShell Gallery. Als een gebruiker wordt geïnstalleerd, bijgewerkt of een module met behulp van PowerShellGet, rechtstreeks of als een afhankelijkheid voor een ander pakket worden opgeslagen en die module moet de gebruiker akkoord gaat met een licentie, wordt de gebruiker moet geven ze de gebruiksrechtovereenkomst accepteren of de bewerking is mislukt.

## <a name="publish-requirements-for-modules"></a>Vereisten voor Modules publiceren

Modules die u dat wilt gebruikers om licentie te accepteren, moeten de volgende vereisten voldoen:

- PSData-sectie van de module-manifest moet zijn opgenomen RequireLicenseAcceptance = $True.
- Module moet license.txt-bestand in de hoofdmap bevatten.
- Module-manifest moet licentie Uri bevatten.
- Module moet worden gepubliceerd met PowerShellGet indeling versie 2.0 en hoger.

## <a name="impact-on-installsaveupdate-module"></a>Gevolgen voor de installatie/Save/Update-Module

- Installeer/Save/Update cmdlets biedt ondersteuning voor een nieuwe parameter – AcceptLicense die gedraagt zich alsof de gebruiker de licentie hebt gezien.
- Als RequiredLicenseAcceptance ingesteld op True is en – AcceptLicense niet is opgegeven, worden de gebruiker de license.txt weergegeven, en u wordt gevraagd met: &quot;Gaat u akkoord met deze licentievoorwaarden (Ja/Nee/YesToAll/NoToAll)&quot;.
  - Als de licentie wordt geaccepteerd
    - **Save-Module:** de module wordt gekopieerd naar de gebruiker&#39;s system
    - **Install-Module:** de module wordt gekopieerd naar de gebruiker&#39;s systeem naar de juiste map (op basis van bereik)
    - **Update-Module:** de module wordt bijgewerkt.
  - Als de licentie is afgewezen.
    - Kan de bewerking wordt geannuleerd.
    - Alle cmdlets wordt gecontroleerd voor de metagegevens (requireLicenseAcceptance en versie-indeling) waarmee wordt aangegeven dat een acceptatie van de licentie is vereist
    - Als de versie van client ouder is dan 2.0, wordt de bewerking mislukt en de vraag de gebruiker om de client te werken.
    - Als de module is gepubliceerd met versie ouder is dan 2.0, worden requireLicenseAcceptance vlag genegeerd.

## <a name="module-dependencies"></a>Module-afhankelijkheden

- Tijdens de installatie/Save/Update is-bewerking, als een afhankelijke-module (iets anders afhankelijk is van de module) is vereist voor acceptatie van de licentie en het gedrag van licentie acceptatie (hierboven) vereist.
- Als de versie van de module al in de lokale catalogus opgenomen is als het wordt geïnstalleerd op het systeem, zouden we negeren controleren van de licentie.
- Tijdens de installatie/Save/Update-bewerking, als een afhankelijke module een licentie moet en de acceptatie van de licentie niet wordt uitgevoerd, wordt de bewerking niet voldoen aan en volgt normale processen voor het pakket kan niet installeren/save/bijwerken.

## <a name="impact-on--force"></a>Gevolgen voor de - Force

Op te geven `–Force` is niet voldoende is om een licentie te accepteren. `–AcceptLicense` is vereist voor de machtiging om te installeren. Als `–Force` is opgegeven, RequiredLicenseAcceptance is ingesteld op True, en `–AcceptLicense` niet is opgegeven, mislukt de bewerking.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Voorbeeld 1: Update-Module-Manifest om te vereisen van instemming met licentie vereisen

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Met deze opdracht werkt het manifestbestand en wordt de RequireLicenseAcceptance-vlag ingesteld op true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Voorbeeld 2: Vereisen van instemming met licentie-Module installeren

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

Met deze opdracht ziet u de licentie van license.txt bestand en vraagt de gebruiker om de licentie te accepteren.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Voorbeeld 3: Vereisen van instemming met licentie vereisen bij - AcceptLicense-Module installeren

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Module is geïnstalleerd zonder een prompt om licentie te accepteren.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Voorbeeld 4: Vereisen van instemming met licentie vereisen bij - Force-Module installeren

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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Voorbeeld 5: Module installeren met afhankelijkheden die instemming met licentie vereisen

Module 'ModuleWithDependency', is afhankelijk van module 'ModuleRequireLicenseAcceptance'. Gebruiker wordt gevraagd naar licentie accepteren.

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Voorbeeld 6: Module installeren met afhankelijkheden die instemming met licentie vereisen en -AcceptLicense vereisen

Module 'ModuleWithDependency', is afhankelijk van module 'ModuleRequireLicenseAcceptance'. Gebruiker niet gevraagd om te accepteren van licentie - AcceptLicense is opgegeven.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Voorbeeld 7: Vereisen van instemming met licentie vereisen op een client die ouder zijn dan PSGetFormatVersion 2.0-module installeren

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Voorbeeld 8: Opslaan van de Module die instemming met licentie vereisen

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

Met deze opdracht ziet u de licentie van license.txt bestand en vraagt de gebruiker om de licentie te accepteren.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Voorbeeld 9: Module die instemming met licentie vereisen bij - AcceptLicense opslaan

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Module is opgeslagen zonder een prompt om licentie te accepteren.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Voorbeeld 10: Bijwerken van de Module die instemming met licentie vereisen

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

Met deze opdracht ziet u de licentie van license.txt bestand en vraagt de gebruiker om de licentie te accepteren.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Voorbeeld 11: Module die instemming met licentie vereisen bij - AcceptLicense bijwerken

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Module wordt bijgewerkt zonder een prompt om licentie te accepteren.

## <a name="more-details"></a>Meer informatie

[Acceptatie van de licentie vereisen voor scripts](./script-license-acceptance.md)

[Ondersteuning voor acceptatie van de licentie op PowerShellGallery vereisen](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Acceptatie van de licentie vereisen bij implementeren naar Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
