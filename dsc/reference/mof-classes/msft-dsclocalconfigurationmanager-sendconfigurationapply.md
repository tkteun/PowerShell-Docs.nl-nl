---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078250"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="06ee3-103">De SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="06ee3-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="06ee3-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de Agent configureren om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="06ee3-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="06ee3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="06ee3-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="06ee3-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="06ee3-106">Parameters</span></span>

<span data-ttu-id="06ee3-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="06ee3-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="06ee3-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="06ee3-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="06ee3-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="06ee3-109">Return value</span></span>

<span data-ttu-id="06ee3-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="06ee3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="06ee3-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="06ee3-111">Remarks</span></span>

<span data-ttu-id="06ee3-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="06ee3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="06ee3-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="06ee3-113">Requirements</span></span>

<span data-ttu-id="06ee3-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="06ee3-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="06ee3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="06ee3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="06ee3-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="06ee3-116">See also</span></span>

[<span data-ttu-id="06ee3-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="06ee3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)