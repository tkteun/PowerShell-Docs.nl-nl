---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: StopConfiguration-methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941528"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="fc994-103">StopConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="fc994-103">StopConfiguration method</span></span>

<span data-ttu-id="fc994-104">Hiermee stopt u de configuratie wijziging die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fc994-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc994-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fc994-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="fc994-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="fc994-106">Parameters</span></span>

<span data-ttu-id="fc994-107">*dwing* \[in\] **waar** om te voor komen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="fc994-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc994-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="fc994-108">Return value</span></span>

<span data-ttu-id="fc994-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fc994-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fc994-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="fc994-110">Remarks</span></span>

<span data-ttu-id="fc994-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="fc994-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc994-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fc994-112">Requirements</span></span>

<span data-ttu-id="fc994-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="fc994-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fc994-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc994-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fc994-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fc994-115">See also</span></span>

[<span data-ttu-id="fc994-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="fc994-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
