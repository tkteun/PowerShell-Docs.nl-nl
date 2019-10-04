---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendConfigurationApply-methode
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942599"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="3ed2c-103">SendConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="3ed2c-103">SendConfigurationApply method</span></span>

<span data-ttu-id="3ed2c-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="3ed2c-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="3ed2c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3ed2c-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3ed2c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3ed2c-106">Parameters</span></span>

<span data-ttu-id="3ed2c-107">*ConfigurationData* \[in @ no__t-2 de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="3ed2c-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="3ed2c-108">*force* \[in @ no__t-2 **True** om te voor komen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="3ed2c-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ed2c-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="3ed2c-109">Return value</span></span>

<span data-ttu-id="3ed2c-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3ed2c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ed2c-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3ed2c-111">Remarks</span></span>

<span data-ttu-id="3ed2c-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="3ed2c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ed2c-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3ed2c-113">Requirements</span></span>

<span data-ttu-id="3ed2c-114">**MANAGE** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="3ed2c-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3ed2c-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ed2c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3ed2c-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3ed2c-116">See also</span></span>

[<span data-ttu-id="3ed2c-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3ed2c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
