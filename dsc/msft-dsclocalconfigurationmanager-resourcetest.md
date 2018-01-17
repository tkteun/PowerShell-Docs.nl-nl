---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3c88f74c5f623502e8cbe0d7aa7390fca75569a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/17/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="83ef8-103">ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="83ef8-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="83ef8-104">Rechtstreeks roept de **Test** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="83ef8-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="83ef8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="83ef8-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="83ef8-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="83ef8-106">Parameters</span></span>
----------

<span data-ttu-id="83ef8-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="83ef8-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="83ef8-108">De naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="83ef8-108">The name of the resource to call.</span></span>

<span data-ttu-id="83ef8-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="83ef8-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="83ef8-110">De naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="83ef8-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="83ef8-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="83ef8-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="83ef8-112">Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hashtabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="83ef8-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="83ef8-113">Gebruik de [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="83ef8-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="83ef8-114">*InDesiredState* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="83ef8-114">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="83ef8-115">Bij resultaat, deze eigenschap is ingesteld op **true** als het doelknooppunt in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="83ef8-115">On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="83ef8-116">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="83ef8-116">Return value</span></span>
------------

<span data-ttu-id="83ef8-117">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="83ef8-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="83ef8-118">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="83ef8-118">Remarks</span></span>

<span data-ttu-id="83ef8-119">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="83ef8-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="83ef8-120">Vereisten</span><span class="sxs-lookup"><span data-stu-id="83ef8-120">Requirements</span></span>
------------
><span data-ttu-id="83ef8-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="83ef8-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="83ef8-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="83ef8-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="83ef8-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83ef8-123">See also</span></span>


[<span data-ttu-id="83ef8-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="83ef8-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



