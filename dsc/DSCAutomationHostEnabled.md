---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
>Van toepassing op: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>De registersleutel DSCAutomationHostEnabled

Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** waarmee de configuratie van de computer na de initiële boot-up.
DSCAutomationHostEnabled ondersteunt drie beschikbare modi:

|  DSCAutomationHostEnabled waarde  |  Beschrijving   |
|---|---|
0 | Schakel de computer bij opstartprocedure te configureren. |
1 | Schakel de computer bij opstartprocedure te configureren. |
2 | Configureren van de machine als DSC in inschakelen in behandeling of de huidige status. Dit is de standaardwaarde. |

## <a name="see-also"></a>Zie ook

Zie voor een voorbeeld van het gebruik van deze functie configuraties op initiële boot-up wordt uitgevoerd, [een virtuele machines op de eerste boot-up configureren met behulp van DSC](bootstrapDsc.md).