---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688201"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frequenties voor RefreshMode en ConfigurationMode hoeft te worden veelvouden van elkaar worden verbonden

In de vorige versie van DSC, de LCM zou behandelen `RefreshFrequencyMins` en `ConfigurationModeFrequencyMins` als veelvouden van elkaar. In WMF 5.0 RTM, worden deze eigenschappen verwerkt onafhankelijk van elkaar.

Zie voor meer informatie, [de Local Configuration Manager configureren](https://msdn.microsoft.com/powershell/dsc/metaconfig).
