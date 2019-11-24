---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ApplyConfiguration-methode
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941598"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="074f1-103">ApplyConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="074f1-103">ApplyConfiguration method</span></span>

<span data-ttu-id="074f1-104">Maakt gebruik van de configuratie agent om de in behandeling zijnde configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="074f1-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="074f1-105">Als er geen configuratie in behandeling is, past deze methode de huidige configuratie opnieuw toe.</span><span class="sxs-lookup"><span data-stu-id="074f1-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="074f1-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="074f1-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="074f1-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="074f1-107">Parameters</span></span>

<span data-ttu-id="074f1-108">\[*afdwingen* in\] als dit **waar**is, wordt de huidige configuratie opnieuw toegepast, zelfs als er een configuratie in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="074f1-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="074f1-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="074f1-109">Return value</span></span>

<span data-ttu-id="074f1-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="074f1-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="074f1-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="074f1-111">Remarks</span></span>

<span data-ttu-id="074f1-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="074f1-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="074f1-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="074f1-113">Requirements</span></span>

<span data-ttu-id="074f1-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="074f1-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="074f1-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="074f1-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="074f1-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="074f1-116">See also</span></span>

[<span data-ttu-id="074f1-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="074f1-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
