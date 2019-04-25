---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078233"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5129e-103">De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5129e-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5129e-104">Hiermee stopt u de wijziging in de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="5129e-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="5129e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5129e-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5129e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="5129e-106">Parameters</span></span>

<span data-ttu-id="5129e-107">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="5129e-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5129e-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="5129e-108">Return value</span></span>

<span data-ttu-id="5129e-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="5129e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5129e-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5129e-110">Remarks</span></span>

<span data-ttu-id="5129e-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="5129e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5129e-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5129e-112">Requirements</span></span>

<span data-ttu-id="5129e-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5129e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5129e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5129e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5129e-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5129e-115">See also</span></span>

[<span data-ttu-id="5129e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5129e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)