---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: PerformRequiredConfigurationChecks-methode
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942683"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="2e17e-103">PerformRequiredConfigurationChecks-methode</span><span class="sxs-lookup"><span data-stu-id="2e17e-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="2e17e-104">Start een consistentie controle met behulp van de taak planner.</span><span class="sxs-lookup"><span data-stu-id="2e17e-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e17e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2e17e-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="2e17e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="2e17e-106">Parameters</span></span>

<span data-ttu-id="2e17e-107">*Flags* \[in @ no__t-2 een bitmasker dat het type consistentie controle opgeeft dat moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="2e17e-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="2e17e-108">De volgende waarden zijn geldig en kunnen worden gecombineerd met behulp van een bitsgewijze **or** -bewerking:</span><span class="sxs-lookup"><span data-stu-id="2e17e-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="2e17e-109">Value</span><span class="sxs-lookup"><span data-stu-id="2e17e-109">Value</span></span> |<span data-ttu-id="2e17e-110">Description</span><span class="sxs-lookup"><span data-stu-id="2e17e-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="2e17e-111">**1**</span><span class="sxs-lookup"><span data-stu-id="2e17e-111">**1**</span></span> | <span data-ttu-id="2e17e-112">Een normale consistentie controle.</span><span class="sxs-lookup"><span data-stu-id="2e17e-112">A normal consistency check.</span></span> |
|<span data-ttu-id="2e17e-113">**2**</span><span class="sxs-lookup"><span data-stu-id="2e17e-113">**2**</span></span> | <span data-ttu-id="2e17e-114">Een voortzetting van een consistentie controle na het opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="2e17e-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="2e17e-115">Deze waarde mag niet worden gecombineerd met andere waarden.</span><span class="sxs-lookup"><span data-stu-id="2e17e-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="2e17e-116">**4**</span><span class="sxs-lookup"><span data-stu-id="2e17e-116">**4**</span></span> | <span data-ttu-id="2e17e-117">De configuratie moet worden opgehaald van de pull-server die is opgegeven in de-configuratie voor het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="2e17e-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="2e17e-118">Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**.</span><span class="sxs-lookup"><span data-stu-id="2e17e-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="2e17e-119">**8**</span><span class="sxs-lookup"><span data-stu-id="2e17e-119">**8**</span></span> | <span data-ttu-id="2e17e-120">Status verzenden naar de rapport server.</span><span class="sxs-lookup"><span data-stu-id="2e17e-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="2e17e-121">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="2e17e-121">Return value</span></span>

<span data-ttu-id="2e17e-122">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2e17e-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2e17e-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2e17e-123">Remarks</span></span>

<span data-ttu-id="2e17e-124">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="2e17e-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2e17e-125">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2e17e-125">Requirements</span></span>

<span data-ttu-id="2e17e-126">**MANAGE** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="2e17e-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2e17e-127">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2e17e-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2e17e-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2e17e-128">See also</span></span>

[<span data-ttu-id="2e17e-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2e17e-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
