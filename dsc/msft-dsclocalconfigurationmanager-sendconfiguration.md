---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07ae48dd456e68be4ad0b09127ba9801359fd101
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="30273-103">De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="30273-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="30273-104">Het configuratiebestand voor verzendt naar het beheerde knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="30273-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="30273-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="30273-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="30273-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="30273-106">Parameters</span></span>
----------

<span data-ttu-id="30273-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="30273-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="30273-108">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="30273-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="30273-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="30273-109">Return value</span></span>
------------

<span data-ttu-id="30273-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="30273-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="30273-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="30273-111">Remarks</span></span>

<span data-ttu-id="30273-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="30273-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="30273-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="30273-113">Requirements</span></span>
------------
><span data-ttu-id="30273-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="30273-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="30273-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="30273-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="30273-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="30273-116">See also</span></span>


[<span data-ttu-id="30273-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="30273-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)