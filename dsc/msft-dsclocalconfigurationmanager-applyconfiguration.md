---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ef8488246b2c8614452d32009e45535f0ff2e184
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222136"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="df9a5-103">De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="df9a5-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="df9a5-104">Gebruik de Configuration-Agent voor de configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="df9a5-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="df9a5-105">Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="df9a5-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="df9a5-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="df9a5-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="df9a5-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="df9a5-107">Parameters</span></span>
----------

<span data-ttu-id="df9a5-108">*Force* \[in\] als dit **true**, de huidige configuratie wordt opnieuw toegepast, zelfs als er een configuratie in behandeling.</span><span class="sxs-lookup"><span data-stu-id="df9a5-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="df9a5-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="df9a5-109">Return value</span></span>
------------

<span data-ttu-id="df9a5-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="df9a5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="df9a5-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="df9a5-111">Remarks</span></span>

<span data-ttu-id="df9a5-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="df9a5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="df9a5-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="df9a5-113">Requirements</span></span>
------------
><span data-ttu-id="df9a5-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="df9a5-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="df9a5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="df9a5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="df9a5-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="df9a5-116">See also</span></span>


[<span data-ttu-id="df9a5-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="df9a5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)