---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893073"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="776cb-103">De ResourceTest-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="776cb-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="776cb-104">Rechtstreeks roept de **Test** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="776cb-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="776cb-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="776cb-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="776cb-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="776cb-106">Parameters</span></span>

<span data-ttu-id="776cb-107">*ResourceType* \[in\] de naam van de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="776cb-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="776cb-108">*ModuleName* \[in\] de naam van de module met de resource om aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="776cb-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="776cb-109">*resourceProperty* \[in\] Hiermee geeft u de naam van de resource-eigenschap en de waarde ervan in een hash-tabel als de sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="776cb-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="776cb-110">Gebruik de [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet voor het detecteren van resource-eigenschappen en het bijhorende type.</span><span class="sxs-lookup"><span data-stu-id="776cb-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="776cb-111">*InDesiredState* \[uit\] bij resultaat, deze eigenschap is ingesteld op **waar** als het doelknooppunt in de gewenste status.</span><span class="sxs-lookup"><span data-stu-id="776cb-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="776cb-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="776cb-112">Return value</span></span>

<span data-ttu-id="776cb-113">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="776cb-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="776cb-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="776cb-114">Remarks</span></span>

<span data-ttu-id="776cb-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="776cb-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="776cb-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="776cb-116">Requirements</span></span>

<span data-ttu-id="776cb-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="776cb-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="776cb-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="776cb-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="776cb-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="776cb-119">See also</span></span>

[<span data-ttu-id="776cb-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="776cb-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)