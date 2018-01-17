---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c829b-103">GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c829b-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c829b-104">Haal de geschiedenis van de configuratie-status.</span><span class="sxs-lookup"><span data-stu-id="c829b-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="c829b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c829b-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="c829b-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="c829b-106">Parameters</span></span>
----------

<span data-ttu-id="c829b-107">*Alle* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c829b-107">*All* \[in\]</span></span>  
<span data-ttu-id="c829b-108">**de waarde True** als deze methode informatie over de configuratie op de machine wordt uitgevoerd retourneren moet, met inbegrip van de configuratie-toepassing en de consistentiecontrole.</span><span class="sxs-lookup"><span data-stu-id="c829b-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="c829b-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="c829b-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="c829b-110">Op return bevat een ingesloten exemplaar van de **MSFT_DSCConfigurationStatus** klasse die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="c829b-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="c829b-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="c829b-111">Return value</span></span>
------------

<span data-ttu-id="c829b-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="c829b-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c829b-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c829b-113">Remarks</span></span>

<span data-ttu-id="c829b-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="c829b-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c829b-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c829b-115">Requirements</span></span>
------------
><span data-ttu-id="c829b-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c829b-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="c829b-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c829b-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="c829b-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c829b-118">See also</span></span>


[<span data-ttu-id="c829b-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c829b-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



