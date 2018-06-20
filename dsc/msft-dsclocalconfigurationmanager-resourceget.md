---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 30cbaa907d4dc3a921c9e5fe61ffddc5d61c2347
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187864"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5dcd7-103">De ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5dcd7-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5dcd7-104">Rechtstreeks roept de **ophalen** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="5dcd7-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5dcd7-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="5dcd7-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="5dcd7-106">Parameters</span></span>
----------

<span data-ttu-id="5dcd7-107">*ResourceType* \[in\] de naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="5dcd7-108">*Modulenaam* \[in\] de naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="5dcd7-109">*resourceProperty* \[in\] specificeert de naam van de resource-eigenschap en de waarde in een hashtabel als sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="5dcd7-110">Gebruik de [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="5dcd7-111">*configuraties* \[uit\] op return bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="5dcd7-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="5dcd7-112">Return value</span></span>
------------

<span data-ttu-id="5dcd7-113">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5dcd7-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5dcd7-114">Remarks</span></span>

<span data-ttu-id="5dcd7-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="5dcd7-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5dcd7-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5dcd7-116">Requirements</span></span>
------------
><span data-ttu-id="5dcd7-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5dcd7-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5dcd7-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5dcd7-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5dcd7-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5dcd7-119">See also</span></span>


[<span data-ttu-id="5dcd7-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="5dcd7-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)