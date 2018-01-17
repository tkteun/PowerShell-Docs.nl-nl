---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="838f8-103">SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="838f8-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="838f8-104">Het configuratiebestand voor het beheerde knooppunt verzendt en gebruik van de configuratie-Agent voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="838f8-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="838f8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="838f8-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="838f8-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="838f8-106">Parameters</span></span>
----------

<span data-ttu-id="838f8-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="838f8-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="838f8-108">De omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="838f8-108">The environment data for the configuration.</span></span>

<span data-ttu-id="838f8-109">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="838f8-109">*force* \[in\]</span></span>  
<span data-ttu-id="838f8-110">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="838f8-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="838f8-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="838f8-111">Return value</span></span>
------------

<span data-ttu-id="838f8-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="838f8-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="838f8-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="838f8-113">Remarks</span></span>

<span data-ttu-id="838f8-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="838f8-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="838f8-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="838f8-115">Requirements</span></span>
------------
><span data-ttu-id="838f8-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="838f8-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="838f8-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="838f8-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="838f8-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="838f8-118">See also</span></span>


[<span data-ttu-id="838f8-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="838f8-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



