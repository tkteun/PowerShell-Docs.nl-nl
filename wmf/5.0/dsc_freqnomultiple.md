---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218379"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequenties voor RefreshMode en ConfigurationMode hoeven niet veelvouden van elkaar

In de vorige versie van DSC de LCM zou behandelen `RefreshFrequencyMins` en `ConfigurationModeFrequencyMins` als veelvouden van elkaar. In het WMF 5.0 RTM, worden deze eigenschappen onafhankelijk van elkaar verwerkt.

Zie voor meer informatie [configureren van de lokale Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).
