---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfiguration-methode
description: GetConfiguration-methode
ms.openlocfilehash: a49f810bd227142c8c3ae4de45f69450400e4e8c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650877"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="e30de-103">GetConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="e30de-103">GetConfiguration method</span></span>

<span data-ttu-id="e30de-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de **Get** -methode van de configuratie agent gebruikt om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="e30de-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="e30de-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e30de-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="e30de-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e30de-106">Parameters</span></span>

<span data-ttu-id="e30de-107">**configurationData** \[ in \] geeft de configuratie gegevens op die moeten worden verzonden.</span><span class="sxs-lookup"><span data-stu-id="e30de-107">**configurationData** \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="e30de-108">**configuraties** \[ out \] on return bevat een Inge sloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="e30de-108">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="e30de-109">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e30de-109">Return value</span></span>

<span data-ttu-id="e30de-110">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e30de-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e30de-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e30de-111">Remarks</span></span>

<span data-ttu-id="e30de-112">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e30de-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e30de-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e30de-113">Requirements</span></span>

<span data-ttu-id="e30de-114">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="e30de-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e30de-115">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e30de-115">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e30de-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e30de-116">See also</span></span>

[<span data-ttu-id="e30de-117">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e30de-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
