---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De RemoveConfiguration-methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734384"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="497f8-103">De RemoveConfiguration-methode</span><span class="sxs-lookup"><span data-stu-id="497f8-103">RemoveConfiguration method</span></span>

<span data-ttu-id="497f8-104">Hiermee verwijdert u de configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="497f8-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="497f8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="497f8-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="497f8-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="497f8-106">Parameters</span></span>

<span data-ttu-id="497f8-107">*Fase* \[in\] geeft aan welke configuratiedocument te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="497f8-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="497f8-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="497f8-108">The following values are valid:</span></span>

|<span data-ttu-id="497f8-109">Waarde</span><span class="sxs-lookup"><span data-stu-id="497f8-109">Value</span></span> |<span data-ttu-id="497f8-110">Description</span><span class="sxs-lookup"><span data-stu-id="497f8-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="497f8-111">**1**</span><span class="sxs-lookup"><span data-stu-id="497f8-111">**1**</span></span> | <span data-ttu-id="497f8-112">De **huidige** configuratiedocument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="497f8-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="497f8-113">**2**</span><span class="sxs-lookup"><span data-stu-id="497f8-113">**2**</span></span> | <span data-ttu-id="497f8-114">De **in behandeling** configuratiedocument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="497f8-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="497f8-115">**4**</span><span class="sxs-lookup"><span data-stu-id="497f8-115">**4**</span></span> | <span data-ttu-id="497f8-116">De **vorige** configuratiedocument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="497f8-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="497f8-117">*Afdwingen dat* \[in\] **waar** om af te dwingen van het verwijderen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="497f8-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="497f8-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="497f8-118">Return value</span></span>

<span data-ttu-id="497f8-119">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="497f8-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="497f8-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="497f8-120">Remarks</span></span>

<span data-ttu-id="497f8-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="497f8-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="497f8-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="497f8-122">Requirements</span></span>

<span data-ttu-id="497f8-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="497f8-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="497f8-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="497f8-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="497f8-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="497f8-125">See also</span></span>

[<span data-ttu-id="497f8-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="497f8-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
