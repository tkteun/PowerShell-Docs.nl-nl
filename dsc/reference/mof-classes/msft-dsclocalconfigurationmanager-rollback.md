---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De rollBack-methode
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727023"
---
# <a name="rollback-method"></a><span data-ttu-id="04b0a-103">De rollBack-methode</span><span class="sxs-lookup"><span data-stu-id="04b0a-103">RollBack method</span></span>

<span data-ttu-id="04b0a-104">De configuratie teruggedraaid naar een eerdere versie.</span><span class="sxs-lookup"><span data-stu-id="04b0a-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="04b0a-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="04b0a-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="04b0a-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="04b0a-106">Parameters</span></span>

<span data-ttu-id="04b0a-107">*configurationNumber* \[in\] Hiermee geeft u de aangevraagde configuratie.</span><span class="sxs-lookup"><span data-stu-id="04b0a-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="04b0a-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="04b0a-108">Return value</span></span>

<span data-ttu-id="04b0a-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="04b0a-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="04b0a-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="04b0a-110">Remarks</span></span>

<span data-ttu-id="04b0a-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="04b0a-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="04b0a-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="04b0a-112">Requirements</span></span>

<span data-ttu-id="04b0a-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="04b0a-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="04b0a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="04b0a-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="04b0a-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="04b0a-115">See also</span></span>

[<span data-ttu-id="04b0a-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="04b0a-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
