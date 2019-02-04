---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684799"
---
><span data-ttu-id="e17c3-103">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e17c3-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="e17c3-104">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="e17c3-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="e17c3-105">Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** om in te schakelen van de configuratie van de machine op de eerste Start-up.</span><span class="sxs-lookup"><span data-stu-id="e17c3-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="e17c3-106">**DSCAutomationHostEnabled** ondersteunt drie modi:</span><span class="sxs-lookup"><span data-stu-id="e17c3-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="e17c3-107">DSCAutomationHostEnabled waarde</span><span class="sxs-lookup"><span data-stu-id="e17c3-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="e17c3-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e17c3-108">Description</span></span>   |
|---|---|
<span data-ttu-id="e17c3-109">0</span><span class="sxs-lookup"><span data-stu-id="e17c3-109">0</span></span> | <span data-ttu-id="e17c3-110">Configureren van de machine bij de keer opstarten uitschakelen</span><span class="sxs-lookup"><span data-stu-id="e17c3-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="e17c3-111">1</span><span class="sxs-lookup"><span data-stu-id="e17c3-111">1</span></span> | <span data-ttu-id="e17c3-112">Configureren van de machine bij de keer opstarten inschakelen</span><span class="sxs-lookup"><span data-stu-id="e17c3-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="e17c3-113">2</span><span class="sxs-lookup"><span data-stu-id="e17c3-113">2</span></span> | <span data-ttu-id="e17c3-114">Configureren van de machine als DSC in inschakelen in behandeling of de huidige status.</span><span class="sxs-lookup"><span data-stu-id="e17c3-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="e17c3-115">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="e17c3-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="e17c3-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e17c3-116">See Also</span></span>

<span data-ttu-id="e17c3-117">Zie voor een voorbeeld van hoe u deze functie wilt gebruiken om uit te voeren van configuraties bij de eerste keer opstarten [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="e17c3-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
