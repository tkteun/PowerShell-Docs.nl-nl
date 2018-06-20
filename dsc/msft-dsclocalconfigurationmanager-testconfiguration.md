---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De TestConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2df04d317bd5e7a5c2a713d92be57c5c9a9f5e8c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219008"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8f668-103">De TestConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8f668-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8f668-104">Het configuratiebestand voor het beheerde knooppunt verzendt en controleert of de huidige configuratie op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="8f668-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="8f668-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8f668-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="8f668-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="8f668-106">Parameters</span></span>
----------

<span data-ttu-id="8f668-107">*configurationData* \[in\] omgevingsgegevens voor de confuguration.</span><span class="sxs-lookup"><span data-stu-id="8f668-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="8f668-108">*InDesiredState* \[uit\] bij resultaat, geeft aan of het beheerde knooppunt in de status van de opgegeven door het configuratie-document.</span><span class="sxs-lookup"><span data-stu-id="8f668-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="8f668-109">*ResourcesInDesiredState* \[uit\] op return bevat een ingesloten exemplaar van de **MSFT_ResourceInDesiredState** klasse waarmee bronnen die zich in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="8f668-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="8f668-110">*ResourcesNotInDesiredState* \[uit\] op return bevat een ingesloten exemplaar van de **MSFT_ResourceNotInDesiredState** klasse waarmee bronnen die zich niet in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="8f668-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="8f668-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="8f668-111">Return value</span></span>
------------

<span data-ttu-id="8f668-112">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="8f668-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8f668-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8f668-113">Remarks</span></span>

<span data-ttu-id="8f668-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="8f668-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8f668-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8f668-115">Requirements</span></span>
------------
><span data-ttu-id="8f668-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8f668-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8f668-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8f668-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8f668-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8f668-118">See also</span></span>


[<span data-ttu-id="8f668-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8f668-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)