---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: GetConfigurationResultOutput-methode
ms.openlocfilehash: 480e710ce1a208253f0e664474c3e9bab296066a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941570"
---
# <a name="getconfigurationresultoutput-method"></a><span data-ttu-id="49aaa-103">GetConfigurationResultOutput-methode</span><span class="sxs-lookup"><span data-stu-id="49aaa-103">GetConfigurationResultOutput method</span></span>

<span data-ttu-id="49aaa-104">Hiermee wordt de uitvoer van de configuratie agent opgehaald die is gekoppeld aan een specifieke taak.</span><span class="sxs-lookup"><span data-stu-id="49aaa-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="49aaa-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="49aaa-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="49aaa-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="49aaa-106">Parameters</span></span>

<span data-ttu-id="49aaa-107">*jobId* \[in\] de id van de taak waarvoor uitvoer gegevens moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="49aaa-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="49aaa-108">*resumeOutputBookmark* \[in\] geeft aan dat de uitvoer een voortzetting van een vorige blad wijzer moet zijn.</span><span class="sxs-lookup"><span data-stu-id="49aaa-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="49aaa-109">*uitvoer* \[\] de uitvoer voor de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="49aaa-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="49aaa-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="49aaa-110">Return value</span></span>

<span data-ttu-id="49aaa-111">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="49aaa-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="49aaa-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="49aaa-112">Remarks</span></span>

<span data-ttu-id="49aaa-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="49aaa-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="49aaa-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="49aaa-114">Requirements</span></span>

<span data-ttu-id="49aaa-115">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="49aaa-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="49aaa-116">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="49aaa-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="49aaa-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="49aaa-117">See also</span></span>

[<span data-ttu-id="49aaa-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="49aaa-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
