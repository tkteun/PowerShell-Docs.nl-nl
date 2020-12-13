---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateRange
description: Declaratie van het kenmerk ValidateRange
ms.openlocfilehash: 1fec9d1bd36cd21b7f0f23bf6d72338d276dce91
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660608"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="a0a0d-103">Declaratie van het kenmerk ValidateRange</span><span class="sxs-lookup"><span data-stu-id="a0a0d-103">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="a0a0d-104">Met het kenmerk ValidateRange worden de minimum-en maximum waarden (het bereik) opgegeven voor het argument van de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-104">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="a0a0d-105">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="a0a0d-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a0a0d-106">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="a0a0d-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="a0a0d-107">Parameters</span></span>

<span data-ttu-id="a0a0d-108">`MinRange` ([System. object](/dotnet/api/system.object)) vereist.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-108">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="a0a0d-109">Hiermee geeft u de toegestane minimum waarde.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-109">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="a0a0d-110">`MaxRange` ([System. object](/dotnet/api/system.object)) vereist.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-110">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="a0a0d-111">Hiermee geeft u de toegestane maximum waarde.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-111">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0a0d-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a0a0d-112">Remarks</span></span>

- <span data-ttu-id="a0a0d-113">De Windows Power shell-runtime genereert een constructie fout wanneer de waarde van de `MinRange` para meter groter is dan de waarde van de `MaxRange` para meter.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-113">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="a0a0d-114">De Windows Power shell-runtime genereert een validatie fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="a0a0d-114">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="a0a0d-115">Wanneer de waarde van het argument kleiner is dan de `MinRange` limiet of groter is dan de `MaxRange` limiet.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-115">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="a0a0d-116">Wanneer het argument niet van hetzelfde type is als de `MinRange` `MaxRange` para meters en.</span><span class="sxs-lookup"><span data-stu-id="a0a0d-116">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="a0a0d-117">Het kenmerk ValidateRange wordt gedefinieerd door de klasse [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="a0a0d-117">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0a0d-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a0a0d-118">See Also</span></span>

[<span data-ttu-id="a0a0d-119">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="a0a0d-119">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="a0a0d-120">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="a0a0d-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
