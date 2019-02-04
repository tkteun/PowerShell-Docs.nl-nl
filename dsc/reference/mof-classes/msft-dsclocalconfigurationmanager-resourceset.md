---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685464"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="cc91a-103">De ResourceSet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="cc91a-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="cc91a-104">Rechtstreeks roept de **ingesteld** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="cc91a-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="cc91a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="cc91a-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="cc91a-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="cc91a-106">Parameters</span></span>

<span data-ttu-id="cc91a-107">*ResourceType* \[in\] de naam van de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="cc91a-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="cc91a-108">*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="cc91a-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="cc91a-109">*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="cc91a-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="cc91a-110">Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.</span><span class="sxs-lookup"><span data-stu-id="cc91a-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="cc91a-111">*RebootRequired* \[uit\] bij resultaat, deze eigenschap is ingesteld op **waar** als het doelknooppunt moet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="cc91a-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="cc91a-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="cc91a-112">Return value</span></span>

<span data-ttu-id="cc91a-113">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="cc91a-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc91a-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cc91a-114">Remarks</span></span>

<span data-ttu-id="cc91a-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="cc91a-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cc91a-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cc91a-116">Requirements</span></span>

<span data-ttu-id="cc91a-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cc91a-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cc91a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cc91a-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cc91a-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cc91a-119">See also</span></span>

[<span data-ttu-id="cc91a-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="cc91a-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)