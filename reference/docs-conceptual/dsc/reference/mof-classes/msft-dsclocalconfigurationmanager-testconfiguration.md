---
ms.date: 07/17/2020
ms.topic: reference
title: TestConfiguration-methode
description: TestConfiguration-methode
ms.openlocfilehash: ed26fcad2286ca753fb4b1845b8c6ad0741d491b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648916"
---
# <a name="testconfiguration-method"></a><span data-ttu-id="59ffa-103">TestConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="59ffa-103">TestConfiguration method</span></span>

<span data-ttu-id="59ffa-104">Hiermee wordt het configuratie document naar het beheerde knoop punt verzonden en wordt de huidige configuratie gecontroleerd op basis van het document.</span><span class="sxs-lookup"><span data-stu-id="59ffa-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

## <a name="syntax"></a><span data-ttu-id="59ffa-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="59ffa-105">Syntax</span></span>

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a><span data-ttu-id="59ffa-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="59ffa-106">Parameters</span></span>

<span data-ttu-id="59ffa-107">**configurationData** \[ in \] omgevings gegevens voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="59ffa-107">**configurationData** \[in\] Environment data for the configuration.</span></span>

<span data-ttu-id="59ffa-108">**InDesiredState** \[ \] Hiermee geeft u op of het beheerde knoop punt zich in de status bevindt die is opgegeven in het configuratie document.</span><span class="sxs-lookup"><span data-stu-id="59ffa-108">**InDesiredState** \[out\] On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="59ffa-109">**ResourcesInDesiredState** \[ out \] on return bevat een Inge sloten exemplaar van de klasse **MSFT_ResourceInDesiredState** die resources opgeeft die de gewenste status hebben.</span><span class="sxs-lookup"><span data-stu-id="59ffa-109">**ResourcesInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="59ffa-110">**ResourcesNotInDesiredState** \[ out \] on return bevat een Inge sloten exemplaar van de **MSFT_ResourceNotInDesiredState** -klasse waarmee resources worden opgegeven die niet de gewenste status hebben.</span><span class="sxs-lookup"><span data-stu-id="59ffa-110">**ResourcesNotInDesiredState** \[out\] On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="59ffa-111">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="59ffa-111">Return value</span></span>

<span data-ttu-id="59ffa-112">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="59ffa-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="59ffa-113">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="59ffa-113">Remarks</span></span>

<span data-ttu-id="59ffa-114">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="59ffa-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="59ffa-115">Vereisten</span><span class="sxs-lookup"><span data-stu-id="59ffa-115">Requirements</span></span>

<span data-ttu-id="59ffa-116">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="59ffa-116">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="59ffa-117">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="59ffa-117">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="59ffa-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="59ffa-118">See also</span></span>

[<span data-ttu-id="59ffa-119">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="59ffa-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
