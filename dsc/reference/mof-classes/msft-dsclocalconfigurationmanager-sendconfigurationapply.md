---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfigurationApply-methode
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727013"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="0801d-103">De SendConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="0801d-103">SendConfigurationApply method</span></span>

<span data-ttu-id="0801d-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de Agent configureren om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="0801d-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0801d-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0801d-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="0801d-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="0801d-106">Parameters</span></span>

<span data-ttu-id="0801d-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="0801d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="0801d-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="0801d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="0801d-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="0801d-109">Return value</span></span>

<span data-ttu-id="0801d-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="0801d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0801d-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0801d-111">Remarks</span></span>

<span data-ttu-id="0801d-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="0801d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0801d-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0801d-113">Requirements</span></span>

<span data-ttu-id="0801d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="0801d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0801d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0801d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0801d-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0801d-116">See also</span></span>

[<span data-ttu-id="0801d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0801d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
