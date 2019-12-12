---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: ResourceSet-methode
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942648"
---
# <a name="resourceset-method"></a><span data-ttu-id="9532c-103">ResourceSet-methode</span><span class="sxs-lookup"><span data-stu-id="9532c-103">ResourceSet method</span></span>

<span data-ttu-id="9532c-104">Roept rechtstreeks de **ingestelde** methode van een DSC-resource aan.</span><span class="sxs-lookup"><span data-stu-id="9532c-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="9532c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="9532c-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="9532c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="9532c-106">Parameters</span></span>

<span data-ttu-id="9532c-107">Resource *type* -\[in\] de naam van de resource die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="9532c-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="9532c-108">*Module* \[in\] de naam van de module die de resource bevat die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="9532c-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="9532c-109">*resource property* \[in\] geeft de naam van de resource eigenschap en de waarde ervan in een hash-tabel op, respectievelijk sleutel en waarde.</span><span class="sxs-lookup"><span data-stu-id="9532c-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="9532c-110">Gebruik de cmdlet [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) om de bron eigenschappen en hun typen te detecteren.</span><span class="sxs-lookup"><span data-stu-id="9532c-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="9532c-111">*RebootRequired* \[\] als resultaat, wordt deze eigenschap ingesteld op **True** als het doel knooppunt opnieuw moet worden opgestart.</span><span class="sxs-lookup"><span data-stu-id="9532c-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="9532c-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="9532c-112">Return value</span></span>

<span data-ttu-id="9532c-113">Retourneert nul bij voltooiing; anders wordt een fout code geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="9532c-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9532c-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="9532c-114">Remarks</span></span>

<span data-ttu-id="9532c-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="9532c-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9532c-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9532c-116">Requirements</span></span>

<span data-ttu-id="9532c-117">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="9532c-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9532c-118">**Naam ruimte**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9532c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9532c-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9532c-119">See also</span></span>

[<span data-ttu-id="9532c-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="9532c-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
