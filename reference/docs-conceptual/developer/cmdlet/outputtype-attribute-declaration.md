---
title: Output type kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356159"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="abbcd-102">Declaratie van het kenmerk OutputType</span><span class="sxs-lookup"><span data-stu-id="abbcd-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="abbcd-103">Het kenmerk `OutputType` identificeert de .NET Framework typen die door een cmdlet, functie of script worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="abbcd-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="abbcd-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="abbcd-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="abbcd-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="abbcd-105">Parameters</span></span>

<span data-ttu-id="abbcd-106">Type (`string[]` of `Type[]`) vereist.</span><span class="sxs-lookup"><span data-stu-id="abbcd-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="abbcd-107">Hiermee geeft u de typen op die worden geretourneerd door de functie cmdlet of het script.</span><span class="sxs-lookup"><span data-stu-id="abbcd-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="abbcd-108">ParameterSetName (string []) optioneel.</span><span class="sxs-lookup"><span data-stu-id="abbcd-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="abbcd-109">Hiermee geeft u de parameter sets op die de typen retour neren die zijn opgegeven in de para meter `type`.</span><span class="sxs-lookup"><span data-stu-id="abbcd-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="abbcd-110">providerCmdlet optioneel.</span><span class="sxs-lookup"><span data-stu-id="abbcd-110">providerCmdlet Optional.</span></span> <span data-ttu-id="abbcd-111">Hiermee geeft u de provider-cmdlet op waarmee de typen worden geretourneerd die zijn opgegeven in de para meter `type`.</span><span class="sxs-lookup"><span data-stu-id="abbcd-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="abbcd-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="abbcd-112">See Also</span></span>

[<span data-ttu-id="abbcd-113">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="abbcd-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
