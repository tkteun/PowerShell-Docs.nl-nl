---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration-methode
description: ApplyConfiguration-methode
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664274"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="e49ab-103">ApplyConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="e49ab-103">ApplyConfiguration method</span></span>

<span data-ttu-id="e49ab-104">Maakt gebruik van de configuratie agent om de in behandeling zijnde configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="e49ab-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="e49ab-105">Als er geen configuratie in behandeling is, past deze methode de huidige configuratie opnieuw toe.</span><span class="sxs-lookup"><span data-stu-id="e49ab-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="e49ab-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e49ab-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e49ab-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="e49ab-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="e49ab-108">verkopers</span><span class="sxs-lookup"><span data-stu-id="e49ab-108">force</span></span>

<span data-ttu-id="e49ab-109">Als dit het **geval** is, wordt de huidige configuratie opnieuw toegepast, zelfs als er een configuratie in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="e49ab-109">If this is **true** , the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="e49ab-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e49ab-110">Return value</span></span>

<span data-ttu-id="e49ab-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e49ab-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e49ab-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e49ab-112">Remarks</span></span>

<span data-ttu-id="e49ab-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e49ab-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e49ab-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e49ab-114">Requirements</span></span>

<span data-ttu-id="e49ab-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="e49ab-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e49ab-116">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e49ab-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e49ab-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e49ab-117">See also</span></span>

[<span data-ttu-id="e49ab-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e49ab-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
