---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceGet-methode
description: ResourceGet-methode
ms.openlocfilehash: bff737f04e02740fa09fd82d7b27c75b11303dad
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650765"
---
# <a name="resourceget-method"></a><span data-ttu-id="e7ac0-103">ResourceGet-methode</span><span class="sxs-lookup"><span data-stu-id="e7ac0-103">ResourceGet method</span></span>

<span data-ttu-id="e7ac0-104">Roept rechtstreeks de **Get** -methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7ac0-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e7ac0-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="e7ac0-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e7ac0-106">Parameters</span></span>

<span data-ttu-id="e7ac0-107">**Resource type** \[ in \] de naam van de resource die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-107">**ResourceType** \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="e7ac0-108">**Module naam** \[ in \] de naam van de module die de resource bevat die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-108">**ModuleName** \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="e7ac0-109">**resource Property** \[ in \] geeft de naam van de bron eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-109">**resourceProperty** \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="e7ac0-110">Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="e7ac0-111">**configuraties** \[ out \] on return bevat een Inge sloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-111">**configurations** \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="e7ac0-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="e7ac0-112">Return value</span></span>

<span data-ttu-id="e7ac0-113">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7ac0-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e7ac0-114">Remarks</span></span>

<span data-ttu-id="e7ac0-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7ac0-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e7ac0-116">Requirements</span></span>

<span data-ttu-id="e7ac0-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="e7ac0-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e7ac0-118">**Naam ruimte** : Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7ac0-118">**Namespace** : Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e7ac0-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e7ac0-119">See also</span></span>

[<span data-ttu-id="e7ac0-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="e7ac0-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
