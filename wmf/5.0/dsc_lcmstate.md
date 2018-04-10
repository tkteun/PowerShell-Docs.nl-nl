---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>Gedetailleerde informatie over LCM status

Er zijn verbeteringen aangebracht in de gegevens over de status LCM blootstellen. De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

Ook hebben we een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.