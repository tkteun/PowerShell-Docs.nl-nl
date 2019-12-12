---
title: Alias kenmerk declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359484"
---
# <a name="alias-attribute-declaration"></a><span data-ttu-id="460b8-102">Declaratie van het kenmerk Alias</span><span class="sxs-lookup"><span data-stu-id="460b8-102">Alias Attribute Declaration</span></span>

<span data-ttu-id="460b8-103">Met het alias kenmerk kan de gebruiker verschillende namen opgeven voor een cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="460b8-103">The Alias attribute allows the user to specify different names for a cmdlet parameter.</span></span> <span data-ttu-id="460b8-104">Aliassen kunnen worden gebruikt om snelkoppelingen voor de naam van een para meter op te geven, of ze kunnen verschillende namen opgeven die geschikt zijn voor verschillende scenario's.</span><span class="sxs-lookup"><span data-stu-id="460b8-104">Aliases can be used to provide shortcuts for a parameter name, or they can provide different names that are appropriate for different scenarios.</span></span>

## <a name="syntax"></a><span data-ttu-id="460b8-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="460b8-105">Syntax</span></span>

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a><span data-ttu-id="460b8-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="460b8-106">Parameters</span></span>

<span data-ttu-id="460b8-107">`aliasName` (string []) vereist.</span><span class="sxs-lookup"><span data-stu-id="460b8-107">`aliasName` (String[]) Required.</span></span> <span data-ttu-id="460b8-108">Hiermee geeft u een set met door komma's gescheiden alias namen op voor de cmdlet-para meter.</span><span class="sxs-lookup"><span data-stu-id="460b8-108">Specifies a set of comma-separated alias names for the cmdlet parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="460b8-109">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="460b8-109">Remarks</span></span>

- <span data-ttu-id="460b8-110">Het kenmerk alias wordt gebruikt met het parameter kenmerk wanneer u een cmdlet-para meter opgeeft.</span><span class="sxs-lookup"><span data-stu-id="460b8-110">The Alias attribute is used with the Parameter attribute when you specify a cmdlet parameter.</span></span> <span data-ttu-id="460b8-111">Zie voor meer informatie over het declareren van deze kenmerken [cmdlet-para meters declareren](./how-to-declare-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="460b8-111">For more information about how to declare these attributes, see [How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md).</span></span>

- <span data-ttu-id="460b8-112">Elke alias naam moet uniek zijn binnen een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="460b8-112">Each alias name must be unique within a cmdlet.</span></span> <span data-ttu-id="460b8-113">Windows Power shell controleert niet op dubbele alias namen.</span><span class="sxs-lookup"><span data-stu-id="460b8-113">Windows PowerShell does not check for duplicate alias names.</span></span>

- <span data-ttu-id="460b8-114">Het alias kenmerk wordt één keer gebruikt voor elke para meter in een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="460b8-114">The Alias attribute is used once for each parameter in a cmdlet.</span></span>

- <span data-ttu-id="460b8-115">Het alias kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) .</span><span class="sxs-lookup"><span data-stu-id="460b8-115">The Alias attribute is defined by the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="460b8-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="460b8-116">See Also</span></span>

[<span data-ttu-id="460b8-117">Parameter aliassen</span><span class="sxs-lookup"><span data-stu-id="460b8-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="460b8-118">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="460b8-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
