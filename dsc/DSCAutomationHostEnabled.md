---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="327c6-103">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="327c6-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="327c6-104">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="327c6-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="327c6-105">Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** waarmee de configuratie van de computer na de initiële boot-up.</span><span class="sxs-lookup"><span data-stu-id="327c6-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="327c6-106">DSCAutomationHostEnabled ondersteunt drie beschikbare modi:</span><span class="sxs-lookup"><span data-stu-id="327c6-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="327c6-107">DSCAutomationHostEnabled waarde</span><span class="sxs-lookup"><span data-stu-id="327c6-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="327c6-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="327c6-108">Description</span></span>   |
|---|---|
<span data-ttu-id="327c6-109">0</span><span class="sxs-lookup"><span data-stu-id="327c6-109">0</span></span> | <span data-ttu-id="327c6-110">Schakel de computer bij opstartprocedure te configureren.</span><span class="sxs-lookup"><span data-stu-id="327c6-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="327c6-111">1</span><span class="sxs-lookup"><span data-stu-id="327c6-111">1</span></span> | <span data-ttu-id="327c6-112">Schakel de computer bij opstartprocedure te configureren.</span><span class="sxs-lookup"><span data-stu-id="327c6-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="327c6-113">2</span><span class="sxs-lookup"><span data-stu-id="327c6-113">2</span></span> | <span data-ttu-id="327c6-114">Configureren van de machine als DSC in inschakelen in behandeling of de huidige status.</span><span class="sxs-lookup"><span data-stu-id="327c6-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="327c6-115">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="327c6-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="327c6-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="327c6-116">See Also</span></span>

<span data-ttu-id="327c6-117">Zie voor een voorbeeld van het gebruik van deze functie configuraties op initiële boot-up wordt uitgevoerd, [een virtuele machines op de eerste boot-up configureren met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="327c6-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>