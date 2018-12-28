---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 38e3189323c39a522b2ccad89f5cfcadf5e45616
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403899"
---
><span data-ttu-id="751b8-103">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="751b8-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="751b8-104">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="751b8-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="751b8-105">Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** om in te schakelen van de configuratie van de machine bij de eerste keer opstarten.</span><span class="sxs-lookup"><span data-stu-id="751b8-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="751b8-106">DSCAutomationHostEnabled ondersteunt drie modi:</span><span class="sxs-lookup"><span data-stu-id="751b8-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="751b8-107">DSCAutomationHostEnabled waarde</span><span class="sxs-lookup"><span data-stu-id="751b8-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="751b8-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="751b8-108">Description</span></span>   |
|---|---|
<span data-ttu-id="751b8-109">0</span><span class="sxs-lookup"><span data-stu-id="751b8-109">0</span></span> | <span data-ttu-id="751b8-110">Configureren van de machine bij de keer opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="751b8-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="751b8-111">1</span><span class="sxs-lookup"><span data-stu-id="751b8-111">1</span></span> | <span data-ttu-id="751b8-112">Configureren van de machine bij de keer opstarten inschakelen</span><span class="sxs-lookup"><span data-stu-id="751b8-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="751b8-113">2</span><span class="sxs-lookup"><span data-stu-id="751b8-113">2</span></span> | <span data-ttu-id="751b8-114">Configureren van de machine als DSC in inschakelen in behandeling of de huidige status.</span><span class="sxs-lookup"><span data-stu-id="751b8-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="751b8-115">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="751b8-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="751b8-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="751b8-116">See Also</span></span>

<span data-ttu-id="751b8-117">Zie voor een voorbeeld van hoe u deze functie wilt gebruiken om uit te voeren van configuraties bij de eerste keer opstarten [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="751b8-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>