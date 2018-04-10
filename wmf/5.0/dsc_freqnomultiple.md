---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequenties voor RefreshMode en ConfigurationMode hoeven niet veelvouden van elkaar

In de vorige versie van DSC de LCM zou behandelen `RefreshFrequencyMins` en `ConfigurationModeFrequencyMins` als veelvouden van elkaar. In het WMF 5.0 RTM, worden deze eigenschappen onafhankelijk van elkaar verwerkt.

Zie voor meer informatie [configureren van de lokale Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).