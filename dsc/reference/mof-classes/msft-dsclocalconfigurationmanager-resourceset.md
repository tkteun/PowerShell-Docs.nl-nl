---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceSet-methode
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727099"
---
# <a name="resourceset-method"></a><span data-ttu-id="e35c3-103">De ResourceSet-methode</span><span class="sxs-lookup"><span data-stu-id="e35c3-103">ResourceSet method</span></span>

<span data-ttu-id="e35c3-104">Rechtstreeks roept de **ingesteld** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="e35c3-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="e35c3-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e35c3-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="e35c3-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e35c3-106">Parameters</span></span>

<span data-ttu-id="e35c3-107">*ResourceType* \[in\] de naam van de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="e35c3-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="e35c3-108">*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="e35c3-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="e35c3-109">*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="e35c3-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="e35c3-110">Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.</span><span class="sxs-lookup"><span data-stu-id="e35c3-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="e35c3-111">*RebootRequired* \[uit\] bij resultaat, deze eigenschap is ingesteld op **waar** als het doelknooppunt moet opnieuw worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="e35c3-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="e35c3-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e35c3-112">Return value</span></span>

<span data-ttu-id="e35c3-113">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="e35c3-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e35c3-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e35c3-114">Remarks</span></span>

<span data-ttu-id="e35c3-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e35c3-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e35c3-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e35c3-116">Requirements</span></span>

<span data-ttu-id="e35c3-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e35c3-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e35c3-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e35c3-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e35c3-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e35c3-119">See also</span></span>

[<span data-ttu-id="e35c3-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e35c3-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
