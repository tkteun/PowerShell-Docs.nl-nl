---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateLength
description: Declaratie van het kenmerk ValidateLength
ms.openlocfilehash: b35fe24c6fc44aaca6a39d819d6e3fc2d8a2cade
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646188"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="885f8-103">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="885f8-103">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="885f8-104">Het kenmerk ValidateLength geeft het minimale en maximale aantal tekens voor een argument van een cmdlet-para meter aan.</span><span class="sxs-lookup"><span data-stu-id="885f8-104">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="885f8-105">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="885f8-105">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="885f8-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="885f8-106">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="885f8-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="885f8-107">Parameters</span></span>

<span data-ttu-id="885f8-108">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="885f8-108">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="885f8-109">Hiermee geeft u het minimum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="885f8-109">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="885f8-110">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="885f8-110">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="885f8-111">Hiermee geeft u het maximum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="885f8-111">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="885f8-112">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="885f8-112">Remarks</span></span>

- <span data-ttu-id="885f8-113">Zie [Invoer validatie regels declareren](./how-to-validate-parameter-input.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="885f8-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="885f8-114">Als dit kenmerk niet wordt gebruikt, kan het bijbehorende parameter argument een wille keurige lengte hebben.</span><span class="sxs-lookup"><span data-stu-id="885f8-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="885f8-115">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="885f8-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="885f8-116">Wanneer de waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` kenmerk parameter.</span><span class="sxs-lookup"><span data-stu-id="885f8-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="885f8-117">Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="885f8-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="885f8-118">Wanneer het argument geen teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="885f8-118">When the argument is not a string.</span></span>

- <span data-ttu-id="885f8-119">Het kenmerk ValidateLength wordt gedefinieerd door de klasse [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="885f8-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="885f8-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="885f8-120">See Also</span></span>

[<span data-ttu-id="885f8-121">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="885f8-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="885f8-122">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="885f8-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
