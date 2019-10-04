---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: EnableDebugConfiguration-methode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941584"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="399eb-103">EnableDebugConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="399eb-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="399eb-104">Hiermee schakelt u fout opsporing voor DSC-resources in.</span><span class="sxs-lookup"><span data-stu-id="399eb-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="399eb-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="399eb-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="399eb-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="399eb-106">Parameters</span></span>

<span data-ttu-id="399eb-107">*BreakAll* \[in @ no__t-2 stelt een onderbrekings punt in op elke regel in het bron script.</span><span class="sxs-lookup"><span data-stu-id="399eb-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="399eb-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="399eb-108">Return value</span></span>

<span data-ttu-id="399eb-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="399eb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="399eb-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="399eb-110">Remarks</span></span>

<span data-ttu-id="399eb-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="399eb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="399eb-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="399eb-112">Requirements</span></span>

<span data-ttu-id="399eb-113">**MANAGE** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="399eb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="399eb-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="399eb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="399eb-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="399eb-115">See also</span></span>

[<span data-ttu-id="399eb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="399eb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
