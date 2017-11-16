---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a16aa-103">StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a16aa-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a16aa-104">Stopt het wijzigen van de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="a16aa-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="a16aa-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a16aa-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="a16aa-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a16aa-106">Parameters</span></span>
----------

<span data-ttu-id="a16aa-107">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="a16aa-107">*force* \[in\]</span></span>  
<span data-ttu-id="a16aa-108">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="a16aa-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a16aa-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="a16aa-109">Return value</span></span>
------------

<span data-ttu-id="a16aa-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="a16aa-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a16aa-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a16aa-111">Remarks</span></span>

<span data-ttu-id="a16aa-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="a16aa-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a16aa-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a16aa-113">Requirements</span></span>
------------
><span data-ttu-id="a16aa-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a16aa-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a16aa-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a16aa-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a16aa-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a16aa-116">See also</span></span>


[<span data-ttu-id="a16aa-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a16aa-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



