---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Modules die instemming met licentie vereisen
ms.openlocfilehash: fe197ea271e18580a221ad4d5245b685bd81775b
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/10/2018
---
# <a name="modules-requiring-license-acceptance"></a>Modules die instemming met licentie vereisen

## <a name="synopsis"></a>SAMENVATTING

Juridische afdelingen voor sommige uitgevers van de module vereist dat klanten expliciet de licentievoorwaarden accepteren voordat hun-module installeren vanuit PowerShell-galerie. Als een gebruiker wordt geïnstalleerd, bijgewerkt of een module met behulp van PowerShellGet, rechtstreeks of als een afhankelijkheid voor een ander item wordt opgeslagen en die module moet de gebruiker akkoord gaat met een licentie, moet de gebruiker aan ze de licentievoorwaarden accepteren of dat de bewerking is mislukt.

## <a name="publish-requirements-for-modules"></a>Vereisten voor Modules publiceren

Modules die u dat wilt gebruikers moeten akkoord gaan met licentievoorwaarden moeten volgende vereisten voldoen:

- PSData sectie van de module-manifest bevatten RequireLicenseAcceptance = $True.
- Module moet license.txt bestand in de hoofdmap bevatten.
- Module-manifest moet licentie Uri bevatten.
- Module moet worden gepubliceerd met PowerShellGet indeling versie 2.0 en hoger.

## <a name="impact-on-installsaveupdate-module"></a>Gevolgen voor de installatie/Save/Update-Module

- Cmdlets opslaan-installatie-Update wordt ondersteuning voor een nieuwe parameter – het AcceptLicense gedraagt zich alsof de gebruiker de licentievoorwaarden hebt gezien.
- Als RequiredLicenseAcceptance ingesteld op True is en – AcceptLicense niet is opgegeven, de gebruiker worden weergegeven de license.txt, en met gevraagd: &quot;gaat u akkoord met deze licentievoorwaarden (Ja/Nee/YesToAll/NoToAll)&quot;.
  - Als de licentie is geaccepteerd
    - **Opslaan-Module:** de module wordt gekopieerd naar de gebruiker&#39;s systeem
    - **Installatie-Module:** de module wordt gekopieerd naar de gebruiker&#39;s systeem naar de juiste map (op basis van bereik)
    - **Update-Module:** de module wordt bijgewerkt.
  - Als de licentie is geweigerd.
    - Bewerking wordt geannuleerd.
- Alle cmdlets wordt voor de metagegevens (requireLicenseAcceptance en versie-indeling) waarin staat dat de acceptatie van een licentie is vereist dat gecontroleerd
  - Als de versie van de indeling van de client is ouder dan 2.0, bewerking mislukken en vraag de gebruiker naar de client bijwerken.
  - Als de module is gepubliceerd met versie ouder is dan 2.0-indeling, worden requireLicenseAcceptance vlag genegeerd.


 ## <a name="module-dependencies"></a>Module-afhankelijkheden
- Tijdens het opslaan-installatie-Update is-bewerking, als een afhankelijke module (iets anders is afhankelijk van de module) licentie acceptatie en vervolgens het gedrag van licentie acceptatie (boven vereist) vereist.
- Als de moduleversie al wordt vermeld in de lokale catalogus als het wordt geïnstalleerd op het systeem, zouden we omzeilen licentie moet worden gecontroleerd.
- Tijdens de bewerking opslaan-installatie-Update, als een afhankelijke module een licentie moet en de acceptatie van de licentie niet wordt uitgevoerd, zal de bewerking mislukken en volg normale processen voor het item kan niet opslaan-installatie-update.

 ## <a name="impact-on--force"></a>Gevolgen voor de - Force

Geven – Force is niet voldoende zijn voor het accepteren van een licentie. – AcceptLicense is vereist voor de machtiging om te installeren. Als – Force is opgegeven, RequiredLicenseAcceptance is ingesteld op True, en – AcceptLicense niet is opgegeven, mislukt de bewerking.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Voorbeeld 1: Update Module Manifest licentie acceptatie vereisen

```PowerShell
PS> Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance

PrivateData = @{

    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Deze opdracht werkt het manifestbestand en wordt de RequireLicenseAcceptance-vlag ingesteld op true.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Voorbeeld 2: Installeer Module vereisen licentie acceptatie

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance

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

Deze opdracht geeft de licentie van license.txt bestand en vraagt de gebruiker de licentievoorwaarden accepteren.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Voorbeeld 3: Installatie Module vereisen licentie instemming met - AcceptLicense

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Module is zonder een prompt te accepteren van de licentie geïnstalleerd.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Voorbeeld 4: Installatie Module vereisen licentie instemming met - Force

```PowerShell
PS> Install-Module -Name ModuleRequireLicenseAcceptance -Force
PackageManagement\Install-Package : License Acceptance is required for module 'ModuleRequireLicenseAcceptance'. Please specify '-AcceptLicense' to perform this operation.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.1.3.3\PSModule.psm1:1837 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], E
   xception
    + FullyQualifiedErrorId : ForceAcceptLicense,Install-PackageUtility,Microsoft.PowerShell.PackageManagement.Cmdlets
   .InstallPackage
```

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Voorbeeld 5: Installatie Module met afhankelijkheden vereisen van instemming met licentie

Module 'ModuleWithDependency', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'. Gebruiker wordt gevraagd om een licentie accepteren.

```PowerShell
PS> Install-Module -Name ModuleWithDependency

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Voorbeeld 6: Installatie Module met afhankelijkheden licentie acceptatie en -AcceptLicense vereisen

Module 'ModuleWithDependency', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'. Gebruiker niet gevraagd licentie accepteren omdat - AcceptLicense is opgegeven.

```PowerShell
PS>  Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Voorbeeld 7: Vereisen van instemming van de licentie op een client die ouder zijn dan PSGetFormatVersion 2.0-module installeren

```PowerShell
PS C:\windows\system32> Install-Module -Name ModuleRequireLicenseAcceptance

WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.

```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Voorbeeld 8: Sla Module vereisen van instemming met licentie

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -Path C:\Saved

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

Deze opdracht geeft de licentie van license.txt bestand en vraagt de gebruiker de licentievoorwaarden accepteren.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Voorbeeld 9: Sla Module vereisen van instemming met AcceptLicense - licentie

```PowerShell
PS> Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

Module is zonder een prompt te accepteren van de licentie opgeslagen.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Voorbeeld 10: Update Module vereisen licentie acceptatie

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance

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

Deze opdracht geeft de licentie van license.txt bestand en vraagt de gebruiker de licentievoorwaarden accepteren.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Voorbeeld 11: Module Update vereisen licentie instemming met - AcceptLicense

```PowerShell
PS> Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

Module bijgewerkt zonder een prompt licentie accepteren.

## <a name="more-details"></a>meer informatie

### <a name="require-license-acceptance-for-scriptsscript-license-acceptancemd"></a>[Acceptatie van de licentie vereisen voor scripts](./script-license-acceptance.md)

### <a name="require-license-acceptance-support-on-powershellgalleryhow-toworking-with-itemsitems-that-require-license-acceptancemd"></a>[Acceptatie van de licentie-ondersteuning op PowerShellGallery vereist](../how-to/working-with-items/items-that-require-license-acceptance.md)

### <a name="require-license-acceptance-on-deploy-to-azure-automationhow-toworking-with-itemsdeploy-to-azure-automationmd"></a>[Acceptatie van de licentie vereisen bij implementeren naar Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)