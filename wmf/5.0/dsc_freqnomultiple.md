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
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="85799-102">Frequenties voor RefreshMode en ConfigurationMode hoeven niet veelvouden van elkaar</span><span class="sxs-lookup"><span data-stu-id="85799-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="85799-103">In de vorige versie van DSC de LCM zou behandelen `RefreshFrequencyMins` en `ConfigurationModeFrequencyMins` als veelvouden van elkaar.</span><span class="sxs-lookup"><span data-stu-id="85799-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="85799-104">In het WMF 5.0 RTM, worden deze eigenschappen onafhankelijk van elkaar verwerkt.</span><span class="sxs-lookup"><span data-stu-id="85799-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="85799-105">Zie voor meer informatie [configureren van de lokale Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="85799-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
