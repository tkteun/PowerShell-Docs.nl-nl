---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685744"
---
# <a name="detailed-information-about-lcm-state"></a>Gedetailleerde informatie over LCM-status

We hebben verbeteringen aangebracht in het weergeven van informatie over LCM-status. De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:

* **Idle**
* **Bezig**
* **PendingReboot**
* **PendingConfiguration**

We hebben ook een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.
