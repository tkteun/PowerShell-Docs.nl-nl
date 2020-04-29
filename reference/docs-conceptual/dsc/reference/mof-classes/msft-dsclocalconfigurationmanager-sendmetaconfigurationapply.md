---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: SendMetaConfigurationApply-methode
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942592"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="5781e-103">SendMetaConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="5781e-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="5781e-104">Hiermee stelt u de lokale Configuration Manager-instellingen in die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="5781e-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="5781e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5781e-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5781e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="5781e-106">Parameters</span></span>

<span data-ttu-id="5781e-107">*ConfigurationData* \[in\] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="5781e-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="5781e-108">*geforceerd* \[in\] op **waar** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="5781e-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5781e-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="5781e-109">Return value</span></span>

<span data-ttu-id="5781e-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="5781e-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5781e-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5781e-111">Remarks</span></span>

<span data-ttu-id="5781e-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="5781e-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5781e-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5781e-113">Requirements</span></span>

<span data-ttu-id="5781e-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="5781e-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5781e-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5781e-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5781e-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5781e-116">See also</span></span>

[<span data-ttu-id="5781e-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5781e-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
