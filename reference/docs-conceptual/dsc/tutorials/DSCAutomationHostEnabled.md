---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: De registersleutel DSCAutomationHostEnabled
description: In dit artikel worden de waarden gedefinieerd die kunnen worden ingesteld in de register sleutel DSCAutomationHostEnabled
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656182"
---
# <a name="dscautomationhostenabled-registry-key"></a>De registersleutel DSCAutomationHostEnabled

> Van toepassing op: Windows Power shell 5,0

DSC maakt gebruik van de register sleutel **DSCAutomationHostEnabled** onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** om de configuratie van de machine bij de eerste keer opstarten in te scha kelen. **DSCAutomationHostEnabled** ondersteunt drie modi:

| Waarde DSCAutomationHostEnabled |                                              Beschrijving                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| 0                              | Het configureren van de machine bij het opstarten uitschakelen.                                                           |
| 1                              | Het configureren van de machine bij het opstarten inschakelen.                                                            |
| 2                              | Schakel het configureren van de computer alleen in als DSC de status in behandeling of actueel heeft. Dit is de standaardwaarde. |

## <a name="see-also"></a>Zie ook

Voor een voor beeld van hoe u deze functie kunt gebruiken om configuraties uit te voeren bij de eerste keer opstarten, raadpleegt u [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).
