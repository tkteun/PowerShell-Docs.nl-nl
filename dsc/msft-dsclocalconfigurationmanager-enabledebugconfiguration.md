---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="02e2b-103">EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="02e2b-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="02e2b-104">Hiermee schakelt u foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="02e2b-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="02e2b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="02e2b-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="02e2b-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="02e2b-106">Parameters</span></span>
----------

<span data-ttu-id="02e2b-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="02e2b-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="02e2b-108">Hiermee stelt u een onderbrekingspunt op elke regel in het resource-script.</span><span class="sxs-lookup"><span data-stu-id="02e2b-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="02e2b-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="02e2b-109">Return value</span></span>
------------

<span data-ttu-id="02e2b-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="02e2b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="02e2b-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="02e2b-111">Remarks</span></span>

<span data-ttu-id="02e2b-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="02e2b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="02e2b-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="02e2b-113">Requirements</span></span>
------------
><span data-ttu-id="02e2b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="02e2b-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="02e2b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="02e2b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="02e2b-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="02e2b-116">See also</span></span>


[<span data-ttu-id="02e2b-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="02e2b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



