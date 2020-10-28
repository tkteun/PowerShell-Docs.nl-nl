---
ms.date: 07/17/2020
ms.topic: reference
title: StopConfiguration-methode
description: StopConfiguration-methode
ms.openlocfilehash: 854c0dbe8554c08413735a5a7bc872776e0b0a6c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644619"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="7ddcd-103">StopConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="7ddcd-103">StopConfiguration method</span></span>

<span data-ttu-id="7ddcd-104">Hiermee stopt u de configuratie wijziging die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="7ddcd-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="7ddcd-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7ddcd-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7ddcd-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7ddcd-106">Parameters</span></span>

<span data-ttu-id="7ddcd-107">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="7ddcd-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7ddcd-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="7ddcd-108">Return value</span></span>

<span data-ttu-id="7ddcd-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="7ddcd-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ddcd-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7ddcd-110">Remarks</span></span>

<span data-ttu-id="7ddcd-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="7ddcd-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7ddcd-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7ddcd-112">Requirements</span></span>

<span data-ttu-id="7ddcd-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="7ddcd-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7ddcd-114">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ddcd-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7ddcd-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7ddcd-115">See also</span></span>

[<span data-ttu-id="7ddcd-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7ddcd-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
