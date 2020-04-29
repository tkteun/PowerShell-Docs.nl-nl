---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: StopConfiguration-methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941528"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="da8e1-103">StopConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="da8e1-103">StopConfiguration method</span></span>

<span data-ttu-id="da8e1-104">Hiermee stopt u de configuratie wijziging die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="da8e1-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="da8e1-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="da8e1-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="da8e1-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="da8e1-106">Parameters</span></span>

<span data-ttu-id="da8e1-107">*geforceerd* \[in\] op **waar** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="da8e1-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="da8e1-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="da8e1-108">Return value</span></span>

<span data-ttu-id="da8e1-109">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="da8e1-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="da8e1-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="da8e1-110">Remarks</span></span>

<span data-ttu-id="da8e1-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="da8e1-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="da8e1-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="da8e1-112">Requirements</span></span>

<span data-ttu-id="da8e1-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="da8e1-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="da8e1-114">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="da8e1-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="da8e1-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="da8e1-115">See also</span></span>

[<span data-ttu-id="da8e1-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="da8e1-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
