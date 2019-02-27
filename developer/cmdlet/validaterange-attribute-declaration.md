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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847535"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="402c8-102">Declaratie van het kenmerk ValidateRange</span><span class="sxs-lookup"><span data-stu-id="402c8-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="402c8-103">Het kenmerk ValidateRange Hiermee geeft u de minimale en maximale waarden (bereik) voor het argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="402c8-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="402c8-104">Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.</span><span class="sxs-lookup"><span data-stu-id="402c8-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="402c8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="402c8-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="402c8-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="402c8-106">Parameters</span></span>

<span data-ttu-id="402c8-107">`MinRange` ([System.Object](/dotnet/api/system.object)) vereist.</span><span class="sxs-lookup"><span data-stu-id="402c8-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="402c8-108">Hiermee geeft u de minimaal toegestane waarde.</span><span class="sxs-lookup"><span data-stu-id="402c8-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="402c8-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) vereist.</span><span class="sxs-lookup"><span data-stu-id="402c8-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="402c8-110">Hiermee geeft u de maximaal toegestane waarde.</span><span class="sxs-lookup"><span data-stu-id="402c8-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="402c8-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="402c8-111">Remarks</span></span>

- <span data-ttu-id="402c8-112">De Windows PowerShell-runtime genereert een fout bouw wanneer de waarde van de `MinRange` parameter is groter dan de waarde van de `MaxRange` parameter.</span><span class="sxs-lookup"><span data-stu-id="402c8-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="402c8-113">De Windows PowerShell-runtime genereert een fout in de volgende voorwaarden:</span><span class="sxs-lookup"><span data-stu-id="402c8-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

    - <span data-ttu-id="402c8-114">Wanneer de waarde van het argument is kleiner dan de `MinRange` beperken of groter is dan de `MaxRange` limiet.</span><span class="sxs-lookup"><span data-stu-id="402c8-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

    - <span data-ttu-id="402c8-115">Als het argument is niet van hetzelfde type als de `MinRange` en de `MaxRange` parameters.</span><span class="sxs-lookup"><span data-stu-id="402c8-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="402c8-116">Het kenmerk ValidateRange wordt gedefinieerd door de [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="402c8-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="402c8-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="402c8-117">See Also</span></span>

[<span data-ttu-id="402c8-118">System.Management.Automation.Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="402c8-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="402c8-119">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="402c8-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
