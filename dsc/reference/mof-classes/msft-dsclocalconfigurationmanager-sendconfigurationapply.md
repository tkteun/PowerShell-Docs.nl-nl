---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048171"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="10524-103">De SendConfigurationApply-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="10524-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="10524-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en maakt gebruik van de Agent configureren om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="10524-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="10524-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="10524-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="10524-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="10524-106">Parameters</span></span>

<span data-ttu-id="10524-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="10524-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="10524-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="10524-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="10524-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="10524-109">Return value</span></span>

<span data-ttu-id="10524-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="10524-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="10524-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="10524-111">Remarks</span></span>

<span data-ttu-id="10524-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="10524-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="10524-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="10524-113">Requirements</span></span>

<span data-ttu-id="10524-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="10524-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="10524-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="10524-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="10524-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="10524-116">See also</span></span>

[<span data-ttu-id="10524-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="10524-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)