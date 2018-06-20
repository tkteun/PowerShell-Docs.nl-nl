---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221762"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="03571-103">De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="03571-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="03571-104">Haal de geschiedenis van de configuratie-status.</span><span class="sxs-lookup"><span data-stu-id="03571-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="03571-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="03571-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="03571-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="03571-106">Parameters</span></span>
----------

<span data-ttu-id="03571-107">*Alle* \[in\] **true** als deze methode informatie over de configuratie op de machine wordt uitgevoerd retourneren moet, met inbegrip van de configuratie-toepassing en de consistentiecontrole.</span><span class="sxs-lookup"><span data-stu-id="03571-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="03571-108">*configurationStatus* \[uit\] op return bevat een ingesloten exemplaar van de **MSFT_DSCConfigurationStatus** klasse die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="03571-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="03571-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="03571-109">Return value</span></span>
------------

<span data-ttu-id="03571-110">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="03571-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="03571-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="03571-111">Remarks</span></span>

<span data-ttu-id="03571-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="03571-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="03571-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="03571-113">Requirements</span></span>
------------
><span data-ttu-id="03571-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="03571-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="03571-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="03571-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="03571-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="03571-116">See also</span></span>


[<span data-ttu-id="03571-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="03571-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)