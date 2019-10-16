---
title: ValidateLength kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, described
- attributes, ValidateLength
- ValidateLength attribute
ms.assetid: 82fe3a35-a94b-4bc1-ad9e-dfc5f1e788b3
caps.latest.revision: 13
ms.openlocfilehash: a25fa2410fcc6803563573596af1bc99052c3ffa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359152"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="5617c-102">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="5617c-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="5617c-103">Het kenmerk ValidateLength geeft het minimale en maximale aantal tekens voor een argument van een cmdlet-para meter aan.</span><span class="sxs-lookup"><span data-stu-id="5617c-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="5617c-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="5617c-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="5617c-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="5617c-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="5617c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="5617c-106">Parameters</span></span>

<span data-ttu-id="5617c-107">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) is vereist.</span><span class="sxs-lookup"><span data-stu-id="5617c-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="5617c-108">Hiermee geeft u het minimum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="5617c-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="5617c-109">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) is vereist.</span><span class="sxs-lookup"><span data-stu-id="5617c-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="5617c-110">Hiermee geeft u het maximum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="5617c-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="5617c-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="5617c-111">Remarks</span></span>

- <span data-ttu-id="5617c-112">Zie [Invoer validatie regels declareren](./how-to-validate-parameter-input.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="5617c-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="5617c-113">Als dit kenmerk niet wordt gebruikt, kan het bijbehorende parameter argument een wille keurige lengte hebben.</span><span class="sxs-lookup"><span data-stu-id="5617c-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="5617c-114">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="5617c-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="5617c-115">Als de waarde van de para meter `MaxLength` kleiner is dan de waarde van de para meter `MinLength`-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="5617c-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="5617c-116">Wanneer de para meter `MaxLength`-kenmerk is ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="5617c-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="5617c-117">Wanneer het argument geen teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="5617c-117">When the argument is not a string.</span></span>

- <span data-ttu-id="5617c-118">Het kenmerk ValidateLength wordt gedefinieerd door de klasse [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="5617c-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="5617c-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="5617c-119">See Also</span></span>

[<span data-ttu-id="5617c-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="5617c-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="5617c-121">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="5617c-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
