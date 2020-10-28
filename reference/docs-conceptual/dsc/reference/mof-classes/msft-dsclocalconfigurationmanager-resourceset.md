---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceSet-methode
description: ResourceSet-methode
ms.openlocfilehash: 2554ff5805d7ed9518bd283565dc879a0fdfdfd0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650696"
---
# <a name="resourceset-method"></a><span data-ttu-id="0f07f-103">ResourceSet-methode</span><span class="sxs-lookup"><span data-stu-id="0f07f-103">ResourceSet method</span></span>

<span data-ttu-id="0f07f-104">Roept rechtstreeks de **ingestelde** methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="0f07f-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f07f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0f07f-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="0f07f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="0f07f-106">Parameters</span></span>

<span data-ttu-id="0f07f-107">**Resource type** \[ in \] de naam van de resource die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="0f07f-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="0f07f-108">**Module naam** \[ in \] de naam van de module die de resource bevat die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="0f07f-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="0f07f-109">**resource Property** \[ in \] geeft de naam van de bron eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="0f07f-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="0f07f-110">Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="0f07f-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="0f07f-111">**RebootRequired** \[ \] Deze eigenschap wordt ingesteld op **True** als het doel knooppunt opnieuw moet worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="0f07f-111">**RebootRequired** \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="0f07f-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="0f07f-112">Return value</span></span>

<span data-ttu-id="0f07f-113">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0f07f-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="0f07f-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0f07f-114">Remarks</span></span>

<span data-ttu-id="0f07f-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="0f07f-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f07f-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0f07f-116">Requirements</span></span>

<span data-ttu-id="0f07f-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="0f07f-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="0f07f-118">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="0f07f-118">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="0f07f-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0f07f-119">See also</span></span>

[<span data-ttu-id="0f07f-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="0f07f-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
