---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: TestConfiguration-methode
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942585"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="669d8-103">TestConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="669d8-103">TestConfiguration method</span></span>

<span data-ttu-id="669d8-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de huidige configuratie gecontroleerd op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="669d8-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="669d8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="669d8-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="669d8-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="669d8-106">Parameters</span></span>

<span data-ttu-id="669d8-107">*configurationData* \[in\] omgevings gegevens voor de confuguration.</span><span class="sxs-lookup"><span data-stu-id="669d8-107">*configurationData* \[in\] Environment data for the confuguration.</span></span>

<span data-ttu-id="669d8-108">*InDesiredState* \[out\] bij retour, geeft aan of het beheerde knoop punt zich in de status bevindt die is opgegeven in het configuratie document.</span><span class="sxs-lookup"><span data-stu-id="669d8-108">*InDesiredState* \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="669d8-109">*ResourcesInDesiredState* \[out\] on return bevat een Inge sloten instantie van de klasse **MSFT_ResourceInDesiredState** waarmee resources worden opgegeven die de gewenste status hebben.</span><span class="sxs-lookup"><span data-stu-id="669d8-109">*ResourcesInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="669d8-110">*ResourcesNotInDesiredState* \[out\] on return bevat een Inge sloten instantie van de klasse **MSFT_ResourceNotInDesiredState** waarmee resources worden opgegeven die niet de gewenste status hebben.</span><span class="sxs-lookup"><span data-stu-id="669d8-110">*ResourcesNotInDesiredState* \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="669d8-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="669d8-111">Return value</span></span>

<span data-ttu-id="669d8-112">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="669d8-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="669d8-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="669d8-113">Remarks</span></span>

<span data-ttu-id="669d8-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="669d8-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="669d8-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="669d8-115">Requirements</span></span>

<span data-ttu-id="669d8-116">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="669d8-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="669d8-117">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="669d8-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="669d8-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="669d8-118">See also</span></span>

[<span data-ttu-id="669d8-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="669d8-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
