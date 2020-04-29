---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942165"
---
>Van toepassing op: Windows Power shell 5,0

# <a name="dscautomationhostenabled-registry-key"></a>De registersleutel DSCAutomationHostEnabled

DSC maakt gebruik van de register sleutel **DSCAutomationHostEnabled** onder **HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\Policies\System** om de configuratie van de machine bij de eerste keer opstarten in te scha kelen.
**DSCAutomationHostEnabled** ondersteunt drie modi:

|  Waarde DSCAutomationHostEnabled  |  Beschrijving   |
|---|---|
0 | Het configureren van de machine bij het opstarten uitschakelen. |
1 | Het configureren van de machine bij het opstarten inschakelen. |
2 | Schakel het configureren van de computer alleen in als DSC de status in behandeling of actueel heeft. Dit is de standaardwaarde. |

## <a name="see-also"></a>Zie ook

Voor een voor beeld van hoe u deze functie kunt gebruiken om configuraties uit te voeren bij de eerste keer opstarten, raadpleegt u [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).
