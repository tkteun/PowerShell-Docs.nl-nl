---
title: OutputType kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067600"
---
# <a name="outputtype-attribute-declaration"></a><span data-ttu-id="b5464-102">Declaratie van het kenmerk OutputType</span><span class="sxs-lookup"><span data-stu-id="b5464-102">OutputType Attribute Declaration</span></span>

<span data-ttu-id="b5464-103">De `OutputType` kenmerk wordt de .NET Framework-typen die wordt geretourneerd door een cmdlet, een functie of een script.</span><span class="sxs-lookup"><span data-stu-id="b5464-103">The `OutputType` attribute identifies the .NET Framework types returned by a cmdlet, function, or script.</span></span>

## <a name="syntax"></a><span data-ttu-id="b5464-104">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="b5464-104">Syntax</span></span>

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="b5464-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="b5464-105">Parameters</span></span>

<span data-ttu-id="b5464-106">Type (`string[]` of `Type[]`) vereist.</span><span class="sxs-lookup"><span data-stu-id="b5464-106">Type (`string[]` or `Type[]`) Required.</span></span> <span data-ttu-id="b5464-107">Hiermee geeft u de typen die zijn geretourneerd door de cmdlet-functie of het script.</span><span class="sxs-lookup"><span data-stu-id="b5464-107">Specifies the types returned by the cmdlet function, or script.</span></span>

<span data-ttu-id="b5464-108">ParameterSetName (string[]) Optional.</span><span class="sxs-lookup"><span data-stu-id="b5464-108">ParameterSetName (string[]) Optional.</span></span> <span data-ttu-id="b5464-109">Hiermee geeft u de parametersets die resulteren in de opgegeven typen in de `type` parameter.</span><span class="sxs-lookup"><span data-stu-id="b5464-109">Specifies the parameter sets that return the types specified in the `type` parameter.</span></span>

<span data-ttu-id="b5464-110">providerCmdlet optioneel.</span><span class="sxs-lookup"><span data-stu-id="b5464-110">providerCmdlet Optional.</span></span> <span data-ttu-id="b5464-111">Hiermee geeft u de provider-cmdlet die wordt geretourneerd van de typen die zijn opgegeven de `type` parameter.</span><span class="sxs-lookup"><span data-stu-id="b5464-111">Specifies the provider cmdlet that returns the types specified in the `type` parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5464-112">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b5464-112">See Also</span></span>

[<span data-ttu-id="b5464-113">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5464-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
