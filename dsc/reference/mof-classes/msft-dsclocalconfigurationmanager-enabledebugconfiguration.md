---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De EnableDebugConfiguration-methode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727148"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="07998-103">De EnableDebugConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="07998-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="07998-104">U kunt foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="07998-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="07998-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="07998-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="07998-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="07998-106">Parameters</span></span>

<span data-ttu-id="07998-107">*BreakAll* \[in\] een onderbrekingspunt instellen op elke regel in het resource-script.</span><span class="sxs-lookup"><span data-stu-id="07998-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="07998-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="07998-108">Return value</span></span>

<span data-ttu-id="07998-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="07998-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="07998-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="07998-110">Remarks</span></span>

<span data-ttu-id="07998-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="07998-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="07998-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="07998-112">Requirements</span></span>

<span data-ttu-id="07998-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="07998-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="07998-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="07998-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="07998-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="07998-115">See also</span></span>

[<span data-ttu-id="07998-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="07998-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
