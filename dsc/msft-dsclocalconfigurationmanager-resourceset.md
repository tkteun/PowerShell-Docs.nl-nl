---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cd9c1b3f58a5862db6c4eea0488423b8dfe7310
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2b58e-103">ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2b58e-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2b58e-104">Rechtstreeks roept de **ingesteld** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="2b58e-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="2b58e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2b58e-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="2b58e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="2b58e-106">Parameters</span></span>
----------

<span data-ttu-id="2b58e-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2b58e-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="2b58e-108">De naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="2b58e-108">The name of the resource to call.</span></span>

<span data-ttu-id="2b58e-109">*Modulenaam* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2b58e-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="2b58e-110">De naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="2b58e-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="2b58e-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2b58e-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="2b58e-112">Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hashtabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="2b58e-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="2b58e-113">Gebruik de [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="2b58e-113">Use the [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="2b58e-114">*RebootRequired* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="2b58e-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="2b58e-115">Bij resultaat, deze eigenschap is ingesteld op **true** als het doelknooppunt moet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="2b58e-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b58e-116">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="2b58e-116">Return value</span></span>
------------

<span data-ttu-id="2b58e-117">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="2b58e-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b58e-118">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2b58e-118">Remarks</span></span>

<span data-ttu-id="2b58e-119">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="2b58e-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b58e-120">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2b58e-120">Requirements</span></span>
------------
><span data-ttu-id="2b58e-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2b58e-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2b58e-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b58e-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2b58e-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2b58e-123">See also</span></span>


[<span data-ttu-id="2b58e-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2b58e-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



