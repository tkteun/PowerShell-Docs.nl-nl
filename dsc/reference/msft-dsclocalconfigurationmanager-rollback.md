---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404019"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f8d4e-103">De RollBack-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="f8d4e-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f8d4e-104">De configuratie teruggedraaid naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="f8d4e-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8d4e-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f8d4e-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="f8d4e-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="f8d4e-106">Parameters</span></span>

<span data-ttu-id="f8d4e-107">*configurationNumber* \[in\] Hiermee geeft u de aangevraagde configuratie.</span><span class="sxs-lookup"><span data-stu-id="f8d4e-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f8d4e-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="f8d4e-108">Return value</span></span>

<span data-ttu-id="f8d4e-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="f8d4e-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8d4e-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f8d4e-110">Remarks</span></span>

<span data-ttu-id="f8d4e-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="f8d4e-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8d4e-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f8d4e-112">Requirements</span></span>

<span data-ttu-id="f8d4e-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f8d4e-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f8d4e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f8d4e-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f8d4e-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f8d4e-115">See also</span></span>

[<span data-ttu-id="f8d4e-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="f8d4e-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)