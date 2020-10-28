---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk OutputType
description: Declaratie van het kenmerk OutputType
ms.openlocfilehash: b5e33346e9ac29c13323781d62daffab892573a4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646455"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="b0517-103">Declaratie van het kenmerk OutputType</span><span class="sxs-lookup"><span data-stu-id="b0517-103">OutputType Attribute Declaration</span></span>

<span data-ttu-id="b0517-104">Het `OutputType` kenmerk identificeert de .NET Framework typen die worden geretourneerd door een cmdlet, functie of script.</span><span class="sxs-lookup"><span data-stu-id="b0517-104">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0517-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b0517-105">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="b0517-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="b0517-106">Parameters</span></span>

<span data-ttu-id="b0517-107">Type ( `string[]` of `Type[]` ) vereist.</span><span class="sxs-lookup"><span data-stu-id="b0517-107">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="b0517-108">Hiermee geeft u de typen op die worden geretourneerd door de functie cmdlet of het script.</span><span class="sxs-lookup"><span data-stu-id="b0517-108">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="b0517-109">ParameterSetName (string []) optioneel.</span><span class="sxs-lookup"><span data-stu-id="b0517-109">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="b0517-110">Hiermee geeft u de parameter sets op die de typen retour neren die zijn opgegeven in de `type` para meter.</span><span class="sxs-lookup"><span data-stu-id="b0517-110">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="b0517-111">providerCmdlet optioneel.</span><span class="sxs-lookup"><span data-stu-id="b0517-111">providerCmdlet Optional.</span></span> <span data-ttu-id="b0517-112">Hiermee geeft u de provider-cmdlet op waarmee de typen worden geretourneerd die zijn opgegeven in de `type` para meter.</span><span class="sxs-lookup"><span data-stu-id="b0517-112">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0517-113">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b0517-113">See Also</span></span>

[<span data-ttu-id="b0517-114">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="b0517-114">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
