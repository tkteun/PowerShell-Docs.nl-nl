---
ms.date: 07/17/2020
ms.topic: reference
title: RollBack-methode
description: RollBack-methode
ms.openlocfilehash: 82ca54ed23a3a892b785f603be3b423def5ee636
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650619"
---
# <a name="rollback-method"></a><span data-ttu-id="4c66e-103">RollBack-methode</span><span class="sxs-lookup"><span data-stu-id="4c66e-103">RollBack method</span></span>

<span data-ttu-id="4c66e-104">Hiermee wordt de configuratie teruggezet naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="4c66e-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="4c66e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4c66e-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="4c66e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="4c66e-106">Parameters</span></span>

<span data-ttu-id="4c66e-107">**configurationNumber** \[ in \] geeft de aangevraagde configuratie aan.</span><span class="sxs-lookup"><span data-stu-id="4c66e-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c66e-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="4c66e-108">Return value</span></span>

<span data-ttu-id="4c66e-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4c66e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4c66e-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4c66e-110">Remarks</span></span>

<span data-ttu-id="4c66e-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="4c66e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c66e-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4c66e-112">Requirements</span></span>

<span data-ttu-id="4c66e-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="4c66e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4c66e-114">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4c66e-114">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4c66e-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4c66e-115">See also</span></span>

[<span data-ttu-id="4c66e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4c66e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
