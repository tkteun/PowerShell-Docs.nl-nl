---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a>Gedetailleerde informatie over LCM status

Er zijn verbeteringen aangebracht in de gegevens over de status LCM blootstellen. De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:

* **Inactief**
* **Bezet**
* **PendingReboot**
* **PendingConfiguration**

Ook hebben we een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.

