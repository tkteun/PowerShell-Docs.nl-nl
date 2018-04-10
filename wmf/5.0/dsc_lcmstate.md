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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="fdced-102">Gedetailleerde informatie over LCM status</span><span class="sxs-lookup"><span data-stu-id="fdced-102">Detailed information about LCM state</span></span>

<span data-ttu-id="fdced-103">Er zijn verbeteringen aangebracht in de gegevens over de status LCM blootstellen.</span><span class="sxs-lookup"><span data-stu-id="fdced-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="fdced-104">De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:</span><span class="sxs-lookup"><span data-stu-id="fdced-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="fdced-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="fdced-105">**Idle**</span></span>
* <span data-ttu-id="fdced-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="fdced-106">**Busy**</span></span>
* <span data-ttu-id="fdced-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="fdced-107">**PendingReboot**</span></span>
* <span data-ttu-id="fdced-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="fdced-108">**PendingConfiguration**</span></span>

<span data-ttu-id="fdced-109">Ook hebben we een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fdced-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>