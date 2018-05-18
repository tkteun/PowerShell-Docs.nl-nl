---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 46acd86ac52b7b6b39f06fc65af2498b4f5348ed
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cce16-103">De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cce16-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cce16-104">Hiermee stelt u de lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="cce16-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="cce16-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cce16-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="cce16-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="cce16-106">Parameters</span></span>
----------

<span data-ttu-id="cce16-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="cce16-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="cce16-108">*Force* \[in\] **true** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="cce16-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="cce16-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="cce16-109">Return value</span></span>
------------

<span data-ttu-id="cce16-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="cce16-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cce16-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cce16-111">Remarks</span></span>

<span data-ttu-id="cce16-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="cce16-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cce16-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cce16-113">Requirements</span></span>
------------
><span data-ttu-id="cce16-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cce16-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="cce16-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cce16-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="cce16-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cce16-116">See also</span></span>


[<span data-ttu-id="cce16-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cce16-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)