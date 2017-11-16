---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De methode ApplyConfiguration van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="574aa-103">De methode ApplyConfiguration van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="574aa-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="574aa-104">Gebruik de Configuration-Agent voor de configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="574aa-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="574aa-105">Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="574aa-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="574aa-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="574aa-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="574aa-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="574aa-107">Parameters</span></span>
----------

<span data-ttu-id="574aa-108">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="574aa-108">*force* \[in\]</span></span>  
<span data-ttu-id="574aa-109">Als dit **true**, de huidige configuratie wordt opnieuw toegepast, zelfs als er een configuratie in behandeling.</span><span class="sxs-lookup"><span data-stu-id="574aa-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="574aa-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="574aa-110">Return value</span></span>
------------

<span data-ttu-id="574aa-111">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="574aa-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="574aa-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="574aa-112">Remarks</span></span>

<span data-ttu-id="574aa-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="574aa-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="574aa-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="574aa-114">Requirements</span></span>
------------
><span data-ttu-id="574aa-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="574aa-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="574aa-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="574aa-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="574aa-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="574aa-117">See also</span></span>


[<span data-ttu-id="574aa-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="574aa-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



