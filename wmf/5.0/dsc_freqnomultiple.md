---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058400"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="736fb-102">Frequenties voor RefreshMode en ConfigurationMode hoeft te worden veelvouden van elkaar worden verbonden</span><span class="sxs-lookup"><span data-stu-id="736fb-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="736fb-103">In de vorige versie van DSC, de LCM zou behandelen `RefreshFrequencyMins` en `ConfigurationModeFrequencyMins` als veelvouden van elkaar.</span><span class="sxs-lookup"><span data-stu-id="736fb-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="736fb-104">In WMF 5.0 RTM, worden deze eigenschappen verwerkt onafhankelijk van elkaar.</span><span class="sxs-lookup"><span data-stu-id="736fb-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="736fb-105">Zie voor meer informatie, [de Local Configuration Manager configureren](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="736fb-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
