---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationStatus-methode
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942690"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="2aedd-103">GetConfigurationStatus-methode</span><span class="sxs-lookup"><span data-stu-id="2aedd-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="2aedd-104">De geschiedenis van de configuratie status ophalen.</span><span class="sxs-lookup"><span data-stu-id="2aedd-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="2aedd-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2aedd-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="2aedd-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="2aedd-106">Parameters</span></span>

<span data-ttu-id="2aedd-107">*Alle* \[in\] **waar** als deze methode informatie moet retour neren over alle configuratie runs op de computer, met inbegrip van de configuratie toepassing en de consistentie controle.</span><span class="sxs-lookup"><span data-stu-id="2aedd-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="2aedd-108">*configurationStatus* \[out\] als resultaat, bevat een Inge sloten instantie van de **MSFT_DSCConfigurationStatus** -klasse die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="2aedd-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="2aedd-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="2aedd-109">Return value</span></span>

<span data-ttu-id="2aedd-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2aedd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2aedd-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2aedd-111">Remarks</span></span>

<span data-ttu-id="2aedd-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="2aedd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2aedd-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2aedd-113">Requirements</span></span>

<span data-ttu-id="2aedd-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="2aedd-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2aedd-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2aedd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2aedd-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2aedd-116">See also</span></span>

[<span data-ttu-id="2aedd-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2aedd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
