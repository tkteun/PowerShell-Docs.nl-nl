---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De registersleutel DSCAutomationHostEnabled
ms.openlocfilehash: e47c929b366f93738343eabc431aab5a4428352d
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="44f63-103">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="44f63-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="44f63-104">De registersleutel DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="44f63-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="44f63-105">Maakt gebruik van DSC de **DSCAutomationHostEnabled** registersleutel onder **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** waarmee de configuratie van de computer na de initiële boot-up.</span><span class="sxs-lookup"><span data-stu-id="44f63-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="44f63-106">DSCAutomationHostEnabled ondersteunt drie beschikbare modi:</span><span class="sxs-lookup"><span data-stu-id="44f63-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="44f63-107">DSCAutomationHostEnabled waarde</span><span class="sxs-lookup"><span data-stu-id="44f63-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="44f63-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="44f63-108">Description</span></span>   | 
|---|---| 
<span data-ttu-id="44f63-109">0</span><span class="sxs-lookup"><span data-stu-id="44f63-109">0</span></span> | <span data-ttu-id="44f63-110">Schakel de computer bij opstartprocedure te configureren.</span><span class="sxs-lookup"><span data-stu-id="44f63-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="44f63-111">1</span><span class="sxs-lookup"><span data-stu-id="44f63-111">1</span></span> | <span data-ttu-id="44f63-112">Schakel de computer bij opstartprocedure te configureren.</span><span class="sxs-lookup"><span data-stu-id="44f63-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="44f63-113">2</span><span class="sxs-lookup"><span data-stu-id="44f63-113">2</span></span> | <span data-ttu-id="44f63-114">Configureren van de machine als DSC in inschakelen in behandeling of de huidige status.</span><span class="sxs-lookup"><span data-stu-id="44f63-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="44f63-115">Dit is de standaardwaarde.</span><span class="sxs-lookup"><span data-stu-id="44f63-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="44f63-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="44f63-116">See Also</span></span>

<span data-ttu-id="44f63-117">Zie voor een voorbeeld van het gebruik van deze functie configuraties op initiële boot-up wordt uitgevoerd, [een virtuele machines op de eerste boot-up configureren met behulp van DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="44f63-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>


