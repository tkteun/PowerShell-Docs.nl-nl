---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cb0a5-103">SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cb0a5-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cb0a5-104">Het configuratiebestand voor asynchroon verzendt naar het beheerde knooppunt en gebruik van de configuratie-Agent voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="cb0a5-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cb0a5-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="cb0a5-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="cb0a5-106">Parameters</span></span>
----------

<span data-ttu-id="cb0a5-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="cb0a5-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="cb0a5-108">De omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-108">The environment data for the configuration.</span></span>

<span data-ttu-id="cb0a5-109">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="cb0a5-109">*force* \[in\]</span></span>  
<span data-ttu-id="cb0a5-110">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="cb0a5-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="cb0a5-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="cb0a5-112">De ID van de taak voor voor het verzenden van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="cb0a5-113">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="cb0a5-113">Return value</span></span>
------------

<span data-ttu-id="cb0a5-114">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb0a5-115">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cb0a5-115">Remarks</span></span>

<span data-ttu-id="cb0a5-116">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="cb0a5-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cb0a5-117">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cb0a5-117">Requirements</span></span>
------------
><span data-ttu-id="cb0a5-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cb0a5-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cb0a5-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cb0a5-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cb0a5-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cb0a5-120">See also</span></span>


[<span data-ttu-id="cb0a5-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cb0a5-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



