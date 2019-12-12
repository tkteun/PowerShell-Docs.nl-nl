---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: EnableDebugConfiguration-methode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941584"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="ade67-103">EnableDebugConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="ade67-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="ade67-104">Hiermee schakelt u fout opsporing voor DSC-resources in.</span><span class="sxs-lookup"><span data-stu-id="ade67-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="ade67-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ade67-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="ade67-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="ade67-106">Parameters</span></span>

<span data-ttu-id="ade67-107">*BreakAll* \[in\] stelt een onderbrekings punt in op elke regel in het bron script.</span><span class="sxs-lookup"><span data-stu-id="ade67-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="ade67-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="ade67-108">Return value</span></span>

<span data-ttu-id="ade67-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="ade67-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ade67-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ade67-110">Remarks</span></span>

<span data-ttu-id="ade67-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="ade67-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ade67-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ade67-112">Requirements</span></span>

<span data-ttu-id="ade67-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="ade67-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ade67-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ade67-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ade67-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ade67-115">See also</span></span>

[<span data-ttu-id="ade67-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="ade67-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
