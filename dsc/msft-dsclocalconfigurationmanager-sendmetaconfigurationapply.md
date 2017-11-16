---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2a82f-103">SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2a82f-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2a82f-104">Hiermee stelt u de lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="2a82f-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="2a82f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2a82f-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="2a82f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="2a82f-106">Parameters</span></span>
----------

<span data-ttu-id="2a82f-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2a82f-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="2a82f-108">De omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="2a82f-108">The environment data for the configuration.</span></span>

<span data-ttu-id="2a82f-109">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2a82f-109">*force* \[in\]</span></span>  
<span data-ttu-id="2a82f-110">**de waarde True** om af te dwingen van de configuratie te stoppen.</span><span class="sxs-lookup"><span data-stu-id="2a82f-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="2a82f-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="2a82f-111">Return value</span></span>
------------

<span data-ttu-id="2a82f-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="2a82f-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a82f-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2a82f-113">Remarks</span></span>

<span data-ttu-id="2a82f-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="2a82f-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2a82f-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2a82f-115">Requirements</span></span>
------------
><span data-ttu-id="2a82f-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2a82f-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2a82f-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2a82f-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2a82f-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2a82f-118">See also</span></span>


[<span data-ttu-id="2a82f-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2a82f-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



