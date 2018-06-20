---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34186803"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="be378-103">De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="be378-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="be378-104">Hiermee wordt de uitvoer van de Configuration-Agent die is gekoppeld aan een specifieke taak opgehaald.</span><span class="sxs-lookup"><span data-stu-id="be378-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="be378-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="be378-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="be378-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="be378-106">Parameters</span></span>
----------

<span data-ttu-id="be378-107">*jobId* \[in\] de ID van de taak voor die uitvoergegevens ophalen.</span><span class="sxs-lookup"><span data-stu-id="be378-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="be378-108">*resumeOutputBookmark* \[in\] Hiermee geeft u de uitvoer moet een vervolg van een vorige bladwijzer.</span><span class="sxs-lookup"><span data-stu-id="be378-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="be378-109">*uitvoer* \[uit\] de uitvoer voor de opgegeven taak.</span><span class="sxs-lookup"><span data-stu-id="be378-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="be378-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="be378-110">Return value</span></span>
------------

<span data-ttu-id="be378-111">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="be378-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="be378-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="be378-112">Remarks</span></span>

<span data-ttu-id="be378-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="be378-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="be378-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="be378-114">Requirements</span></span>
------------
><span data-ttu-id="be378-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="be378-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="be378-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="be378-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="be378-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="be378-117">See also</span></span>


[<span data-ttu-id="be378-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="be378-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)