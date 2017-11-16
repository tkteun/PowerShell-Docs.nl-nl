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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="2118c-102">Gedetailleerde informatie over LCM status</span><span class="sxs-lookup"><span data-stu-id="2118c-102">Detailed information about LCM state</span></span>

<span data-ttu-id="2118c-103">Er zijn verbeteringen aangebracht in de gegevens over de status LCM blootstellen.</span><span class="sxs-lookup"><span data-stu-id="2118c-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="2118c-104">De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:</span><span class="sxs-lookup"><span data-stu-id="2118c-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="2118c-105">**Inactief**</span><span class="sxs-lookup"><span data-stu-id="2118c-105">**Idle**</span></span>
* <span data-ttu-id="2118c-106">**Bezet**</span><span class="sxs-lookup"><span data-stu-id="2118c-106">**Busy**</span></span>
* <span data-ttu-id="2118c-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="2118c-107">**PendingReboot**</span></span>
* <span data-ttu-id="2118c-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="2118c-108">**PendingConfiguration**</span></span>

<span data-ttu-id="2118c-109">Ook hebben we een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2118c-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

