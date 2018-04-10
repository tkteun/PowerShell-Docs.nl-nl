---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f03a034329a9cde5cd44dbaf42ba1789c2b8f4f9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6542f-103">De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="6542f-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6542f-104">Rechtstreeks roept de **Test** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="6542f-104">Directly calls the **Test** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="6542f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="6542f-105">Syntax</span></span>
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a name="parameters"></a><span data-ttu-id="6542f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="6542f-106">Parameters</span></span>
----------

<span data-ttu-id="6542f-107">*ResourceType* \[in\] de naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="6542f-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="6542f-108">*Modulenaam* \[in\] de naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="6542f-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="6542f-109">*resourceProperty* \[in\] specificeert de naam van de resource-eigenschap en de waarde in een hashtabel als sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="6542f-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="6542f-110">Gebruik de [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="6542f-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="6542f-111">*InDesiredState* \[uit\] op return deze eigenschap is ingesteld op **true** als het doelknooppunt in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="6542f-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="6542f-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="6542f-112">Return value</span></span>
------------

<span data-ttu-id="6542f-113">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="6542f-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6542f-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="6542f-114">Remarks</span></span>

<span data-ttu-id="6542f-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="6542f-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6542f-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6542f-116">Requirements</span></span>
------------
><span data-ttu-id="6542f-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6542f-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6542f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6542f-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6542f-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="6542f-119">See also</span></span>


[<span data-ttu-id="6542f-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="6542f-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)