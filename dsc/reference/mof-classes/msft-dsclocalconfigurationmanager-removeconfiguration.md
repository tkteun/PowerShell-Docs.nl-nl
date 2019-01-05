---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048292"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e72fb-103">De RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="e72fb-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e72fb-104">Hiermee verwijdert u de configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="e72fb-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="e72fb-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e72fb-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="e72fb-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e72fb-106">Parameters</span></span>

<span data-ttu-id="e72fb-107">*Fase* \[in\] geeft aan welke configuratiedocument te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="e72fb-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="e72fb-108">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="e72fb-108">The following values are valid:</span></span>

|<span data-ttu-id="e72fb-109">Waarde</span><span class="sxs-lookup"><span data-stu-id="e72fb-109">Value</span></span> |<span data-ttu-id="e72fb-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e72fb-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="e72fb-111">**1**</span><span class="sxs-lookup"><span data-stu-id="e72fb-111">**1**</span></span> | <span data-ttu-id="e72fb-112">De **huidige** configuratiedocument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="e72fb-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="e72fb-113">**2**</span><span class="sxs-lookup"><span data-stu-id="e72fb-113">**2**</span></span> | <span data-ttu-id="e72fb-114">De **in behandeling** configuratiedocument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="e72fb-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="e72fb-115">**4**</span><span class="sxs-lookup"><span data-stu-id="e72fb-115">**4**</span></span> | <span data-ttu-id="e72fb-116">De **vorige** configuratiedocument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="e72fb-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="e72fb-117">*Afdwingen dat* \[in\] **waar** om af te dwingen van het verwijderen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="e72fb-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e72fb-118">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e72fb-118">Return value</span></span>

<span data-ttu-id="e72fb-119">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="e72fb-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e72fb-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e72fb-120">Remarks</span></span>

<span data-ttu-id="e72fb-121">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e72fb-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e72fb-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e72fb-122">Requirements</span></span>

<span data-ttu-id="e72fb-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e72fb-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e72fb-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e72fb-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e72fb-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e72fb-125">See also</span></span>

[<span data-ttu-id="e72fb-126">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e72fb-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)