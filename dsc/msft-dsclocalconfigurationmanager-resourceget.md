---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7d8b185c49778253dcb4e983ad948775c4cb0842
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7e86f-103">ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="7e86f-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7e86f-104">Rechtstreeks roept de **ophalen** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="7e86f-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="7e86f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7e86f-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="7e86f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7e86f-106">Parameters</span></span>
----------

<span data-ttu-id="7e86f-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7e86f-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="7e86f-108">De naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="7e86f-108">The name of the resource to call.</span></span>

<span data-ttu-id="7e86f-109">*Modulenaam* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7e86f-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="7e86f-110">De naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="7e86f-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="7e86f-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="7e86f-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="7e86f-112">Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hashtabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="7e86f-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="7e86f-113">Gebruik de [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="7e86f-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="7e86f-114">*configuraties* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="7e86f-114">*configurations* \[out\]</span></span>  
<span data-ttu-id="7e86f-115">Bevat een ingesloten exemplaar van de configuraties op return.</span><span class="sxs-lookup"><span data-stu-id="7e86f-115">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e86f-116">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="7e86f-116">Return value</span></span>
------------

<span data-ttu-id="7e86f-117">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="7e86f-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e86f-118">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7e86f-118">Remarks</span></span>

<span data-ttu-id="7e86f-119">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="7e86f-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e86f-120">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7e86f-120">Requirements</span></span>
------------
><span data-ttu-id="7e86f-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7e86f-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7e86f-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7e86f-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7e86f-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7e86f-123">See also</span></span>


[<span data-ttu-id="7e86f-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="7e86f-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



