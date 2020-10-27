---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApplyAsync-methode
description: SendConfigurationApplyAsync-methode
ms.openlocfilehash: 92c9d03a7653e72b1ff04084caea4a8b5aadb0e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644792"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="f86a0-103">SendConfigurationApplyAsync-methode</span><span class="sxs-lookup"><span data-stu-id="f86a0-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="f86a0-104">Hiermee wordt het configuratie document asynchroon verzonden naar het beheerde knoop punt en wordt de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="f86a0-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="f86a0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f86a0-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="f86a0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f86a0-106">Parameters</span></span>

<span data-ttu-id="f86a0-107">**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f86a0-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="f86a0-108">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="f86a0-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="f86a0-109">**jobId** \[ in \] de id van de taak waarvoor de configuratie moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="f86a0-109">**jobId** \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f86a0-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f86a0-110">Return value</span></span>

<span data-ttu-id="f86a0-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f86a0-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f86a0-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f86a0-112">Remarks</span></span>

<span data-ttu-id="f86a0-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f86a0-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f86a0-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f86a0-114">Requirements</span></span>

<span data-ttu-id="f86a0-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="f86a0-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f86a0-116">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f86a0-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f86a0-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f86a0-117">See also</span></span>

[<span data-ttu-id="f86a0-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f86a0-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
