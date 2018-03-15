---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3486ef559102929f8d05994a4bf6e45d49a0c140
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="da7ea-103">ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="da7ea-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="da7ea-104">Rechtstreeks roept de **ingesteld** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="da7ea-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="da7ea-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="da7ea-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="da7ea-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="da7ea-106">Parameters</span></span>
----------

<span data-ttu-id="da7ea-107">*ResourceType* \[in\]</span><span class="sxs-lookup"><span data-stu-id="da7ea-107">*ResourceType* \[in\]</span></span>  
<span data-ttu-id="da7ea-108">De naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="da7ea-108">The name of the resource to call.</span></span>

<span data-ttu-id="da7ea-109">*ModuleName* \[in\]</span><span class="sxs-lookup"><span data-stu-id="da7ea-109">*ModuleName* \[in\]</span></span>  
<span data-ttu-id="da7ea-110">De naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="da7ea-110">The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="da7ea-111">*resourceProperty* \[in\]</span><span class="sxs-lookup"><span data-stu-id="da7ea-111">*resourceProperty* \[in\]</span></span>  
<span data-ttu-id="da7ea-112">Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hashtabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="da7ea-112">Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="da7ea-113">Gebruik de [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="da7ea-113">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="da7ea-114">*RebootRequired* \[uit\]</span><span class="sxs-lookup"><span data-stu-id="da7ea-114">*RebootRequired* \[out\]</span></span>  
<span data-ttu-id="da7ea-115">Bij resultaat, deze eigenschap is ingesteld op **true** als het doelknooppunt moet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="da7ea-115">On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="da7ea-116">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="da7ea-116">Return value</span></span>
------------

<span data-ttu-id="da7ea-117">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="da7ea-117">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="da7ea-118">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="da7ea-118">Remarks</span></span>

<span data-ttu-id="da7ea-119">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="da7ea-119">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="da7ea-120">Vereisten</span><span class="sxs-lookup"><span data-stu-id="da7ea-120">Requirements</span></span>
------------
><span data-ttu-id="da7ea-121">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="da7ea-121">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="da7ea-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="da7ea-122">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="da7ea-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="da7ea-123">See also</span></span>


[<span data-ttu-id="da7ea-124">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="da7ea-124">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



