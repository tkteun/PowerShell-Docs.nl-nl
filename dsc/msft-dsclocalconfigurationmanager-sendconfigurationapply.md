---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 8edf8c55089e767394ba21b42fe74072777a45c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="53995-103">De SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="53995-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="53995-104">Het configuratiebestand voor het beheerde knooppunt verzendt en gebruik van de configuratie-Agent voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="53995-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="53995-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="53995-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="53995-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="53995-106">Parameters</span></span>
----------

<span data-ttu-id="53995-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="53995-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="53995-108">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="53995-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="53995-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="53995-109">Return value</span></span>
------------

<span data-ttu-id="53995-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="53995-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="53995-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="53995-111">Remarks</span></span>

<span data-ttu-id="53995-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="53995-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="53995-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="53995-113">Requirements</span></span>
------------
><span data-ttu-id="53995-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="53995-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="53995-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="53995-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="53995-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="53995-116">See also</span></span>


[<span data-ttu-id="53995-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="53995-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)