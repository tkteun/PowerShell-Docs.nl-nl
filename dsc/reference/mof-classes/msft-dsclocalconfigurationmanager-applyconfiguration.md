---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683910"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3e21e-103">De ApplyConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3e21e-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3e21e-104">Gebruik de configuratie van Agent voor de configuratie die in behandeling is.</span><span class="sxs-lookup"><span data-stu-id="3e21e-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="3e21e-105">Als er geen configuratie in behandeling is, wordt deze methode de huidige configuratie opnieuw toegepast.</span><span class="sxs-lookup"><span data-stu-id="3e21e-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e21e-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3e21e-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3e21e-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="3e21e-107">Parameters</span></span>

<span data-ttu-id="3e21e-108">*afdwingen dat* \[in\] als dit **waar**, de huidige configuratie is toegepast, zelfs als er een configuratie in behandeling.</span><span class="sxs-lookup"><span data-stu-id="3e21e-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="3e21e-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="3e21e-109">Return value</span></span>

<span data-ttu-id="3e21e-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="3e21e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e21e-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3e21e-111">Remarks</span></span>

<span data-ttu-id="3e21e-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="3e21e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e21e-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3e21e-113">Requirements</span></span>

<span data-ttu-id="3e21e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3e21e-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3e21e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3e21e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3e21e-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3e21e-116">See also</span></span>

[<span data-ttu-id="3e21e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3e21e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)