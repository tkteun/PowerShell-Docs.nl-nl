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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359166"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="f4745-102">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="f4745-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="f4745-103">Het kenmerk ValidateCount geeft het minimale en maximale aantal argumenten op dat is toegestaan voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="f4745-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4745-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f4745-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="f4745-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f4745-105">Parameters</span></span>

<span data-ttu-id="f4745-106">`MinLength` ([System. Int32][]) is vereist.</span><span class="sxs-lookup"><span data-stu-id="f4745-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="f4745-107">Hiermee geeft u het minimum aantal argumenten op.</span><span class="sxs-lookup"><span data-stu-id="f4745-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="f4745-108">`MaxLength` ([System. Int32][]) is vereist.</span><span class="sxs-lookup"><span data-stu-id="f4745-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="f4745-109">Hiermee geeft u het maximum aantal argumenten op.</span><span class="sxs-lookup"><span data-stu-id="f4745-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4745-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f4745-110">Remarks</span></span>

- <span data-ttu-id="f4745-111">Zie [Een aantal argumenten valideren][](Engelstalig) voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="f4745-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="f4745-112">Als dit kenmerk niet wordt aangeroepen, kan de bijbehorende cmdlet-para meter een wille keurig aantal argumenten hebben.</span><span class="sxs-lookup"><span data-stu-id="f4745-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="f4745-113">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="f4745-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="f4745-114">De kenmerk parameters `MinLength` en `MaxLength` zijn niet van het type [System. Int32][].</span><span class="sxs-lookup"><span data-stu-id="f4745-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="f4745-115">De waarde van de para meter `MaxLength`-kenmerk is kleiner dan de waarde van de para meter `MinLength`-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="f4745-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="f4745-116">Het kenmerk ValidateCount wordt gedefinieerd door de klasse [System. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="f4745-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4745-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f4745-117">See Also</span></span>

<span data-ttu-id="f4745-118">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="f4745-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="f4745-119">[Een aantal argumenten valideren][]</span><span class="sxs-lookup"><span data-stu-id="f4745-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="f4745-120">[Een Windows Power shell-cmdlet schrijven][]</span><span class="sxs-lookup"><span data-stu-id="f4745-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Een aantal argumenten valideren]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Een Windows Power shell-cmdlet schrijven]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
