---
title: ValidateCount kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 4e0be34b6f7a56dcf02a4381de4d2a5d08db14df
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794434"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="f1fc1-102">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="f1fc1-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="f1fc1-103">Het kenmerk ValidateCount Hiermee geeft u het minimum en maximum aantal argumenten dat is toegestaan voor een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1fc1-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f1fc1-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="f1fc1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f1fc1-105">Parameters</span></span>

<span data-ttu-id="f1fc1-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="f1fc1-107">Hiermee geeft u het minimale aantal argumenten.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="f1fc1-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="f1fc1-109">Hiermee geeft u het maximum aantal argumenten.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1fc1-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f1fc1-110">Remarks</span></span>

- <span data-ttu-id="f1fc1-111">Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u invoer validatieregels declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="f1fc1-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="f1fc1-112">Als dit kenmerk niet gestart is, kan de bijbehorende cmdlet-parameter een willekeurig aantal argumenten hebben.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="f1fc1-113">De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:</span><span class="sxs-lookup"><span data-stu-id="f1fc1-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="f1fc1-114">De `MinLength` en `MaxLength` kenmerk parameters zijn niet van het type [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="f1fc1-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="f1fc1-115">De waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="f1fc1-116">Het kenmerk ValidateCount wordt gedefinieerd door de [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klasse.</span><span class="sxs-lookup"><span data-stu-id="f1fc1-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1fc1-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f1fc1-117">See Also</span></span>

[<span data-ttu-id="f1fc1-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="f1fc1-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="f1fc1-119">Hoe u regels voor Invoervalidatie declareren</span><span class="sxs-lookup"><span data-stu-id="f1fc1-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="f1fc1-120">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f1fc1-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
