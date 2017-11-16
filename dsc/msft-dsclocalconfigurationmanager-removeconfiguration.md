---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="52aa5-103">RemoveConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="52aa5-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="52aa5-104">Hiermee verwijdert u de configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="52aa5-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="52aa5-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="52aa5-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="52aa5-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="52aa5-106">Parameters</span></span>
----------

<span data-ttu-id="52aa5-107">*Fase* \[in\]</span><span class="sxs-lookup"><span data-stu-id="52aa5-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="52aa5-108">Hiermee geeft u op welke configuratie-document te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="52aa5-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="52aa5-109">De volgende waarden zijn geldig:</span><span class="sxs-lookup"><span data-stu-id="52aa5-109">The following values are valid:</span></span>

|<span data-ttu-id="52aa5-110">Value</span><span class="sxs-lookup"><span data-stu-id="52aa5-110">Value</span></span> |<span data-ttu-id="52aa5-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="52aa5-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="52aa5-112">**1**</span><span class="sxs-lookup"><span data-stu-id="52aa5-112">**1**</span></span> | <span data-ttu-id="52aa5-113">De **huidige** configuratie document (current.mof).</span><span class="sxs-lookup"><span data-stu-id="52aa5-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="52aa5-114">**2**</span><span class="sxs-lookup"><span data-stu-id="52aa5-114">**2**</span></span> | <span data-ttu-id="52aa5-115">De **in behandeling** configuratie document (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="52aa5-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="52aa5-116">**4**</span><span class="sxs-lookup"><span data-stu-id="52aa5-116">**4**</span></span> | <span data-ttu-id="52aa5-117">De **vorige** configuratie document (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="52aa5-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="52aa5-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="52aa5-118">*Force* \[in\]</span></span>  
<span data-ttu-id="52aa5-119">**de waarde True** om af te dwingen van het verwijderen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="52aa5-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="52aa5-120">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="52aa5-120">Return value</span></span>
------------

<span data-ttu-id="52aa5-121">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="52aa5-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="52aa5-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="52aa5-122">Remarks</span></span>

<span data-ttu-id="52aa5-123">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="52aa5-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="52aa5-124">Vereisten</span><span class="sxs-lookup"><span data-stu-id="52aa5-124">Requirements</span></span>
------------
><span data-ttu-id="52aa5-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="52aa5-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="52aa5-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="52aa5-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="52aa5-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="52aa5-127">See also</span></span>


[<span data-ttu-id="52aa5-128">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="52aa5-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



