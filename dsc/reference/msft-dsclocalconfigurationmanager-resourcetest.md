---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403896"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="316fd-103">De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="316fd-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="316fd-104">Rechtstreeks roept de **Test** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="316fd-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="316fd-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="316fd-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="316fd-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="316fd-106">Parameters</span></span>

<span data-ttu-id="316fd-107">*ResourceType* \[in\] de naam van de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="316fd-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="316fd-108">*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="316fd-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="316fd-109">*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="316fd-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="316fd-110">Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.</span><span class="sxs-lookup"><span data-stu-id="316fd-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="316fd-111">*InDesiredState* \[uit\] bij resultaat, deze eigenschap is ingesteld op **waar** als het doelknooppunt in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="316fd-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="316fd-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="316fd-112">Return value</span></span>

<span data-ttu-id="316fd-113">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="316fd-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="316fd-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="316fd-114">Remarks</span></span>

<span data-ttu-id="316fd-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="316fd-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="316fd-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="316fd-116">Requirements</span></span>

<span data-ttu-id="316fd-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="316fd-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="316fd-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="316fd-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="316fd-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="316fd-119">See also</span></span>

[<span data-ttu-id="316fd-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="316fd-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)