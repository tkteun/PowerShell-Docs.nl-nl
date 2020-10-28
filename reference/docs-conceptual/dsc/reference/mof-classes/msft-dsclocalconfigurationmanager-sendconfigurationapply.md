---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApply-methode
description: SendConfigurationApply-methode
ms.openlocfilehash: 9bd63220644e096b348f71ee9d4ac216af6a7ccc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648979"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="9e012-103">SendConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="9e012-103">SendConfigurationApply method</span></span>

<span data-ttu-id="9e012-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="9e012-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="9e012-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9e012-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9e012-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9e012-106">Parameters</span></span>

<span data-ttu-id="9e012-107">**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="9e012-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9e012-108">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="9e012-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9e012-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="9e012-109">Return value</span></span>

<span data-ttu-id="9e012-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9e012-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e012-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9e012-111">Remarks</span></span>

<span data-ttu-id="9e012-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="9e012-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9e012-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9e012-113">Requirements</span></span>

<span data-ttu-id="9e012-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="9e012-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9e012-115">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9e012-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9e012-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9e012-116">See also</span></span>

[<span data-ttu-id="9e012-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9e012-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
