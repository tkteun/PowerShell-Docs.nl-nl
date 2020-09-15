---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: RollBack-methode
ms.openlocfilehash: 301b8926d2ebf1ebe524f52a67928d34e26d860e
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464329"
---
# <a name="rollback-method"></a><span data-ttu-id="ac8cf-103">RollBack-methode</span><span class="sxs-lookup"><span data-stu-id="ac8cf-103">RollBack method</span></span>

<span data-ttu-id="ac8cf-104">Hiermee wordt de configuratie teruggezet naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="ac8cf-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="ac8cf-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ac8cf-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="ac8cf-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="ac8cf-106">Parameters</span></span>

<span data-ttu-id="ac8cf-107">**configurationNumber** \[ in \] geeft de aangevraagde configuratie aan.</span><span class="sxs-lookup"><span data-stu-id="ac8cf-107">**configurationNumber** \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="ac8cf-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="ac8cf-108">Return value</span></span>

<span data-ttu-id="ac8cf-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ac8cf-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ac8cf-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ac8cf-110">Remarks</span></span>

<span data-ttu-id="ac8cf-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="ac8cf-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ac8cf-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ac8cf-112">Requirements</span></span>

<span data-ttu-id="ac8cf-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="ac8cf-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ac8cf-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ac8cf-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ac8cf-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ac8cf-115">See also</span></span>

[<span data-ttu-id="ac8cf-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ac8cf-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
