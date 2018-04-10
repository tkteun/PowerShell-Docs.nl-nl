---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a89b0-103">De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a89b0-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a89b0-104">Het configuratiebestand voor asynchroon verzendt naar het beheerde knooppunt en gebruik van de configuratie-Agent voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a89b0-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="a89b0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a89b0-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="a89b0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a89b0-106">Parameters</span></span>
----------

<span data-ttu-id="a89b0-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a89b0-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a89b0-108">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="a89b0-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="a89b0-109">*jobId* \[in\] de ID van de taak voor voor het verzenden van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a89b0-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a89b0-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="a89b0-110">Return value</span></span>
------------

<span data-ttu-id="a89b0-111">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="a89b0-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a89b0-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a89b0-112">Remarks</span></span>

<span data-ttu-id="a89b0-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="a89b0-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a89b0-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a89b0-114">Requirements</span></span>
------------
><span data-ttu-id="a89b0-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a89b0-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a89b0-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a89b0-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a89b0-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a89b0-117">See also</span></span>


[<span data-ttu-id="a89b0-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a89b0-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)