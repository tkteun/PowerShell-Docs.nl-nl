---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683938"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e4003-103">De SendConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e4003-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e4003-104">Het configuratiebestand voor verzendt naar de beheerd knooppunt en wordt deze opgeslagen als een wijziging in behandeling.</span><span class="sxs-lookup"><span data-stu-id="e4003-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4003-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e4003-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e4003-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e4003-106">Parameters</span></span>

<span data-ttu-id="e4003-107">*ConfigurationData* \[in\] de omgevingsgegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="e4003-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="e4003-108">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="e4003-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e4003-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e4003-109">Return value</span></span>

<span data-ttu-id="e4003-110">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="e4003-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4003-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e4003-111">Remarks</span></span>

<span data-ttu-id="e4003-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e4003-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4003-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e4003-113">Requirements</span></span>

<span data-ttu-id="e4003-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e4003-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e4003-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e4003-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e4003-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e4003-116">See also</span></span>

[<span data-ttu-id="e4003-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e4003-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)