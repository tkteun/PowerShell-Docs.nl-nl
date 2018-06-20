---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219858"
---
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="00ef7-102">Gedetailleerde informatie over LCM status</span><span class="sxs-lookup"><span data-stu-id="00ef7-102">Detailed information about LCM state</span></span>

<span data-ttu-id="00ef7-103">Er zijn verbeteringen aangebracht in de gegevens over de status LCM blootstellen.</span><span class="sxs-lookup"><span data-stu-id="00ef7-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="00ef7-104">De LCMState die wordt geretourneerd door Get-DscLocalConfigurationManager kan nu de volgende waarden bevatten:</span><span class="sxs-lookup"><span data-stu-id="00ef7-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="00ef7-105">**Inactief**</span><span class="sxs-lookup"><span data-stu-id="00ef7-105">**Idle**</span></span>
* <span data-ttu-id="00ef7-106">**Bezet**</span><span class="sxs-lookup"><span data-stu-id="00ef7-106">**Busy**</span></span>
* <span data-ttu-id="00ef7-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="00ef7-107">**PendingReboot**</span></span>
* <span data-ttu-id="00ef7-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="00ef7-108">**PendingConfiguration**</span></span>

<span data-ttu-id="00ef7-109">Ook hebben we een LCMStateDetail-eigenschap die meer informatie over de status bevat toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="00ef7-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
