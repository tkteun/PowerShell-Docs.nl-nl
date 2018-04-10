---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9fe41fa806a6abff1d36dadd0c041a5cf0e78caf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="515f5-103">De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="515f5-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="515f5-104">Hiermee schakelt u foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="515f5-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="515f5-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="515f5-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="515f5-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="515f5-106">Parameters</span></span>
----------

<span data-ttu-id="515f5-107">*BreakAll* \[in\] een onderbrekingspunt instellen op elke regel in het resource-script.</span><span class="sxs-lookup"><span data-stu-id="515f5-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="515f5-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="515f5-108">Return value</span></span>
------------

<span data-ttu-id="515f5-109">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="515f5-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="515f5-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="515f5-110">Remarks</span></span>

<span data-ttu-id="515f5-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="515f5-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="515f5-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="515f5-112">Requirements</span></span>
------------
><span data-ttu-id="515f5-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="515f5-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="515f5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="515f5-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="515f5-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="515f5-115">See also</span></span>


[<span data-ttu-id="515f5-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="515f5-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)