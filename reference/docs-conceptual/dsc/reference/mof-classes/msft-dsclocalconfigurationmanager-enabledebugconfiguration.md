---
ms.date: 07/17/2020
ms.topic: reference
title: EnableDebugConfiguration-methode
description: EnableDebugConfiguration-methode
ms.openlocfilehash: 536366e6e1627a249f3bc2dc19bfd8ff3de42117
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644771"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="db080-103">EnableDebugConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="db080-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="db080-104">Hiermee schakelt u fout opsporing voor DSC-resources in.</span><span class="sxs-lookup"><span data-stu-id="db080-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="db080-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="db080-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="db080-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="db080-106">Parameters</span></span>

<span data-ttu-id="db080-107">**BreakAll** \[ in \] stelt een onderbrekings punt in op elke regel in het bron script.</span><span class="sxs-lookup"><span data-stu-id="db080-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="db080-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="db080-108">Return value</span></span>

<span data-ttu-id="db080-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="db080-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="db080-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="db080-110">Remarks</span></span>

<span data-ttu-id="db080-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="db080-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="db080-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="db080-112">Requirements</span></span>

<span data-ttu-id="db080-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="db080-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="db080-114">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="db080-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="db080-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="db080-115">See also</span></span>

[<span data-ttu-id="db080-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="db080-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
