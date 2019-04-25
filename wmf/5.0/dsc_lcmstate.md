---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085793"
---
# <a name="detailed-information-about-lcm-state"></a>Gedetailleerde informatie over LCM-status

We hebben verbeteringen aangebracht in het weergeven van informatie over LCM-status. De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:

* **Idle**
* **Bezig**
* **PendingReboot**
* **PendingConfiguration**

We hebben ook een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.
