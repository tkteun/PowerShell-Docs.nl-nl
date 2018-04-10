---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ab82b239ddfdb4075d9440cd66343266b3c08eda
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="44c1e-103">De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="44c1e-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="44c1e-104">Hiermee stelt u de lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="44c1e-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="44c1e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="44c1e-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="44c1e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="44c1e-106">Parameters</span></span>
----------

<span data-ttu-id="44c1e-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="44c1e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="44c1e-108">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="44c1e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="44c1e-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="44c1e-109">Return value</span></span>
------------

<span data-ttu-id="44c1e-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="44c1e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="44c1e-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="44c1e-111">Remarks</span></span>

<span data-ttu-id="44c1e-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="44c1e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="44c1e-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="44c1e-113">Requirements</span></span>
------------
><span data-ttu-id="44c1e-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="44c1e-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="44c1e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="44c1e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="44c1e-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="44c1e-116">See also</span></span>


[<span data-ttu-id="44c1e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="44c1e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)