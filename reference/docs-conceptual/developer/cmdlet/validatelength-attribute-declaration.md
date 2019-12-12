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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359152"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="1b022-102">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="1b022-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="1b022-103">Het kenmerk ValidateLength geeft het minimale en maximale aantal tekens voor een argument van een cmdlet-para meter aan.</span><span class="sxs-lookup"><span data-stu-id="1b022-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="1b022-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="1b022-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b022-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1b022-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="1b022-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="1b022-106">Parameters</span></span>

<span data-ttu-id="1b022-107">`MinLength` ([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="1b022-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="1b022-108">Hiermee geeft u het minimum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1b022-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="1b022-109">`MaxLength` ([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="1b022-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="1b022-110">Hiermee geeft u het maximum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="1b022-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b022-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1b022-111">Remarks</span></span>

- <span data-ttu-id="1b022-112">Zie [Invoer validatie regels declareren](./how-to-validate-parameter-input.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="1b022-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="1b022-113">Als dit kenmerk niet wordt gebruikt, kan het bijbehorende parameter argument een wille keurige lengte hebben.</span><span class="sxs-lookup"><span data-stu-id="1b022-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="1b022-114">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="1b022-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="1b022-115">Wanneer de waarde van de para meter `MaxLength` van het kenmerk kleiner is dan de waarde van de kenmerk parameter `MinLength`.</span><span class="sxs-lookup"><span data-stu-id="1b022-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="1b022-116">Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="1b022-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="1b022-117">Wanneer het argument geen teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="1b022-117">When the argument is not a string.</span></span>

- <span data-ttu-id="1b022-118">Het kenmerk ValidateLength wordt gedefinieerd door de klasse [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="1b022-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b022-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1b022-119">See Also</span></span>

[<span data-ttu-id="1b022-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="1b022-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="1b022-121">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="1b022-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
