---
ms.date: 06/09/2017
schema: 2.0.0
keywords: PowerShell
title: Vereisen van instemming met licentie vereisen voor scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002579"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Vereisen van instemming met licentie vereisen voor scripts

Acceptatie van de licentie wordt niet ondersteund voor scripts. Het scenario waarbij een script afhankelijk is van een module die is vereist acceptatie van de licentie wordt echter ondersteund.

Script commands(Install-Script/Save-Script/Update-Script) ondersteuning voor een nieuwe parameter - AcceptLicense dat zich gedraagt alsof de gebruiker de licentie hebt gezien. Als de - AcceptLicense is niet opgegeven. de gebruiker wordt license.txt voor afhankelijke module weergegeven en u wordt gevraagd om de licentie te accepteren.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Voorbeeld 1: Installatiescript met afhankelijkheden die instemming met licentie vereisen

Script 'ScriptRequireLicenseAcceptance', is afhankelijk van module 'ModuleRequireLicenseAcceptance'. Gebruiker wordt gevraagd naar licentie accepteren.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Voorbeeld 2: Installatiescript met afhankelijkheden die instemming met licentie vereisen en -AcceptLicense vereisen

Script 'ScriptRequireLicenseAcceptance', is afhankelijk van module 'ModuleRequireLicenseAcceptance'. Gebruiker niet gevraagd om te accepteren van licentie - AcceptLicense is opgegeven.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Meer informatie

- [Ondersteuning voor acceptatie van de licentie vereisen voor Modules](module-license-acceptance.md)
- [Ondersteuning voor acceptatie van de licentie op PowerShellGallery vereisen](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Acceptatie van de licentie vereisen bij implementeren naar Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
