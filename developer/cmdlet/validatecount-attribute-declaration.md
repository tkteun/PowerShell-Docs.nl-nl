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
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849019"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="e711b-102">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="e711b-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="e711b-103">Het kenmerk ValidateCount Hiermee geeft u het minimum en maximum aantal argumenten dat is toegestaan voor een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="e711b-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="e711b-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e711b-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="e711b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e711b-105">Parameters</span></span>

<span data-ttu-id="e711b-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="e711b-106">`MinLength` ([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="e711b-107">Hiermee geeft u het minimale aantal argumenten.</span><span class="sxs-lookup"><span data-stu-id="e711b-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="e711b-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) vereist.</span><span class="sxs-lookup"><span data-stu-id="e711b-108">`MaxLength`([System.Int32](/dotnet/api/System.Int32)) Required.</span></span> <span data-ttu-id="e711b-109">Hiermee geeft u het maximum aantal argumenten.</span><span class="sxs-lookup"><span data-stu-id="e711b-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="e711b-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e711b-110">Remarks</span></span>

- <span data-ttu-id="e711b-111">Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u invoer validatieregels declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="e711b-111">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="e711b-112">Als dit kenmerk niet gestart is, kan de bijbehorende cmdlet-parameter een willekeurig aantal argumenten hebben.</span><span class="sxs-lookup"><span data-stu-id="e711b-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="e711b-113">De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:</span><span class="sxs-lookup"><span data-stu-id="e711b-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="e711b-114">De `MinLength` en `MaxLength` kenmerk parameters zijn niet van het type [System.Int32](/dotnet/api/System.Int32).</span><span class="sxs-lookup"><span data-stu-id="e711b-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32](/dotnet/api/System.Int32).</span></span>

    - <span data-ttu-id="e711b-115">De waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e711b-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="e711b-116">Het kenmerk ValidateCount wordt gedefinieerd door de [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) klasse.</span><span class="sxs-lookup"><span data-stu-id="e711b-116">The ValidateCount attribute is defined by the [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e711b-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e711b-117">See Also</span></span>

[<span data-ttu-id="e711b-118">System.Management.Automation.Validatecount</span><span class="sxs-lookup"><span data-stu-id="e711b-118">System.Management.Automation.Validatecount</span></span>](/dotnet/api/System.Management.Automation.ValidateCount)

[<span data-ttu-id="e711b-119">Hoe u regels voor Invoervalidatie declareren</span><span class="sxs-lookup"><span data-stu-id="e711b-119">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="e711b-120">Hoe u regels voor Invoervalidatie declareren</span><span class="sxs-lookup"><span data-stu-id="e711b-120">How to Declare Input Validation Rules</span></span>](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[<span data-ttu-id="e711b-121">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e711b-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
