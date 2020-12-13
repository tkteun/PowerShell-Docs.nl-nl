---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk ValidateCount
description: Declaratie van het kenmerk ValidateCount
ms.openlocfilehash: 6acdd02a10ecc1bc2be0e6be88cf2f42a3673eb8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646269"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="e057f-103">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="e057f-103">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="e057f-104">Het kenmerk ValidateCount geeft het minimale en maximale aantal argumenten op dat is toegestaan voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="e057f-104">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="e057f-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="e057f-105">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="e057f-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="e057f-106">Parameters</span></span>

<span data-ttu-id="e057f-107">`MinLength` ([System. Int32][]) vereist.</span><span class="sxs-lookup"><span data-stu-id="e057f-107">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="e057f-108">Hiermee geeft u het minimum aantal argumenten op.</span><span class="sxs-lookup"><span data-stu-id="e057f-108">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="e057f-109">`MaxLength`([System. Int32][]) vereist.</span><span class="sxs-lookup"><span data-stu-id="e057f-109">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="e057f-110">Hiermee geeft u het maximum aantal argumenten op.</span><span class="sxs-lookup"><span data-stu-id="e057f-110">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="e057f-111">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="e057f-111">Remarks</span></span>

- <span data-ttu-id="e057f-112">Zie [How to validate a argument Count][](Engelstalig) voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="e057f-112">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="e057f-113">Als dit kenmerk niet wordt aangeroepen, kan de bijbehorende cmdlet-para meter een wille keurig aantal argumenten hebben.</span><span class="sxs-lookup"><span data-stu-id="e057f-113">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="e057f-114">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="e057f-114">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="e057f-115">De `MinLength` `MaxLength` para meters en zijn niet van het type [System. Int32][].</span><span class="sxs-lookup"><span data-stu-id="e057f-115">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="e057f-116">De waarde van de `MaxLength` kenmerk parameter is kleiner dan de waarde van de `MinLength` kenmerk parameter.</span><span class="sxs-lookup"><span data-stu-id="e057f-116">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="e057f-117">Het kenmerk ValidateCount wordt gedefinieerd door de klasse [System. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="e057f-117">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e057f-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e057f-118">See Also</span></span>

<span data-ttu-id="e057f-119">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="e057f-119">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="e057f-120">[Het aantal argumenten valideren][]</span><span class="sxs-lookup"><span data-stu-id="e057f-120">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="e057f-121">[Een Windows PowerShell-cmdlet schrijven][]</span><span class="sxs-lookup"><span data-stu-id="e057f-121">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Het aantal argumenten valideren]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Een Windows PowerShell-cmdlet schrijven]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
