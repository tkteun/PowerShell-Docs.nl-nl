---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7c773-103">RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7c773-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7c773-104">Hiermee verwijdert u de configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="7c773-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="7c773-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7c773-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="7c773-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7c773-106">Parameters</span></span>
----------

<span data-ttu-id="7c773-107">*Fase* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7c773-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="7c773-108">Hiermee geeft u op welke configuratie-document te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7c773-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="7c773-109">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="7c773-109">The following values are valid:</span></span>

|<span data-ttu-id="7c773-110">Value</span><span class="sxs-lookup"><span data-stu-id="7c773-110">Value</span></span> |<span data-ttu-id="7c773-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7c773-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="7c773-112">**1**</span><span class="sxs-lookup"><span data-stu-id="7c773-112">**1**</span></span> | <span data-ttu-id="7c773-113">De **huidige** configuratie document (current.mof).</span><span class="sxs-lookup"><span data-stu-id="7c773-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="7c773-114">**2**</span><span class="sxs-lookup"><span data-stu-id="7c773-114">**2**</span></span> | <span data-ttu-id="7c773-115">De **in behandeling** configuratie document (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="7c773-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="7c773-116">**4**</span><span class="sxs-lookup"><span data-stu-id="7c773-116">**4**</span></span> | <span data-ttu-id="7c773-117">De **vorige** configuratie document (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="7c773-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="7c773-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7c773-118">*Force* \[in\]</span></span>  
<span data-ttu-id="7c773-119">**de waarde True** om af te dwingen van het verwijderen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="7c773-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c773-120">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="7c773-120">Return value</span></span>
------------

<span data-ttu-id="7c773-121">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="7c773-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c773-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7c773-122">Remarks</span></span>

<span data-ttu-id="7c773-123">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="7c773-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c773-124">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7c773-124">Requirements</span></span>
------------
><span data-ttu-id="7c773-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7c773-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7c773-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7c773-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7c773-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7c773-127">See also</span></span>


[<span data-ttu-id="7c773-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7c773-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



