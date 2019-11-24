---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ResourceGet-methode
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942676"
---
# <a name="resourceget-method"></a><span data-ttu-id="f2e8c-103">ResourceGet-methode</span><span class="sxs-lookup"><span data-stu-id="f2e8c-103">ResourceGet method</span></span>

<span data-ttu-id="f2e8c-104">Roept rechtstreeks de **Get** -methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2e8c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f2e8c-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="f2e8c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f2e8c-106">Parameters</span></span>

<span data-ttu-id="f2e8c-107">Resource *type* -\[in\] de naam van de resource die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="f2e8c-108">*Module* \[in\] de naam van de module die de resource bevat die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="f2e8c-109">*resource property* \[in\] geeft de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="f2e8c-110">Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="f2e8c-111">*configuraties* \[out\] als resultaat, bevat een Inge sloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2e8c-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f2e8c-112">Return value</span></span>

<span data-ttu-id="f2e8c-113">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2e8c-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f2e8c-114">Remarks</span></span>

<span data-ttu-id="f2e8c-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f2e8c-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2e8c-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f2e8c-116">Requirements</span></span>

<span data-ttu-id="f2e8c-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="f2e8c-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f2e8c-118">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f2e8c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f2e8c-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f2e8c-119">See also</span></span>

[<span data-ttu-id="f2e8c-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f2e8c-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
