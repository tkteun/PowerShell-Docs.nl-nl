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
# <a name="removeconfiguration-method"></a><span data-ttu-id="539db-103">RemoveConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="539db-103">RemoveConfiguration method</span></span>

<span data-ttu-id="539db-104">Hiermee verwijdert u de configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="539db-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="539db-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="539db-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="539db-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="539db-106">Parameters</span></span>

<span data-ttu-id="539db-107">**Fase** \[ in \] geeft aan welk configuratie document moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="539db-107">**Stage** \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="539db-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="539db-108">The following values are valid:</span></span>

|<span data-ttu-id="539db-109">Waarde</span><span class="sxs-lookup"><span data-stu-id="539db-109">Value</span></span> |<span data-ttu-id="539db-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="539db-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="539db-111">**1**</span><span class="sxs-lookup"><span data-stu-id="539db-111">**1**</span></span> | <span data-ttu-id="539db-112">Het **huidige** configuratie document (huidige. MOF).</span><span class="sxs-lookup"><span data-stu-id="539db-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="539db-113">**2**</span><span class="sxs-lookup"><span data-stu-id="539db-113">**2**</span></span> | <span data-ttu-id="539db-114">Het **in behandeling zijnde** configuratie document (in behandeling. MOF).</span><span class="sxs-lookup"><span data-stu-id="539db-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="539db-115">**4**</span><span class="sxs-lookup"><span data-stu-id="539db-115">**4**</span></span> | <span data-ttu-id="539db-116">Het **vorige** configuratie document (vorige. MOF).</span><span class="sxs-lookup"><span data-stu-id="539db-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="539db-117">*Forceren* \[ in \] **True** om het verwijderen van de configuratie af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="539db-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="539db-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="539db-118">Return value</span></span>

<span data-ttu-id="539db-119">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="539db-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="539db-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="539db-120">Remarks</span></span>

<span data-ttu-id="539db-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="539db-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="539db-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="539db-122">Requirements</span></span>

<span data-ttu-id="539db-123">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="539db-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="539db-124">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="539db-124">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="539db-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="539db-125">See also</span></span>

[<span data-ttu-id="539db-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="539db-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
