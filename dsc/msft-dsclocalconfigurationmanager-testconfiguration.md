---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De TestConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7815d458a9a67639a31c917510097212d104eb8a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bca5e-103">De TestConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="bca5e-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bca5e-104">Het configuratiebestand voor het beheerde knooppunt verzendt en controleert of de huidige configuratie op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="bca5e-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="bca5e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="bca5e-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="bca5e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="bca5e-106">Parameters</span></span>
----------

<span data-ttu-id="bca5e-107">*configurationData* \[in\] omgevingsgegevens voor de confuguration.</span><span class="sxs-lookup"><span data-stu-id="bca5e-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="bca5e-108">*InDesiredState* \[uit\] bij resultaat, geeft aan of het beheerde knooppunt in de status van de opgegeven door het configuratie-document.</span><span class="sxs-lookup"><span data-stu-id="bca5e-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="bca5e-109">*ResourcesInDesiredState* \[uit\] op return bevat een ingesloten exemplaar van de **MSFT_ResourceInDesiredState** klasse waarmee bronnen die zich in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="bca5e-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="bca5e-110">*ResourcesNotInDesiredState* \[uit\] op return bevat een ingesloten exemplaar van de **MSFT_ResourceNotInDesiredState** klasse waarmee bronnen die zich niet in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="bca5e-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="bca5e-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="bca5e-111">Return value</span></span>
------------

<span data-ttu-id="bca5e-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="bca5e-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bca5e-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="bca5e-113">Remarks</span></span>

<span data-ttu-id="bca5e-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="bca5e-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bca5e-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bca5e-115">Requirements</span></span>
------------
><span data-ttu-id="bca5e-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bca5e-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bca5e-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bca5e-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bca5e-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bca5e-118">See also</span></span>


[<span data-ttu-id="bca5e-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bca5e-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)