---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="94405-103">EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="94405-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="94405-104">Hiermee schakelt u foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="94405-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="94405-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="94405-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="94405-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="94405-106">Parameters</span></span>
----------

<span data-ttu-id="94405-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="94405-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="94405-108">Hiermee stelt u een onderbrekingspunt op elke regel in het resource-script.</span><span class="sxs-lookup"><span data-stu-id="94405-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="94405-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="94405-109">Return value</span></span>
------------

<span data-ttu-id="94405-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="94405-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="94405-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="94405-111">Remarks</span></span>

<span data-ttu-id="94405-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="94405-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="94405-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="94405-113">Requirements</span></span>
------------
><span data-ttu-id="94405-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="94405-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="94405-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="94405-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="94405-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="94405-116">See also</span></span>


[<span data-ttu-id="94405-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="94405-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



