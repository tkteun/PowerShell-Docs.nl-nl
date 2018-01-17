---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3ce47-103">GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="3ce47-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3ce47-104">Hiermee wordt de uitvoer van de Configuration-Agent die is gekoppeld aan een specifieke taak opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3ce47-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="3ce47-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3ce47-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="3ce47-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3ce47-106">Parameters</span></span>
----------

<span data-ttu-id="3ce47-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3ce47-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="3ce47-108">De ID van de taak voor die uitvoergegevens ophalen.</span><span class="sxs-lookup"><span data-stu-id="3ce47-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="3ce47-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="3ce47-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="3ce47-110">Hiermee geeft u de uitvoer moet een vervolg van een vorige bladwijzer.</span><span class="sxs-lookup"><span data-stu-id="3ce47-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="3ce47-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="3ce47-111">*output* \[out\]</span></span>  
<span data-ttu-id="3ce47-112">De uitvoer voor de gespecificeerde taak.</span><span class="sxs-lookup"><span data-stu-id="3ce47-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="3ce47-113">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="3ce47-113">Return value</span></span>
------------

<span data-ttu-id="3ce47-114">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="3ce47-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3ce47-115">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3ce47-115">Remarks</span></span>

<span data-ttu-id="3ce47-116">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="3ce47-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3ce47-117">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3ce47-117">Requirements</span></span>
------------
><span data-ttu-id="3ce47-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3ce47-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="3ce47-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3ce47-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="3ce47-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3ce47-120">See also</span></span>


[<span data-ttu-id="3ce47-121">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3ce47-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



