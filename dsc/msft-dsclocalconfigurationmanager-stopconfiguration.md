---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dadb6912af2e4450381958ed465799056da49946
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4b3f3-103">De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4b3f3-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4b3f3-104">Stopt het wijzigen van de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4b3f3-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="4b3f3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4b3f3-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="4b3f3-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="4b3f3-106">Parameters</span></span>
----------

<span data-ttu-id="4b3f3-107">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="4b3f3-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4b3f3-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="4b3f3-108">Return value</span></span>
------------

<span data-ttu-id="4b3f3-109">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="4b3f3-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4b3f3-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4b3f3-110">Remarks</span></span>

<span data-ttu-id="4b3f3-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="4b3f3-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b3f3-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4b3f3-112">Requirements</span></span>
------------
><span data-ttu-id="4b3f3-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4b3f3-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4b3f3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4b3f3-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4b3f3-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4b3f3-115">See also</span></span>


[<span data-ttu-id="4b3f3-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4b3f3-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)