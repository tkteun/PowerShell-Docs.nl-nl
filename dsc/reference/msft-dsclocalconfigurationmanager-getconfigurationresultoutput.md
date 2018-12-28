---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ea572a4a66befd4e4b8d83e2957632b1b5ed7d93
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404294"
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="64571-103">De GetConfigurationResultOutput-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="64571-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="64571-104">Hiermee haalt u de uitvoer van de Configuration-Agent die is gekoppeld aan een specifieke taak.</span><span class="sxs-lookup"><span data-stu-id="64571-104">Gets the Configuration Agent output associated with a specific job.</span></span>

## <a name="syntax"></a><span data-ttu-id="64571-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="64571-105">Syntax</span></span>

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

## <a name="parameters"></a><span data-ttu-id="64571-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="64571-106">Parameters</span></span>

<span data-ttu-id="64571-107">*jobId* \[in\] de ID van de taak waarvoor u uitvoergegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="64571-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="64571-108">*resumeOutputBookmark* \[in\] geeft aan dat de uitvoer er een voortzetting van een vorige bladwijzer moet.</span><span class="sxs-lookup"><span data-stu-id="64571-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="64571-109">*uitvoer* \[uit\] de uitvoer voor de gespecificeerde taak.</span><span class="sxs-lookup"><span data-stu-id="64571-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="64571-110">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="64571-110">Return value</span></span>

<span data-ttu-id="64571-111">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="64571-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="64571-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="64571-112">Remarks</span></span>

<span data-ttu-id="64571-113">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="64571-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="64571-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="64571-114">Requirements</span></span>

<span data-ttu-id="64571-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="64571-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="64571-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="64571-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="64571-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="64571-117">See also</span></span>

[<span data-ttu-id="64571-118">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="64571-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)