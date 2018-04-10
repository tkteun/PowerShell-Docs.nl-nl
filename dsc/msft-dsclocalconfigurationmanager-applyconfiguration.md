---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="342a5-103">De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="342a5-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="342a5-104">Gebruik de Configuration-Agent voor de configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="342a5-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="342a5-105">Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="342a5-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="342a5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="342a5-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="342a5-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="342a5-107">Parameters</span></span>
----------

<span data-ttu-id="342a5-108">*Force* \[in\] als dit **true**, de huidige configuratie wordt opnieuw toegepast, zelfs als er een configuratie in behandeling.</span><span class="sxs-lookup"><span data-stu-id="342a5-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="342a5-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="342a5-109">Return value</span></span>
------------

<span data-ttu-id="342a5-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="342a5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="342a5-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="342a5-111">Remarks</span></span>

<span data-ttu-id="342a5-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="342a5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="342a5-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="342a5-113">Requirements</span></span>
------------
><span data-ttu-id="342a5-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="342a5-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="342a5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="342a5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="342a5-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="342a5-116">See also</span></span>


[<span data-ttu-id="342a5-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="342a5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)