---
ms.date: 07/17/2020
ms.topic: reference
title: SendMetaConfigurationApply-methode
description: SendMetaConfigurationApply-methode
ms.openlocfilehash: 27c58819c0249ace011c475e500e565e5daed9bb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648962"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="9310f-103">SendMetaConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="9310f-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="9310f-104">Hiermee stelt u de lokale Configuration Manager-instellingen in die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="9310f-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="9310f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9310f-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="9310f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9310f-106">Parameters</span></span>

<span data-ttu-id="9310f-107">**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="9310f-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="9310f-108">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="9310f-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9310f-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="9310f-109">Return value</span></span>

<span data-ttu-id="9310f-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9310f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9310f-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9310f-111">Remarks</span></span>

<span data-ttu-id="9310f-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="9310f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9310f-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9310f-113">Requirements</span></span>

<span data-ttu-id="9310f-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="9310f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9310f-115">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9310f-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9310f-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9310f-116">See also</span></span>

[<span data-ttu-id="9310f-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9310f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
