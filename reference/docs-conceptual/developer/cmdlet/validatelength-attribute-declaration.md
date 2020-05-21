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
ms.openlocfilehash: a1a494534169b2da470286020dfacfa8e9084839
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692320"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="3bc19-102">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="3bc19-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="3bc19-103">Het kenmerk ValidateLength geeft het minimale en maximale aantal tekens voor een argument van een cmdlet-para meter aan.</span><span class="sxs-lookup"><span data-stu-id="3bc19-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="3bc19-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="3bc19-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="3bc19-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="3bc19-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="3bc19-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="3bc19-106">Parameters</span></span>

<span data-ttu-id="3bc19-107">`MinLength`([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="3bc19-107">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="3bc19-108">Hiermee geeft u het minimum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3bc19-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="3bc19-109">`MaxLength`([System. Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="3bc19-109">`MaxLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="3bc19-110">Hiermee geeft u het maximum aantal tekens op dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="3bc19-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bc19-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="3bc19-111">Remarks</span></span>

- <span data-ttu-id="3bc19-112">Zie [Invoer validatie regels declareren](./how-to-validate-parameter-input.md)voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="3bc19-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](./how-to-validate-parameter-input.md).</span></span>

- <span data-ttu-id="3bc19-113">Als dit kenmerk niet wordt gebruikt, kan het bijbehorende parameter argument een wille keurige lengte hebben.</span><span class="sxs-lookup"><span data-stu-id="3bc19-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="3bc19-114">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="3bc19-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="3bc19-115">Wanneer de waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` kenmerk parameter.</span><span class="sxs-lookup"><span data-stu-id="3bc19-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

  - <span data-ttu-id="3bc19-116">Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="3bc19-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

  - <span data-ttu-id="3bc19-117">Wanneer het argument geen teken reeks is.</span><span class="sxs-lookup"><span data-stu-id="3bc19-117">When the argument is not a string.</span></span>

- <span data-ttu-id="3bc19-118">Het kenmerk ValidateLength wordt gedefinieerd door de klasse [System. Management. Automation. Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3bc19-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bc19-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="3bc19-119">See Also</span></span>

[<span data-ttu-id="3bc19-120">System. Management. Automation. Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="3bc19-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="3bc19-121">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="3bc19-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
