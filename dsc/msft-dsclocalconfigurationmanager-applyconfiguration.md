---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De methode ApplyConfiguration van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 72fbedf30e5058d8003ed620400d6b443d50dff6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bef98-103">De methode ApplyConfiguration van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bef98-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bef98-104">Gebruik de Configuration-Agent voor de configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="bef98-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="bef98-105">Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="bef98-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="bef98-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bef98-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="bef98-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="bef98-107">Parameters</span></span>
----------

<span data-ttu-id="bef98-108">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bef98-108">*force* \[in\]</span></span>  
<span data-ttu-id="bef98-109">Als dit **true**, de huidige configuratie wordt opnieuw toegepast, zelfs als er een configuratie in behandeling.</span><span class="sxs-lookup"><span data-stu-id="bef98-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="bef98-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="bef98-110">Return value</span></span>
------------

<span data-ttu-id="bef98-111">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="bef98-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bef98-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bef98-112">Remarks</span></span>

<span data-ttu-id="bef98-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="bef98-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bef98-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bef98-114">Requirements</span></span>
------------
><span data-ttu-id="bef98-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bef98-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bef98-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bef98-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bef98-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bef98-117">See also</span></span>


[<span data-ttu-id="bef98-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bef98-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



