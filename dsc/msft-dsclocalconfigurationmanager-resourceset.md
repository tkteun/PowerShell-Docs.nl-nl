---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7291641098578226449f8cbd360da0a3f9842598
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b7269-103">ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b7269-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b7269-104">Rechtstreeks roept de **ingesteld** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="b7269-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="b7269-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b7269-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="b7269-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="b7269-106">Parameters</span></span>
----------

<span data-ttu-id="b7269-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b7269-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="b7269-108">De naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b7269-108">The name of the resource to call.</span></span>

<span data-ttu-id="b7269-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b7269-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="b7269-110">De naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b7269-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b7269-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b7269-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="b7269-112">Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hashtabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="b7269-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b7269-113">Gebruik de [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="b7269-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b7269-114">*RebootRequired* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="b7269-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="b7269-115">Bij resultaat, deze eigenschap is ingesteld op **true** als het doelknooppunt moet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="b7269-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7269-116">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="b7269-116">Return value</span></span>
------------

<span data-ttu-id="b7269-117">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="b7269-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7269-118">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b7269-118">Remarks</span></span>

<span data-ttu-id="b7269-119">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="b7269-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b7269-120">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b7269-120">Requirements</span></span>
------------
><span data-ttu-id="b7269-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b7269-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b7269-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b7269-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b7269-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b7269-123">See also</span></span>


[<span data-ttu-id="b7269-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b7269-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



