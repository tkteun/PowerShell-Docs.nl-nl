---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218872"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="79868-103">De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="79868-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="79868-104">Stopt het wijzigen van de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="79868-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="79868-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="79868-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="79868-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="79868-106">Parameters</span></span>
----------

<span data-ttu-id="79868-107">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="79868-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="79868-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="79868-108">Return value</span></span>
------------

<span data-ttu-id="79868-109">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="79868-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="79868-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="79868-110">Remarks</span></span>

<span data-ttu-id="79868-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="79868-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="79868-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="79868-112">Requirements</span></span>
------------
><span data-ttu-id="79868-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="79868-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="79868-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="79868-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="79868-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="79868-115">See also</span></span>


[<span data-ttu-id="79868-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="79868-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)