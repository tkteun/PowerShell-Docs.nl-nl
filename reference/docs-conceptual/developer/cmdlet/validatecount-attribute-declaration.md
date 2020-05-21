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
ms.openlocfilehash: 3cae95fab30a4abe4e544ed5cb7dadc9f4debf02
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692367"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="843cd-102">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="843cd-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="843cd-103">Het kenmerk ValidateCount geeft het minimale en maximale aantal argumenten op dat is toegestaan voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="843cd-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="843cd-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="843cd-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="843cd-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="843cd-105">Parameters</span></span>

<span data-ttu-id="843cd-106">`MinLength`([System. Int32][]) vereist.</span><span class="sxs-lookup"><span data-stu-id="843cd-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="843cd-107">Hiermee geeft u het minimum aantal argumenten op.</span><span class="sxs-lookup"><span data-stu-id="843cd-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="843cd-108">`MaxLength`([System. Int32][]) vereist.</span><span class="sxs-lookup"><span data-stu-id="843cd-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="843cd-109">Hiermee geeft u het maximum aantal argumenten op.</span><span class="sxs-lookup"><span data-stu-id="843cd-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="843cd-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="843cd-110">Remarks</span></span>

- <span data-ttu-id="843cd-111">Zie [How to validate a argument Count][](Engelstalig) voor meer informatie over het declareren van dit kenmerk.</span><span class="sxs-lookup"><span data-stu-id="843cd-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="843cd-112">Als dit kenmerk niet wordt aangeroepen, kan de bijbehorende cmdlet-para meter een wille keurig aantal argumenten hebben.</span><span class="sxs-lookup"><span data-stu-id="843cd-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="843cd-113">De Windows Power shell-runtime genereert een fout in de volgende situaties:</span><span class="sxs-lookup"><span data-stu-id="843cd-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

  - <span data-ttu-id="843cd-114">De `MinLength` `MaxLength` para meters en zijn niet van het type [System. Int32][].</span><span class="sxs-lookup"><span data-stu-id="843cd-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

  - <span data-ttu-id="843cd-115">De waarde van de `MaxLength` kenmerk parameter is kleiner dan de waarde van de `MinLength` kenmerk parameter.</span><span class="sxs-lookup"><span data-stu-id="843cd-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="843cd-116">Het kenmerk ValidateCount wordt gedefinieerd door de klasse [System. Management. Automation. ValidateCountAttribute][] .</span><span class="sxs-lookup"><span data-stu-id="843cd-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="843cd-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="843cd-117">See Also</span></span>

<span data-ttu-id="843cd-118">[System. Management. Automation. ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="843cd-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="843cd-119">[Het aantal argumenten valideren][]</span><span class="sxs-lookup"><span data-stu-id="843cd-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="843cd-120">[Een Windows PowerShell-cmdlet schrijven][]</span><span class="sxs-lookup"><span data-stu-id="843cd-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Het aantal argumenten valideren]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Een Windows PowerShell-cmdlet schrijven]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System. Int32]: /dotnet/api/System.Int32
[System.Int32]: /dotnet/api/System.Int32
[System. Management. Automation. ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
