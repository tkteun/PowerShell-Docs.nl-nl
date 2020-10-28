---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: De registersleutel DSCAutomationHostEnabled
description: In dit artikel worden de waarden gedefinieerd die kunnen worden ingesteld in de register sleutel DSCAutomationHostEnabled
ms.openlocfilehash: 50f752dd882e9b0787ed4a4cbc22731fc1d608f5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656182"
---
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="657bf-104">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="657bf-104">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="657bf-105">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="657bf-105">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="657bf-106">DSC maakt gebruik van de register sleutel **DSCAutomationHostEnabled** onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** om de configuratie van de machine bij de eerste keer opstarten in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="657bf-106">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span> <span data-ttu-id="657bf-107">**DSCAutomationHostEnabled** ondersteunt drie modi:</span><span class="sxs-lookup"><span data-stu-id="657bf-107">**DSCAutomationHostEnabled** supports three modes:</span></span>

| <span data-ttu-id="657bf-108">Waarde DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="657bf-108">DSCAutomationHostEnabled Value</span></span> |                                              <span data-ttu-id="657bf-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="657bf-109">Description</span></span>                                              |
| ------------------------------ | ----------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="657bf-110">0</span><span class="sxs-lookup"><span data-stu-id="657bf-110">0</span></span>                              | <span data-ttu-id="657bf-111">Het configureren van de machine bij het opstarten uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="657bf-111">Disable configuring the machine at boot-up.</span></span>                                                           |
| <span data-ttu-id="657bf-112">1</span><span class="sxs-lookup"><span data-stu-id="657bf-112">1</span></span>                              | <span data-ttu-id="657bf-113">Het configureren van de machine bij het opstarten inschakelen.</span><span class="sxs-lookup"><span data-stu-id="657bf-113">Enable configuring the machine at boot-up.</span></span>                                                            |
| <span data-ttu-id="657bf-114">2</span><span class="sxs-lookup"><span data-stu-id="657bf-114">2</span></span>                              | <span data-ttu-id="657bf-115">Schakel het configureren van de computer alleen in als DSC de status in behandeling of actueel heeft.</span><span class="sxs-lookup"><span data-stu-id="657bf-115">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="657bf-116">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="657bf-116">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="657bf-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="657bf-117">See Also</span></span>

<span data-ttu-id="657bf-118">Voor een voor beeld van hoe u deze functie kunt gebruiken om configuraties uit te voeren bij de eerste keer opstarten, raadpleegt u [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="657bf-118">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
