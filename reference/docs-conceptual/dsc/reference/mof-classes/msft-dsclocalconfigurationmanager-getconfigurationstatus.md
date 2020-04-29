---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationStatus-methode
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942690"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="3cdfd-103">GetConfigurationStatus-methode</span><span class="sxs-lookup"><span data-stu-id="3cdfd-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="3cdfd-104">De geschiedenis van de configuratie status ophalen.</span><span class="sxs-lookup"><span data-stu-id="3cdfd-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="3cdfd-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3cdfd-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="3cdfd-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3cdfd-106">Parameters</span></span>

<span data-ttu-id="3cdfd-107">*Alle* \[in\] **waar** als deze methode informatie moet retour neren over alle configuratie runs op de computer, met inbegrip van de configuratie toepassing en de consistentie controle.</span><span class="sxs-lookup"><span data-stu-id="3cdfd-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="3cdfd-108">*configurationStatus* \[out\] on return bevat een Inge sloten instantie van de klasse **MSFT_DSCConfigurationStatus** die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="3cdfd-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="3cdfd-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="3cdfd-109">Return value</span></span>

<span data-ttu-id="3cdfd-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3cdfd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cdfd-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3cdfd-111">Remarks</span></span>

<span data-ttu-id="3cdfd-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="3cdfd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cdfd-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3cdfd-113">Requirements</span></span>

<span data-ttu-id="3cdfd-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="3cdfd-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3cdfd-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3cdfd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3cdfd-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3cdfd-116">See also</span></span>

[<span data-ttu-id="3cdfd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3cdfd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
