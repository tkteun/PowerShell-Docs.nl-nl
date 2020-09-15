---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationStatus-methode
ms.openlocfilehash: c2c478151428052d656832fb4079f12d666a910d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464044"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="0e9f3-103">GetConfigurationStatus-methode</span><span class="sxs-lookup"><span data-stu-id="0e9f3-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="0e9f3-104">De geschiedenis van de configuratie status ophalen.</span><span class="sxs-lookup"><span data-stu-id="0e9f3-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e9f3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0e9f3-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="0e9f3-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="0e9f3-106">Parameters</span></span>

<span data-ttu-id="0e9f3-107">**Alle** \[ in \] **True** als deze methode informatie moet retour neren over alle configuratie runs op de computer, met inbegrip van de configuratie toepassing en de consistentie controle.</span><span class="sxs-lookup"><span data-stu-id="0e9f3-107">**All** \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="0e9f3-108">**configurationStatus** \[ out \] on return bevat een Inge sloten exemplaar van de klasse **MSFT_DSCConfigurationStatus** die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="0e9f3-108">**configurationStatus** \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="0e9f3-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="0e9f3-109">Return value</span></span>

<span data-ttu-id="0e9f3-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0e9f3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e9f3-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0e9f3-111">Remarks</span></span>

<span data-ttu-id="0e9f3-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="0e9f3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e9f3-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0e9f3-113">Requirements</span></span>

<span data-ttu-id="0e9f3-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="0e9f3-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0e9f3-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0e9f3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0e9f3-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0e9f3-116">See also</span></span>

[<span data-ttu-id="0e9f3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0e9f3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
