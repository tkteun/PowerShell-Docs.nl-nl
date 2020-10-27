---
ms.date: 07/17/2020
ms.topic: reference
title: RemoveConfiguration-methode
description: RemoveConfiguration-methode
ms.openlocfilehash: d5988ac014c457407c56a097c9a376427376eb3f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650734"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="d6204-103">RemoveConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="d6204-103">RemoveConfiguration method</span></span>

<span data-ttu-id="d6204-104">Hiermee verwijdert u de configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="d6204-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="d6204-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d6204-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="d6204-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="d6204-106">Parameters</span></span>

<span data-ttu-id="d6204-107">**Fase** \[ in \] geeft aan welk configuratie document moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d6204-107">**Stage** \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="d6204-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="d6204-108">The following values are valid:</span></span>

|<span data-ttu-id="d6204-109">Waarde</span><span class="sxs-lookup"><span data-stu-id="d6204-109">Value</span></span> |<span data-ttu-id="d6204-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d6204-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="d6204-111">**1**</span><span class="sxs-lookup"><span data-stu-id="d6204-111">**1**</span></span> | <span data-ttu-id="d6204-112">Het **huidige** configuratie document (huidige. MOF).</span><span class="sxs-lookup"><span data-stu-id="d6204-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="d6204-113">**2**</span><span class="sxs-lookup"><span data-stu-id="d6204-113">**2**</span></span> | <span data-ttu-id="d6204-114">Het **in behandeling zijnde** configuratie document (in behandeling. MOF).</span><span class="sxs-lookup"><span data-stu-id="d6204-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="d6204-115">**4**</span><span class="sxs-lookup"><span data-stu-id="d6204-115">**4**</span></span> | <span data-ttu-id="d6204-116">Het **vorige** configuratie document (vorige. MOF).</span><span class="sxs-lookup"><span data-stu-id="d6204-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="d6204-117">*Forceren* \[ in \] **True** om het verwijderen van de configuratie af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="d6204-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6204-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="d6204-118">Return value</span></span>

<span data-ttu-id="d6204-119">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d6204-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6204-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d6204-120">Remarks</span></span>

<span data-ttu-id="d6204-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="d6204-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6204-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d6204-122">Requirements</span></span>

<span data-ttu-id="d6204-123">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="d6204-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d6204-124">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d6204-124">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d6204-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d6204-125">See also</span></span>

[<span data-ttu-id="d6204-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d6204-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
