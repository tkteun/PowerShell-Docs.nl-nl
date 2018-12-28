---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403962"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8c2cf-103">De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8c2cf-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8c2cf-104">Hiermee verwijdert u de configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="8c2cf-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c2cf-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8c2cf-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="8c2cf-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="8c2cf-106">Parameters</span></span>

<span data-ttu-id="8c2cf-107">*Fase* \[in\] geeft aan welke configuratiedocument te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="8c2cf-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="8c2cf-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="8c2cf-108">The following values are valid:</span></span>

|<span data-ttu-id="8c2cf-109">Value</span><span class="sxs-lookup"><span data-stu-id="8c2cf-109">Value</span></span> |<span data-ttu-id="8c2cf-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8c2cf-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="8c2cf-111">**1**</span><span class="sxs-lookup"><span data-stu-id="8c2cf-111">**1**</span></span> | <span data-ttu-id="8c2cf-112">De **huidige** configuratiedocument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="8c2cf-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="8c2cf-113">**2**</span><span class="sxs-lookup"><span data-stu-id="8c2cf-113">**2**</span></span> | <span data-ttu-id="8c2cf-114">De **in behandeling** configuratiedocument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="8c2cf-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="8c2cf-115">**4**</span><span class="sxs-lookup"><span data-stu-id="8c2cf-115">**4**</span></span> | <span data-ttu-id="8c2cf-116">De **vorige** configuratiedocument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="8c2cf-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="8c2cf-117">*Afdwingen dat* \[in\] **waar** om af te dwingen van het verwijderen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="8c2cf-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="8c2cf-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="8c2cf-118">Return value</span></span>

<span data-ttu-id="8c2cf-119">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="8c2cf-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c2cf-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8c2cf-120">Remarks</span></span>

<span data-ttu-id="8c2cf-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="8c2cf-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c2cf-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8c2cf-122">Requirements</span></span>

<span data-ttu-id="8c2cf-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8c2cf-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8c2cf-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8c2cf-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8c2cf-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8c2cf-125">See also</span></span>

[<span data-ttu-id="8c2cf-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8c2cf-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)