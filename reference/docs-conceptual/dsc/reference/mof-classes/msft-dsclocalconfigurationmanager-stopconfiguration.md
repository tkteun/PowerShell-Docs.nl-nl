---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: StopConfiguration-methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941528"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="cd325-103">StopConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="cd325-103">StopConfiguration method</span></span>

<span data-ttu-id="cd325-104">Hiermee stopt u de configuratie wijziging die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="cd325-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd325-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cd325-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="cd325-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="cd325-106">Parameters</span></span>

<span data-ttu-id="cd325-107">*force* \[in @ no__t-2 **True** om te voor komen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="cd325-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd325-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="cd325-108">Return value</span></span>

<span data-ttu-id="cd325-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cd325-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd325-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cd325-110">Remarks</span></span>

<span data-ttu-id="cd325-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="cd325-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd325-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cd325-112">Requirements</span></span>

<span data-ttu-id="cd325-113">**MANAGE** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="cd325-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cd325-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cd325-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cd325-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cd325-115">See also</span></span>

[<span data-ttu-id="cd325-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cd325-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
