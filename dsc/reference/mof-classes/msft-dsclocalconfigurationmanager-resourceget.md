---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceGet-methode
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727107"
---
# <a name="resourceget-method"></a><span data-ttu-id="9880a-103">De ResourceGet-methode</span><span class="sxs-lookup"><span data-stu-id="9880a-103">ResourceGet method</span></span>

<span data-ttu-id="9880a-104">Rechtstreeks roept de **ophalen** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="9880a-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="9880a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9880a-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="9880a-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9880a-106">Parameters</span></span>

<span data-ttu-id="9880a-107">*ResourceType* \[in\] de naam van de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="9880a-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="9880a-108">*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="9880a-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="9880a-109">*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="9880a-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="9880a-110">Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.</span><span class="sxs-lookup"><span data-stu-id="9880a-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="9880a-111">*configuraties* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="9880a-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="9880a-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="9880a-112">Return value</span></span>

<span data-ttu-id="9880a-113">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="9880a-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9880a-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9880a-114">Remarks</span></span>

<span data-ttu-id="9880a-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="9880a-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9880a-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9880a-116">Requirements</span></span>

<span data-ttu-id="9880a-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9880a-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9880a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9880a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9880a-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9880a-119">See also</span></span>

[<span data-ttu-id="9880a-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9880a-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
