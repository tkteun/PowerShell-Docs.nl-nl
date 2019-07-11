---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De StopConfiguration-methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727000"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="19d6e-103">De StopConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="19d6e-103">StopConfiguration method</span></span>

<span data-ttu-id="19d6e-104">Hiermee stopt u de wijziging in de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="19d6e-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="19d6e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="19d6e-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="19d6e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="19d6e-106">Parameters</span></span>

<span data-ttu-id="19d6e-107">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="19d6e-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="19d6e-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="19d6e-108">Return value</span></span>

<span data-ttu-id="19d6e-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="19d6e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="19d6e-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="19d6e-110">Remarks</span></span>

<span data-ttu-id="19d6e-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="19d6e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="19d6e-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="19d6e-112">Requirements</span></span>

<span data-ttu-id="19d6e-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="19d6e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="19d6e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="19d6e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="19d6e-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="19d6e-115">See also</span></span>

[<span data-ttu-id="19d6e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="19d6e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
