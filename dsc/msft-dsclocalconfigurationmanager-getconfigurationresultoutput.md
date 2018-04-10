---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f4c2ddaa37cdafeff1a442f3f1fa656788a1c6c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a180c-103">De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a180c-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a180c-104">Hiermee wordt de uitvoer van de Configuration-Agent die is gekoppeld aan een specifieke taak opgehaald.</span><span class="sxs-lookup"><span data-stu-id="a180c-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="a180c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a180c-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="a180c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a180c-106">Parameters</span></span>
----------

<span data-ttu-id="a180c-107">*jobId* \[in\] de ID van de taak voor die uitvoergegevens ophalen.</span><span class="sxs-lookup"><span data-stu-id="a180c-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="a180c-108">*resumeOutputBookmark* \[in\] Hiermee geeft u de uitvoer moet een vervolg van een vorige bladwijzer.</span><span class="sxs-lookup"><span data-stu-id="a180c-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="a180c-109">*uitvoer* \[uit\] de uitvoer voor de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="a180c-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="a180c-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="a180c-110">Return value</span></span>
------------

<span data-ttu-id="a180c-111">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="a180c-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a180c-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a180c-112">Remarks</span></span>

<span data-ttu-id="a180c-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="a180c-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a180c-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a180c-114">Requirements</span></span>
------------
><span data-ttu-id="a180c-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a180c-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a180c-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a180c-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a180c-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a180c-117">See also</span></span>


[<span data-ttu-id="a180c-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a180c-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)