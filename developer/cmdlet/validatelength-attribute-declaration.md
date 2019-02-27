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
ms.openlocfilehash: 1e8364c78abba5272007019550ffcb2cedaf9fd0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848816"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="532ad-102">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="532ad-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="532ad-103">Het kenmerk ValidateLength Hiermee geeft u het minimum en maximum aantal tekens in voor een argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="532ad-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="532ad-104">Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.</span><span class="sxs-lookup"><span data-stu-id="532ad-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="532ad-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="532ad-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="532ad-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="532ad-106">Parameters</span></span>

<span data-ttu-id="532ad-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) vereist.</span><span class="sxs-lookup"><span data-stu-id="532ad-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="532ad-108">Hiermee geeft u het minimale aantal tekens dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="532ad-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="532ad-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) vereist.</span><span class="sxs-lookup"><span data-stu-id="532ad-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="532ad-110">Hiermee geeft u het maximale aantal toegestane tekens.</span><span class="sxs-lookup"><span data-stu-id="532ad-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="532ad-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="532ad-111">Remarks</span></span>

- <span data-ttu-id="532ad-112">Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u invoer validatieregels declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="532ad-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>
- <span data-ttu-id="532ad-113">Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u invoer validatieregels declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="532ad-113">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="532ad-114">Wanneer dit kenmerk niet gebruikt wordt, wordt het bijbehorende parameterargument is van een willekeurige lengte.</span><span class="sxs-lookup"><span data-stu-id="532ad-114">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="532ad-115">De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:</span><span class="sxs-lookup"><span data-stu-id="532ad-115">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="532ad-116">Wanneer de waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="532ad-116">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="532ad-117">Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="532ad-117">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="532ad-118">Als het argument is geen tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="532ad-118">When the argument is not a string.</span></span>

- <span data-ttu-id="532ad-119">Het kenmerk ValidateLength wordt gedefinieerd door de [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="532ad-119">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="532ad-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="532ad-120">See Also</span></span>

[<span data-ttu-id="532ad-121">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="532ad-121">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="532ad-122">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="532ad-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
