---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685744"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="6cf47-102">Gedetailleerde informatie over LCM-status</span><span class="sxs-lookup"><span data-stu-id="6cf47-102">Detailed information about LCM state</span></span>

<span data-ttu-id="6cf47-103">We hebben verbeteringen aangebracht in het weergeven van informatie over LCM-status.</span><span class="sxs-lookup"><span data-stu-id="6cf47-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="6cf47-104">De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:</span><span class="sxs-lookup"><span data-stu-id="6cf47-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="6cf47-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="6cf47-105">**Idle**</span></span>
* <span data-ttu-id="6cf47-106">**Bezig**</span><span class="sxs-lookup"><span data-stu-id="6cf47-106">**Busy**</span></span>
* <span data-ttu-id="6cf47-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="6cf47-107">**PendingReboot**</span></span>
* <span data-ttu-id="6cf47-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="6cf47-108">**PendingConfiguration**</span></span>

<span data-ttu-id="6cf47-109">We hebben ook een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="6cf47-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
