---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1cf3c-103">De GetConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="1cf3c-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1cf3c-104">Verzendt het configuratie-document naar het beheerde knooppunt en maakt gebruik van de **ophalen** methode van de configuratie-Agent de configuratie toepassen.</span><span class="sxs-lookup"><span data-stu-id="1cf3c-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="1cf3c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1cf3c-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="1cf3c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="1cf3c-106">Parameters</span></span>
----------

<span data-ttu-id="1cf3c-107">*configurationData* \[in\] Hiermee geeft u de configuratiegegevens te verzenden.</span><span class="sxs-lookup"><span data-stu-id="1cf3c-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="1cf3c-108">*configuraties* \[uit\] op return bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="1cf3c-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="1cf3c-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="1cf3c-109">Return value</span></span>
------------

<span data-ttu-id="1cf3c-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="1cf3c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1cf3c-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1cf3c-111">Remarks</span></span>

<span data-ttu-id="1cf3c-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="1cf3c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1cf3c-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1cf3c-113">Requirements</span></span>
------------
><span data-ttu-id="1cf3c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1cf3c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1cf3c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1cf3c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1cf3c-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1cf3c-116">See also</span></span>


[<span data-ttu-id="1cf3c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1cf3c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)