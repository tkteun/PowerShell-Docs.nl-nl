---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: EnableDebugConfiguration-methode
ms.openlocfilehash: be75b1012f49db79eb75a68c6912ffd5772bf16f
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464091"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="157fe-103">EnableDebugConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="157fe-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="157fe-104">Hiermee schakelt u fout opsporing voor DSC-resources in.</span><span class="sxs-lookup"><span data-stu-id="157fe-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="157fe-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="157fe-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="157fe-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="157fe-106">Parameters</span></span>

<span data-ttu-id="157fe-107">**BreakAll** \[ in \] stelt een onderbrekings punt in op elke regel in het bron script.</span><span class="sxs-lookup"><span data-stu-id="157fe-107">**BreakAll** \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="157fe-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="157fe-108">Return value</span></span>

<span data-ttu-id="157fe-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="157fe-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="157fe-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="157fe-110">Remarks</span></span>

<span data-ttu-id="157fe-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="157fe-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="157fe-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="157fe-112">Requirements</span></span>

<span data-ttu-id="157fe-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="157fe-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="157fe-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="157fe-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="157fe-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="157fe-115">See also</span></span>

[<span data-ttu-id="157fe-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="157fe-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
