---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 0f35a798e5b7d51fdfb66e4e79ceab0e36ccea5b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808330"
---
# <a name="dscautomationhostenabled-registry-key"></a>De registersleutel DSCAutomationHostEnabled

> Van toepassing op: Windows Power shell 5,0

DSC maakt gebruik van de register sleutel **DSCAutomationHostEnabled** onder **HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\Policies\System** om de configuratie van de machine bij de eerste keer opstarten in te scha kelen.
**DSCAutomationHostEnabled** ondersteunt drie modi:

|  Waarde DSCAutomationHostEnabled  |  Beschrijving   |
|---|---|
0 | Het configureren van de machine bij het opstarten uitschakelen. |
1 | Het configureren van de machine bij het opstarten inschakelen. |
2 | Schakel het configureren van de computer alleen in als DSC de status in behandeling of actueel heeft. Dit is de standaardwaarde. |

## <a name="see-also"></a>Zie ook

Voor een voor beeld van hoe u deze functie kunt gebruiken om configuraties uit te voeren bij de eerste keer opstarten, raadpleegt u [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).
