---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076471"
---
>Van toepassing op: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>De registersleutel DSCAutomationHostEnabled

Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** om in te schakelen van de configuratie van de machine op de eerste Start-up.
**DSCAutomationHostEnabled** ondersteunt drie modi:

|  DSCAutomationHostEnabled waarde  |  Description   |
|---|---|
0 | Configureren van de machine bij de keer opstarten uitschakelen |
1 | Configureren van de machine bij de keer opstarten inschakelen |
2 | Configureren van de machine als DSC in inschakelen in behandeling of de huidige status. Dit is de standaardwaarde. |

## <a name="see-also"></a>Zie ook

Zie voor een voorbeeld van hoe u deze functie wilt gebruiken om uit te voeren van configuraties bij de eerste keer opstarten [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).
