---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: StopConfiguration-methode
ms.openlocfilehash: 76e50c98b09dca86983320918c6899082580672a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463700"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="d787e-103">StopConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="d787e-103">StopConfiguration method</span></span>

<span data-ttu-id="d787e-104">Hiermee stopt u de configuratie wijziging die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d787e-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="d787e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d787e-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d787e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="d787e-106">Parameters</span></span>

<span data-ttu-id="d787e-107">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="d787e-107">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d787e-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="d787e-108">Return value</span></span>

<span data-ttu-id="d787e-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d787e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d787e-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d787e-110">Remarks</span></span>

<span data-ttu-id="d787e-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="d787e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d787e-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d787e-112">Requirements</span></span>

<span data-ttu-id="d787e-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="d787e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d787e-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d787e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d787e-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d787e-115">See also</span></span>

[<span data-ttu-id="d787e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d787e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
