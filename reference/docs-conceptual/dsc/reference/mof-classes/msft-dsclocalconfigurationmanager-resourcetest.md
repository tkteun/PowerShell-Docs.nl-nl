---
ms.date: 07/17/2020
keywords: DSC, Power shell, configuratie, installatie
title: ResourceTest-methode
ms.openlocfilehash: 7ef65227342091cb2a5063aaf95a2780d217f85a
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463802"
---
# <a name="resourcetest-method"></a><span data-ttu-id="3cce1-103">ResourceTest-methode</span><span class="sxs-lookup"><span data-stu-id="3cce1-103">ResourceTest method</span></span>

<span data-ttu-id="3cce1-104">Roept rechtstreeks de **test** methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="3cce1-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="3cce1-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3cce1-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="3cce1-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3cce1-106">Parameters</span></span>

<span data-ttu-id="3cce1-107">**Resource type** \[ in \] de naam van de resource die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="3cce1-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="3cce1-108">**Module naam** \[ in \] de naam van de module die de resource bevat die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="3cce1-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="3cce1-109">\***resource Property** \[ in \] geeft de naam van de bron eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="3cce1-109">\***resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="3cce1-110">Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="3cce1-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="3cce1-111">*InDesiredState* \*  InDesiredState \[ \]Deze eigenschap wordt ingesteld op **True** als het doel knooppunt de gewenste status heeft.</span><span class="sxs-lookup"><span data-stu-id="3cce1-111">*InDesiredState*\* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="3cce1-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="3cce1-112">Return value</span></span>

<span data-ttu-id="3cce1-113">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="3cce1-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3cce1-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3cce1-114">Remarks</span></span>

<span data-ttu-id="3cce1-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="3cce1-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3cce1-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3cce1-116">Requirements</span></span>

<span data-ttu-id="3cce1-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="3cce1-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3cce1-118">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3cce1-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3cce1-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3cce1-119">See also</span></span>

[<span data-ttu-id="3cce1-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="3cce1-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
