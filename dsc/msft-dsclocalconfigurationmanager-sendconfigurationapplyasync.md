---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893890"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="21fed-103">De SendConfigurationApplyAsync-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="21fed-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="21fed-104">Het configuratiebestand voor asynchroon verzendt naar de beheerd knooppunt en maakt gebruik van de Agent configureren om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="21fed-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="21fed-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="21fed-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="21fed-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="21fed-106">Parameters</span></span>

<span data-ttu-id="21fed-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="21fed-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="21fed-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="21fed-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="21fed-109">*jobId* \[in\] de ID van de taak voor voor het verzenden van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="21fed-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="21fed-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="21fed-110">Return value</span></span>

<span data-ttu-id="21fed-111">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="21fed-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="21fed-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="21fed-112">Remarks</span></span>

<span data-ttu-id="21fed-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="21fed-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="21fed-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="21fed-114">Requirements</span></span>

<span data-ttu-id="21fed-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="21fed-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="21fed-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="21fed-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="21fed-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="21fed-117">See also</span></span>

[<span data-ttu-id="21fed-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="21fed-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)