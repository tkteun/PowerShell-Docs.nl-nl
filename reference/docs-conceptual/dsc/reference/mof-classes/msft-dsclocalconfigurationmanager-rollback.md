---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: RollBack-methode
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942634"
---
# <a name="rollback-method"></a><span data-ttu-id="032e0-103">RollBack-methode</span><span class="sxs-lookup"><span data-stu-id="032e0-103">RollBack method</span></span>

<span data-ttu-id="032e0-104">Hiermee wordt de configuratie teruggezet naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="032e0-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="032e0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="032e0-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="032e0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="032e0-106">Parameters</span></span>

<span data-ttu-id="032e0-107">*configurationNumber* \[in\] geeft de aangevraagde configuratie aan.</span><span class="sxs-lookup"><span data-stu-id="032e0-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="032e0-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="032e0-108">Return value</span></span>

<span data-ttu-id="032e0-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="032e0-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="032e0-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="032e0-110">Remarks</span></span>

<span data-ttu-id="032e0-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="032e0-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="032e0-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="032e0-112">Requirements</span></span>

<span data-ttu-id="032e0-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="032e0-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="032e0-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="032e0-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="032e0-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="032e0-115">See also</span></span>

[<span data-ttu-id="032e0-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="032e0-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
