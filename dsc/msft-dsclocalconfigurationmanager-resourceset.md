---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b5f437a123bd38df21f30d11e71d2c3b36bc9f3a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f6da4-103">De ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f6da4-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f6da4-104">Rechtstreeks roept de **ingesteld** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="f6da4-104">Directly calls the **Set** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="f6da4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f6da4-105">Syntax</span></span>
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a><span data-ttu-id="f6da4-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f6da4-106">Parameters</span></span>
----------

<span data-ttu-id="f6da4-107">*ResourceType* \[in\] de naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f6da4-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="f6da4-108">*Modulenaam* \[in\] de naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f6da4-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f6da4-109">*resourceProperty* \[in\] specificeert de naam van de resource-eigenschap en de waarde in een hashtabel als sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="f6da4-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f6da4-110">Gebruik de [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="f6da4-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f6da4-111">*RebootRequired* \[uit\] op return deze eigenschap is ingesteld op **true** als het doelknooppunt moet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="f6da4-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="f6da4-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f6da4-112">Return value</span></span>
------------

<span data-ttu-id="f6da4-113">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="f6da4-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6da4-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f6da4-114">Remarks</span></span>

<span data-ttu-id="f6da4-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f6da4-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6da4-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f6da4-116">Requirements</span></span>
------------
><span data-ttu-id="f6da4-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f6da4-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f6da4-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f6da4-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f6da4-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f6da4-119">See also</span></span>


[<span data-ttu-id="f6da4-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f6da4-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)