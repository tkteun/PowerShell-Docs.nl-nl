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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067175"
---
# <a name="validatecount-attribute-declaration"></a><span data-ttu-id="1065b-102">Declaratie van het kenmerk ValidateCount</span><span class="sxs-lookup"><span data-stu-id="1065b-102">ValidateCount Attribute Declaration</span></span>

<span data-ttu-id="1065b-103">Het kenmerk ValidateCount Hiermee geeft u het minimum en maximum aantal argumenten dat is toegestaan voor een cmdlet-parameter.</span><span class="sxs-lookup"><span data-stu-id="1065b-103">The ValidateCount attribute specifies the minimum and maximum number of arguments allowed for a cmdlet parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="1065b-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1065b-104">Syntax</span></span>

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a><span data-ttu-id="1065b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="1065b-105">Parameters</span></span>

<span data-ttu-id="1065b-106">`MinLength` ([System.Int32][]) vereist.</span><span class="sxs-lookup"><span data-stu-id="1065b-106">`MinLength` ([System.Int32][]) Required.</span></span> <span data-ttu-id="1065b-107">Hiermee geeft u het minimale aantal argumenten.</span><span class="sxs-lookup"><span data-stu-id="1065b-107">Specifies the minimum number of arguments.</span></span>

<span data-ttu-id="1065b-108">`MaxLength`([System.Int32][]) vereist.</span><span class="sxs-lookup"><span data-stu-id="1065b-108">`MaxLength`([System.Int32][]) Required.</span></span> <span data-ttu-id="1065b-109">Hiermee geeft u het maximum aantal argumenten.</span><span class="sxs-lookup"><span data-stu-id="1065b-109">Specifies the maximum number of arguments.</span></span>

## <a name="remarks"></a><span data-ttu-id="1065b-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1065b-110">Remarks</span></span>

- <span data-ttu-id="1065b-111">Zie voor meer informatie over hoe u dit kenmerk declareren [het valideren van een aantal argumenten][].</span><span class="sxs-lookup"><span data-stu-id="1065b-111">For more information about how to declare this attribute, see [How to Validate an Argument Count][].</span></span>

- <span data-ttu-id="1065b-112">Als dit kenmerk niet gestart is, kan de bijbehorende cmdlet-parameter een willekeurig aantal argumenten hebben.</span><span class="sxs-lookup"><span data-stu-id="1065b-112">When this attribute is not invoked, the corresponding cmdlet parameter can have any number of arguments.</span></span>

- <span data-ttu-id="1065b-113">De Windows PowerShell-runtime genereert een fout in de volgende omstandigheden:</span><span class="sxs-lookup"><span data-stu-id="1065b-113">The Windows PowerShell runtime throws an error under the following conditions:</span></span>

    - <span data-ttu-id="1065b-114">De `MinLength` en `MaxLength` kenmerk parameters zijn niet van het type [System.Int32][].</span><span class="sxs-lookup"><span data-stu-id="1065b-114">The `MinLength` and `MaxLength` attribute parameters are not of type [System.Int32][].</span></span>

    - <span data-ttu-id="1065b-115">De waarde van de `MaxLength` kenmerk parameter kleiner is dan de waarde van de `MinLength` parameter van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="1065b-115">The value of the `MaxLength` attribute parameter is less than the value of the `MinLength` attribute parameter.</span></span>

- <span data-ttu-id="1065b-116">Het kenmerk ValidateCount wordt gedefinieerd door de [System.Management.Automation.ValidateCountAttribute][] klasse.</span><span class="sxs-lookup"><span data-stu-id="1065b-116">The ValidateCount attribute is defined by the [System.Management.Automation.ValidateCountAttribute][] class.</span></span>

## <a name="see-also"></a><span data-ttu-id="1065b-117">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1065b-117">See Also</span></span>

<span data-ttu-id="1065b-118">[System.Management.Automation.ValidateCountAttribute][]</span><span class="sxs-lookup"><span data-stu-id="1065b-118">[System.Management.Automation.ValidateCountAttribute][]</span></span>

<span data-ttu-id="1065b-119">[Het valideren van een aantal argumenten][]</span><span class="sxs-lookup"><span data-stu-id="1065b-119">[How to Validate an Argument Count][]</span></span>

<span data-ttu-id="1065b-120">[Schrijven van een Windows PowerShell-Cmdlet][]</span><span class="sxs-lookup"><span data-stu-id="1065b-120">[Writing a Windows PowerShell Cmdlet][]</span></span>

[Het valideren van een aantal argumenten]: how-to-validate-an-argument-count.md
[How to Validate an Argument Count]: how-to-validate-an-argument-count.md
[Schrijven van een Windows PowerShell-Cmdlet]: writing-a-windows-powershell-cmdlet.md
[Writing a Windows PowerShell Cmdlet]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
