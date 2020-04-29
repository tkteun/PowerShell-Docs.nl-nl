---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ResourceTest-methode
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942641"
---
# <a name="resourcetest-method"></a><span data-ttu-id="2b3b2-103">ResourceTest-methode</span><span class="sxs-lookup"><span data-stu-id="2b3b2-103">ResourceTest method</span></span>

<span data-ttu-id="2b3b2-104">Roept rechtstreeks de **test** methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="2b3b2-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b3b2-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="2b3b2-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="2b3b2-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="2b3b2-106">Parameters</span></span>

<span data-ttu-id="2b3b2-107">*ResourceType* \[Resource type\] in de naam van de resource die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="2b3b2-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="2b3b2-108">Module naam voor de module die de resource bevat die moet worden aangeroepen. *ModuleName* \[\]</span><span class="sxs-lookup"><span data-stu-id="2b3b2-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="2b3b2-109">*resource Property* \[in\] Hiermee geeft u de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="2b3b2-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="2b3b2-110">Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="2b3b2-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="2b3b2-111">*InDesiredState* \[InDesiredState\] op retour waarde deze eigenschap is ingesteld op **True** als het doel knooppunt de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="2b3b2-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="2b3b2-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="2b3b2-112">Return value</span></span>

<span data-ttu-id="2b3b2-113">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2b3b2-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b3b2-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="2b3b2-114">Remarks</span></span>

<span data-ttu-id="2b3b2-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="2b3b2-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b3b2-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2b3b2-116">Requirements</span></span>

<span data-ttu-id="2b3b2-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="2b3b2-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="2b3b2-118">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b3b2-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="2b3b2-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2b3b2-119">See also</span></span>

[<span data-ttu-id="2b3b2-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="2b3b2-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
