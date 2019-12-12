---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: RemoveConfiguration-methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941556"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="abbc0-103">RemoveConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="abbc0-103">RemoveConfiguration method</span></span>

<span data-ttu-id="abbc0-104">Hiermee verwijdert u de configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="abbc0-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="abbc0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="abbc0-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="abbc0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="abbc0-106">Parameters</span></span>

<span data-ttu-id="abbc0-107">*Fase* \[in\] geeft aan welk configuratie document moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="abbc0-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="abbc0-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="abbc0-108">The following values are valid:</span></span>

|<span data-ttu-id="abbc0-109">Value</span><span class="sxs-lookup"><span data-stu-id="abbc0-109">Value</span></span> |<span data-ttu-id="abbc0-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="abbc0-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="abbc0-111">**1**</span><span class="sxs-lookup"><span data-stu-id="abbc0-111">**1**</span></span> | <span data-ttu-id="abbc0-112">Het **huidige** configuratie document (huidige. MOF).</span><span class="sxs-lookup"><span data-stu-id="abbc0-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="abbc0-113">**2**</span><span class="sxs-lookup"><span data-stu-id="abbc0-113">**2**</span></span> | <span data-ttu-id="abbc0-114">Het **in behandeling zijnde** configuratie document (in behandeling. MOF).</span><span class="sxs-lookup"><span data-stu-id="abbc0-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="abbc0-115">**4**</span><span class="sxs-lookup"><span data-stu-id="abbc0-115">**4**</span></span> | <span data-ttu-id="abbc0-116">Het **vorige** configuratie document (vorige. MOF).</span><span class="sxs-lookup"><span data-stu-id="abbc0-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="abbc0-117">*Dwing* \[in\] **waar** om het verwijderen van de configuratie af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="abbc0-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="abbc0-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="abbc0-118">Return value</span></span>

<span data-ttu-id="abbc0-119">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="abbc0-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="abbc0-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="abbc0-120">Remarks</span></span>

<span data-ttu-id="abbc0-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="abbc0-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="abbc0-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="abbc0-122">Requirements</span></span>

<span data-ttu-id="abbc0-123">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="abbc0-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="abbc0-124">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="abbc0-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="abbc0-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="abbc0-125">See also</span></span>

[<span data-ttu-id="abbc0-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="abbc0-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
