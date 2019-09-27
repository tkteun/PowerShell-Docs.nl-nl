---
ms.date: 06/09/2017
schema: 2.0.0
keywords: zo
title: Modules die instemming met licentie vereisen
ms.openlocfilehash: 369e32d5278a2e1bf1d3f2ae67f670c524b9f878
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329202"
---
# <a name="modules-requiring-license-acceptance"></a>Modules die instemming met licentie vereisen

## <a name="synopsis"></a>SAMEN VATTING

Voor sommige uitgevers van modules moeten klanten expliciet de licentie accepteren voordat ze hun module van PowerShell Gallery kunnen installeren. Als een gebruiker een module installeert, bijwerkt of opslaat met behulp van PowerShellGet, of dit nu rechtstreeks of als afhankelijkheid voor een ander pakket is, en die module vereist dat de gebruiker akkoord gaat met een licentie, dan moet de gebruiker aangeven dat ze de licentie accepteren of mislukt de bewerking.

## <a name="publish-requirements-for-modules"></a>Publicatie vereisten voor modules

Aan de volgende vereisten moet worden voldaan aan de modules die gebruikers nodig hebben om de licentie te accepteren:

- De sectie PSData van module manifest moet RequireLicenseAcceptance = $True bevatten.
- De module moet een License. txt-bestand in de hoofdmap bevatten.
- Module manifest moet licentie-URI bevatten.
- De module moet worden gepubliceerd met PowerShellGet-indeling versie 2,0 en hoger.

## <a name="impact-on-installsaveupdate-module"></a>Gevolgen voor installeren/opslaan/bijwerken-module

- Install/Save/update-cmdlets ondersteunen een nieuwe para meter – AcceptLicense die zich gedraagt alsof de gebruiker de licentie heeft gezien.
- Als RequiredLicenseAcceptance is ingesteld op True en – AcceptLicense niet is opgegeven, wordt de gebruiker de licentie. txt weer gegeven en wordt u gevraagd om het volgende te doen: &quot;Gaat u akkoord met deze licentie voorwaarden (Ja/Nee/YesToAll/NoToAll&quot;).
  - Als de licentie is geaccepteerd
    - **Save-module:** de module wordt naar het systeem van de&#39;gebruiker gekopieerd
    - **Install-module:** de module wordt naar het systeem van de&#39;gebruiker gekopieerd naar de juiste map (op basis van het bereik)
    - **Update-module:** de module wordt bijgewerkt.
  - Als de licentie wordt afgewezen.
    - De bewerking wordt geannuleerd.
    - Alle cmdlets controleren op de meta gegevens (requireLicenseAcceptance en indelings versie) die aangeeft dat een acceptatie van de licentie is vereist
    - Als de indelings versie van de client ouder is dan 2,0, mislukt de bewerking en wordt de gebruiker gevraagd om de client bij te werken.
    - Als de module is gepubliceerd met een indelings versie ouder dan 2,0, wordt de vlag requireLicenseAcceptance genegeerd.

## <a name="module-dependencies"></a>Module-afhankelijkheden

- Als in een afhankelijke module (iets anders is afhankelijk van de module) tijdens de installatie/het opslaan/bijwerken van de acceptatie van de licentie vereist is, wordt het acceptatie gedrag van de licentie (hierboven) vereist.
- Als de module versie al in de lokale catalogus wordt weer gegeven als op het systeem wordt geïnstalleerd, wordt de licentie controle omzeild.
- Als er tijdens het installeren/opslaan/bijwerken van een afhankelijke module een licentie is vereist en de licentie acceptatie niet plaatsvindt, zal de bewerking mislukken en worden de normale processen voor het pakket niet geïnstalleerd/opgeslagen/bijgewerkt.

## <a name="impact-on--force"></a>Impact op Force

Opgeven `–Force` is niet voldoende om een licentie te accepteren. `–AcceptLicense`is vereist voor de installatie van. Als `–Force` is opgegeven, RequiredLicenseAcceptance True is en `–AcceptLicense` niet is opgegeven, mislukt de bewerking.

## <a name="examples"></a>VINDT

### <a name="example-1-update-module-manifest-to-require-license-acceptance"></a>Voorbeeld 1: Module manifest bijwerken om acceptatie van licenties te vereisen

```powershell
Update-ModuleManifest -Path C:\modulemanifest.psd1 -RequireLicenseAcceptance -PrivateData @{
    PSData = @{
        # Flag to indicate whether the module requires explicit user acceptance
        RequireLicenseAcceptance = $true
    } # End of PSData hashtable

 } # End of PrivateData hashtable
```

Met deze opdracht wordt het manifest bestand bijgewerkt en wordt de RequireLicenseAcceptance-vlag ingesteld op True.

### <a name="example-2-install-module-requiring-license-acceptance"></a>Voor beeld 2: Installatie module waarvoor licentie acceptatie is vereist

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

Met deze opdracht wordt de licentie van het bestand License. txt weer gegeven en wordt de gebruiker gevraagd om de licentie te accepteren.

### <a name="example-3-install-module-requiring-license-acceptance-with--acceptlicense"></a>Voor beeld 3: Installatie module waarvoor licentie acceptatie is vereist met-AcceptLicense

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

De module wordt geïnstalleerd zonder dat u wordt gevraagd om een licentie te accepteren.

### <a name="example-4-install-module-requiring-license-acceptance-with--force"></a>Voor beeld 4: Installatie module waarvoor licentie acceptatie is vereist met-Force

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

### <a name="example-5-install-module-with-dependencies-requiring-license-acceptance"></a>Voor beeld 5: Module installeren met afhankelijkheden waarvoor acceptatie van licenties is vereist

Module ' ModuleWithDependency ' is afhankelijk van de module ' ModuleRequireLicenseAcceptance '. De gebruiker wordt gevraagd de licentie te accepteren.

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

### <a name="example-6-install-module-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Voor beeld 6: Module installeren met afhankelijkheden waarvoor acceptatie van licenties en AcceptLicense is vereist

Module ' ModuleWithDependency ' is afhankelijk van de module ' ModuleRequireLicenseAcceptance '. De gebruiker wordt niet gevraagd om de licentie te accepteren als-AcceptLicense is opgegeven.

```powershell
Install-Module -Name ModuleWithDependency -AcceptLicense
```

### <a name="example-7-install-module-requiring-license-acceptance-on-a-client-older-than-psgetformatversion-20"></a>Voor beeld 7: Installatie module waarvoor acceptatie van licenties is vereist voor een client die ouder is dan PSGetFormatVersion 2,0

```powershell
Install-Module -Name ModuleRequireLicenseAcceptance
```

```output
WARNING: The specified module 'ModuleRequireLicenseAcceptance' with PowerShellGetFormatVersion '2.0' is not supported by the current version of PowerShellGet. Get the latest version of the PowerShellGet module to install this module, 'ModuleRequireLicenseAcceptance'.
```

### <a name="example-8-save-module-requiring-license-acceptance"></a>Voor beeld 8: Module opslaan waarvoor acceptatie van de licentie is vereist

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

Met deze opdracht wordt de licentie van het bestand License. txt weer gegeven en wordt de gebruiker gevraagd om de licentie te accepteren.

### <a name="example-9-save-module-requiring-license-acceptance-with--acceptlicense"></a>Voor beeld 9: Module opslaan waarvoor licentie acceptatie is vereist met-AcceptLicense

```powershell
Save-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense -Path C:\Saved
```

De module wordt opgeslagen zonder dat u wordt gevraagd om de licentie te accepteren.

### <a name="example-10-update-module-requiring-license-acceptance"></a>Voor beeld 10: Update module waarvoor licentie acceptatie is vereist

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

Met deze opdracht wordt de licentie van het bestand License. txt weer gegeven en wordt de gebruiker gevraagd om de licentie te accepteren.

### <a name="example-11-update-module-requiring-license-acceptance-with--acceptlicense"></a>Voor beeld 11: Update module waarvoor licentie acceptatie is vereist met-AcceptLicense

```powershell
Update-Module -Name ModuleRequireLicenseAcceptance -AcceptLicense
```

De module wordt bijgewerkt zonder dat u wordt gevraagd om een licentie te accepteren.

## <a name="more-details"></a>Meer Details

[Acceptatie van de licentie vereisen voor scripts](./script-license-acceptance.md)

[Ondersteuning voor acceptatie van licenties vereisen op PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)

[Acceptatie van de licentie vereisen bij implementeren naar Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
