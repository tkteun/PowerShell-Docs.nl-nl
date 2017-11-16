---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="10204-102">Frequenties voor RefreshMode en ConfigurationMode hoeven niet veelvouden van elkaar</span><span class="sxs-lookup"><span data-stu-id="10204-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="10204-103">In de vorige versie van DSC de LCM zou behandelen `RefreshFrequencyMins` en `ConfigurationModeFrequencyMins` als veelvouden van elkaar.</span><span class="sxs-lookup"><span data-stu-id="10204-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="10204-104">In het WMF 5.0 RTM, worden deze eigenschappen onafhankelijk van elkaar verwerkt.</span><span class="sxs-lookup"><span data-stu-id="10204-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span> 

<span data-ttu-id="10204-105">Zie voor meer informatie [configureren van de lokale Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="10204-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>

