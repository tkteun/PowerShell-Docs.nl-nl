---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: acd8f380f1c49eb008563398c2c3de3fce5477f9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186674"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a9a1c-103">De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a9a1c-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a9a1c-104">Het configuratiebestand voor asynchroon verzendt naar het beheerde knooppunt en gebruik van de configuratie-Agent voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a9a1c-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="a9a1c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a9a1c-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="a9a1c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a9a1c-106">Parameters</span></span>
----------

<span data-ttu-id="a9a1c-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a9a1c-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a9a1c-108">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="a9a1c-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="a9a1c-109">*jobId* \[in\] de ID van de taak voor voor het verzenden van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a9a1c-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9a1c-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="a9a1c-110">Return value</span></span>
------------

<span data-ttu-id="a9a1c-111">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="a9a1c-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9a1c-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a9a1c-112">Remarks</span></span>

<span data-ttu-id="a9a1c-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="a9a1c-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9a1c-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a9a1c-114">Requirements</span></span>
------------
><span data-ttu-id="a9a1c-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a9a1c-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a9a1c-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a9a1c-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a9a1c-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a9a1c-117">See also</span></span>


[<span data-ttu-id="a9a1c-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a9a1c-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)