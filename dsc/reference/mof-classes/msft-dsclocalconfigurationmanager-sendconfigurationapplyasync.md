---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfigurationApplyAsync-methode
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734297"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="7adbc-103">De SendConfigurationApplyAsync-methode</span><span class="sxs-lookup"><span data-stu-id="7adbc-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="7adbc-104">Het configuratiebestand voor asynchroon verzendt naar de beheerd knooppunt en maakt gebruik van de Agent configureren om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="7adbc-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="7adbc-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7adbc-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="7adbc-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7adbc-106">Parameters</span></span>

<span data-ttu-id="7adbc-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="7adbc-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7adbc-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="7adbc-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="7adbc-109">*jobId* \[in\] de ID van de taak voor voor het verzenden van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="7adbc-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7adbc-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="7adbc-110">Return value</span></span>

<span data-ttu-id="7adbc-111">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="7adbc-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7adbc-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7adbc-112">Remarks</span></span>

<span data-ttu-id="7adbc-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="7adbc-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7adbc-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7adbc-114">Requirements</span></span>

<span data-ttu-id="7adbc-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7adbc-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7adbc-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7adbc-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7adbc-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7adbc-117">See also</span></span>

[<span data-ttu-id="7adbc-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7adbc-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
