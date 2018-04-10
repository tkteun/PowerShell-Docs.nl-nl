---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="96401-103">De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="96401-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="96401-104">Hiermee verwijdert u de configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="96401-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="96401-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="96401-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="96401-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="96401-106">Parameters</span></span>
----------

<span data-ttu-id="96401-107">*Fase* \[in\] geeft aan welke configuratie-document te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="96401-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="96401-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="96401-108">The following values are valid:</span></span>

|<span data-ttu-id="96401-109">Value</span><span class="sxs-lookup"><span data-stu-id="96401-109">Value</span></span> |<span data-ttu-id="96401-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="96401-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="96401-111">**1**</span><span class="sxs-lookup"><span data-stu-id="96401-111">**1**</span></span> | <span data-ttu-id="96401-112">De **huidige** configuratie document (current.mof).</span><span class="sxs-lookup"><span data-stu-id="96401-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="96401-113">**2**</span><span class="sxs-lookup"><span data-stu-id="96401-113">**2**</span></span> | <span data-ttu-id="96401-114">De **in behandeling** configuratie document (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="96401-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="96401-115">**4**</span><span class="sxs-lookup"><span data-stu-id="96401-115">**4**</span></span> | <span data-ttu-id="96401-116">De **vorige** configuratie document (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="96401-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="96401-117">*Force* \[in\] **true** om af te dwingen van het verwijderen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="96401-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="96401-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="96401-118">Return value</span></span>
------------

<span data-ttu-id="96401-119">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="96401-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="96401-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="96401-120">Remarks</span></span>

<span data-ttu-id="96401-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="96401-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="96401-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="96401-122">Requirements</span></span>
------------
><span data-ttu-id="96401-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="96401-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="96401-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="96401-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="96401-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="96401-125">See also</span></span>


[<span data-ttu-id="96401-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="96401-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)