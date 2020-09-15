---
ms.date: 07/14/2020
keywords: DSC, Power shell, configuratie, installatie
title: ApplyConfiguration-methode
ms.openlocfilehash: bec74ccd6f75448484adfd26bf8a4af4e224eb3f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463836"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="34d49-103">ApplyConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="34d49-103">ApplyConfiguration method</span></span>

<span data-ttu-id="34d49-104">Maakt gebruik van de configuratie agent om de in behandeling zijnde configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="34d49-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="34d49-105">Als er geen configuratie in behandeling is, past deze methode de huidige configuratie opnieuw toe.</span><span class="sxs-lookup"><span data-stu-id="34d49-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="34d49-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="34d49-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="34d49-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="34d49-107">Parameters</span></span>

### <a name="force"></a><span data-ttu-id="34d49-108">verkopers</span><span class="sxs-lookup"><span data-stu-id="34d49-108">force</span></span>

<span data-ttu-id="34d49-109">Als dit het **geval**is, wordt de huidige configuratie opnieuw toegepast, zelfs als er een configuratie in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="34d49-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="34d49-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="34d49-110">Return value</span></span>

<span data-ttu-id="34d49-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="34d49-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="34d49-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="34d49-112">Remarks</span></span>

<span data-ttu-id="34d49-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="34d49-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="34d49-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="34d49-114">Requirements</span></span>

<span data-ttu-id="34d49-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="34d49-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="34d49-116">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="34d49-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="34d49-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="34d49-117">See also</span></span>

[<span data-ttu-id="34d49-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="34d49-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
