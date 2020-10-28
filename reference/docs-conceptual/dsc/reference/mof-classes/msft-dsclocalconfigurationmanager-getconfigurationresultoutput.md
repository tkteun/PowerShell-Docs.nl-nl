---
ms.date: 07/17/2020
ms.topic: reference
title: GetConfigurationResultOutput-methode
description: GetConfigurationResultOutput-methode
ms.openlocfilehash: 7c885109b3078189b7ac653733a5fb24db66312e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644705"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="11605-103">GetConfigurationResultOutput-methode</span><span class="sxs-lookup"><span data-stu-id="11605-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="11605-104">Hiermee wordt de uitvoer van de configuratie agent opgehaald die is gekoppeld aan een specifieke taak.</span><span class="sxs-lookup"><span data-stu-id="11605-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="11605-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="11605-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="11605-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="11605-106">Parameters</span></span>

<span data-ttu-id="11605-107">**jobId** \[ in \] de id van de taak waarvoor uitvoer gegevens moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="11605-107">**jobId** \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="11605-108">**resumeOutputBookmark** \[ in \] geeft aan dat de uitvoer een voortzetting van een vorige blad wijzer moet zijn.</span><span class="sxs-lookup"><span data-stu-id="11605-108">**resumeOutputBookmark** \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="11605-109">**uitvoer** \[ \] de uitvoer voor de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="11605-109">**output** \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="11605-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="11605-110">Return value</span></span>

<span data-ttu-id="11605-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="11605-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="11605-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="11605-112">Remarks</span></span>

<span data-ttu-id="11605-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="11605-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="11605-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="11605-114">Requirements</span></span>

<span data-ttu-id="11605-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="11605-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="11605-116">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="11605-116">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="11605-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11605-117">See also</span></span>

[<span data-ttu-id="11605-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="11605-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
