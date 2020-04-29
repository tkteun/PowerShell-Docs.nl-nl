---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Acceptatie van de licentie vereisen voor scripts
ms.openlocfilehash: e7101eb6a480dd87965b7b9be9d49583042b603f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328894"
---
# <a name="requiring-license-acceptance-for-scripts"></a>Acceptatie van de licentie vereisen voor scripts

Acceptatie van licenties wordt niet ondersteund voor scripts. Het scenario waarbij een script afhankelijk is van een module waarvoor acceptatie van licenties vereist is, wordt echter wel ondersteund.

Script opdrachten (install-script/Save-script/update-script) ondersteunen een nieuwe para meter-AcceptLicense die zich gedraagt alsof de gebruiker de licentie heeft gezien. If-AcceptLicense is niet opgegeven. de gebruiker krijgt de licentie. txt voor de afhankelijke module te zien en u wordt gevraagd de licentie te accepteren.

## <a name="examples"></a>VOORBEELDEN

### <a name="example-1-install-script-with-dependencies-requiring-license-acceptance"></a>Voor beeld 1: script installeren met afhankelijkheden waarvoor licentie acceptatie is vereist

Het script ScriptRequireLicenseAcceptance is afhankelijk van de module ModuleRequireLicenseAcceptance. De gebruiker wordt gevraagd de licentie te accepteren.

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

### <a name="example-2-install-script-with-dependencies-requiring-license-acceptance-and--acceptlicense"></a>Voor beeld 2: script installeren met afhankelijkheden waarvoor acceptatie van licenties is vereist en-AcceptLicense

Het script ScriptRequireLicenseAcceptance is afhankelijk van de module ModuleRequireLicenseAcceptance. De gebruiker wordt niet gevraagd om de licentie te accepteren als-AcceptLicense is opgegeven.

```PowerShell
PS> Install-Script -Name ScriptRequireLicenseAcceptance -AcceptLicense
```

## <a name="more-details"></a>Meer informatie

- [Ondersteuning van acceptatie van licenties voor modules vereisen](module-license-acceptance.md)
- [Ondersteuning voor acceptatie van licenties vereisen op PowerShellGallery](../how-to/working-with-packages/packages-that-require-license-acceptance.md)
- [Acceptatie van de licentie vereisen bij implementeren naar Azure Automation](../how-to/working-with-packages/deploy-to-azure-automation.md)
