---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078568"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b1d42-103">De ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b1d42-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b1d42-104">Rechtstreeks roept de **ophalen** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="b1d42-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1d42-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b1d42-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="b1d42-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="b1d42-106">Parameters</span></span>

<span data-ttu-id="b1d42-107">*ResourceType* \[in\] de naam van de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b1d42-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="b1d42-108">*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b1d42-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="b1d42-109">*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="b1d42-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="b1d42-110">Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.</span><span class="sxs-lookup"><span data-stu-id="b1d42-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="b1d42-111">*configuraties* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="b1d42-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="b1d42-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="b1d42-112">Return value</span></span>

<span data-ttu-id="b1d42-113">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="b1d42-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1d42-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="b1d42-114">Remarks</span></span>

<span data-ttu-id="b1d42-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="b1d42-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1d42-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b1d42-116">Requirements</span></span>

<span data-ttu-id="b1d42-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b1d42-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b1d42-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1d42-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b1d42-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b1d42-119">See also</span></span>

[<span data-ttu-id="b1d42-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="b1d42-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)