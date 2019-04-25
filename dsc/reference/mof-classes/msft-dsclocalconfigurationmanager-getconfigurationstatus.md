---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078762"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d54f0-103">De GetConfigurationStatus-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d54f0-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d54f0-104">De geschiedenis van de configuratie-status ophalen.</span><span class="sxs-lookup"><span data-stu-id="d54f0-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="d54f0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d54f0-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="d54f0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="d54f0-106">Parameters</span></span>

<span data-ttu-id="d54f0-107">*Alle* \[in\] **waar** als deze methode informatie over de configuratie op de machine wordt uitgevoerd retourneren moet, met inbegrip van de configuratie van toepassing en de consistentiecontrole.</span><span class="sxs-lookup"><span data-stu-id="d54f0-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="d54f0-108">*configurationStatus* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_DSCConfigurationStatus** klasse waarin de instellingen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d54f0-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d54f0-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="d54f0-109">Return value</span></span>

<span data-ttu-id="d54f0-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="d54f0-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d54f0-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d54f0-111">Remarks</span></span>

<span data-ttu-id="d54f0-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="d54f0-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d54f0-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d54f0-113">Requirements</span></span>

<span data-ttu-id="d54f0-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d54f0-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d54f0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d54f0-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d54f0-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d54f0-116">See also</span></span>

[<span data-ttu-id="d54f0-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d54f0-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)