---
title: Output type kenmerk declaratie | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a4cc874031bba092cfef6041bef0e19e6af3f09c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786540"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="02332-102">Declaratie van het kenmerk OutputType</span><span class="sxs-lookup"><span data-stu-id="02332-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="02332-103">Het `OutputType` kenmerk identificeert de .NET Framework typen die worden geretourneerd door een cmdlet, functie of script.</span><span class="sxs-lookup"><span data-stu-id="02332-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="02332-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="02332-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="02332-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="02332-105">Parameters</span></span>

<span data-ttu-id="02332-106">Type ( `string[]` of `Type[]` ) vereist.</span><span class="sxs-lookup"><span data-stu-id="02332-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="02332-107">Hiermee geeft u de typen op die worden geretourneerd door de functie cmdlet of het script.</span><span class="sxs-lookup"><span data-stu-id="02332-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="02332-108">ParameterSetName (string []) optioneel.</span><span class="sxs-lookup"><span data-stu-id="02332-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="02332-109">Hiermee geeft u de parameter sets op die de typen retour neren die zijn opgegeven in de `type` para meter.</span><span class="sxs-lookup"><span data-stu-id="02332-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="02332-110">providerCmdlet optioneel.</span><span class="sxs-lookup"><span data-stu-id="02332-110">providerCmdlet Optional.</span></span> <span data-ttu-id="02332-111">Hiermee geeft u de provider-cmdlet op waarmee de typen worden geretourneerd die zijn opgegeven in de `type` para meter.</span><span class="sxs-lookup"><span data-stu-id="02332-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="02332-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="02332-112">See Also</span></span>

[<span data-ttu-id="02332-113">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="02332-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
