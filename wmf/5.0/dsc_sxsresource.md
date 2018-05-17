---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Side-By-Side Module Versioning ondersteuning voor DSC-Resources

Modules met DSC-resources kunnen worden geïnstalleerd side-by-side en DSC-configuraties kunt een specifieke versie van de resource die is geïnstalleerd op het systeem.

Zie voor meer informatie [door resources met meerdere versies](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Bekende problemen

In deze release Hier volgen enkele bekende problemen van side-by-side-installatie:

-   Met behulp van twee verschillende versies van de DSC-resource in dezelfde configuratie wordt niet ondersteund.
