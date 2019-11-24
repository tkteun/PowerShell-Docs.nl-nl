---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: RemoveConfiguration-methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941556"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="c4c12-103">RemoveConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="c4c12-103">RemoveConfiguration method</span></span>

<span data-ttu-id="c4c12-104">Hiermee verwijdert u de configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="c4c12-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4c12-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c4c12-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="c4c12-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="c4c12-106">Parameters</span></span>

<span data-ttu-id="c4c12-107">*Fase* \[in\] geeft aan welk configuratie document moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="c4c12-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="c4c12-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="c4c12-108">The following values are valid:</span></span>

|<span data-ttu-id="c4c12-109">Waarde</span><span class="sxs-lookup"><span data-stu-id="c4c12-109">Value</span></span> |<span data-ttu-id="c4c12-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c4c12-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="c4c12-111">**1**</span><span class="sxs-lookup"><span data-stu-id="c4c12-111">**1**</span></span> | <span data-ttu-id="c4c12-112">Het **huidige** configuratie document (huidige. MOF).</span><span class="sxs-lookup"><span data-stu-id="c4c12-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="c4c12-113">**2**</span><span class="sxs-lookup"><span data-stu-id="c4c12-113">**2**</span></span> | <span data-ttu-id="c4c12-114">Het **in behandeling zijnde** configuratie document (in behandeling. MOF).</span><span class="sxs-lookup"><span data-stu-id="c4c12-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="c4c12-115">**4**</span><span class="sxs-lookup"><span data-stu-id="c4c12-115">**4**</span></span> | <span data-ttu-id="c4c12-116">Het **vorige** configuratie document (vorige. MOF).</span><span class="sxs-lookup"><span data-stu-id="c4c12-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="c4c12-117">*Dwing* \[in\] **waar** om het verwijderen van de configuratie af te dwingen.</span><span class="sxs-lookup"><span data-stu-id="c4c12-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c4c12-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="c4c12-118">Return value</span></span>

<span data-ttu-id="c4c12-119">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="c4c12-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4c12-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c4c12-120">Remarks</span></span>

<span data-ttu-id="c4c12-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="c4c12-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4c12-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c4c12-122">Requirements</span></span>

<span data-ttu-id="c4c12-123">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="c4c12-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c4c12-124">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4c12-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c4c12-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c4c12-125">See also</span></span>

[<span data-ttu-id="c4c12-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="c4c12-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
