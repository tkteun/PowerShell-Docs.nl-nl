---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: 0f35a798e5b7d51fdfb66e4e79ceab0e36ccea5b
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808330"
---
# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="75113-103">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="75113-103">DSCAutomationHostEnabled registry key</span></span>

> <span data-ttu-id="75113-104">Van toepassing op: Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="75113-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="75113-105">DSC maakt gebruik van de register sleutel **DSCAutomationHostEnabled** onder **HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\Policies\System** om de configuratie van de machine bij de eerste keer opstarten in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="75113-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="75113-106">**DSCAutomationHostEnabled** ondersteunt drie modi:</span><span class="sxs-lookup"><span data-stu-id="75113-106">**DSCAutomationHostEnabled** supports three modes:</span></span>

|  <span data-ttu-id="75113-107">Waarde DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="75113-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="75113-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="75113-108">Description</span></span>   |
|---|---|
<span data-ttu-id="75113-109">0</span><span class="sxs-lookup"><span data-stu-id="75113-109">0</span></span> | <span data-ttu-id="75113-110">Het configureren van de machine bij het opstarten uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="75113-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="75113-111">1</span><span class="sxs-lookup"><span data-stu-id="75113-111">1</span></span> | <span data-ttu-id="75113-112">Het configureren van de machine bij het opstarten inschakelen.</span><span class="sxs-lookup"><span data-stu-id="75113-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="75113-113">2</span><span class="sxs-lookup"><span data-stu-id="75113-113">2</span></span> | <span data-ttu-id="75113-114">Schakel het configureren van de computer alleen in als DSC de status in behandeling of actueel heeft.</span><span class="sxs-lookup"><span data-stu-id="75113-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="75113-115">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="75113-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="75113-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75113-116">See Also</span></span>

<span data-ttu-id="75113-117">Voor een voor beeld van hoe u deze functie kunt gebruiken om configuraties uit te voeren bij de eerste keer opstarten, raadpleegt u [een virtuele machine configureren bij de eerste keer opstarten met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="75113-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>
