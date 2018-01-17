---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f1c6a-103">GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f1c6a-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f1c6a-104">Verzendt het configuratie-document naar het beheerde knooppunt en maakt gebruik van de **ophalen** methode van de configuratie-Agent de configuratie toepassen.</span><span class="sxs-lookup"><span data-stu-id="f1c6a-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="f1c6a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f1c6a-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="f1c6a-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f1c6a-106">Parameters</span></span>
----------

<span data-ttu-id="f1c6a-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f1c6a-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="f1c6a-108">Hiermee geeft u de configuratiegegevens te verzenden.</span><span class="sxs-lookup"><span data-stu-id="f1c6a-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="f1c6a-109">*configuraties* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="f1c6a-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="f1c6a-110">Bevat een ingesloten exemplaar van de configuraties op return.</span><span class="sxs-lookup"><span data-stu-id="f1c6a-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="f1c6a-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f1c6a-111">Return value</span></span>
------------

<span data-ttu-id="f1c6a-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="f1c6a-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1c6a-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f1c6a-113">Remarks</span></span>

<span data-ttu-id="f1c6a-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f1c6a-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f1c6a-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f1c6a-115">Requirements</span></span>
------------
><span data-ttu-id="f1c6a-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f1c6a-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f1c6a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f1c6a-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f1c6a-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f1c6a-118">See also</span></span>


[<span data-ttu-id="f1c6a-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f1c6a-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



