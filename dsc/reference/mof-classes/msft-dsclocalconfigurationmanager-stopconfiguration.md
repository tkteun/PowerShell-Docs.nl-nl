---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048174"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="043c4-103">De StopConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="043c4-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="043c4-104">Hiermee stopt u de wijziging in de configuratie die wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="043c4-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="043c4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="043c4-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="043c4-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="043c4-106">Parameters</span></span>

<span data-ttu-id="043c4-107">*afdwingen dat* \[in\] **waar** om af te dwingen de configuratie om te stoppen.</span><span class="sxs-lookup"><span data-stu-id="043c4-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="043c4-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="043c4-108">Return value</span></span>

<span data-ttu-id="043c4-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="043c4-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="043c4-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="043c4-110">Remarks</span></span>

<span data-ttu-id="043c4-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="043c4-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="043c4-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="043c4-112">Requirements</span></span>

<span data-ttu-id="043c4-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="043c4-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="043c4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="043c4-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="043c4-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="043c4-115">See also</span></span>

[<span data-ttu-id="043c4-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="043c4-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)