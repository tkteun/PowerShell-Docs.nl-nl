---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="12ec4-103">SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="12ec4-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="12ec4-104">Hiermee stelt u de lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="12ec4-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="12ec4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="12ec4-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="12ec4-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="12ec4-106">Parameters</span></span>
----------

<span data-ttu-id="12ec4-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="12ec4-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="12ec4-108">De omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="12ec4-108">The environment data for the configuration.</span></span>

<span data-ttu-id="12ec4-109">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="12ec4-109">*force* \[in\]</span></span>  
<span data-ttu-id="12ec4-110">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="12ec4-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="12ec4-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="12ec4-111">Return value</span></span>
------------

<span data-ttu-id="12ec4-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="12ec4-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="12ec4-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="12ec4-113">Remarks</span></span>

<span data-ttu-id="12ec4-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="12ec4-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="12ec4-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="12ec4-115">Requirements</span></span>
------------
><span data-ttu-id="12ec4-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="12ec4-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="12ec4-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="12ec4-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="12ec4-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="12ec4-118">See also</span></span>


[<span data-ttu-id="12ec4-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="12ec4-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



