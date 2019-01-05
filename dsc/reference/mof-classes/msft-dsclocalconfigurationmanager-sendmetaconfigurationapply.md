---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048330"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7740d-103">De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7740d-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7740d-104">Hiermee stelt de Local Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie van Agent.</span><span class="sxs-lookup"><span data-stu-id="7740d-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="7740d-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7740d-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="7740d-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7740d-106">Parameters</span></span>

<span data-ttu-id="7740d-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="7740d-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7740d-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="7740d-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7740d-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="7740d-109">Return value</span></span>

<span data-ttu-id="7740d-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="7740d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7740d-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7740d-111">Remarks</span></span>

<span data-ttu-id="7740d-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="7740d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7740d-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7740d-113">Requirements</span></span>

<span data-ttu-id="7740d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7740d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7740d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7740d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7740d-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7740d-116">See also</span></span>

[<span data-ttu-id="7740d-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7740d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)