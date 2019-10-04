---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: TestConfiguration-methode
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942585"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="401bf-103">TestConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="401bf-103">TestConfiguration method</span></span>

<span data-ttu-id="401bf-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de huidige configuratie gecontroleerd op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="401bf-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="401bf-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="401bf-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="401bf-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="401bf-106">Parameters</span></span>

<span data-ttu-id="401bf-107">*configurationData* \[in @ no__t-2-omgevings gegevens voor de confuguration.</span><span class="sxs-lookup"><span data-stu-id="401bf-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="401bf-108">*InDesiredState* \[out @ no__t-2 bij Return geeft aan of het beheerde knoop punt zich in de staat bevindt die is opgegeven in het configuratie document.</span><span class="sxs-lookup"><span data-stu-id="401bf-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="401bf-109">*ResourcesInDesiredState* \[out @ no__t-2 bij Return bevat een Inge sloten instantie van de klasse **MSFT_ResourceInDesiredState** waarmee resources worden opgegeven die de gewenste status hebben.</span><span class="sxs-lookup"><span data-stu-id="401bf-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="401bf-110">*ResourcesNotInDesiredState* \[out @ no__t-2 bij Return bevat een Inge sloten instantie van de klasse **MSFT_ResourceNotInDesiredState** waarmee resources worden opgegeven die niet de gewenste status hebben.</span><span class="sxs-lookup"><span data-stu-id="401bf-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="401bf-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="401bf-111">Return value</span></span>

<span data-ttu-id="401bf-112">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="401bf-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="401bf-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="401bf-113">Remarks</span></span>

<span data-ttu-id="401bf-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="401bf-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="401bf-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="401bf-115">Requirements</span></span>

<span data-ttu-id="401bf-116">**MANAGE** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="401bf-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="401bf-117">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="401bf-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="401bf-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="401bf-118">See also</span></span>

[<span data-ttu-id="401bf-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="401bf-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
