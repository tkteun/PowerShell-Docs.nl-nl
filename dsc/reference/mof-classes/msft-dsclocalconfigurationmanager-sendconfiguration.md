---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078381"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f72b2-103">De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f72b2-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f72b2-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="f72b2-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="f72b2-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f72b2-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="f72b2-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f72b2-106">Parameters</span></span>

<span data-ttu-id="f72b2-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="f72b2-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="f72b2-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="f72b2-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="f72b2-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f72b2-109">Return value</span></span>

<span data-ttu-id="f72b2-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="f72b2-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f72b2-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f72b2-111">Remarks</span></span>

<span data-ttu-id="f72b2-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f72b2-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f72b2-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f72b2-113">Requirements</span></span>

<span data-ttu-id="f72b2-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f72b2-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f72b2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f72b2-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f72b2-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f72b2-116">See also</span></span>

[<span data-ttu-id="f72b2-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f72b2-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)