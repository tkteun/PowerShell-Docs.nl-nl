---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403923"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c7ab9-103">De SendMetaConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c7ab9-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c7ab9-104">Hiermee stelt de Local Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie van Agent.</span><span class="sxs-lookup"><span data-stu-id="c7ab9-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="c7ab9-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c7ab9-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c7ab9-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="c7ab9-106">Parameters</span></span>

<span data-ttu-id="c7ab9-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="c7ab9-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="c7ab9-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="c7ab9-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7ab9-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="c7ab9-109">Return value</span></span>

<span data-ttu-id="c7ab9-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="c7ab9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7ab9-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c7ab9-111">Remarks</span></span>

<span data-ttu-id="c7ab9-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="c7ab9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c7ab9-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c7ab9-113">Requirements</span></span>

<span data-ttu-id="c7ab9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c7ab9-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c7ab9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c7ab9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c7ab9-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c7ab9-116">See also</span></span>

[<span data-ttu-id="c7ab9-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c7ab9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)