---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: TestConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d6678-103">TestConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d6678-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d6678-104">Het configuratiebestand voor het beheerde knooppunt verzendt en controleert of de huidige configuratie op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="d6678-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="d6678-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d6678-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="d6678-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="d6678-106">Parameters</span></span>
----------

<span data-ttu-id="d6678-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d6678-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="d6678-108">De omgevingsgegevens voor de confuguration.</span><span class="sxs-lookup"><span data-stu-id="d6678-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="d6678-109">*InDesiredState* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="d6678-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="d6678-110">Bij resultaat, geeft aan of het beheerde knooppunt in de status van de opgegeven door het configuratie-document.</span><span class="sxs-lookup"><span data-stu-id="d6678-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="d6678-111">*ResourcesInDesiredState* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="d6678-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="d6678-112">Op return bevat een ingesloten exemplaar van de **MSFT_ResourceInDesiredState** klasse waarmee bronnen die zich in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="d6678-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="d6678-113">*ResourcesNotInDesiredState* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="d6678-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="d6678-114">Op return bevat een ingesloten exemplaar van de **MSFT_ResourceNotInDesiredState** klasse waarmee bronnen die zich niet in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="d6678-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6678-115">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="d6678-115">Return value</span></span>
------------

<span data-ttu-id="d6678-116">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="d6678-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6678-117">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d6678-117">Remarks</span></span>

<span data-ttu-id="d6678-118">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="d6678-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6678-119">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d6678-119">Requirements</span></span>
------------
><span data-ttu-id="d6678-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d6678-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="d6678-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d6678-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="d6678-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d6678-122">See also</span></span>


[<span data-ttu-id="d6678-123">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d6678-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



