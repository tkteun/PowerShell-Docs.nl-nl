---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f837a-103">SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f837a-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f837a-104">Het configuratiebestand voor asynchroon verzendt naar het beheerde knooppunt en gebruik van de configuratie-Agent voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f837a-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="f837a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f837a-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="f837a-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f837a-106">Parameters</span></span>
----------

<span data-ttu-id="f837a-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f837a-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="f837a-108">De omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f837a-108">The environment data for the configuration.</span></span>

<span data-ttu-id="f837a-109">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f837a-109">*force* \[in\]</span></span>  
<span data-ttu-id="f837a-110">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="f837a-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="f837a-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f837a-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="f837a-112">De ID van de taak voor voor het verzenden van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f837a-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f837a-113">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f837a-113">Return value</span></span>
------------

<span data-ttu-id="f837a-114">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="f837a-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f837a-115">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f837a-115">Remarks</span></span>

<span data-ttu-id="f837a-116">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f837a-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f837a-117">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f837a-117">Requirements</span></span>
------------
><span data-ttu-id="f837a-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f837a-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f837a-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f837a-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f837a-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f837a-120">See also</span></span>


[<span data-ttu-id="f837a-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f837a-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



