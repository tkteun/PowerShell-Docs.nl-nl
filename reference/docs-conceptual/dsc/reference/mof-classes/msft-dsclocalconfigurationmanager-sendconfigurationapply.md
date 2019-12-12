---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendConfigurationApply-methode
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942599"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="d47a8-103">SendConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="d47a8-103">SendConfigurationApply method</span></span>

<span data-ttu-id="d47a8-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="d47a8-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d47a8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d47a8-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d47a8-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="d47a8-106">Parameters</span></span>

<span data-ttu-id="d47a8-107">*ConfigurationData* \[in\] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="d47a8-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="d47a8-108">*dwing* \[in\] **waar** om te voor komen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="d47a8-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="d47a8-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="d47a8-109">Return value</span></span>

<span data-ttu-id="d47a8-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d47a8-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d47a8-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d47a8-111">Remarks</span></span>

<span data-ttu-id="d47a8-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="d47a8-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d47a8-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d47a8-113">Requirements</span></span>

<span data-ttu-id="d47a8-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="d47a8-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d47a8-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d47a8-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d47a8-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d47a8-116">See also</span></span>

[<span data-ttu-id="d47a8-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d47a8-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
