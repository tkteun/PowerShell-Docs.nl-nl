---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationStatus-methode
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942690"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="e909c-103">GetConfigurationStatus-methode</span><span class="sxs-lookup"><span data-stu-id="e909c-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="e909c-104">De geschiedenis van de configuratie status ophalen.</span><span class="sxs-lookup"><span data-stu-id="e909c-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="e909c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e909c-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="e909c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e909c-106">Parameters</span></span>

<span data-ttu-id="e909c-107">*Alle* \[in @ no__t-2 **waar** als deze methode informatie moet retour neren over alle configuratie runs op de computer, met inbegrip van de configuratie toepassing en de consistentie controle.</span><span class="sxs-lookup"><span data-stu-id="e909c-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="e909c-108">*configurationStatus* \[out @ no__t-2 bij Return bevat een Inge sloten instantie van de klasse **MSFT_DSCConfigurationStatus** waarmee de instellingen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e909c-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="e909c-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e909c-109">Return value</span></span>

<span data-ttu-id="e909c-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e909c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e909c-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e909c-111">Remarks</span></span>

<span data-ttu-id="e909c-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e909c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e909c-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e909c-113">Requirements</span></span>

<span data-ttu-id="e909c-114">**MANAGE** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="e909c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e909c-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e909c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e909c-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e909c-116">See also</span></span>

[<span data-ttu-id="e909c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e909c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
