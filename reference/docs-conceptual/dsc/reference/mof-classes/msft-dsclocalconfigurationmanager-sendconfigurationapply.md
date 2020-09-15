---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: SendConfigurationApply-methode
ms.openlocfilehash: 9b684790e5a7d6c7bdf074caca6040e13807f1ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464312"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="25753-103">SendConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="25753-103">SendConfigurationApply method</span></span>

<span data-ttu-id="25753-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="25753-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="25753-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="25753-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="25753-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="25753-106">Parameters</span></span>

<span data-ttu-id="25753-107">**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="25753-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="25753-108">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="25753-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="25753-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="25753-109">Return value</span></span>

<span data-ttu-id="25753-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="25753-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="25753-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="25753-111">Remarks</span></span>

<span data-ttu-id="25753-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="25753-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="25753-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="25753-113">Requirements</span></span>

<span data-ttu-id="25753-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="25753-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="25753-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="25753-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="25753-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="25753-116">See also</span></span>

[<span data-ttu-id="25753-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="25753-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
