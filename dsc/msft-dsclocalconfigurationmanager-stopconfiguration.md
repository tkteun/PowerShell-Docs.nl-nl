---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c98a7-103">StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c98a7-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c98a7-104">Stopt het wijzigen van de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c98a7-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="c98a7-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c98a7-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="c98a7-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="c98a7-106">Parameters</span></span>
----------

<span data-ttu-id="c98a7-107">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c98a7-107">*force* \[in\]</span></span>  
<span data-ttu-id="c98a7-108">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="c98a7-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c98a7-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="c98a7-109">Return value</span></span>
------------

<span data-ttu-id="c98a7-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="c98a7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c98a7-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c98a7-111">Remarks</span></span>

<span data-ttu-id="c98a7-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="c98a7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c98a7-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c98a7-113">Requirements</span></span>
------------
><span data-ttu-id="c98a7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c98a7-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c98a7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c98a7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c98a7-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c98a7-116">See also</span></span>


[<span data-ttu-id="c98a7-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c98a7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



