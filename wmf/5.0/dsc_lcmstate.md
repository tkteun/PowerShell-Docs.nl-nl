---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="detailed-information-about-lcm-state"></a>Gedetailleerde informatie over LCM status

Er zijn verbeteringen aangebracht in de gegevens over de status LCM blootstellen. De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:

* **Inactief**
* **Bezet**
* **PendingReboot**
* **PendingConfiguration**

Ook hebben we een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.
