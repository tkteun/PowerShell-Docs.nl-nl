---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationResultOutput-methode
ms.openlocfilehash: 9c81082c28b2ffcc329264d29784782deaa9779d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464074"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="2bf91-103">GetConfigurationResultOutput-methode</span><span class="sxs-lookup"><span data-stu-id="2bf91-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="2bf91-104">Hiermee wordt de uitvoer van de configuratie agent opgehaald die is gekoppeld aan een specifieke taak.</span><span class="sxs-lookup"><span data-stu-id="2bf91-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="2bf91-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2bf91-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="2bf91-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="2bf91-106">Parameters</span></span>

<span data-ttu-id="2bf91-107">**jobId** \[ in \] de id van de taak waarvoor uitvoer gegevens moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2bf91-107">**jobId** \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="2bf91-108">**resumeOutputBookmark** \[ in \] geeft aan dat de uitvoer een voortzetting van een vorige blad wijzer moet zijn.</span><span class="sxs-lookup"><span data-stu-id="2bf91-108">**resumeOutputBookmark** \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="2bf91-109">**uitvoer** \[ \] de uitvoer voor de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="2bf91-109">**output** \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="2bf91-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="2bf91-110">Return value</span></span>

<span data-ttu-id="2bf91-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2bf91-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2bf91-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2bf91-112">Remarks</span></span>

<span data-ttu-id="2bf91-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="2bf91-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2bf91-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2bf91-114">Requirements</span></span>

<span data-ttu-id="2bf91-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="2bf91-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2bf91-116">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2bf91-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2bf91-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2bf91-117">See also</span></span>

[<span data-ttu-id="2bf91-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2bf91-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
