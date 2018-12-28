---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403899"
---
>Van toepassing op: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>De registersleutel DSCAutomationHostEnabled

Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** om in te schakelen van de configuratie van de machine bij de eerste keer opstarten.
DSCAutomationHostEnabled ondersteunt drie modi:

|  DSCAutomationHostEnabled waarde  |  Beschrijving   |
|---|---|
0 | Configureren van de machine bij de keer opstarten uitschakelen |
1 | Configureren van de machine bij de keer opstarten inschakelen |
2 | Configureren van de machine als DSC in inschakelen in behandeling of de huidige status. Dit is de standaardwaarde. |

## <a name="see-also"></a>Zie ook

Zie voor een voorbeeld van hoe u deze functie wilt gebruiken om uit te voeren van configuraties bij de eerste keer opstarten [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).