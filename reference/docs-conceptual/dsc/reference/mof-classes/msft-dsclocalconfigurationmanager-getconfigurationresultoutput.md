---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationResultOutput-methode
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941570"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="d5f31-103">GetConfigurationResultOutput-methode</span><span class="sxs-lookup"><span data-stu-id="d5f31-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="d5f31-104">Hiermee wordt de uitvoer van de configuratie agent opgehaald die is gekoppeld aan een specifieke taak.</span><span class="sxs-lookup"><span data-stu-id="d5f31-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="d5f31-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d5f31-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="d5f31-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="d5f31-106">Parameters</span></span>

<span data-ttu-id="d5f31-107">*jobId* \[in\] de id van de taak waarvoor uitvoer gegevens moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d5f31-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="d5f31-108">*resumeOutputBookmark* \[in\] geeft aan dat de uitvoer een voortzetting van een vorige blad wijzer moet zijn.</span><span class="sxs-lookup"><span data-stu-id="d5f31-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="d5f31-109">*uitvoer* \[\] de uitvoer voor de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="d5f31-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="d5f31-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="d5f31-110">Return value</span></span>

<span data-ttu-id="d5f31-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d5f31-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5f31-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d5f31-112">Remarks</span></span>

<span data-ttu-id="d5f31-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="d5f31-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d5f31-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d5f31-114">Requirements</span></span>

<span data-ttu-id="d5f31-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="d5f31-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d5f31-116">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d5f31-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d5f31-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d5f31-117">See also</span></span>

[<span data-ttu-id="d5f31-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d5f31-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
