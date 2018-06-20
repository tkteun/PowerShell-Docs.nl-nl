---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219875"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4052e-103">De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="4052e-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4052e-104">De configuratie teruggedraaid naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="4052e-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="4052e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="4052e-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="4052e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="4052e-106">Parameters</span></span>
----------

<span data-ttu-id="4052e-107">*configurationNumber* \[in\] Hiermee geeft u de aangevraagde configuratie.</span><span class="sxs-lookup"><span data-stu-id="4052e-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="4052e-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="4052e-108">Return value</span></span>
------------

<span data-ttu-id="4052e-109">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="4052e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4052e-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="4052e-110">Remarks</span></span>

<span data-ttu-id="4052e-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="4052e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4052e-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4052e-112">Requirements</span></span>
------------
><span data-ttu-id="4052e-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4052e-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4052e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4052e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4052e-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4052e-115">See also</span></span>


[<span data-ttu-id="4052e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="4052e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)