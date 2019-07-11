---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceTest-methode
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727069"
---
# <a name="resourcetest-method"></a><span data-ttu-id="9176d-103">De ResourceTest-methode</span><span class="sxs-lookup"><span data-stu-id="9176d-103">ResourceTest method</span></span>

<span data-ttu-id="9176d-104">Rechtstreeks roept de **Test** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="9176d-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="9176d-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9176d-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="9176d-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9176d-106">Parameters</span></span>

<span data-ttu-id="9176d-107">*ResourceType* \[in\] de naam van de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="9176d-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="9176d-108">*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="9176d-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="9176d-109">*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="9176d-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="9176d-110">Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.</span><span class="sxs-lookup"><span data-stu-id="9176d-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="9176d-111">*InDesiredState* \[uit\] bij resultaat, deze eigenschap is ingesteld op **waar** als het doelknooppunt in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="9176d-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="9176d-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="9176d-112">Return value</span></span>

<span data-ttu-id="9176d-113">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="9176d-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9176d-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9176d-114">Remarks</span></span>

<span data-ttu-id="9176d-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="9176d-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9176d-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9176d-116">Requirements</span></span>

<span data-ttu-id="9176d-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9176d-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9176d-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9176d-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9176d-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9176d-119">See also</span></span>

[<span data-ttu-id="9176d-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9176d-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
