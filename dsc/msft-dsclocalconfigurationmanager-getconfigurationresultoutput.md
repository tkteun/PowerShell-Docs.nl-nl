---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6190c-103">GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6190c-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6190c-104">Hiermee wordt de uitvoer van de Configuration-Agent die is gekoppeld aan een specifieke taak opgehaald.</span><span class="sxs-lookup"><span data-stu-id="6190c-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="6190c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6190c-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="6190c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="6190c-106">Parameters</span></span>
----------

<span data-ttu-id="6190c-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6190c-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="6190c-108">De ID van de taak voor die uitvoergegevens ophalen.</span><span class="sxs-lookup"><span data-stu-id="6190c-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="6190c-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6190c-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="6190c-110">Hiermee geeft u de uitvoer moet een vervolg van een vorige bladwijzer.</span><span class="sxs-lookup"><span data-stu-id="6190c-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="6190c-111">*uitvoer* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="6190c-111">*output* \[out\]</span></span>  
<span data-ttu-id="6190c-112">De uitvoer voor de gespecificeerde taak.</span><span class="sxs-lookup"><span data-stu-id="6190c-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="6190c-113">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="6190c-113">Return value</span></span>
------------

<span data-ttu-id="6190c-114">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="6190c-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6190c-115">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6190c-115">Remarks</span></span>

<span data-ttu-id="6190c-116">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="6190c-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6190c-117">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6190c-117">Requirements</span></span>
------------
><span data-ttu-id="6190c-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6190c-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6190c-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6190c-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6190c-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6190c-120">See also</span></span>


[<span data-ttu-id="6190c-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6190c-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



