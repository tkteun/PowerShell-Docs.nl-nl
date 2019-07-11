---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De PerformRequiredConfigurationChecks-methode
ms.openlocfilehash: 909e3a48d08e0220ab0efc6a03bea7ead5d9843e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734403"
---
# <a name="performrequiredconfigurationchecks-method"></a><span data-ttu-id="5b75e-103">De PerformRequiredConfigurationChecks-methode</span><span class="sxs-lookup"><span data-stu-id="5b75e-103">PerformRequiredConfigurationChecks method</span></span>

<span data-ttu-id="5b75e-104">Een consistentiecontrole starten met behulp van de Taakplanner.</span><span class="sxs-lookup"><span data-stu-id="5b75e-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b75e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5b75e-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="5b75e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="5b75e-106">Parameters</span></span>

<span data-ttu-id="5b75e-107">*Vlaggen* \[in\] een bitmasker waarmee het type van een consistentiecontrole uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="5b75e-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="5b75e-108">De volgende waarden geldig zijn en kunnen worden gecombineerd met behulp van een bitwise **of** bewerking:</span><span class="sxs-lookup"><span data-stu-id="5b75e-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="5b75e-109">Waarde</span><span class="sxs-lookup"><span data-stu-id="5b75e-109">Value</span></span> |<span data-ttu-id="5b75e-110">Description</span><span class="sxs-lookup"><span data-stu-id="5b75e-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="5b75e-111">**1**</span><span class="sxs-lookup"><span data-stu-id="5b75e-111">**1**</span></span> | <span data-ttu-id="5b75e-112">Een normale consistentiecontrole uit.</span><span class="sxs-lookup"><span data-stu-id="5b75e-112">A normal consistency check.</span></span> |
|<span data-ttu-id="5b75e-113">**2**</span><span class="sxs-lookup"><span data-stu-id="5b75e-113">**2**</span></span> | <span data-ttu-id="5b75e-114">Een voortzetting van een consistentiecontrole uit na het opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="5b75e-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="5b75e-115">Deze waarde moet niet worden gecombineerd met andere waarden.</span><span class="sxs-lookup"><span data-stu-id="5b75e-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="5b75e-116">**4**</span><span class="sxs-lookup"><span data-stu-id="5b75e-116">**4**</span></span> | <span data-ttu-id="5b75e-117">De configuratie moet worden opgehaald uit de pull-server die is opgegeven in de metaconfiguration voor het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5b75e-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="5b75e-118">Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**.</span><span class="sxs-lookup"><span data-stu-id="5b75e-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="5b75e-119">**8**</span><span class="sxs-lookup"><span data-stu-id="5b75e-119">**8**</span></span> | <span data-ttu-id="5b75e-120">De status verzenden naar de rapportserver.</span><span class="sxs-lookup"><span data-stu-id="5b75e-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="5b75e-121">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="5b75e-121">Return value</span></span>

<span data-ttu-id="5b75e-122">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="5b75e-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b75e-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5b75e-123">Remarks</span></span>

<span data-ttu-id="5b75e-124">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="5b75e-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5b75e-125">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5b75e-125">Requirements</span></span>

<span data-ttu-id="5b75e-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5b75e-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5b75e-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b75e-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5b75e-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5b75e-128">See also</span></span>

[<span data-ttu-id="5b75e-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5b75e-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
