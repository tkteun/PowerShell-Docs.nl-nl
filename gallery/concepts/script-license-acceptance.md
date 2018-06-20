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
# <a name="requiring-license-acceptance-for-scripts"></a>Het vereisen van instemming van de licentie voor scripts

Acceptatie van de licentie wordt niet ondersteund voor scripts. Het scenario waarbij een script is afhankelijk van een module die vereist dat de acceptatie van de licentie wordt echter ondersteund.

Script commands(Install-Script/Save-Script/Update-Script) ondersteunen een nieuwe parameter - AcceptLicense dat zich gedraagt alsof de gebruiker de licentievoorwaarden hebt gezien. Als niet - AcceptLicense is opgegeven; de gebruiker wordt license.txt voor afhankelijke module weergegeven en wordt gevraagd of u de licentievoorwaarden accepteert.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Voorbeeld 1: Installatiescript met afhankelijkheden vereisen van instemming met licentie

Script 'ScriptRequireLicenseAcceptance', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'. Gebruiker wordt gevraagd om een licentie accepteren.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Voorbeeld 2: Installatiescript met afhankelijkheden licentie acceptatie en -AcceptLicense vereisen

Script 'ScriptRequireLicenseAcceptance', is afhankelijk van de module 'ModuleRequireLicenseAcceptance'. Gebruiker niet gevraagd licentie accepteren omdat - AcceptLicense is opgegeven.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>meer informatie

- [Acceptatie van de licentie-ondersteuning vereist voor Modules](module-license-acceptance.md)
- [Acceptatie van de licentie-ondersteuning op PowerShellGallery vereist](../how-to/working-with-items/items-that-require-license-acceptance.md)
- [Acceptatie van de licentie vereisen bij implementeren naar Azure Automation](../how-to/working-with-items/deploy-to-azure-automation.md)