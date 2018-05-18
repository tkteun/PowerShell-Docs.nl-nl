---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 0cecbadc6802938cadb4ffb9745a23e6b98544be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
><span data-ttu-id="859e2-103">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="859e2-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="859e2-104">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="859e2-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="859e2-105">Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** waarmee de configuratie van de computer na de initiële boot-up.</span><span class="sxs-lookup"><span data-stu-id="859e2-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="859e2-106">DSCAutomationHostEnabled ondersteunt drie beschikbare modi:</span><span class="sxs-lookup"><span data-stu-id="859e2-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="859e2-107">DSCAutomationHostEnabled waarde</span><span class="sxs-lookup"><span data-stu-id="859e2-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="859e2-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="859e2-108">Description</span></span>   |
|---|---|
<span data-ttu-id="859e2-109">0</span><span class="sxs-lookup"><span data-stu-id="859e2-109">0</span></span> | <span data-ttu-id="859e2-110">Schakel de computer bij opstartprocedure te configureren.</span><span class="sxs-lookup"><span data-stu-id="859e2-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="859e2-111">1</span><span class="sxs-lookup"><span data-stu-id="859e2-111">1</span></span> | <span data-ttu-id="859e2-112">Schakel de computer bij opstartprocedure te configureren.</span><span class="sxs-lookup"><span data-stu-id="859e2-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="859e2-113">2</span><span class="sxs-lookup"><span data-stu-id="859e2-113">2</span></span> | <span data-ttu-id="859e2-114">Configureren van de machine als DSC in inschakelen in behandeling of de huidige status.</span><span class="sxs-lookup"><span data-stu-id="859e2-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="859e2-115">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="859e2-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="859e2-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="859e2-116">See Also</span></span>

<span data-ttu-id="859e2-117">Zie voor een voorbeeld van het gebruik van deze functie configuraties op initiële boot-up wordt uitgevoerd, [een virtuele machines op de eerste boot-up configureren met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="859e2-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>