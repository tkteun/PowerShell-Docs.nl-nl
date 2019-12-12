---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendConfigurationApplyAsync-methode
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941542"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="b0707-103">SendConfigurationApplyAsync-methode</span><span class="sxs-lookup"><span data-stu-id="b0707-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="b0707-104">Hiermee wordt het configuratie document asynchroon verzonden naar het beheerde knoop punt en wordt de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="b0707-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0707-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b0707-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="b0707-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="b0707-106">Parameters</span></span>

<span data-ttu-id="b0707-107">*ConfigurationData* \[in\] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="b0707-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b0707-108">*dwing* \[in\] **waar** om te voor komen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="b0707-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="b0707-109">*jobId* \[in\] de id van de taak waarvoor de configuratie moet worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="b0707-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0707-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="b0707-110">Return value</span></span>

<span data-ttu-id="b0707-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b0707-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0707-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b0707-112">Remarks</span></span>

<span data-ttu-id="b0707-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="b0707-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0707-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b0707-114">Requirements</span></span>

<span data-ttu-id="b0707-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="b0707-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b0707-116">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b0707-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b0707-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b0707-117">See also</span></span>

[<span data-ttu-id="b0707-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b0707-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
