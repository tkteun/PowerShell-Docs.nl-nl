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
ms.openlocfilehash: 3a4c5f279ce8587eeb5d583376ea3d2286210b83
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794328"
---
# <a name="validatelength-attribute-declaration"></a><span data-ttu-id="0c484-102">Declaratie van het kenmerk ValidateLength</span><span class="sxs-lookup"><span data-stu-id="0c484-102">ValidateLength Attribute Declaration</span></span>

<span data-ttu-id="0c484-103">Het kenmerk ValidateLength Hiermee geeft u het minimum en maximum aantal tekens in voor een argument van de cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="0c484-103">The ValidateLength attribute specifies the minimum and maximum number of characters for a cmdlet parameter argument.</span></span> <span data-ttu-id="0c484-104">Dit kenmerk kan ook worden gebruikt door Windows PowerShell-functies.</span><span class="sxs-lookup"><span data-stu-id="0c484-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c484-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="0c484-105">Syntax</span></span>

```csharp
[ValidateLength(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="0c484-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="0c484-106">Parameters</span></span>

<span data-ttu-id="0c484-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) vereist.</span><span class="sxs-lookup"><span data-stu-id="0c484-107">`MinLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="0c484-108">Hiermee geeft u het minimale aantal tekens dat is toegestaan.</span><span class="sxs-lookup"><span data-stu-id="0c484-108">Specifies the minimum number of characters allowed.</span></span>

<span data-ttu-id="0c484-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) vereist.</span><span class="sxs-lookup"><span data-stu-id="0c484-109">`MaxLength` ([System.Integer](/dotnet/api/System.Integer)) Required.</span></span> <span data-ttu-id="0c484-110">Hiermee geeft u het maximale aantal toegestane tekens.</span><span class="sxs-lookup"><span data-stu-id="0c484-110">Specifies the maximum number of characters allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c484-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="0c484-111">Remarks</span></span>

- <span data-ttu-id="0c484-112">Zie voor meer informatie over hoe u dit kenmerk declareren [hoe u invoer validatieregels declareren](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span><span class="sxs-lookup"><span data-stu-id="0c484-112">For more information about how to declare this attribute, see [How to Declare Input Validation Rules](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).</span></span>

- <span data-ttu-id="0c484-113">Wanneer dit kenmerk niet gebruikt wordt, wordt het bijbehorende parameterargument is van een willekeurige lengte.</span><span class="sxs-lookup"><span data-stu-id="0c484-113">When this attribute is not used, the corresponding parameter argument can be of any length.</span></span>

- <span data-ttu-id="0c484-114">De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:</span><span class="sxs-lookup"><span data-stu-id="0c484-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="0c484-115">Wanneer de waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="0c484-115">When the value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

    - <span data-ttu-id="0c484-116">Wanneer de `MaxLength` kenmerk parameter is ingesteld op 0.</span><span class="sxs-lookup"><span data-stu-id="0c484-116">When the `MaxLength` attribute parameter is set to 0.</span></span>

    - <span data-ttu-id="0c484-117">Als het argument is geen tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="0c484-117">When the argument is not a string.</span></span>

- <span data-ttu-id="0c484-118">Het kenmerk ValidateLength wordt gedefinieerd door de [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) klasse.</span><span class="sxs-lookup"><span data-stu-id="0c484-118">The ValidateLength attribute is defined by the [System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c484-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0c484-119">See Also</span></span>

[<span data-ttu-id="0c484-120">System.Management.Automation.Validatelengthattribute</span><span class="sxs-lookup"><span data-stu-id="0c484-120">System.Management.Automation.Validatelengthattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)

[<span data-ttu-id="0c484-121">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0c484-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
