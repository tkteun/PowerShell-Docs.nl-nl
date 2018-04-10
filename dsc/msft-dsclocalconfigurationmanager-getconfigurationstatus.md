---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a6132-103">De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a6132-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a6132-104">Haal de geschiedenis van de configuratie-status.</span><span class="sxs-lookup"><span data-stu-id="a6132-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="a6132-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a6132-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="a6132-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a6132-106">Parameters</span></span>
----------

<span data-ttu-id="a6132-107">*Alle* \[in\] **true** als deze methode informatie over de configuratie op de machine wordt uitgevoerd retourneren moet, met inbegrip van de configuratie-toepassing en de consistentiecontrole.</span><span class="sxs-lookup"><span data-stu-id="a6132-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="a6132-108">*configurationStatus* \[uit\] op return bevat een ingesloten exemplaar van de **MSFT_DSCConfigurationStatus** klasse die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="a6132-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="a6132-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="a6132-109">Return value</span></span>
------------

<span data-ttu-id="a6132-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="a6132-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6132-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a6132-111">Remarks</span></span>

<span data-ttu-id="a6132-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="a6132-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6132-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a6132-113">Requirements</span></span>
------------
><span data-ttu-id="a6132-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a6132-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a6132-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a6132-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a6132-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a6132-116">See also</span></span>


[<span data-ttu-id="a6132-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a6132-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)