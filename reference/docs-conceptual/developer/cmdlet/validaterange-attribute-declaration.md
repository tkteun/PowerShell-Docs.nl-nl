---
title: ValidateRange kenmerk declaratie | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.openlocfilehash: 9aeaa6f03c170389ff61a058b505dbcf74df6958
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787781"
---
# <a name="validaterange-attribute-declaration"></a><span data-ttu-id="32bda-102">Declaratie van het kenmerk ValidateRange</span><span class="sxs-lookup"><span data-stu-id="32bda-102">ValidateRange Attribute Declaration</span></span>

<span data-ttu-id="32bda-103">Met het kenmerk ValidateRange worden de minimum-en maximum waarden (het bereik) opgegeven voor het argument van de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="32bda-103">The ValidateRange attribute specifies the minimum and maximum values (the range) for the cmdlet parameter argument.</span></span> <span data-ttu-id="32bda-104">Dit kenmerk kan ook worden gebruikt door Windows Power shell-functies.</span><span class="sxs-lookup"><span data-stu-id="32bda-104">This attribute can also be used by Windows PowerShell functions.</span></span>

## <a name="syntax"></a><span data-ttu-id="32bda-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="32bda-105">Syntax</span></span>

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a><span data-ttu-id="32bda-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="32bda-106">Parameters</span></span>

<span data-ttu-id="32bda-107">`MinRange` ([System. object](/dotnet/api/system.object)) vereist.</span><span class="sxs-lookup"><span data-stu-id="32bda-107">`MinRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="32bda-108">Hiermee geeft u de toegestane minimum waarde.</span><span class="sxs-lookup"><span data-stu-id="32bda-108">Specifies the minimum value allowed.</span></span>

<span data-ttu-id="32bda-109">`MaxRange` ([System. object](/dotnet/api/system.object)) vereist.</span><span class="sxs-lookup"><span data-stu-id="32bda-109">`MaxRange` ([System.Object](/dotnet/api/system.object)) Required.</span></span> <span data-ttu-id="32bda-110">Hiermee geeft u de toegestane maximum waarde.</span><span class="sxs-lookup"><span data-stu-id="32bda-110">Specifies the maximum value allowed.</span></span>

## <a name="remarks"></a><span data-ttu-id="32bda-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="32bda-111">Remarks</span></span>

- <span data-ttu-id="32bda-112">De Windows Power shell-runtime genereert een constructie fout wanneer de waarde van de `MinRange` para meter groter is dan de waarde van de `MaxRange` para meter.</span><span class="sxs-lookup"><span data-stu-id="32bda-112">The Windows PowerShell runtime throws a construction error when the value of the `MinRange` parameter is greater than the value of the `MaxRange` parameter.</span></span>

- <span data-ttu-id="32bda-113">De Windows Power shell-runtime genereert een validatie fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="32bda-113">The Windows PowerShell runtime throws a validation error under the following conditions:</span></span>

  - <span data-ttu-id="32bda-114">Wanneer de waarde van het argument kleiner is dan de `MinRange` limiet of groter is dan de `MaxRange` limiet.</span><span class="sxs-lookup"><span data-stu-id="32bda-114">When the value of the argument is less than the `MinRange` limit or greater than the `MaxRange` limit.</span></span>

  - <span data-ttu-id="32bda-115">Wanneer het argument niet van hetzelfde type is als de `MinRange` `MaxRange` para meters en.</span><span class="sxs-lookup"><span data-stu-id="32bda-115">When the argument is not of the same type as the `MinRange` and the `MaxRange` parameters.</span></span>

- <span data-ttu-id="32bda-116">Het kenmerk ValidateRange wordt gedefinieerd door de klasse [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="32bda-116">The ValidateRange attribute is defined by the [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="32bda-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="32bda-117">See Also</span></span>

[<span data-ttu-id="32bda-118">System. Management. Automation. Validaterangeattribute</span><span class="sxs-lookup"><span data-stu-id="32bda-118">System.Management.Automation.Validaterangeattribute</span></span>](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[<span data-ttu-id="32bda-119">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="32bda-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
