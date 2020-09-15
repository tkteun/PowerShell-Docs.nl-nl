---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: SendMetaConfigurationApply-methode
ms.openlocfilehash: 896afe2f3370e108b48583aafb33ee7b0eb1301b
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463717"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="8d6e4-103">SendMetaConfigurationApply-methode</span><span class="sxs-lookup"><span data-stu-id="8d6e4-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="8d6e4-104">Hiermee stelt u de lokale Configuration Manager-instellingen in die worden gebruikt voor het beheren van de configuratie agent.</span><span class="sxs-lookup"><span data-stu-id="8d6e4-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d6e4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8d6e4-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="8d6e4-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="8d6e4-106">Parameters</span></span>

<span data-ttu-id="8d6e4-107">**ConfigurationData** \[ in \] de omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="8d6e4-107">**ConfigurationData** \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="8d6e4-108">**forceren** \[ in \] **True** om te zorgen dat de configuratie wordt gestopt.</span><span class="sxs-lookup"><span data-stu-id="8d6e4-108">**force** \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="8d6e4-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="8d6e4-109">Return value</span></span>

<span data-ttu-id="8d6e4-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="8d6e4-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d6e4-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8d6e4-111">Remarks</span></span>

<span data-ttu-id="8d6e4-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="8d6e4-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d6e4-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8d6e4-113">Requirements</span></span>

<span data-ttu-id="8d6e4-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="8d6e4-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8d6e4-115">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d6e4-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8d6e4-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8d6e4-116">See also</span></span>

[<span data-ttu-id="8d6e4-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8d6e4-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
