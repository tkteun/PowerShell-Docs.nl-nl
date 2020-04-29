---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942165"
---
><span data-ttu-id="94510-103">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="94510-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="94510-104">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="94510-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="94510-105">DSC maakt gebruik van de register sleutel **DSCAutomationHostEnabled** onder **HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\Policies\System** om de configuratie van de machine bij de eerste keer opstarten in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="94510-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="94510-106">**DSCAutomationHostEnabled** ondersteunt drie modi:</span><span class="sxs-lookup"><span data-stu-id="94510-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="94510-107">Waarde DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="94510-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="94510-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="94510-108">Description</span></span>   |
|---|---|
<span data-ttu-id="94510-109">0</span><span class="sxs-lookup"><span data-stu-id="94510-109">0</span></span> | <span data-ttu-id="94510-110">Het configureren van de machine bij het opstarten uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="94510-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="94510-111">1</span><span class="sxs-lookup"><span data-stu-id="94510-111">1</span></span> | <span data-ttu-id="94510-112">Het configureren van de machine bij het opstarten inschakelen.</span><span class="sxs-lookup"><span data-stu-id="94510-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="94510-113">2</span><span class="sxs-lookup"><span data-stu-id="94510-113">2</span></span> | <span data-ttu-id="94510-114">Schakel het configureren van de computer alleen in als DSC de status in behandeling of actueel heeft.</span><span class="sxs-lookup"><span data-stu-id="94510-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="94510-115">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="94510-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="94510-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="94510-116">See Also</span></span>

<span data-ttu-id="94510-117">Voor een voor beeld van hoe u deze functie kunt gebruiken om configuraties uit te voeren bij de eerste keer opstarten, raadpleegt u [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="94510-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
