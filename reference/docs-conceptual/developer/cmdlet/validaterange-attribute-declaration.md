---
title: ValidateRange kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359133"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="3b979-102">Declaratie van het kenmerk ValidateRange</span><span class="sxs-lookup"><span data-stu-id="3b979-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="3b979-103">Met het kenmerk ValidateRange worden de minimum-en maximum waarden (het bereik) opgegeven voor het argument van de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="3b979-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="3b979-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="3b979-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b979-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3b979-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="3b979-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3b979-106">Parameters</span></span>

<span data-ttu-id="3b979-107">`MinRange` ([System. object](/dotnet/api/system.object)) is vereist.</span><span class="sxs-lookup"><span data-stu-id="3b979-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="3b979-108">Hiermee geeft u de toegestane minimum waarde.</span><span class="sxs-lookup"><span data-stu-id="3b979-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="3b979-109">`MaxRange` ([System. object](/dotnet/api/system.object)) is vereist.</span><span class="sxs-lookup"><span data-stu-id="3b979-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="3b979-110">Hiermee geeft u de toegestane maximum waarde.</span><span class="sxs-lookup"><span data-stu-id="3b979-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3b979-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3b979-111">Remarks</span></span>

- <span data-ttu-id="3b979-112">De Windows Power shell-runtime genereert een constructie fout wanneer de waarde van de para meter `MinRange` groter is dan de waarde van de para meter `MaxRange`.</span><span class="sxs-lookup"><span data-stu-id="3b979-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="3b979-113">De Windows Power shell-runtime genereert een validatie fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="3b979-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="3b979-114">Wanneer de waarde van het argument kleiner is dan de limiet van @no__t 0 of groter is dan de limiet van `MaxRange`.</span><span class="sxs-lookup"><span data-stu-id="3b979-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="3b979-115">Wanneer het argument niet van hetzelfde type is als de `MinRange` en de para meters `MaxRange`.</span><span class="sxs-lookup"><span data-stu-id="3b979-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="3b979-116">Het kenmerk ValidateRange wordt gedefinieerd door de klasse [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3b979-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b979-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3b979-117">See Also</span></span>

[<span data-ttu-id="3b979-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="3b979-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="3b979-119">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="3b979-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
