---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: PerformRequiredConfigurationChecks-methode
ms.openlocfilehash: ea4294ffdcb2580fa7b39b18966b642d58073eb6
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464448"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="1c98c-103">PerformRequiredConfigurationChecks-methode</span><span class="sxs-lookup"><span data-stu-id="1c98c-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="1c98c-104">Start een consistentie controle met behulp van de taak planner.</span><span class="sxs-lookup"><span data-stu-id="1c98c-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c98c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1c98c-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="1c98c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="1c98c-106">Parameters</span></span>

<span data-ttu-id="1c98c-107">**Vlaggen** \[ in \] een bitmasker waarmee wordt aangegeven welk type consistentie controle moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1c98c-107">**Flags** \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="1c98c-108">De volgende waarden zijn geldig en kunnen worden gecombineerd met behulp van een bitsgewijze **or** -bewerking:</span><span class="sxs-lookup"><span data-stu-id="1c98c-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="1c98c-109">Waarde</span><span class="sxs-lookup"><span data-stu-id="1c98c-109">Value</span></span> |<span data-ttu-id="1c98c-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1c98c-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="1c98c-111">**1**</span><span class="sxs-lookup"><span data-stu-id="1c98c-111">**1**</span></span> | <span data-ttu-id="1c98c-112">Een normale consistentie controle.</span><span class="sxs-lookup"><span data-stu-id="1c98c-112">A normal consistency check.</span></span> |
|<span data-ttu-id="1c98c-113">**2**</span><span class="sxs-lookup"><span data-stu-id="1c98c-113">**2**</span></span> | <span data-ttu-id="1c98c-114">Een voortzetting van een consistentie controle na het opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="1c98c-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="1c98c-115">Deze waarde mag niet worden gecombineerd met andere waarden.</span><span class="sxs-lookup"><span data-stu-id="1c98c-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="1c98c-116">**4**</span><span class="sxs-lookup"><span data-stu-id="1c98c-116">**4**</span></span> | <span data-ttu-id="1c98c-117">De configuratie moet worden opgehaald van de pull-server die is opgegeven in de-configuratie voor het knoop punt.</span><span class="sxs-lookup"><span data-stu-id="1c98c-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="1c98c-118">Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**.</span><span class="sxs-lookup"><span data-stu-id="1c98c-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="1c98c-119">**8**</span><span class="sxs-lookup"><span data-stu-id="1c98c-119">**8**</span></span> | <span data-ttu-id="1c98c-120">Status verzenden naar de rapport server.</span><span class="sxs-lookup"><span data-stu-id="1c98c-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="1c98c-121">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="1c98c-121">Return value</span></span>

<span data-ttu-id="1c98c-122">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="1c98c-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c98c-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1c98c-123">Remarks</span></span>

<span data-ttu-id="1c98c-124">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="1c98c-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c98c-125">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1c98c-125">Requirements</span></span>

<span data-ttu-id="1c98c-126">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="1c98c-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="1c98c-127">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1c98c-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="1c98c-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1c98c-128">See also</span></span>

[<span data-ttu-id="1c98c-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="1c98c-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
