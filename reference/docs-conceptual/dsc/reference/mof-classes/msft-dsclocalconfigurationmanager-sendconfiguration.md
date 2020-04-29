---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendConfiguration-methode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941549"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="a026d-103">SendConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="a026d-103">SendConfiguration method</span></span>

<span data-ttu-id="a026d-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="a026d-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="a026d-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a026d-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="a026d-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a026d-106">Parameters</span></span>

<span data-ttu-id="a026d-107">*ConfigurationData* \[in\] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="a026d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a026d-108">*geforceerd* \[in\] op **waar** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="a026d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="a026d-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="a026d-109">Return value</span></span>

<span data-ttu-id="a026d-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a026d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a026d-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a026d-111">Remarks</span></span>

<span data-ttu-id="a026d-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="a026d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a026d-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a026d-113">Requirements</span></span>

<span data-ttu-id="a026d-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="a026d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a026d-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a026d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a026d-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a026d-116">See also</span></span>

[<span data-ttu-id="a026d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a026d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
