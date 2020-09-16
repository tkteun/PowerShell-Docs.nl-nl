---
title: ValidateLength kenmerk declaratie | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.openlocfilehash: 7145dde55e79eeea6e3ceb91dfc1c93043a8857c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786302"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="7141d-102">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="7141d-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="7141d-103">Het kenmerk ValidateLength geeft het minimale en maximale aantal tekens voor een argument van een cmdlet-para meter aan.</span><span class="sxs-lookup"><span data-stu-id="7141d-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="7141d-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="7141d-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="7141d-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7141d-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="7141d-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7141d-106">Parameters</span></span>

<span data-ttu-id="7141d-107">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="7141d-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="7141d-108">Hiermee geeft u het minimum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7141d-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="7141d-109">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="7141d-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="7141d-110">Hiermee geeft u het maximum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="7141d-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="7141d-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7141d-111">Remarks</span></span>

- <span data-ttu-id="7141d-112">Zie [Invoer validatie regels declareren](./how-to-validate-parameter-input.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="7141d-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="7141d-113">Als dit kenmerk niet wordt gebruikt, kan het bijbehorende parameter argument een wille keurige lengte hebben.</span><span class="sxs-lookup"><span data-stu-id="7141d-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="7141d-114">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="7141d-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="7141d-115">Wanneer de waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` kenmerk parameter.</span><span class="sxs-lookup"><span data-stu-id="7141d-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="7141d-116">Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="7141d-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="7141d-117">Wanneer het argument geen teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="7141d-117">When the argument is not a string.</span></span>

- <span data-ttu-id="7141d-118">Het kenmerk ValidateLength wordt gedefinieerd door de klasse [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="7141d-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7141d-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7141d-119">See Also</span></span>

[<span data-ttu-id="7141d-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="7141d-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="7141d-121">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="7141d-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
